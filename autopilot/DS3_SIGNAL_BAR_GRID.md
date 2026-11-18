# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 06:29Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 12375 | 400 | 0.000 | -0.68 / -0.60 / -0.58 / -1.02 | YES | {"Asia": 0.815, "London": 0.813, "NYAM": 0.814, "NYPM": 0.814} |  |
| p1rand2 | 12561 | 400 | 0.000 | -0.65 / -0.62 / -0.61 / -0.98 | YES | {"Asia": 0.816, "London": 0.813, "NYAM": 0.815, "NYPM": 0.815} |  |
| p1rand3 | 220 | 220 | 0.000 | -0.67 / -0.59 / -0.60 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand4 | 220 | 220 | 0.000 | -0.66 / -0.59 / -0.60 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 220 | 220 | 0.000 | -0.68 / -0.61 / -0.59 / -1.03 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 06:29Z):** result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 13893, "p1rand2": 13805, "p1rand3": 222, "p1rand4": 222, "p1rand5": 222, "p1real": 21117, "p1realx": 219, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 2, "London": 2, "NYAM": 2, "NYPM": 2}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 06:29Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 13893, "p1rand2": 13805, "p1rand3": 222, "p1rand4": 222, "p1rand5": 222, "p1real": 21117, "p1realx": 219, "rand1": 0, "real": 1654}; loop status: 2026-11-18T06:16Z rows=322 mods=146 todo=82705 running=0. 
Cells scored per session: {"Asia": 3266871, "London": 3162454, "NYAM": 3413551, "NYPM": 3428308}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -24.0 | -0.026 | 1316.3 | 0.44 | -26.5 | -64.3 | -3.7 | 17.5 | -20.3 | 0.50 | -20.1 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| agreed | -22.6 | -0.020 | 1242.8 | 0.44 | -26.5 | -64.3 | 1.6 | 8.8 | -24.1 | 0.00 | -19.3 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -52.5 [-62.2; 0.00] | -32.4 [-32.6; 0.00] | -40.0 [-48.1; 0.00] | 2.5 [0.6; 0.50] |
| bands (native) | -24.3 [-6.5; 0.00] | -9.7 [-22.6; 0.00] | -24.9 [-3.5; 0.50] | -22.5 [-0.8; 0.50] |
| barnative | -12.7 [6.0; 0.50] | 5.3 [26.6; 1.00] | 11.1 [33.1; 1.00] | -14.4 [-1.4; 0.50] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -3.5 [16.3; 1.00] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 0.6 [-0.3; 0.50] | n/a (no signals by construction) |
| confluence | -11.0 [-23.6; 0.00] | -14.0 [-13.4; 0.50] | -20.6 [-22.3; 0.00] | 14.7 [18.2; 1.00] |
| levels | -21.3 [-10.4; 0.50] | -28.0 [-20.9; 0.50] | 15.9 [32.6; 1.00] | -23.2 [-29.5; 0.00] |
| levels (native) | -22.3 [-17.6; 0.50] | 2.1 [19.9; 1.00] | -2.5 [-10.2; 0.00] | -14.9 [17.3; 1.00] |
| live | -1.4 [9.7; 1.00] | -16.9 [-11.9; 0.00] | 0.8 [16.7; 1.00] | 6.3 [-4.3; 0.50] |
| manual | -8.5 [8.6; 0.50] | -5.2 [7.0; 1.00] | -26.6 [-17.3; 0.00] | -5.0 [5.1; 0.50] |
| manual (native) | 4.4 [8.3; 1.00] | -30.5 [-26.3; 0.00] | -14.9 [1.4; 0.50] | -27.1 [0.7; 0.50] |
| momentum | -6.6 [-5.8; 0.50] | 16.1 [13.7; 0.50] | -14.6 [-8.1; 0.50] | -4.9 [1.9; 0.50] |
| momentum (native) | -38.9 [-11.3; 0.00] | -23.6 [-33.2; 0.00] | -3.8 [-1.5; 0.50] | -8.1 [1.3; 0.50] |
| pullback | -14.2 [-12.3; 0.50] | -9.2 [8.3; 0.50] | 6.2 [-18.0; 0.00] | -4.6 [19.9; 1.00] |
| pullback (native) | -16.7 [-0.1; 0.50] | -0.1 [18.2; 1.00] | 2.1 [42.1; 1.00] | -39.7 [-24.6; 0.00] |
| structure | -17.0 [-24.9; 0.00] | -18.0 [-22.7; 0.00] | -27.7 [-12.6; 0.00] | -20.1 [10.7; 0.50] |
| structure (native) | -18.8 [-35.0; 0.00] | -19.7 [-32.1; 0.00] | -0.6 [14.3; 1.00] | -33.3 [-29.7; 0.00] |
| tape | -12.6 [-15.7; 0.50] | -17.3 [-2.8; 0.00] | -23.9 [-31.7; 0.00] | -14.9 [1.4; 0.50] |
| tape (native) | -21.0 [-33.9; 0.00] | -18.3 [7.7; 1.00] | -12.4 [2.8; 0.50] | -38.4 [-21.5; 0.00] |
| trend | -16.0 [-9.2; 0.00] | -18.2 [2.4; 0.50] | -19.7 [-19.7; 0.00] | 9.0 [35.7; 1.00] |
| trend (native) | 2.2 [17.7; 1.00] | -6.7 [13.8; 1.00] | -18.4 [-7.9; 0.00] | -7.2 [-8.9; 0.50] |
| xmarket | 2.5 [-13.0; 0.00] | 6.0 [4.9; 0.50] | 6.4 [7.0; 1.00] | -8.9 [-7.1; 0.50] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|INFORMATION | 16.1 | 0.028 | 278.2 | 0.56 | -26.0 | -60.3 | {"2023": -15.5, "2024": 56.6, "2025": 10.1, "2026": -14.5} | 2.5 | 13.7 | 0.50 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels|PRICE | 15.9 | 0.014 | 342.4 | 0.54 | 52.3 | 93.9 | {"2023": -47.0, "2024": 20.9, "2025": -1.3, "2026": 50.2} | -16.7 | 32.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|TIME | 14.7 | 0.017 | 190.5 | 0.53 | 40.3 | -23.0 | {"2023": -4.8, "2024": 9.5, "2025": 13.4, "2026": 28.7} | -3.4 | 18.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|PRICE | 11.1 | 0.004 | 513.0 | 0.51 | 73.7 | 134.5 | {"2023": 17.8, "2024": -29.4, "2025": 33.1, "2026": 30.7} | -22.0 | 33.1 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend|TIME | 9.0 | 0.015 | 622.2 | 0.53 | -100.9 | 41.0 | {"2023": 6.9, "2024": 23.5, "2025": 30.1, "2026": -32.6} | -26.7 | 35.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| xmarket|PRICE | 6.4 | 0.005 | 352.8 | 0.51 | 33.4 | 80.2 | {"2023": 7.4, "2024": -1.7, "2025": -1.5, "2026": 24.9} | -0.6 | 7.0 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "AMBER", "2026": "ok"} |
| live|TIME | 6.3 | 0.006 | 538.3 | 0.54 | 81.1 | 29.7 | {"2023": -30.4, "2024": -12.7, "2025": -14.9, "2026": 65.7} | 10.6 | -4.3 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| pullback|PRICE | 6.2 | 0.007 | 717.6 | 0.52 | 81.9 | 115.9 | {"2023": 8.5, "2024": -6.8, "2025": 2.2, "2026": 25.7} | 24.2 | -18.0 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|INFORMATION | 6.0 | 0.008 | 354.7 | 0.57 | 11.5 | 78.7 | {"2023": -5.3, "2024": 19.1, "2025": 5.5, "2026": -5.4} | 1.1 | 4.9 | 0.50 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| barnative|INFORMATION | 5.3 | 0.000 | 795.6 | 0.52 | 61.9 | 76.1 | {"2023": 29.5, "2024": 30.3, "2025": -12.4, "2026": -11.0} | -21.3 | 26.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.2%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.2%); U7 tm600 L6M -10.7 pts/wk, rank 33% (top 67.5%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.2%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 38.2%); A7 tm60 L6M 14.3 pts/wk, rank 79% (top 20.7%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|INFORMATION | 30.2 | 0.023 | 222.3 | 0.58 | 56.4 | -3.5 | {"2023": -25.3, "2024": 61.9, "2025": 9.1, "2026": 35.4} | 0.3 | 29.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|PRICE | 18.8 | 0.020 | 483.7 | 0.53 | 126.6 | 134.5 | {"2023": -54.1, "2024": 5.3, "2025": -0.3, "2026": 80.4} | 1.7 | 17.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| xmarket|TIME | 17.5 | 0.026 | 469.0 | 0.57 | 77.1 | 116.5 | {"2023": 34.5, "2024": 26.0, "2025": 29.2, "2026": -11.8} | 17.0 | 0.5 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| xmarket|ACTIVITY | 12.5 | 0.014 | 424.5 | 0.52 | -12.9 | -98.5 | {"2023": -10.4, "2024": -6.3, "2025": 12.5, "2026": 42.2} | -8.1 | 20.7 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 9.1 | 0.012 | 356.4 | 0.53 | 99.4 | 151.5 | {"2023": -46.0, "2024": -3.6, "2025": 30.5, "2026": 16.4} | -20.4 | 29.5 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| pullback|PRICE | 8.4 | 0.002 | 615.3 | 0.52 | 101.2 | 115.9 | {"2023": -16.3, "2024": -6.2, "2025": 5.9, "2026": 36.6} | 27.0 | -18.6 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 8.2 | 0.007 | 447.5 | 0.51 | 32.4 | 58.3 | {"2023": -18.0, "2024": -12.4, "2025": -3.5, "2026": 54.7} | -31.8 | 40.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| manual (native)|ACTIVITY | 8.0 | 0.004 | 448.9 | 0.53 | 2.0 | -48.1 | {"2023": -8.8, "2024": 33.7, "2025": -15.4, "2026": 10.5} | -7.2 | 15.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|INFORMATION | 6.6 | 0.002 | 652.6 | 0.49 | 75.8 | 35.7 | {"2023": -38.5, "2024": 16.1, "2025": -15.4, "2026": 35.6} | -20.8 | 27.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape (native)|INFORMATION | 4.6 | -0.004 | 322.1 | 0.51 | 13.4 | -49.1 | {"2023": 3.8, "2024": -9.3, "2025": 42.4, "2026": -23.5} | -25.1 | 29.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | vsess_600 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | sym8u | both | 6120 | 2666 | 701 | 1.00 | 5 / -1086 / 562 / 1.00 | {"2023": -421.0, "2024": -1541.0, "2025": -1139.0, "2026": 6064.0} |
| 2 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 50} | sym8u | both | 6032 | 3321 | 643 | 1.00 | 5 / -163 / 2254 / 1.00 | {"2023": -1534.0, "2024": 277.0, "2025": 116.0, "2026": 5648.0} |
| 3 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym8u | both | 5846 | 2536 | 233 | 1.00 | 5 / -495 / 1844 / 1.00 | {"2023": 667.0, "2024": 1147.0, "2025": -135.0, "2026": 5737.0} |
| 4 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | 5 / -290 / 857 / 1.00 | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 5 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym15u/30u | both | 5725 | 2309 | 222 | 1.00 | 5 / -324 / 869 / 1.00 | {"2023": 805.0, "2024": -945.0, "2025": -3204.0, "2026": 7489.0} |
| 6 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 200} | sym8u | both | 5714 | 2851 | 645 | 1.00 | 5 / -2256 / 214 / 1.00 | {"2023": -1209.0, "2024": 895.0, "2025": -1513.0, "2026": 6526.0} |
| 7 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym20u/10u | both | 5657 | 2334 | 231 | 1.00 | 5 / -482 / 2351 / 1.00 | {"2023": 891.0, "2024": 2127.0, "2025": 454.0, "2026": 5288.0} |
| 8 | tm20 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 5614 | 2080 | 613 | 0.67 | 5 / -1401 / 1393 / 1.00 | {"2023": -1695.0, "2024": -839.0, "2025": -981.0, "2026": 7113.0} |
| 9 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | sym15u | both | 5590 | 3492 | 248 | 0.50 | 2 / -1321 / 736 / 1.00 | {"2023": 3.0, "2024": -891.0, "2025": 769.0, "2026": 4654.0} |
| 10 | dlt_45 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "close"} | sym8u | both | 5555 | 1195 | 312 | 1.00 | 5 / -1109 / 3168 / 1.00 | {"2023": -1481.0, "2024": -1100.0, "2025": 62.0, "2026": 7032.0} |
| 11 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 5541 | 2215 | 231 | 1.00 | 5 / -457 / 2314 / 1.00 | {"2023": 1193.0, "2024": 760.0, "2025": -21.0, "2026": 5146.0} |
| 12 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 13 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 812.0, "2024": 1425.0, "2025": 18.0, "2026": 5170.0} |
| 14 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 766.0, "2024": 1526.0, "2025": 18.0, "2026": 5170.0} |
| 15 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym30u | both | 5528 | 2119 | 220 | 1.00 | 5 / -257 / 968 / 1.00 | {"2023": 677.0, "2024": -476.0, "2025": -2538.0, "2026": 6998.0} |
| 16 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym10u/20u | both | 5527 | 1802 | 260 | 1.00 | 5 / -84 / 712 / 1.00 | {"2023": 418.0, "2024": -2082.0, "2025": -1357.0, "2026": 6422.0} |
| 17 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | 5 / -350 / 2382 / 1.00 | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 18 | swing_atr_0.1 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -397 / 391 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |
| 19 | swing_atr_0.1 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -469 / 2733 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |
| 20 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | asym20u/10u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 768.0, "2024": -842.0, "2025": -872.0, "2026": 5499.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 43.7 | 0.028 | 270.9 | 0.62 | 60.5 | 91.3 | -48.1 | -41.6 | 91.8 | 1.00 | -2.5 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 41.6 | 0.026 | 325.0 | 0.60 | 46.0 | 91.3 | -25.3 | -17.7 | 66.9 | 1.00 | -2.7 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 37.3 [20.4; 1.00] | -2.7 [-5.8; 0.50] | -14.7 [-3.7; 0.50] | 30.1 [21.2; 1.00] |
| bands (native) | 3.2 [10.0; 0.50] | 4.6 [17.6; 0.50] | 13.1 [62.6; 1.00] | 30.0 [65.6; 1.00] |
| barnative | -15.3 [11.7; 0.50] | -25.9 [-57.9; 0.00] | 45.5 [79.6; 1.00] | 11.1 [-13.6; 0.00] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -23.5 [4.6; 0.50] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 7.4 [12.9; 0.50] | n/a (no signals by construction) |
| confluence | -1.8 [24.7; 1.00] | -6.4 [7.3; 0.50] | 26.9 [37.4; 1.00] | 1.9 [1.9; 0.50] |
| levels | 7.9 [32.5; 1.00] | -25.5 [3.0; 0.50] | 5.2 [33.7; 1.00] | -1.3 [-22.3; 0.50] |
| levels (native) | 27.5 [32.2; 1.00] | 16.0 [28.6; 1.00] | 29.0 [56.9; 1.00] | -9.2 [6.7; 0.50] |
| live | 17.8 [27.8; 0.50] | 4.6 [30.7; 1.00] | 0.2 [-4.3; 0.00] | -10.3 [-5.0; 0.50] |
| manual | 28.8 [46.7; 1.00] | 40.1 [32.9; 1.00] | -20.0 [-30.9; 0.00] | 33.3 [37.0; 1.00] |
| manual (native) | -67.2 [-36.2; 0.00] | -58.7 [-58.3; 0.00] | 0.5 [20.2; 0.50] | -16.6 [1.6; 0.50] |
| momentum | 4.5 [-3.6; 0.50] | 5.3 [11.7; 0.50] | -2.8 [-28.5; 0.00] | 39.8 [27.0; 1.00] |
| momentum (native) | 1.9 [24.5; 0.50] | 14.2 [10.2; 0.50] | 21.4 [23.1; 0.50] | 36.0 [48.2; 1.00] |
| pullback | 21.6 [38.7; 1.00] | 22.6 [59.6; 1.00] | -26.4 [16.4; 1.00] | -1.4 [11.6; 1.00] |
| pullback (native) | 26.2 [47.0; 1.00] | -4.6 [7.6; 0.50] | -9.9 [36.6; 1.00] | -18.9 [5.1; 0.50] |
| structure | 20.4 [20.2; 1.00] | -6.3 [4.9; 0.50] | 20.9 [32.0; 1.00] | -0.9 [24.2; 0.50] |
| structure (native) | 36.8 [69.6; 1.00] | 40.8 [34.9; 1.00] | -3.3 [-19.9; 0.00] | 38.2 [42.6; 1.00] |
| tape | 1.7 [-19.3; 0.50] | -37.2 [-72.8; 0.00] | 10.3 [7.6; 0.50] | 22.6 [27.1; 1.00] |
| tape (native) | -6.8 [-5.3; 0.50] | -24.2 [-31.1; 0.00] | 4.7 [18.8; 1.00] | 0.3 [-12.4; 0.00] |
| trend | -30.7 [-55.6; 0.00] | -3.6 [1.0; 0.50] | 4.3 [-0.9; 0.50] | -4.5 [18.6; 1.00] |
| trend (native) | -60.1 [-72.5; 0.00] | -21.8 [10.0; 1.00] | 37.2 [43.1; 1.00] | -23.4 [-11.6; 0.50] |
| xmarket | -1.7 [1.4; 0.50] | -17.5 [-9.0; 0.50] | -46.5 [-56.3; 0.00] | -19.2 [-19.1; 0.50] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 45.5 | 0.019 | 534.7 | 0.59 | 45.9 | -36.9 | {"2023": -29.3, "2024": -21.0, "2025": 104.9, "2026": 77.7} | -34.1 | 79.6 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 40.8 | 0.026 | 575.2 | 0.59 | 66.4 | 44.7 | {"2023": 56.8, "2024": 0.4, "2025": 94.7, "2026": 19.6} | 5.8 | 34.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 40.1 | 0.025 | 425.4 | 0.59 | 73.0 | -52.6 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 52.5} | 7.3 | 32.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 39.8 | 0.023 | 654.3 | 0.57 | 96.6 | 167.5 | {"2023": 22.0, "2024": 70.5, "2025": 52.6, "2026": -6.1} | 12.8 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} | -4.4 | 42.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|ACTIVITY | 37.3 | 0.022 | 354.8 | 0.54 | 21.7 | -17.3 | {"2023": -8.1, "2024": 39.9, "2025": 76.3, "2026": 2.4} | 16.9 | 20.4 | 1.00 | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|PRICE | 37.2 | 0.024 | 347.2 | 0.60 | 27.6 | 66.6 | {"2023": -15.1, "2024": 24.8, "2025": 79.8, "2026": 18.2} | -5.9 | 43.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 36.8 | 0.024 | 824.1 | 0.60 | -16.6 | 60.5 | {"2023": 51.5, "2024": 23.8, "2025": 94.6, "2026": -20.9} | -32.9 | 69.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 36.0 | 0.023 | 864.9 | 0.54 | 71.5 | 198.2 | {"2023": 22.0, "2024": 86.3, "2025": 52.6, "2026": -38.6} | -12.1 | 48.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | -3.7 | 37.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 6% (top 94.0%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 56.6%); U7 tm600 L6M -11.4 pts/wk, rank 40% (top 59.7%); P7 tm60 L6M -60.7 pts/wk, rank 10% (top 90.5%); H7 tm60 L6M 28.8 pts/wk, rank 86% (top 13.6%); A7 tm60 L6M -17.2 pts/wk, rank 34% (top 65.7%); O7 tm60 L6M 15.1 pts/wk, rank 77% (top 22.9%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands (native)|TIME | 48.7 | 0.024 | 585.7 | 0.52 | -30.1 | -92.1 | {"2023": 15.7, "2024": -14.5, "2025": 136.2, "2026": 30.5} | -28.5 | 77.2 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 44.9 | 0.041 | 593.4 | 0.64 | -4.7 | 9.1 | {"2023": 71.5, "2024": 6.5, "2025": 122.1, "2026": -9.4} | 2.2 | 42.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| bands|ACTIVITY | 42.7 | 0.027 | 354.7 | 0.56 | 21.7 | -17.3 | {"2023": -8.1, "2024": 56.9, "2025": 76.3, "2026": 2.4} | 27.9 | 14.9 | 1.00 | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 38.6 | 0.023 | 665.0 | 0.57 | 96.6 | 167.5 | {"2023": 17.7, "2024": 67.9, "2025": 52.6, "2026": -6.1} | 1.8 | 36.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|ACTIVITY | 36.8 | 0.024 | 824.1 | 0.60 | -16.6 | 60.5 | {"2023": 51.5, "2024": 23.8, "2025": 94.6, "2026": -20.9} | -25.5 | 62.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 35.1 | 0.022 | 872.8 | 0.54 | 71.5 | 198.2 | {"2023": 17.7, "2024": 84.6, "2025": 52.6, "2026": -38.6} | -17.3 | 52.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| bands (native)|INFORMATION | 34.7 | 0.014 | 767.6 | 0.59 | -59.0 | 113.6 | {"2023": 74.7, "2024": 1.8, "2025": 118.8, "2026": -38.7} | -15.4 | 50.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|PRICE | 34.6 | 0.025 | 757.2 | 0.59 | 69.2 | 138.5 | {"2023": 80.3, "2024": -63.7, "2025": 116.1, "2026": 39.9} | -17.7 | 52.3 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | 6.4 | 26.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|TIME | 28.3 | 0.015 | 845.5 | 0.52 | 77.8 | -68.9 | {"2023": 10.2, "2024": -24.8, "2025": 48.7, "2026": 72.6} | 1.4 | 26.8 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | sym15u | both | 8704 | 3814 | 509 | 1.00 | 2 / -2012 / -295 / 1.00 | {"2023": -91.0, "2024": -1608.0, "2025": 3335.0, "2026": 10363.0} |
| 2 | dib_700 | bands.bands_bollinger.break | {"n": 14, "k": 1.5} | asym20u/10u | both | 8440 | 3980 | 1152 | 0.60 | 5 / -950 / 759 / 1.00 | {"2023": -1554.0, "2024": 596.0, "2025": 771.0, "2026": 6996.0} |
| 3 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym20u/10u | both | 8284 | 2906 | 505 | 1.00 | 5 / 378 / 3088 / 1.00 | {"2023": -852.0, "2024": -683.0, "2025": 2764.0, "2026": 7588.0} |
| 4 | swing_atr_0.1 | tape.tape_speed.follow_native | {"f": 3.0, "L": 3600} | sym15u | both | 8142 | 2340 | 562 | 1.00 | 5 / -371 / 1825 / 1.00 | {"2023": -2474.0, "2024": -2255.0, "2025": 763.0, "2026": 10386.0} |
| 5 | mrenko_14 | book.book_sweep.cnt_fade | {"thr": 1} | plain60/60 | both | 8102 | 4824 | 1744 | 1.00 | 2 / -2743 / -2138 / 1.00 | {"2023": 369.0, "2024": -2136.0, "2025": -998.0, "2026": 6430.0} |
| 6 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | sym30u | both | 8082 | 2155 | 480 | 1.00 | 5 / 602 / 1633 / 1.00 | {"2023": 547.0, "2024": 474.0, "2025": 3963.0, "2026": 8386.0} |
| 7 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym15u/30u | both | 8038 | 3705 | 499 | 1.00 | 5 / 704 / 3235 / 1.00 | {"2023": 16.0, "2024": 1506.0, "2025": 4489.0, "2026": 6565.0} |
| 8 | renko_10 | levels.levels_round.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 8023 | 656 | 657 | 0.67 | 5 / -146 / 2906 / 1.00 | {"2023": -600.0, "2024": -3119.0, "2025": -4002.0, "2026": 8822.0} |
| 9 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym15u | both | 8013 | 3680 | 500 | 1.00 | 5 / 677 / 3228 / 1.00 | {"2023": -200.0, "2024": 1750.0, "2025": 4356.0, "2026": 6540.0} |
| 10 | vsess_450 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | asym15u/30u | both | 7960 | 3412 | 531 | 0.83 | 5 / -1909 / 1527 / 1.00 | {"2023": -1290.0, "2024": 1149.0, "2025": -12.0, "2026": 9238.0} |
| 11 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym10u/20u | both | 7943 | 3967 | 504 | 1.00 | 5 / 766 / 3407 / 1.00 | {"2023": 648.0, "2024": 1861.0, "2025": 5118.0, "2026": 6144.0} |
| 12 | vol_350 | levels.levels_round.break | {"n": 3, "k": 0.5} | sym8u | both | 7909 | 2632 | 645 | 1.00 | 5 / -866 / 424 / 1.00 | {"2023": -295.0, "2024": -2844.0, "2025": 582.0, "2026": 6211.0} |
| 13 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym30u | both | 7895 | 3566 | 499 | 1.00 | 5 / 707 / 3316 / 1.00 | {"2023": -294.0, "2024": 898.0, "2025": 4173.0, "2026": 6422.0} |
| 14 | rng_14 | structure.structure_libpattern.pin | {"k": 2.0, "filt": 0} | asym20u/10u | both | 7856 | 1051 | 651 | 0.50 | 5 / -794 / 236 / 1.00 | {"2023": 229.0, "2024": 581.0, "2025": -3440.0, "2026": 2714.0} |
| 15 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | sym15u | both | 7764 | 2031 | 485 | 1.00 | 5 / 647 / 1691 / 1.00 | {"2023": 100.0, "2024": 1062.0, "2025": 4709.0, "2026": 8127.0} |
| 16 | vol_350 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | sym30u | both | 7714 | 4377 | 491 | 1.00 | 5 / -835 / 1210 / 1.00 | {"2023": 210.0, "2024": 678.0, "2025": 6774.0, "2026": 7589.0} |
| 17 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | asym15u/30u | both | 7709 | 1976 | 483 | 1.00 | 5 / 675 / 1781 / 1.00 | {"2023": 487.0, "2024": 1185.0, "2025": 4743.0, "2026": 8084.0} |
| 18 | vol_350 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym30u | both | 7696 | 4091 | 488 | 1.00 | 5 / -185 / 4832 / 1.00 | {"2023": 513.0, "2024": -317.0, "2025": 6915.0, "2026": 6928.0} |
| 19 | tm20 | trend.trend_macd.hist_turn_native | {"len": 12, "width": 0.01} | sym30u | both | 7594 | 3098 | 518 | 0.83 | 5 / -992 / 642 / 1.00 | {"2023": -1680.0, "2024": -205.0, "2025": 4683.0, "2026": 4457.0} |
| 20 | tm20 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym30u | both | 7594 | 3098 | 518 | 0.83 | 5 / -498 / 887 / 1.00 | {"2023": -1680.0, "2024": -205.0, "2025": 4683.0, "2026": 4457.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -35.0 | -0.021 | 2395.0 | 0.41 | 44.8 | 69.9 | -2.4 | 2.7 | -32.6 | 0.00 | 5.7 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -30.0 | -0.015 | 2163.6 | 0.43 | 44.8 | 69.9 | -15.3 | -10.4 | -14.7 | 0.00 | 6.5 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -7.9 [0.8; 0.50] | 3.1 [17.7; 1.00] | 21.5 [45.2; 1.00] | -19.9 [-8.1; 0.50] |
| bands (native) | 22.6 [28.6; 1.00] | 9.9 [-5.0; 0.00] | -26.0 [2.6; 0.50] | -24.5 [-37.2; 0.00] |
| barnative | -27.0 [-39.7; 0.00] | -6.5 [27.1; 1.00] | -0.0 [19.3; 1.00] | -19.2 [-53.6; 0.00] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -0.8 [-17.8; 0.00] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 28.3 [52.2; 1.00] | n/a (no signals by construction) |
| confluence | 1.2 [15.4; 1.00] | 4.6 [-19.2; 0.00] | 7.8 [28.5; 1.00] | -18.3 [-35.4; 0.00] |
| levels | 2.4 [-13.8; 0.00] | -40.4 [-56.0; 0.00] | -5.0 [5.1; 0.50] | 9.4 [25.3; 1.00] |
| levels (native) | -11.2 [18.1; 1.00] | -11.8 [-21.2; 0.00] | -33.4 [-26.7; 0.00] | -31.2 [-5.8; 0.50] |
| live | -31.3 [-3.4; 0.50] | -33.5 [-36.1; 0.00] | -15.8 [-31.0; 0.00] | -16.8 [-48.1; 0.00] |
| manual | -19.7 [-52.8; 0.00] | -27.7 [-10.3; 0.00] | 15.1 [18.0; 1.00] | -12.8 [-12.1; 0.50] |
| manual (native) | 25.7 [43.0; 0.50] | 7.4 [39.5; 1.00] | 2.4 [-7.8; 0.50] | -32.2 [-14.9; 0.50] |
| momentum | -2.7 [13.1; 1.00] | -7.0 [20.7; 1.00] | 5.5 [41.7; 1.00] | -2.0 [-5.5; 0.50] |
| momentum (native) | 17.0 [27.5; 1.00] | -48.7 [-41.1; 0.00] | 1.9 [-10.5; 0.00] | -9.9 [-5.2; 0.50] |
| pullback | -38.4 [-51.9; 0.00] | -6.7 [-18.9; 0.00] | -32.8 [-4.3; 0.00] | -10.2 [13.2; 1.00] |
| pullback (native) | -6.3 [27.0; 0.50] | -69.1 [-63.1; 0.00] | 2.4 [11.1; 0.50] | -20.2 [1.3; 0.50] |
| structure | 24.5 [32.0; 1.00] | -14.0 [2.0; 0.50] | -47.9 [-42.8; 0.00] | 22.5 [32.0; 1.00] |
| structure (native) | 5.2 [-3.1; 0.50] | -23.2 [-0.2; 0.50] | -28.4 [-17.1; 0.50] | 23.2 [40.9; 1.00] |
| tape | 18.1 [15.0; 1.00] | 31.5 [18.8; 1.00] | -3.9 [-11.9; 0.00] | -37.4 [-8.8; 0.00] |
| tape (native) | -2.3 [33.3; 1.00] | -23.1 [-5.5; 0.50] | 11.9 [15.3; 0.50] | -1.5 [0.4; 0.50] |
| trend | 4.7 [39.6; 1.00] | -23.4 [-6.1; 0.50] | 14.3 [27.2; 1.00] | 17.8 [0.6; 0.50] |
| trend (native) | 29.1 [30.1; 1.00] | -31.6 [-33.1; 0.00] | 4.5 [39.4; 1.00] | 15.2 [32.7; 1.00] |
| xmarket | -15.6 [-3.0; 0.50] | -36.9 [-18.2; 0.00] | -9.1 [-15.2; 0.00] | -16.5 [0.3; 0.50] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| tape|INFORMATION | 31.5 | 0.013 | 422.8 | 0.57 | -42.2 | 22.3 | {"2023": 54.3, "2024": -20.8, "2025": 95.6, "2026": 10.3} | 12.7 | 18.8 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend (native)|ACTIVITY | 29.1 | 0.020 | 301.5 | 0.52 | 35.2 | 33.9 | {"2023": -11.0, "2024": 0.7, "2025": 82.8, "2026": 11.8} | -1.0 | 30.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|PRICE | 28.3 | 0.019 | 468.3 | 0.54 | 10.7 | 56.3 | {"2023": 22.0, "2024": -13.0, "2025": 30.2, "2026": 76.8} | -24.0 | 52.2 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual (native)|ACTIVITY | 25.7 | 0.031 | 366.0 | 0.54 | 48.5 | 6.0 | {"2023": -42.5, "2024": -13.5, "2025": 82.6, "2026": 26.6} | -17.2 | 43.0 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure|ACTIVITY | 24.5 | 0.009 | 788.4 | 0.49 | 102.6 | 189.5 | {"2023": 0.5, "2024": -6.3, "2025": 12.7, "2026": 82.5} | -7.5 | 32.0 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 23.2 | 0.022 | 469.8 | 0.58 | 40.4 | -3.8 | {"2023": 49.7, "2024": 5.8, "2025": -1.5, "2026": 64.7} | -17.6 | 40.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 22.6 | 0.030 | 294.3 | 0.54 | 11.8 | -93.6 | {"2023": 25.8, "2024": 55.4, "2025": 27.5, "2026": -22.9} | -6.0 | 28.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|TIME | 22.5 | 0.020 | 875.2 | 0.57 | 127.0 | 175.4 | {"2023": -36.0, "2024": 18.3, "2025": -26.9, "2026": 104.6} | -9.5 | 32.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 21.5 | 0.015 | 577.8 | 0.47 | -26.7 | 48.7 | {"2023": 75.2, "2024": 23.1, "2025": 50.4, "2026": -31.5} | -23.7 | 45.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| tape|ACTIVITY | 18.1 | 0.000 | 644.9 | 0.58 | -96.9 | 15.9 | {"2023": 37.6, "2024": 43.8, "2025": 26.3, "2026": -28.2} | 3.1 | 15.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 23% (top 77.4%); M7 tm60 L6M -36.8 pts/wk, rank 14% (top 86.1%); U7 tm600 L6M 4.8 pts/wk, rank 61% (top 39.3%); P7 tm60 L6M -35.9 pts/wk, rank 14% (top 85.7%); H7 tm60 L6M -20.1 pts/wk, rank 24% (top 75.6%); A7 tm60 L6M -32.5 pts/wk, rank 16% (top 83.9%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|INFORMATION | 39.9 | 0.019 | 479.9 | 0.53 | 41.1 | 70.9 | {"2023": 69.5, "2024": -0.9, "2025": 118.0, "2026": -13.7} | 24.4 | 15.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend (native)|ACTIVITY | 35.1 | 0.033 | 324.7 | 0.51 | 92.1 | 127.8 | {"2023": -4.9, "2024": -7.8, "2025": 79.5, "2026": 46.0} | -5.6 | 40.7 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| momentum (native)|ACTIVITY | 31.3 | 0.030 | 380.0 | 0.62 | 44.5 | 111.1 | {"2023": 31.0, "2024": 31.7, "2025": 11.6, "2026": 54.2} | -15.1 | 46.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 25.9 | 0.020 | 445.9 | 0.58 | 23.9 | 143.3 | {"2023": -13.8, "2024": 23.1, "2025": 26.3, "2026": 41.6} | -44.8 | 70.8 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 25.0 | 0.032 | 255.1 | 0.56 | 11.8 | -93.6 | {"2023": 25.8, "2024": 55.4, "2025": 27.5, "2026": -14.3} | -2.8 | 27.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|TIME | 23.9 | 0.023 | 538.1 | 0.56 | 7.2 | 147.4 | {"2023": 23.8, "2024": 51.0, "2025": -11.6, "2026": 33.8} | 1.2 | 22.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 22.7 | 0.014 | 692.4 | 0.57 | -6.3 | 83.3 | {"2023": 60.8, "2024": 67.0, "2025": -21.6, "2026": 10.6} | 6.3 | 16.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape|ACTIVITY | 21.5 | 0.003 | 673.5 | 0.58 | -96.9 | 15.9 | {"2023": 37.6, "2024": 61.6, "2025": 19.0, "2026": -28.2} | -1.5 | 23.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual (native)|ACTIVITY | 21.3 | 0.026 | 471.4 | 0.54 | 50.2 | 58.2 | {"2023": -42.5, "2024": -22.8, "2025": 82.6, "2026": 21.4} | -19.9 | 41.2 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| barnative|INFORMATION | 20.2 | 0.017 | 411.1 | 0.49 | 85.3 | 70.8 | {"2023": -16.9, "2024": -15.0, "2025": 49.6, "2026": 38.7} | -51.8 | 72.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.75 | 5 / 991 / 2269 / 1.00 | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 2 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 3 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 4 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym15u/30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 5 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym20u/10u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1266.0, "2024": -1067.0, "2025": 3095.0, "2026": 7745.0} |
| 6 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym10u/20u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1046.0, "2024": -1508.0, "2025": 3102.0, "2026": 7745.0} |
| 7 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym8u | both | 6722 | 2181 | 270 | 1.00 | 5 / 507 / 1497 / 1.00 | {"2023": -1094.0, "2024": -1432.0, "2025": 3159.0, "2026": 7746.0} |
| 8 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 10, "r": 0.6} | plain60/60 | both | 6610 | 590 | 1034 | 1.00 | 5 / -1524 / -356 / 1.00 | {"2023": -294.0, "2024": 1303.0, "2025": 3131.0, "2026": 6965.0} |
| 9 | pnf_20 | levels.levels_sdx_vol1100.lim_mid | {"d": "E", "F": 9, "tgt": "r2"} | sym15u | both | 6337 | 2070 | 275 | 1.00 | 2 / -899 / 240 / 1.00 | {"2023": -998.0, "2024": 71.0, "2025": 1443.0, "2026": 6397.0} |
| 10 | pnf_5 | book.book_ofi.follow | {"L": 100, "z": 1.5} | sym15u | both | 6242 | 3060 | 328 | 1.00 | 2 / 72 / 1067 / 1.00 | {"2023": 1290.0, "2024": -755.0, "2025": -3099.0, "2026": 6638.0} |
| 11 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym15u/30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 419 / 1855 / 1.00 | {"2023": -306.0, "2024": 1499.0, "2025": -1131.0, "2026": 6319.0} |
| 12 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 398 / 1855 / 1.00 | {"2023": -927.0, "2024": 1201.0, "2025": -1574.0, "2026": 6224.0} |
| 13 | tm10 | trend.trend_ma_hma.cross | {"len": 21, "width": 4, "hyst": 0.0} | plain60/60 | both | 6076 | 1146 | 908 | 1.00 | 5 / 182 / 1688 / 1.00 | {"2023": -1233.0, "2024": -756.0, "2025": 2796.0, "2026": 6659.0} |
| 14 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym10u/20u | both | 6072 | 2310 | 311 | 1.00 | 5 / 453 / 1701 / 1.00 | {"2023": -508.0, "2024": 1153.0, "2025": -2178.0, "2026": 6086.0} |
| 15 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | asym15u/30u | both | 6046 | 1396 | 308 | 0.75 | 2 / -607 / 447 / 1.00 | {"2023": -2011.0, "2024": 1321.0, "2025": -300.0, "2026": 5317.0} |
| 16 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym15u | both | 6039 | 2351 | 303 | 1.00 | 5 / 454 / 1959 / 1.00 | {"2023": -93.0, "2024": 1981.0, "2025": -1045.0, "2026": 6138.0} |
| 17 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | sym30u | both | 6039 | 1385 | 308 | 0.75 | 2 / -570 / 414 / 1.00 | {"2023": -2595.0, "2024": 1415.0, "2025": -287.0, "2026": 5508.0} |
| 18 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | sym15u | both | 5981 | 1331 | 310 | 0.75 | 2 / -599 / 334 / 1.00 | {"2023": -1974.0, "2024": 1669.0, "2025": -713.0, "2026": 5066.0} |
| 19 | cusum_28 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym8u | both | 5937 | 1863 | 338 | 1.00 | 5 / 380 / 2239 / 1.00 | {"2023": -46.0, "2024": -2789.0, "2025": 246.0, "2026": 7789.0} |
| 20 | dib_400 | trend.trend_ma_hma.cross_native | {"len": 8, "width": 1.0, "ratio": 3} | asym10u/20u | both | 5902 | 1702 | 1158 | 1.00 | 5 / 534 / 2839 / 1.00 | {"2023": -1702.0, "2024": 1031.0, "2025": -505.0, "2026": 3945.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -14.1 | -0.012 | 1252.8 | 0.49 | -24.4 | -82.2 | -7.3 | -4.7 | -6.8 | 0.00 | 4.7 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -12.2 | -0.010 | 1140.2 | 0.51 | -24.4 | -82.2 | 9.6 | 16.6 | -21.8 | 0.00 | 6.0 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 4.6 [10.9; 1.00] | 20.2 [17.7; 1.00] | 14.2 [24.6; 1.00] | 9.7 [9.5; 1.00] |
| bands (native) | 5.9 [11.4; 1.00] | 4.1 [-20.2; 0.00] | 24.9 [17.1; 1.00] | 8.7 [13.6; 1.00] |
| barnative | 14.8 [32.5; 1.00] | 1.0 [11.7; 1.00] | -0.7 [17.1; 1.00] | -21.6 [-9.8; 0.50] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -20.2 [-1.2; 0.50] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 21.4 [41.7; 1.00] | n/a (no signals by construction) |
| confluence | 21.8 [26.0; 1.00] | -14.7 [-16.9; 0.00] | -9.6 [-13.5; 0.00] | -25.6 [-11.7; 0.50] |
| levels | 7.7 [15.7; 0.50] | -3.4 [-2.1; 0.00] | 8.1 [29.6; 1.00] | -4.0 [13.3; 1.00] |
| levels (native) | 29.4 [75.4; 1.00] | 30.8 [63.2; 1.00] | -5.1 [-14.6; 0.00] | 11.0 [22.9; 1.00] |
| live | 17.0 [38.0; 1.00] | -4.1 [-6.9; 0.00] | 1.7 [3.1; 0.50] | 11.7 [20.3; 1.00] |
| manual | 12.4 [8.8; 1.00] | 3.5 [0.1; 0.50] | -2.3 [6.3; 0.50] | -36.0 [-18.8; 0.50] |
| manual (native) | -2.3 [10.0; 1.00] | -24.2 [-12.9; 0.50] | -16.5 [-1.9; 0.50] | 10.8 [20.5; 1.00] |
| momentum | 16.1 [13.0; 1.00] | 7.1 [7.6; 0.50] | 0.5 [19.4; 0.50] | -3.1 [10.9; 1.00] |
| momentum (native) | -4.1 [-8.3; 0.50] | 3.0 [9.5; 0.50] | 16.8 [15.9; 1.00] | -1.5 [-24.1; 0.00] |
| pullback | 24.0 [32.5; 1.00] | 34.2 [41.8; 1.00] | -13.6 [3.8; 0.50] | -4.4 [-2.0; 0.50] |
| pullback (native) | 25.2 [39.8; 1.00] | -1.1 [-5.6; 0.50] | 12.0 [29.9; 1.00] | -8.8 [15.7; 1.00] |
| structure | -1.2 [-13.0; 0.50] | 31.3 [11.0; 1.00] | -1.7 [-5.0; 0.00] | 2.3 [12.3; 1.00] |
| structure (native) | -10.2 [-6.9; 0.00] | -4.8 [5.6; 0.50] | 11.8 [6.7; 0.50] | -10.3 [-4.1; 0.50] |
| tape | -9.7 [-25.6; 0.00] | -3.1 [-0.8; 0.50] | -19.6 [-1.7; 0.00] | 20.5 [30.3; 1.00] |
| tape (native) | -2.9 [4.1; 0.50] | -22.4 [-22.9; 0.00] | -1.3 [40.0; 1.00] | 0.4 [-8.6; 0.00] |
| trend | -7.7 [2.7; 0.50] | 7.2 [3.1; 0.50] | 19.8 [34.4; 1.00] | 6.9 [14.4; 1.00] |
| trend (native) | -9.8 [1.3; 1.00] | 6.7 [9.4; 1.00] | -16.7 [-12.4; 0.00] | -20.7 [-28.8; 0.00] |
| xmarket | -10.8 [-2.9; 0.50] | -18.7 [-11.4; 0.00] | -33.3 [-39.2; 0.00] | 0.1 [-6.5; 0.50] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pullback|INFORMATION | 34.2 | 0.031 | 142.3 | 0.62 | 63.5 | 9.4 | {"2023": 37.4, "2024": 19.8, "2025": 36.0, "2026": 48.2} | -7.6 | 41.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 31.3 | 0.030 | 203.6 | 0.56 | 106.7 | 56.1 | {"2023": 34.0, "2024": 11.4, "2025": 17.9, "2026": 70.0} | 20.3 | 11.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION | 30.8 | 0.043 | 271.5 | 0.62 | 121.5 | 146.8 | {"2023": 36.1, "2024": 26.9, "2025": 5.2, "2026": 63.9} | -32.5 | 63.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 29.4 | 0.037 | 144.0 | 0.57 | 95.3 | 161.8 | {"2023": 18.2, "2024": 20.4, "2025": 10.8, "2026": 65.8} | -46.0 | 75.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|ACTIVITY | 25.2 | 0.021 | 183.4 | 0.63 | -13.7 | -6.4 | {"2023": 38.4, "2024": 21.0, "2025": 33.9, "2026": 15.6} | -14.6 | 39.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 24.9 | 0.027 | 196.0 | 0.58 | -20.7 | 3.3 | {"2023": -3.3, "2024": 15.6, "2025": 52.7, "2026": 12.1} | 7.9 | 17.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|ACTIVITY | 24.0 | 0.019 | 345.8 | 0.59 | 62.2 | -53.7 | {"2023": 3.2, "2024": 32.4, "2025": 17.3, "2026": 28.5} | -8.5 | 32.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|ACTIVITY | 21.8 | 0.017 | 286.4 | 0.62 | 51.3 | 79.4 | {"2023": 8.6, "2024": 20.2, "2025": 6.0, "2026": 46.7} | -4.1 | 26.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|PRICE | 21.4 | 0.019 | 330.9 | 0.51 | 106.5 | 59.5 | {"2023": -21.2, "2024": -3.3, "2025": 3.5, "2026": 85.1} | -20.3 | 41.7 | 1.00 | {"2023": "RED", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| tape|TIME | 20.5 | 0.014 | 391.8 | 0.51 | 49.3 | -7.6 | {"2023": -12.4, "2024": 14.6, "2025": 38.4, "2026": 16.9} | -9.8 | 30.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 1.8%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.2%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 9.6%); P7 tm60 L6M 66.1 pts/wk, rank 98% (top 2.3%); H7 tm60 L6M 25.1 pts/wk, rank 85% (top 15.3%); A7 tm60 L6M 6.5 pts/wk, rank 65% (top 34.6%). Rank = share of ALL Asia cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands (native)|PRICE | 40.7 | 0.044 | 132.3 | 0.63 | -5.1 | -43.4 | {"2023": -22.5, "2024": 39.8, "2025": 72.0, "2026": 24.8} | -27.5 | 68.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 40.4 | 0.065 | 180.0 | 0.64 | 47.6 | 5.0 | {"2023": 7.1, "2024": 46.0, "2025": 53.9, "2026": 28.4} | -17.9 | 58.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|PRICE | 32.5 | 0.038 | 181.1 | 0.54 | 66.8 | -18.5 | {"2023": -18.2, "2024": 3.9, "2025": 64.1, "2026": 45.2} | -6.8 | 39.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 30.5 | 0.038 | 144.0 | 0.58 | 95.3 | 161.8 | {"2023": 30.6, "2024": 20.4, "2025": 10.8, "2026": 65.8} | -45.2 | 75.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 27.7 | 0.031 | 339.6 | 0.59 | 87.0 | 191.3 | {"2023": 5.3, "2024": 2.9, "2025": 47.3, "2026": 40.7} | -18.8 | 46.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 25.0 | 0.033 | 234.7 | 0.60 | 13.7 | 5.5 | {"2023": 10.0, "2024": 23.2, "2025": 40.6, "2026": 13.6} | 0.6 | 24.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 24.7 | 0.029 | 208.4 | 0.53 | 23.9 | 36.1 | {"2023": 3.4, "2024": 27.9, "2025": 36.5, "2026": 13.8} | -21.4 | 46.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|INFORMATION | 24.6 | 0.035 | 254.0 | 0.60 | 16.9 | 11.1 | {"2023": 28.8, "2024": 19.1, "2025": 8.0, "2026": 49.2} | 0.6 | 23.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|PRICE | 24.1 | 0.023 | 190.1 | 0.52 | -3.0 | -12.0 | {"2023": 17.0, "2024": 35.9, "2025": 4.0, "2026": 36.2} | -19.9 | 44.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|PRICE | 22.8 | 0.027 | 175.9 | 0.57 | 14.1 | 15.1 | {"2023": 21.4, "2024": 11.7, "2025": 38.0, "2026": 18.4} | -7.2 | 30.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | trend.trend_ma_hma.cross | {"len": 13, "width": 3, "hyst": 0.0} | sym30u | both | 7428 | 3631 | 401 | 0.83 | 5 / -601 / 763 / 1.00 | {"2023": 254.0, "2024": -1383.0, "2025": 13.0, "2026": 5811.0} |
| 2 | vol_350 | levels.levels_profile_nodes.break_native | {"n": 2, "k": 0.25} | sym8u | both | 6822 | 2719 | 315 | 1.00 | 2 / -281 / 1340 / 1.00 | {"2023": -337.0, "2024": 673.0, "2025": 881.0, "2026": 6105.0} |
| 3 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym15u | both | 6751 | 922 | 421 | 1.00 | 5 / 1088 / 3330 / 1.00 | {"2023": -77.0, "2024": -853.0, "2025": 1402.0, "2026": 4274.0} |
| 4 | mrenko_14 | book.book_imb.fade_native | {"lv": 1, "thr": 0.35, "sm": 60} | sym15u | both | 6464 | 3197 | 346 | 1.00 | 2 / -625 / 348 / 1.00 | {"2023": -276.0, "2024": 509.0, "2025": -3208.0, "2026": 6787.0} |
| 5 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym8u | both | 6461 | 2123 | 278 | 0.75 | 5 / -868 / -70 / 1.00 | {"2023": -19.0, "2024": -2170.0, "2025": 2679.0, "2026": 6279.0} |
| 6 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | asym15u/30u | both | 6369 | 1236 | 398 | 0.80 | 5 / 904 / 3238 / 1.00 | {"2023": -38.0, "2024": -1031.0, "2025": 1666.0, "2026": 3644.0} |
| 7 | urenko_14 | book.book_pslope.follow_native | {"L": 900, "z": 1.0} | plain60/60 | both | 6194 | 2575 | 1058 | 1.00 | 2 / -1366 / -13 / 1.00 | {"2023": 241.0, "2024": -762.0, "2025": -4489.0, "2026": 6137.0} |
| 8 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 6125 | 2643 | 259 | 1.00 | 5 / -2371 / -215 / 1.00 | {"2023": -66.0, "2024": 51.0, "2025": -560.0, "2026": 6208.0} |
| 9 | vsess_120 | trend.trend_ma_t3.cross_native | {"len": 4, "width": 0.25, "ratio": 3} | sym8u | both | 6113 | 2645 | 424 | 1.00 | 5 / 696 / 2116 / 1.00 | {"2023": -698.0, "2024": -1679.0, "2025": 315.0, "2026": 5443.0} |
| 10 | vsess_600 | trend.trend_ma_hma.cross_native | {"len": 21, "width": 0.25, "ratio": 3} | asym15u/30u | both | 6097 | 2830 | 350 | 1.00 | 5 / 400 / 1654 / 1.00 | {"2023": -317.0, "2024": -2123.0, "2025": -897.0, "2026": 6782.0} |
| 11 | vsess_120 | bands.bands_atrchan.break_ext | {"n": 10, "atr": 14, "k": 2.0} | asym20u/10u | both | 6035 | 2241 | 408 | 0.67 | 2 / -121 / 150 / 1.00 | {"2023": -912.0, "2024": -2332.0, "2025": 99.0, "2026": 3938.0} |
| 12 | dib_400 | trend.trend_ma_hma.price | {"len": 50, "width": 0.25} | sym30u | both | 6019 | 1995 | 402 | 1.00 | 5 / 5 / 4244 / 1.00 | {"2023": 360.0, "2024": -1389.0, "2025": -886.0, "2026": 2708.0} |
| 13 | dib_1200 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | plain60/60 | both | 6002 | 2374 | 888 | 1.00 | 5 / -1154 / 720 / 1.00 | {"2023": -602.0, "2024": 1979.0, "2025": 1051.0, "2026": 7294.0} |
| 14 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym15u/30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 15 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 16 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym15u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -120.0, "2024": -2395.0, "2025": 2657.0, "2026": 5184.0} |
| 17 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym20u/10u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -136.0, "2024": -2419.0, "2025": 3110.0, "2026": 5184.0} |
| 18 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym10u/20u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -114.0, "2024": -2478.0, "2025": 2600.0, "2026": 5184.0} |
| 19 | renko_10 | tape.tape_vpin.follow | {"N": 10, "thr": 0.05} | asym10u/20u | both | 5955 | 2993 | 541 | 1.00 | 5 / -609 / 917 / 1.00 | {"2023": -1003.0, "2024": -585.0, "2025": 1260.0, "2026": 4197.0} |
| 20 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5952 | 2470 | 257 | 1.00 | 5 / -2315 / 162 / 1.00 | {"2023": -103.0, "2024": 35.0, "2025": -467.0, "2026": 6647.0} |

