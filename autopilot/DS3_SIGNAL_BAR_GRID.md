# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 11:00Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 15238 | 400 | 0.000 | -0.65 / -0.62 / -0.60 / -1.00 | YES | {"Asia": 0.837, "London": 0.835, "NYAM": 0.835, "NYPM": 0.836} |  |
| p1rand2 | 15204 | 400 | 0.000 | -0.63 / -0.62 / -0.63 / -1.01 | YES | {"Asia": 0.833, "London": 0.83, "NYAM": 0.831, "NYPM": 0.832} |  |
| p1rand3 | 222 | 222 | 0.000 | -0.67 / -0.59 / -0.60 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand4 | 222 | 222 | 0.000 | -0.66 / -0.59 / -0.60 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 222 | 222 | 0.000 | -0.68 / -0.61 / -0.59 / -1.02 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 11:00Z):** result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 15501, "p1rand2": 15462, "p1rand3": 222, "p1rand4": 222, "p1rand5": 222, "p1real": 22686, "p1realx": 219, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 2, "London": 2, "NYAM": 2, "NYPM": 2}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 11:00Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 15501, "p1rand2": 15462, "p1rand3": 222, "p1rand4": 222, "p1rand5": 222, "p1real": 22686, "p1realx": 219, "rand1": 0, "real": 1654}; loop status: 2026-11-18T10:46Z rows=322 mods=146 todo=86271 running=0. 
Cells scored per session: {"Asia": 3487598, "London": 3377734, "NYAM": 3645380, "NYPM": 3660350}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -18.3 | -0.017 | 1064.9 | 0.43 | -27.7 | -78.3 | 3.1 | 23.3 | -21.4 | 0.00 | -20.4 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -16.7 | -0.010 | 992.2 | 0.43 | -26.5 | -64.3 | 8.2 | 16.3 | -24.9 | 0.00 | -19.6 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -52.8 [-71.4; 0.00] | -29.6 [-30.6; 0.00] | -11.6 [-28.9; 0.00] | 2.5 [0.6; 0.50] |
| bands (native) | -29.4 [-6.1; 0.00] | -9.7 [-15.7; 0.00] | -19.4 [-3.2; 0.50] | -22.5 [-0.8; 0.50] |
| barnative | -12.7 [6.0; 0.50] | 5.3 [27.0; 1.00] | 8.2 [34.4; 1.00] | -14.4 [-1.4; 0.50] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -8.4 [0.1; 0.50] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 11.9 [21.4; 1.00] | n/a (no signals by construction) |
| confluence | -17.7 [-30.3; 0.00] | -14.0 [-0.2; 0.50] | 0.9 [-4.3; 0.50] | 14.7 [18.2; 1.00] |
| levels | -21.3 [-10.4; 0.50] | -28.0 [-32.0; 0.00] | 28.6 [43.2; 1.00] | -23.2 [-29.5; 0.00] |
| levels (native) | -22.3 [-17.6; 0.50] | 2.1 [25.9; 1.00] | 13.6 [12.7; 1.00] | -14.9 [17.3; 1.00] |
| live | -1.4 [9.7; 1.00] | -16.9 [-24.9; 0.00] | 1.5 [23.3; 1.00] | 6.3 [-4.3; 0.50] |
| manual | -8.5 [8.6; 0.50] | -5.2 [-19.0; 0.00] | -36.6 [-25.9; 0.00] | -5.0 [5.1; 0.50] |
| manual (native) | 4.4 [8.3; 1.00] | -30.5 [-37.5; 0.00] | -17.6 [-0.9; 0.50] | -27.1 [0.7; 0.50] |
| momentum | 3.7 [10.5; 0.50] | 14.9 [28.8; 1.00] | -12.2 [-1.6; 0.50] | -4.9 [1.9; 0.50] |
| momentum (native) | -37.6 [-12.4; 0.00] | -29.0 [-36.7; 0.00] | 0.2 [-4.0; 0.00] | -8.1 [1.3; 0.50] |
| pullback | -14.2 [-12.3; 0.50] | -9.2 [-0.6; 0.50] | 15.1 [-13.3; 0.00] | -4.6 [19.9; 1.00] |
| pullback (native) | -16.7 [-0.1; 0.50] | -0.1 [1.4; 0.50] | 1.0 [34.7; 1.00] | -39.7 [-24.6; 0.00] |
| structure | -17.0 [-24.9; 0.00] | -18.0 [-33.6; 0.00] | -32.1 [-21.4; 0.00] | -20.1 [10.7; 0.50] |
| structure (native) | -18.8 [-35.0; 0.00] | -19.7 [-7.1; 0.00] | -3.1 [3.6; 0.50] | -33.3 [-29.7; 0.00] |
| tape | -12.6 [-15.7; 0.50] | -17.3 [-1.2; 0.00] | -19.7 [-14.4; 0.50] | -14.9 [1.4; 0.50] |
| tape (native) | -21.0 [-33.9; 0.00] | -18.3 [16.7; 1.00] | -12.4 [5.3; 0.50] | -38.4 [-21.5; 0.00] |
| trend | -17.5 [-16.7; 0.00] | -16.7 [16.2; 0.50] | -14.8 [-7.6; 0.00] | 9.0 [35.7; 1.00] |
| trend (native) | -13.2 [-4.9; 0.50] | -8.8 [-8.2; 0.00] | -25.4 [-12.4; 0.50] | -7.2 [-8.9; 0.50] |
| xmarket | -4.0 [-23.9; 0.00] | -23.0 [-24.8; 0.00] | -3.3 [5.4; 1.00] | -8.9 [-7.1; 0.50] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels|PRICE | 28.6 | 0.021 | 179.9 | 0.70 | 16.2 | 15.6 | {"2023": 13.5, "2024": 26.4, "2025": 47.4, "2026": 13.8} | -14.6 | 43.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|PRICE | 15.1 | 0.012 | 519.4 | 0.54 | 81.9 | 115.9 | {"2023": -7.2, "2024": -6.8, "2025": 25.0, "2026": 36.4} | 28.4 | -13.3 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum|INFORMATION | 14.9 | 0.024 | 304.8 | 0.57 | -26.0 | -60.3 | {"2023": -15.5, "2024": 56.6, "2025": 6.1, "2026": -14.5} | -13.9 | 28.8 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| confluence|TIME | 14.7 | 0.017 | 190.5 | 0.53 | 40.3 | -23.0 | {"2023": -4.8, "2024": 9.5, "2025": 13.4, "2026": 28.7} | -3.4 | 18.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 13.6 | 0.015 | 476.8 | 0.53 | 36.7 | 83.2 | {"2023": 38.9, "2024": 13.1, "2025": -11.4, "2026": 35.6} | 0.9 | 12.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| book (native)|PRICE | 11.9 | 0.008 | 409.9 | 0.53 | 14.2 | -170.5 | {"2023": -11.4, "2024": 9.4, "2025": -4.7, "2026": 42.0} | -9.4 | 21.4 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| trend|TIME | 9.0 | 0.015 | 622.2 | 0.53 | -100.9 | 41.0 | {"2023": 6.9, "2024": 23.5, "2025": 30.1, "2026": -32.6} | -26.7 | 35.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| barnative|PRICE | 8.2 | 0.006 | 487.6 | 0.48 | 43.4 | 47.8 | {"2023": 13.0, "2024": -27.9, "2025": 39.1, "2026": 12.9} | -26.2 | 34.4 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| live|TIME | 6.3 | 0.006 | 538.3 | 0.54 | 81.1 | 29.7 | {"2023": -30.4, "2024": -12.7, "2025": -14.9, "2026": 65.7} | 10.6 | -4.3 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| barnative|INFORMATION | 5.3 | 0.000 | 795.6 | 0.52 | 61.9 | 76.1 | {"2023": 29.5, "2024": 30.3, "2025": -12.4, "2026": -11.0} | -21.7 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.2%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.2%); U7 tm600 L6M -10.7 pts/wk, rank 33% (top 67.5%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.2%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 38.1%); A7 tm60 L6M 14.3 pts/wk, rank 79% (top 20.7%). Rank = share of ALL London cells with a lower trailing-26w result.

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
| 12 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 766.0, "2024": 1526.0, "2025": 18.0, "2026": 5170.0} |
| 13 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 14 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 812.0, "2024": 1425.0, "2025": 18.0, "2026": 5170.0} |
| 15 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym30u | both | 5528 | 2119 | 220 | 1.00 | 5 / -257 / 968 / 1.00 | {"2023": 677.0, "2024": -476.0, "2025": -2538.0, "2026": 6998.0} |
| 16 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym10u/20u | both | 5527 | 1802 | 260 | 1.00 | 5 / -84 / 712 / 1.00 | {"2023": 418.0, "2024": -2082.0, "2025": -1357.0, "2026": 6422.0} |
| 17 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | 5 / -350 / 2382 / 1.00 | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 18 | swing_atr_0.1 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -469 / 2733 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |
| 19 | swing_atr_0.1 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -397 / 391 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |
| 20 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym30u | both | 5463 | 2464 | 237 | 1.00 | 5 / -166 / 2075 / 1.00 | {"2023": 826.0, "2024": -692.0, "2025": -822.0, "2026": 5499.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 46.2 | 0.029 | 288.4 | 0.60 | 60.5 | 91.3 | -39.9 | -35.5 | 86.1 | 1.00 | 6.4 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 47.3 | 0.031 | 297.8 | 0.60 | 46.8 | 91.3 | -15.8 | -14.0 | 63.1 | 1.00 | 8.8 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 28.6 [12.4; 1.00] | 1.6 [-8.7; 0.50] | 15.3 [10.9; 0.50] | 30.1 [21.2; 1.00] |
| bands (native) | 3.2 [6.5; 0.50] | 1.9 [6.1; 0.50] | 9.0 [46.1; 1.00] | 30.0 [65.6; 1.00] |
| barnative | -15.3 [11.7; 0.50] | -25.9 [-38.4; 0.00] | 44.8 [88.1; 1.00] | 11.1 [-13.6; 0.00] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -18.0 [17.0; 0.50] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 12.3 [16.7; 0.50] | n/a (no signals by construction) |
| confluence | 13.5 [40.0; 1.00] | -6.4 [-2.8; 0.50] | 41.9 [41.6; 1.00] | 1.9 [1.9; 0.50] |
| levels | 7.9 [32.5; 1.00] | -25.5 [20.0; 0.50] | 7.7 [36.0; 1.00] | -1.3 [-22.3; 0.50] |
| levels (native) | 27.5 [32.2; 1.00] | 16.0 [51.6; 1.00] | 10.1 [42.0; 1.00] | -9.2 [6.7; 0.50] |
| live | 17.8 [27.8; 0.50] | 4.6 [21.0; 1.00] | 10.4 [-8.3; 0.00] | -10.3 [-5.0; 0.50] |
| manual | 28.8 [46.7; 1.00] | 40.1 [106.4; 1.00] | -6.2 [-22.9; 0.00] | 33.3 [37.0; 1.00] |
| manual (native) | -67.2 [-36.2; 0.00] | -58.7 [-72.0; 0.00] | -22.8 [-36.3; 0.00] | -16.6 [1.6; 0.50] |
| momentum | 30.1 [13.7; 1.00] | 8.4 [15.6; 1.00] | -6.5 [-34.5; 0.00] | 39.8 [27.0; 1.00] |
| momentum (native) | -8.4 [9.6; 0.50] | 4.0 [10.3; 1.00] | 41.2 [49.3; 1.00] | 36.0 [48.2; 1.00] |
| pullback | 21.6 [38.7; 1.00] | 22.6 [44.8; 1.00] | -17.8 [20.3; 1.00] | -1.4 [11.6; 1.00] |
| pullback (native) | 26.2 [47.0; 1.00] | -4.6 [8.7; 1.00] | -2.7 [31.5; 1.00] | -18.9 [5.1; 0.50] |
| structure | 20.4 [20.2; 1.00] | -6.3 [8.7; 0.50] | 26.9 [56.7; 1.00] | -0.9 [24.2; 0.50] |
| structure (native) | 36.8 [69.6; 1.00] | 40.8 [49.7; 1.00] | 2.9 [-3.4; 0.50] | 38.2 [42.6; 1.00] |
| tape | 1.7 [-19.3; 0.50] | -37.2 [-30.5; 0.00] | 7.1 [-1.5; 0.50] | 22.6 [27.1; 1.00] |
| tape (native) | -6.8 [-5.3; 0.50] | -24.2 [-41.6; 0.00] | 4.7 [16.4; 0.50] | 0.3 [-12.4; 0.00] |
| trend | -17.9 [-38.6; 0.00] | -6.0 [1.5; 0.50] | -7.7 [4.9; 1.00] | -4.5 [18.6; 1.00] |
| trend (native) | -58.7 [-68.4; 0.00] | -21.9 [12.5; 1.00] | 21.6 [39.8; 1.00] | -23.4 [-11.6; 0.50] |
| xmarket | -13.3 [-10.3; 0.00] | -24.9 [-17.8; 0.50] | 11.2 [15.9; 1.00] | -19.2 [-19.1; 0.50] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 44.8 | 0.018 | 563.7 | 0.58 | 45.9 | -36.9 | {"2023": -29.3, "2024": -23.3, "2025": 104.9, "2026": 77.7} | -43.3 | 88.1 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| confluence|PRICE | 41.9 | 0.027 | 387.9 | 0.54 | 58.2 | -121.7 | {"2023": 89.5, "2024": -14.0, "2025": 63.5, "2026": 67.4} | 0.3 | 41.6 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 41.2 | 0.023 | 536.1 | 0.56 | -6.9 | 4.4 | {"2023": -10.0, "2024": -12.6, "2025": 87.7, "2026": 66.1} | -8.0 | 49.3 | 1.00 | {"2023": "AMBER", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 40.8 | 0.026 | 575.2 | 0.59 | 66.4 | 44.7 | {"2023": 56.8, "2024": 0.4, "2025": 94.7, "2026": 19.6} | -9.0 | 49.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 40.1 | 0.025 | 425.4 | 0.59 | 73.0 | -52.6 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 52.5} | -66.3 | 106.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 39.8 | 0.023 | 654.3 | 0.57 | 96.6 | 167.5 | {"2023": 22.0, "2024": 70.5, "2025": 52.6, "2026": -6.1} | 12.8 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} | -4.4 | 42.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 36.8 | 0.024 | 824.1 | 0.60 | -16.6 | 60.5 | {"2023": 51.5, "2024": 23.8, "2025": 94.6, "2026": -20.9} | -32.9 | 69.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 36.0 | 0.023 | 864.9 | 0.54 | 71.5 | 198.2 | {"2023": 22.0, "2024": 86.3, "2025": 52.6, "2026": -38.6} | -12.1 | 48.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | -3.7 | 37.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 6% (top 94.0%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 56.6%); U7 tm600 L6M -11.4 pts/wk, rank 40% (top 59.6%); P7 tm60 L6M -60.7 pts/wk, rank 10% (top 90.4%); H7 tm60 L6M 28.8 pts/wk, rank 86% (top 13.7%); A7 tm60 L6M -17.2 pts/wk, rank 34% (top 65.6%); O7 tm60 L6M 15.1 pts/wk, rank 77% (top 22.9%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

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
| 3 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym15u | both | 8330 | 2851 | 454 | 1.00 | 2 / -936 / 215 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 4 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym20u/10u | both | 8284 | 2906 | 505 | 1.00 | 5 / 378 / 3088 / 1.00 | {"2023": -852.0, "2024": -683.0, "2025": 2764.0, "2026": 7588.0} |
| 5 | kagi_28 | levels.levels_swsr5.false_break_native | {"M": 2, "k": 0.5} | sym15u | both | 8188 | 3060 | 432 | 1.00 | 2 / 3437 / 5586 / 1.00 | {"2023": 1948.0, "2024": -2061.0, "2025": 866.0, "2026": 8579.0} |
| 6 | swing_atr_0.1 | tape.tape_speed.follow_native | {"f": 3.0, "L": 3600} | sym15u | both | 8142 | 2340 | 562 | 1.00 | 5 / -371 / 1825 / 1.00 | {"2023": -2474.0, "2024": -2255.0, "2025": 763.0, "2026": 10386.0} |
| 7 | mrenko_14 | book.book_sweep.cnt_fade | {"thr": 1} | plain60/60 | both | 8102 | 4824 | 1744 | 1.00 | 2 / -2743 / -2138 / 1.00 | {"2023": 369.0, "2024": -2136.0, "2025": -998.0, "2026": 6430.0} |
| 8 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | sym30u | both | 8082 | 2155 | 480 | 1.00 | 5 / 602 / 1633 / 1.00 | {"2023": 547.0, "2024": 474.0, "2025": 3963.0, "2026": 8386.0} |
| 9 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym15u/30u | both | 8038 | 3705 | 499 | 1.00 | 5 / 704 / 3235 / 1.00 | {"2023": 16.0, "2024": 1506.0, "2025": 4489.0, "2026": 6565.0} |
| 10 | renko_10 | levels.levels_round.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 8023 | 656 | 657 | 0.67 | 5 / -146 / 2906 / 1.00 | {"2023": -600.0, "2024": -3119.0, "2025": -4002.0, "2026": 8822.0} |
| 11 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym15u | both | 8013 | 3680 | 500 | 1.00 | 5 / 677 / 3228 / 1.00 | {"2023": -200.0, "2024": 1750.0, "2025": 4356.0, "2026": 6540.0} |
| 12 | vsess_450 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | asym15u/30u | both | 7960 | 3412 | 531 | 0.83 | 5 / -1909 / 1527 / 1.00 | {"2023": -1290.0, "2024": 1149.0, "2025": -12.0, "2026": 9238.0} |
| 13 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym10u/20u | both | 7943 | 3967 | 504 | 1.00 | 5 / 766 / 3407 / 1.00 | {"2023": 648.0, "2024": 1861.0, "2025": 5118.0, "2026": 6144.0} |
| 14 | vol_350 | levels.levels_round.break | {"n": 3, "k": 0.5} | sym8u | both | 7909 | 2632 | 645 | 1.00 | 5 / -866 / 424 / 1.00 | {"2023": -295.0, "2024": -2844.0, "2025": 582.0, "2026": 6211.0} |
| 15 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym30u | both | 7895 | 3566 | 499 | 1.00 | 5 / 707 / 3316 / 1.00 | {"2023": -294.0, "2024": 898.0, "2025": 4173.0, "2026": 6422.0} |
| 16 | rng_14 | structure.structure_libpattern.pin | {"k": 2.0, "filt": 0} | asym20u/10u | both | 7856 | 1051 | 651 | 0.50 | 5 / -794 / 236 / 1.00 | {"2023": 229.0, "2024": 581.0, "2025": -3440.0, "2026": 2714.0} |
| 17 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | sym15u | both | 7764 | 2031 | 485 | 1.00 | 5 / 647 / 1691 / 1.00 | {"2023": 100.0, "2024": 1062.0, "2025": 4709.0, "2026": 8127.0} |
| 18 | vol_350 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | sym30u | both | 7714 | 4377 | 491 | 1.00 | 5 / -835 / 1210 / 1.00 | {"2023": 210.0, "2024": 678.0, "2025": 6774.0, "2026": 7589.0} |
| 19 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | asym15u/30u | both | 7709 | 1976 | 483 | 1.00 | 5 / 675 / 1781 / 1.00 | {"2023": 487.0, "2024": 1185.0, "2025": 4743.0, "2026": 8084.0} |
| 20 | vol_350 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym30u | both | 7696 | 4091 | 488 | 1.00 | 5 / -185 / 4832 / 1.00 | {"2023": 513.0, "2024": -317.0, "2025": 6915.0, "2026": 6928.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -29.5 | -0.015 | 1999.3 | 0.43 | 44.8 | 69.9 | 1.6 | 11.3 | -31.1 | 0.00 | 7.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | -21.0 | -0.009 | 1712.3 | 0.47 | 44.8 | 69.9 | -12.0 | -3.9 | -9.0 | 0.00 | 12.0 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -15.3 [-13.1; 0.50] | 3.1 [12.7; 0.50] | 19.9 [44.8; 1.00] | -19.9 [-8.1; 0.50] |
| bands (native) | 22.6 [27.0; 1.00] | 2.3 [-22.4; 0.00] | -2.2 [32.0; 1.00] | -24.5 [-37.2; 0.00] |
| barnative | -27.0 [-39.7; 0.00] | -6.5 [9.4; 1.00] | -3.1 [7.9; 1.00] | -19.2 [-53.6; 0.00] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | 2.1 [-20.0; 0.50] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | -1.8 [0.4; 0.50] | n/a (no signals by construction) |
| confluence | 1.5 [15.7; 1.00] | 4.6 [-16.5; 0.00] | -34.9 [-13.1; 0.00] | -18.3 [-35.4; 0.00] |
| levels | 2.4 [-13.8; 0.00] | -40.4 [-37.8; 0.00] | -20.1 [-16.1; 0.50] | 9.4 [25.3; 1.00] |
| levels (native) | -11.2 [18.1; 1.00] | -11.8 [-10.2; 0.00] | -29.7 [-15.2; 0.50] | -31.2 [-5.8; 0.50] |
| live | -31.3 [-3.4; 0.50] | -33.5 [-24.5; 0.00] | -13.6 [-39.6; 0.00] | -16.8 [-48.1; 0.00] |
| manual | -19.7 [-52.8; 0.00] | -27.7 [-34.7; 0.00] | 13.9 [13.0; 1.00] | -12.8 [-12.1; 0.50] |
| manual (native) | 25.7 [43.0; 0.50] | 7.4 [16.1; 0.50] | 17.9 [-9.4; 0.50] | -32.2 [-14.9; 0.50] |
| momentum | -5.0 [0.9; 0.50] | -11.6 [16.9; 0.50] | 1.8 [37.6; 1.00] | -2.0 [-5.5; 0.50] |
| momentum (native) | 19.9 [31.0; 1.00] | -41.6 [-39.5; 0.00] | 16.5 [26.5; 1.00] | -9.9 [-5.2; 0.50] |
| pullback | -38.4 [-51.9; 0.00] | -6.7 [-31.4; 0.00] | -29.0 [-1.6; 0.00] | -10.2 [13.2; 1.00] |
| pullback (native) | -6.3 [27.0; 0.50] | -69.1 [-61.7; 0.00] | 0.8 [19.0; 1.00] | -20.2 [1.3; 0.50] |
| structure | 24.5 [32.0; 1.00] | -14.0 [11.9; 1.00] | -38.8 [-27.2; 0.00] | 22.5 [32.0; 1.00] |
| structure (native) | 5.2 [-3.1; 0.50] | -23.2 [-10.1; 0.50] | -25.2 [-6.8; 0.50] | 23.2 [40.9; 1.00] |
| tape | 18.1 [15.0; 1.00] | 31.5 [-6.9; 0.50] | -13.2 [-15.9; 0.00] | -37.4 [-8.8; 0.00] |
| tape (native) | -2.3 [33.3; 1.00] | -23.1 [-22.5; 0.00] | 19.1 [30.3; 1.00] | -1.5 [0.4; 0.50] |
| trend | 5.0 [40.3; 1.00] | -5.7 [-2.7; 0.50] | 19.1 [39.0; 1.00] | 17.8 [0.6; 0.50] |
| trend (native) | 33.5 [39.9; 1.00] | -10.3 [-18.2; 0.00] | -2.4 [2.8; 0.50] | 15.2 [32.7; 1.00] |
| xmarket | 9.6 [25.1; 1.00] | -26.9 [-35.6; 0.00] | 5.8 [-8.0; 0.50] | -16.5 [0.3; 0.50] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| trend (native)|ACTIVITY | 33.5 | 0.032 | 404.1 | 0.56 | 35.2 | 33.9 | {"2023": -11.0, "2024": 33.1, "2025": 64.3, "2026": 11.8} | -6.4 | 39.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|INFORMATION | 31.5 | 0.013 | 422.8 | 0.57 | -42.2 | 22.3 | {"2023": 54.3, "2024": -20.8, "2025": 95.6, "2026": 10.3} | 38.4 | -6.9 | 0.50 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual (native)|ACTIVITY | 25.7 | 0.031 | 366.0 | 0.54 | 48.5 | 6.0 | {"2023": -42.5, "2024": -13.5, "2025": 82.6, "2026": 26.6} | -17.2 | 43.0 | 0.50 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure|ACTIVITY | 24.5 | 0.009 | 788.4 | 0.49 | 102.6 | 189.5 | {"2023": 0.5, "2024": -6.3, "2025": 12.7, "2026": 82.5} | -7.5 | 32.0 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 23.2 | 0.022 | 469.8 | 0.58 | 40.4 | -3.8 | {"2023": 49.7, "2024": 5.8, "2025": -1.5, "2026": 64.7} | -17.6 | 40.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 22.6 | 0.030 | 294.3 | 0.54 | 11.8 | -93.6 | {"2023": 25.8, "2024": 55.4, "2025": 27.5, "2026": -22.9} | -4.4 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|TIME | 22.5 | 0.020 | 875.2 | 0.57 | 127.0 | 175.4 | {"2023": -36.0, "2024": 18.3, "2025": -26.9, "2026": 104.6} | -9.5 | 32.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 19.9 | 0.013 | 536.5 | 0.49 | -64.2 | -32.6 | {"2023": 75.2, "2024": 42.8, "2025": 44.5, "2026": -53.7} | -24.8 | 44.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|ACTIVITY | 19.9 | 0.021 | 595.8 | 0.53 | 100.3 | 100.5 | {"2023": 101.2, "2024": 22.2, "2025": -39.2, "2026": 61.2} | -11.1 | 31.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape (native)|PRICE | 19.1 | 0.013 | 1001.2 | 0.48 | 111.9 | -74.3 | {"2023": -62.2, "2024": -41.5, "2025": 32.6, "2026": 100.5} | -11.2 | 30.3 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 23% (top 77.3%); M7 tm60 L6M -36.8 pts/wk, rank 14% (top 86.0%); U7 tm600 L6M 4.8 pts/wk, rank 61% (top 39.1%); P7 tm60 L6M -35.9 pts/wk, rank 14% (top 85.6%); H7 tm60 L6M -20.1 pts/wk, rank 25% (top 75.5%); A7 tm60 L6M -32.5 pts/wk, rank 16% (top 83.8%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

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
| 3 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym10u/20u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1046.0, "2024": -1508.0, "2025": 3102.0, "2026": 7745.0} |
| 4 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym20u/10u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1266.0, "2024": -1067.0, "2025": 3095.0, "2026": 7745.0} |
| 5 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym15u/30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 6 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 7 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym8u | both | 6722 | 2181 | 270 | 1.00 | 5 / 507 / 1497 / 1.00 | {"2023": -1094.0, "2024": -1432.0, "2025": 3159.0, "2026": 7746.0} |
| 8 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 10, "r": 0.6} | plain60/60 | both | 6610 | 590 | 1034 | 1.00 | 5 / -1524 / -356 / 1.00 | {"2023": -294.0, "2024": 1303.0, "2025": 3131.0, "2026": 6965.0} |
| 9 | pnf_20 | levels.levels_sdx_vol1100.lim_mid | {"d": "E", "F": 9, "tgt": "r2"} | sym15u | both | 6337 | 2070 | 275 | 1.00 | 2 / -899 / 240 / 1.00 | {"2023": -998.0, "2024": 71.0, "2025": 1443.0, "2026": 6397.0} |
| 10 | pnf_5 | book.book_ofi.follow | {"L": 100, "z": 1.5} | sym15u | both | 6242 | 3060 | 328 | 1.00 | 2 / 72 / 1067 / 1.00 | {"2023": 1290.0, "2024": -755.0, "2025": -3099.0, "2026": 6638.0} |
| 11 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym15u/30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 419 / 1855 / 1.00 | {"2023": -306.0, "2024": 1499.0, "2025": -1131.0, "2026": 6319.0} |
| 12 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 398 / 1855 / 1.00 | {"2023": -927.0, "2024": 1201.0, "2025": -1574.0, "2026": 6224.0} |
| 13 | tm10 | trend.trend_ma_hma.cross | {"len": 21, "width": 4, "hyst": 0.0} | plain60/60 | both | 6076 | 1146 | 908 | 1.00 | 5 / 182 / 1688 / 1.00 | {"2023": -1233.0, "2024": -756.0, "2025": 2796.0, "2026": 6659.0} |
| 14 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym10u/20u | both | 6072 | 2310 | 311 | 1.00 | 5 / 453 / 1701 / 1.00 | {"2023": -508.0, "2024": 1153.0, "2025": -2178.0, "2026": 6086.0} |
| 15 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | asym15u/30u | both | 6046 | 1396 | 308 | 0.75 | 5 / -137 / 1458 / 1.00 | {"2023": -2011.0, "2024": 1321.0, "2025": -300.0, "2026": 5317.0} |
| 16 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym15u | both | 6039 | 2351 | 303 | 1.00 | 5 / 454 / 1959 / 1.00 | {"2023": -93.0, "2024": 1981.0, "2025": -1045.0, "2026": 6138.0} |
| 17 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | sym30u | both | 6039 | 1385 | 308 | 0.75 | 5 / -94 / 1351 / 1.00 | {"2023": -2595.0, "2024": 1415.0, "2025": -287.0, "2026": 5508.0} |
| 18 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | sym15u | both | 5981 | 1331 | 310 | 0.75 | 5 / -124 / 1479 / 1.00 | {"2023": -1974.0, "2024": 1669.0, "2025": -713.0, "2026": 5066.0} |
| 19 | cusum_28 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym8u | both | 5937 | 1863 | 338 | 1.00 | 5 / 380 / 2239 / 1.00 | {"2023": -46.0, "2024": -2789.0, "2025": 246.0, "2026": 7789.0} |
| 20 | dib_400 | trend.trend_ma_hma.cross_native | {"len": 8, "width": 1.0, "ratio": 3} | asym10u/20u | both | 5902 | 1702 | 1158 | 1.00 | 5 / 534 / 2839 / 1.00 | {"2023": -1702.0, "2024": 1031.0, "2025": -505.0, "2026": 3945.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -12.6 | -0.011 | 1129.4 | 0.48 | -24.4 | -82.2 | -12.3 | -3.9 | -0.3 | 0.50 | -3.5 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -10.7 | -0.010 | 1017.7 | 0.49 | -24.4 | -82.2 | 5.5 | 9.0 | -16.2 | 0.00 | -3.0 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 8.0 [8.9; 1.00] | 26.9 [9.6; 0.50] | 18.0 [35.2; 1.00] | 9.7 [9.5; 1.00] |
| bands (native) | 12.0 [10.8; 1.00] | 4.1 [-2.8; 0.50] | 23.2 [26.5; 1.00] | 8.7 [13.6; 1.00] |
| barnative | 14.8 [32.5; 1.00] | 1.0 [-14.7; 0.00] | 1.8 [7.5; 1.00] | -21.6 [-9.8; 0.50] |
| book | n/a (no signals by construction) | n/a (no signals by construction) | -38.0 [-28.8; 0.00] | n/a (no signals by construction) |
| book (native) | n/a (no signals by construction) | n/a (no signals by construction) | 13.2 [26.8; 1.00] | n/a (no signals by construction) |
| confluence | 9.0 [13.1; 1.00] | -14.7 [-16.1; 0.00] | 16.7 [20.4; 1.00] | -25.6 [-11.7; 0.50] |
| levels | 7.7 [15.7; 0.50] | -3.4 [11.8; 1.00] | 12.7 [26.7; 1.00] | -4.0 [13.3; 1.00] |
| levels (native) | 29.4 [75.4; 1.00] | 30.8 [62.3; 1.00] | -2.1 [-10.0; 0.50] | 11.0 [22.9; 1.00] |
| live | 17.0 [38.0; 1.00] | -4.1 [15.0; 1.00] | -4.6 [5.6; 0.50] | 11.7 [20.3; 1.00] |
| manual | 12.4 [8.8; 1.00] | 3.5 [7.8; 0.50] | 7.8 [25.6; 1.00] | -36.0 [-18.8; 0.50] |
| manual (native) | -2.3 [10.0; 1.00] | -24.2 [-13.7; 0.00] | 0.6 [4.4; 0.50] | 10.8 [20.5; 1.00] |
| momentum | 12.3 [12.2; 1.00] | 6.0 [-0.6; 0.50] | 9.4 [6.4; 0.50] | -3.1 [10.9; 1.00] |
| momentum (native) | -11.8 [-17.7; 0.00] | 17.8 [21.3; 1.00] | 24.8 [21.8; 1.00] | -1.5 [-24.1; 0.00] |
| pullback | 24.0 [32.5; 1.00] | 34.2 [44.6; 1.00] | -18.4 [3.4; 1.00] | -4.4 [-2.0; 0.50] |
| pullback (native) | 25.2 [39.8; 1.00] | -1.1 [9.3; 0.50] | 12.1 [28.0; 1.00] | -8.8 [15.7; 1.00] |
| structure | -1.2 [-13.0; 0.50] | 31.3 [29.8; 1.00] | 4.6 [10.9; 1.00] | 2.3 [12.3; 1.00] |
| structure (native) | -10.2 [-6.9; 0.00] | -4.8 [-17.0; 0.50] | 14.6 [20.0; 1.00] | -10.3 [-4.1; 0.50] |
| tape | -9.7 [-25.6; 0.00] | -3.1 [16.6; 0.50] | -31.7 [-13.2; 0.00] | 20.5 [30.3; 1.00] |
| tape (native) | -2.9 [4.1; 0.50] | -22.4 [-11.2; 0.00] | -2.6 [39.2; 1.00] | 0.4 [-8.6; 0.00] |
| trend | 0.3 [13.4; 1.00] | 4.4 [0.7; 0.50] | 0.6 [18.6; 0.50] | 6.9 [14.4; 1.00] |
| trend (native) | -6.8 [0.8; 0.50] | 6.6 [25.4; 1.00] | -20.7 [-11.4; 0.00] | -20.7 [-28.8; 0.00] |
| xmarket | -6.5 [0.5; 0.50] | -33.7 [-26.6; 0.00] | -20.6 [-28.4; 0.00] | 0.1 [-6.5; 0.50] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pullback|INFORMATION | 34.2 | 0.031 | 142.3 | 0.62 | 63.5 | 9.4 | {"2023": 37.4, "2024": 19.8, "2025": 36.0, "2026": 48.2} | -10.4 | 44.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 31.3 | 0.030 | 203.6 | 0.56 | 106.7 | 56.1 | {"2023": 34.0, "2024": 11.4, "2025": 17.9, "2026": 70.0} | 1.6 | 29.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION | 30.8 | 0.043 | 271.5 | 0.62 | 121.5 | 146.8 | {"2023": 36.1, "2024": 26.9, "2025": 5.2, "2026": 63.9} | -31.6 | 62.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 29.4 | 0.037 | 144.0 | 0.57 | 95.3 | 161.8 | {"2023": 18.2, "2024": 20.4, "2025": 10.8, "2026": 65.8} | -46.0 | 75.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 26.9 | 0.037 | 230.9 | 0.58 | 29.0 | -53.9 | {"2023": 16.8, "2024": 15.0, "2025": 32.5, "2026": 37.5} | 17.3 | 9.6 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|ACTIVITY | 25.2 | 0.021 | 183.4 | 0.63 | -13.7 | -6.4 | {"2023": 38.4, "2024": 21.0, "2025": 33.9, "2026": 15.6} | -14.6 | 39.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 24.8 | 0.026 | 374.1 | 0.53 | 9.1 | -128.0 | {"2023": -15.0, "2024": -7.7, "2025": 61.3, "2026": 32.7} | 3.0 | 21.8 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| pullback|ACTIVITY | 24.0 | 0.019 | 345.8 | 0.59 | 62.2 | -53.7 | {"2023": 3.2, "2024": 32.4, "2025": 17.3, "2026": 28.5} | -8.5 | 32.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 23.2 | 0.025 | 201.4 | 0.56 | -43.1 | -45.2 | {"2023": 0.0, "2024": 15.6, "2025": 57.7, "2026": -1.2} | -3.3 | 26.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|TIME | 20.5 | 0.014 | 391.8 | 0.51 | 49.3 | -7.6 | {"2023": -12.4, "2024": 14.6, "2025": 38.4, "2026": 16.9} | -9.8 | 30.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 1.8%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.2%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 9.6%); P7 tm60 L6M 66.1 pts/wk, rank 98% (top 2.4%); H7 tm60 L6M 25.1 pts/wk, rank 85% (top 15.3%); A7 tm60 L6M 6.5 pts/wk, rank 65% (top 34.5%). Rank = share of ALL Asia cells with a lower trailing-26w result.

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
| 15 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym10u/20u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -114.0, "2024": -2478.0, "2025": 2600.0, "2026": 5184.0} |
| 16 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym20u/10u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -136.0, "2024": -2419.0, "2025": 3110.0, "2026": 5184.0} |
| 17 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 18 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym15u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -120.0, "2024": -2395.0, "2025": 2657.0, "2026": 5184.0} |
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
| Asia | K7 | tm120 | neighbour | 98.9 | 36.5 | 26.2 | 556.4 | 0.56 | 759 | 0.99 |  |
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
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.31 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.83 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.90 |  |
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.39 | WEAK |
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
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.18 | WEAK |
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
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.87 | WEAK |
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
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.22 |  |
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
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.25 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.25 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.49 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.27 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.60 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.16 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.14 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.10 |  |
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
| sd5 | break | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 17 | -252 | -206 | -351 | 1 | 34 |
| sd5 | break_native | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 52 | -252 | -206 | -351 | 1 | 34 |
| sdx15 | break | kagi_80 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 140 | 2579 | 645 | -535 | -454 | 2325 | 1 | 34 |
| sdx15 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 195 | 2214 | 105 | -102 | 862 | 1176 | 1 | 34 |
| sdx15 | lim_prox | kagi_112 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 156 | 1722 | -776 | 900 | -2080 | 1504 | 1 | 34 |
| sdx15 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 359 | 1336 | 713 | -70 | 1061 | 384 | 1 | 34 |
| sdx15 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / both | 174 | 950 | -225 | 789 | 232 | 1321 | 1 | 34 |
| sdx15 | rej_native | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 1444 | -1063 | -311 | 1126 | 240 | 1 | 34 |
| sdx15 | rej_zone | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 172 | 1391 | -373 | -860 | 1022 | 1632 | 1 | 34 |
| sdx15 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 73 | 1895 | -252 | -737 | -146 | 1593 | 1 | 34 |
| sdx3 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 3088 | -168 | 318 | -923 | 2963 | 1 | 34 |
| sdx3 | lim_mid | kagi_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 276 | 3690 | 400 | 1269 | -2651 | 4082 | 1 | 34 |
| sdx3 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 358 | 4320 | 49 | 1608 | -1461 | 3654 | 1 | 34 |
| sdx3 | rej | urenko_10 | {"d": "B", "F": 9, "tol": 0.5} | sym15u / both | 161 | 1505 | -172 | -1100 | -778 | 1381 | 1 | 34 |
| sdx3 | rej_flow | wrenko_20 | {"d": "B", "F": 9} | sym15u / both | 71 | 1238 | -32 | -410 | -333 | 1105 | 1 | 34 |
| sdx3 | rej_native | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 245 | 3620 | 859 | 1354 | 441 | 3653 | 1 | 34 |
| sdx3 | rej_zone | urenko_10 | {"d": "B", "F": 9, "tgt": "opp"} | sym15u / both | 151 | 2671 | -57 | -178 | -380 | 2466 | 1 | 34 |
| sdx3 | retest | mrenko_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 195 | 1881 | -279 | 106 | 782 | 2331 | 1 | 34 |
| sdx30 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 75 | 1445 | 411 | -743 | -552 | 1630 | 1 | 34 |
| sdx30 | lim_mid | kagi_56 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 112 | 1852 | -92 | 580 | -256 | 1934 | 1 | 34 |
| sdx30 | lim_prox | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 228 | 3089 | -6 | 17 | 1634 | 3464 | 1 | 34 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 82 | 661 | 617 | 642 | 504 | -21 | 1 | 34 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 31 | 633 | -473 | 306 | 239 | 176 | 1 | 34 |
| sdx30 | rej_native | kagi_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / long | 51 | 1413 | 260 | -189 | -77 | 1398 | 1 | 34 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 64 | 1016 | -341 | 208 | 498 | 718 | 1 | 34 |
| sdx30 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 30 | 570 | 110 | -6 | 144 | 250 | 1 | 34 |
| sdx5 | break | urenko_14 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 179 | 3068 | 197 | 1069 | 1759 | 2498 | 1 | 34 |
| sdx5 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 214 | 2364 | 118 | 1141 | -997 | 2486 | 1 | 34 |
| sdx5 | lim_prox | frenko_40 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 489 | 2470 | -182 | -1246 | 1005 | 3420 | 1 | 34 |
| sdx5 | rej | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 89 | 2268 | 121 | -280 | 338 | 1883 | 1 | 34 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 76 | 1086 | -347 | -317 | 939 | 771 | 1 | 34 |
| sdx5 | rej_native | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 155 | 2126 | -203 | -436 | 139 | 981 | 1 | 34 |
| sdx5 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 102 | 1959 | 163 | 674 | -953 | 2077 | 1 | 34 |
| sdx5 | retest | kagi_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 156 | 3004 | -581 | -1198 | -562 | 1728 | 1 | 34 |
| sdx60 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 31 | 1222 | -351 | -320 | 116 | 1749 | 1 | 34 |
| sdx60 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 162 | 2417 | -215 | 125 | -1666 | 2534 | 1 | 34 |
| sdx60 | lim_prox | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 3080 | 290 | 236 | -323 | 3089 | 1 | 34 |
| sdx60 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 64 | 538 | -208 | -141 | 111 | 796 | 1 | 34 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 57 | -103 | -459 | 284 | -944 | 100 | 1 | 34 |
| sdx60 | rej_native | pnf_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 34 |
| sdx60 | rej_zone | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 34 |
| sdx_renko28 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 144 | 2263 | -119 | -618 | -1891 | 1174 | 1 | 34 |
| sdx_renko28 | lim_mid | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 157 | 2991 | -88 | -812 | -829 | 2811 | 1 | 34 |
| sdx_renko28 | lim_prox | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 156 | 3623 | -359 | -657 | -693 | 3375 | 1 | 34 |
| sdx_renko28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 1095 | 778 | -472 | 371 | -403 | 1 | 34 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "B", "F": 0} | plain60/60 / both | 37 | 445 | -26 | -150 | 326 | -29 | 1 | 34 |
| sdx_renko28 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 34 |
| sdx_renko28 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 34 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 85 | 1772 | -155 | -1444 | -732 | 1006 | 1 | 34 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 34 |
| sdx_rng28 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 261 | 3467 | -998 | 2482 | -838 | 2583 | 1 | 34 |
| sdx_rng28 | lim_prox | wrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 281 | 2565 | -697 | 820 | 191 | 5046 | 1 | 34 |
| sdx_rng28 | rej | kagi_56 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 93 | 1361 | 603 | 353 | -205 | 971 | 1 | 34 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / both | 166 | 1446 | 811 | -32 | 1520 | 715 | 1 | 34 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 34 |
| sdx_rng28 | rej_zone | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 34 |
| sdx_rng28 | retest | pnf_7 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 235 | 2538 | 635 | -1058 | -796 | 2576 | 1 | 34 |
| sdx_vol1100 | break | mrenko_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 179 | 2316 | -308 | 241 | -398 | 3305 | 1 | 34 |
| sdx_vol1100 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 247 | 3366 | 163 | 465 | 1569 | 4370 | 1 | 34 |
| sdx_vol1100 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 244 | 3123 | 198 | -474 | 859 | 3530 | 1 | 34 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 285 | 1551 | -175 | 755 | -1556 | 357 | 1 | 34 |
| sdx_vol1100 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / short | 57 | 887 | -67 | -326 | 37 | 2097 | 1 | 34 |
| sdx_vol1100 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 34 |
| sdx_vol1100 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 34 |
| sdx_vol1100 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 112 | 1778 | -246 | -234 | -609 | 1473 | 1 | 34 |
| fib15 | break | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 249 | 3282 | -364 | -1291 | 590 | 4632 | 1 | 34 |
| fib15 | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 164 | 2716 | -400 | -119 | -1799 | 2918 | 1 | 34 |
| fib15 | false_break | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 243 | 4142 | 430 | 262 | -578 | 3255 | 1 | 34 |
| fib15 | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | sym15u / both | 243 | 3974 | 399 | 289 | -884 | 3402 | 1 | 34 |
| fib15 | pullback | wrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / long | 166 | 1233 | -351 | -828 | -503 | 891 | 1 | 34 |
| fib15 | pullback_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 199 | 2553 | -505 | -2114 | -1143 | 2766 | 1 | 34 |
| fib15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 525 | 3712 | -473 | -683 | 2041 | 4718 | 1 | 34 |
| fib15 | reject_native | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 249 | 2516 | -870 | 1390 | 290 | 3091 | 1 | 34 |
| fib15 | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 203 | 3012 | -328 | 676 | -1536 | 4669 | 1 | 34 |
| fib15 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 210 | 2792 | 329 | 815 | -1874 | 3907 | 1 | 34 |
| fib5 | break | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 209 | 2478 | 923 | 588 | -748 | 3301 | 1 | 34 |
| fib5 | break_native | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 2474 | 665 | -63 | 652 | 2753 | 1 | 34 |
| fib5 | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 215 | 3383 | 715 | 310 | -1361 | 3415 | 1 | 34 |
| fib5 | false_break_native | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 214 | 3196 | 963 | 251 | -520 | 2826 | 1 | 34 |
| fib5 | pullback | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 194 | 1590 | 1243 | 113 | 223 | 1728 | 1 | 34 |
| fib5 | pullback_native | lbrk_3_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 155 | 1164 | 677 | -276 | 1144 | 854 | 1 | 34 |
| fib5 | reject | urenko_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 243 | 2344 | 186 | -2299 | -368 | 3117 | 1 | 34 |
| fib5 | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 2128 | -618 | 172 | -2575 | 2937 | 1 | 34 |
| fib5 | retest | urenko_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 525 | 2243 | 323 | 944 | -1709 | 1936 | 1 | 34 |
| fib5 | retest_native | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 207 | 3002 | 919 | 626 | -2031 | 4002 | 1 | 34 |
| fib60 | break | lbrk_3_10 | {"n": 3, "k": 0.5} | plain60/60 / both | 430 | 2830 | 528 | -2082 | 186 | 1880 | 1 | 34 |
| fib60 | break_native | lbrk_3_10 | {"n": 3, "k": 0.5} | plain60/60 / both | 436 | 2648 | 1046 | -1546 | -110 | 1502 | 1 | 34 |
| fib60 | false_break | kagi_14 | {"M": 2, "k": 0.5} | sym15u / both | 210 | 2654 | 1181 | 1317 | -829 | 2273 | 1 | 34 |
| fib60 | false_break_native | kagi_14 | {"M": 2, "k": 0.5} | sym15u / both | 209 | 2749 | 1588 | 1316 | -68 | 2351 | 1 | 34 |
| fib60 | pullback | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 1205 | -627 | -79 | -654 | -548 | 1 | 34 |
| fib60 | pullback_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 102 | 1231 | -694 | 107 | -2246 | 1353 | 1 | 34 |
| fib60 | reject | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 107 | 2314 | -527 | -402 | -2571 | 2192 | 1 | 34 |
| fib60 | reject_native | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 178 | 2299 | -228 | -443 | -3051 | 2199 | 1 | 34 |
| fib60 | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 3143 | 228 | 413 | -1867 | 3391 | 1 | 34 |
| fib60 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 3612 | -726 | 592 | -710 | 4771 | 1 | 34 |
| fibr_dev | break | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 34 |
| fibr_dev | break_native | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 34 |
| fibr_dev | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 180 | 1774 | 127 | -330 | -1672 | 2055 | 1 | 34 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 640 | 2530 | -963 | -884 | -3116 | 2367 | 1 | 34 |
| fibr_dev | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 256 | 3197 | 564 | -144 | -10 | 1750 | 1 | 34 |
| fibr_dev | reject_native | pnf_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 1943 | 13 | 365 | -532 | 839 | 1 | 34 |
| fibr_dev | retest | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 622 | 2751 | 131 | -652 | -1202 | 838 | 1 | 34 |
| fibr_dev | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 212 | 2228 | -96 | -768 | -515 | 2316 | 1 | 34 |
| fibr_pd | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 211 | 2784 | 1325 | -554 | -802 | 3958 | 1 | 34 |
| fibr_pd | break_native | pnf_5 | {"n": 2, "k": 0.25} | sym15u / both | 207 | 3135 | 51 | 239 | -950 | 2891 | 1 | 34 |
| fibr_pd | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 176 | 1922 | -666 | -75 | -1 | 2455 | 1 | 34 |
| fibr_pd | false_break_native | pnf_28 | {"M": 3, "k": 0.5} | sym15u / both | 174 | 1857 | -580 | 114 | -478 | 2515 | 1 | 34 |
| fibr_pd | reject | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 203 | 2146 | 523 | -1414 | -889 | 2858 | 1 | 34 |
| fibr_pd | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 237 | 3803 | 503 | 321 | -2364 | 2894 | 1 | 34 |
| fibr_pd | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 155 | 2461 | 865 | 467 | -2371 | 816 | 1 | 34 |
| fibr_pd | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 202 | 2979 | -199 | -788 | -742 | 2241 | 1 | 34 |
| piv_cama | break | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -355 | -657 | -3166 | 2471 | 1 | 34 |
| piv_cama | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -439 | -657 | -3166 | 2471 | 1 | 34 |
| piv_cama | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -589 | -486 | -3125 | 2453 | 1 | 34 |
| piv_cama | false_break_native | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -536 | -486 | -3125 | 2453 | 1 | 34 |
| piv_cama | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 1882 | -418 | 222 | -1471 | 1356 | 1 | 34 |
| piv_cama | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 500 | 2839 | -84 | -1811 | 959 | 3224 | 1 | 34 |
| piv_cama | retest | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 34 |
| piv_cama | retest_native | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 34 |
| piv_floor | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 34 |
| piv_floor | break_native | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 34 |
| piv_floor | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 34 |
| piv_floor | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 34 |
| piv_floor | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / long | 48 | 1156 | 133 | 855 | 1142 | 2067 | 1 | 34 |
| piv_floor | reject_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 183 | 2290 | 720 | 70 | -1278 | 2948 | 1 | 34 |
| piv_floor | retest | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 34 |
| piv_floor | retest_native | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 34 |
| piv_wf | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 199 | 2656 | -333 | -1729 | -430 | 1511 | 1 | 34 |
| piv_wf | break_native | urenko_40 | {"n": 3, "k": 0.5} | sym15u / both | 202 | 2880 | -608 | -890 | -364 | 3606 | 1 | 34 |
| piv_wf | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 199 | 2887 | -211 | -1555 | -414 | 1976 | 1 | 34 |
| piv_wf | false_break_native | kagi_80 | {"M": 1, "k": 0.0} | sym15u / both | 199 | 2636 | -144 | -1563 | -448 | 1481 | 1 | 34 |
| piv_wf | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 147 | 1472 | 651 | 362 | -430 | 1487 | 1 | 34 |
| piv_wf | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 230 | 3435 | -674 | 1015 | -1014 | 4860 | 1 | 34 |
| piv_wf | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 174 | 2164 | -5 | -1635 | -1545 | 1610 | 1 | 34 |
| piv_wf | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3307 | -134 | -1185 | -1620 | 3176 | 1 | 34 |
| swcluster | break | kagi_56 | {"n": 2, "k": 0.25} | sym15u / both | 50 | 1670 | -518 | -793 | -14 | 465 | 1 | 34 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1656 | -586 | -594 | -193 | 450 | 1 | 34 |
| swcluster | false_break | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 74 | 1459 | -140 | -948 | 37 | 490 | 1 | 34 |
| swcluster | false_break_native | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 68 | 1438 | -192 | -927 | 429 | 1017 | 1 | 34 |
| swcluster | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | -808 | 524 | -708 | 198 | 1 | 34 |
| swcluster | reject_native | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 53 | 1389 | 5 | -698 | -300 | 1666 | 1 | 34 |
| swcluster | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 72 | 1227 | -296 | 686 | 80 | 817 | 1 | 34 |
| swcluster | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | plain60/60 / both | 117 | 1228 | 47 | -874 | -370 | 1269 | 1 | 34 |
| swsr15 | break | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 229 | 2294 | 97 | -2202 | -2829 | 4155 | 1 | 34 |
| swsr15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 247 | 2675 | -145 | -1131 | -495 | 2962 | 1 | 34 |
| swsr15 | false_break | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 170 | 1830 | -590 | -550 | -3102 | 2238 | 1 | 34 |
| swsr15 | false_break_native | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 92 | 1864 | -177 | 269 | -551 | 3234 | 1 | 34 |
| swsr15 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 480 | 2378 | -1258 | -508 | 212 | 1830 | 1 | 34 |
| swsr15 | reject_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 234 | 2619 | -292 | -295 | -2422 | 1243 | 1 | 34 |
| swsr15 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3116 | -742 | -538 | 263 | 2136 | 1 | 34 |
| swsr15 | retest_native | pnf_28 | {"M": 6, "tol": 0.5} | sym15u / both | 188 | 2587 | -36 | 852 | 31 | 1170 | 1 | 34 |
| swsr5 | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 1969 | -49 | 176 | -191 | 2616 | 1 | 34 |
| swsr5 | break_native | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 2084 | -669 | -1018 | 182 | 1811 | 1 | 34 |
| swsr5 | false_break | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 171 | 2538 | 48 | 76 | -1945 | 2966 | 1 | 34 |
| swsr5 | false_break_native | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 168 | 2788 | 236 | -264 | -2437 | 2402 | 1 | 34 |
| swsr5 | reject | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 143 | 1638 | -293 | -1179 | -1318 | 1907 | 1 | 34 |
| swsr5 | reject_native | kagi_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 236 | 3237 | 265 | 1368 | 654 | 2042 | 1 | 34 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | plain60/60 / both | 529 | 2659 | -716 | -995 | -709 | 3038 | 1 | 34 |
| swsr5 | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 268 | 2360 | 398 | -1263 | -1865 | 3266 | 1 | 34 |
| swsr60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 173 | 2714 | -1019 | -989 | 1889 | 3578 | 1 | 34 |
| swsr60 | break_native | kagi_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 287 | 2084 | -313 | -2637 | -700 | 2284 | 1 | 34 |
| swsr60 | false_break | pnf_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 182 | 1557 | -946 | -1881 | -885 | 915 | 1 | 34 |
| swsr60 | false_break_native | frenko_40 | {"M": 2, "k": 0.5} | sym15u / both | 169 | 1673 | 1094 | -445 | -324 | 3542 | 1 | 34 |
| swsr60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 171 | 2075 | -1036 | -2049 | -1412 | 1142 | 1 | 34 |
| swsr60 | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 193 | 2648 | -423 | -1524 | 1834 | 2876 | 1 | 34 |
| swsr60 | retest | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 151 | 1599 | -190 | -251 | 910 | 2102 | 1 | 34 |
| swsr60 | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 166 | 2367 | -533 | -15 | -85 | 3016 | 1 | 34 |
| stack | break | kagi_20 | {"k": 3, "cw": 1.0} | sym15u / both | 148 | 3437 | 176 | 1393 | -17 | 1971 | 1 | 204 |
| stack | break_native | swing_atr_0.9 | {"k": 2, "cw": 0.5} | sym15u / both | 161 | 2660 | 316 | -1526 | -153 | 2343 | 1 | 204 |
| stack | reject | vsess_120 | {"k": 2, "cw": 0.5} | sym8u / both | 94 | 2473 | 270 | -72 | -962 | 2621 | 2 | 204 |
| stack | reject_native | pnf_14 | {"k": 2, "cw": 0.5} | sym15u / both | 194 | 3864 | -615 | -258 | -63 | 4021 | 1 | 204 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 202 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 202 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 202 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 202 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 202 |
| book_walls | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 55 | 1152 | 209 | -451 | 107 | 688 | 1 | 202 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 202 |
| book_walls | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym15u / both | 31 | 948 | -230 | -711 | 334 | 598 | 1 | 202 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 197 | 2357 | -978 | -1528 | -3048 | 1807 | 2 | 204 |
| book_walls_loose | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 2309 | -1415 | 296 | -1880 | 2748 | 2 | 204 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 204 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 204 |
| book_walls_loose | reject | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 170 | 3163 | -1118 | 31 | -1206 | 3714 | 1 | 204 |
| book_walls_loose | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 208 | 3375 | -1082 | -93 | -1302 | 3631 | 1 | 204 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3516 | 15 | -764 | -863 | 4040 | 1 | 204 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1 | 204 |
| channel | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 253 | 3125 | -354 | -1559 | 474 | 4044 | 1 | 34 |
| channel | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 173 | 2782 | -78 | -142 | -1977 | 2827 | 1 | 34 |
| channel | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 172 | 2909 | -148 | -291 | -2237 | 2992 | 1 | 34 |
| channel | false_break_native | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3344 | 373 | 1739 | 1102 | 4639 | 1 | 34 |
| channel | reject | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 118 | 2681 | 332 | 48 | -1806 | 2627 | 1 | 34 |
| channel | reject_native | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3978 | -529 | -363 | -2591 | 3263 | 1 | 34 |
| channel | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 34 |
| channel | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 34 |
| fvg15 | break | kagi_80 | {"n": 3, "k": 0.5} | sym15u / both | 83 | 1769 | -239 | 176 | 876 | 1390 | 1 | 34 |
| fvg15 | break_native | wrenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2142 | 699 | 1173 | -2521 | 1701 | 1 | 34 |
| fvg15 | false_break | pnf_10 | {"M": 3, "k": 0.5} | plain60/60 / short | 131 | 1273 | 165 | -386 | -465 | 1786 | 1 | 34 |
| fvg15 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | plain60/60 / short | 130 | 1094 | 257 | -577 | -633 | 1723 | 1 | 34 |
| fvg15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 3384 | -99 | 1317 | -307 | 4690 | 1 | 34 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 167 | 4419 | -178 | 432 | 336 | 5177 | 1 | 34 |
| fvg15 | retest | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 1682 | -181 | -793 | -565 | 1944 | 1 | 34 |
| fvg15 | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 162 | 2753 | 583 | -533 | -855 | 2947 | 1 | 34 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 34 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 34 |
| fvg5 | false_break | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 34 |
| fvg5 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 34 |
| fvg5 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 239 | 2756 | 214 | -1882 | -387 | 2095 | 1 | 34 |
| fvg5 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 242 | 2182 | 193 | -1316 | -820 | 1313 | 1 | 34 |
| fvg5 | retest | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 172 | 2473 | -230 | -1137 | -66 | 1925 | 1 | 34 |
| fvg5 | retest_native | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 189 | 3090 | -276 | -1553 | 384 | 2624 | 1 | 34 |
| gaps | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 93 | 2458 | 515 | -722 | -3227 | 1532 | 1 | 205 |
| gaps | break_native | pnf_7 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2868 | -251 | -161 | -3421 | 2136 | 1 | 205 |
| gaps | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 1779 | 18 | -19 | 344 | 2112 | 1 | 205 |
| gaps | false_break_native | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 99 | 1843 | -87 | 76 | 307 | 2380 | 1 | 205 |
| gaps | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 191 | 2035 | -730 | -1775 | 708 | 1690 | 1 | 205 |
| gaps | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 147 | 2332 | -600 | 3 | -1106 | 2770 | 1 | 205 |
| gaps | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1584 | -348 | -820 | -994 | 1765 | 1 | 205 |
| gaps | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 100 | 2963 | -29 | 441 | -1448 | 3370 | 1 | 205 |
| mmove | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 210 | 2588 | -853 | -45 | -2503 | 1001 | 1 | 34 |
| mmove | break_native | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 202 | 2486 | -450 | 418 | -1675 | 1326 | 1 | 34 |
| mmove | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2557 | -462 | -577 | -579 | 2977 | 1 | 34 |
| mmove | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 225 | 2897 | -838 | -578 | -949 | 3394 | 1 | 34 |
| mmove | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 430 | 2106 | 652 | 71 | 184 | 2834 | 1 | 34 |
| mmove | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 214 | 3153 | -70 | 1060 | -1089 | 3669 | 1 | 34 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 34 |
| mmove | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 34 |
| ob15 | break | wrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 81 | 1091 | 244 | -107 | 133 | 1385 | 1 | 34 |
| ob15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 75 | 1244 | 663 | -890 | -72 | 1890 | 1 | 34 |
| ob15 | false_break | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 90 | 748 | -455 | -628 | 338 | 1292 | 1 | 34 |
| ob15 | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 90 | 748 | -455 | -628 | 338 | 1292 | 1 | 34 |
| ob15 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 1376 | 323 | -1331 | 1080 | 1930 | 1 | 34 |
| ob15 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 71 | 1184 | 775 | -274 | 61 | 2027 | 1 | 34 |
| ob15 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1142 | 267 | -325 | 553 | 1702 | 1 | 34 |
| ob15 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 87 | 1197 | 155 | -638 | 61 | 1172 | 1 | 34 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 34 |
| ob5 | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 34 |
| ob5 | false_break | pnf_5 | {"M": 3, "k": 0.5} | plain60/60 / both | 200 | 1963 | -56 | 924 | 346 | 1463 | 1 | 34 |
| ob5 | false_break_native | kagi_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 204 | 2094 | 10 | 566 | -25 | 1605 | 1 | 34 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 129 | 1424 | 71 | -876 | -916 | 1490 | 1 | 34 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 | 1981 | -488 | -1059 | -729 | 757 | 1 | 34 |
| ob5 | retest | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 97 | 2215 | -850 | -680 | 932 | 2095 | 1 | 34 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 111 | 2232 | -468 | -959 | 1160 | 2143 | 1 | 34 |
| opens | break | renko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 3946 | 43 | 1332 | 422 | 3112 | 2 | 205 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 205 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 205 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 205 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 205 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 205 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 205 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 205 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1 | 205 |
| prior_day | break_native | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 103 | 2083 | 433 | -525 | -990 | 3127 | 1 | 205 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 2376 | 649 | -33 | -1668 | 3829 | 1 | 205 |
| prior_day | false_break_native | swing_atr_0.1 | {"M": 3, "k": 0.5} | sym15u / both | 126 | 2405 | 621 | -246 | -702 | 3078 | 1 | 205 |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 105 | 1827 | -426 | -804 | -662 | 720 | 1 | 205 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 205 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 1 | 205 |
| prior_day | retest_native | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 191 | 2712 | -110 | -383 | 424 | 2187 | 1 | 205 |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 162 | 2957 | -620 | 59 | -1689 | 2002 | 1 | 204 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 204 |
| profile_nodes | false_break | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 2292 | -55 | -984 | -1066 | 1894 | 1 | 204 |
| profile_nodes | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 208 | 2676 | -200 | -70 | 183 | 1964 | 2 | 204 |
| profile_nodes | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 152 | 2817 | -450 | -1140 | -2494 | 1640 | 1 | 204 |
| profile_nodes | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | sym15u / both | 204 | 2821 | -98 | -360 | 235 | 2346 | 2 | 204 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 204 |
| profile_nodes | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 204 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 1 | 205 |
| profile_va | break_native | renko_28 | {"n": 1, "k": 0.5} | sym8u / both | 143 | 2591 | -66 | -1416 | -848 | 2717 | 2 | 205 |
| profile_va | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 120 | 2493 | -419 | -437 | -1179 | 2786 | 1 | 205 |
| profile_va | false_break_native | tm30 | {"M": 2, "k": 0.5} | sym15u / both | 162 | 2584 | 299 | -691 | -241 | 3689 | 1 | 205 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 205 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 205 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym15u / both | 133 | 3198 | 93 | -1886 | -354 | 2602 | 1 | 205 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 205 |
| round | break | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 205 |
| round | break_native | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 205 |
| round | false_break | pasl_10 | {"M": 3, "k": 0.5} | plain60/60 / both | 717 | 3076 | -134 | 387 | -1885 | 3447 | 1 | 205 |
| round | false_break_native | dchg_112 | {"M": 2, "k": 0.5} | sym15u / both | 166 | 3286 | 139 | -661 | -1168 | 2614 | 1 | 205 |
| round | reject | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 405 | 3731 | -1516 | 737 | 448 | 5872 | 1 | 205 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 205 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 205 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 205 |
| session_hl | break | pasl_56 | {"n": 1, "k": 0.0} | sym15u / both | 139 | 1771 | -1102 | -336 | -292 | 2220 | 1 | 201 |
| session_hl | break_native | pasl_20 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2654 | -107 | 389 | -378 | 3494 | 1 | 201 |
| session_hl | false_break | renko_14 | {"M": 2, "k": 0.5} | asym20u/10u / both | 130 | 1640 | -516 | 85 | -1030 | 1483 | 2 | 201 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 201 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 201 |
| session_hl | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 1805 | -162 | -987 | -1228 | -754 | 1 | 201 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 201 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 1 | 201 |
| trendline | break | mrenko_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 490 | 2957 | -338 | -167 | -927 | 697 | 1 | 34 |
| trendline | break_native | mrenko_14 | {"n": 2, "k": 0.25} | sym15u / both | 234 | 3004 | 8 | 371 | -320 | 5564 | 1 | 34 |
| trendline | false_break | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / both | 540 | 1894 | 260 | -1042 | -2133 | -658 | 1 | 34 |
| trendline | false_break_native | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / long | 281 | 1886 | 383 | -246 | -48 | 1129 | 1 | 34 |
| trendline | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 34 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 34 |
| trendline | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 225 | 2709 | 329 | -350 | 447 | 2557 | 1 | 34 |
| trendline | retest_native | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 220 | 3008 | -48 | -1940 | 1275 | 1937 | 1 | 34 |
| uw_dp | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 205 |
| uw_dp | break_native | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 205 |
| uw_dp | false_break | dchg_40 | {"M": 2, "k": 0.5} | sym15u / both | 109 | 2734 | 0 | 0 | 530 | 3624 | 1 | 205 |
| uw_dp | false_break_native | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 205 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 112 | 1964 | 0 | 0 | 365 | 1874 | 1 | 205 |
| uw_dp | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 122 | 2086 | 0 | 0 | -468 | 1673 | 1 | 205 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 205 |
| uw_dp | retest_native | dchg_40 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2424 | 0 | 0 | 561 | 1869 | 1 | 205 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1 | 204 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 204 |
| uw_ndx | false_break | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 204 |
| uw_ndx | false_break_native | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 204 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 204 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 204 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 204 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 204 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 204 |
| uw_qqq | break_native | renko_20 | {"n": 2, "k": 0.0} | sym8u / both | 145 | 2846 | 0 | 48 | 263 | 2703 | 2 | 204 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 204 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 204 |
| uw_qqq | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 116 | 2612 | 0 | 241 | -787 | -337 | 1 | 204 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 204 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 204 |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1 | 204 |
| vwap | break | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 5484 | 276 | -1123 | -2301 | 6752 | 2 | 204 |
| vwap | break_native | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 227 | 5738 | 534 | -1080 | -3184 | 7299 | 2 | 204 |
| vwap | false_break | dchg_56 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2837 | 298 | -962 | 1185 | 2960 | 1 | 204 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 204 |
| vwap | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 248 | 4751 | -37 | -1718 | 768 | 7179 | 2 | 204 |
| vwap | reject_native | cdr_100 | {"tol": 0.5, "conf": "body"} | sym8u / both | 233 | 5846 | 667 | 1147 | -135 | 5737 | 2 | 204 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 204 |
| vwap | retest_native | cdr_100 | {"M": 10, "tol": 0.5} | sym8u / both | 218 | 4634 | 959 | 362 | -947 | 5800 | 2 | 204 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 203 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 203 |
| vwap_bands | false_break | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 724 | 2432 | 689 | -2155 | 618 | 2198 | 1 | 203 |
| vwap_bands | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 724 | 2432 | 689 | -2155 | 618 | 2198 | 1 | 203 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 203 |
| vwap_bands | reject_native | dib_1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 280 | 3027 | 61 | -795 | 419 | 5272 | 1 | 203 |
| vwap_bands | retest | drb_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 684 | 3403 | 537 | -777 | -29 | 2793 | 1 | 203 |
| vwap_bands | retest_native | vsess_30 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 3675 | 581 | -1198 | -2832 | 5778 | 1 | 203 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 1 | 205 |
| week_month | break_native | swing_atr_0.25 | {"n": 2, "k": 0.25} | sym15u / both | 43 | 1508 | -111 | -183 | -1226 | 1563 | 1 | 205 |
| week_month | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 205 |
| week_month | false_break_native | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 205 |
| week_month | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 38 | 1618 | 133 | -162 | -2232 | 2609 | 1 | 205 |
| week_month | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 32 | 1579 | -70 | -765 | -196 | 1671 | 1 | 205 |
| week_month | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 33 | 1229 | 124 | -30 | -141 | 1120 | 1 | 205 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 1 | 205 |
| zones | break | vol_4000 | {"n": 1, "k": 0.5} | sym8u / both | 113 | 2090 | 229 | 143 | 393 | 2008 | 2 | 204 |
| zones | break_native | renko_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 195 | 2650 | -114 | -424 | -736 | 2949 | 2 | 204 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 204 |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 112 | 1825 | -112 | -996 | 314 | 2093 | 2 | 204 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 204 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 204 |
| zones | retest | tib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 128 | 2375 | -1292 | 285 | 258 | 2085 | 1 | 204 |
| zones | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 102 | 2223 | -765 | 332 | -877 | 1559 | 1 | 204 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | wrenko_10 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -218 | -115 | 358 | -542 | -84 | 1 | 34 |
| sd5 | break_native | wrenko_10 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -218 | -115 | 358 | -542 | -84 | 1 | 34 |
| sd5 | retest | kagi_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 31 | -237 | -183 | 312 | -408 | -277 | 1 | 34 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 1 | 34 |
| sdx15 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 171 | 2399 | -85 | 715 | 2594 | 3384 | 1 | 34 |
| sdx15 | lim_mid | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 333 | 2976 | -2286 | -2403 | -427 | 2983 | 1 | 34 |
| sdx15 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 373 | 3815 | 30 | -593 | -1777 | 5127 | 1 | 34 |
| sdx15 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 68 | 2107 | -1412 | -869 | 341 | 1563 | 1 | 34 |
| sdx15 | rej_flow | wrenko_10 | {"d": "A", "F": 0} | sym15u / both | 58 | 1194 | -483 | 1191 | -1486 | 1139 | 1 | 34 |
| sdx15 | rej_native | kagi_56 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 2039 | -160 | -2368 | -1749 | 2557 | 1 | 34 |
| sdx15 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 386 | 1956 | -1553 | -1374 | -943 | 1143 | 1 | 34 |
| sdx15 | retest | kagi_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 87 | 1671 | 1303 | -626 | 3804 | 2010 | 1 | 34 |
| sdx3 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 350 | 3483 | 1458 | 3578 | 5139 | 4750 | 1 | 34 |
| sdx3 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 182 | 3365 | 26 | 2134 | 1935 | 3244 | 1 | 34 |
| sdx3 | lim_prox | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 224 | 3509 | 1324 | 128 | -1502 | 4960 | 1 | 34 |
| sdx3 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 475 | 3002 | -2715 | -1978 | -5508 | 1958 | 1 | 34 |
| sdx3 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / long | 156 | 3037 | 6 | 1057 | -3441 | 2950 | 1 | 34 |
| sdx3 | rej_native | mrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 34 |
| sdx3 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 34 |
| sdx3 | retest | kagi_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 245 | 2392 | 2042 | 2685 | 4969 | 3185 | 1 | 34 |
| sdx30 | break | pnf_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 79 | 1933 | -372 | 1333 | 866 | 1755 | 1 | 34 |
| sdx30 | lim_mid | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 52 | 1565 | 12 | -897 | 111 | 634 | 1 | 34 |
| sdx30 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 142 | 2308 | -245 | -373 | 1505 | 5248 | 1 | 34 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 73 | 1261 | -467 | -838 | -1738 | 1427 | 1 | 34 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 34 | 1001 | 73 | -979 | -1302 | 1556 | 1 | 34 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 34 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 34 |
| sdx30 | retest | pnf_28 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 35 | 976 | -101 | -1016 | 521 | 952 | 1 | 34 |
| sdx5 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 128 | 2348 | 760 | 872 | 1375 | 1924 | 1 | 34 |
| sdx5 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 4263 | -912 | -271 | 1146 | 4807 | 1 | 34 |
| sdx5 | lim_prox | urenko_80 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 214 | 4370 | 1480 | 714 | 2473 | 2468 | 1 | 34 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 216 | 2627 | -830 | 131 | -3477 | 4401 | 1 | 34 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / both | 319 | 735 | -722 | 565 | 43 | 2367 | 1 | 34 |
| sdx5 | rej_native | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 34 |
| sdx5 | rej_zone | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 34 |
| sdx5 | retest | pnf_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 114 | 2164 | 463 | 1190 | 1731 | 2812 | 1 | 34 |
| sdx60 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 52 | 1464 | 466 | 334 | 762 | 926 | 1 | 34 |
| sdx60 | lim_mid | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 413 | 1413 | -1233 | -23 | -2684 | 345 | 1 | 34 |
| sdx60 | lim_prox | urenko_80 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 209 | 1005 | 76 | 77 | -422 | 1306 | 1 | 34 |
| sdx60 | rej | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 124 | 2540 | -595 | -1785 | -237 | 2453 | 1 | 34 |
| sdx60 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | plain60/60 / both | 32 | 589 | -294 | -644 | -547 | 980 | 1 | 34 |
| sdx60 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 34 |
| sdx60 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 34 |
| sdx_renko28 | break | pnf_56 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 158 | 2617 | -1111 | 1032 | 1543 | 2235 | 1 | 34 |
| sdx_renko28 | lim_mid | kagi_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 475 | 4203 | 121 | -178 | 3832 | 2308 | 1 | 34 |
| sdx_renko28 | lim_prox | pnf_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 188 | 4526 | 216 | 1871 | -67 | 4152 | 1 | 34 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 417 | 2601 | -2519 | -2626 | -4344 | 2070 | 1 | 34 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 202 | 2765 | 740 | -3083 | 894 | 2859 | 1 | 34 |
| sdx_renko28 | rej_native | urenko_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 34 |
| sdx_renko28 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 34 |
| sdx_renko28 | retest | pnf_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 135 | 2994 | -717 | 618 | 233 | 2746 | 1 | 34 |
| sdx_rng28 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 487 | 4615 | 1288 | 2874 | 6639 | 8079 | 1 | 34 |
| sdx_rng28 | lim_mid | kagi_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 502 | 4204 | -595 | -701 | -2 | 1835 | 1 | 34 |
| sdx_rng28 | lim_prox | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 493 | 5342 | 520 | 1267 | -40 | 7530 | 1 | 34 |
| sdx_rng28 | rej | mrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 504 | 2856 | -984 | -1842 | -5463 | 2791 | 1 | 34 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / long | 172 | 2052 | 2014 | -466 | -281 | 3800 | 1 | 34 |
| sdx_rng28 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 431 | 3332 | 1328 | -4047 | 1358 | 3443 | 1 | 34 |
| sdx_rng28 | rej_zone | frenko_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4594 | 559 | -3692 | -3237 | 3340 | 1 | 34 |
| sdx_rng28 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 449 | 3491 | -1168 | 3003 | 5388 | 3398 | 1 | 34 |
| sdx_vol1100 | break | lbrk_3_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 599 | 2954 | -817 | 879 | 1581 | 2600 | 1 | 34 |
| sdx_vol1100 | lim_mid | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1444 | 5146 | -307 | -267 | -7260 | 5686 | 1 | 34 |
| sdx_vol1100 | lim_prox | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1412 | 4616 | 1989 | -3 | -5487 | 5378 | 1 | 34 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 429 | 5058 | -1453 | -1789 | -1589 | 7224 | 1 | 34 |
| sdx_vol1100 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / long | 161 | 1923 | -695 | -1236 | -1274 | 1821 | 1 | 34 |
| sdx_vol1100 | rej_native | kagi_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 477 | 3771 | -172 | -664 | -3831 | 5515 | 1 | 34 |
| sdx_vol1100 | rej_zone | kagi_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 477 | 3771 | -172 | -664 | -3831 | 5515 | 1 | 34 |
| sdx_vol1100 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 398 | 4494 | -381 | -1960 | 2674 | 5777 | 1 | 34 |
| fib15 | break | kagi_20 | {"n": 1, "k": 0.0} | sym15u / both | 346 | 3524 | 552 | 2335 | 3568 | 2093 | 1 | 34 |
| fib15 | break_native | kagi_56 | {"n": 2, "k": 0.25} | sym15u / both | 311 | 3762 | 75 | -500 | 6087 | 5412 | 1 | 34 |
| fib15 | false_break | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 356 | 3289 | -131 | 2456 | 3878 | 2191 | 1 | 34 |
| fib15 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 985 | 3291 | 444 | 1910 | -2104 | 2878 | 1 | 34 |
| fib15 | pullback | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / long | 116 | 2115 | 1754 | 472 | -1463 | 3636 | 1 | 34 |
| fib15 | pullback_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / long | 106 | 2608 | 1196 | 45 | -914 | 4367 | 1 | 34 |
| fib15 | reject | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 294 | 2531 | 868 | -585 | 3010 | 3488 | 1 | 34 |
| fib15 | reject_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 4502 | 87 | 1288 | 1778 | 4269 | 1 | 34 |
| fib15 | retest | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 328 | 4147 | -1385 | 2285 | 2790 | 3457 | 1 | 34 |
| fib15 | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 342 | 3490 | -840 | 1601 | -161 | 3295 | 1 | 34 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 392 | 4876 | -635 | -1541 | 2534 | 5721 | 1 | 34 |
| fib5 | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 187 | 3101 | 1263 | -128 | 1540 | 1917 | 1 | 34 |
| fib5 | false_break | kagi_20 | {"M": 3, "k": 0.5} | sym15u / both | 403 | 4940 | 944 | 1313 | 3307 | 5844 | 1 | 34 |
| fib5 | false_break_native | wrenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 394 | 5399 | 68 | -2894 | 1385 | 3042 | 1 | 34 |
| fib5 | pullback | lbrk_3_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 254 | 2243 | -33 | -959 | -883 | 2909 | 1 | 34 |
| fib5 | pullback_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 2320 | 692 | 1177 | -653 | 2698 | 1 | 34 |
| fib5 | reject | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 34 | 1877 | -184 | 434 | -161 | 2037 | 1 | 34 |
| fib5 | reject_native | pnf_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 284 | 2753 | -140 | 262 | 1608 | 2820 | 1 | 34 |
| fib5 | retest | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 375 | 4340 | 561 | -571 | 2129 | 2299 | 1 | 34 |
| fib5 | retest_native | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 392 | 4261 | 1104 | -1881 | 3422 | 2396 | 1 | 34 |
| fib60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 302 | 3565 | 654 | 1558 | -1114 | 4562 | 1 | 34 |
| fib60 | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 296 | 3466 | 16 | 15 | 1046 | 4959 | 1 | 34 |
| fib60 | false_break | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 301 | 3933 | 1570 | 2104 | 2305 | 4830 | 1 | 34 |
| fib60 | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 304 | 4321 | 2499 | 3022 | 1035 | 4383 | 1 | 34 |
| fib60 | pullback | lbrk_3_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 111 | 1315 | -353 | 2477 | 284 | 602 | 1 | 34 |
| fib60 | pullback_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 144 | 1953 | 409 | 2239 | 1366 | 1976 | 1 | 34 |
| fib60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 297 | 3853 | 197 | -2307 | -1069 | 5413 | 1 | 34 |
| fib60 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 309 | 3595 | -544 | -1575 | -629 | 3065 | 1 | 34 |
| fib60 | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 283 | 4034 | 1024 | 761 | 814 | 3982 | 1 | 34 |
| fib60 | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 350 | 3645 | -129 | 298 | 273 | 3427 | 1 | 34 |
| fibr_dev | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 34 |
| fibr_dev | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 34 |
| fibr_dev | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 460 | 3921 | 2689 | 822 | 2042 | 4742 | 1 | 34 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 452 | 4732 | 2585 | -852 | 3835 | 5674 | 1 | 34 |
| fibr_dev | reject | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 3087 | 936 | 1508 | -135 | 2125 | 1 | 34 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 448 | 4974 | 1168 | 2667 | 817 | 4931 | 1 | 34 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 414 | 5720 | -316 | 1766 | 2350 | 3254 | 1 | 34 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 427 | 4867 | -1061 | -570 | 4293 | 5344 | 1 | 34 |
| fibr_ib | break | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 314 | 2586 | -59 | 1126 | 2764 | 2172 | 1 | 34 |
| fibr_ib | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 324 | 2561 | 214 | 1839 | 2319 | 1672 | 1 | 34 |
| fibr_ib | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 34 |
| fibr_ib | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 34 |
| fibr_ib | reject | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 710 | 3281 | -283 | -506 | 2843 | 3230 | 1 | 34 |
| fibr_ib | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 313 | 3225 | 598 | 890 | -471 | 3776 | 1 | 34 |
| fibr_ib | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 222 | 2506 | 180 | -429 | 3 | 1221 | 1 | 34 |
| fibr_ib | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 333 | 2991 | 863 | 1825 | 1106 | 3425 | 1 | 34 |
| fibr_on | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 390 | 3646 | 879 | 2200 | 7144 | 3961 | 1 | 34 |
| fibr_on | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 414 | 4795 | 1610 | 372 | 7170 | 7330 | 1 | 34 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 383 | 5252 | 1464 | 1013 | 2918 | 7973 | 1 | 34 |
| fibr_on | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 1 | 34 |
| fibr_on | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 376 | 2691 | 1164 | -1169 | 4230 | 2505 | 1 | 34 |
| fibr_on | reject_native | kagi_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 286 | 3620 | 579 | -1335 | -1835 | 3947 | 1 | 34 |
| fibr_on | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 2663 | -1647 | 883 | 1488 | 3069 | 1 | 34 |
| fibr_on | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 3227 | 1904 | -823 | -47 | 375 | 1 | 34 |
| fibr_or | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 34 |
| fibr_or | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 34 |
| fibr_or | false_break | urenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 349 | 3867 | 432 | 1403 | -216 | 2811 | 1 | 34 |
| fibr_or | false_break_native | kagi_14 | {"M": 1, "k": 0.0} | sym15u / both | 383 | 3852 | 98 | 1427 | 1769 | 3344 | 1 | 34 |
| fibr_or | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 374 | 3996 | -233 | 328 | 4247 | 4044 | 1 | 34 |
| fibr_or | reject_native | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 490 | 3288 | 56 | 1396 | 513 | -467 | 1 | 34 |
| fibr_or | retest | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 1 | 34 |
| fibr_or | retest_native | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 1 | 34 |
| fibr_pd | break | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 363 | 6035 | -981 | 1122 | 3395 | 6251 | 1 | 34 |
| fibr_pd | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 365 | 5426 | -679 | 158 | 2300 | 6842 | 1 | 34 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 1 | 34 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 1 | 34 |
| fibr_pd | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 34 |
| fibr_pd | reject_native | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 34 |
| fibr_pd | retest | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 34 |
| fibr_pd | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 34 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 357 | 5210 | 1949 | 420 | -2741 | 6204 | 1 | 34 |
| piv_cama | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 379 | 6524 | 489 | 1354 | 649 | 7212 | 1 | 34 |
| piv_cama | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 194 | 3092 | 319 | 526 | 2048 | 2764 | 1 | 34 |
| piv_cama | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 187 | 3276 | 454 | 729 | 1972 | 3605 | 1 | 34 |
| piv_cama | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 369 | 2583 | -1426 | 1370 | 3989 | 2748 | 1 | 34 |
| piv_cama | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 412 | 4654 | -2040 | -878 | -4527 | 4643 | 1 | 34 |
| piv_cama | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 34 |
| piv_cama | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 34 |
| piv_floor | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3553 | -161 | 488 | 2430 | 2793 | 1 | 34 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 1 | 34 |
| piv_floor | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 186 | 3796 | -476 | 286 | 3151 | 3316 | 1 | 34 |
| piv_floor | false_break_native | kagi_40 | {"M": 3, "k": 0.5} | sym15u / both | 377 | 4160 | 1164 | 1611 | 1824 | 5277 | 1 | 34 |
| piv_floor | reject | kagi_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 152 | 1062 | 595 | 2464 | 2078 | 277 | 1 | 34 |
| piv_floor | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 530 | 2407 | 1631 | 3763 | 519 | 1290 | 1 | 34 |
| piv_floor | retest | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 136 | 3307 | 1674 | 1218 | 2007 | 4474 | 1 | 34 |
| piv_floor | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 3913 | 1673 | 239 | 2389 | 4656 | 1 | 34 |
| piv_wf | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3685 | 42 | 27 | 876 | 2866 | 1 | 34 |
| piv_wf | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 394 | 3769 | -323 | 382 | 4352 | 7535 | 1 | 34 |
| piv_wf | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 3750 | 2632 | 2336 | 1588 | 3570 | 1 | 34 |
| piv_wf | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 373 | 3736 | 2381 | 2146 | 1178 | 2963 | 1 | 34 |
| piv_wf | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 306 | 2772 | -874 | -732 | 1160 | 5492 | 1 | 34 |
| piv_wf | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 404 | 2303 | -833 | 3724 | 3038 | 2931 | 1 | 34 |
| piv_wf | retest | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 361 | 4657 | 320 | 3797 | -729 | 5338 | 1 | 34 |
| piv_wf | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 323 | 4338 | 1465 | 1240 | 2816 | 3449 | 1 | 34 |
| swcluster | break | urenko_112 | {"n": 3, "k": 0.5} | sym15u / both | 54 | 1306 | 832 | -672 | 48 | 1510 | 1 | 34 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / long | 56 | 1203 | -745 | -84 | -805 | 1222 | 1 | 34 |
| swcluster | false_break | pnf_40 | {"M": 1, "k": 0.0} | sym15u / both | 93 | 1551 | -519 | -769 | 385 | 1862 | 1 | 34 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 1 | 34 |
| swcluster | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 78 | 994 | -808 | 727 | -1417 | 573 | 1 | 34 |
| swcluster | reject_native | kagi_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 115 | 1254 | -69 | -238 | 607 | 824 | 1 | 34 |
| swcluster | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 47 | 1317 | -512 | -727 | -288 | 1601 | 1 | 34 |
| swcluster | retest_native | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1293 | 791 | -1867 | 192 | 1950 | 1 | 34 |
| swsr15 | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 34 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 34 |
| swsr15 | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 372 | 3937 | 1163 | 182 | 1458 | 3348 | 1 | 34 |
| swsr15 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | sym15u / both | 361 | 4013 | -579 | -1717 | 3531 | 3475 | 1 | 34 |
| swsr15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 328 | 3874 | -2044 | -176 | -1129 | 4458 | 1 | 34 |
| swsr15 | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 354 | 3290 | -1693 | 687 | -2566 | 6013 | 1 | 34 |
| swsr15 | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 290 | 5015 | -392 | -944 | 1428 | 4099 | 1 | 34 |
| swsr15 | retest_native | urenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 333 | 4907 | 1503 | -111 | 2647 | 3519 | 1 | 34 |
| swsr5 | break | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 435 | 5683 | 1075 | -778 | -1404 | 4628 | 1 | 34 |
| swsr5 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 435 | 5683 | 1075 | -778 | -1404 | 4628 | 1 | 34 |
| swsr5 | false_break | kagi_28 | {"M": 1, "k": 0.0} | sym15u / both | 444 | 5625 | 880 | -288 | -1389 | 4925 | 1 | 34 |
| swsr5 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | sym15u / both | 432 | 8188 | 1948 | -2061 | 866 | 8579 | 1 | 34 |
| swsr5 | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 407 | 3165 | -776 | 1166 | 1559 | 3156 | 1 | 34 |
| swsr5 | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 452 | 4120 | -609 | 1554 | 3190 | 5222 | 1 | 34 |
| swsr5 | retest | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 665 | 2200 | 3212 | 5780 | 1 | 34 |
| swsr5 | retest_native | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 691 | 2200 | 3212 | 5780 | 1 | 34 |
| swsr60 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3965 | 36 | 158 | -2380 | 1344 | 1 | 34 |
| swsr60 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 254 | 4303 | 338 | -270 | -2273 | 3058 | 1 | 34 |
| swsr60 | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 290 | 2588 | 1112 | -417 | 1728 | 2743 | 1 | 34 |
| swsr60 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 286 | 2726 | 385 | -291 | 3026 | 3397 | 1 | 34 |
| swsr60 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 240 | 2871 | -893 | -1110 | -691 | 4303 | 1 | 34 |
| swsr60 | reject_native | pnf_7 | {"tol": 0.5, "conf": "body"} | sym15u / both | 207 | 2996 | -223 | 738 | -2958 | 2749 | 1 | 34 |
| swsr60 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 264 | 3367 | 417 | 713 | 2105 | 2877 | 1 | 34 |
| swsr60 | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 235 | 3947 | -295 | 1712 | 542 | 2019 | 1 | 34 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 251 | 5486 | 738 | 818 | 1504 | 1968 | 2 | 203 |
| stack | break_native | rng_80 | {"k": 2, "cw": 2.0} | sym8u / both | 307 | 6590 | -1020 | 397 | 79 | 3936 | 2 | 203 |
| stack | reject | pnf_5 | {"k": 2, "cw": 0.5} | sym15u / both | 152 | 2969 | -1754 | -1412 | -638 | 2326 | 1 | 203 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | asym20u/10u / both | 248 | 3290 | -789 | 971 | -1202 | 4802 | 2 | 203 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 204 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1335 | -822 | 539 | 550 | 1717 | 1 | 204 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 204 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 204 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 204 |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 126 | 1601 | -738 | -637 | 518 | 1605 | 1 | 204 |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1266 | -894 | 749 | 1751 | 1947 | 1 | 204 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 204 |
| channel | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 34 |
| channel | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 34 |
| channel | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 34 |
| channel | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 34 |
| channel | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 401 | 3917 | -208 | 972 | 4672 | 2881 | 1 | 34 |
| channel | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 463 | 4187 | 146 | -2476 | 4036 | 4709 | 1 | 34 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 527 | 5168 | 1396 | -726 | 235 | 2951 | 1 | 34 |
| channel | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 420 | 6420 | 1977 | 2723 | 3726 | 6347 | 1 | 34 |
| fvg15 | break | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 330 | -695 | 1898 | 2097 | 1 | 34 |
| fvg15 | break_native | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 408 | -695 | 1898 | 2097 | 1 | 34 |
| fvg15 | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 63 | 2026 | 106 | -1123 | 207 | 1397 | 1 | 34 |
| fvg15 | false_break_native | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 108 | 2100 | -895 | 84 | -297 | 1921 | 1 | 34 |
| fvg15 | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 176 | 1407 | -534 | 1658 | -536 | 571 | 1 | 34 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 354 | 1253 | 175 | 1053 | 1876 | 1196 | 1 | 34 |
| fvg15 | retest | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 34 |
| fvg15 | retest_native | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 34 |
| fvg5 | break | lbrk_3_40 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2212 | 932 | -1000 | -902 | -520 | 1 | 34 |
| fvg5 | break_native | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 2280 | 649 | 1613 | 1744 | 1553 | 1 | 34 |
| fvg5 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 1913 | -47 | -1966 | 1134 | 1338 | 1 | 34 |
| fvg5 | false_break_native | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 1676 | -1207 | -1321 | 1577 | 1248 | 1 | 34 |
| fvg5 | reject | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 126 | 1934 | 248 | 21 | 1054 | 1217 | 1 | 34 |
| fvg5 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 131 | 1899 | 677 | 400 | -1831 | 3448 | 1 | 34 |
| fvg5 | retest | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 222 | 3806 | -1035 | -262 | -445 | 2561 | 1 | 34 |
| fvg5 | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 2329 | -55 | -245 | -934 | 2721 | 1 | 34 |
| gaps | break | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 104 | -1328 | 2128 | 1944 | 1 | 204 |
| gaps | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 142 | -1328 | 2128 | 1944 | 1 | 204 |
| gaps | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -820 | -86 | 2898 | 2982 | 1 | 204 |
| gaps | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -762 | -86 | 2898 | 2982 | 1 | 204 |
| gaps | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 204 |
| gaps | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 204 |
| gaps | retest | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 494 | 2981 | -132 | -126 | -354 | 1963 | 1 | 204 |
| gaps | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / short | 304 | 2211 | -1073 | 726 | -402 | 1511 | 1 | 204 |
| mmove | break | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 34 |
| mmove | break_native | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 34 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 1 | 34 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 1 | 34 |
| mmove | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 95 | 2790 | 1939 | 398 | 1792 | 3227 | 1 | 34 |
| mmove | reject_native | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 317 | 3372 | -70 | 595 | -1300 | 2698 | 1 | 34 |
| mmove | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 329 | 3092 | 1424 | 140 | 3397 | 3171 | 1 | 34 |
| mmove | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 170 | 3030 | 552 | -385 | 1137 | 4321 | 1 | 34 |
| ob15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 143 | 2715 | -364 | 1077 | -198 | 2970 | 1 | 34 |
| ob15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 144 | 2579 | -490 | 437 | 440 | 3050 | 1 | 34 |
| ob15 | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 120 | 1724 | 1840 | 757 | 2754 | 1249 | 1 | 34 |
| ob15 | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | sym15u / both | 128 | 1730 | 694 | -773 | 1270 | -274 | 1 | 34 |
| ob15 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 128 | 1612 | -55 | -833 | 1139 | 1595 | 1 | 34 |
| ob15 | reject_native | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2140 | 289 | -157 | 1697 | 330 | 1 | 34 |
| ob15 | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 110 | 2538 | -231 | 102 | 2014 | 2666 | 1 | 34 |
| ob15 | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | plain60/60 / both | 200 | 2091 | 649 | -1044 | 32 | 1538 | 1 | 34 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 34 |
| ob5 | break_native | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 34 |
| ob5 | false_break | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 34 |
| ob5 | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 34 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 139 | 1592 | 443 | -1429 | -219 | 1037 | 1 | 34 |
| ob5 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 140 | 2232 | -724 | -50 | -411 | 97 | 1 | 34 |
| ob5 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 2614 | -885 | -1043 | -1778 | 2222 | 1 | 34 |
| ob5 | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 2537 | -637 | -296 | -515 | 1382 | 1 | 34 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 200 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 200 |
| open_range | false_break | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 435 | 2425 | 23 | -145 | -730 | 1542 | 2 | 200 |
| open_range | false_break_native | renko_20 | {"M": 1, "k": 0.5} | sym8u / both | 420 | 2670 | 231 | -183 | -1477 | 2468 | 2 | 200 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 200 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 200 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 200 |
| open_range | retest_native | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 298 | 4014 | 703 | 324 | -1734 | 2744 | 2 | 200 |
| opens | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 360 | 5490 | -643 | 803 | 229 | 6745 | 1 | 204 |
| opens | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 338 | 5821 | 1364 | -659 | -1602 | 6521 | 1 | 204 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 168 | 4705 | -649 | -420 | 1329 | 4754 | 1 | 204 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 1 | 204 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 367 | 5218 | -809 | 1237 | -891 | 2404 | 1 | 204 |
| opens | reject_native | vol_1100 | {"tol": 0.5, "conf": "body"} | sym15u / both | 349 | 4967 | 853 | 1322 | -3541 | 4460 | 2 | 204 |
| opens | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 306 | 4952 | 1079 | -2912 | 3174 | 4784 | 1 | 204 |
| opens | retest_native | pnf_20 | {"M": 6, "tol": 0.5} | sym15u / both | 294 | 4635 | 1331 | 789 | 2801 | 6670 | 1 | 204 |
| prior_day | break | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 204 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 204 |
| prior_day | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 6120 | 1169 | 654 | 6266 | 6027 | 1 | 204 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 1 | 204 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 204 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 204 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 204 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 204 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 203 |
| profile_nodes | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 277 | 3995 | 2467 | -1651 | 1370 | 3940 | 1 | 203 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 203 |
| profile_nodes | false_break_native | rng_40 | {"M": 1, "k": 0.5} | sym8u / both | 226 | 3965 | -671 | 942 | 823 | 4444 | 2 | 203 |
| profile_nodes | reject | renko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 483 | 3360 | 110 | -1175 | 115 | 1930 | 2 | 203 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 203 |
| profile_nodes | retest | renko_40 | {"M": 6, "tol": 0.5} | sym8u / both | 164 | 3845 | 172 | 438 | 986 | 2760 | 2 | 203 |
| profile_nodes | retest_native | cusum_28 | {"M": 10, "tol": 0.5} | sym15u / both | 262 | 4087 | 1118 | 403 | 1644 | 5061 | 1 | 203 |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 2 | 204 |
| profile_va | break_native | rng_28 | {"n": 2, "k": 0.5} | sym15u / both | 217 | 4047 | 449 | 1260 | 3137 | 4304 | 2 | 204 |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 198 | 3091 | 543 | 151 | 2346 | 3855 | 2 | 204 |
| profile_va | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | plain60/60 / both | 548 | 2993 | 1062 | 46 | 172 | 1929 | 1 | 204 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 1 | 204 |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 263 | 4791 | -360 | 58 | 2424 | 3455 | 1 | 204 |
| profile_va | retest | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 465 | 3564 | -541 | -277 | 960 | 1989 | 1 | 204 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 204 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 204 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 204 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 204 |
| round | false_break_native | vol_500 | {"M": 2, "k": 0.5} | asym10u/20u / both | 543 | 5669 | -1429 | -2821 | 263 | 7059 | 2 | 204 |
| round | reject | renko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 657 | 8023 | -600 | -3119 | -4002 | 8822 | 2 | 204 |
| round | reject_native | vsess_200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 540 | 6009 | 257 | -1854 | -806 | 4925 | 2 | 204 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 204 |
| round | retest_native | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 617 | 6587 | -614 | 2075 | 217 | 5937 | 2 | 204 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 202 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 202 |
| session_hl | false_break | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 346 | 4857 | 1820 | -135 | 2442 | 2702 | 1 | 202 |
| session_hl | false_break_native | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 344 | 5417 | 1497 | 47 | 2767 | 3055 | 1 | 202 |
| session_hl | reject | tick_5000 | {"tol": 0.0, "conf": "body"} | sym8u / both | 257 | 2738 | -362 | 1005 | -702 | 2504 | 2 | 202 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 202 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 202 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 202 |
| trendline | break | kagi_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 538 | 3996 | 289 | 1595 | -1677 | 2376 | 1 | 34 |
| trendline | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 297 | 3534 | 1905 | 1508 | -2673 | 3553 | 1 | 34 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 285 | 4062 | 1560 | 1127 | 1434 | 5996 | 1 | 34 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4692 | 42 | 1654 | 1101 | 5496 | 1 | 34 |
| trendline | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 206 | 2009 | -383 | -16 | 2214 | 954 | 1 | 34 |
| trendline | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 272 | 3205 | 233 | 64 | 1560 | 4027 | 1 | 34 |
| trendline | retest | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 234 | 3192 | -7 | -266 | -583 | 2917 | 1 | 34 |
| trendline | retest_native | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 283 | 3545 | 204 | 994 | 2670 | 3978 | 1 | 34 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 204 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 204 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 204 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 204 |
| uw_dp | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 94 | 3468 | 0 | 0 | 524 | 3496 | 1 | 204 |
| uw_dp | reject_native | mom_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 135 | 3130 | 0 | 0 | 439 | 2925 | 1 | 204 |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 153 | 3839 | 0 | 0 | 1297 | 3514 | 2 | 204 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 204 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 203 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 1 | 203 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 1 | 203 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 1 | 203 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 1 | 203 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 203 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 203 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 203 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 203 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 203 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 203 |
| uw_qqq | false_break_native | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3384 | 0 | 197 | 3751 | 4321 | 1 | 203 |
| uw_qqq | reject | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 203 |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 203 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 203 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 203 |
| vwap | break | rng_80 | {"n": 2, "k": 0.5} | sym8u / both | 294 | 4569 | 929 | 247 | 3761 | 4575 | 2 | 203 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 203 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 178 | 4696 | 63 | -174 | 2422 | 5048 | 1 | 203 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 166 | 4411 | -108 | -214 | 2319 | 4241 | 1 | 203 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 203 |
| vwap | reject_native | tm60 | {"tol": 0.0, "conf": "close"} | sym15u / both | 302 | 5838 | -1468 | 1495 | -1469 | 6714 | 1 | 203 |
| vwap | retest | tm15 | {"M": 10, "tol": 0.5} | sym15u / both | 353 | 4113 | 1019 | 662 | 1923 | 5583 | 1 | 203 |
| vwap | retest_native | tm15 | {"M": 6, "tol": 0.5} | sym15u / both | 352 | 4260 | 459 | 1038 | 2222 | 6362 | 1 | 203 |
| vwap_bands | break | mom_20 | {"n": 3, "k": 0.5} | sym15u / both | 475 | 6544 | 86 | 1981 | 5311 | 8312 | 1 | 202 |
| vwap_bands | break_native | drb_400 | {"n": 2, "k": 0.25} | sym15u / both | 545 | 5721 | -772 | -2232 | 2651 | 4494 | 1 | 202 |
| vwap_bands | false_break | swing_atr_0.6 | {"M": 3, "k": 0.5} | sym15u / both | 477 | 3977 | 1234 | -534 | 5712 | 3574 | 1 | 202 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 202 |
| vwap_bands | reject | tick_300 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 481 | 6944 | 1737 | -351 | 2059 | 7316 | 2 | 202 |
| vwap_bands | reject_native | vol_500 | {"tol": 0.5, "conf": "close"} | asym10u/20u / both | 512 | 6769 | -741 | 751 | 2018 | 2515 | 2 | 202 |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 475 | 5871 | -47 | -3369 | -2356 | 8027 | 2 | 202 |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 452 | 5820 | -431 | 1126 | 1466 | 4714 | 1 | 202 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 204 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 204 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 204 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 204 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 | 1812 | 674 | -92 | 992 | 1655 | 1 | 204 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 82 | 2131 | 988 | -272 | -1646 | 1573 | 1 | 204 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 204 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 204 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 203 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym15u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 1 | 203 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 3068 | 829 | 2566 | -2302 | 3067 | 1 | 203 |
| zones | false_break_native | urenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 169 | 3155 | 720 | 2082 | -2078 | 3224 | 1 | 203 |
| zones | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 96 | 2134 | 178 | -1365 | -390 | 3312 | 1 | 203 |
| zones | reject_native | dlt_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 2882 | -1835 | -913 | -60 | 3270 | 1 | 203 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 203 |
| zones | retest_native | rng_14 | {"M": 6, "tol": 0.5} | sym8u / both | 217 | 2669 | -1529 | -653 | -535 | 2164 | 2 | 203 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 63 | 745 | -750 | 713 | 55 | 78 | 1 | 34 |
| sdx15 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 218 | 3979 | 866 | -1611 | -3817 | 3589 | 1 | 34 |
| sdx15 | lim_prox | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 276 | 3753 | 213 | -649 | -2699 | 2977 | 1 | 34 |
| sdx15 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 151 | 2838 | 1403 | -67 | -500 | 3343 | 1 | 34 |
| sdx15 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / both | 103 | 1888 | -308 | 1188 | 1098 | 2361 | 1 | 34 |
| sdx15 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 34 |
| sdx15 | rej_zone | kagi_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 34 |
| sdx15 | retest | pnf_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 31 | 526 | -752 | 859 | -350 | 61 | 1 | 34 |
| sdx3 | break | pnf_7 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 103 | 1995 | -691 | -13 | 2296 | 1834 | 1 | 34 |
| sdx3 | lim_mid | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 315 | 3243 | 1073 | -1181 | -5173 | 1197 | 1 | 34 |
| sdx3 | lim_prox | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 405 | 3173 | -505 | 837 | -3633 | 2384 | 1 | 34 |
| sdx3 | rej | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 108 | 2223 | 1029 | -286 | -877 | 2043 | 1 | 34 |
| sdx3 | rej_flow | wrenko_14 | {"d": "B", "F": 9} | plain60/60 / both | 51 | 1295 | 306 | 9 | -317 | 994 | 1 | 34 |
| sdx3 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 34 |
| sdx3 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 34 |
| sdx3 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 68 | 1390 | 118 | 65 | 1080 | 1692 | 1 | 34 |
| sdx30 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 34 | 466 | -431 | 870 | -122 | 440 | 1 | 34 |
| sdx30 | lim_mid | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 103 | 1951 | 721 | -406 | -107 | 947 | 1 | 34 |
| sdx30 | lim_prox | kagi_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 217 | 2657 | -934 | -1031 | -26 | 1123 | 1 | 34 |
| sdx30 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 38 | 1091 | -267 | -1452 | -151 | 712 | 1 | 34 |
| sdx30 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | plain60/60 / short | 35 | 383 | -313 | -316 | -602 | 47 | 1 | 34 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 34 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 34 |
| sdx5 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 91 | 2323 | -533 | 988 | 255 | 1749 | 1 | 34 |
| sdx5 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 354 | 2442 | 357 | 891 | -1052 | 3642 | 1 | 34 |
| sdx5 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 746 | 2572 | -102 | -1530 | -5419 | 2741 | 1 | 34 |
| sdx5 | rej | kagi_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 143 | 2330 | 3481 | 902 | -3209 | 2420 | 1 | 34 |
| sdx5 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | plain60/60 / short | 113 | 441 | 27 | 873 | 69 | 704 | 1 | 34 |
| sdx5 | rej_native | urenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 178 | 2412 | -1189 | 369 | -649 | 2087 | 1 | 34 |
| sdx5 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 198 | 2334 | -819 | -884 | -1076 | 2111 | 1 | 34 |
| sdx5 | retest | kagi_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 82 | 1774 | -756 | -147 | -45 | 2087 | 1 | 34 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 384 | 10 | 407 | 778 | 289 | 1 | 34 |
| sdx60 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 73 | 1628 | 155 | 544 | -311 | 1363 | 1 | 34 |
| sdx60 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 259 | 1933 | -320 | -699 | -24 | 2535 | 1 | 34 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 76 | 986 | -87 | -92 | 901 | 1294 | 1 | 34 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 37 | 432 | -131 | 314 | 665 | 397 | 1 | 34 |
| sdx60 | rej_native | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 34 |
| sdx60 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 34 |
| sdx_renko28 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 129 | 2292 | -1534 | 786 | -391 | 1043 | 1 | 34 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 34 |
| sdx_renko28 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 285 | 3300 | 213 | 469 | 2009 | 5781 | 1 | 34 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 279 | 4161 | -1746 | -3181 | -2583 | 3043 | 1 | 34 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 142 | 877 | 513 | -550 | 377 | 864 | 1 | 34 |
| sdx_renko28 | rej_native | pnf_5 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 34 |
| sdx_renko28 | rej_zone | pnf_5 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 34 |
| sdx_renko28 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 89 | 1596 | -851 | 795 | 41 | 977 | 1 | 34 |
| sdx_rng28 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 301 | 3408 | -2123 | 661 | -816 | 3058 | 1 | 34 |
| sdx_rng28 | lim_mid | frenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 331 | 3377 | 299 | -3020 | -3304 | 3142 | 1 | 34 |
| sdx_rng28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 343 | 3324 | -202 | 219 | -1999 | 2640 | 1 | 34 |
| sdx_rng28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 472 | 2249 | 2358 | -2729 | 945 | 3149 | 1 | 34 |
| sdx_rng28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 224 | 2295 | 245 | -1493 | 2758 | 457 | 1 | 34 |
| sdx_rng28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 34 |
| sdx_rng28 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 34 |
| sdx_rng28 | retest | kagi_40 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 146 | 2051 | -787 | -89 | -67 | 1971 | 1 | 34 |
| sdx_vol1100 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 314 | 4031 | -1409 | -503 | 658 | 4201 | 1 | 34 |
| sdx_vol1100 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 275 | 6337 | -998 | 71 | 1443 | 6397 | 1 | 34 |
| sdx_vol1100 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 278 | 5565 | -679 | -26 | -465 | 6171 | 1 | 34 |
| sdx_vol1100 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 346 | 2639 | 554 | -192 | -349 | 2420 | 1 | 34 |
| sdx_vol1100 | rej_flow | wrenko_20 | {"d": "E", "F": 0} | sym15u / short | 90 | 2232 | -129 | -218 | 268 | 1907 | 1 | 34 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 768 | 3970 | -570 | -433 | -756 | 4714 | 1 | 34 |
| sdx_vol1100 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 162 | 3444 | 914 | 374 | -624 | 4290 | 1 | 34 |
| sdx_vol1100 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 134 | 2174 | -829 | 511 | -380 | 1220 | 1 | 34 |
| fib15 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3386 | -215 | -1066 | -1338 | 3676 | 1 | 34 |
| fib15 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3296 | 118 | -747 | -1540 | 3799 | 1 | 34 |
| fib15 | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 34 |
| fib15 | false_break_native | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 34 |
| fib15 | pullback | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 92 | 1869 | -30 | -12 | -37 | 2298 | 1 | 34 |
| fib15 | pullback_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / short | 83 | 2154 | 184 | -420 | -152 | 2586 | 1 | 34 |
| fib15 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 34 |
| fib15 | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 34 |
| fib15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / short | 125 | 3286 | 93 | -404 | 983 | 3482 | 1 | 34 |
| fib15 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 208 | 3836 | 116 | -100 | -2461 | 3206 | 1 | 34 |
| fib5 | break | kagi_14 | {"n": 2, "k": 0.25} | sym15u / both | 287 | 4326 | 634 | -449 | -5249 | 4348 | 1 | 34 |
| fib5 | break_native | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 283 | 3290 | -1099 | 214 | -1933 | 5199 | 1 | 34 |
| fib5 | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 34 |
| fib5 | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 34 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 1 | 34 |
| fib5 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / short | 135 | 1865 | -693 | 1105 | -22 | 1426 | 1 | 34 |
| fib5 | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 389 | 5190 | 867 | 1104 | 100 | 5716 | 1 | 34 |
| fib5 | reject_native | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 295 | 3775 | -1517 | 2905 | 1380 | 4817 | 1 | 34 |
| fib5 | retest | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 213 | 2669 | -792 | 1234 | -3864 | 4158 | 1 | 34 |
| fib5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 282 | 2959 | -1605 | -750 | -58 | 3452 | 1 | 34 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 34 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 34 |
| fib60 | false_break | urenko_20 | {"M": 2, "k": 0.5} | sym15u / both | 180 | 2491 | -930 | -991 | -2211 | 2940 | 1 | 34 |
| fib60 | false_break_native | mrenko_10 | {"M": 3, "k": 0.5} | sym15u / both | 241 | 2680 | -442 | -424 | -1292 | 1918 | 1 | 34 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 66 | 950 | -134 | -49 | -111 | 1331 | 1 | 34 |
| fib60 | pullback_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / short | 30 | 1090 | 514 | -645 | 216 | 1306 | 1 | 34 |
| fib60 | reject | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 139 | 1820 | -241 | -150 | -56 | 433 | 1 | 34 |
| fib60 | reject_native | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 181 | 2566 | -602 | -1595 | -766 | 3167 | 1 | 34 |
| fib60 | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 124 | 2392 | -360 | 1609 | -959 | 2711 | 1 | 34 |
| fib60 | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2972 | -1194 | 195 | 1413 | 1856 | 1 | 34 |
| fibr_dev | break | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 323 | 3270 | -463 | 160 | 151 | 3127 | 1 | 34 |
| fibr_dev | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 318 | 3177 | 292 | 1852 | -1651 | 4840 | 1 | 34 |
| fibr_dev | false_break | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / short | 135 | 2113 | -1084 | 533 | -722 | 1248 | 1 | 34 |
| fibr_dev | false_break_native | pnf_14 | {"M": 2, "k": 0.5} | sym15u / short | 147 | 2266 | -564 | -453 | 81 | 2314 | 1 | 34 |
| fibr_dev | reject | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 111 | 3039 | -906 | -439 | 785 | 4073 | 1 | 34 |
| fibr_dev | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 209 | 2679 | -1704 | 1086 | -206 | 3193 | 1 | 34 |
| fibr_dev | retest | kagi_112 | {"M": 10, "tol": 0.5} | sym15u / both | 209 | 2769 | -1419 | 969 | 78 | 2576 | 1 | 34 |
| fibr_dev | retest_native | kagi_112 | {"M": 3, "tol": 0.0} | sym15u / both | 193 | 2734 | -611 | -1064 | -1498 | 2411 | 1 | 34 |
| fibr_ib | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 251 | 3612 | 92 | -1032 | -493 | 1859 | 1 | 34 |
| fibr_ib | break_native | frenko_40 | {"n": 2, "k": 0.25} | sym15u / both | 245 | 3856 | -1527 | 184 | -1787 | 3643 | 1 | 34 |
| fibr_ib | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 231 | 2998 | -1461 | -465 | -1676 | 5234 | 1 | 34 |
| fibr_ib | false_break_native | mrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 258 | 3604 | -782 | -1742 | -1366 | 5952 | 1 | 34 |
| fibr_ib | reject | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 2311 | -1067 | -120 | 1124 | 4438 | 1 | 34 |
| fibr_ib | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 116 | 2936 | -599 | 129 | -207 | 3430 | 1 | 34 |
| fibr_ib | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 34 |
| fibr_ib | retest_native | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 34 |
| fibr_on | break | urenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 206 | 2288 | -1496 | 1579 | 3141 | 1942 | 1 | 34 |
| fibr_on | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 235 | 2613 | 83 | 1407 | 1700 | 2276 | 1 | 34 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 232 | 2221 | -828 | 1006 | -1840 | 1304 | 1 | 34 |
| fibr_on | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 233 | 2219 | -607 | 594 | -2194 | 1699 | 1 | 34 |
| fibr_on | reject | kagi_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 111 | 2090 | -805 | -1514 | 1626 | 2220 | 1 | 34 |
| fibr_on | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 274 | 3277 | -279 | -634 | -938 | 2826 | 1 | 34 |
| fibr_on | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 228 | 2547 | -512 | 810 | -273 | 485 | 1 | 34 |
| fibr_on | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 217 | 2587 | -133 | 2095 | -1145 | 3420 | 1 | 34 |
| fibr_or | break | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 223 | 3722 | 1679 | 177 | 2896 | 4918 | 1 | 34 |
| fibr_or | break_native | lbrk_3_10 | {"n": 2, "k": 0.25} | sym15u / both | 296 | 3227 | -97 | -651 | -3922 | 1283 | 1 | 34 |
| fibr_or | false_break | kagi_10 | {"M": 2, "k": 0.5} | sym15u / both | 227 | 3162 | -2539 | 1556 | 88 | 4085 | 1 | 34 |
| fibr_or | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 2711 | -2616 | 999 | 797 | 3303 | 1 | 34 |
| fibr_or | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 34 |
| fibr_or | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 34 |
| fibr_or | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / short | 106 | 2541 | -582 | -25 | -891 | 2914 | 1 | 34 |
| fibr_or | retest_native | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 226 | 3433 | -1079 | 1971 | 1090 | 4690 | 1 | 34 |
| fibr_pd | break | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 34 |
| fibr_pd | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 34 |
| fibr_pd | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 1998 | -349 | 1339 | -3324 | 2735 | 1 | 34 |
| fibr_pd | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 38 | -1381 | 1884 | 1 | 34 |
| fibr_pd | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 197 | 3093 | 14 | 1008 | -2214 | 3340 | 1 | 34 |
| fibr_pd | reject_native | kagi_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 3634 | -868 | -66 | -1162 | 2545 | 1 | 34 |
| fibr_pd | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 88 | 2090 | 436 | -59 | -1075 | 1885 | 1 | 34 |
| fibr_pd | retest_native | kagi_56 | {"M": 6, "tol": 0.5} | sym15u / short | 101 | 2104 | 27 | 796 | -2196 | 1839 | 1 | 34 |
| piv_cama | break | kagi_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 529 | 2062 | 1743 | 913 | -1667 | 1448 | 1 | 34 |
| piv_cama | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 219 | 2483 | 797 | 1927 | 1854 | 4271 | 1 | 34 |
| piv_cama | false_break | kagi_20 | {"M": 1, "k": 0.0} | sym15u / both | 232 | 1059 | -2014 | 1462 | -4681 | 3019 | 1 | 34 |
| piv_cama | false_break_native | kagi_20 | {"M": 3, "k": 0.5} | sym15u / both | 231 | 1272 | -2038 | 898 | -4067 | 2317 | 1 | 34 |
| piv_cama | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 536 | 2838 | 205 | -269 | -2327 | 3249 | 1 | 34 |
| piv_cama | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 551 | 2235 | 495 | -257 | -1384 | 2735 | 1 | 34 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 3017 | 1323 | -981 | 973 | 1360 | 1 | 34 |
| piv_cama | retest_native | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 209 | 2890 | -621 | -741 | 2051 | 2186 | 1 | 34 |
| piv_floor | break | urenko_80 | {"n": 2, "k": 0.25} | sym15u / both | 146 | 2104 | 89 | 2484 | 144 | 1328 | 1 | 34 |
| piv_floor | break_native | urenko_56 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2598 | 440 | 2679 | 586 | 1925 | 1 | 34 |
| piv_floor | false_break | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 34 |
| piv_floor | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 34 |
| piv_floor | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 174 | 2732 | 312 | 945 | 1219 | 3340 | 1 | 34 |
| piv_floor | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 4162 | -247 | 2182 | -410 | 2889 | 1 | 34 |
| piv_floor | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 2261 | -762 | -663 | -1617 | 2246 | 1 | 34 |
| piv_floor | retest_native | lbrk_3_10 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 2174 | 539 | -433 | 264 | 1551 | 1 | 34 |
| piv_wf | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 34 |
| piv_wf | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 34 |
| piv_wf | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 225 | 2201 | -2119 | 1210 | 156 | 75 | 1 | 34 |
| piv_wf | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1842 | 1094 | 416 | -154 | 1 | 34 |
| piv_wf | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 88 | 1762 | -1585 | -62 | -1571 | 3382 | 1 | 34 |
| piv_wf | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 265 | 3055 | -151 | -947 | -2159 | 1619 | 1 | 34 |
| piv_wf | retest | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 34 |
| piv_wf | retest_native | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 34 |
| swcluster | break | pnf_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 78 | 1434 | -579 | -308 | -267 | 1378 | 1 | 34 |
| swcluster | break_native | lbrk_3_20 | {"n": 3, "k": 0.5} | sym15u / both | 47 | 1484 | -898 | 212 | -2023 | 2300 | 1 | 34 |
| swcluster | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 66 | 711 | -608 | 898 | -670 | 546 | 1 | 34 |
| swcluster | false_break_native | urenko_112 | {"M": 3, "k": 0.5} | sym15u / both | 33 | 948 | -1573 | 501 | -496 | 1074 | 1 | 34 |
| swcluster | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1368 | -235 | -439 | 744 | 1365 | 1 | 34 |
| swcluster | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 51 | 1544 | 242 | 371 | -1281 | 1329 | 1 | 34 |
| swcluster | retest | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 41 | 1442 | -759 | 86 | 271 | 908 | 1 | 34 |
| swcluster | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 39 | 1287 | -302 | 729 | 809 | 785 | 1 | 34 |
| swsr15 | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / short | 117 | 3147 | -556 | 558 | 71 | 3221 | 1 | 34 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / short | 117 | 3147 | -556 | 558 | 71 | 3221 | 1 | 34 |
| swsr15 | false_break | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 247 | 2905 | -826 | 1401 | 1932 | 1475 | 1 | 34 |
| swsr15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / short | 117 | 2948 | 43 | -480 | 1191 | 3055 | 1 | 34 |
| swsr15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 118 | 3340 | 255 | -524 | 1304 | 2502 | 1 | 34 |
| swsr15 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 271 | 4013 | 690 | 61 | -2201 | 2481 | 1 | 34 |
| swsr15 | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 176 | 2920 | 1261 | 1356 | -1090 | 2148 | 1 | 34 |
| swsr15 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 246 | 2938 | -421 | -968 | 2213 | 2463 | 1 | 34 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 34 |
| swsr5 | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 34 |
| swsr5 | false_break | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 34 |
| swsr5 | false_break_native | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 34 |
| swsr5 | reject | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / short | 131 | 2900 | 435 | -192 | 1157 | 4072 | 1 | 34 |
| swsr5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 236 | 2951 | -1432 | 2774 | -395 | 2301 | 1 | 34 |
| swsr5 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 260 | 4440 | -950 | -3103 | 1054 | 1787 | 1 | 34 |
| swsr5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 291 | 4019 | -261 | -2125 | 4208 | 2958 | 1 | 34 |
| swsr60 | break | pnf_40 | {"n": 2, "k": 0.25} | sym15u / short | 38 | 1767 | 558 | -107 | 48 | 2005 | 1 | 34 |
| swsr60 | break_native | kagi_40 | {"n": 3, "k": 0.5} | sym15u / both | 163 | 2879 | -1426 | 831 | -277 | 3346 | 1 | 34 |
| swsr60 | false_break | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 1784 | -2173 | -454 | -1920 | 1883 | 1 | 34 |
| swsr60 | false_break_native | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 1784 | -2173 | -454 | -1920 | 1883 | 1 | 34 |
| swsr60 | reject | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 81 | 1934 | -1464 | 154 | -1935 | 2404 | 1 | 34 |
| swsr60 | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 212 | 3196 | -733 | 1116 | -3739 | 3316 | 1 | 34 |
| swsr60 | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / short | 129 | 1496 | 335 | -641 | -63 | 1628 | 1 | 34 |
| swsr60 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 1967 | -1647 | 1506 | -2401 | 1541 | 1 | 34 |
| stack | break | urenko_28 | {"k": 2, "cw": 0.5} | sym15u / short | 86 | 2291 | 234 | -41 | 1145 | 1866 | 1 | 203 |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 107 | 3072 | 144 | 769 | -10 | 2485 | 1 | 203 |
| stack | reject | rng_20 | {"k": 2, "cw": 1.0} | asym10u/20u / both | 101 | 2187 | -447 | 1473 | -506 | 1062 | 2 | 203 |
| stack | reject_native | mrenko_14 | {"k": 2, "cw": 0.5} | sym15u / both | 215 | 2715 | -713 | -2101 | -338 | 3647 | 1 | 203 |
| book_walls | break | time_s_5 | {"n": 2, "k": 0.25} | plain60/60 / both | 42 | 894 | -489 | -382 | 220 | 1042 | 1 | 202 |
| book_walls | break_native | tm15 | {"n": 1, "k": 0.0} | plain60/60 / both | 30 | 605 | -584 | -435 | -96 | 784 | 1 | 202 |
| book_walls | reject | time_s_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 47 | 475 | -958 | -263 | -638 | 569 | 1 | 202 |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 34 | 561 | 55 | -204 | -128 | 492 | 1 | 202 |
| book_walls | retest | time_s_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 499 | -402 | -181 | 44 | 592 | 1 | 202 |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 34 | 627 | -374 | 538 | 3 | 600 | 1 | 202 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 204 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 204 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 204 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 204 |
| book_walls_loose | reject | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 57 | 1173 | 963 | -1384 | -1489 | 994 | 2 | 204 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 204 |
| book_walls_loose | retest | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / short | 41 | 962 | -161 | -663 | 174 | 1475 | 1 | 204 |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 1146 | 212 | 787 | -261 | 941 | 1 | 204 |
| channel | break | pnf_20 | {"n": 1, "k": 0.0} | sym15u / both | 259 | 2734 | 517 | -988 | -662 | 4298 | 1 | 34 |
| channel | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 275 | 3932 | -2003 | 2173 | -8 | 4372 | 1 | 34 |
| channel | false_break | pnf_7 | {"M": 3, "k": 0.5} | sym15u / both | 293 | 3216 | -1127 | 782 | 1821 | 3617 | 1 | 34 |
| channel | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 269 | 3285 | -130 | 684 | 4085 | 3749 | 1 | 34 |
| channel | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 200 | 3044 | -754 | 780 | -1553 | 4489 | 1 | 34 |
| channel | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 227 | 3124 | -1460 | -819 | -1409 | 4809 | 1 | 34 |
| channel | retest | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 2884 | -1066 | -819 | -1144 | 2504 | 1 | 34 |
| channel | retest_native | kagi_40 | {"M": 6, "tol": 0.5} | sym15u / both | 279 | 4816 | -153 | -1208 | 1427 | 4943 | 1 | 34 |
| fvg15 | break | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 34 |
| fvg15 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 34 |
| fvg15 | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 34 |
| fvg15 | false_break_native | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 34 |
| fvg15 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 59 | 1177 | 560 | -604 | 190 | 541 | 1 | 34 |
| fvg15 | reject_native | pnf_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 111 | 1044 | -987 | 68 | 64 | 1053 | 1 | 34 |
| fvg15 | retest | urenko_28 | {"M": 10, "tol": 0.5} | sym15u / both | 81 | 1488 | -659 | 345 | -893 | 1193 | 1 | 34 |
| fvg15 | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 97 | 2069 | -451 | 295 | -1907 | 1585 | 1 | 34 |
| fvg5 | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2941 | -43 | 529 | 74 | 1047 | 1 | 34 |
| fvg5 | break_native | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 2590 | -1104 | -310 | -224 | 1211 | 1 | 34 |
| fvg5 | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / short | 97 | 1497 | 237 | -1092 | -344 | 965 | 1 | 34 |
| fvg5 | false_break_native | kagi_28 | {"M": 3, "k": 0.5} | sym15u / short | 110 | 1603 | -227 | -235 | -464 | 1975 | 1 | 34 |
| fvg5 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 157 | 1877 | 86 | 1529 | -360 | 2685 | 1 | 34 |
| fvg5 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 218 | 1978 | -13 | -449 | -1512 | 1297 | 1 | 34 |
| fvg5 | retest | wrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 170 | 1812 | -1404 | 1937 | 357 | 1585 | 1 | 34 |
| fvg5 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 148 | 1893 | 54 | 15 | -175 | 1618 | 1 | 34 |
| gaps | break | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 106 | 2351 | -1950 | -331 | -1857 | 1830 | 1 | 204 |
| gaps | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 108 | 1966 | -1477 | 311 | -678 | 1813 | 1 | 204 |
| gaps | false_break | time_s_5 | {"M": 1, "k": 0.0} | sym30u / both | 39 | 1447 | -588 | 325 | -1319 | 918 | 2 | 204 |
| gaps | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 113 | 1904 | -1039 | 978 | -175 | 1124 | 1 | 204 |
| gaps | reject | kagi_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 31 | 1442 | -214 | -380 | -128 | 1246 | 1 | 204 |
| gaps | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2841 | -343 | 129 | -838 | 2493 | 1 | 204 |
| gaps | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 102 | 1919 | -539 | 412 | 1770 | 768 | 1 | 204 |
| gaps | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 122 | 2649 | -496 | -97 | 417 | 1216 | 1 | 204 |
| mmove | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 34 |
| mmove | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 34 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 34 |
| mmove | false_break_native | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 34 |
| mmove | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 144 | 1952 | 75 | -438 | 2598 | 782 | 1 | 34 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / short | 134 | 2490 | -534 | 260 | 1315 | 2427 | 1 | 34 |
| mmove | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 34 |
| mmove | retest_native | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 34 |
| ob15 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1173 | -161 | 1098 | 647 | 1326 | 1 | 34 |
| ob15 | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1173 | -161 | 1098 | 647 | 1326 | 1 | 34 |
| ob15 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 55 | 1383 | -438 | 971 | 66 | 1341 | 1 | 34 |
| ob15 | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 51 | 1394 | -674 | 804 | 277 | 1544 | 1 | 34 |
| ob15 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 55 | 925 | -325 | -377 | 1269 | 2009 | 1 | 34 |
| ob15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 55 | 1100 | 158 | 617 | 1076 | 2402 | 1 | 34 |
| ob15 | retest | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1312 | -71 | 347 | 114 | 1901 | 1 | 34 |
| ob15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1242 | -237 | 630 | -361 | 1947 | 1 | 34 |
| ob5 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 80 | 1964 | -227 | -120 | 1433 | 2441 | 1 | 34 |
| ob5 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 2181 | -420 | 239 | 1123 | 2407 | 1 | 34 |
| ob5 | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 49 | 1758 | -619 | 734 | 1100 | 1775 | 1 | 34 |
| ob5 | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 49 | 1758 | -619 | 734 | 1100 | 1775 | 1 | 34 |
| ob5 | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 72 | 1483 | -588 | -295 | -66 | 561 | 1 | 34 |
| ob5 | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 125 | 1452 | -364 | -720 | -1186 | 1708 | 1 | 34 |
| ob5 | retest | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 77 | 2171 | -115 | 238 | -314 | 2762 | 1 | 34 |
| ob5 | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 78 | 2276 | 28 | 288 | 302 | 2581 | 1 | 34 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 202 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 202 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym15u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 1 | 202 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 202 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 202 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 202 |
| open_range | retest | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 202 |
| open_range | retest_native | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 202 |
| opens | break | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 204 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 204 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 204 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 204 |
| opens | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 204 |
| opens | reject_native | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 204 |
| opens | retest | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 204 |
| opens | retest_native | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 204 |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 2 | 204 |
| prior_day | break_native | vsess_120 | {"n": 3, "k": 0.0} | sym15u / both | 91 | 2959 | -204 | -697 | -3330 | 1835 | 2 | 204 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 115 | 2873 | -837 | 323 | -2884 | 1490 | 1 | 204 |
| prior_day | false_break_native | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 88 | 2868 | -302 | 511 | -1840 | 2689 | 2 | 204 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 204 |
| prior_day | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 2665 | 149 | 475 | -2001 | 1894 | 2 | 204 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 1 | 204 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 1 | 204 |
| profile_nodes | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2489 | -45 | -739 | -7388 | 1667 | 1 | 203 |
| profile_nodes | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 146 | 2992 | -647 | 1127 | -2618 | 2123 | 1 | 203 |
| profile_nodes | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 180 | 2054 | -1160 | -714 | -3668 | 2648 | 2 | 203 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 203 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 203 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 203 |
| profile_nodes | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 109 | 2447 | -490 | 89 | -3842 | 2750 | 1 | 203 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 128 | 2802 | -508 | 830 | -3084 | 3094 | 1 | 203 |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 93 | 2285 | -957 | 2055 | -845 | 2570 | 2 | 204 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 204 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 204 |
| profile_va | false_break_native | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 204 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 204 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 204 |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 204 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 204 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 290 | 4837 | -1805 | 1243 | 3655 | 5119 | 1 | 204 |
| round | break_native | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 292 | 3869 | -1678 | -471 | -86 | 2338 | 1 | 204 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 204 |
| round | false_break_native | urenko_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 965 | 4358 | -1829 | -1460 | 284 | 6297 | 1 | 204 |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 2 | 204 |
| round | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 313 | 4704 | -419 | 268 | -1458 | 3186 | 1 | 204 |
| round | retest | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 302 | 4728 | -399 | 513 | -1661 | 5351 | 2 | 204 |
| round | retest_native | renko_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 319 | 4722 | -107 | 506 | 309 | 2985 | 2 | 204 |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 171 | 3430 | -820 | 2114 | -94 | 2764 | 1 | 202 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 202 |
| session_hl | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 237 | 2956 | 1816 | 1583 | -123 | 2794 | 2 | 202 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 202 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 1 | 202 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 202 |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 95 | 3205 | -819 | -845 | -75 | 4545 | 2 | 202 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 202 |
| trendline | break | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 397 | 2404 | -1368 | -1341 | -1311 | 2339 | 1 | 34 |
| trendline | break_native | kagi_14 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 3812 | 1332 | 2406 | 3337 | 5866 | 1 | 34 |
| trendline | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3067 | 348 | -1809 | 440 | 2553 | 1 | 34 |
| trendline | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 2770 | 640 | -2164 | 534 | 2407 | 1 | 34 |
| trendline | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 154 | 1991 | 1175 | -2319 | 1129 | 389 | 1 | 34 |
| trendline | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 239 | 3408 | 1778 | 3021 | 2069 | 2094 | 1 | 34 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 34 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 34 |
| uw_dp | break | swing_atr_0.4 | {"n": 2, "k": 0.25} | sym15u / both | 63 | 2095 | 0 | 0 | 399 | 1949 | 1 | 204 |
| uw_dp | break_native | tick_800 | {"n": 2, "k": 0.5} | sym15u / both | 64 | 2127 | 0 | 0 | -317 | 1086 | 2 | 204 |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1430 | 0 | 0 | 210 | 1085 | 1 | 204 |
| uw_dp | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 61 | 1448 | 0 | 0 | 28 | 1366 | 2 | 204 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 74 | 1508 | 0 | 0 | -241 | 886 | 1 | 204 |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 92 | 2286 | 0 | 0 | -217 | 1948 | 2 | 204 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 56 | 1926 | 0 | 0 | 295 | 2044 | 1 | 204 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 204 |
| uw_ndx | break | rng_40 | {"n": 3, "k": 0.25} | sym8u / both | 95 | 2347 | 0 | -1001 | -2044 | 1016 | 2 | 203 |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 102 | 2167 | 0 | -30 | -1920 | 1473 | 2 | 203 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 203 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 203 |
| uw_ndx | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 101 | 1925 | 0 | -40 | -1237 | 2405 | 2 | 203 |
| uw_ndx | reject_native | swing_atr_0.25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 123 | 1867 | 0 | -44 | -84 | 927 | 1 | 203 |
| uw_ndx | retest | swing_atr_0.15 | {"M": 6, "tol": 0.5} | sym15u / both | 95 | 2055 | 0 | 271 | -781 | 2249 | 1 | 203 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 110 | 2464 | 0 | -631 | 475 | 2424 | 1 | 203 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 203 |
| uw_qqq | break_native | renko_10 | {"n": 2, "k": 0.0} | sym8u / both | 261 | 1644 | 0 | -302 | -257 | 171 | 2 | 203 |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 129 | 1746 | 0 | 169 | -358 | 956 | 2 | 203 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 203 |
| uw_qqq | reject | vol_750 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 239 | 1562 | 0 | 34 | -577 | 1228 | 2 | 203 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 203 |
| uw_qqq | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 93 | 1917 | 0 | 437 | -582 | 1450 | 1 | 203 |
| uw_qqq | retest_native | dchg_20 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1938 | 0 | 452 | -985 | 1145 | 1 | 203 |
| vwap | break | renko_40 | {"n": 1, "k": 0.25} | sym8u / both | 149 | 3681 | -1617 | 765 | 724 | 2951 | 2 | 203 |
| vwap | break_native | time_m_1 | {"n": 1, "k": 0.25} | sym8u / both | 178 | 3781 | -1232 | 727 | 3089 | 3780 | 2 | 203 |
| vwap | false_break | mom_40 | {"M": 1, "k": 0.0} | sym15u / both | 152 | 3221 | -789 | 1199 | 397 | 1850 | 1 | 203 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 203 |
| vwap | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 91 | 2424 | -43 | 12 | 1717 | 1574 | 1 | 203 |
| vwap | reject_native | lbrk_3_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 141 | 2247 | 589 | -748 | -179 | 1775 | 1 | 203 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 203 |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 171 | 4078 | 605 | -156 | 1901 | 3767 | 2 | 203 |
| vwap_bands | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 267 | 4022 | -815 | -2816 | 1718 | 4334 | 1 | 202 |
| vwap_bands | break_native | cusum_56 | {"n": 3, "k": 0.5} | sym15u / both | 242 | 3923 | -2077 | -681 | 2975 | 4369 | 1 | 202 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 202 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 202 |
| vwap_bands | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 270 | 3357 | -1402 | -865 | 800 | 1869 | 1 | 202 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 202 |
| vwap_bands | retest | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 238 | 4091 | -2704 | -152 | -2144 | 3461 | 2 | 202 |
| vwap_bands | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 279 | 4137 | 353 | -1853 | 636 | 4160 | 1 | 202 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym15u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 1 | 204 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 204 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 204 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 204 |
| week_month | reject | time_m_2 | {"tol": 0.5, "conf": "body"} | sym15u / both | 38 | 1814 | -158 | -245 | 711 | 1727 | 2 | 204 |
| week_month | reject_native | tick_8000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 72 | 1892 | -134 | -795 | -399 | 2132 | 2 | 204 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 204 |
| week_month | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 38 | 1687 | -215 | -1383 | 15 | 2423 | 2 | 204 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 203 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 203 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 203 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 203 |
| zones | reject | rng_14 | {"tol": 1.0, "conf": "body"} | sym30u / both | 133 | 3041 | 2935 | -1064 | 682 | 3212 | 2 | 203 |
| zones | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | sym30u / both | 134 | 2702 | 2260 | -2018 | 250 | 3460 | 2 | 203 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 203 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 203 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | kagi_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 485 | -56 | -17 | 715 | 994 | 1 | 34 |
| sd5 | break_native | kagi_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 485 | -56 | -17 | 715 | 994 | 1 | 34 |
| sdx15 | break | urenko_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 70 | 1077 | -200 | -153 | 1318 | 1345 | 1 | 34 |
| sdx15 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 303 | 3630 | -249 | -670 | -1170 | 3468 | 1 | 34 |
| sdx15 | lim_prox | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 271 | 3613 | 443 | 1635 | -503 | 3126 | 1 | 34 |
| sdx15 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 98 | 2164 | 235 | -369 | -1160 | 1645 | 1 | 34 |
| sdx15 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / both | 111 | 2275 | 39 | -418 | -673 | 3243 | 1 | 34 |
| sdx15 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 34 |
| sdx15 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 34 |
| sdx15 | retest | pnf_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 44 | 546 | -90 | -274 | 367 | 375 | 1 | 34 |
| sdx3 | break | wrenko_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 174 | 2989 | -298 | 492 | 507 | 2803 | 1 | 34 |
| sdx3 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 461 | 3840 | -653 | -1268 | -1861 | 3838 | 1 | 34 |
| sdx3 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1050 | 6224 | -119 | -224 | -2213 | 5021 | 1 | 34 |
| sdx3 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 305 | 3708 | -457 | -454 | -1839 | 2258 | 1 | 34 |
| sdx3 | rej_flow | wrenko_20 | {"d": "A", "F": 0} | plain60/60 / both | 173 | 1286 | -498 | 192 | -724 | 1986 | 1 | 34 |
| sdx3 | rej_native | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 34 |
| sdx3 | rej_zone | urenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 34 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 34 |
| sdx30 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 43 | 796 | -102 | 249 | 541 | 651 | 1 | 34 |
| sdx30 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 206 | 3133 | -150 | -817 | -949 | 1695 | 1 | 34 |
| sdx30 | lim_prox | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 232 | 3270 | -189 | -1338 | -13 | 2950 | 1 | 34 |
| sdx30 | rej | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 155 | 1478 | -177 | -1037 | -308 | 171 | 1 | 34 |
| sdx30 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / short | 44 | 980 | -54 | -29 | -875 | 983 | 1 | 34 |
| sdx30 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 34 |
| sdx30 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 34 |
| sdx5 | break | urenko_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 113 | 2472 | -146 | -590 | 1239 | 2914 | 1 | 34 |
| sdx5 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 434 | 4411 | -88 | -1705 | -1193 | 3777 | 1 | 34 |
| sdx5 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 360 | 5056 | 283 | 711 | -1448 | 2414 | 1 | 34 |
| sdx5 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 284 | 4568 | -952 | -1164 | -3346 | 3706 | 1 | 34 |
| sdx5 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 213 | 2801 | 412 | -179 | -668 | 1032 | 1 | 34 |
| sdx5 | rej_native | kagi_28 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 257 | 4053 | -521 | -922 | -442 | 6216 | 1 | 34 |
| sdx5 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 279 | 3304 | -209 | -1861 | 763 | 177 | 1 | 34 |
| sdx5 | retest | kagi_40 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / short | 93 | 1465 | -6 | -476 | -174 | 1868 | 1 | 34 |
| sdx60 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 246 | -54 | 16 | 405 | -586 | 1 | 34 |
| sdx60 | lim_mid | urenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 144 | 1330 | 181 | -523 | -342 | 1028 | 1 | 34 |
| sdx60 | lim_prox | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 87 | 1502 | -62 | -1032 | -516 | 1170 | 1 | 34 |
| sdx60 | rej | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 30 | 1580 | -20 | -174 | -290 | 2169 | 1 | 34 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 33 | 352 | -29 | 149 | -99 | 390 | 1 | 34 |
| sdx60 | rej_native | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 56 | 2048 | -3 | -244 | -270 | 2246 | 1 | 34 |
| sdx60 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 64 | 1710 | 25 | -264 | -895 | 1797 | 1 | 34 |
| sdx_renko28 | break | kagi_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 223 | 2989 | -99 | -30 | 159 | 4578 | 1 | 34 |
| sdx_renko28 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 335 | 3926 | -225 | -191 | -3870 | 3498 | 1 | 34 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 332 | 3491 | 102 | -741 | -4298 | 1272 | 1 | 34 |
| sdx_renko28 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 223 | 2070 | -289 | -772 | -816 | -946 | 1 | 34 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 105 | 2509 | -260 | -487 | -1295 | 1700 | 1 | 34 |
| sdx_renko28 | rej_native | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 290 | 3009 | -86 | -3096 | -4876 | 1290 | 1 | 34 |
| sdx_renko28 | rej_zone | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 290 | 3009 | -86 | -3096 | -4876 | 1290 | 1 | 34 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2189 | 230 | -226 | -1251 | 1966 | 1 | 34 |
| sdx_rng28 | break | mrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 803 | 5407 | 129 | 1213 | -529 | 4740 | 1 | 34 |
| sdx_rng28 | lim_mid | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 358 | 3033 | 349 | -535 | 1306 | 3345 | 1 | 34 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 34 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 180 | 4551 | 663 | 859 | -858 | 6367 | 1 | 34 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 131 | 1284 | -125 | -911 | -891 | 1041 | 1 | 34 |
| sdx_rng28 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 817 | 2929 | -775 | -407 | -1591 | 2117 | 1 | 34 |
| sdx_rng28 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 325 | 2693 | -208 | -802 | -2507 | 1921 | 1 | 34 |
| sdx_rng28 | retest | kagi_28 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 805 | 2488 | 202 | 1443 | 17 | 3924 | 1 | 34 |
| sdx_vol1100 | break | kagi_14 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 575 | 3019 | -303 | -758 | 428 | 2892 | 1 | 34 |
| sdx_vol1100 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 351 | 3043 | -308 | 140 | -2784 | 1952 | 1 | 34 |
| sdx_vol1100 | lim_prox | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 334 | 4466 | -175 | -58 | -998 | 5680 | 1 | 34 |
| sdx_vol1100 | rej | kagi_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 245 | 1728 | -252 | -1315 | -1161 | 2531 | 1 | 34 |
| sdx_vol1100 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / short | 113 | 1360 | -676 | -750 | -806 | 1037 | 1 | 34 |
| sdx_vol1100 | rej_native | kagi_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 292 | 3389 | -344 | -1220 | -2227 | 4421 | 1 | 34 |
| sdx_vol1100 | rej_zone | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 241 | 3356 | 427 | -643 | -1132 | 2743 | 1 | 34 |
| sdx_vol1100 | retest | urenko_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 273 | 2414 | 61 | -321 | 464 | 2757 | 1 | 34 |
| fib15 | break | lbrk_3_10 | {"n": 1, "k": 0.0} | sym15u / both | 357 | 3199 | -503 | 800 | 2149 | 1847 | 1 | 34 |
| fib15 | break_native | lbrk_3_10 | {"n": 1, "k": 0.0} | sym15u / both | 357 | 3199 | -503 | 800 | 2149 | 1847 | 1 | 34 |
| fib15 | false_break | urenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 305 | 3531 | -251 | 204 | 302 | 3497 | 1 | 34 |
| fib15 | false_break_native | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3386 | -101 | -338 | 505 | 2207 | 1 | 34 |
| fib15 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 244 | 2343 | -775 | -1245 | -49 | 1766 | 1 | 34 |
| fib15 | pullback_native | pnf_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 281 | 2079 | -225 | -602 | 77 | 2651 | 1 | 34 |
| fib15 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 583 | 3114 | 323 | -624 | 1153 | 3098 | 1 | 34 |
| fib15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 3684 | 770 | -1991 | 1912 | 3118 | 1 | 34 |
| fib15 | retest | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 273 | 3063 | -31 | -967 | -487 | 3108 | 1 | 34 |
| fib15 | retest_native | urenko_56 | {"M": 6, "tol": 0.5} | sym15u / both | 222 | 3088 | -193 | -359 | 911 | 2239 | 1 | 34 |
| fib5 | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 780 | 3710 | 255 | 1241 | -1391 | 4410 | 1 | 34 |
| fib5 | break_native | urenko_80 | {"n": 1, "k": 0.0} | plain60/60 / both | 496 | 3121 | -59 | 232 | 1286 | 2488 | 1 | 34 |
| fib5 | false_break | pnf_14 | {"M": 2, "k": 0.5} | sym15u / both | 312 | 2831 | -211 | 899 | -3174 | 3833 | 1 | 34 |
| fib5 | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 298 | 3381 | 57 | 598 | -2618 | 1711 | 1 | 34 |
| fib5 | pullback | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 3450 | -194 | -957 | 412 | 4059 | 1 | 34 |
| fib5 | pullback_native | kagi_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 613 | 3577 | -99 | 252 | -1371 | 4557 | 1 | 34 |
| fib5 | reject | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 248 | 3634 | 32 | -710 | -768 | 4336 | 1 | 34 |
| fib5 | reject_native | pnf_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 3481 | 593 | -1004 | -1778 | 5364 | 1 | 34 |
| fib5 | retest | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5432 | 117 | -762 | -4567 | 7004 | 1 | 34 |
| fib5 | retest_native | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5432 | 117 | -762 | -4567 | 7004 | 1 | 34 |
| fib60 | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 263 | 4046 | -15 | -506 | 1369 | 4306 | 1 | 34 |
| fib60 | break_native | frenko_40 | {"n": 3, "k": 0.5} | plain60/60 / both | 502 | 3264 | -219 | 856 | 1257 | 3182 | 1 | 34 |
| fib60 | false_break | lbrk_3_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 430 | 2589 | -24 | 1523 | -232 | 2171 | 1 | 34 |
| fib60 | false_break_native | lbrk_3_40 | {"M": 3, "k": 0.5} | plain60/60 / both | 415 | 2559 | -102 | 1257 | -523 | 1966 | 1 | 34 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 133 | 2500 | 277 | -321 | -1857 | 3041 | 1 | 34 |
| fib60 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 156 | 2403 | 331 | -240 | -1482 | 3044 | 1 | 34 |
| fib60 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 254 | 3600 | 321 | -1524 | -787 | 4078 | 1 | 34 |
| fib60 | reject_native | urenko_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 598 | 3269 | 101 | -14 | 853 | 3533 | 1 | 34 |
| fib60 | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 303 | 2269 | 379 | -1909 | -1529 | 2945 | 1 | 34 |
| fib60 | retest_native | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 308 | 2705 | 324 | -1493 | -867 | 2814 | 1 | 34 |
| fibr_dev | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 492 | 1108 | 1598 | 3481 | 1 | 34 |
| fibr_dev | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 515 | 1108 | 1598 | 3481 | 1 | 34 |
| fibr_dev | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 316 | 3799 | 772 | 931 | 1745 | 3779 | 1 | 34 |
| fibr_dev | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3556 | 1165 | 401 | 1540 | 3473 | 1 | 34 |
| fibr_dev | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 268 | 3144 | -189 | 873 | -2406 | 3760 | 1 | 34 |
| fibr_dev | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 4083 | -588 | 684 | -1434 | 4699 | 1 | 34 |
| fibr_dev | retest | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 34 |
| fibr_dev | retest_native | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 34 |
| fibr_ib | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 34 |
| fibr_ib | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 34 |
| fibr_ib | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / long | 31 | 987 | 109 | 245 | 994 | 2440 | 1 | 34 |
| fibr_ib | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 218 | 954 | 2426 | 1 | 34 |
| fibr_ib | reject | pnf_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 32 | 624 | 386 | 146 | -104 | 606 | 1 | 34 |
| fibr_ib | reject_native | pnf_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | 460 | -101 | 173 | 929 | 1 | 34 |
| fibr_ib | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 1139 | 116 | -501 | 309 | 1475 | 1 | 34 |
| fibr_ib | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 60 | 1416 | 2 | -1461 | -161 | 2126 | 1 | 34 |
| fibr_on | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 34 |
| fibr_on | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 34 |
| fibr_on | false_break | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 31 | 1342 | 57 | 761 | 588 | 2157 | 1 | 34 |
| fibr_on | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 43 | 1558 | 176 | 575 | 928 | 2229 | 1 | 34 |
| fibr_on | reject | kagi_112 | {"tol": 0.0, "conf": "close"} | sym15u / both | 39 | 769 | 6 | 260 | 62 | 989 | 1 | 34 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 1 | 34 |
| fibr_on | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 37 | 1166 | -61 | -3 | 830 | 1123 | 1 | 34 |
| fibr_on | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 50 | 1220 | -2 | 140 | 639 | 1292 | 1 | 34 |
| fibr_or | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 34 |
| fibr_or | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 34 |
| fibr_or | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 34 |
| fibr_or | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 34 |
| fibr_or | reject | pnf_40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 34 | 319 | 180 | -2 | -170 | 578 | 1 | 34 |
| fibr_or | reject_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / short | 36 | 808 | 243 | -645 | -131 | 1067 | 1 | 34 |
| fibr_or | retest | urenko_80 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1143 | 260 | -956 | -170 | 1606 | 1 | 34 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 1 | 34 |
| fibr_pd | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 34 |
| fibr_pd | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 34 |
| fibr_pd | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 678 | 3579 | -1005 | -279 | 981 | 5723 | 1 | 34 |
| fibr_pd | false_break_native | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 666 | 3464 | -1047 | -220 | 995 | 5358 | 1 | 34 |
| fibr_pd | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 349 | 2746 | -87 | -674 | -1595 | 3667 | 1 | 34 |
| fibr_pd | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 342 | 2899 | 228 | -466 | 1300 | 2291 | 1 | 34 |
| fibr_pd | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / both | 603 | 2661 | 78 | 584 | 477 | 2260 | 1 | 34 |
| fibr_pd | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 686 | 3100 | 305 | 253 | 787 | 3272 | 1 | 34 |
| piv_cama | break | mrenko_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 734 | 2847 | -237 | -199 | -769 | 3696 | 1 | 34 |
| piv_cama | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 306 | 3386 | 269 | 1492 | 959 | 3771 | 1 | 34 |
| piv_cama | false_break | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 837 | 2755 | -1113 | -1285 | 50 | 4031 | 1 | 34 |
| piv_cama | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 832 | 3200 | -1113 | -1440 | 84 | 4151 | 1 | 34 |
| piv_cama | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 309 | 3116 | -104 | -1966 | -1113 | 2737 | 1 | 34 |
| piv_cama | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 334 | 3432 | -1039 | -1266 | 885 | 3417 | 1 | 34 |
| piv_cama | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 787 | 2950 | -169 | -864 | 823 | 3736 | 1 | 34 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 1 | 34 |
| piv_floor | break | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 34 |
| piv_floor | break_native | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 34 |
| piv_floor | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 552 | 3654 | -727 | -863 | 251 | 3755 | 1 | 34 |
| piv_floor | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 553 | 3592 | -577 | -783 | 419 | 3557 | 1 | 34 |
| piv_floor | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 259 | 2195 | -719 | -1237 | -497 | 3369 | 1 | 34 |
| piv_floor | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 222 | 2515 | 703 | -945 | -1135 | 3210 | 1 | 34 |
| piv_floor | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 468 | 3194 | -7 | 722 | -1698 | 3884 | 1 | 34 |
| piv_floor | retest_native | mrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 2992 | 134 | -1048 | 1326 | 4059 | 1 | 34 |
| piv_wf | break | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 34 |
| piv_wf | break_native | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 34 |
| piv_wf | false_break | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 291 | 2328 | -761 | -1299 | 763 | 3828 | 1 | 34 |
| piv_wf | false_break_native | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 288 | 2691 | -648 | -1103 | 567 | 3937 | 1 | 34 |
| piv_wf | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 580 | 2409 | -138 | -114 | -2979 | 874 | 1 | 34 |
| piv_wf | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 294 | 3050 | -355 | -1518 | -2651 | 4373 | 1 | 34 |
| piv_wf | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 265 | 3002 | -306 | -16 | -2883 | 4150 | 1 | 34 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 1 | 34 |
| swcluster | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1027 | -344 | -315 | -623 | 734 | 1 | 34 |
| swcluster | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1024 | -227 | -349 | -670 | 879 | 1 | 34 |
| swcluster | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 34 |
| swcluster | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 34 |
| swcluster | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 50 | 591 | -154 | -551 | -336 | 712 | 1 | 34 |
| swcluster | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1097 | 102 | -253 | -33 | 902 | 1 | 34 |
| swcluster | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 51 | 972 | -130 | 69 | 114 | 2028 | 1 | 34 |
| swcluster | retest_native | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 52 | 973 | -319 | 31 | 1182 | 1353 | 1 | 34 |
| swsr15 | break | urenko_28 | {"n": 3, "k": 0.5} | plain60/60 / both | 607 | 2835 | -125 | 665 | 1504 | 4520 | 1 | 34 |
| swsr15 | break_native | frenko_40 | {"n": 1, "k": 0.0} | plain60/60 / both | 532 | 2391 | -295 | 324 | -1522 | 2685 | 1 | 34 |
| swsr15 | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 283 | 2324 | -223 | -60 | -629 | 1560 | 1 | 34 |
| swsr15 | false_break_native | kagi_20 | {"M": 2, "k": 0.5} | sym15u / both | 322 | 2961 | 743 | -10 | -136 | 4162 | 1 | 34 |
| swsr15 | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 177 | 2218 | 174 | -27 | -468 | 3125 | 1 | 34 |
| swsr15 | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 660 | 2650 | -1013 | 464 | -381 | 3861 | 1 | 34 |
| swsr15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 34 |
| swsr15 | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 34 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 306 | 3427 | -11 | 1352 | -1241 | 2548 | 1 | 34 |
| swsr5 | break_native | wrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 789 | 3514 | 80 | 1736 | 1316 | 4658 | 1 | 34 |
| swsr5 | false_break | kagi_56 | {"M": 3, "k": 0.5} | plain60/60 / both | 737 | 2683 | 222 | 1358 | 730 | 2451 | 1 | 34 |
| swsr5 | false_break_native | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 272 | 3016 | 270 | 578 | -45 | 3124 | 1 | 34 |
| swsr5 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 228 | 4159 | 82 | 315 | 42 | 4336 | 1 | 34 |
| swsr5 | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 899 | 3040 | 121 | -370 | 48 | 3663 | 1 | 34 |
| swsr5 | retest | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 261 | 4292 | -147 | -323 | -3129 | 3722 | 1 | 34 |
| swsr5 | retest_native | urenko_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 592 | 3645 | -130 | 1122 | 406 | 2944 | 1 | 34 |
| swsr60 | break | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 34 |
| swsr60 | break_native | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 34 |
| swsr60 | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 34 |
| swsr60 | false_break_native | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 34 |
| swsr60 | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / short | 63 | 901 | 155 | -797 | 359 | 831 | 1 | 34 |
| swsr60 | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 1613 | 196 | 417 | -574 | 1076 | 1 | 34 |
| swsr60 | retest | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 167 | 2036 | -8 | -105 | -593 | 2733 | 1 | 34 |
| swsr60 | retest_native | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 254 | 2089 | 120 | -274 | -719 | 2097 | 1 | 34 |
| stack | break | wrenko_14 | {"k": 3, "cw": 1.0} | sym15u / both | 163 | 3697 | -1113 | -75 | 53 | 4771 | 1 | 204 |
| stack | break_native | vol_1100 | {"k": 2, "cw": 2.0} | sym8u / both | 259 | 4020 | -769 | 291 | 1001 | 4305 | 2 | 204 |
| stack | reject | tick_300 | {"k": 2, "cw": 2.0} | asym10u/20u / both | 186 | 2906 | 61 | 648 | 73 | 1352 | 2 | 204 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | sym30u / both | 181 | 2425 | 449 | -1688 | -402 | 2186 | 2 | 204 |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 791 | 86 | 772 | 1607 | 2 | 203 |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 841 | 86 | 772 | 1607 | 2 | 203 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 203 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 203 |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 1480 | -474 | -213 | -350 | 2822 | 1 | 203 |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1443 | 732 | 638 | 74 | 699 | 1 | 203 |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 899 | -1465 | 616 | 147 | 1417 | 1 | 203 |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 821 | -381 | -305 | -21 | 226 | 1 | 203 |
| book_walls_loose | break | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 461 | 137 | 581 | 4298 | 2 | 204 |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 411 | 137 | 581 | 4298 | 2 | 204 |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 1856 | -61 | -317 | 372 | 986 | 1 | 204 |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 62 | 1806 | 153 | -209 | 562 | 1133 | 1 | 204 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 329 | 3303 | -618 | -483 | -2918 | 3949 | 1 | 204 |
| book_walls_loose | reject_native | tm45 | {"tol": 0.5, "conf": "body"} | sym30u / both | 209 | 3172 | 252 | -1284 | -1029 | 2939 | 2 | 204 |
| book_walls_loose | retest | tm20 | {"M": 6, "tol": 0.5} | sym15u / both | 353 | 2344 | -963 | -496 | 59 | 3790 | 1 | 204 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 438 | 1781 | -951 | -565 | -1164 | 2912 | 1 | 204 |
| channel | break | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 34 |
| channel | break_native | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 34 |
| channel | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 34 |
| channel | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 34 |
| channel | reject | frenko_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 149 | 2239 | -137 | -627 | -253 | 2244 | 1 | 34 |
| channel | reject_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 690 | 2704 | -28 | 101 | 2034 | 3732 | 1 | 34 |
| channel | retest | kagi_56 | {"M": 3, "tol": 0.0} | plain60/60 / both | 478 | 3220 | 669 | -520 | 191 | 3415 | 1 | 34 |
| channel | retest_native | kagi_56 | {"M": 3, "tol": 0.0} | plain60/60 / both | 478 | 3220 | 669 | -520 | 191 | 3415 | 1 | 34 |
| fvg15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 232 | 3843 | -251 | 495 | 933 | 3840 | 1 | 34 |
| fvg15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 3696 | -362 | 650 | 1002 | 4034 | 1 | 34 |
| fvg15 | false_break | urenko_40 | {"M": 1, "k": 0.0} | sym15u / both | 159 | 3689 | -171 | -177 | 1864 | 3470 | 1 | 34 |
| fvg15 | false_break_native | mrenko_20 | {"M": 2, "k": 0.5} | sym15u / both | 180 | 3960 | 34 | 246 | 1170 | 3341 | 1 | 34 |
| fvg15 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 137 | 1390 | -795 | -80 | 724 | 486 | 1 | 34 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 192 | 3238 | -531 | 176 | 1230 | 3572 | 1 | 34 |
| fvg15 | retest | wrenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 127 | 2561 | -576 | 357 | 459 | 1091 | 1 | 34 |
| fvg15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 186 | 3378 | -38 | 97 | -280 | 2780 | 1 | 34 |
| fvg5 | break | lbrk_3_10 | {"n": 3, "k": 0.5} | plain60/60 / both | 508 | 3062 | -156 | 942 | 947 | 4922 | 1 | 34 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 269 | 3021 | -697 | 476 | 1207 | 4798 | 1 | 34 |
| fvg5 | false_break | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 333 | 2970 | -57 | -288 | -1769 | 3049 | 1 | 34 |
| fvg5 | false_break_native | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 332 | 3092 | -31 | -408 | -1857 | 3270 | 1 | 34 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 34 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 34 |
| fvg5 | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3156 | -584 | -548 | -2079 | 4493 | 1 | 34 |
| fvg5 | retest_native | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 270 | 3569 | -603 | -322 | -233 | 4778 | 1 | 34 |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 140 | 2941 | 712 | 954 | 90 | 2534 | 2 | 204 |
| gaps | break_native | dib_400 | {"n": 2, "k": 0.25} | sym15u / both | 181 | 3181 | 83 | 121 | -102 | 2510 | 1 | 204 |
| gaps | false_break | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 435 | 3838 | -315 | -223 | 999 | 4659 | 1 | 204 |
| gaps | false_break_native | kagi_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 435 | 3828 | -358 | 225 | 1018 | 4408 | 1 | 204 |
| gaps | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2273 | 361 | 369 | -613 | 1685 | 1 | 204 |
| gaps | reject_native | renko_20 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 89 | 2688 | -72 | -741 | 685 | 2799 | 2 | 204 |
| gaps | retest | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 2373 | -138 | 438 | 1115 | 1777 | 1 | 204 |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2887 | -129 | 409 | 967 | 2191 | 1 | 204 |
| mmove | break | urenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 376 | 2830 | 129 | 164 | 668 | 3190 | 1 | 34 |
| mmove | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 372 | 2754 | 256 | 494 | 1132 | 2119 | 1 | 34 |
| mmove | false_break | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 664 | 3727 | -662 | -437 | 695 | 2685 | 1 | 34 |
| mmove | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 664 | 3727 | -665 | -437 | 695 | 2685 | 1 | 34 |
| mmove | reject | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 89 | 2172 | -113 | 1317 | 220 | 2986 | 1 | 34 |
| mmove | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 494 | 2494 | -127 | -205 | -307 | 3948 | 1 | 34 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 270 | 4009 | -265 | 707 | 166 | 4154 | 1 | 34 |
| mmove | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 3501 | 153 | -509 | -661 | 2363 | 1 | 34 |
| ob15 | break | mrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 87 | 1145 | -110 | 211 | 463 | 1243 | 1 | 34 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 1 | 34 |
| ob15 | false_break | mrenko_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 95 | 527 | 393 | 352 | 362 | 815 | 1 | 34 |
| ob15 | false_break_native | mrenko_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 95 | 527 | 409 | 357 | 362 | 815 | 1 | 34 |
| ob15 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 62 | 791 | -118 | 315 | -442 | 1181 | 1 | 34 |
| ob15 | reject_native | lbrk_3_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 57 | 1375 | 108 | 245 | -15 | 1584 | 1 | 34 |
| ob15 | retest | mrenko_10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 | 729 | 168 | 295 | -73 | 1126 | 1 | 34 |
| ob15 | retest_native | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 79 | 942 | 14 | -160 | 421 | 1025 | 1 | 34 |
| ob5 | break | kagi_10 | {"n": 2, "k": 0.25} | sym15u / both | 145 | 1926 | -810 | -333 | 600 | 2773 | 1 | 34 |
| ob5 | break_native | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 118 | 1866 | 238 | 603 | 530 | 2260 | 1 | 34 |
| ob5 | false_break | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 39 | 1216 | 28 | 406 | 1050 | 1397 | 1 | 34 |
| ob5 | false_break_native | urenko_40 | {"M": 3, "k": 0.5} | sym15u / both | 115 | 1109 | -143 | 486 | 1724 | 1968 | 1 | 34 |
| ob5 | reject | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 81 | 2035 | 288 | -683 | -526 | 2219 | 1 | 34 |
| ob5 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 330 | 2437 | -94 | -408 | 247 | 3278 | 1 | 34 |
| ob5 | retest | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 114 | 2116 | -453 | -364 | 1873 | 1885 | 1 | 34 |
| ob5 | retest_native | mrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1697 | 111 | -230 | 324 | 2333 | 1 | 34 |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 203 |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 53 | 1298 | 117 | 673 | 306 | 1466 | 2 | 203 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 203 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 203 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 203 |
| open_range | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 1841 | -107 | -871 | 61 | 1790 | 1 | 203 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 203 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 203 |
| opens | break | tick_800 | {"n": 1, "k": 0.5} | asym10u/20u / both | 187 | 3057 | -72 | -628 | 803 | 3795 | 2 | 205 |
| opens | break_native | renko_10 | {"n": 2, "k": 0.25} | asym20u/10u / both | 287 | 3101 | -120 | -401 | 418 | 3462 | 2 | 205 |
| opens | false_break | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 205 |
| opens | false_break_native | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 205 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 205 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 205 |
| opens | retest | tm10 | {"M": 3, "tol": 0.5} | sym15u / both | 435 | 3568 | -310 | -114 | -1092 | 4604 | 2 | 205 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 205 |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 205 |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 205 |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 2 | 205 |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 2 | 205 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 205 |
| prior_day | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 205 |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 2 | 205 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 205 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 204 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 204 |
| profile_nodes | false_break | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 556 | 3365 | -801 | 527 | 801 | 3841 | 2 | 204 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 204 |
| profile_nodes | reject | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 217 | 3451 | -794 | -877 | -1862 | 3671 | 2 | 204 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 204 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 1 | 204 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 295 | 4808 | -512 | 139 | 1484 | 5809 | 1 | 204 |
| profile_va | break | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 3734 | 98 | -1260 | -135 | 2075 | 1 | 205 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 205 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 1 | 205 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 1 | 205 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 205 |
| profile_va | reject_native | rng_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 523 | 3959 | 232 | -523 | -699 | 2840 | 2 | 205 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 205 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 1 | 205 |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2 | 205 |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 2 | 205 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 205 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 205 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 205 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 205 |
| round | retest | vsess_50 | {"M": 3, "tol": 0.0} | plain60/60 / both | 480 | 4161 | -390 | -850 | -175 | 4245 | 1 | 205 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 1 | 205 |
| session_hl | break | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 203 |
| session_hl | break_native | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 203 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym15u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 1 | 203 |
| session_hl | false_break_native | mom_112 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1310 | 345 | -28 | -555 | 1077 | 1 | 203 |
| session_hl | reject | swing_pct_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 31 | 966 | 156 | 215 | 82 | 717 | 1 | 203 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 203 |
| session_hl | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 930 | 394 | -159 | 104 | 1490 | 1 | 203 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 1 | 203 |
| trendline | break | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 281 | 4036 | 458 | 302 | -1947 | 3931 | 1 | 34 |
| trendline | break_native | frenko_40 | {"n": 2, "k": 0.25} | sym15u / both | 260 | 2983 | 184 | 307 | -1840 | 3551 | 1 | 34 |
| trendline | false_break | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 2652 | 5 | 374 | -456 | 3314 | 1 | 34 |
| trendline | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 290 | 2491 | 555 | -381 | 1308 | 960 | 1 | 34 |
| trendline | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 249 | 2489 | -856 | 1637 | -467 | 1528 | 1 | 34 |
| trendline | reject_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 3233 | -304 | 1786 | -548 | 2457 | 1 | 34 |
| trendline | retest | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 276 | 2659 | 77 | -1818 | -579 | 1610 | 1 | 34 |
| trendline | retest_native | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 248 | 2648 | -109 | -215 | 1694 | 3705 | 1 | 34 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 204 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 204 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 204 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 204 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 204 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 1 | 204 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 204 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 204 |
| uw_ndx | break | renko_14 | {"n": 2, "k": 0.5} | sym8u / both | 331 | 2910 | 0 | -114 | 269 | 2774 | 2 | 204 |
| uw_ndx | break_native | renko_28 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 2821 | 0 | 832 | 1783 | 4375 | 2 | 204 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 204 |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 296 | 2751 | 0 | 605 | 329 | 2931 | 2 | 204 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 204 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 204 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 204 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 204 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 204 |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 444 | 3333 | 0 | 825 | 798 | 2619 | 2 | 204 |
| uw_qqq | false_break | cusum_112 | {"M": 1, "k": 0.0} | sym15u / both | 189 | 2553 | 0 | -215 | 1193 | 2621 | 1 | 204 |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 228 | 2553 | 0 | -518 | 1669 | 3080 | 2 | 204 |
| uw_qqq | reject | rng_28 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 487 | 3819 | 0 | 532 | -3 | 3522 | 2 | 204 |
| uw_qqq | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 585 | 4310 | 0 | 145 | -321 | 3898 | 2 | 204 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 204 |
| uw_qqq | retest_native | renko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 252 | 2711 | 0 | -192 | 815 | 3673 | 2 | 204 |
| vwap | break | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 204 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 204 |
| vwap | false_break | pasl_10 | {"M": 1, "k": 0.0} | sym15u / both | 272 | 3707 | 24 | -1009 | 1272 | 5049 | 1 | 204 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 204 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 204 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 204 |
| vwap | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym30u / both | 244 | 3984 | 745 | -933 | 4153 | 6617 | 2 | 204 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 204 |
| vwap_bands | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 618 | 4055 | 470 | -88 | 753 | 4340 | 1 | 203 |
| vwap_bands | break_native | time_m_2 | {"n": 2, "k": 0.25} | sym15u / both | 309 | 4019 | -106 | -2428 | -2221 | 2246 | 1 | 203 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 203 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 203 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 203 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 203 |
| vwap_bands | retest | dib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 483 | 3490 | -310 | -978 | -792 | 2632 | 1 | 203 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 203 |
| week_month | break | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 44 | 1289 | -193 | -513 | -213 | 813 | 2 | 205 |
| week_month | break_native | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 44 | 1289 | -193 | -513 | -213 | 813 | 2 | 205 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 205 |
| week_month | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 53 | 1816 | -233 | -4 | 426 | 2452 | 1 | 205 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 205 |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | 1233 | -161 | 407 | -240 | 443 | 1 | 205 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 205 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 205 |
| zones | break | rng_40 | {"n": 1, "k": 0.5} | sym8u / both | 199 | 3211 | 33 | 78 | 580 | 2604 | 2 | 204 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 204 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 204 |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 177 | 2863 | -154 | 660 | -299 | 2423 | 2 | 204 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 196 | 3254 | -73 | -1065 | -502 | 3105 | 1 | 204 |
| zones | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 278 | 3157 | -1008 | -1664 | -1608 | 2818 | 2 | 204 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 204 |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 161 | 2948 | -119 | -238 | 150 | 2390 | 2 | 204 |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 12240 of 14280 (modules x 476 bar rows); pass-1 result files written in the last hour: 405 (all modules); ETA for these at that rate if they were alone: 30.2 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