## Exit families (second result column; stage a2, screen-level): flip study and best exit family
Flip study (random 2% sample of pass-1 cells, capped): cells negative on EVERY fixed bracket that become positive with their best of 68 exit specs. A best-of-68 pick is biased upward: read it against the null3 sample / random-entry nulls (null_pctile in the candidates table), not as a gain.
| session | cells | negative on every fixed bracket | flipped positive with an exit family |
|---|---|---|---|
| Asia | 11 | 1 | 1 |
| London | 17 | 4 | 4 |
| NYAM | 17 | 5 | 3 |
| NYPM | 19 | 5 | 4 |
| session | best exit family | cells | mean exit L6M (pts) | mean gain vs best fixed bracket |
|---|---|---|---|---|
| Asia | market target | 161 | 1674 | -1526 |
| Asia | staged | 4 | 1278 | 969 |
| Asia | stop-and-reverse | 3 | 3734 | 961 |
| Asia | structure stop | 1 | 1901 | 693 |
| Asia | time / behaviour | 53 | 2067 | -1047 |
| Asia | trailing | 57 | 2319 | -348 |
| London | market target | 240 | 1267 | -1964 |
| London | staged | 16 | 2187 | -538 |
| London | stop-and-reverse | 2 | 1022 | -1517 |
| London | structure stop | 1 | 422 | 570 |
| London | time / behaviour | 49 | 1344 | -1801 |
| London | trailing | 41 | 1313 | -2278 |
| NYAM | market target | 113 | 1231 | -2055 |
| NYAM | order flow | 2 | 611 | 472 |
| NYAM | staged | 3 | 1982 | 283 |
| NYAM | stop-and-reverse | 9 | 2712 | -1739 |
| NYAM | structure stop | 1 | 2323 | 983 |
| NYAM | time / behaviour | 155 | 1935 | -1615 |
| NYAM | trailing | 22 | 2421 | 305 |
| NYPM | market target | 199 | 1850 | -661 |
| NYPM | order flow | 1 | 76 | -277 |
| NYPM | staged | 8 | 508 | -1885 |
| NYPM | stop-and-reverse | 2 | 3863 | 215 |
| NYPM | structure stop | 2 | 899 | 583 |
| NYPM | time / behaviour | 33 | 1327 | -1643 |
| NYPM | trailing | 20 | 963 | -1503 |
Family 6 (order-flow exits) by component, candidate + live-seven + book/tape cells: best flow spec vs the cell best fixed bracket / best non-flow exit
| session | component | cells | mean best flow-spec L6M (pts) | share beating best fixed bracket | share beating best exit |
|---|---|---|---|---|---|
| Asia | absorb | 67 | -2986 | 0.00 | 0.00 |
| Asia | book | 67 | -3474 | 0.00 | 0.00 |
| Asia | delta | 67 | -3989 | 0.00 | 0.00 |
| Asia | speed | 67 | -3269 | 0.00 | 0.00 |
| Asia | wall | 67 | -3524 | 0.00 | 0.00 |
| London | absorb | 81 | -2812 | 0.00 | 0.00 |
| London | book | 81 | -3329 | 0.00 | 0.00 |
| London | delta | 81 | -3500 | 0.00 | 0.00 |
| London | speed | 81 | -3300 | 0.00 | 0.00 |
| London | wall | 81 | -3576 | 0.00 | 0.00 |
| NYAM | absorb | 95 | -5808 | 0.01 | 0.00 |
| NYAM | book | 95 | -5806 | 0.01 | 0.00 |
| NYAM | delta | 95 | -5951 | 0.02 | 0.00 |
| NYAM | speed | 95 | -5113 | 0.01 | 0.00 |
| NYAM | wall | 95 | -5268 | 0.01 | 0.00 |
| NYPM | absorb | 58 | -5242 | 0.02 | 0.00 |
| NYPM | book | 58 | -5283 | 0.00 | 0.00 |
| NYPM | delta | 59 | -6325 | 0.00 | 0.00 |
| NYPM | speed | 58 | -5323 | 0.00 | 0.00 |
| NYPM | wall | 58 | -5758 | 0.00 | 0.00 |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
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
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.90 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.38 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.89 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.11 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.23 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.98 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.93 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.47 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.14 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.85 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.86 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.87 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.93 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.65 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.42 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.32 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.83 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.90 |  |
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.40 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.11 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.09 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.84 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.84 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.61 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.33 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.79 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.78 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.25 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 0.99 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.95 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.90 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.62 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.57 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.28 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.62 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.57 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.79 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.18 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.16 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.83 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.77 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.06 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.17 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.24 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.05 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.77 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.43 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.05 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.11 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.10 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.45 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.40 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.40 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.56 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.70 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.44 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.10 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.05 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.05 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.10 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.86 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.88 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.76 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.88 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.61 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.34 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.12 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.18 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.78 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.74 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.77 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.70 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.77 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.37 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.33 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.23 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.03 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.84 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.17 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.06 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.14 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.21 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.28 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.79 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.16 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.61 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.32 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.68 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.25 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.32 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.14 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.06 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.10 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.22 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.13 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.24 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.24 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.49 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.27 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.60 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.16 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.14 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.09 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.29 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.58 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell vsess_600 trend.trend_ma_hma.cross sym8u L6M 235.4 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell pnf_5 book.book_cancel.ratio_follow sym15u L6M 334.8 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell dib_2000 barnative.barnative_speed.burst_fade plain60/60 L6M 269.0 pts/wk vs weak baselines K7 -22.5
## LEVEL triggers per session (supply/demand first, then Fibonacci, pivots, swing S/R, level stack, others): best cell per (module, variant) over all bar rows / parameters / brackets, last 26 weeks, >= 30 trades, in-sample pick: a LEAD needs the candidates-table nulls
### London (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 17 | -252 | -206 | -351 | 1 | 24 |
| sd5 | break_native | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 52 | -252 | -206 | -351 | 1 | 24 |
| sdx15 | break | pnf_7 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 124 | 2051 | 550 | -568 | -626 | 1846 | 1 | 24 |
| sdx15 | lim_mid | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 293 | 1940 | 403 | 378 | 297 | 1850 | 1 | 24 |
| sdx15 | lim_prox | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 154 | 1484 | -582 | 1063 | 2672 | 1876 | 1 | 24 |
| sdx15 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / long | 139 | 1135 | -239 | -282 | 1270 | 1568 | 1 | 24 |
| sdx15 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / both | 174 | 950 | -225 | 789 | 232 | 1321 | 1 | 24 |
| sdx15 | rej_native | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 1444 | -1063 | -311 | 1126 | 240 | 1 | 24 |
| sdx15 | rej_zone | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 172 | 1391 | -373 | -860 | 1022 | 1632 | 1 | 24 |
| sdx15 | retest | pnf_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 61 | 1279 | -175 | -146 | -740 | 1080 | 1 | 24 |
| sdx3 | break | urenko_28 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 224 | 2386 | -172 | 129 | -928 | 2633 | 1 | 24 |
| sdx3 | lim_mid | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 341 | 3233 | -657 | 374 | -3030 | 2695 | 1 | 24 |
| sdx3 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 358 | 4320 | 49 | 1608 | -1461 | 3654 | 1 | 24 |
| sdx3 | rej | urenko_10 | {"d": "B", "F": 9, "tol": 0.5} | sym15u / both | 161 | 1505 | -172 | -1100 | -778 | 1381 | 1 | 24 |
| sdx3 | rej_flow | wrenko_20 | {"d": "B", "F": 9} | sym15u / both | 71 | 1238 | -32 | -410 | -333 | 1105 | 1 | 24 |
| sdx3 | rej_native | urenko_20 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 440 | 3124 | 207 | 1913 | 1133 | 4130 | 1 | 24 |
| sdx3 | rej_zone | urenko_10 | {"d": "B", "F": 9, "tgt": "opp"} | sym15u / both | 151 | 2671 | -57 | -178 | -380 | 2466 | 1 | 24 |
| sdx3 | retest | mrenko_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 195 | 1881 | -279 | 106 | 782 | 2331 | 1 | 24 |
| sdx30 | break | pnf_40 | {"d": "A", "F": 9, "n": 1} | plain60/60 / both | 51 | 1087 | -169 | -649 | 515 | 1209 | 1 | 24 |
| sdx30 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 106 | 1410 | -99 | 693 | 319 | 1537 | 1 | 24 |
| sdx30 | lim_prox | pnf_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 85 | 1477 | 301 | 652 | 610 | 2400 | 1 | 24 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 82 | 661 | 617 | 642 | 504 | -21 | 1 | 24 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 31 | 633 | -473 | 306 | 239 | 176 | 1 | 24 |
| sdx30 | rej_native | wrenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 130 | 1272 | 694 | 24 | -42 | 1661 | 1 | 24 |
| sdx30 | rej_zone | pnf_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 45 | 868 | -374 | -336 | -424 | -272 | 1 | 24 |
| sdx30 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 30 | 570 | 110 | -6 | 144 | 250 | 1 | 24 |
| sdx5 | break | urenko_14 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 179 | 3068 | 197 | 1069 | 1759 | 2498 | 1 | 24 |
| sdx5 | lim_mid | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 697 | 1580 | 834 | 553 | -128 | -534 | 1 | 24 |
| sdx5 | lim_prox | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 240 | 2314 | -320 | 761 | -242 | 2457 | 1 | 24 |
| sdx5 | rej | urenko_20 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 127 | 1430 | 615 | -542 | 1687 | 1474 | 1 | 24 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 76 | 1086 | -347 | -317 | 939 | 771 | 1 | 24 |
| sdx5 | rej_native | wrenko_14 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 303 | 1566 | -324 | -1800 | 1511 | 1505 | 1 | 24 |
| sdx5 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 286 | 1266 | -459 | -56 | -667 | 203 | 1 | 24 |
| sdx5 | retest | pnf_5 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 127 | 2271 | -363 | -987 | -544 | 978 | 1 | 24 |
| sdx60 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 31 | 1222 | -351 | -320 | 116 | 1749 | 1 | 24 |
| sdx60 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 151 | 1182 | 300 | 504 | -771 | 696 | 1 | 24 |
| sdx60 | lim_prox | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 3080 | 290 | 236 | -323 | 3089 | 1 | 24 |
| sdx60 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 64 | 538 | -208 | -141 | 111 | 796 | 1 | 24 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 57 | -103 | -459 | 284 | -944 | 100 | 1 | 24 |
| sdx60 | rej_native | pnf_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 24 |
| sdx60 | rej_zone | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 24 |
| sdx_renko28 | break | wrenko_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 126 | 1608 | -8 | -1039 | 743 | 2957 | 1 | 24 |
| sdx_renko28 | lim_mid | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 677 | 2013 | -1189 | 1711 | 2202 | 2157 | 1 | 24 |
| sdx_renko28 | lim_prox | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 737 | 2430 | -1250 | 1465 | 2287 | 2880 | 1 | 24 |
| sdx_renko28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 1095 | 778 | -472 | 371 | -403 | 1 | 24 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "B", "F": 0} | plain60/60 / both | 37 | 445 | -26 | -150 | 326 | -29 | 1 | 24 |
| sdx_renko28 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 24 |
| sdx_renko28 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 24 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 85 | 1772 | -155 | -1444 | -732 | 1006 | 1 | 24 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 24 |
| sdx_rng28 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 261 | 3467 | -998 | 2482 | -838 | 2583 | 1 | 24 |
| sdx_rng28 | lim_prox | wrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 281 | 2565 | -697 | 820 | 191 | 5046 | 1 | 24 |
| sdx_rng28 | rej | pnf_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 859 | 247 | 1730 | -29 | 619 | 1 | 24 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / both | 166 | 1446 | 811 | -32 | 1520 | 715 | 1 | 24 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 24 |
| sdx_rng28 | rej_zone | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 24 |
| sdx_rng28 | retest | pnf_7 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 235 | 2538 | 635 | -1058 | -796 | 2576 | 1 | 24 |
| sdx_vol1100 | break | mrenko_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 179 | 2316 | -308 | 241 | -398 | 3305 | 1 | 24 |
| sdx_vol1100 | lim_mid | pnf_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 252 | 2375 | 722 | -434 | -217 | 3604 | 1 | 24 |
| sdx_vol1100 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 629 | 2059 | 121 | 696 | 1402 | 2119 | 1 | 24 |
| sdx_vol1100 | rej | wrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / short | 191 | 1256 | -14 | -1102 | 1114 | 1803 | 1 | 24 |
| sdx_vol1100 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / short | 57 | 887 | -67 | -326 | 37 | 2097 | 1 | 24 |
| sdx_vol1100 | rej_native | pnf_28 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 118 | 1632 | -355 | -568 | -842 | 366 | 1 | 24 |
| sdx_vol1100 | rej_zone | urenko_80 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 63 | 1543 | 227 | -560 | -510 | 2373 | 1 | 24 |
| sdx_vol1100 | retest | urenko_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 107 | 1285 | -488 | -967 | -408 | 1984 | 1 | 24 |
| fib15 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 241 | 2860 | -519 | -873 | -1089 | 3637 | 1 | 23 |
| fib15 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 2666 | 269 | -729 | -750 | 5804 | 1 | 23 |
| fib15 | false_break | urenko_56 | {"M": 1, "k": 0.0} | sym15u / both | 219 | 2020 | 245 | -209 | -1136 | 2072 | 1 | 23 |
| fib15 | false_break_native | urenko_56 | {"M": 1, "k": 0.0} | sym15u / both | 219 | 2020 | 220 | -209 | -1136 | 2072 | 1 | 23 |
| fib15 | pullback | wrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / long | 166 | 1233 | -351 | -828 | -503 | 891 | 1 | 23 |
| fib15 | pullback_native | pnf_14 | {"tol": 0.5, "conf": "body"} | sym15u / short | 73 | 1363 | 31 | -784 | 210 | 817 | 1 | 23 |
| fib15 | reject | urenko_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 94 | 2126 | -143 | -185 | -196 | 2077 | 1 | 23 |
| fib15 | reject_native | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 249 | 2516 | -870 | 1390 | 290 | 3091 | 1 | 23 |
| fib15 | retest | urenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 232 | 2390 | 111 | 994 | -1786 | 746 | 1 | 23 |
| fib15 | retest_native | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 238 | 2301 | -543 | 1428 | -1050 | 277 | 1 | 23 |
| fib5 | break | urenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 643 | 1853 | -212 | -891 | -211 | 2141 | 1 | 23 |
| fib5 | break_native | pnf_20 | {"n": 3, "k": 0.5} | sym15u / both | 159 | 2270 | 592 | -531 | -1023 | 2480 | 1 | 23 |
| fib5 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 229 | 2933 | 320 | 22 | -1965 | 3455 | 1 | 23 |
| fib5 | false_break_native | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 229 | 2665 | 397 | 318 | -2015 | 3133 | 1 | 23 |
| fib5 | pullback | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 194 | 1590 | 1243 | 113 | 223 | 1728 | 1 | 23 |
| fib5 | pullback_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 519 | 1074 | -607 | -1213 | -394 | 5 | 1 | 23 |
| fib5 | reject | urenko_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 243 | 2344 | 186 | -2299 | -368 | 3117 | 1 | 23 |
| fib5 | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 2128 | -618 | 172 | -2575 | 2937 | 1 | 23 |
| fib5 | retest | urenko_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 525 | 2243 | 323 | 944 | -1709 | 1936 | 1 | 23 |
| fib5 | retest_native | urenko_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 540 | 2451 | 118 | 599 | -9 | 2167 | 1 | 23 |
| fib60 | break | lbrk_3_40 | {"n": 3, "k": 0.5} | sym15u / both | 155 | 2547 | 590 | -363 | 148 | 3492 | 1 | 23 |
| fib60 | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 174 | 2096 | 204 | -1070 | -1007 | 3052 | 1 | 23 |
| fib60 | false_break | pnf_5 | {"M": 1, "k": 0.0} | sym15u / both | 211 | 2093 | 1169 | 1016 | -265 | 2313 | 1 | 23 |
| fib60 | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | sym15u / both | 211 | 2093 | 1169 | 1016 | -265 | 2313 | 1 | 23 |
| fib60 | pullback | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / long | 54 | 588 | -291 | -248 | -314 | -281 | 1 | 23 |
| fib60 | pullback_native | lbrk_3_40 | {"tol": 0.5, "conf": "body"} | sym15u / long | 31 | 1022 | -2 | -483 | 421 | 541 | 1 | 23 |
| fib60 | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 337 | 1480 | -226 | 221 | 300 | 334 | 1 | 23 |
| fib60 | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 426 | 1715 | -280 | -2322 | 1147 | 1620 | 1 | 23 |
| fib60 | retest | wrenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 413 | 2240 | -479 | -57 | -921 | 862 | 1 | 23 |
| fib60 | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 153 | 2962 | -326 | -107 | -3206 | 3766 | 1 | 23 |
| fibr_dev | break | urenko_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 661 | 2070 | 291 | 995 | -652 | 1105 | 1 | 23 |
| fibr_dev | break_native | wrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 249 | 2104 | -559 | 311 | -1357 | 2438 | 1 | 23 |
| fibr_dev | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 206 | 1766 | -191 | -536 | -273 | 2063 | 1 | 23 |
| fibr_dev | false_break_native | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 2226 | 169 | -119 | -950 | 3012 | 1 | 23 |
| fibr_dev | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 1779 | -604 | 1725 | -3146 | 1352 | 1 | 23 |
| fibr_dev | reject_native | pnf_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 1943 | 13 | 365 | -532 | 839 | 1 | 23 |
| fibr_dev | retest | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 622 | 2751 | 131 | -652 | -1202 | 838 | 1 | 23 |
| fibr_dev | retest_native | urenko_56 | {"M": 3, "tol": 0.0} | sym15u / both | 165 | 2197 | -163 | -1582 | 52 | 2857 | 1 | 23 |
| fibr_pd | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 211 | 2784 | 1325 | -554 | -802 | 3958 | 1 | 23 |
| fibr_pd | break_native | pnf_5 | {"n": 2, "k": 0.25} | sym15u / both | 207 | 3135 | 51 | 239 | -950 | 2891 | 1 | 23 |
| fibr_pd | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 176 | 1922 | -666 | -75 | -1 | 2455 | 1 | 23 |
| fibr_pd | false_break_native | pnf_28 | {"M": 3, "k": 0.5} | sym15u / both | 174 | 1857 | -580 | 114 | -478 | 2515 | 1 | 23 |
| fibr_pd | reject | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 203 | 2146 | 523 | -1414 | -889 | 2858 | 1 | 23 |
| fibr_pd | reject_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 183 | 1945 | 45 | 613 | 121 | 359 | 1 | 23 |
| fibr_pd | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 160 | 2031 | 749 | 128 | -2083 | 2990 | 1 | 23 |
| fibr_pd | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 1964 | 104 | 326 | -959 | 2262 | 1 | 23 |
| piv_cama | break | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 195 | 2335 | -291 | -367 | -1410 | 3681 | 1 | 23 |
| piv_cama | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 195 | 2335 | -291 | -367 | -1410 | 3681 | 1 | 23 |
| piv_cama | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 194 | 2351 | -1303 | 268 | -1157 | 3534 | 1 | 23 |
| piv_cama | false_break_native | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 194 | 2351 | -1303 | 268 | -1157 | 3534 | 1 | 23 |
| piv_cama | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 1882 | -418 | 222 | -1471 | 1356 | 1 | 23 |
| piv_cama | reject_native | pnf_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 78 | 1807 | -599 | -49 | -1285 | 2017 | 1 | 23 |
| piv_cama | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / both | 194 | 2197 | 185 | 605 | -1236 | 2130 | 1 | 23 |
| piv_cama | retest_native | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 223 | 2299 | -303 | 579 | -2265 | 871 | 1 | 23 |
| piv_floor | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 410 | -1452 | -3038 | 1859 | 1 | 23 |
| piv_floor | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 190 | 2685 | -366 | 639 | -242 | 3309 | 1 | 23 |
| piv_floor | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 23 |
| piv_floor | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 23 |
| piv_floor | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / long | 48 | 1156 | 133 | 855 | 1142 | 2067 | 1 | 23 |
| piv_floor | reject_native | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 205 | 1537 | 16 | 213 | 1463 | 2120 | 1 | 23 |
| piv_floor | retest | mrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 153 | 2191 | 264 | -1091 | -2228 | 4390 | 1 | 23 |
| piv_floor | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 159 | 1982 | 143 | -571 | 862 | 1923 | 1 | 23 |
| piv_wf | break | pnf_20 | {"n": 3, "k": 0.5} | sym15u / both | 153 | 2201 | -128 | -905 | -583 | 1529 | 1 | 23 |
| piv_wf | break_native | urenko_40 | {"n": 3, "k": 0.5} | sym15u / both | 202 | 2880 | -608 | -890 | -364 | 3606 | 1 | 23 |
| piv_wf | false_break | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 205 | 2139 | -460 | -1925 | -1030 | 1587 | 1 | 23 |
| piv_wf | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 200 | 2228 | -580 | -1416 | -201 | 1188 | 1 | 23 |
| piv_wf | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 147 | 1472 | 651 | 362 | -430 | 1487 | 1 | 23 |
| piv_wf | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 224 | 2546 | 763 | 1227 | -1031 | 2405 | 1 | 23 |
| piv_wf | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 200 | 1536 | -328 | -1584 | -929 | 1504 | 1 | 23 |
| piv_wf | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 200 | 1536 | -328 | -1584 | -929 | 1504 | 1 | 23 |
| swcluster | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 48 | 1283 | -22 | -150 | 1068 | 1838 | 1 | 24 |
| swcluster | break_native | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 53 | 1226 | -630 | -886 | -738 | -454 | 1 | 24 |
| swcluster | false_break | pnf_28 | {"M": 3, "k": 0.5} | sym15u / both | 67 | 1167 | -139 | -564 | 239 | 509 | 1 | 24 |
| swcluster | false_break_native | pnf_28 | {"M": 3, "k": 0.5} | sym15u / both | 62 | 1394 | -65 | -779 | 261 | 959 | 1 | 24 |
| swcluster | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 49 | 1206 | -348 | -620 | -1218 | -36 | 1 | 24 |
| swcluster | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 52 | 1172 | -1039 | -849 | -847 | 332 | 1 | 24 |
| swcluster | retest | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 39 | 890 | -261 | 184 | 168 | 820 | 1 | 24 |
| swcluster | retest_native | pnf_5 | {"M": 6, "tol": 0.5} | sym15u / both | 47 | 1225 | -187 | 35 | -1003 | 283 | 1 | 24 |
| swsr15 | break | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 229 | 2294 | 97 | -2202 | -2829 | 4155 | 1 | 24 |
| swsr15 | break_native | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 246 | 2638 | 760 | -1321 | -415 | 4383 | 1 | 24 |
| swsr15 | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / long | 94 | 1544 | -158 | 621 | -288 | 2848 | 1 | 24 |
| swsr15 | false_break_native | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 92 | 1864 | -177 | 269 | -551 | 3234 | 1 | 24 |
| swsr15 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 480 | 2378 | -1258 | -508 | 212 | 1830 | 1 | 24 |
| swsr15 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 1894 | -668 | -343 | -2460 | 2004 | 1 | 24 |
| swsr15 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3116 | -742 | -538 | 263 | 2136 | 1 | 24 |
| swsr15 | retest_native | pnf_28 | {"M": 6, "tol": 0.5} | sym15u / both | 188 | 2587 | -36 | 852 | 31 | 1170 | 1 | 24 |
| swsr5 | break | pnf_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 556 | 1879 | -729 | -2654 | -1982 | 1259 | 1 | 24 |
| swsr5 | break_native | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 2084 | -669 | -1018 | 182 | 1811 | 1 | 24 |
| swsr5 | false_break | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 232 | 1987 | -409 | -2 | -1587 | 3188 | 1 | 24 |
| swsr5 | false_break_native | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 229 | 2240 | -772 | -415 | -1219 | 2685 | 1 | 24 |
| swsr5 | reject | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 143 | 1638 | -293 | -1179 | -1318 | 1907 | 1 | 24 |
| swsr5 | reject_native | pnf_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 152 | 1286 | -857 | -273 | -756 | 969 | 1 | 24 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | plain60/60 / both | 529 | 2659 | -716 | -995 | -709 | 3038 | 1 | 24 |
| swsr5 | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 268 | 2360 | 398 | -1263 | -1865 | 3266 | 1 | 24 |
| swsr60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 173 | 2714 | -1019 | -989 | 1889 | 3578 | 1 | 24 |
| swsr60 | break_native | urenko_56 | {"n": 3, "k": 0.5} | sym15u / both | 155 | 1992 | -1274 | -469 | 705 | 2277 | 1 | 24 |
| swsr60 | false_break | pnf_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 182 | 1557 | -946 | -1881 | -885 | 915 | 1 | 24 |
| swsr60 | false_break_native | pnf_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 182 | 1557 | -946 | -1881 | -885 | 915 | 1 | 24 |
| swsr60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 171 | 2075 | -1036 | -2049 | -1412 | 1142 | 1 | 24 |
| swsr60 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 135 | 2627 | 113 | -1386 | -415 | 1768 | 1 | 24 |
| swsr60 | retest | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 151 | 1599 | -190 | -251 | 910 | 2102 | 1 | 24 |
| swsr60 | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 166 | 2367 | -533 | -15 | -85 | 3016 | 1 | 24 |
| stack | break | pnf_7 | {"k": 3, "cw": 1.0} | sym15u / both | 139 | 1640 | 184 | 602 | -1381 | 1134 | 1 | 194 |
| stack | break_native | swing_atr_0.9 | {"k": 2, "cw": 0.5} | sym15u / both | 161 | 2660 | 316 | -1526 | -153 | 2343 | 1 | 194 |
| stack | reject | vsess_120 | {"k": 2, "cw": 0.5} | sym8u / both | 94 | 2473 | 270 | -72 | -962 | 2621 | 2 | 194 |
| stack | reject_native | pnf_14 | {"k": 2, "cw": 0.5} | sym15u / both | 194 | 3864 | -615 | -258 | -63 | 4021 | 1 | 194 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 191 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 191 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 191 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 191 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 191 |
| book_walls | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 55 | 1152 | 209 | -451 | 107 | 688 | 1 | 191 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 191 |
| book_walls | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym15u / both | 31 | 948 | -230 | -711 | 334 | 598 | 1 | 191 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 197 | 2357 | -978 | -1528 | -3048 | 1807 | 2 | 193 |
| book_walls_loose | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 2309 | -1415 | 296 | -1880 | 2748 | 2 | 193 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 193 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 193 |
| book_walls_loose | reject | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 170 | 3163 | -1118 | 31 | -1206 | 3714 | 1 | 193 |
| book_walls_loose | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 208 | 3375 | -1082 | -93 | -1302 | 3631 | 1 | 193 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3516 | 15 | -764 | -863 | 4040 | 1 | 193 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1 | 193 |
| channel | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 253 | 3125 | -354 | -1559 | 474 | 4044 | 1 | 23 |
| channel | break_native | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 254 | 2630 | -801 | -738 | -18 | 4060 | 1 | 23 |
| channel | false_break | urenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 258 | 2242 | -546 | 497 | 677 | 2316 | 1 | 23 |
| channel | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2533 | -7 | 626 | -261 | 3312 | 1 | 23 |
| channel | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 251 | 1977 | -1348 | -16 | -541 | -531 | 1 | 23 |
| channel | reject_native | urenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 697 | 1307 | 212 | -74 | 1506 | 1416 | 1 | 23 |
| channel | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 23 |
| channel | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 23 |
| fvg15 | break | pnf_14 | {"n": 3, "k": 0.5} | sym15u / both | 135 | 1564 | -22 | 359 | -595 | -327 | 1 | 24 |
| fvg15 | break_native | wrenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2142 | 699 | 1173 | -2521 | 1701 | 1 | 24 |
| fvg15 | false_break | pnf_10 | {"M": 3, "k": 0.5} | plain60/60 / short | 131 | 1273 | 165 | -386 | -465 | 1786 | 1 | 24 |
| fvg15 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | plain60/60 / short | 130 | 1094 | 257 | -577 | -633 | 1723 | 1 | 24 |
| fvg15 | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 155 | 1666 | -703 | 407 | -195 | 1222 | 1 | 24 |
| fvg15 | reject_native | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 3505 | -133 | 1543 | 430 | 3621 | 1 | 24 |
| fvg15 | retest | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 1682 | -181 | -793 | -565 | 1944 | 1 | 24 |
| fvg15 | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 138 | 2366 | 712 | -208 | -912 | 2048 | 1 | 24 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 24 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 24 |
| fvg5 | false_break | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 24 |
| fvg5 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 24 |
| fvg5 | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 673 | -444 | -1125 | -544 | 2798 | 1 | 24 |
| fvg5 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 421 | 1199 | -460 | 192 | -2061 | 2296 | 1 | 24 |
| fvg5 | retest | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 195 | 1782 | 270 | -472 | -598 | 1260 | 1 | 24 |
| fvg5 | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / long | 63 | 1620 | 237 | -240 | 399 | 2090 | 1 | 24 |
| gaps | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 93 | 2458 | 515 | -722 | -3227 | 1532 | 1 | 194 |
| gaps | break_native | pnf_7 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2868 | -251 | -161 | -3421 | 2136 | 1 | 194 |
| gaps | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 1779 | 18 | -19 | 344 | 2112 | 1 | 194 |
| gaps | false_break_native | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 99 | 1843 | -87 | 76 | 307 | 2380 | 1 | 194 |
| gaps | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 191 | 2035 | -730 | -1775 | 708 | 1690 | 1 | 194 |
| gaps | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 122 | 2154 | -82 | -88 | -822 | 2050 | 1 | 194 |
| gaps | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1584 | -348 | -820 | -994 | 1765 | 1 | 194 |
| gaps | retest_native | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1584 | -348 | -820 | -994 | 1765 | 1 | 194 |
| mmove | break | urenko_56 | {"n": 2, "k": 0.25} | sym15u / both | 187 | 2232 | -39 | -744 | 660 | 3022 | 1 | 24 |
| mmove | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 195 | 1979 | -128 | -737 | -71 | 1252 | 1 | 24 |
| mmove | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2557 | -462 | -577 | -579 | 2977 | 1 | 24 |
| mmove | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 225 | 2897 | -838 | -578 | -949 | 3394 | 1 | 24 |
| mmove | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 316 | 1867 | -56 | -673 | 325 | 1297 | 1 | 24 |
| mmove | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 214 | 3153 | -70 | 1060 | -1089 | 3669 | 1 | 24 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 24 |
| mmove | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 24 |
| ob15 | break | wrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 81 | 1091 | 244 | -107 | 133 | 1385 | 1 | 24 |
| ob15 | break_native | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 65 | 1110 | 244 | -374 | 300 | 2052 | 1 | 24 |
| ob15 | false_break | lbrk_3_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 63 | 585 | -511 | -623 | -325 | 441 | 1 | 24 |
| ob15 | false_break_native | urenko_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 70 | 561 | -549 | -345 | -208 | 682 | 1 | 24 |
| ob15 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 1376 | 323 | -1331 | 1080 | 1930 | 1 | 24 |
| ob15 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 71 | 1184 | 775 | -274 | 61 | 2027 | 1 | 24 |
| ob15 | retest | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 64 | 773 | -222 | -1101 | 556 | 1452 | 1 | 24 |
| ob15 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 87 | 1197 | 155 | -638 | 61 | 1172 | 1 | 24 |
| ob5 | break | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 201 | 1860 | 462 | 900 | 237 | 1572 | 1 | 24 |
| ob5 | break_native | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 201 | 1860 | 462 | 900 | 237 | 1572 | 1 | 24 |
| ob5 | false_break | pnf_5 | {"M": 3, "k": 0.5} | plain60/60 / both | 200 | 1963 | -56 | 924 | 346 | 1463 | 1 | 24 |
| ob5 | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 201 | 1949 | 74 | 1204 | 655 | 1389 | 1 | 24 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 129 | 1424 | 71 | -876 | -916 | 1490 | 1 | 24 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 | 1981 | -488 | -1059 | -729 | 757 | 1 | 24 |
| ob5 | retest | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 97 | 2215 | -850 | -680 | 932 | 2095 | 1 | 24 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 111 | 2232 | -468 | -959 | 1160 | 2143 | 1 | 24 |
| opens | break | renko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 3946 | 43 | 1332 | 422 | 3112 | 2 | 195 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 195 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 195 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 195 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 195 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 195 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 195 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 195 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1 | 195 |
| prior_day | break_native | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 103 | 2083 | 433 | -525 | -990 | 3127 | 1 | 195 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 2376 | 649 | -33 | -1668 | 3829 | 1 | 195 |
| prior_day | false_break_native | swing_atr_0.1 | {"M": 3, "k": 0.5} | sym15u / both | 126 | 2405 | 621 | -246 | -702 | 3078 | 1 | 195 |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 105 | 1827 | -426 | -804 | -662 | 720 | 1 | 195 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 195 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 1 | 195 |
| prior_day | retest_native | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 191 | 2712 | -110 | -383 | 424 | 2187 | 1 | 195 |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 162 | 2957 | -620 | 59 | -1689 | 2002 | 1 | 194 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 194 |
| profile_nodes | false_break | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 2292 | -55 | -984 | -1066 | 1894 | 1 | 194 |
| profile_nodes | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 208 | 2676 | -200 | -70 | 183 | 1964 | 2 | 194 |
| profile_nodes | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 152 | 2817 | -450 | -1140 | -2494 | 1640 | 1 | 194 |
| profile_nodes | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | sym15u / both | 204 | 2821 | -98 | -360 | 235 | 2346 | 2 | 194 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 194 |
| profile_nodes | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 194 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 1 | 195 |
| profile_va | break_native | renko_28 | {"n": 1, "k": 0.5} | sym8u / both | 143 | 2591 | -66 | -1416 | -848 | 2717 | 2 | 195 |
| profile_va | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 120 | 2493 | -419 | -437 | -1179 | 2786 | 1 | 195 |
| profile_va | false_break_native | tm30 | {"M": 2, "k": 0.5} | sym15u / both | 162 | 2584 | 299 | -691 | -241 | 3689 | 1 | 195 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 195 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 195 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym15u / both | 133 | 3198 | 93 | -1886 | -354 | 2602 | 1 | 195 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 195 |
| round | break | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 195 |
| round | break_native | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 195 |
| round | false_break | pasl_10 | {"M": 3, "k": 0.5} | plain60/60 / both | 717 | 3076 | -134 | 387 | -1885 | 3447 | 1 | 195 |
| round | false_break_native | dchg_112 | {"M": 2, "k": 0.5} | sym15u / both | 166 | 3286 | 139 | -661 | -1168 | 2614 | 1 | 195 |
| round | reject | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 405 | 3731 | -1516 | 737 | 448 | 5872 | 1 | 195 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 195 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 195 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 195 |
| session_hl | break | pasl_56 | {"n": 1, "k": 0.0} | sym15u / both | 139 | 1771 | -1102 | -336 | -292 | 2220 | 1 | 191 |
| session_hl | break_native | pasl_20 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2654 | -107 | 389 | -378 | 3494 | 1 | 191 |
| session_hl | false_break | renko_14 | {"M": 2, "k": 0.5} | asym20u/10u / both | 130 | 1640 | -516 | 85 | -1030 | 1483 | 2 | 191 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 191 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 191 |
| session_hl | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 1805 | -162 | -987 | -1228 | -754 | 1 | 191 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 191 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 1 | 191 |
| trendline | break | mrenko_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 490 | 2957 | -338 | -167 | -927 | 697 | 1 | 24 |
| trendline | break_native | mrenko_14 | {"n": 2, "k": 0.25} | sym15u / both | 234 | 3004 | 8 | 371 | -320 | 5564 | 1 | 24 |
| trendline | false_break | mrenko_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 493 | 1774 | 0 | -830 | 1115 | -292 | 1 | 24 |
| trendline | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | plain60/60 / long | 285 | 1884 | 342 | -178 | 159 | 1221 | 1 | 24 |
| trendline | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 24 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 24 |
| trendline | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 225 | 2709 | 329 | -350 | 447 | 2557 | 1 | 24 |
| trendline | retest_native | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 220 | 3008 | -48 | -1940 | 1275 | 1937 | 1 | 24 |
| uw_dp | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 195 |
| uw_dp | break_native | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 195 |
| uw_dp | false_break | dchg_40 | {"M": 2, "k": 0.5} | sym15u / both | 109 | 2734 | 0 | 0 | 530 | 3624 | 1 | 195 |
| uw_dp | false_break_native | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 195 |
| uw_dp | reject | vsess_30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 1652 | 0 | 0 | 311 | 1135 | 1 | 195 |
| uw_dp | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 122 | 2086 | 0 | 0 | -468 | 1673 | 1 | 195 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 195 |
| uw_dp | retest_native | dchg_40 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2424 | 0 | 0 | 561 | 1869 | 1 | 195 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1 | 194 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 194 |
| uw_ndx | false_break | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 194 |
| uw_ndx | false_break_native | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 194 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 194 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 194 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 194 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 194 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 194 |
| uw_qqq | break_native | renko_20 | {"n": 2, "k": 0.0} | sym8u / both | 145 | 2846 | 0 | 48 | 263 | 2703 | 2 | 194 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 194 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 194 |
| uw_qqq | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 116 | 2612 | 0 | 241 | -787 | -337 | 1 | 194 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 194 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 194 |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1 | 194 |
| vwap | break | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 5484 | 276 | -1123 | -2301 | 6752 | 2 | 194 |
| vwap | break_native | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 227 | 5738 | 534 | -1080 | -3184 | 7299 | 2 | 194 |
| vwap | false_break | dchg_56 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2837 | 298 | -962 | 1185 | 2960 | 1 | 194 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 194 |
| vwap | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 248 | 4751 | -37 | -1718 | 768 | 7179 | 2 | 194 |
| vwap | reject_native | cdr_100 | {"tol": 0.5, "conf": "body"} | sym8u / both | 233 | 5846 | 667 | 1147 | -135 | 5737 | 2 | 194 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 194 |
| vwap | retest_native | cdr_100 | {"M": 10, "tol": 0.5} | sym8u / both | 218 | 4634 | 959 | 362 | -947 | 5800 | 2 | 194 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 193 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 193 |
| vwap_bands | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 411 | 2275 | -995 | -112 | -2179 | 2949 | 2 | 193 |
| vwap_bands | false_break_native | rng_14 | {"M": 1, "k": 0.5} | plain60/60 / both | 659 | 2315 | -458 | -1886 | -2589 | 2706 | 2 | 193 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 193 |
| vwap_bands | reject_native | dib_1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 280 | 3027 | 61 | -795 | 419 | 5272 | 1 | 193 |
| vwap_bands | retest | drb_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 684 | 3403 | 537 | -777 | -29 | 2793 | 1 | 193 |
| vwap_bands | retest_native | vsess_30 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 3675 | 581 | -1198 | -2832 | 5778 | 1 | 193 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 1 | 195 |
| week_month | break_native | swing_atr_0.25 | {"n": 2, "k": 0.25} | sym15u / both | 43 | 1508 | -111 | -183 | -1226 | 1563 | 1 | 195 |
| week_month | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 195 |
| week_month | false_break_native | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 195 |
| week_month | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 38 | 1618 | 133 | -162 | -2232 | 2609 | 1 | 195 |
| week_month | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 32 | 1579 | -70 | -765 | -196 | 1671 | 1 | 195 |
| week_month | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 33 | 1229 | 124 | -30 | -141 | 1120 | 1 | 195 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 1 | 195 |
| zones | break | vol_4000 | {"n": 1, "k": 0.5} | sym8u / both | 113 | 2090 | 229 | 143 | 393 | 2008 | 2 | 194 |
| zones | break_native | renko_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 195 | 2650 | -114 | -424 | -736 | 2949 | 2 | 194 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 194 |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 112 | 1825 | -112 | -996 | 314 | 2093 | 2 | 194 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 194 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 194 |
| zones | retest | tib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 128 | 2375 | -1292 | 285 | 258 | 2085 | 1 | 194 |
| zones | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 102 | 2223 | -765 | 332 | -877 | 1559 | 1 | 194 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | wrenko_10 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -218 | -115 | 358 | -542 | -84 | 1 | 24 |
| sd5 | break_native | wrenko_10 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -218 | -115 | 358 | -542 | -84 | 1 | 24 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 1 | 24 |
| sdx15 | break | pnf_56 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 118 | 2174 | -143 | -648 | 1525 | 2167 | 1 | 24 |
| sdx15 | lim_mid | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 333 | 2976 | -2286 | -2403 | -427 | 2983 | 1 | 24 |
| sdx15 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 159 | 2723 | -873 | 389 | 55 | 3666 | 1 | 24 |
| sdx15 | rej | wrenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 119 | 1419 | -959 | 71 | -2822 | 2002 | 1 | 24 |
| sdx15 | rej_flow | wrenko_10 | {"d": "A", "F": 0} | sym15u / both | 58 | 1194 | -483 | 1191 | -1486 | 1139 | 1 | 24 |
| sdx15 | rej_native | urenko_28 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 169 | 1432 | -2118 | -521 | -1352 | 1011 | 1 | 24 |
| sdx15 | rej_zone | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 169 | 1432 | -2118 | -521 | -1352 | 1011 | 1 | 24 |
| sdx15 | retest | pnf_56 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 62 | 1462 | -155 | 589 | 1520 | 2625 | 1 | 24 |
| sdx3 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 368 | 1826 | 1956 | 2152 | 3229 | 1191 | 1 | 24 |
| sdx3 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 182 | 3365 | 26 | 2134 | 1935 | 3244 | 1 | 24 |
| sdx3 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 187 | 3299 | -387 | 1934 | 996 | 2695 | 1 | 24 |
| sdx3 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 475 | 3002 | -2715 | -1978 | -5508 | 1958 | 1 | 24 |
| sdx3 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / long | 156 | 3037 | 6 | 1057 | -3441 | 2950 | 1 | 24 |
| sdx3 | rej_native | mrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 24 |
| sdx3 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 24 |
| sdx3 | retest | pnf_5 | {"d": "A", "M": 6, "tol": 0.5} | plain60/60 / both | 289 | 2176 | 1424 | 475 | 2820 | 848 | 1 | 24 |
| sdx30 | break | pnf_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 79 | 1933 | -372 | 1333 | 866 | 1755 | 1 | 24 |
| sdx30 | lim_mid | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 52 | 1565 | 12 | -897 | 111 | 634 | 1 | 24 |
| sdx30 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 142 | 2308 | -245 | -373 | 1505 | 5248 | 1 | 24 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 73 | 1261 | -467 | -838 | -1738 | 1427 | 1 | 24 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 34 | 1001 | 73 | -979 | -1302 | 1556 | 1 | 24 |
| sdx30 | rej_native | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 82 | 1477 | -181 | -1340 | -1261 | 1609 | 1 | 24 |
| sdx30 | rej_zone | pnf_7 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 43 | 1139 | -691 | -319 | -425 | 642 | 1 | 24 |
| sdx30 | retest | pnf_28 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 35 | 976 | -101 | -1016 | 521 | 952 | 1 | 24 |
| sdx5 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 128 | 2348 | 760 | 872 | 1375 | 1924 | 1 | 24 |
| sdx5 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 4263 | -912 | -271 | 1146 | 4807 | 1 | 24 |
| sdx5 | lim_prox | urenko_80 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 214 | 4370 | 1480 | 714 | 2473 | 2468 | 1 | 24 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 216 | 2627 | -830 | 131 | -3477 | 4401 | 1 | 24 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / both | 319 | 735 | -722 | 565 | 43 | 2367 | 1 | 24 |
| sdx5 | rej_native | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 24 |
| sdx5 | rej_zone | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 24 |
| sdx5 | retest | pnf_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 114 | 2164 | 463 | 1190 | 1731 | 2812 | 1 | 24 |
| sdx60 | break | pnf_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 72 | 1439 | 1041 | 256 | 611 | 1419 | 1 | 24 |
| sdx60 | lim_mid | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 413 | 1413 | -1233 | -23 | -2684 | 345 | 1 | 24 |
| sdx60 | lim_prox | urenko_80 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 209 | 1005 | 76 | 77 | -422 | 1306 | 1 | 24 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 159 | 1224 | -1408 | -491 | -2004 | 1426 | 1 | 24 |
| sdx60 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | plain60/60 / both | 32 | 589 | -294 | -644 | -547 | 980 | 1 | 24 |
| sdx60 | rej_native | urenko_28 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 206 | 1367 | -1146 | -633 | -1693 | 1006 | 1 | 24 |
| sdx60 | rej_zone | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 206 | 1367 | -1146 | -633 | -1693 | 1006 | 1 | 24 |
| sdx_renko28 | break | pnf_56 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 158 | 2617 | -1111 | 1032 | 1543 | 2235 | 1 | 24 |
| sdx_renko28 | lim_mid | pnf_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 187 | 4127 | 224 | 1631 | 220 | 3880 | 1 | 24 |
| sdx_renko28 | lim_prox | pnf_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 188 | 4526 | 216 | 1871 | -67 | 4152 | 1 | 24 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 417 | 2601 | -2519 | -2626 | -4344 | 2070 | 1 | 24 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 202 | 2765 | 740 | -3083 | 894 | 2859 | 1 | 24 |
| sdx_renko28 | rej_native | urenko_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 24 |
| sdx_renko28 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 24 |
| sdx_renko28 | retest | pnf_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 135 | 2994 | -717 | 618 | 233 | 2746 | 1 | 24 |
| sdx_rng28 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 471 | 3029 | 2347 | 3513 | 2750 | 4662 | 1 | 24 |
| sdx_rng28 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 536 | 3929 | 2918 | 3446 | -166 | 3793 | 1 | 24 |
| sdx_rng28 | lim_prox | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 493 | 5342 | 520 | 1267 | -40 | 7530 | 1 | 24 |
| sdx_rng28 | rej | mrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 504 | 2856 | -984 | -1842 | -5463 | 2791 | 1 | 24 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / long | 172 | 2052 | 2014 | -466 | -281 | 3800 | 1 | 24 |
| sdx_rng28 | rej_native | mrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 1016 | 2817 | 597 | 198 | -4637 | 2826 | 1 | 24 |
| sdx_rng28 | rej_zone | urenko_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 249 | 3235 | -3010 | 1100 | -3061 | 2194 | 1 | 24 |
| sdx_rng28 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 461 | 2861 | 1885 | 77 | 4582 | 2654 | 1 | 24 |
| sdx_vol1100 | break | pnf_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 101 | 2033 | 1 | 261 | 1653 | 2027 | 1 | 24 |
| sdx_vol1100 | lim_mid | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1444 | 5146 | -307 | -267 | -7260 | 5686 | 1 | 24 |
| sdx_vol1100 | lim_prox | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1412 | 4616 | 1989 | -3 | -5487 | 5378 | 1 | 24 |
| sdx_vol1100 | rej | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 212 | 3279 | 423 | 1203 | 1461 | 4661 | 1 | 24 |
| sdx_vol1100 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / long | 161 | 1923 | -695 | -1236 | -1274 | 1821 | 1 | 24 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 1195 | 3085 | -168 | -4263 | -5707 | 2907 | 1 | 24 |
| sdx_vol1100 | rej_zone | pnf_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 325 | 3417 | 221 | 1034 | 2864 | 4121 | 1 | 24 |
| sdx_vol1100 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 398 | 4494 | -381 | -1960 | 2674 | 5777 | 1 | 24 |
| fib15 | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 177 | 2959 | -49 | 489 | 2685 | 1451 | 1 | 23 |
| fib15 | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 177 | 2959 | 167 | 489 | 2685 | 1451 | 1 | 23 |
| fib15 | false_break | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 356 | 3289 | -131 | 2456 | 3878 | 2191 | 1 | 23 |
| fib15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 357 | 2838 | 255 | 2166 | 2252 | 1600 | 1 | 23 |
| fib15 | pullback | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / long | 117 | 1946 | 1189 | 228 | -1464 | 2989 | 1 | 23 |
| fib15 | pullback_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / long | 106 | 2608 | 1196 | 45 | -914 | 4367 | 1 | 23 |
| fib15 | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 131 | 1656 | 774 | 915 | -1823 | 2987 | 1 | 23 |
| fib15 | reject_native | pnf_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 265 | 4270 | 864 | -2607 | 5306 | 5333 | 1 | 23 |
| fib15 | retest | urenko_28 | {"M": 3, "tol": 0.0} | sym15u / both | 224 | 2112 | 493 | 711 | -410 | 586 | 1 | 23 |
| fib15 | retest_native | pnf_20 | {"M": 6, "tol": 0.5} | sym15u / both | 315 | 3242 | 486 | 244 | 3836 | 5851 | 1 | 23 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 392 | 4876 | -635 | -1541 | 2534 | 5721 | 1 | 23 |
| fib5 | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 187 | 3101 | 1263 | -128 | 1540 | 1917 | 1 | 23 |
| fib5 | false_break | wrenko_10 | {"M": 1, "k": 0.0} | sym15u / both | 399 | 4750 | -168 | -2587 | 2230 | 3088 | 1 | 23 |
| fib5 | false_break_native | wrenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 394 | 5399 | 68 | -2894 | 1385 | 3042 | 1 | 23 |
| fib5 | pullback | urenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 191 | 1488 | -249 | -1220 | 892 | 1036 | 1 | 23 |
| fib5 | pullback_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 2320 | 692 | 1177 | -653 | 2698 | 1 | 23 |
| fib5 | reject | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 34 | 1877 | -184 | 434 | -161 | 2037 | 1 | 23 |
| fib5 | reject_native | pnf_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 284 | 2753 | -140 | 262 | 1608 | 2820 | 1 | 23 |
| fib5 | retest | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 369 | 4099 | -931 | -806 | 62 | 2123 | 1 | 23 |
| fib5 | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 379 | 3505 | -1724 | -1477 | -1029 | 3463 | 1 | 23 |
| fib60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 302 | 3565 | 654 | 1558 | -1114 | 4562 | 1 | 23 |
| fib60 | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 296 | 3466 | 16 | 15 | 1046 | 4959 | 1 | 23 |
| fib60 | false_break | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 301 | 3933 | 1570 | 2104 | 2305 | 4830 | 1 | 23 |
| fib60 | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 286 | 3959 | 582 | 1959 | 1016 | 3259 | 1 | 23 |
| fib60 | pullback | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 82 | 1289 | -49 | 1805 | -492 | -423 | 1 | 23 |
| fib60 | pullback_native | pnf_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 141 | 1468 | -980 | -49 | -337 | 1601 | 1 | 23 |
| fib60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 297 | 3853 | 197 | -2307 | -1069 | 5413 | 1 | 23 |
| fib60 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 309 | 3595 | -544 | -1575 | -629 | 3065 | 1 | 23 |
| fib60 | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 283 | 4034 | 1024 | 761 | 814 | 3982 | 1 | 23 |
| fib60 | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 350 | 3645 | -129 | 298 | 273 | 3427 | 1 | 23 |
| fibr_dev | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 449 | 3553 | 1785 | -585 | -379 | 4869 | 1 | 23 |
| fibr_dev | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 449 | 3553 | 1785 | -585 | -379 | 4869 | 1 | 23 |
| fibr_dev | false_break | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 433 | 3797 | -853 | 2868 | 6803 | 3615 | 1 | 23 |
| fibr_dev | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 439 | 4446 | -854 | 2791 | 5818 | 4817 | 1 | 23 |
| fibr_dev | reject | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 3087 | 936 | 1508 | -135 | 2125 | 1 | 23 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 448 | 4974 | 1168 | 2667 | 817 | 4931 | 1 | 23 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 414 | 5720 | -316 | 1766 | 2350 | 3254 | 1 | 23 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 427 | 4867 | -1061 | -570 | 4293 | 5344 | 1 | 23 |
| fibr_ib | break | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 314 | 2586 | -59 | 1126 | 2764 | 2172 | 1 | 23 |
| fibr_ib | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 324 | 2561 | 214 | 1839 | 2319 | 1672 | 1 | 23 |
| fibr_ib | false_break | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3039 | 2049 | -573 | 1916 | 2034 | 1 | 23 |
| fibr_ib | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3039 | 2049 | -573 | 1916 | 2034 | 1 | 23 |
| fibr_ib | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 236 | 2819 | -468 | 1691 | 261 | 3131 | 1 | 23 |
| fibr_ib | reject_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 316 | 2308 | 510 | 887 | -2498 | 3391 | 1 | 23 |
| fibr_ib | retest | urenko_56 | {"M": 3, "tol": 0.0} | sym15u / both | 143 | 2293 | -1092 | 193 | -591 | 992 | 1 | 23 |
| fibr_ib | retest_native | urenko_56 | {"M": 3, "tol": 0.0} | sym15u / both | 143 | 2293 | -1092 | 193 | -591 | 992 | 1 | 23 |
| fibr_on | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 390 | 3646 | 879 | 2200 | 7144 | 3961 | 1 | 23 |
| fibr_on | break_native | urenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 1053 | 3458 | 2520 | 1667 | 572 | 3735 | 1 | 23 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 383 | 5252 | 1464 | 1013 | 2918 | 7973 | 1 | 23 |
| fibr_on | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 1 | 23 |
| fibr_on | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 376 | 2691 | 1164 | -1169 | 4230 | 2505 | 1 | 23 |
| fibr_on | reject_native | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 376 | 2691 | 1164 | -1169 | 4230 | 2505 | 1 | 23 |
| fibr_on | retest | wrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 344 | 2478 | -924 | -572 | 3641 | 3662 | 1 | 23 |
| fibr_on | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 3227 | 1904 | -823 | -47 | 375 | 1 | 23 |
| fibr_or | break | pnf_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 1079 | 3842 | -257 | -362 | -2255 | 2384 | 1 | 23 |
| fibr_or | break_native | wrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 362 | 4188 | -21 | -1259 | 3570 | 3338 | 1 | 23 |
| fibr_or | false_break | urenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 349 | 3867 | 432 | 1403 | -216 | 2811 | 1 | 23 |
| fibr_or | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 361 | 3626 | -1249 | 2110 | -3711 | 3093 | 1 | 23 |
| fibr_or | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 374 | 3996 | -233 | 328 | 4247 | 4044 | 1 | 23 |
| fibr_or | reject_native | urenko_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 297 | 3199 | 1545 | 2963 | 1056 | 2443 | 1 | 23 |
| fibr_or | retest | pnf_5 | {"M": 6, "tol": 0.5} | sym15u / both | 360 | 3130 | -315 | -373 | -3697 | 270 | 1 | 23 |
| fibr_or | retest_native | pnf_5 | {"M": 6, "tol": 0.5} | sym15u / both | 372 | 4633 | 137 | -1237 | 762 | 2496 | 1 | 23 |
| fibr_pd | break | pnf_7 | {"n": 3, "k": 0.5} | sym15u / both | 373 | 5173 | 19 | -1331 | 2658 | 5625 | 1 | 23 |
| fibr_pd | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 363 | 5381 | -742 | 2469 | 3094 | 4965 | 1 | 23 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 1 | 23 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 1 | 23 |
| fibr_pd | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 23 |
| fibr_pd | reject_native | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 23 |
| fibr_pd | retest | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 23 |
| fibr_pd | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 23 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 357 | 5210 | 1949 | 420 | -2741 | 6204 | 1 | 23 |
| piv_cama | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 379 | 6524 | 489 | 1354 | 649 | 7212 | 1 | 23 |
| piv_cama | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 194 | 3092 | 319 | 526 | 2048 | 2764 | 1 | 23 |
| piv_cama | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 187 | 3276 | 454 | 729 | 1972 | 3605 | 1 | 23 |
| piv_cama | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 369 | 2583 | -1426 | 1370 | 3989 | 2748 | 1 | 23 |
| piv_cama | reject_native | pnf_5 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 1013 | 4236 | 1052 | -2213 | -2797 | 3106 | 1 | 23 |
| piv_cama | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 23 |
| piv_cama | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 23 |
| piv_floor | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3553 | -161 | 488 | 2430 | 2793 | 1 | 23 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 1 | 23 |
| piv_floor | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 186 | 3796 | -476 | 286 | 3151 | 3316 | 1 | 23 |
| piv_floor | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 186 | 3796 | -435 | 286 | 3151 | 3316 | 1 | 23 |
| piv_floor | reject | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 62 | 919 | 1578 | 412 | 964 | 2485 | 1 | 23 |
| piv_floor | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 530 | 2407 | 1631 | 3763 | 519 | 1290 | 1 | 23 |
| piv_floor | retest | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 136 | 3307 | 1674 | 1218 | 2007 | 4474 | 1 | 23 |
| piv_floor | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 3913 | 1673 | 239 | 2389 | 4656 | 1 | 23 |
| piv_wf | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3685 | 42 | 27 | 876 | 2866 | 1 | 23 |
| piv_wf | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3685 | 207 | 27 | 876 | 2866 | 1 | 23 |
| piv_wf | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 185 | 3564 | 45 | 748 | 1031 | 2634 | 1 | 23 |
| piv_wf | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 185 | 3564 | 87 | 748 | 1031 | 2634 | 1 | 23 |
| piv_wf | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 306 | 2772 | -874 | -732 | 1160 | 5492 | 1 | 23 |
| piv_wf | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 404 | 2303 | -833 | 3724 | 3038 | 2931 | 1 | 23 |
| piv_wf | retest | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 269 | 3310 | 1599 | -50 | 2844 | 3725 | 1 | 23 |
| piv_wf | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 323 | 4338 | 1465 | 1240 | 2816 | 3449 | 1 | 23 |
| swcluster | break | urenko_112 | {"n": 3, "k": 0.5} | sym15u / both | 54 | 1306 | 832 | -672 | 48 | 1510 | 1 | 24 |
| swcluster | break_native | pnf_7 | {"n": 1, "k": 0.0} | plain60/60 / both | 204 | 1189 | -400 | 21 | 1130 | 1117 | 1 | 24 |
| swcluster | false_break | pnf_40 | {"M": 1, "k": 0.0} | sym15u / both | 93 | 1551 | -519 | -769 | 385 | 1862 | 1 | 24 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 1 | 24 |
| swcluster | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 78 | 994 | -808 | 727 | -1417 | 573 | 1 | 24 |
| swcluster | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / long | 53 | 1018 | -438 | -981 | -61 | 873 | 1 | 24 |
| swcluster | retest | pnf_28 | {"M": 6, "tol": 0.5} | sym15u / both | 66 | 1269 | 113 | -619 | 775 | 1235 | 1 | 24 |
| swcluster | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 59 | 1166 | -461 | -164 | 10 | 2586 | 1 | 24 |
| swsr15 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 338 | 2943 | 119 | 2375 | 3679 | 5043 | 1 | 24 |
| swsr15 | break_native | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 347 | 3788 | 957 | 2665 | 4333 | 7229 | 1 | 24 |
| swsr15 | false_break | mrenko_10 | {"M": 3, "k": 0.5} | sym15u / both | 445 | 3451 | 1096 | -2477 | -1848 | 470 | 1 | 24 |
| swsr15 | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 856 | 3971 | 760 | 1137 | -923 | 4097 | 1 | 24 |
| swsr15 | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / long | 67 | 2215 | -504 | 1425 | 1878 | 2990 | 1 | 24 |
| swsr15 | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 354 | 3290 | -1693 | 687 | -2566 | 6013 | 1 | 24 |
| swsr15 | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 290 | 5015 | -392 | -944 | 1428 | 4099 | 1 | 24 |
| swsr15 | retest_native | urenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 333 | 4907 | 1503 | -111 | 2647 | 3519 | 1 | 24 |
| swsr5 | break | urenko_40 | {"n": 3, "k": 0.5} | sym15u / both | 406 | 3770 | 1529 | -682 | 1021 | 3574 | 1 | 24 |
| swsr5 | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 427 | 3055 | 1759 | 4038 | 2487 | 3173 | 1 | 24 |
| swsr5 | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 436 | 4795 | 870 | 764 | -2218 | 6844 | 1 | 24 |
| swsr5 | false_break_native | pnf_7 | {"M": 3, "k": 0.5} | sym15u / both | 434 | 5686 | 1598 | -558 | -740 | 8009 | 1 | 24 |
| swsr5 | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 407 | 3165 | -776 | 1166 | 1559 | 3156 | 1 | 24 |
| swsr5 | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 452 | 4120 | -609 | 1554 | 3190 | 5222 | 1 | 24 |
| swsr5 | retest | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 665 | 2200 | 3212 | 5780 | 1 | 24 |
| swsr5 | retest_native | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 691 | 2200 | 3212 | 5780 | 1 | 24 |
| swsr60 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3965 | 36 | 158 | -2380 | 1344 | 1 | 24 |
| swsr60 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 254 | 4303 | 338 | -270 | -2273 | 3058 | 1 | 24 |
| swsr60 | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 290 | 2588 | 1112 | -417 | 1728 | 2743 | 1 | 24 |
| swsr60 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 286 | 2726 | 385 | -291 | 3026 | 3397 | 1 | 24 |
| swsr60 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 240 | 2871 | -893 | -1110 | -691 | 4303 | 1 | 24 |
| swsr60 | reject_native | pnf_7 | {"tol": 0.5, "conf": "body"} | sym15u / both | 207 | 2996 | -223 | 738 | -2958 | 2749 | 1 | 24 |
| swsr60 | retest | wrenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 227 | 2640 | -538 | -208 | 713 | 2633 | 1 | 24 |
| swsr60 | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 235 | 3947 | -295 | 1712 | 542 | 2019 | 1 | 24 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 251 | 5486 | 738 | 818 | 1504 | 1968 | 2 | 193 |
| stack | break_native | rng_80 | {"k": 2, "cw": 2.0} | sym8u / both | 307 | 6590 | -1020 | 397 | 79 | 3936 | 2 | 193 |
| stack | reject | pnf_5 | {"k": 2, "cw": 0.5} | sym15u / both | 152 | 2969 | -1754 | -1412 | -638 | 2326 | 1 | 193 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | asym20u/10u / both | 248 | 3290 | -789 | 971 | -1202 | 4802 | 2 | 193 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 193 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1335 | -822 | 539 | 550 | 1717 | 1 | 193 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 193 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 193 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 193 |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 126 | 1601 | -738 | -637 | 518 | 1605 | 1 | 193 |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1266 | -894 | 749 | 1751 | 1947 | 1 | 193 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 193 |
| channel | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 23 |
| channel | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 23 |
| channel | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 23 |
| channel | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 23 |
| channel | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 401 | 3917 | -208 | 972 | 4672 | 2881 | 1 | 23 |
| channel | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 463 | 4187 | 146 | -2476 | 4036 | 4709 | 1 | 23 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 527 | 5168 | 1396 | -726 | 235 | 2951 | 1 | 23 |
| channel | retest_native | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 537 | 4227 | 646 | 80 | 1390 | 1969 | 1 | 23 |
| fvg15 | break | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 330 | -695 | 1898 | 2097 | 1 | 24 |
| fvg15 | break_native | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 408 | -695 | 1898 | 2097 | 1 | 24 |
| fvg15 | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 63 | 2026 | 106 | -1123 | 207 | 1397 | 1 | 24 |
| fvg15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 177 | 1876 | -479 | -158 | -2188 | 247 | 1 | 24 |
| fvg15 | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 176 | 1407 | -534 | 1658 | -536 | 571 | 1 | 24 |
| fvg15 | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 35 | 1191 | 369 | 46 | 468 | 1129 | 1 | 24 |
| fvg15 | retest | pnf_20 | {"M": 6, "tol": 0.5} | sym15u / both | 109 | 2173 | -724 | 1345 | -1198 | 521 | 1 | 24 |
| fvg15 | retest_native | pnf_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 128 | 1339 | -941 | 369 | -615 | 421 | 1 | 24 |
| fvg5 | break | lbrk_3_40 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2212 | 932 | -1000 | -902 | -520 | 1 | 24 |
| fvg5 | break_native | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 2280 | 649 | 1613 | 1744 | 1553 | 1 | 24 |
| fvg5 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 1913 | -47 | -1966 | 1134 | 1338 | 1 | 24 |
| fvg5 | false_break_native | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 1676 | -1207 | -1321 | 1577 | 1248 | 1 | 24 |
| fvg5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / long | 127 | 1665 | -219 | -553 | -608 | 2318 | 1 | 24 |
| fvg5 | reject_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / long | 103 | 1726 | 744 | 240 | -667 | 2561 | 1 | 24 |
| fvg5 | retest | pnf_14 | {"M": 3, "tol": 0.0} | sym15u / both | 128 | 1413 | -297 | 661 | -848 | 2585 | 1 | 24 |
| fvg5 | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 2329 | -55 | -245 | -934 | 2721 | 1 | 24 |
| gaps | break | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 104 | -1328 | 2128 | 1944 | 1 | 193 |
| gaps | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 142 | -1328 | 2128 | 1944 | 1 | 193 |
| gaps | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -820 | -86 | 2898 | 2982 | 1 | 193 |
| gaps | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -762 | -86 | 2898 | 2982 | 1 | 193 |
| gaps | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 193 |
| gaps | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 193 |
| gaps | retest | swing_pct_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 148 | 2014 | -165 | 197 | -298 | 1531 | 1 | 193 |
| gaps | retest_native | dib_3500 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 2042 | 108 | 1386 | 570 | 1429 | 1 | 193 |
| mmove | break | pnf_5 | {"n": 1, "k": 0.0} | sym15u / both | 334 | 3120 | -172 | -489 | 3589 | 4581 | 1 | 24 |
| mmove | break_native | pnf_5 | {"n": 1, "k": 0.0} | sym15u / both | 334 | 3120 | -172 | -489 | 3589 | 4581 | 1 | 24 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 1 | 24 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 1 | 24 |
| mmove | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 95 | 2790 | 1939 | 398 | 1792 | 3227 | 1 | 24 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / long | 147 | 2318 | 927 | -105 | -528 | 3959 | 1 | 24 |
| mmove | retest | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 248 | 1992 | -427 | 626 | -2425 | 1116 | 1 | 24 |
| mmove | retest_native | urenko_56 | {"M": 6, "tol": 0.5} | sym15u / both | 256 | 2027 | 77 | 1548 | 2539 | 2016 | 1 | 24 |
| ob15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 143 | 2715 | -364 | 1077 | -198 | 2970 | 1 | 24 |
| ob15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 144 | 2579 | -490 | 437 | 440 | 3050 | 1 | 24 |
| ob15 | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 105 | 1511 | 348 | -1062 | 1449 | 331 | 1 | 24 |
| ob15 | false_break_native | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 1440 | 1095 | -475 | 1708 | 112 | 1 | 24 |
| ob15 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 128 | 1612 | -55 | -833 | 1139 | 1595 | 1 | 24 |
| ob15 | reject_native | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2140 | 289 | -157 | 1697 | 330 | 1 | 24 |
| ob15 | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 110 | 2538 | -231 | 102 | 2014 | 2666 | 1 | 24 |
| ob15 | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | plain60/60 / both | 200 | 2091 | 649 | -1044 | 32 | 1538 | 1 | 24 |
| ob5 | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 151 | 2619 | 566 | 93 | -1836 | 1111 | 1 | 24 |
| ob5 | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 151 | 2619 | 566 | 93 | -1836 | 1111 | 1 | 24 |
| ob5 | false_break | urenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 164 | 2385 | 415 | 203 | 408 | 1682 | 1 | 24 |
| ob5 | false_break_native | urenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 164 | 2385 | 566 | 295 | 168 | 1682 | 1 | 24 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 139 | 1592 | 443 | -1429 | -219 | 1037 | 1 | 24 |
| ob5 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 140 | 2232 | -724 | -50 | -411 | 97 | 1 | 24 |
| ob5 | retest | pnf_5 | {"M": 6, "tol": 0.5} | sym15u / both | 138 | 2263 | -524 | -1280 | 584 | 1165 | 1 | 24 |
| ob5 | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 2537 | -637 | -296 | -515 | 1382 | 1 | 24 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 189 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 189 |
| open_range | false_break | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 435 | 2425 | 23 | -145 | -730 | 1542 | 2 | 189 |
| open_range | false_break_native | renko_20 | {"M": 1, "k": 0.5} | sym8u / both | 420 | 2670 | 231 | -183 | -1477 | 2468 | 2 | 189 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 189 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 189 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 189 |
| open_range | retest_native | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 298 | 4014 | 703 | 324 | -1734 | 2744 | 2 | 189 |
| opens | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 360 | 5490 | -643 | 803 | 229 | 6745 | 1 | 194 |
| opens | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 338 | 5821 | 1364 | -659 | -1602 | 6521 | 1 | 194 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 168 | 4705 | -649 | -420 | 1329 | 4754 | 1 | 194 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 1 | 194 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 367 | 5218 | -809 | 1237 | -891 | 2404 | 1 | 194 |
| opens | reject_native | vol_1100 | {"tol": 0.5, "conf": "body"} | sym15u / both | 349 | 4967 | 853 | 1322 | -3541 | 4460 | 2 | 194 |
| opens | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 306 | 4952 | 1079 | -2912 | 3174 | 4784 | 1 | 194 |
| opens | retest_native | pnf_20 | {"M": 6, "tol": 0.5} | sym15u / both | 294 | 4635 | 1331 | 789 | 2801 | 6670 | 1 | 194 |
| prior_day | break | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 194 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 194 |
| prior_day | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 6120 | 1169 | 654 | 6266 | 6027 | 1 | 194 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 1 | 194 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 194 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 194 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 194 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 194 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 193 |
| profile_nodes | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 277 | 3995 | 2467 | -1651 | 1370 | 3940 | 1 | 193 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 193 |
| profile_nodes | false_break_native | rng_40 | {"M": 1, "k": 0.5} | sym8u / both | 226 | 3965 | -671 | 942 | 823 | 4444 | 2 | 193 |
| profile_nodes | reject | renko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 483 | 3360 | 110 | -1175 | 115 | 1930 | 2 | 193 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 193 |
| profile_nodes | retest | renko_40 | {"M": 6, "tol": 0.5} | sym8u / both | 164 | 3845 | 172 | 438 | 986 | 2760 | 2 | 193 |
| profile_nodes | retest_native | cusum_28 | {"M": 10, "tol": 0.5} | sym15u / both | 262 | 4087 | 1118 | 403 | 1644 | 5061 | 1 | 193 |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 2 | 194 |
| profile_va | break_native | rng_28 | {"n": 2, "k": 0.5} | sym15u / both | 217 | 4047 | 449 | 1260 | 3137 | 4304 | 2 | 194 |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 198 | 3091 | 543 | 151 | 2346 | 3855 | 2 | 194 |
| profile_va | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | plain60/60 / both | 548 | 2993 | 1062 | 46 | 172 | 1929 | 1 | 194 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 1 | 194 |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 263 | 4791 | -360 | 58 | 2424 | 3455 | 1 | 194 |
| profile_va | retest | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 465 | 3564 | -541 | -277 | 960 | 1989 | 1 | 194 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 194 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 194 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 194 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 194 |
| round | false_break_native | vol_500 | {"M": 2, "k": 0.5} | asym10u/20u / both | 543 | 5669 | -1429 | -2821 | 263 | 7059 | 2 | 194 |
| round | reject | renko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 657 | 8023 | -600 | -3119 | -4002 | 8822 | 2 | 194 |
| round | reject_native | vsess_200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 540 | 6009 | 257 | -1854 | -806 | 4925 | 2 | 194 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 194 |
| round | retest_native | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 617 | 6587 | -614 | 2075 | 217 | 5937 | 2 | 194 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 192 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 192 |
| session_hl | false_break | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 346 | 4857 | 1820 | -135 | 2442 | 2702 | 1 | 192 |
| session_hl | false_break_native | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 344 | 5417 | 1497 | 47 | 2767 | 3055 | 1 | 192 |
| session_hl | reject | tick_5000 | {"tol": 0.0, "conf": "body"} | sym8u / both | 257 | 2738 | -362 | 1005 | -702 | 2504 | 2 | 192 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 192 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 192 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 192 |
| trendline | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 269 | 3909 | 1089 | -255 | 2448 | 3188 | 1 | 24 |
| trendline | break_native | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 287 | 3275 | 616 | 1885 | 141 | 3826 | 1 | 24 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 285 | 4062 | 1560 | 1127 | 1434 | 5996 | 1 | 24 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4692 | 42 | 1654 | 1101 | 5496 | 1 | 24 |
| trendline | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 206 | 2009 | -383 | -16 | 2214 | 954 | 1 | 24 |
| trendline | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 272 | 3205 | 233 | 64 | 1560 | 4027 | 1 | 24 |
| trendline | retest | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 234 | 3192 | -7 | -266 | -583 | 2917 | 1 | 24 |
| trendline | retest_native | pnf_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 475 | 3341 | -1121 | -1548 | 199 | -139 | 1 | 24 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 194 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 194 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 194 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 194 |
| uw_dp | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 94 | 3468 | 0 | 0 | 524 | 3496 | 1 | 194 |
| uw_dp | reject_native | mom_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 135 | 3130 | 0 | 0 | 439 | 2925 | 1 | 194 |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 153 | 3839 | 0 | 0 | 1297 | 3514 | 2 | 194 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 194 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 193 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 1 | 193 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 1 | 193 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 1 | 193 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 1 | 193 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 193 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 193 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 193 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 193 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 193 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 193 |
| uw_qqq | false_break_native | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3384 | 0 | 197 | 3751 | 4321 | 1 | 193 |
| uw_qqq | reject | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 193 |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 193 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 193 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 193 |
| vwap | break | rng_80 | {"n": 2, "k": 0.5} | sym8u / both | 294 | 4569 | 929 | 247 | 3761 | 4575 | 2 | 193 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 193 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 178 | 4696 | 63 | -174 | 2422 | 5048 | 1 | 193 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 166 | 4411 | -108 | -214 | 2319 | 4241 | 1 | 193 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 193 |
| vwap | reject_native | tm60 | {"tol": 0.0, "conf": "close"} | sym15u / both | 302 | 5838 | -1468 | 1495 | -1469 | 6714 | 1 | 193 |
| vwap | retest | tm15 | {"M": 10, "tol": 0.5} | sym15u / both | 353 | 4113 | 1019 | 662 | 1923 | 5583 | 1 | 193 |
| vwap | retest_native | tm15 | {"M": 6, "tol": 0.5} | sym15u / both | 352 | 4260 | 459 | 1038 | 2222 | 6362 | 1 | 193 |
| vwap_bands | break | mom_20 | {"n": 3, "k": 0.5} | sym15u / both | 475 | 6544 | 86 | 1981 | 5311 | 8312 | 1 | 192 |
| vwap_bands | break_native | drb_400 | {"n": 2, "k": 0.25} | sym15u / both | 545 | 5721 | -772 | -2232 | 2651 | 4494 | 1 | 192 |
| vwap_bands | false_break | swing_atr_0.6 | {"M": 3, "k": 0.5} | sym15u / both | 477 | 3977 | 1234 | -534 | 5712 | 3574 | 1 | 192 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 192 |
| vwap_bands | reject | tick_300 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 481 | 6944 | 1737 | -351 | 2059 | 7316 | 2 | 192 |
| vwap_bands | reject_native | vol_500 | {"tol": 0.5, "conf": "close"} | asym10u/20u / both | 512 | 6769 | -741 | 751 | 2018 | 2515 | 2 | 192 |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 475 | 5871 | -47 | -3369 | -2356 | 8027 | 2 | 192 |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 452 | 5820 | -431 | 1126 | 1466 | 4714 | 1 | 192 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 194 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 194 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 194 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 194 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 | 1812 | 674 | -92 | 992 | 1655 | 1 | 194 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 82 | 2131 | 988 | -272 | -1646 | 1573 | 1 | 194 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 194 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 194 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 193 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym15u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 1 | 193 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 3068 | 829 | 2566 | -2302 | 3067 | 1 | 193 |
| zones | false_break_native | urenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 169 | 3155 | 720 | 2082 | -2078 | 3224 | 1 | 193 |
| zones | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 96 | 2134 | 178 | -1365 | -390 | 3312 | 1 | 193 |
| zones | reject_native | dlt_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 2882 | -1835 | -913 | -60 | 3270 | 1 | 193 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 193 |
| zones | retest_native | rng_14 | {"M": 6, "tol": 0.5} | sym8u / both | 217 | 2669 | -1529 | -653 | -535 | 2164 | 2 | 193 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 63 | 745 | -750 | 713 | 55 | 78 | 1 | 24 |
| sdx15 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 218 | 3979 | 866 | -1611 | -3817 | 3589 | 1 | 24 |
| sdx15 | lim_prox | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 520 | 3351 | 996 | -658 | -1400 | 3970 | 1 | 24 |
| sdx15 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 151 | 2838 | 1403 | -67 | -500 | 3343 | 1 | 24 |
| sdx15 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / both | 103 | 1888 | -308 | 1188 | 1098 | 2361 | 1 | 24 |
| sdx15 | rej_native | pnf_7 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 163 | 3025 | 609 | -1420 | -997 | 2439 | 1 | 24 |
| sdx15 | rej_zone | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 163 | 3025 | 609 | -1420 | -997 | 2439 | 1 | 24 |
| sdx15 | retest | pnf_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 31 | 526 | -752 | 859 | -350 | 61 | 1 | 24 |
| sdx3 | break | pnf_7 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 103 | 1995 | -691 | -13 | 2296 | 1834 | 1 | 24 |
| sdx3 | lim_mid | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 315 | 3243 | 1073 | -1181 | -5173 | 1197 | 1 | 24 |
| sdx3 | lim_prox | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 168 | 2443 | 681 | 615 | -1647 | 1257 | 1 | 24 |
| sdx3 | rej | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 108 | 2223 | 1029 | -286 | -877 | 2043 | 1 | 24 |
| sdx3 | rej_flow | wrenko_14 | {"d": "B", "F": 9} | plain60/60 / both | 51 | 1295 | 306 | 9 | -317 | 994 | 1 | 24 |
| sdx3 | rej_native | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 304 | 2775 | 2012 | 3309 | -2595 | 3415 | 1 | 24 |
| sdx3 | rej_zone | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 304 | 2775 | 2012 | 3309 | -2595 | 3415 | 1 | 24 |
| sdx3 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 72 | 1126 | -463 | 715 | -932 | 1323 | 1 | 24 |
| sdx30 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 34 | 466 | -431 | 870 | -122 | 440 | 1 | 24 |
| sdx30 | lim_mid | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 103 | 1951 | 721 | -406 | -107 | 947 | 1 | 24 |
| sdx30 | lim_prox | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 100 | 1907 | 302 | 51 | -486 | 1273 | 1 | 24 |
| sdx30 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 38 | 1091 | -267 | -1452 | -151 | 712 | 1 | 24 |
| sdx30 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | plain60/60 / short | 35 | 383 | -313 | -316 | -602 | 47 | 1 | 24 |
| sdx30 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 162 | 1426 | 542 | -1070 | 282 | 545 | 1 | 24 |
| sdx30 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 162 | 1426 | 542 | -1070 | 282 | 545 | 1 | 24 |
| sdx5 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 91 | 2323 | -533 | 988 | 255 | 1749 | 1 | 24 |
| sdx5 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 354 | 2442 | 357 | 891 | -1052 | 3642 | 1 | 24 |
| sdx5 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 746 | 2572 | -102 | -1530 | -5419 | 2741 | 1 | 24 |
| sdx5 | rej | pnf_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 32 | 1747 | 397 | 156 | 700 | 1728 | 1 | 24 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / short | 113 | 441 | 27 | 873 | 69 | 704 | 1 | 24 |
| sdx5 | rej_native | urenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 178 | 2412 | -1189 | 369 | -649 | 2087 | 1 | 24 |
| sdx5 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 198 | 2334 | -819 | -884 | -1076 | 2111 | 1 | 24 |
| sdx5 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 118 | 1208 | -390 | 1093 | -1050 | 1030 | 1 | 24 |
| sdx60 | break | pnf_28 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 31 | 98 | -542 | 508 | -491 | 56 | 1 | 24 |
| sdx60 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 77 | 1433 | 356 | -715 | 911 | 1463 | 1 | 24 |
| sdx60 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 259 | 1933 | -320 | -699 | -24 | 2535 | 1 | 24 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 76 | 986 | -87 | -92 | 901 | 1294 | 1 | 24 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 37 | 432 | -131 | 314 | 665 | 397 | 1 | 24 |
| sdx60 | rej_native | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 24 |
| sdx60 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 24 |
| sdx_renko28 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 129 | 2292 | -1534 | 786 | -391 | 1043 | 1 | 24 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 24 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 143 | 2385 | 29 | 449 | -1218 | 2065 | 1 | 24 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 279 | 4161 | -1746 | -3181 | -2583 | 3043 | 1 | 24 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 142 | 877 | 513 | -550 | 377 | 864 | 1 | 24 |
| sdx_renko28 | rej_native | pnf_5 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 24 |
| sdx_renko28 | rej_zone | pnf_5 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 24 |
| sdx_renko28 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 89 | 1596 | -851 | 795 | 41 | 977 | 1 | 24 |
| sdx_rng28 | break | lbrk_3_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 243 | 2807 | -2732 | 420 | -1997 | 2106 | 1 | 24 |
| sdx_rng28 | lim_mid | urenko_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 290 | 3100 | -1678 | 1370 | -2387 | 963 | 1 | 24 |
| sdx_rng28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 343 | 3324 | -202 | 219 | -1999 | 2640 | 1 | 24 |
| sdx_rng28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 472 | 2249 | 2358 | -2729 | 945 | 3149 | 1 | 24 |
| sdx_rng28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 224 | 2295 | 245 | -1493 | 2758 | 457 | 1 | 24 |
| sdx_rng28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 24 |
| sdx_rng28 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 24 |
| sdx_rng28 | retest | urenko_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 274 | 2029 | -1887 | -610 | -3866 | 853 | 1 | 24 |
| sdx_vol1100 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 314 | 4031 | -1409 | -503 | 658 | 4201 | 1 | 24 |
| sdx_vol1100 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 275 | 6337 | -998 | 71 | 1443 | 6397 | 1 | 24 |
| sdx_vol1100 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 278 | 5565 | -679 | -26 | -465 | 6171 | 1 | 24 |
| sdx_vol1100 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 346 | 2639 | 554 | -192 | -349 | 2420 | 1 | 24 |
| sdx_vol1100 | rej_flow | wrenko_20 | {"d": "E", "F": 0} | sym15u / short | 90 | 2232 | -129 | -218 | 268 | 1907 | 1 | 24 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 768 | 3970 | -570 | -433 | -756 | 4714 | 1 | 24 |
| sdx_vol1100 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 162 | 3444 | 914 | 374 | -624 | 4290 | 1 | 24 |
| sdx_vol1100 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 134 | 2174 | -829 | 511 | -380 | 1220 | 1 | 24 |
| fib15 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3386 | -215 | -1066 | -1338 | 3676 | 1 | 23 |
| fib15 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3296 | 118 | -747 | -1540 | 3799 | 1 | 23 |
| fib15 | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 23 |
| fib15 | false_break_native | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 23 |
| fib15 | pullback | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 92 | 1869 | -30 | -12 | -37 | 2298 | 1 | 23 |
| fib15 | pullback_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / short | 83 | 2154 | 184 | -420 | -152 | 2586 | 1 | 23 |
| fib15 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 23 |
| fib15 | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 23 |
| fib15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / short | 125 | 3286 | 93 | -404 | 983 | 3482 | 1 | 23 |
| fib15 | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / short | 125 | 3286 | 93 | -404 | 983 | 3482 | 1 | 23 |
| fib5 | break | urenko_14 | {"n": 2, "k": 0.25} | sym15u / both | 290 | 3998 | -1693 | 2446 | -509 | 3246 | 1 | 23 |
| fib5 | break_native | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 283 | 3290 | -1099 | 214 | -1933 | 5199 | 1 | 23 |
| fib5 | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 23 |
| fib5 | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 23 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 1 | 23 |
| fib5 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / short | 135 | 1865 | -693 | 1105 | -22 | 1426 | 1 | 23 |
| fib5 | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 389 | 5190 | 867 | 1104 | 100 | 5716 | 1 | 23 |
| fib5 | reject_native | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 295 | 3775 | -1517 | 2905 | 1380 | 4817 | 1 | 23 |
| fib5 | retest | lbrk_3_40 | {"M": 3, "tol": 0.0} | sym15u / both | 115 | 2213 | 351 | 104 | -1002 | 2215 | 1 | 23 |
| fib5 | retest_native | urenko_56 | {"M": 10, "tol": 0.5} | sym15u / both | 234 | 2282 | -727 | -725 | -906 | 2640 | 1 | 23 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 23 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 23 |
| fib60 | false_break | urenko_20 | {"M": 2, "k": 0.5} | sym15u / both | 180 | 2491 | -930 | -991 | -2211 | 2940 | 1 | 23 |
| fib60 | false_break_native | mrenko_10 | {"M": 3, "k": 0.5} | sym15u / both | 241 | 2680 | -442 | -424 | -1292 | 1918 | 1 | 23 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 66 | 950 | -134 | -49 | -111 | 1331 | 1 | 23 |
| fib60 | pullback_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / short | 30 | 1090 | 514 | -645 | 216 | 1306 | 1 | 23 |
| fib60 | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 345 | 1686 | 372 | 1695 | 206 | 1427 | 1 | 23 |
| fib60 | reject_native | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 111 | 2302 | -527 | 419 | 985 | 1304 | 1 | 23 |
| fib60 | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 124 | 2392 | -360 | 1609 | -959 | 2711 | 1 | 23 |
| fib60 | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2972 | -1194 | 195 | 1413 | 1856 | 1 | 23 |
| fibr_dev | break | urenko_80 | {"n": 3, "k": 0.5} | sym15u / short | 131 | 3154 | -942 | 769 | -2141 | 2275 | 1 | 23 |
| fibr_dev | break_native | urenko_80 | {"n": 3, "k": 0.5} | sym15u / both | 252 | 2914 | -2010 | 1694 | -2441 | 1815 | 1 | 23 |
| fibr_dev | false_break | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / short | 135 | 2113 | -1084 | 533 | -722 | 1248 | 1 | 23 |
| fibr_dev | false_break_native | pnf_14 | {"M": 2, "k": 0.5} | sym15u / short | 147 | 2266 | -564 | -453 | 81 | 2314 | 1 | 23 |
| fibr_dev | reject | urenko_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 2384 | -1728 | 1344 | -1037 | 1263 | 1 | 23 |
| fibr_dev | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 209 | 2679 | -1704 | 1086 | -206 | 3193 | 1 | 23 |
| fibr_dev | retest | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / short | 113 | 2148 | -1114 | 590 | -2563 | 1308 | 1 | 23 |
| fibr_dev | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / short | 118 | 2121 | -803 | -352 | -3304 | 1265 | 1 | 23 |
| fibr_ib | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 251 | 3612 | 92 | -1032 | -493 | 1859 | 1 | 23 |
| fibr_ib | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / both | 233 | 2795 | -1381 | -381 | -1387 | 5050 | 1 | 23 |
| fibr_ib | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 231 | 2998 | -1461 | -465 | -1676 | 5234 | 1 | 23 |
| fibr_ib | false_break_native | mrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 258 | 3604 | -782 | -1742 | -1366 | 5952 | 1 | 23 |
| fibr_ib | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 256 | 1999 | -811 | 2337 | 2241 | 2718 | 1 | 23 |
| fibr_ib | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 116 | 2936 | -599 | 129 | -207 | 3430 | 1 | 23 |
| fibr_ib | retest | mrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 233 | 2630 | -2292 | -1847 | -2167 | 467 | 1 | 23 |
| fibr_ib | retest_native | mrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 240 | 2981 | -1742 | -2010 | -940 | 2147 | 1 | 23 |
| fibr_on | break | urenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 206 | 2288 | -1496 | 1579 | 3141 | 1942 | 1 | 23 |
| fibr_on | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 235 | 2613 | 83 | 1407 | 1700 | 2276 | 1 | 23 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 232 | 2221 | -828 | 1006 | -1840 | 1304 | 1 | 23 |
| fibr_on | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 233 | 2219 | -607 | 594 | -2194 | 1699 | 1 | 23 |
| fibr_on | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 269 | 1353 | -352 | -1030 | -930 | 1521 | 1 | 23 |
| fibr_on | reject_native | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 241 | 3127 | -1035 | 619 | 4028 | 1810 | 1 | 23 |
| fibr_on | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 228 | 2547 | -512 | 810 | -273 | 485 | 1 | 23 |
| fibr_on | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 217 | 2587 | -133 | 2095 | -1145 | 3420 | 1 | 23 |
| fibr_or | break | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 223 | 3722 | 1679 | 177 | 2896 | 4918 | 1 | 23 |
| fibr_or | break_native | pnf_5 | {"n": 2, "k": 0.25} | sym15u / both | 232 | 3169 | 76 | 567 | -2045 | 2085 | 1 | 23 |
| fibr_or | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 190 | 2273 | -1455 | 2029 | -472 | 2614 | 1 | 23 |
| fibr_or | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 190 | 2273 | -1455 | 2029 | -472 | 2614 | 1 | 23 |
| fibr_or | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 23 |
| fibr_or | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 23 |
| fibr_or | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / short | 106 | 2541 | -582 | -25 | -891 | 2914 | 1 | 23 |
| fibr_or | retest_native | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 226 | 3433 | -1079 | 1971 | 1090 | 4690 | 1 | 23 |
| fibr_pd | break | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 23 |
| fibr_pd | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 23 |
| fibr_pd | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 1998 | -349 | 1339 | -3324 | 2735 | 1 | 23 |
| fibr_pd | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 38 | -1381 | 1884 | 1 | 23 |
| fibr_pd | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 197 | 3093 | 14 | 1008 | -2214 | 3340 | 1 | 23 |
| fibr_pd | reject_native | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 211 | 2307 | -66 | 547 | -2237 | 2254 | 1 | 23 |
| fibr_pd | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 88 | 2090 | 436 | -59 | -1075 | 1885 | 1 | 23 |
| fibr_pd | retest_native | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 88 | 2090 | 436 | -59 | -1075 | 1885 | 1 | 23 |
| piv_cama | break | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 220 | 1725 | 1462 | 802 | -119 | 3328 | 1 | 23 |
| piv_cama | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 219 | 2483 | 797 | 1927 | 1854 | 4271 | 1 | 23 |
| piv_cama | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 181 | 818 | -1131 | 1918 | -2578 | -377 | 1 | 23 |
| piv_cama | false_break_native | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 172 | 1035 | -1466 | 1103 | -2837 | -421 | 1 | 23 |
| piv_cama | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 146 | 1797 | 624 | -91 | -809 | 1490 | 1 | 23 |
| piv_cama | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 220 | 1749 | 2973 | 1720 | -1412 | 2021 | 1 | 23 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 3017 | 1323 | -981 | 973 | 1360 | 1 | 23 |
| piv_cama | retest_native | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 209 | 2890 | -621 | -741 | 2051 | 2186 | 1 | 23 |
| piv_floor | break | urenko_80 | {"n": 2, "k": 0.25} | sym15u / both | 146 | 2104 | 89 | 2484 | 144 | 1328 | 1 | 23 |
| piv_floor | break_native | urenko_56 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2598 | 440 | 2679 | 586 | 1925 | 1 | 23 |
| piv_floor | false_break | urenko_112 | {"M": 2, "k": 0.5} | sym15u / short | 70 | 1049 | -527 | 416 | -715 | 1400 | 1 | 23 |
| piv_floor | false_break_native | urenko_112 | {"M": 1, "k": 0.0} | sym15u / short | 71 | 928 | -457 | 280 | -567 | 1279 | 1 | 23 |
| piv_floor | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 64 | 1744 | -884 | -360 | -2877 | 2328 | 1 | 23 |
| piv_floor | reject_native | urenko_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 2706 | 569 | 1518 | 105 | 1374 | 1 | 23 |
| piv_floor | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 2261 | -762 | -663 | -1617 | 2246 | 1 | 23 |
| piv_floor | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 136 | 1463 | 388 | 1561 | -926 | 1786 | 1 | 23 |
| piv_wf | break | pnf_20 | {"n": 1, "k": 0.0} | sym15u / short | 110 | 1700 | -1119 | 204 | -1044 | 1784 | 1 | 23 |
| piv_wf | break_native | pnf_20 | {"n": 1, "k": 0.0} | sym15u / short | 110 | 1700 | -1119 | 204 | -1044 | 1784 | 1 | 23 |
| piv_wf | false_break | pnf_20 | {"M": 1, "k": 0.0} | sym15u / short | 110 | 1700 | -1119 | 204 | -1044 | 1784 | 1 | 23 |
| piv_wf | false_break_native | pnf_20 | {"M": 1, "k": 0.0} | sym15u / short | 110 | 1700 | -1119 | 204 | -1044 | 1784 | 1 | 23 |
| piv_wf | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 88 | 1762 | -1585 | -62 | -1571 | 3382 | 1 | 23 |
| piv_wf | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 223 | 1716 | -538 | 1442 | -3384 | 2696 | 1 | 23 |
| piv_wf | retest | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / short | 118 | 1239 | -506 | -390 | -253 | -605 | 1 | 23 |
| piv_wf | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / short | 108 | 1208 | -223 | 667 | -1849 | 902 | 1 | 23 |
| swcluster | break | pnf_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 78 | 1434 | -579 | -308 | -267 | 1378 | 1 | 24 |
| swcluster | break_native | lbrk_3_20 | {"n": 3, "k": 0.5} | sym15u / both | 47 | 1484 | -898 | 212 | -2023 | 2300 | 1 | 24 |
| swcluster | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 66 | 711 | -608 | 898 | -670 | 546 | 1 | 24 |
| swcluster | false_break_native | urenko_112 | {"M": 3, "k": 0.5} | sym15u / both | 33 | 948 | -1573 | 501 | -496 | 1074 | 1 | 24 |
| swcluster | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1368 | -235 | -439 | 744 | 1365 | 1 | 24 |
| swcluster | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 51 | 1544 | 242 | 371 | -1281 | 1329 | 1 | 24 |
| swcluster | retest | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 36 | 1151 | -1021 | 504 | 142 | 573 | 1 | 24 |
| swcluster | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 39 | 1287 | -302 | 729 | 809 | 785 | 1 | 24 |
| swsr15 | break | pnf_5 | {"n": 1, "k": 0.0} | sym15u / short | 108 | 2833 | 26 | -288 | 495 | 3453 | 1 | 24 |
| swsr15 | break_native | pnf_5 | {"n": 1, "k": 0.0} | sym15u / short | 108 | 2833 | 26 | -288 | 495 | 3453 | 1 | 24 |
| swsr15 | false_break | pnf_5 | {"M": 1, "k": 0.0} | sym15u / short | 113 | 2838 | -180 | -495 | 961 | 3092 | 1 | 24 |
| swsr15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / short | 117 | 2948 | 43 | -480 | 1191 | 3055 | 1 | 24 |
| swsr15 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / short | 122 | 2579 | -81 | -506 | 1821 | 2538 | 1 | 24 |
| swsr15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / short | 128 | 3255 | 54 | -929 | 2286 | 3425 | 1 | 24 |
| swsr15 | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 176 | 2920 | 1261 | 1356 | -1090 | 2148 | 1 | 24 |
| swsr15 | retest_native | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 89 | 2917 | -900 | -924 | 226 | 3525 | 1 | 24 |
| swsr5 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 185 | 3380 | -452 | -1389 | 1021 | 3074 | 1 | 24 |
| swsr5 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 184 | 3396 | -173 | -1192 | 683 | 3081 | 1 | 24 |
| swsr5 | false_break | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 24 |
| swsr5 | false_break_native | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 24 |
| swsr5 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / short | 135 | 2767 | -736 | -1265 | 2147 | 3051 | 1 | 24 |
| swsr5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 236 | 2951 | -1432 | 2774 | -395 | 2301 | 1 | 24 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 232 | 4334 | -1647 | 19 | -238 | 4595 | 1 | 24 |
| swsr5 | retest_native | pnf_10 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 3900 | -224 | -1776 | -2 | 4700 | 1 | 24 |
| swsr60 | break | pnf_40 | {"n": 2, "k": 0.25} | sym15u / short | 38 | 1767 | 558 | -107 | 48 | 2005 | 1 | 24 |
| swsr60 | break_native | urenko_56 | {"n": 3, "k": 0.5} | sym15u / both | 129 | 1674 | -3334 | 873 | -468 | 2209 | 1 | 24 |
| swsr60 | false_break | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 1784 | -2173 | -454 | -1920 | 1883 | 1 | 24 |
| swsr60 | false_break_native | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 1784 | -2173 | -454 | -1920 | 1883 | 1 | 24 |
| swsr60 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / short | 79 | 1806 | -405 | -154 | -399 | 2738 | 1 | 24 |
| swsr60 | reject_native | pnf_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 117 | 2997 | -228 | 297 | 1282 | 3213 | 1 | 24 |
| swsr60 | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / both | 117 | 1360 | -1220 | -204 | -577 | 1862 | 1 | 24 |
| swsr60 | retest_native | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / both | 117 | 1360 | -1220 | -204 | -577 | 1862 | 1 | 24 |
| stack | break | urenko_28 | {"k": 2, "cw": 0.5} | sym15u / short | 86 | 2291 | 234 | -41 | 1145 | 1866 | 1 | 193 |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 107 | 3072 | 144 | 769 | -10 | 2485 | 1 | 193 |
| stack | reject | rng_20 | {"k": 2, "cw": 1.0} | asym10u/20u / both | 101 | 2187 | -447 | 1473 | -506 | 1062 | 2 | 193 |
| stack | reject_native | mrenko_14 | {"k": 2, "cw": 0.5} | sym15u / both | 215 | 2715 | -713 | -2101 | -338 | 3647 | 1 | 193 |
| book_walls | break | time_s_5 | {"n": 2, "k": 0.25} | plain60/60 / both | 42 | 894 | -489 | -382 | 220 | 1042 | 1 | 191 |
| book_walls | break_native | tm15 | {"n": 1, "k": 0.0} | plain60/60 / both | 30 | 605 | -584 | -435 | -96 | 784 | 1 | 191 |
| book_walls | reject | time_s_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 47 | 475 | -958 | -263 | -638 | 569 | 1 | 191 |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 34 | 561 | 55 | -204 | -128 | 492 | 1 | 191 |
| book_walls | retest | time_s_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 499 | -402 | -181 | 44 | 592 | 1 | 191 |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 34 | 627 | -374 | 538 | 3 | 600 | 1 | 191 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 193 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 193 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 193 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 193 |
| book_walls_loose | reject | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 57 | 1173 | 963 | -1384 | -1489 | 994 | 2 | 193 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 193 |
| book_walls_loose | retest | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / short | 41 | 962 | -161 | -663 | 174 | 1475 | 1 | 193 |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 1146 | 212 | 787 | -261 | 941 | 1 | 193 |
| channel | break | pnf_20 | {"n": 1, "k": 0.0} | sym15u / both | 259 | 2734 | 517 | -988 | -662 | 4298 | 1 | 23 |
| channel | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 275 | 3932 | -2003 | 2173 | -8 | 4372 | 1 | 23 |
| channel | false_break | pnf_7 | {"M": 3, "k": 0.5} | sym15u / both | 293 | 3216 | -1127 | 782 | 1821 | 3617 | 1 | 23 |
| channel | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 293 | 2974 | -991 | 875 | 2184 | 3395 | 1 | 23 |
| channel | reject | wrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 254 | 2610 | 557 | -1166 | -2512 | 2272 | 1 | 23 |
| channel | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 639 | 2960 | -694 | -123 | -366 | 1118 | 1 | 23 |
| channel | retest | urenko_28 | {"M": 3, "tol": 0.0} | sym15u / both | 181 | 2454 | -28 | 911 | -10 | 1958 | 1 | 23 |
| channel | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 268 | 3176 | -2025 | -947 | 1357 | 4563 | 1 | 23 |
| fvg15 | break | pnf_20 | {"n": 1, "k": 0.0} | sym15u / short | 50 | 1337 | -701 | 1039 | -422 | 1353 | 1 | 24 |
| fvg15 | break_native | pnf_20 | {"n": 1, "k": 0.0} | sym15u / short | 50 | 1337 | -701 | 1039 | -422 | 1353 | 1 | 24 |
| fvg15 | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 24 |
| fvg15 | false_break_native | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 24 |
| fvg15 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 59 | 1177 | 560 | -604 | 190 | 541 | 1 | 24 |
| fvg15 | reject_native | pnf_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 111 | 1044 | -987 | 68 | 64 | 1053 | 1 | 24 |
| fvg15 | retest | urenko_28 | {"M": 10, "tol": 0.5} | sym15u / both | 81 | 1488 | -659 | 345 | -893 | 1193 | 1 | 24 |
| fvg15 | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 97 | 2069 | -451 | 295 | -1907 | 1585 | 1 | 24 |
| fvg5 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 206 | 2078 | 850 | -246 | 945 | 2091 | 1 | 24 |
| fvg5 | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / both | 129 | 1990 | -427 | 863 | -481 | 1206 | 1 | 24 |
| fvg5 | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / short | 82 | 1114 | 114 | 360 | 552 | 871 | 1 | 24 |
| fvg5 | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / short | 83 | 1092 | 149 | -41 | 778 | 965 | 1 | 24 |
| fvg5 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 157 | 1877 | 86 | 1529 | -360 | 2685 | 1 | 24 |
| fvg5 | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 100 | 1595 | -1730 | 887 | 355 | 2368 | 1 | 24 |
| fvg5 | retest | wrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 170 | 1812 | -1404 | 1937 | 357 | 1585 | 1 | 24 |
| fvg5 | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 315 | 1828 | 1289 | 1218 | -784 | 1429 | 1 | 24 |
| gaps | break | vol_500 | {"n": 1, "k": 0.25} | sym30u / both | 36 | 1482 | -209 | 1576 | 785 | 971 | 2 | 193 |
| gaps | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 108 | 1966 | -1477 | 311 | -678 | 1813 | 1 | 193 |
| gaps | false_break | time_s_5 | {"M": 1, "k": 0.0} | sym30u / both | 39 | 1447 | -588 | 325 | -1319 | 918 | 2 | 193 |
| gaps | false_break_native | vsess_200 | {"M": 3, "k": 0.5} | sym8u / both | 34 | 1555 | -904 | 638 | -875 | 1064 | 2 | 193 |
| gaps | reject | rng_10 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 44 | 1207 | 761 | 514 | -567 | 1000 | 2 | 193 |
| gaps | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 114 | 2547 | -815 | -742 | -938 | 2343 | 1 | 193 |
| gaps | retest | cusum_28 | {"M": 6, "tol": 0.5} | sym15u / both | 32 | 1736 | -1009 | 1068 | -1865 | 1624 | 1 | 193 |
| gaps | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 99 | 1715 | -1063 | 304 | 2429 | 2317 | 1 | 193 |
| mmove | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 24 |
| mmove | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 24 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 24 |
| mmove | false_break_native | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 24 |
| mmove | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 144 | 1952 | 75 | -438 | 2598 | 782 | 1 | 24 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / short | 134 | 2490 | -534 | 260 | 1315 | 2427 | 1 | 24 |
| mmove | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 24 |
| mmove | retest_native | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 24 |
| ob15 | break | pnf_20 | {"n": 1, "k": 0.0} | sym15u / both | 56 | 1165 | -280 | 874 | 314 | 1352 | 1 | 24 |
| ob15 | break_native | pnf_20 | {"n": 1, "k": 0.0} | sym15u / both | 56 | 1165 | -280 | 874 | 314 | 1352 | 1 | 24 |
| ob15 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 55 | 1383 | -438 | 971 | 66 | 1341 | 1 | 24 |
| ob15 | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 51 | 1394 | -674 | 804 | 277 | 1544 | 1 | 24 |
| ob15 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 55 | 925 | -325 | -377 | 1269 | 2009 | 1 | 24 |
| ob15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 55 | 1100 | 158 | 617 | 1076 | 2402 | 1 | 24 |
| ob15 | retest | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 41 | 1285 | -255 | 630 | -438 | 1547 | 1 | 24 |
| ob15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1242 | -237 | 630 | -361 | 1947 | 1 | 24 |
| ob5 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 80 | 1964 | -227 | -120 | 1433 | 2441 | 1 | 24 |
| ob5 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 2181 | -420 | 239 | 1123 | 2407 | 1 | 24 |
| ob5 | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 49 | 1758 | -619 | 734 | 1100 | 1775 | 1 | 24 |
| ob5 | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 49 | 1758 | -619 | 734 | 1100 | 1775 | 1 | 24 |
| ob5 | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 106 | 1402 | -393 | 592 | -159 | 1038 | 1 | 24 |
| ob5 | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 125 | 1452 | -364 | -720 | -1186 | 1708 | 1 | 24 |
| ob5 | retest | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 77 | 2171 | -115 | 238 | -314 | 2762 | 1 | 24 |
| ob5 | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 78 | 2276 | 28 | 288 | 302 | 2581 | 1 | 24 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 191 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 191 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym15u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 1 | 191 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 191 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 191 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 191 |
| open_range | retest | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 191 |
| open_range | retest_native | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 191 |
| opens | break | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 194 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 194 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 194 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 194 |
| opens | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 194 |
| opens | reject_native | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 194 |
| opens | retest | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 194 |
| opens | retest_native | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 194 |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 2 | 194 |
| prior_day | break_native | vsess_120 | {"n": 3, "k": 0.0} | sym15u / both | 91 | 2959 | -204 | -697 | -3330 | 1835 | 2 | 194 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 115 | 2873 | -837 | 323 | -2884 | 1490 | 1 | 194 |
| prior_day | false_break_native | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 88 | 2868 | -302 | 511 | -1840 | 2689 | 2 | 194 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 194 |
| prior_day | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 2665 | 149 | 475 | -2001 | 1894 | 2 | 194 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 1 | 194 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 1 | 194 |
| profile_nodes | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2489 | -45 | -739 | -7388 | 1667 | 1 | 193 |
| profile_nodes | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 146 | 2992 | -647 | 1127 | -2618 | 2123 | 1 | 193 |
| profile_nodes | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 180 | 2054 | -1160 | -714 | -3668 | 2648 | 2 | 193 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 193 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 193 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 193 |
| profile_nodes | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 109 | 2447 | -490 | 89 | -3842 | 2750 | 1 | 193 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 128 | 2802 | -508 | 830 | -3084 | 3094 | 1 | 193 |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 93 | 2285 | -957 | 2055 | -845 | 2570 | 2 | 194 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 194 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 194 |
| profile_va | false_break_native | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 194 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 194 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 194 |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 194 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 194 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 290 | 4837 | -1805 | 1243 | 3655 | 5119 | 1 | 194 |
| round | break_native | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 292 | 3869 | -1678 | -471 | -86 | 2338 | 1 | 194 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 194 |
| round | false_break_native | urenko_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 965 | 4358 | -1829 | -1460 | 284 | 6297 | 1 | 194 |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 2 | 194 |
| round | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 313 | 4704 | -419 | 268 | -1458 | 3186 | 1 | 194 |
| round | retest | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 302 | 4728 | -399 | 513 | -1661 | 5351 | 2 | 194 |
| round | retest_native | renko_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 319 | 4722 | -107 | 506 | 309 | 2985 | 2 | 194 |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 171 | 3430 | -820 | 2114 | -94 | 2764 | 1 | 192 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 192 |
| session_hl | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 237 | 2956 | 1816 | 1583 | -123 | 2794 | 2 | 192 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 192 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 1 | 192 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 192 |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 95 | 3205 | -819 | -845 | -75 | 4545 | 2 | 192 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 192 |
| trendline | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 220 | 1927 | 527 | 2176 | 3572 | 1306 | 1 | 24 |
| trendline | break_native | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 2264 | 431 | 3038 | 4532 | 4342 | 1 | 24 |
| trendline | false_break | urenko_112 | {"M": 3, "k": 0.5} | sym15u / short | 64 | 1930 | 482 | 816 | 608 | 2337 | 1 | 24 |
| trendline | false_break_native | lbrk_3_40 | {"M": 3, "k": 0.5} | sym15u / both | 170 | 1835 | -1385 | 256 | 1123 | 2631 | 1 | 24 |
| trendline | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 154 | 1991 | 1175 | -2319 | 1129 | 389 | 1 | 24 |
| trendline | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 239 | 3408 | 1778 | 3021 | 2069 | 2094 | 1 | 24 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 24 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 24 |
| uw_dp | break | swing_atr_0.4 | {"n": 2, "k": 0.25} | sym15u / both | 63 | 2095 | 0 | 0 | 399 | 1949 | 1 | 194 |
| uw_dp | break_native | tick_800 | {"n": 2, "k": 0.5} | sym15u / both | 64 | 2127 | 0 | 0 | -317 | 1086 | 2 | 194 |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1430 | 0 | 0 | 210 | 1085 | 1 | 194 |
| uw_dp | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 61 | 1448 | 0 | 0 | 28 | 1366 | 2 | 194 |
| uw_dp | reject | vol_2600 | {"tol": 1.0, "conf": "body"} | sym8u / both | 58 | 1359 | 0 | 0 | -37 | 922 | 2 | 194 |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 92 | 2286 | 0 | 0 | -217 | 1948 | 2 | 194 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 56 | 1926 | 0 | 0 | 295 | 2044 | 1 | 194 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 194 |
| uw_ndx | break | rng_40 | {"n": 3, "k": 0.25} | sym8u / both | 95 | 2347 | 0 | -1001 | -2044 | 1016 | 2 | 193 |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 102 | 2167 | 0 | -30 | -1920 | 1473 | 2 | 193 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 193 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 193 |
| uw_ndx | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 101 | 1925 | 0 | -40 | -1237 | 2405 | 2 | 193 |
| uw_ndx | reject_native | swing_atr_0.25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 123 | 1867 | 0 | -44 | -84 | 927 | 1 | 193 |
| uw_ndx | retest | swing_atr_0.15 | {"M": 6, "tol": 0.5} | sym15u / both | 95 | 2055 | 0 | 271 | -781 | 2249 | 1 | 193 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 110 | 2464 | 0 | -631 | 475 | 2424 | 1 | 193 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 193 |
| uw_qqq | break_native | renko_10 | {"n": 2, "k": 0.0} | sym8u / both | 261 | 1644 | 0 | -302 | -257 | 171 | 2 | 193 |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 129 | 1746 | 0 | 169 | -358 | 956 | 2 | 193 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 193 |
| uw_qqq | reject | vol_750 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 239 | 1562 | 0 | 34 | -577 | 1228 | 2 | 193 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 193 |
| uw_qqq | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 93 | 1917 | 0 | 437 | -582 | 1450 | 1 | 193 |
| uw_qqq | retest_native | dchg_20 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1938 | 0 | 452 | -985 | 1145 | 1 | 193 |
| vwap | break | renko_40 | {"n": 1, "k": 0.25} | sym8u / both | 149 | 3681 | -1617 | 765 | 724 | 2951 | 2 | 193 |
| vwap | break_native | time_m_1 | {"n": 1, "k": 0.25} | sym8u / both | 178 | 3781 | -1232 | 727 | 3089 | 3780 | 2 | 193 |
| vwap | false_break | mom_40 | {"M": 1, "k": 0.0} | sym15u / both | 152 | 3221 | -789 | 1199 | 397 | 1850 | 1 | 193 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 193 |
| vwap | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 91 | 2424 | -43 | 12 | 1717 | 1574 | 1 | 193 |
| vwap | reject_native | lbrk_3_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 141 | 2247 | 589 | -748 | -179 | 1775 | 1 | 193 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 193 |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 171 | 4078 | 605 | -156 | 1901 | 3767 | 2 | 193 |
| vwap_bands | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 267 | 4022 | -815 | -2816 | 1718 | 4334 | 1 | 192 |
| vwap_bands | break_native | cusum_56 | {"n": 3, "k": 0.5} | sym15u / both | 242 | 3923 | -2077 | -681 | 2975 | 4369 | 1 | 192 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 192 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 192 |
| vwap_bands | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 270 | 3357 | -1402 | -865 | 800 | 1869 | 1 | 192 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 192 |
| vwap_bands | retest | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 238 | 4091 | -2704 | -152 | -2144 | 3461 | 2 | 192 |
| vwap_bands | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 279 | 4137 | 353 | -1853 | 636 | 4160 | 1 | 192 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym15u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 1 | 194 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 194 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 194 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 194 |
| week_month | reject | time_m_2 | {"tol": 0.5, "conf": "body"} | sym15u / both | 38 | 1814 | -158 | -245 | 711 | 1727 | 2 | 194 |
| week_month | reject_native | tick_8000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 72 | 1892 | -134 | -795 | -399 | 2132 | 2 | 194 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 194 |
| week_month | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 38 | 1687 | -215 | -1383 | 15 | 2423 | 2 | 194 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 193 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 193 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 193 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 193 |
| zones | reject | rng_14 | {"tol": 1.0, "conf": "body"} | sym30u / both | 133 | 3041 | 2935 | -1064 | 682 | 3212 | 2 | 193 |
| zones | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | sym30u / both | 134 | 2702 | 2260 | -2018 | 250 | 3460 | 2 | 193 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 193 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 193 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | urenko_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 70 | 1077 | -200 | -153 | 1318 | 1345 | 1 | 24 |
| sdx15 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 303 | 3630 | -249 | -670 | -1170 | 3468 | 1 | 24 |
| sdx15 | lim_prox | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 271 | 3613 | 443 | 1635 | -503 | 3126 | 1 | 24 |
| sdx15 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 98 | 2164 | 235 | -369 | -1160 | 1645 | 1 | 24 |
| sdx15 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / both | 111 | 2275 | 39 | -418 | -673 | 3243 | 1 | 24 |
| sdx15 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 24 |
| sdx15 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 24 |
| sdx15 | retest | pnf_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 44 | 546 | -90 | -274 | 367 | 375 | 1 | 24 |
| sdx3 | break | wrenko_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 174 | 2989 | -298 | 492 | 507 | 2803 | 1 | 24 |
| sdx3 | lim_mid | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 343 | 3379 | -154 | -669 | -1723 | 2770 | 1 | 24 |
| sdx3 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 985 | 2720 | -608 | 248 | 713 | 3332 | 1 | 24 |
| sdx3 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 376 | 2836 | -704 | -530 | -3423 | 570 | 1 | 24 |
| sdx3 | rej_flow | wrenko_20 | {"d": "A", "F": 0} | plain60/60 / both | 173 | 1286 | -498 | 192 | -724 | 1986 | 1 | 24 |
| sdx3 | rej_native | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 24 |
| sdx3 | rej_zone | urenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 24 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 24 |
| sdx30 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 38 | 391 | -181 | 224 | 576 | 438 | 1 | 24 |
| sdx30 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 206 | 3133 | -150 | -817 | -949 | 1695 | 1 | 24 |
| sdx30 | lim_prox | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 232 | 3270 | -189 | -1338 | -13 | 2950 | 1 | 24 |
| sdx30 | rej | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 155 | 1478 | -177 | -1037 | -308 | 171 | 1 | 24 |
| sdx30 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / short | 44 | 980 | -54 | -29 | -875 | 983 | 1 | 24 |
| sdx30 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 24 |
| sdx30 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 24 |
| sdx5 | break | urenko_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 113 | 2472 | -146 | -590 | 1239 | 2914 | 1 | 24 |
| sdx5 | lim_mid | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 328 | 3532 | -277 | -1460 | -3413 | 2780 | 1 | 24 |
| sdx5 | lim_prox | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 459 | 4566 | 29 | -2087 | -1263 | 5259 | 1 | 24 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 210 | 3571 | 519 | -254 | 470 | 833 | 1 | 24 |
| sdx5 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 213 | 2801 | 412 | -179 | -668 | 1032 | 1 | 24 |
| sdx5 | rej_native | mrenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 281 | 3384 | -40 | 144 | 491 | 5027 | 1 | 24 |
| sdx5 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 279 | 3304 | -209 | -1861 | 763 | 177 | 1 | 24 |
| sdx5 | retest | urenko_80 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / long | 68 | 1301 | -140 | 343 | 310 | 1320 | 1 | 24 |
| sdx60 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 246 | -54 | 16 | 405 | -586 | 1 | 24 |
| sdx60 | lim_mid | urenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 144 | 1330 | 181 | -523 | -342 | 1028 | 1 | 24 |
| sdx60 | lim_prox | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 87 | 1502 | -62 | -1032 | -516 | 1170 | 1 | 24 |
| sdx60 | rej | wrenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 35 | 1296 | -29 | -270 | 200 | 1676 | 1 | 24 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 33 | 352 | -29 | 149 | -99 | 390 | 1 | 24 |
| sdx60 | rej_native | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 56 | 2048 | -3 | -244 | -270 | 2246 | 1 | 24 |
| sdx60 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 64 | 1710 | 25 | -264 | -895 | 1797 | 1 | 24 |
| sdx_renko28 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 488 | 2349 | 50 | -187 | 882 | 3565 | 1 | 24 |
| sdx_renko28 | lim_mid | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 326 | 3076 | 61 | -790 | -3174 | 3200 | 1 | 24 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 332 | 3491 | 102 | -741 | -4298 | 1272 | 1 | 24 |
| sdx_renko28 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 223 | 2070 | -289 | -772 | -816 | -946 | 1 | 24 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 105 | 2509 | -260 | -487 | -1295 | 1700 | 1 | 24 |
| sdx_renko28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 308 | 2821 | -262 | -1656 | -4365 | 1021 | 1 | 24 |
| sdx_renko28 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 308 | 2821 | -262 | -1656 | -4365 | 1021 | 1 | 24 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 118 | 2043 | -164 | -10 | -546 | 2698 | 1 | 24 |
| sdx_rng28 | break | mrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 803 | 5407 | 129 | 1213 | -529 | 4740 | 1 | 24 |
| sdx_rng28 | lim_mid | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 358 | 3033 | 349 | -535 | 1306 | 3345 | 1 | 24 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 24 |
| sdx_rng28 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 243 | 3949 | -351 | 572 | -1121 | 4040 | 1 | 24 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 131 | 1284 | -125 | -911 | -891 | 1041 | 1 | 24 |
| sdx_rng28 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 817 | 2929 | -775 | -407 | -1591 | 2117 | 1 | 24 |
| sdx_rng28 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 325 | 2693 | -208 | -802 | -2507 | 1921 | 1 | 24 |
| sdx_rng28 | retest | urenko_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 326 | 2318 | -220 | -674 | -518 | 2482 | 1 | 24 |
| sdx_vol1100 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 439 | 2665 | -615 | 152 | 1720 | 2989 | 1 | 24 |
| sdx_vol1100 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 351 | 3043 | -308 | 140 | -2784 | 1952 | 1 | 24 |
| sdx_vol1100 | lim_prox | urenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 328 | 3091 | -243 | 425 | -2209 | 4983 | 1 | 24 |
| sdx_vol1100 | rej | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 264 | 1716 | -137 | 105 | -651 | 670 | 1 | 24 |
| sdx_vol1100 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 113 | 1360 | -676 | -750 | -806 | 1037 | 1 | 24 |
| sdx_vol1100 | rej_native | pnf_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 241 | 3356 | 427 | -643 | -1132 | 2743 | 1 | 24 |
| sdx_vol1100 | rej_zone | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 241 | 3356 | 427 | -643 | -1132 | 2743 | 1 | 24 |
| sdx_vol1100 | retest | urenko_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 273 | 2414 | 61 | -321 | 464 | 2757 | 1 | 24 |
| fib15 | break | wrenko_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 652 | 2241 | -462 | 1465 | 332 | 2102 | 1 | 23 |
| fib15 | break_native | wrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 681 | 3089 | 526 | 1961 | 1373 | 3865 | 1 | 23 |
| fib15 | false_break | urenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 305 | 3531 | -251 | 204 | 302 | 3497 | 1 | 23 |
| fib15 | false_break_native | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3386 | -101 | -338 | 505 | 2207 | 1 | 23 |
| fib15 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 244 | 2343 | -775 | -1245 | -49 | 1766 | 1 | 23 |
| fib15 | pullback_native | pnf_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 281 | 2079 | -225 | -602 | 77 | 2651 | 1 | 23 |
| fib15 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 583 | 3114 | 323 | -624 | 1153 | 3098 | 1 | 23 |
| fib15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 3684 | 770 | -1991 | 1912 | 3118 | 1 | 23 |
| fib15 | retest | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 273 | 3063 | -31 | -967 | -487 | 3108 | 1 | 23 |
| fib15 | retest_native | urenko_56 | {"M": 6, "tol": 0.5} | sym15u / both | 222 | 3088 | -193 | -359 | 911 | 2239 | 1 | 23 |
| fib5 | break | urenko_80 | {"n": 1, "k": 0.0} | plain60/60 / both | 496 | 3121 | -38 | 232 | 1286 | 2488 | 1 | 23 |
| fib5 | break_native | urenko_80 | {"n": 1, "k": 0.0} | plain60/60 / both | 496 | 3121 | -59 | 232 | 1286 | 2488 | 1 | 23 |
| fib5 | false_break | pnf_14 | {"M": 2, "k": 0.5} | sym15u / both | 312 | 2831 | -211 | 899 | -3174 | 3833 | 1 | 23 |
| fib5 | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 346 | 3109 | -34 | 101 | 1316 | 3850 | 1 | 23 |
| fib5 | pullback | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 3450 | -194 | -957 | 412 | 4059 | 1 | 23 |
| fib5 | pullback_native | urenko_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 348 | 3271 | -554 | -985 | -70 | 4850 | 1 | 23 |
| fib5 | reject | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 248 | 3634 | 32 | -710 | -768 | 4336 | 1 | 23 |
| fib5 | reject_native | pnf_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 3481 | 593 | -1004 | -1778 | 5364 | 1 | 23 |
| fib5 | retest | urenko_40 | {"M": 10, "tol": 0.5} | plain60/60 / both | 604 | 3407 | -344 | -597 | -1540 | 4278 | 1 | 23 |
| fib5 | retest_native | urenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 295 | 4539 | -591 | -585 | -2316 | 5144 | 1 | 23 |
| fib60 | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 263 | 4046 | -15 | -506 | 1369 | 4306 | 1 | 23 |
| fib60 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 558 | 2780 | 26 | -944 | -1459 | 2655 | 1 | 23 |
| fib60 | false_break | lbrk_3_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 430 | 2589 | -24 | 1523 | -232 | 2171 | 1 | 23 |
| fib60 | false_break_native | lbrk_3_40 | {"M": 3, "k": 0.5} | plain60/60 / both | 415 | 2559 | -102 | 1257 | -523 | 1966 | 1 | 23 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 133 | 2500 | 277 | -321 | -1857 | 3041 | 1 | 23 |
| fib60 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 156 | 2403 | 331 | -240 | -1482 | 3044 | 1 | 23 |
| fib60 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 287 | 2396 | 82 | -3185 | -1420 | 3223 | 1 | 23 |
| fib60 | reject_native | urenko_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 598 | 3269 | 101 | -14 | 853 | 3533 | 1 | 23 |
| fib60 | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 303 | 2269 | 379 | -1909 | -1529 | 2945 | 1 | 23 |
| fib60 | retest_native | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 308 | 2705 | 324 | -1493 | -867 | 2814 | 1 | 23 |
| fibr_dev | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 492 | 1108 | 1598 | 3481 | 1 | 23 |
| fibr_dev | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 515 | 1108 | 1598 | 3481 | 1 | 23 |
| fibr_dev | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 316 | 3799 | 772 | 931 | 1745 | 3779 | 1 | 23 |
| fibr_dev | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3556 | 1165 | 401 | 1540 | 3473 | 1 | 23 |
| fibr_dev | reject | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 220 | 2676 | -245 | 490 | -1416 | 3923 | 1 | 23 |
| fibr_dev | reject_native | pnf_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 222 | 3007 | 532 | 861 | 852 | 4174 | 1 | 23 |
| fibr_dev | retest | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 23 |
| fibr_dev | retest_native | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 23 |
| fibr_ib | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 23 |
| fibr_ib | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 23 |
| fibr_ib | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / long | 31 | 987 | 109 | 245 | 994 | 2440 | 1 | 23 |
| fibr_ib | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 218 | 954 | 2426 | 1 | 23 |
| fibr_ib | reject | pnf_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 32 | 624 | 386 | 146 | -104 | 606 | 1 | 23 |
| fibr_ib | reject_native | pnf_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | 460 | -101 | 173 | 929 | 1 | 23 |
| fibr_ib | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 1139 | 116 | -501 | 309 | 1475 | 1 | 23 |
| fibr_ib | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 60 | 1416 | 2 | -1461 | -161 | 2126 | 1 | 23 |
| fibr_on | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 23 |
| fibr_on | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 23 |
| fibr_on | false_break | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 31 | 1342 | 57 | 761 | 588 | 2157 | 1 | 23 |
| fibr_on | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 43 | 1558 | 176 | 575 | 928 | 2229 | 1 | 23 |
| fibr_on | reject | pnf_40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 30 | 758 | 155 | 303 | -478 | 1428 | 1 | 23 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 1 | 23 |
| fibr_on | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 37 | 1166 | -61 | -3 | 830 | 1123 | 1 | 23 |
| fibr_on | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 50 | 1220 | -2 | 140 | 639 | 1292 | 1 | 23 |
| fibr_or | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 23 |
| fibr_or | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 23 |
| fibr_or | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 23 |
| fibr_or | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 23 |
| fibr_or | reject | pnf_40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 34 | 319 | 180 | -2 | -170 | 578 | 1 | 23 |
| fibr_or | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 35 | 594 | -37 | -16 | -1166 | -29 | 1 | 23 |
| fibr_or | retest | urenko_80 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1143 | 260 | -956 | -170 | 1606 | 1 | 23 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 1 | 23 |
| fibr_pd | break | pnf_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 659 | 2830 | -210 | -197 | -922 | 2628 | 1 | 23 |
| fibr_pd | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 352 | 2846 | -634 | -496 | 618 | 1155 | 1 | 23 |
| fibr_pd | false_break | pnf_7 | {"M": 1, "k": 0.0} | plain60/60 / both | 687 | 2035 | -1161 | 74 | 95 | 3371 | 1 | 23 |
| fibr_pd | false_break_native | pnf_7 | {"M": 3, "k": 0.5} | plain60/60 / both | 677 | 2833 | -1377 | 24 | 0 | 4145 | 1 | 23 |
| fibr_pd | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 349 | 2746 | -87 | -674 | -1595 | 3667 | 1 | 23 |
| fibr_pd | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 342 | 2899 | 228 | -466 | 1300 | 2291 | 1 | 23 |
| fibr_pd | retest | lbrk_3_40 | {"M": 10, "tol": 0.5} | sym15u / both | 135 | 1898 | -473 | 190 | 1267 | 3142 | 1 | 23 |
| fibr_pd | retest_native | urenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 238 | 2005 | -348 | 2029 | -1332 | 1945 | 1 | 23 |
| piv_cama | break | mrenko_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 734 | 2847 | -237 | -199 | -769 | 3696 | 1 | 23 |
| piv_cama | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 306 | 3386 | 269 | 1492 | 959 | 3771 | 1 | 23 |
| piv_cama | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 2475 | -966 | -371 | 1212 | 3202 | 1 | 23 |
| piv_cama | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 2475 | -966 | -371 | 1212 | 3202 | 1 | 23 |
| piv_cama | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 750 | 2667 | 40 | -1579 | -91 | 1913 | 1 | 23 |
| piv_cama | reject_native | wrenko_10 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 674 | 2618 | 39 | -1228 | 1160 | 979 | 1 | 23 |
| piv_cama | retest | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 719 | 2019 | -392 | -1401 | -1078 | 1623 | 1 | 23 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 1 | 23 |
| piv_floor | break | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 23 |
| piv_floor | break_native | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 23 |
| piv_floor | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 558 | 2713 | -574 | -1129 | 409 | 3175 | 1 | 23 |
| piv_floor | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 558 | 2713 | -574 | -1129 | 409 | 3175 | 1 | 23 |
| piv_floor | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 259 | 2195 | -719 | -1237 | -497 | 3369 | 1 | 23 |
| piv_floor | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 222 | 2515 | 703 | -945 | -1135 | 3210 | 1 | 23 |
| piv_floor | retest | mrenko_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 371 | 2687 | -354 | -1454 | 75 | 4194 | 1 | 23 |
| piv_floor | retest_native | mrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 2992 | 134 | -1048 | 1326 | 4059 | 1 | 23 |
| piv_wf | break | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 23 |
| piv_wf | break_native | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 23 |
| piv_wf | false_break | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 291 | 2328 | -761 | -1299 | 763 | 3828 | 1 | 23 |
| piv_wf | false_break_native | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 288 | 2691 | -648 | -1103 | 567 | 3937 | 1 | 23 |
| piv_wf | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 580 | 2409 | -138 | -114 | -2979 | 874 | 1 | 23 |
| piv_wf | reject_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 273 | 2820 | -188 | 327 | -1879 | 2754 | 1 | 23 |
| piv_wf | retest | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 241 | 2788 | -105 | 1205 | 352 | 4663 | 1 | 23 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 1 | 23 |
| swcluster | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1027 | -344 | -315 | -623 | 734 | 1 | 24 |
| swcluster | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1024 | -227 | -349 | -670 | 879 | 1 | 24 |
| swcluster | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 24 |
| swcluster | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 24 |
| swcluster | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 52 | 532 | -195 | -395 | -153 | 790 | 1 | 24 |
| swcluster | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1097 | 102 | -253 | -33 | 902 | 1 | 24 |
| swcluster | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 51 | 972 | -130 | 69 | 114 | 2028 | 1 | 24 |
| swcluster | retest_native | pnf_5 | {"M": 6, "tol": 0.5} | plain60/60 / short | 36 | 831 | -92 | -293 | 261 | 964 | 1 | 24 |
| swsr15 | break | urenko_28 | {"n": 3, "k": 0.5} | plain60/60 / both | 607 | 2835 | -125 | 665 | 1504 | 4520 | 1 | 24 |
| swsr15 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 643 | 2380 | -912 | 838 | 1403 | 3105 | 1 | 24 |
| swsr15 | false_break | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 312 | 2053 | 752 | 190 | -664 | 2012 | 1 | 24 |
| swsr15 | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 318 | 2241 | 1104 | 395 | 323 | 2854 | 1 | 24 |
| swsr15 | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 177 | 2218 | 174 | -27 | -468 | 3125 | 1 | 24 |
| swsr15 | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 660 | 2650 | -1013 | 464 | -381 | 3861 | 1 | 24 |
| swsr15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 24 |
| swsr15 | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 24 |
| swsr5 | break | mrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / short | 350 | 2561 | 125 | -622 | -439 | 3023 | 1 | 24 |
| swsr5 | break_native | wrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 789 | 3514 | 80 | 1736 | 1316 | 4658 | 1 | 24 |
| swsr5 | false_break | urenko_40 | {"M": 2, "k": 0.5} | sym15u / both | 308 | 2551 | -523 | 1079 | 19 | 1613 | 1 | 24 |
| swsr5 | false_break_native | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 272 | 3016 | 270 | 578 | -45 | 3124 | 1 | 24 |
| swsr5 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 228 | 4159 | 82 | 315 | 42 | 4336 | 1 | 24 |
| swsr5 | reject_native | urenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 855 | 2655 | 502 | 70 | 1099 | 2124 | 1 | 24 |
| swsr5 | retest | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 282 | 3812 | -92 | -1183 | -1114 | 5338 | 1 | 24 |
| swsr5 | retest_native | urenko_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 592 | 3645 | -130 | 1122 | 406 | 2944 | 1 | 24 |
| swsr60 | break | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 24 |
| swsr60 | break_native | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 24 |
| swsr60 | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 24 |
| swsr60 | false_break_native | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 24 |
| swsr60 | reject | urenko_28 | {"tol": 0.5, "conf": "body"} | sym15u / long | 39 | 866 | -299 | 726 | 398 | 329 | 1 | 24 |
| swsr60 | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 1613 | 196 | 417 | -574 | 1076 | 1 | 24 |
| swsr60 | retest | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 167 | 2036 | -8 | -105 | -593 | 2733 | 1 | 24 |
| swsr60 | retest_native | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 254 | 2089 | 120 | -274 | -719 | 2097 | 1 | 24 |
| stack | break | wrenko_14 | {"k": 3, "cw": 1.0} | sym15u / both | 163 | 3697 | -1113 | -75 | 53 | 4771 | 1 | 194 |
| stack | break_native | vol_1100 | {"k": 2, "cw": 2.0} | sym8u / both | 259 | 4020 | -769 | 291 | 1001 | 4305 | 2 | 194 |
| stack | reject | tick_300 | {"k": 2, "cw": 2.0} | asym10u/20u / both | 186 | 2906 | 61 | 648 | 73 | 1352 | 2 | 194 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | sym30u / both | 181 | 2425 | 449 | -1688 | -402 | 2186 | 2 | 194 |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 791 | 86 | 772 | 1607 | 2 | 192 |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 841 | 86 | 772 | 1607 | 2 | 192 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 192 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 192 |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 1480 | -474 | -213 | -350 | 2822 | 1 | 192 |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1443 | 732 | 638 | 74 | 699 | 1 | 192 |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 899 | -1465 | 616 | 147 | 1417 | 1 | 192 |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 821 | -381 | -305 | -21 | 226 | 1 | 192 |
| book_walls_loose | break | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 461 | 137 | 581 | 4298 | 2 | 193 |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 411 | 137 | 581 | 4298 | 2 | 193 |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 1856 | -61 | -317 | 372 | 986 | 1 | 193 |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 62 | 1806 | 153 | -209 | 562 | 1133 | 1 | 193 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 329 | 3303 | -618 | -483 | -2918 | 3949 | 1 | 193 |
| book_walls_loose | reject_native | tm45 | {"tol": 0.5, "conf": "body"} | sym30u / both | 209 | 3172 | 252 | -1284 | -1029 | 2939 | 2 | 193 |
| book_walls_loose | retest | tm20 | {"M": 6, "tol": 0.5} | sym15u / both | 353 | 2344 | -963 | -496 | 59 | 3790 | 1 | 193 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 438 | 1781 | -951 | -565 | -1164 | 2912 | 1 | 193 |
| channel | break | urenko_40 | {"n": 1, "k": 0.0} | plain60/60 / both | 638 | 3566 | -305 | 890 | 6 | 4953 | 1 | 23 |
| channel | break_native | urenko_40 | {"n": 1, "k": 0.0} | plain60/60 / both | 638 | 3566 | -305 | 890 | 6 | 4953 | 1 | 23 |
| channel | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 23 |
| channel | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 23 |
| channel | reject | mrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 389 | 1877 | 15 | 499 | 701 | 1897 | 1 | 23 |
| channel | reject_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 690 | 2704 | -28 | 101 | 2034 | 3732 | 1 | 23 |
| channel | retest | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 380 | 3089 | -102 | -214 | -98 | 2888 | 1 | 23 |
| channel | retest_native | urenko_40 | {"M": 10, "tol": 0.5} | plain60/60 / both | 545 | 2732 | -33 | 504 | 259 | 2459 | 1 | 23 |
| fvg15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 232 | 3843 | -251 | 495 | 933 | 3840 | 1 | 24 |
| fvg15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 3696 | -362 | 650 | 1002 | 4034 | 1 | 24 |
| fvg15 | false_break | urenko_40 | {"M": 1, "k": 0.0} | sym15u / both | 159 | 3689 | -171 | -177 | 1864 | 3470 | 1 | 24 |
| fvg15 | false_break_native | mrenko_20 | {"M": 2, "k": 0.5} | sym15u / both | 180 | 3960 | 34 | 246 | 1170 | 3341 | 1 | 24 |
| fvg15 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 137 | 1390 | -795 | -80 | 724 | 486 | 1 | 24 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 192 | 3238 | -531 | 176 | 1230 | 3572 | 1 | 24 |
| fvg15 | retest | wrenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 127 | 2561 | -576 | 357 | 459 | 1091 | 1 | 24 |
| fvg15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 186 | 3378 | -38 | 97 | -280 | 2780 | 1 | 24 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 269 | 3021 | -697 | 476 | 1207 | 4798 | 1 | 24 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 269 | 3021 | -697 | 476 | 1207 | 4798 | 1 | 24 |
| fvg5 | false_break | urenko_10 | {"M": 1, "k": 0.0} | sym15u / both | 347 | 2300 | -1019 | -126 | -2673 | 1682 | 1 | 24 |
| fvg5 | false_break_native | urenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 353 | 2462 | -785 | 88 | -2182 | 1384 | 1 | 24 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 24 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 24 |
| fvg5 | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3156 | -584 | -548 | -2079 | 4493 | 1 | 24 |
| fvg5 | retest_native | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 270 | 3569 | -603 | -322 | -233 | 4778 | 1 | 24 |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 140 | 2941 | 712 | 954 | 90 | 2534 | 2 | 193 |
| gaps | break_native | dib_400 | {"n": 2, "k": 0.25} | sym15u / both | 181 | 3181 | 83 | 121 | -102 | 2510 | 1 | 193 |
| gaps | false_break | pnf_5 | {"M": 3, "k": 0.5} | plain60/60 / both | 432 | 2587 | -654 | -396 | 204 | 2692 | 1 | 193 |
| gaps | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 446 | 2513 | -119 | -66 | 50 | 2449 | 1 | 193 |
| gaps | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2273 | 361 | 369 | -613 | 1685 | 1 | 193 |
| gaps | reject_native | renko_20 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 89 | 2688 | -72 | -741 | 685 | 2799 | 2 | 193 |
| gaps | retest | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 2373 | -138 | 438 | 1115 | 1777 | 1 | 193 |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2887 | -129 | 409 | 967 | 2191 | 1 | 193 |
| mmove | break | urenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 376 | 2830 | 129 | 164 | 668 | 3190 | 1 | 24 |
| mmove | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 372 | 2754 | 256 | 494 | 1132 | 2119 | 1 | 24 |
| mmove | false_break | pnf_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 725 | 2415 | -539 | 579 | 564 | 1343 | 1 | 24 |
| mmove | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | sym15u / both | 311 | 2510 | -527 | 2112 | 2404 | 983 | 1 | 24 |
| mmove | reject | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 89 | 2172 | -113 | 1317 | 220 | 2986 | 1 | 24 |
| mmove | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 494 | 2494 | -127 | -205 | -307 | 3948 | 1 | 24 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 270 | 4009 | -265 | 707 | 166 | 4154 | 1 | 24 |
| mmove | retest_native | urenko_56 | {"M": 6, "tol": 0.5} | plain60/60 / both | 413 | 3240 | 7 | 922 | 1255 | 5022 | 1 | 24 |
| ob15 | break | mrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 87 | 1145 | -110 | 211 | 463 | 1243 | 1 | 24 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 1 | 24 |
| ob15 | false_break | mrenko_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 95 | 527 | 393 | 352 | 362 | 815 | 1 | 24 |
| ob15 | false_break_native | mrenko_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 95 | 527 | 409 | 357 | 362 | 815 | 1 | 24 |
| ob15 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 62 | 791 | -118 | 315 | -442 | 1181 | 1 | 24 |
| ob15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 36 | 1149 | -142 | -159 | -172 | 1420 | 1 | 24 |
| ob15 | retest | mrenko_10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 | 729 | 168 | 295 | -73 | 1126 | 1 | 24 |
| ob15 | retest_native | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 79 | 942 | 14 | -160 | 421 | 1025 | 1 | 24 |
| ob5 | break | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 149 | 1842 | -177 | -402 | 80 | 2067 | 1 | 24 |
| ob5 | break_native | pnf_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 204 | 1691 | -87 | 173 | 841 | 2373 | 1 | 24 |
| ob5 | false_break | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 39 | 1216 | 28 | 406 | 1050 | 1397 | 1 | 24 |
| ob5 | false_break_native | urenko_40 | {"M": 3, "k": 0.5} | sym15u / both | 115 | 1109 | -143 | 486 | 1724 | 1968 | 1 | 24 |
| ob5 | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 108 | 1365 | -64 | -121 | 668 | 1620 | 1 | 24 |
| ob5 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 141 | 1931 | -100 | -653 | -1218 | 2401 | 1 | 24 |
| ob5 | retest | mrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1697 | 111 | -230 | 324 | 2333 | 1 | 24 |
| ob5 | retest_native | mrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1697 | 111 | -230 | 324 | 2333 | 1 | 24 |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 192 |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 53 | 1298 | 117 | 673 | 306 | 1466 | 2 | 192 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 192 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 192 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 192 |
| open_range | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 1841 | -107 | -871 | 61 | 1790 | 1 | 192 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 192 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 192 |
| opens | break | tick_800 | {"n": 1, "k": 0.5} | asym10u/20u / both | 187 | 3057 | -72 | -628 | 803 | 3795 | 2 | 195 |
| opens | break_native | renko_10 | {"n": 2, "k": 0.25} | asym20u/10u / both | 287 | 3101 | -120 | -401 | 418 | 3462 | 2 | 195 |
| opens | false_break | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 195 |
| opens | false_break_native | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 195 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 195 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 195 |
| opens | retest | tm10 | {"M": 3, "tol": 0.5} | sym15u / both | 435 | 3568 | -310 | -114 | -1092 | 4604 | 2 | 195 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 195 |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 195 |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 195 |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 2 | 195 |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 2 | 195 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 195 |
| prior_day | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 195 |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 2 | 195 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 195 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 194 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 194 |
| profile_nodes | false_break | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 556 | 3365 | -801 | 527 | 801 | 3841 | 2 | 194 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 194 |
| profile_nodes | reject | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 217 | 3451 | -794 | -877 | -1862 | 3671 | 2 | 194 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 194 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 1 | 194 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 295 | 4808 | -512 | 139 | 1484 | 5809 | 1 | 194 |
| profile_va | break | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 3734 | 98 | -1260 | -135 | 2075 | 1 | 195 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 195 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 1 | 195 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 1 | 195 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 195 |
| profile_va | reject_native | rng_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 523 | 3959 | 232 | -523 | -699 | 2840 | 2 | 195 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 195 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 1 | 195 |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2 | 195 |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 2 | 195 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 195 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 195 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 195 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 195 |
| round | retest | vsess_50 | {"M": 3, "tol": 0.0} | plain60/60 / both | 480 | 4161 | -390 | -850 | -175 | 4245 | 1 | 195 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 1 | 195 |
| session_hl | break | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 193 |
| session_hl | break_native | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 193 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym15u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 1 | 193 |
| session_hl | false_break_native | mom_112 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1310 | 345 | -28 | -555 | 1077 | 1 | 193 |
| session_hl | reject | swing_pct_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 31 | 966 | 156 | 215 | 82 | 717 | 1 | 193 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 193 |
| session_hl | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 930 | 394 | -159 | 104 | 1490 | 1 | 193 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 1 | 193 |
| trendline | break | mrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 526 | 3572 | 44 | -196 | 284 | 4807 | 1 | 24 |
| trendline | break_native | urenko_28 | {"n": 3, "k": 0.5} | sym15u / both | 261 | 2923 | 52 | -239 | -142 | 3559 | 1 | 24 |
| trendline | false_break | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 2652 | 5 | 374 | -456 | 3314 | 1 | 24 |
| trendline | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 290 | 2491 | 555 | -381 | 1308 | 960 | 1 | 24 |
| trendline | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 249 | 2489 | -856 | 1637 | -467 | 1528 | 1 | 24 |
| trendline | reject_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 3233 | -304 | 1786 | -548 | 2457 | 1 | 24 |
| trendline | retest | pnf_5 | {"M": 6, "tol": 0.5} | sym15u / both | 249 | 2608 | -316 | -1062 | 473 | 1716 | 1 | 24 |
| trendline | retest_native | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 223 | 2060 | 123 | 943 | 842 | -459 | 1 | 24 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 194 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 194 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 194 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 194 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 194 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 1 | 194 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 194 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 194 |
| uw_ndx | break | renko_14 | {"n": 2, "k": 0.5} | sym8u / both | 331 | 2910 | 0 | -114 | 269 | 2774 | 2 | 194 |
| uw_ndx | break_native | renko_28 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 2821 | 0 | 832 | 1783 | 4375 | 2 | 194 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 194 |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 296 | 2751 | 0 | 605 | 329 | 2931 | 2 | 194 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 194 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 194 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 194 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 194 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 194 |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 444 | 3333 | 0 | 825 | 798 | 2619 | 2 | 194 |
| uw_qqq | false_break | cusum_112 | {"M": 1, "k": 0.0} | sym15u / both | 189 | 2553 | 0 | -215 | 1193 | 2621 | 1 | 194 |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 228 | 2553 | 0 | -518 | 1669 | 3080 | 2 | 194 |
| uw_qqq | reject | rng_28 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 487 | 3819 | 0 | 532 | -3 | 3522 | 2 | 194 |
| uw_qqq | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 585 | 4310 | 0 | 145 | -321 | 3898 | 2 | 194 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 194 |
| uw_qqq | retest_native | renko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 252 | 2711 | 0 | -192 | 815 | 3673 | 2 | 194 |
| vwap | break | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 194 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 194 |
| vwap | false_break | pasl_10 | {"M": 1, "k": 0.0} | sym15u / both | 272 | 3707 | 24 | -1009 | 1272 | 5049 | 1 | 194 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 194 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 194 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 194 |
| vwap | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym30u / both | 244 | 3984 | 745 | -933 | 4153 | 6617 | 2 | 194 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 194 |
| vwap_bands | break | dlt_30 | {"n": 2, "k": 0.25} | sym15u / both | 342 | 4036 | -365 | -1198 | -1134 | 3306 | 1 | 193 |
| vwap_bands | break_native | time_m_2 | {"n": 2, "k": 0.25} | sym15u / both | 309 | 4019 | -106 | -2428 | -2221 | 2246 | 1 | 193 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 193 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 193 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 193 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 193 |
| vwap_bands | retest | dib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 483 | 3490 | -310 | -978 | -792 | 2632 | 1 | 193 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 193 |
| week_month | break | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 44 | 1289 | -193 | -513 | -213 | 813 | 2 | 195 |
| week_month | break_native | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 44 | 1289 | -193 | -513 | -213 | 813 | 2 | 195 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 195 |
| week_month | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 53 | 1816 | -233 | -4 | 426 | 2452 | 1 | 195 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 195 |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | 1233 | -161 | 407 | -240 | 443 | 1 | 195 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 195 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 195 |
| zones | break | rng_40 | {"n": 1, "k": 0.5} | sym8u / both | 199 | 3211 | 33 | 78 | 580 | 2604 | 2 | 194 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 194 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 194 |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 177 | 2863 | -154 | 660 | -299 | 2423 | 2 | 194 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 196 | 3254 | -73 | -1065 | -502 | 3105 | 1 | 194 |
| zones | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 278 | 3157 | -1008 | -1664 | -1608 | 2818 | 2 | 194 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 194 |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 161 | 2948 | -119 | -238 | 150 | 2390 | 2 | 194 |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 7251 of 9120 (modules x 304 bar rows); pass-1 result files written in the last hour: 1087 (all modules); ETA for these at that rate if they were alone: 6.7 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

