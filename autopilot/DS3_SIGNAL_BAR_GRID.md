# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1,randd8a,randd8ax,randd8b,randd8bx): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-19 18:42Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 50284 | 400 | 0.000 | -0.63 / -0.61 / -0.62 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand10 | 427 | 400 | 0.000 | -0.65 / -0.58 / -0.58 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand11 | 427 | 400 | 0.000 | -0.65 / -0.57 / -0.57 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand12 | 421 | 400 | 0.000 | -0.65 / -0.58 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand13 | 316 | 316 | 0.000 | -0.64 / -0.58 / -0.60 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand14 | 285 | 285 | 0.000 | -0.64 / -0.60 / -0.59 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand15 | 285 | 285 | 0.000 | -0.63 / -0.61 / -0.60 / -0.91 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand16 | 285 | 285 | 0.000 | -0.66 / -0.58 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand17 | 284 | 284 | 0.000 | -0.64 / -0.58 / -0.58 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand18 | 284 | 284 | 0.000 | -0.66 / -0.58 / -0.60 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand19 | 368 | 368 | 0.000 | -0.66 / -0.62 / -0.62 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand2 | 50377 | 400 | 0.000 | -0.67 / -0.63 / -0.64 / -0.92 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand20 | 495 | 400 | 0.000 | -0.66 / -0.61 / -0.61 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand21 | 103 | 103 | 0.000 | -0.65 / -0.62 / -0.61 / -0.92 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand22 | 102 | 102 | 0.000 | -0.65 / -0.61 / -0.61 / -0.94 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand23 | 102 | 102 | 0.000 | -0.66 / -0.60 / -0.59 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand24 | 103 | 103 | 0.000 | -0.63 / -0.62 / -0.62 / -0.93 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand25 | 102 | 102 | 0.000 | -0.68 / -0.60 / -0.62 / -0.95 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand26 | 2 | 2 | 0.000 | -0.35 / -0.30 / -0.63 / -0.63 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand27 | 2 | 2 | 0.000 | -0.93 / -0.57 / -0.62 / -0.64 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand28 | 2 | 2 | 0.000 | -0.53 / -0.51 / -1.04 / -0.84 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand29 | 2 | 2 | 0.000 | -0.47 / -0.77 / -0.68 / -0.71 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand3 | 5602 | 400 | 0.000 | -0.67 / -0.60 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand30 | 2 | 2 | 0.000 | -0.85 / -0.67 / -0.71 / -0.70 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand4 | 5534 | 400 | 0.000 | -0.70 / -0.61 / -0.62 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 5392 | 400 | 0.000 | -0.68 / -0.61 / -0.62 / -0.95 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand6 | 428 | 400 | 0.000 | -0.66 / -0.58 / -0.58 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand7 | 427 | 400 | 0.000 | -0.65 / -0.58 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand8 | 427 | 400 | 0.000 | -0.64 / -0.59 / -0.59 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand9 | 427 | 400 | 0.000 | -0.66 / -0.58 / -0.57 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-19 18:42Z):** result files per tag {"acctt1": 4, "acctt2": 1, "d8real": 2, "d8realx": 622, "p1audit": 436, "p1audit2": 436, "p1det": 3, "p1flow_absorbx": 213, "p1flow_bookx": 213, "p1flow_deltax": 214, "p1flow_speedx": 212, "p1flow_wallx": 212, "p1gridops_test": 0, "p1probe": 2, "p1rand1": 52194, "p1rand10": 427, "p1rand11": 427, "p1rand12": 421, "p1rand13": 316, "p1rand14": 285, "p1rand15": 285, "p1rand16": 285, "p1rand17": 285, "p1rand18": 284, "p1rand19": 368, "p1rand2": 52069, "p1rand20": 495, "p1rand21": 103, "p1rand22": 102, "p1rand23": 103, "p1rand24": 103, "p1rand25": 102, "p1rand26": 2, "p1rand27": 2, "p1rand28": 2, "p1rand29": 2, "p1rand3": 5854, "p1rand30": 2, "p1rand4": 5733, "p1rand5": 5571, "p1rand6": 428, "p1rand7": 427, "p1rand8": 427, "p1rand9": 427, "p1real": 69313, "p1realx": 4124, "p1stale": 67, "p1stamptest": 1, "rand1": 0, "randd8a": 0, "randd8ax": 0, "randd8b": 0, "randd8bx": 0, "real": 1654}; bar families present as columns: ACTIVITY, ACTIVITY(book), ANCHORED, COMPOSITE, FOOTPRINT, INFORMATION, INFORMATION(book), PRICE, PROFILE, SESSION-RELATIVE, SMOOTHING, TIME, UNKNOWN; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 0, "London": 0, "NYAM": 0, "NYPM": 0}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-19 18:42Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"acctt1": 4, "acctt2": 1, "d8real": 2, "d8realx": 622, "p1audit": 436, "p1audit2": 436, "p1det": 3, "p1flow_absorbx": 213, "p1flow_bookx": 213, "p1flow_deltax": 214, "p1flow_speedx": 212, "p1flow_wallx": 212, "p1gridops_test": 0, "p1probe": 2, "p1rand1": 52194, "p1rand10": 427, "p1rand11": 427, "p1rand12": 421, "p1rand13": 316, "p1rand14": 285, "p1rand15": 285, "p1rand16": 285, "p1rand17": 285, "p1rand18": 284, "p1rand19": 368, "p1rand2": 52069, "p1rand20": 495, "p1rand21": 103, "p1rand22": 102, "p1rand23": 103, "p1rand24": 103, "p1rand25": 102, "p1rand26": 2, "p1rand27": 2, "p1rand28": 2, "p1rand29": 2, "p1rand3": 5854, "p1rand30": 2, "p1rand4": 5733, "p1rand5": 5571, "p1rand6": 428, "p1rand7": 427, "p1rand8": 427, "p1rand9": 427, "p1real": 69313, "p1realx": 4124, "p1stale": 67, "p1stamptest": 1, "rand1": 0, "randd8a": 0, "randd8ax": 0, "randd8b": 0, "randd8bx": 0, "real": 1654}; loop status: 2026-11-19T18:42Z rows=327 mods=146 todo=17 running=0. 
Cells scored per session: {"Asia": 9802692, "London": 10795230, "NYAM": 11790825, "NYPM": 11808727}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -9.5 | -0.004 | 831.9 | 0.48 | -18.5 | -11.8 |  |  |  |  | -5.1 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -19.1 | -0.013 | 1333.0 | 0.47 | -18.5 | -11.8 |  |  |  |  | -7.5 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | -27.4 [no null yet] | -29.8 [no null yet] | 3.9 [no null yet] | -12.5 [no null yet] | -12.0 [no null yet] | -18.7 [no null yet] | -21.3 [no null yet] | -37.9 [no null yet] | n/a (no signals by construction) | -13.5 [no null yet] | -3.9 [no null yet] | -15.8 [no null yet] | -10.5 [no null yet] |
| bands (native) | -37.6 [no null yet] | 1.4 [no null yet] | 16.0 [no null yet] | -12.1 [no null yet] | -9.9 [no null yet] | -15.1 [no null yet] | -9.3 [no null yet] | -24.7 [no null yet] | n/a (no signals by construction) | -19.1 [no null yet] | -21.2 [no null yet] | -9.1 [no null yet] | -13.1 [no null yet] |
| barnative | -27.5 [no null yet] | -1.3 [no null yet] | -4.8 [no null yet] | 7.2 [no null yet] | 0.9 [no null yet] | -3.2 [no null yet] | -20.3 [no null yet] | -1.5 [no null yet] | 6.0 [no null yet] | -8.2 [no null yet] | -30.3 [no null yet] | -12.0 [no null yet] | -20.8 [no null yet] |
| book | -4.1 [no null yet] | -26.6 [no null yet] | n/a (no signals by construction) | -22.6 [no null yet] | n/a (no signals by construction) | -28.3 [no null yet] | -29.4 [no null yet] | 19.6 [no null yet] | n/a (no signals by construction) | 17.8 [no null yet] | -29.0 [no null yet] | -12.6 [no null yet] | -19.5 [no null yet] |
| book (native) | -8.7 [no null yet] | -20.9 [no null yet] | n/a (no signals by construction) | -6.8 [no null yet] | n/a (no signals by construction) | -9.3 [no null yet] | -6.1 [no null yet] | -9.5 [no null yet] | n/a (no signals by construction) | -8.1 [no null yet] | -5.9 [no null yet] | -9.4 [no null yet] | -6.4 [no null yet] |
| confluence | 3.5 [no null yet] | -21.9 [no null yet] | -3.9 [no null yet] | -33.6 [no null yet] | -16.1 [no null yet] | -2.6 [no null yet] | -6.3 [no null yet] | -29.4 [no null yet] | -4.5 [no null yet] | -4.0 [no null yet] | -27.6 [no null yet] | 6.1 [no null yet] | -26.5 [no null yet] |
| levels | -13.9 [no null yet] | -16.2 [no null yet] | -7.3 [no null yet] | -0.3 [no null yet] | -22.3 [no null yet] | 2.2 [no null yet] | -7.8 [no null yet] | 37.6 [no null yet] | -6.4 [no null yet] | -6.3 [no null yet] | -13.1 [no null yet] | 2.4 [no null yet] | -26.5 [no null yet] |
| levels (native) | -21.8 [no null yet] | -33.0 [no null yet] | 0.5 [no null yet] | -15.6 [no null yet] | 17.9 [no null yet] | -30.4 [no null yet] | -34.5 [no null yet] | 13.3 [no null yet] | -24.8 [no null yet] | -34.8 [no null yet] | -2.8 [no null yet] | 14.3 [no null yet] | 1.1 [no null yet] |
| live | -5.7 [no null yet] | -44.6 [no null yet] | -1.1 [no null yet] | -38.7 [no null yet] | -11.4 [no null yet] | -6.3 [no null yet] | -29.8 [no null yet] | -9.1 [no null yet] | n/a (no signals by construction) | -25.4 [no null yet] | -7.5 [no null yet] | 8.1 [no null yet] | 2.9 [no null yet] |
| manual | -13.3 [no null yet] | -3.5 [no null yet] | -16.6 [no null yet] | -33.1 [no null yet] | -35.7 [no null yet] | 16.5 [no null yet] | -9.1 [no null yet] | -19.7 [no null yet] | 0.3 [no null yet] | -7.3 [no null yet] | -7.2 [no null yet] | -18.2 [no null yet] | -11.2 [no null yet] |
| manual (native) | 3.1 [no null yet] | 0.9 [no null yet] | 0.0 [no null yet] | -3.8 [no null yet] | -10.8 [no null yet] | -1.0 [no null yet] | 16.4 [no null yet] | -14.5 [no null yet] | n/a (no signals by construction) | 4.8 [no null yet] | 1.6 [no null yet] | -21.2 [no null yet] | -28.9 [no null yet] |
| momentum | -6.1 [no null yet] | -1.0 [no null yet] | 0.1 [no null yet] | 2.6 [no null yet] | 0.4 [no null yet] | -4.1 [no null yet] | -7.3 [no null yet] | 6.8 [no null yet] | 0.5 [no null yet] | -22.3 [no null yet] | 10.7 [no null yet] | -26.5 [no null yet] | 19.9 [no null yet] |
| momentum (native) | -20.0 [no null yet] | 5.4 [no null yet] | -20.6 [no null yet] | -12.6 [no null yet] | 6.0 [no null yet] | -28.1 [no null yet] | -1.6 [no null yet] | -6.0 [no null yet] | n/a (no signals by construction) | 11.6 [no null yet] | -3.7 [no null yet] | -15.1 [no null yet] | 9.2 [no null yet] |
| pullback | -22.3 [no null yet] | -5.4 [no null yet] | 4.9 [no null yet] | 4.1 [no null yet] | -23.4 [no null yet] | 4.9 [no null yet] | -8.8 [no null yet] | 10.1 [no null yet] | -0.4 [no null yet] | -31.7 [no null yet] | -22.7 [no null yet] | -4.2 [no null yet] | -9.7 [no null yet] |
| pullback (native) | -13.5 [no null yet] | -14.7 [no null yet] | -1.5 [no null yet] | 16.5 [no null yet] | -14.0 [no null yet] | 2.8 [no null yet] | 3.1 [no null yet] | -9.6 [no null yet] | n/a (no signals by construction) | -5.9 [no null yet] | 6.9 [no null yet] | -29.7 [no null yet] | -2.4 [no null yet] |
| structure | -24.4 [no null yet] | -22.8 [no null yet] | -11.1 [no null yet] | 1.5 [no null yet] | -24.6 [no null yet] | -29.6 [no null yet] | -17.7 [no null yet] | -35.1 [no null yet] | -1.0 [no null yet] | -4.6 [no null yet] | 5.3 [no null yet] | 1.8 [no null yet] | 1.4 [no null yet] |
| structure (native) | -20.9 [no null yet] | 28.1 [no null yet] | n/a (no signals by construction) | 2.2 [no null yet] | 25.3 [no null yet] | -40.0 [no null yet] | 2.4 [no null yet] | 4.8 [no null yet] | n/a (no signals by construction) | -21.8 [no null yet] | -6.6 [no null yet] | -19.8 [no null yet] | -12.6 [no null yet] |
| tape | 0.9 [no null yet] | -10.8 [no null yet] | -0.2 [no null yet] | -30.0 [no null yet] | -5.0 [no null yet] | 0.2 [no null yet] | -25.9 [no null yet] | 2.8 [no null yet] | -0.8 [no null yet] | -11.0 [no null yet] | -21.5 [no null yet] | -43.6 [no null yet] | -28.1 [no null yet] |
| tape (native) | -25.3 [no null yet] | -32.7 [no null yet] | -13.2 [no null yet] | 15.4 [no null yet] | n/a (no signals by construction) | -25.9 [no null yet] | -21.7 [no null yet] | -13.1 [no null yet] | -7.7 [no null yet] | 6.8 [no null yet] | -8.9 [no null yet] | -31.0 [no null yet] | -29.6 [no null yet] |
| trend | -28.7 [no null yet] | -13.7 [no null yet] | -6.4 [no null yet] | -7.8 [no null yet] | -19.9 [no null yet] | -15.2 [no null yet] | -17.9 [no null yet] | -1.2 [no null yet] | 1.2 [no null yet] | -17.5 [no null yet] | -14.2 [no null yet] | -26.0 [no null yet] | -14.5 [no null yet] |
| trend (native) | -14.0 [no null yet] | 11.8 [no null yet] | -12.8 [no null yet] | 8.8 [no null yet] | -13.7 [no null yet] | -2.6 [no null yet] | -24.9 [no null yet] | -27.5 [no null yet] | n/a (no signals by construction) | -21.5 [no null yet] | -18.3 [no null yet] | -21.1 [no null yet] | -6.3 [no null yet] |
| xmarket | -2.2 [no null yet] | 9.3 [no null yet] | 3.5 [no null yet] | 3.8 [no null yet] | -1.8 [no null yet] | -19.4 [no null yet] | -51.1 [no null yet] | 6.9 [no null yet] | 5.0 [no null yet] | -27.1 [no null yet] | -1.4 [no null yet] | -27.0 [no null yet] | 9.2 [no null yet] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels|PRICE | 37.6 | 0.042 | 213.4 | 0.58 | 60.5 | 137.4 | {"2023": -26.6, "2024": 20.5, "2025": 39.4, "2026": 76.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY(book) | 28.1 | 0.034 | 208.1 | 0.58 | 96.5 | -43.2 | {"2023": 19.2, "2024": 6.5, "2025": 17.6, "2026": 68.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|FOOTPRINT | 25.3 | 0.041 | 406.5 | 0.65 | 103.2 | 51.4 | {"2023": -27.3, "2024": 22.6, "2025": -8.2, "2026": 84.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| momentum|UNKNOWN | 19.9 | 0.033 | 263.5 | 0.56 | -1.5 | -46.0 | {"2023": 68.2, "2024": 4.2, "2025": 40.7, "2026": -1.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|PRICE | 19.6 | 0.022 | 271.9 | 0.51 | 41.1 | 40.2 | {"2023": -22.3, "2024": -0.9, "2025": 33.5, "2026": 40.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|FOOTPRINT | 17.9 | 0.029 | 382.0 | 0.49 | 33.4 | 30.4 | {"2023": -34.4, "2024": -16.5, "2025": 5.7, "2026": 89.7} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| book|SESSION-RELATIVE | 17.8 | 0.011 | 257.9 | 0.56 | 52.4 | -10.8 | {"2023": -12.1, "2024": 5.3, "2025": -1.7, "2026": 65.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|COMPOSITE | 16.5 | 0.028 | 324.2 | 0.54 | 32.9 | 18.7 | {"2023": -1.2, "2024": -4.4, "2025": 43.6, "2026": 14.8} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 16.5 | 0.007 | 334.3 | 0.49 | 121.9 | 78.2 | {"2023": 5.8, "2024": -4.2, "2025": -3.5, "2026": 67.9} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "AMBER", "2026": "ok"} |
| manual (native)|INFORMATION(book) | 16.4 | 0.013 | 251.3 | 0.49 | 65.5 | 45.8 | {"2023": -1.8, "2024": -2.4, "2025": 9.7, "2026": 52.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 94.7%); M7 tm60 L6M -39.6 pts/wk, rank 10% (top 90.4%); U7 tm600 L6M -10.7 pts/wk, rank 33% (top 66.8%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.3%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 37.9%); A7 tm60 L6M 14.3 pts/wk, rank 79% (top 21.2%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 20.4 | 0.018 | 369.4 | 0.53 | 67.1 | 134.5 | {"2023": -26.0, "2024": 39.6, "2025": -20.6, "2026": 60.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|INFORMATION | 13.4 | 0.020 | 310.4 | 0.58 | 62.6 | 35.7 | {"2023": 2.2, "2024": 16.9, "2025": -12.1, "2026": 43.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure (native)|PRICE | 13.0 | 0.020 | 410.7 | 0.56 | 39.9 | 175.3 | {"2023": 29.6, "2024": 12.6, "2025": -20.8, "2026": 48.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels|PRICE | 12.9 | 0.013 | 454.8 | 0.51 | 71.9 | 137.4 | {"2023": -49.6, "2024": 19.3, "2025": -1.1, "2026": 41.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|COMPOSITE | 12.6 | 0.013 | 328.0 | 0.54 | 101.6 | 70.6 | {"2023": -44.6, "2024": 13.0, "2025": -4.7, "2026": 50.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| manual|INFORMATION | 11.0 | 0.014 | 445.7 | 0.47 | 115.4 | 89.0 | {"2023": -5.9, "2024": 11.7, "2025": -19.6, "2026": 51.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| confluence|TIME | 9.3 | -0.000 | 280.0 | 0.54 | 8.8 | -29.0 | {"2023": -34.3, "2024": 12.4, "2025": 32.0, "2026": -7.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| tape|COMPOSITE | 6.4 | 0.006 | 685.1 | 0.53 | 102.4 | 13.8 | {"2023": -26.1, "2024": -34.2, "2025": 11.3, "2026": 58.8} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 5.6 | -0.004 | 471.8 | 0.49 | 38.7 | 122.3 | {"2023": 7.9, "2024": -1.5, "2025": -7.7, "2026": 29.1} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "RED", "2026": "ok"} |
| momentum|PRICE | 5.0 | 0.007 | 363.3 | 0.54 | -12.4 | -84.0 | {"2023": -21.8, "2024": 28.7, "2025": 0.1, "2026": -8.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | urenko_10 | momentum.momentum_stoch.zone_break_native | {"len": 14, "lvl": 70} | asym15u/30u | both | 6512 | 2679 | 332 | 1.00 | 5 / -610 / 1359 / 1.00 | {"2023": 46.0, "2024": 711.0, "2025": 731.0, "2026": 5289.0} |
| 2 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | sym8u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 106.0, "2024": 410.0, "2025": -2975.0, "2026": 6199.0} |
| 3 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | sym15u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 94.0, "2024": 833.0, "2025": -2983.0, "2026": 6202.0} |
| 4 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | asym10u/20u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 94.0, "2024": 872.0, "2025": -2975.0, "2026": 6202.0} |
| 5 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | sym30u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 94.0, "2024": 833.0, "2025": -2983.0, "2026": 6202.0} |
| 6 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | asym15u/30u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 94.0, "2024": 833.0, "2025": -2983.0, "2026": 6202.0} |
| 7 | vnorm_400 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | asym20u/10u | both | 6399 | 2685 | 273 | 1.00 | 5 / 1480 / 2815 / 1.00 | {"2023": 12.0, "2024": 600.0, "2025": -2983.0, "2026": 6202.0} |
| 8 | mrenko_20 | levels.levels_vwap.break_native | {"n": 2, "k": 0.5} | asym20u/10u | both | 6284 | 2991 | 226 | 1.00 | 5 / 801 / 1930 / 1.00 | {"2023": 120.0, "2024": -1085.0, "2025": -1977.0, "2026": 7689.0} |
| 9 | trb_400 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | asym15u/30u | both | 6219 | 3065 | 236 | 1.00 | 5 / -686 / 910 / 1.00 | {"2023": 755.0, "2024": 898.0, "2025": -212.0, "2026": 5267.0} |
| 10 | trb_400 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym30u | both | 6215 | 3013 | 234 | 1.00 | 5 / -658 / 922 / 1.00 | {"2023": 562.0, "2024": 1039.0, "2025": -384.0, "2026": 5299.0} |
| 11 | vsess_600 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | sym8u | both | 6120 | 2666 | 701 | 1.00 | 5 / -1086 / 562 / 1.00 | {"2023": -421.0, "2024": -1541.0, "2025": -1139.0, "2026": 6064.0} |
| 12 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym20u/10u | both | 6084 | 2102 | 245 | 1.00 | 5 / -256 / 3416 / 1.00 | {"2023": 76.0, "2024": 61.0, "2025": 1363.0, "2026": 7110.0} |
| 13 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 50} | sym8u | both | 6032 | 3321 | 643 | 1.00 | 5 / -163 / 2254 / 1.00 | {"2023": -1534.0, "2024": 277.0, "2025": 116.0, "2026": 5648.0} |
| 14 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 6002 | 1997 | 238 | 1.00 | 5 / -514 / 2989 / 1.00 | {"2023": 228.0, "2024": 4.0, "2025": 1073.0, "2026": 6927.0} |
| 15 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5987 | 1982 | 237 | 1.00 | 5 / -358 / 3219 / 1.00 | {"2023": 378.0, "2024": 121.0, "2025": 1041.0, "2026": 6917.0} |
| 16 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5984 | 1978 | 238 | 1.00 | 5 / -458 / 2964 / 1.00 | {"2023": 222.0, "2024": -104.0, "2025": 1188.0, "2026": 6903.0} |
| 17 | dib_6000 | levels.levels_fvg15.reject_native | {"tol": 1.0, "conf": "body"} | asym15u/30u | both | 5901 | 2810 | 163 | 1.00 | 5 / -618 / -55 / 1.00 | {"2023": -59.0, "2024": -200.0, "2025": 331.0, "2026": 6224.0} |
| 18 | dib_6000 | levels.levels_fvg15.reject_native | {"tol": 1.0, "conf": "body"} | asym10u/20u | both | 5901 | 2810 | 163 | 1.00 | 5 / -603 / -23 / 1.00 | {"2023": -179.0, "2024": -307.0, "2025": 309.0, "2026": 6270.0} |
| 19 | dib_6000 | levels.levels_fvg15.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5901 | 2810 | 163 | 1.00 | 5 / -618 / -55 / 1.00 | {"2023": -61.0, "2024": -106.0, "2025": 331.0, "2026": 6224.0} |
| 20 | dib_6000 | levels.levels_fvg15.reject_native | {"tol": 1.0, "conf": "body"} | sym30u | both | 5901 | 2810 | 163 | 1.00 | 5 / -618 / -55 / 1.00 | {"2023": -66.0, "2024": -38.0, "2025": 327.0, "2026": 6224.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -12.1 | -0.013 | 1408.2 | 0.49 | -97.1 | -12.4 |  |  |  |  | -14.0 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | -3.6 | -0.003 | 1059.8 | 0.51 | -110.8 | -12.4 |  |  |  |  | -12.4 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | 28.2 [no null yet] | 11.9 [no null yet] | -4.1 [no null yet] | 15.3 [no null yet] | -53.8 [no null yet] | -53.2 [no null yet] | 44.1 [no null yet] | 12.9 [no null yet] | n/a (no signals by construction) | 17.6 [no null yet] | 27.4 [no null yet] | 52.6 [no null yet] | 24.0 [no null yet] |
| bands (native) | 19.5 [no null yet] | 12.2 [no null yet] | 10.7 [no null yet] | -28.1 [no null yet] | -9.3 [no null yet] | 18.6 [no null yet] | -14.1 [no null yet] | 23.1 [no null yet] | n/a (no signals by construction) | -8.1 [no null yet] | 16.3 [no null yet] | 38.2 [no null yet] | 2.2 [no null yet] |
| barnative | -35.0 [no null yet] | -18.5 [no null yet] | -22.8 [no null yet] | 14.0 [no null yet] | 3.4 [no null yet] | 8.0 [no null yet] | -13.6 [no null yet] | 69.2 [no null yet] | -11.4 [no null yet] | 36.1 [no null yet] | -8.0 [no null yet] | 17.2 [no null yet] | 17.0 [no null yet] |
| book | 23.8 [no null yet] | 7.1 [no null yet] | n/a (no signals by construction) | 32.4 [no null yet] | n/a (no signals by construction) | 57.4 [no null yet] | 3.6 [no null yet] | 2.9 [no null yet] | n/a (no signals by construction) | 48.2 [no null yet] | 29.2 [no null yet] | 34.5 [no null yet] | 19.6 [no null yet] |
| book (native) | -2.9 [no null yet] | 39.4 [no null yet] | n/a (no signals by construction) | 37.0 [no null yet] | n/a (no signals by construction) | -25.0 [no null yet] | 26.8 [no null yet] | 14.6 [no null yet] | n/a (no signals by construction) | 26.5 [no null yet] | 25.0 [no null yet] | -26.3 [no null yet] | 49.1 [no null yet] |
| confluence | -8.7 [no null yet] | 31.2 [no null yet] | 2.7 [no null yet] | 4.4 [no null yet] | 15.9 [no null yet] | 6.2 [no null yet] | 16.2 [no null yet] | 21.9 [no null yet] | -5.8 [no null yet] | -11.6 [no null yet] | -8.8 [no null yet] | 1.9 [no null yet] | -5.3 [no null yet] |
| levels | 18.5 [no null yet] | 0.5 [no null yet] | 18.3 [no null yet] | 13.6 [no null yet] | -0.2 [no null yet] | -42.7 [no null yet] | 8.4 [no null yet] | -4.8 [no null yet] | -21.4 [no null yet] | 36.9 [no null yet] | 32.8 [no null yet] | -24.8 [no null yet] | 44.9 [no null yet] |
| levels (native) | 33.4 [no null yet] | 8.7 [no null yet] | -10.7 [no null yet] | 10.7 [no null yet] | -53.6 [no null yet] | -18.1 [no null yet] | -10.5 [no null yet] | 22.0 [no null yet] | -40.4 [no null yet] | 28.4 [no null yet] | 25.0 [no null yet] | 27.9 [no null yet] | 26.7 [no null yet] |
| live | 6.5 [no null yet] | 11.5 [no null yet] | -8.3 [no null yet] | 4.8 [no null yet] | 9.8 [no null yet] | 4.9 [no null yet] | 39.0 [no null yet] | -6.0 [no null yet] | n/a (no signals by construction) | 37.2 [no null yet] | 12.8 [no null yet] | -2.0 [no null yet] | 3.3 [no null yet] |
| manual | 31.0 [no null yet] | 13.1 [no null yet] | -13.3 [no null yet] | 17.3 [no null yet] | 10.3 [no null yet] | 23.6 [no null yet] | 3.0 [no null yet] | -12.8 [no null yet] | -6.6 [no null yet] | -15.1 [no null yet] | 21.6 [no null yet] | 38.1 [no null yet] | 35.9 [no null yet] |
| manual (native) | -64.9 [no null yet] | -27.0 [no null yet] | 5.6 [no null yet] | -12.1 [no null yet] | -16.8 [no null yet] | -26.4 [no null yet] | -31.4 [no null yet] | -18.6 [no null yet] | n/a (no signals by construction) | -14.8 [no null yet] | -26.9 [no null yet] | -14.7 [no null yet] | -29.0 [no null yet] |
| momentum | 15.7 [no null yet] | 42.1 [no null yet] | 4.1 [no null yet] | 27.5 [no null yet] | -47.4 [no null yet] | 1.5 [no null yet] | 21.3 [no null yet] | 0.9 [no null yet] | -8.9 [no null yet] | -3.9 [no null yet] | -3.3 [no null yet] | 29.0 [no null yet] | 21.8 [no null yet] |
| momentum (native) | 26.2 [no null yet] | 17.5 [no null yet] | 9.7 [no null yet] | -2.9 [no null yet] | -21.3 [no null yet] | -1.8 [no null yet] | 4.4 [no null yet] | 47.4 [no null yet] | n/a (no signals by construction) | 5.0 [no null yet] | -8.2 [no null yet] | 35.0 [no null yet] | 7.3 [no null yet] |
| pullback | 30.4 [no null yet] | -11.4 [no null yet] | 12.8 [no null yet] | -8.7 [no null yet] | -62.8 [no null yet] | 37.2 [no null yet] | 34.4 [no null yet] | -18.5 [no null yet] | -1.8 [no null yet] | -9.3 [no null yet] | 40.1 [no null yet] | 5.6 [no null yet] | -20.3 [no null yet] |
| pullback (native) | 14.6 [no null yet] | 14.4 [no null yet] | -22.3 [no null yet] | 10.0 [no null yet] | -3.0 [no null yet] | 14.5 [no null yet] | 1.8 [no null yet] | -21.5 [no null yet] | n/a (no signals by construction) | 12.2 [no null yet] | 9.4 [no null yet] | 18.6 [no null yet] | -12.3 [no null yet] |
| structure | 7.5 [no null yet] | 2.6 [no null yet] | 7.5 [no null yet] | -2.6 [no null yet] | 52.4 [no null yet] | 56.6 [no null yet] | 58.6 [no null yet] | 10.8 [no null yet] | -17.3 [no null yet] | -20.8 [no null yet] | 10.0 [no null yet] | -2.2 [no null yet] | 8.9 [no null yet] |
| structure (native) | 42.1 [no null yet] | 3.7 [no null yet] | 5.0 [no null yet] | -1.3 [no null yet] | -3.2 [no null yet] | 19.5 [no null yet] | -8.2 [no null yet] | 13.7 [no null yet] | n/a (no signals by construction) | -9.8 [no null yet] | 25.6 [no null yet] | 25.4 [no null yet] | 12.8 [no null yet] |
| tape | -9.9 [no null yet] | -11.7 [no null yet] | -8.9 [no null yet] | -0.4 [no null yet] | -21.3 [no null yet] | 10.4 [no null yet] | -9.0 [no null yet] | 18.7 [no null yet] | -5.4 [no null yet] | -24.2 [no null yet] | -0.3 [no null yet] | -20.4 [no null yet] | -13.7 [no null yet] |
| tape (native) | 12.8 [no null yet] | 32.7 [no null yet] | -10.5 [no null yet] | -0.0 [no null yet] | -5.4 [no null yet] | -6.2 [no null yet] | -9.7 [no null yet] | 3.4 [no null yet] | -6.1 [no null yet] | -4.4 [no null yet] | -19.4 [no null yet] | -28.4 [no null yet] | -34.3 [no null yet] |
| trend | -17.4 [no null yet] | 14.8 [no null yet] | -20.3 [no null yet] | -8.0 [no null yet] | -36.7 [no null yet] | -31.8 [no null yet] | -17.4 [no null yet] | 5.4 [no null yet] | -16.3 [no null yet] | -8.6 [no null yet] | 17.9 [no null yet] | -24.2 [no null yet] | 33.7 [no null yet] |
| trend (native) | -43.5 [no null yet] | -1.8 [no null yet] | -23.6 [no null yet] | -37.3 [no null yet] | -7.9 [no null yet] | -28.7 [no null yet] | -7.4 [no null yet] | 1.8 [no null yet] | n/a (no signals by construction) | -27.4 [no null yet] | 17.5 [no null yet] | -12.0 [no null yet] | 23.1 [no null yet] |
| xmarket | -0.2 [no null yet] | -46.2 [no null yet] | 10.1 [no null yet] | -41.1 [no null yet] | -6.8 [no null yet] | -35.5 [no null yet] | -12.9 [no null yet] | -23.4 [no null yet] | -7.9 [no null yet] | -22.7 [no null yet] | 7.1 [no null yet] | 14.5 [no null yet] | 20.4 [no null yet] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 69.2 | 0.035 | 225.6 | 0.59 | 121.5 | 120.2 | {"2023": -42.2, "2024": 15.2, "2025": 108.1, "2026": 122.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION(book) | 58.6 | 0.041 | 377.7 | 0.57 | 71.1 | 146.1 | {"2023": 112.6, "2024": 17.6, "2025": 67.4, "2026": 79.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|INFORMATION | 57.4 | 0.040 | 365.1 | 0.60 | 145.4 | 115.3 | {"2023": 40.9, "2024": 19.6, "2025": 104.2, "2026": 51.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 56.6 | 0.036 | 712.4 | 0.64 | 5.9 | 46.2 | {"2023": 34.1, "2024": 36.0, "2025": 127.3, "2026": 4.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|TIME | 52.6 | 0.033 | 474.1 | 0.58 | 94.7 | 36.4 | {"2023": 10.3, "2024": 24.4, "2025": 63.2, "2026": 86.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|FOOTPRINT | 52.4 | 0.034 | 263.2 | 0.62 | -43.2 | -136.4 | {"2023": -43.0, "2024": 88.2, "2025": 63.8, "2026": 27.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|UNKNOWN | 49.1 | 0.028 | 857.9 | 0.59 | -28.6 | -124.2 | {"2023": -129.0, "2024": 22.3, "2025": 126.4, "2026": 46.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|SESSION-RELATIVE | 48.2 | 0.019 | 651.5 | 0.58 | 25.2 | -19.2 | {"2023": -10.5, "2024": 1.4, "2025": 176.6, "2026": -29.6} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|PRICE | 47.4 | 0.029 | 427.8 | 0.53 | 34.9 | 89.9 | {"2023": 55.2, "2024": -12.1, "2025": 130.9, "2026": 16.5} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| levels|UNKNOWN | 44.9 | 0.034 | 577.1 | 0.58 | 76.1 | 121.9 | {"2023": -14.9, "2024": -2.0, "2025": 107.2, "2026": 45.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 7% (top 93.4%); M7 tm60 L6M -8.9 pts/wk, rank 45% (top 55.0%); U7 tm600 L6M -11.4 pts/wk, rank 42% (top 57.9%); P7 tm60 L6M -60.7 pts/wk, rank 11% (top 89.5%); H7 tm60 L6M 28.8 pts/wk, rank 85% (top 14.5%); A7 tm60 L6M -17.2 pts/wk, rank 36% (top 63.7%); O7 tm60 L6M 15.1 pts/wk, rank 76% (top 23.6%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| book|ACTIVITY | 63.6 | 0.044 | 263.9 | 0.63 | 23.8 | -18.5 | {"2023": 40.4, "2024": 51.3, "2025": 91.2, "2026": 53.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|TIME | 55.0 | 0.033 | 539.0 | 0.58 | 94.7 | 36.4 | {"2023": 10.3, "2024": 22.6, "2025": 72.6, "2026": 86.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 51.0 | 0.034 | 772.1 | 0.65 | -38.7 | 189.4 | {"2023": 67.9, "2024": 56.8, "2025": 108.8, "2026": -29.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| bands|ACTIVITY | 47.5 | 0.028 | 255.0 | 0.53 | 49.3 | 94.6 | {"2023": -41.1, "2024": 56.3, "2025": 80.4, "2026": 26.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 47.1 | 0.026 | 505.4 | 0.56 | -6.4 | 44.6 | {"2023": 26.1, "2024": -21.2, "2025": 145.2, "2026": 18.5} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 46.6 | 0.032 | 729.4 | 0.62 | 2.7 | 60.5 | {"2023": 73.2, "2024": 39.1, "2025": 94.6, "2026": -9.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| momentum|PRICE | 43.3 | 0.031 | 826.1 | 0.58 | 24.1 | 175.4 | {"2023": 77.7, "2024": -25.0, "2025": 115.0, "2026": 28.4} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 42.2 | 0.032 | 541.7 | 0.64 | 117.6 | 105.1 | {"2023": 74.7, "2024": 33.0, "2025": 53.5, "2026": 29.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|INFORMATION | 39.4 | 0.027 | 713.5 | 0.63 | 4.3 | 147.6 | {"2023": 27.6, "2024": 63.1, "2025": 9.8, "2026": 50.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 38.4 | 0.033 | 510.4 | 0.56 | 150.1 | 54.1 | {"2023": -28.6, "2024": 9.9, "2025": 58.3, "2026": 70.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | pnf_5 | book.book_cancel.ratio_follow | {"L": 100, "z": 2.0} | asym20u/10u | both | 9583 | 3157 | 460 | 0.75 | 4 / 1567 / 3977 / 1.00 | {"2023": -15.0, "2024": -2940.0, "2025": 2189.0, "2026": 11746.0} |
| 2 | frenko_28 | tape.tape_delta.cvd_fade | {"N": 10, "L": 100, "z": 1.0} | asym10u/20u | both | 9365 | 2858 | 566 | 0.67 | 0 /  /  /  | {"2023": -3459.0, "2024": 2614.0, "2025": -2110.0, "2026": 8465.0} |
| 3 | sessrng_B500 | tape.tape_run.runv_fade | {"thr": 15} | plain60/60 | both | 8892 | 1908 | 1498 | 1.00 | 0 /  /  /  | {"2023": -256.0, "2024": -3791.0, "2025": -5506.0, "2026": 5948.0} |
| 4 | vib_25000 | tape.tape_delta.fade | {"L": 50, "z": 1.0} | plain60/60 | both | 8835 | 4421 | 979 | 1.00 | 0 /  /  /  | {"2023": -1810.0, "2024": -908.0, "2025": -5425.0, "2026": 9879.0} |
| 5 | pnf_5 | book.book_cancel.ratio_follow | {"L": 200, "z": 2.0} | asym20u/10u | both | 8787 | 2421 | 460 | 0.67 | 4 / -530 / 716 / 1.00 | {"2023": -243.0, "2024": -2348.0, "2025": 5773.0, "2026": 9826.0} |
| 6 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | sym15u | both | 8704 | 3814 | 509 | 1.00 | 4 / 419 / 2979 / 1.00 | {"2023": -91.0, "2024": -1608.0, "2025": 3335.0, "2026": 10363.0} |
| 7 | urenko_10 | levels.levels_round.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 8603 | 1159 | 656 | 0.67 | 5 / -821 / 963 / 1.00 | {"2023": -677.0, "2024": -3216.0, "2025": -3967.0, "2026": 9974.0} |
| 8 | lbrk_4_10 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 8520 | 3011 | 1635 | 1.00 | 5 / 561 / 4165 / 1.00 | {"2023": 911.0, "2024": 1308.0, "2025": -5892.0, "2026": 11502.0} |
| 9 | volor_B500 | tape.tape_run.runv_fade | {"thr": 15} | plain60/60 | both | 8517 | 2708 | 1511 | 1.00 | 5 / -1733 / 104 / 1.00 | {"2023": -228.0, "2024": -2941.0, "2025": -4636.0, "2026": 6130.0} |
| 10 | rngor_B500 | book.book_sweep.cnt_fade | {"thr": 2} | plain60/60 | both | 8485 | 4234 | 1592 | 1.00 | 0 /  /  /  | {"2023": -685.0, "2024": -412.0, "2025": -1026.0, "2026": 8813.0} |
| 11 | urenko_14 | book.book_micro.follow | {"L": 50, "z": 2.0} | sym15u | both | 8473 | 1752 | 476 | 0.67 | 5 / 1914 / 4230 / 1.00 | {"2023": 1064.0, "2024": -1822.0, "2025": -1352.0, "2026": 8902.0} |
| 12 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | asym15u/30u | both | 8456 | 3566 | 508 | 1.00 | 4 / 409 / 2954 / 1.00 | {"2023": 15.0, "2024": 239.0, "2025": 2832.0, "2026": 9992.0} |
| 13 | dib_700 | bands.bands_bollinger.break | {"n": 14, "k": 1.5} | asym20u/10u | both | 8440 | 3980 | 1152 | 0.60 | 5 / -950 / 759 / 1.00 | {"2023": -1554.0, "2024": 596.0, "2025": 771.0, "2026": 6996.0} |
| 14 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | sym30u | both | 8430 | 3540 | 508 | 1.00 | 4 / 263 / 2691 / 1.00 | {"2023": 1715.0, "2024": -318.0, "2025": 3183.0, "2026": 10176.0} |
| 15 | time_s_20 | xmarket.xmarket_fast.follow_RTY | {"w": 5, "thr": 1.0} | sym15u | both | 8370 | 2950 | 570 | 0.75 | 5 / -1518 / 1839 / 1.00 | {"2023": 2445.0, "2024": -2021.0, "2025": 3099.0, "2026": 9901.0} |
| 16 | pnf_5 | book.book_cancel.ratio_follow | {"L": 200, "z": 2.0} | sym15u | both | 8334 | 2137 | 439 | 0.67 | 4 / -1160 / -40 / 1.00 | {"2023": -974.0, "2024": 373.0, "2025": 5390.0, "2026": 6562.0} |
| 17 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym10u/20u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 18 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym8u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1979.0, "2024": 70.0, "2025": 270.0, "2026": 9143.0} |
| 19 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym15u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 20 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym15u/30u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -2.8 | 0.003 | 1068.6 | 0.52 | 26.9 | -27.1 |  |  |  |  | -15.2 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | 5.6 | 0.008 | 889.1 | 0.54 | 51.5 | 26.2 |  |  |  |  | -9.3 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | 10.8 [no null yet] | -18.3 [no null yet] | -17.6 [no null yet] | -1.2 [no null yet] | 25.5 [no null yet] | 33.1 [no null yet] | -16.5 [no null yet] | -12.7 [no null yet] | n/a (no signals by construction) | 2.8 [no null yet] | 16.3 [no null yet] | -44.1 [no null yet] | -28.0 [no null yet] |
| bands (native) | 38.6 [no null yet] | -20.6 [no null yet] | 5.6 [no null yet] | -16.7 [no null yet] | -31.9 [no null yet] | -70.0 [no null yet] | -31.0 [no null yet] | 37.4 [no null yet] | n/a (no signals by construction) | -52.3 [no null yet] | -31.7 [no null yet] | -9.0 [no null yet] | -38.2 [no null yet] |
| barnative | -3.6 [no null yet] | 20.7 [no null yet] | -8.2 [no null yet] | -12.1 [no null yet] | -7.6 [no null yet] | -2.7 [no null yet] | -7.0 [no null yet] | 25.2 [no null yet] | 4.0 [no null yet] | 16.6 [no null yet] | -2.1 [no null yet] | -37.5 [no null yet] | 4.1 [no null yet] |
| book | 1.7 [no null yet] | -35.5 [no null yet] | n/a (no signals by construction) | -18.0 [no null yet] | n/a (no signals by construction) | -21.7 [no null yet] | -31.9 [no null yet] | 4.9 [no null yet] | n/a (no signals by construction) | -5.3 [no null yet] | 2.2 [no null yet] | -23.7 [no null yet] | 6.2 [no null yet] |
| book (native) | -19.1 [no null yet] | -12.1 [no null yet] | n/a (no signals by construction) | 20.5 [no null yet] | n/a (no signals by construction) | -41.4 [no null yet] | 1.2 [no null yet] | 13.4 [no null yet] | n/a (no signals by construction) | -13.6 [no null yet] | 39.1 [no null yet] | -31.7 [no null yet] | 43.8 [no null yet] |
| confluence | 12.0 [no null yet] | 4.6 [no null yet] | -6.9 [no null yet] | -28.1 [no null yet] | -25.9 [no null yet] | -10.7 [no null yet] | -7.8 [no null yet] | -43.5 [no null yet] | 1.8 [no null yet] | 5.1 [no null yet] | -40.7 [no null yet] | -18.3 [no null yet] | 11.7 [no null yet] |
| levels | 11.2 [no null yet] | 14.7 [no null yet] | -0.7 [no null yet] | 23.1 [no null yet] | 17.2 [no null yet] | -38.8 [no null yet] | 7.4 [no null yet] | -31.3 [no null yet] | -16.5 [no null yet] | -4.7 [no null yet] | -21.5 [no null yet] | -18.8 [no null yet] | -34.5 [no null yet] |
| levels (native) | -11.5 [no null yet] | 20.1 [no null yet] | -1.8 [no null yet] | -24.4 [no null yet] | 46.0 [no null yet] | -22.1 [no null yet] | 32.2 [no null yet] | -14.4 [no null yet] | 8.9 [no null yet] | -9.2 [no null yet] | -21.9 [no null yet] | -15.4 [no null yet] | -22.1 [no null yet] |
| live | -18.9 [no null yet] | 1.8 [no null yet] | -29.2 [no null yet] | -20.7 [no null yet] | -26.5 [no null yet] | -46.0 [no null yet] | -51.8 [no null yet] | -33.7 [no null yet] | n/a (no signals by construction) | -31.1 [no null yet] | 24.9 [no null yet] | -15.8 [no null yet] | -7.0 [no null yet] |
| manual | -3.4 [no null yet] | -16.0 [no null yet] | -51.0 [no null yet] | -15.4 [no null yet] | 6.3 [no null yet] | 9.3 [no null yet] | -5.2 [no null yet] | 4.0 [no null yet] | -7.5 [no null yet] | -10.7 [no null yet] | -22.2 [no null yet] | 5.6 [no null yet] | -33.7 [no null yet] |
| manual (native) | 25.5 [no null yet] | 9.7 [no null yet] | -25.2 [no null yet] | 38.5 [no null yet] | -12.0 [no null yet] | 18.3 [no null yet] | -15.4 [no null yet] | 28.6 [no null yet] | n/a (no signals by construction) | 6.6 [no null yet] | -10.4 [no null yet] | -17.8 [no null yet] | -33.5 [no null yet] |
| momentum | 0.7 [no null yet] | -11.1 [no null yet] | -10.7 [no null yet] | -25.4 [no null yet] | -7.6 [no null yet] | 15.1 [no null yet] | -13.2 [no null yet] | -8.1 [no null yet] | -15.0 [no null yet] | -3.8 [no null yet] | -42.8 [no null yet] | -4.0 [no null yet] | -40.4 [no null yet] |
| momentum (native) | 3.1 [no null yet] | 4.8 [no null yet] | -0.6 [no null yet] | -24.1 [no null yet] | -1.3 [no null yet] | -12.5 [no null yet] | -11.2 [no null yet] | -4.1 [no null yet] | n/a (no signals by construction) | 7.7 [no null yet] | -17.7 [no null yet] | -16.0 [no null yet] | -32.8 [no null yet] |
| pullback | -28.0 [no null yet] | -24.6 [no null yet] | 28.3 [no null yet] | 19.9 [no null yet] | -13.5 [no null yet] | -35.4 [no null yet] | 8.8 [no null yet] | -17.6 [no null yet] | 6.0 [no null yet] | -26.8 [no null yet] | -30.5 [no null yet] | -17.4 [no null yet] | 19.1 [no null yet] |
| pullback (native) | -10.4 [no null yet] | -28.1 [no null yet] | -21.5 [no null yet] | -24.4 [no null yet] | -31.1 [no null yet] | -13.1 [no null yet] | -4.3 [no null yet] | -9.1 [no null yet] | n/a (no signals by construction) | -2.8 [no null yet] | -7.0 [no null yet] | -14.0 [no null yet] | -5.9 [no null yet] |
| structure | 1.8 [no null yet] | -15.1 [no null yet] | -25.2 [no null yet] | -17.6 [no null yet] | -1.2 [no null yet] | -24.1 [no null yet] | 15.2 [no null yet] | -35.4 [no null yet] | -6.4 [no null yet] | -30.5 [no null yet] | -30.8 [no null yet] | 15.7 [no null yet] | -34.4 [no null yet] |
| structure (native) | 4.3 [no null yet] | -27.9 [no null yet] | -9.9 [no null yet] | -25.7 [no null yet] | 2.2 [no null yet] | -27.8 [no null yet] | 2.6 [no null yet] | -23.7 [no null yet] | n/a (no signals by construction) | -17.7 [no null yet] | 22.4 [no null yet] | 31.5 [no null yet] | -5.4 [no null yet] |
| tape | -8.1 [no null yet] | 16.6 [no null yet] | -7.8 [no null yet] | 5.9 [no null yet] | -8.0 [no null yet] | 19.9 [no null yet] | 29.5 [no null yet] | -15.2 [no null yet] | -8.0 [no null yet] | -51.0 [no null yet] | -25.0 [no null yet] | -7.4 [no null yet] | 0.3 [no null yet] |
| tape (native) | 11.1 [no null yet] | -11.8 [no null yet] | -26.2 [no null yet] | -31.8 [no null yet] | -1.5 [no null yet] | -18.7 [no null yet] | -20.8 [no null yet] | 19.0 [no null yet] | n/a (no signals by construction) | 27.4 [no null yet] | -31.8 [no null yet] | 7.6 [no null yet] | -15.2 [no null yet] |
| trend | -29.1 [no null yet] | 24.0 [no null yet] | -12.5 [no null yet] | 9.8 [no null yet] | -3.1 [no null yet] | 55.5 [no null yet] | -36.2 [no null yet] | 10.2 [no null yet] | -9.0 [no null yet] | -1.4 [no null yet] | -32.0 [no null yet] | 35.4 [no null yet] | -38.8 [no null yet] |
| trend (native) | 10.7 [no null yet] | -7.5 [no null yet] | 4.0 [no null yet] | -26.3 [no null yet] | 17.1 [no null yet] | 14.1 [no null yet] | -12.0 [no null yet] | -15.7 [no null yet] | n/a (no signals by construction) | -16.0 [no null yet] | -28.7 [no null yet] | 23.1 [no null yet] | -17.6 [no null yet] |
| xmarket | 32.2 [no null yet] | -6.9 [no null yet] | -16.8 [no null yet] | -10.3 [no null yet] | -15.7 [no null yet] | -26.5 [no null yet] | -16.9 [no null yet] | -52.5 [no null yet] | 14.7 [no null yet] | -15.6 [no null yet] | 0.6 [no null yet] | -35.8 [no null yet] | -8.7 [no null yet] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| trend|INFORMATION | 55.5 | 0.031 | 270.0 | 0.62 | 124.6 | 71.7 | {"2023": -1.5, "2024": 22.4, "2025": 107.1, "2026": 51.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|FOOTPRINT | 46.0 | 0.044 | 406.8 | 0.72 | 113.5 | 67.4 | {"2023": 53.9, "2024": 32.0, "2025": 7.3, "2026": 105.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|UNKNOWN | 43.8 | 0.042 | 427.0 | 0.56 | 104.5 | 40.9 | {"2023": 1.3, "2024": 25.1, "2025": 12.9, "2026": 116.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|SMOOTHING | 39.1 | 0.033 | 482.7 | 0.57 | 93.2 | -17.2 | {"2023": 1.3, "2024": 21.2, "2025": -6.6, "2026": 126.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "AMBER", "2026": "ok"} |
| bands (native)|ACTIVITY | 38.6 | 0.038 | 259.2 | 0.56 | 62.6 | 16.5 | {"2023": 62.0, "2024": 56.6, "2025": 27.8, "2026": 22.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual (native)|COMPOSITE | 38.5 | 0.030 | 437.2 | 0.57 | 77.6 | 46.5 | {"2023": 7.6, "2024": -31.4, "2025": 99.7, "2026": 58.4} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 37.4 | 0.031 | 344.2 | 0.59 | 40.6 | -34.5 | {"2023": 36.3, "2024": 71.6, "2025": -1.2, "2026": 43.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|TIME | 35.4 | 0.023 | 375.2 | 0.54 | 98.7 | -47.7 | {"2023": -58.2, "2024": -4.4, "2025": 73.9, "2026": 66.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 33.1 | 0.028 | 415.0 | 0.58 | -10.4 | -37.2 | {"2023": 8.3, "2024": 79.3, "2025": 26.1, "2026": -5.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| levels (native)|INFORMATION(book) | 32.2 | 0.030 | 242.0 | 0.53 | 48.1 | -44.7 | {"2023": 11.9, "2024": 25.4, "2025": 51.9, "2026": 23.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 25% (top 75.3%); M7 tm60 L6M -36.8 pts/wk, rank 16% (top 84.4%); U7 tm600 L6M 4.8 pts/wk, rank 61% (top 38.9%); P7 tm60 L6M -35.9 pts/wk, rank 16% (top 84.0%); H7 tm60 L6M -20.1 pts/wk, rank 27% (top 73.5%); A7 tm60 L6M -32.5 pts/wk, rank 18% (top 82.1%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| tape|INFORMATION | 44.6 | 0.025 | 278.5 | 0.56 | -20.3 | 70.9 | {"2023": 5.3, "2024": 17.6, "2025": 99.1, "2026": 24.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|INFORMATION | 43.3 | 0.025 | 295.9 | 0.58 | 89.8 | 71.7 | {"2023": -15.8, "2024": 1.2, "2025": 116.6, "2026": 25.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|ACTIVITY | 42.7 | 0.041 | 345.8 | 0.63 | -15.1 | -15.2 | {"2023": 89.1, "2024": 27.4, "2025": 55.3, "2026": 31.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|TIME | 42.0 | 0.026 | 323.5 | 0.57 | 98.7 | -47.7 | {"2023": -34.1, "2024": -2.6, "2025": 86.1, "2026": 66.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|INFORMATION | 40.9 | 0.025 | 456.2 | 0.53 | 41.1 | 70.9 | {"2023": 69.5, "2024": 2.4, "2025": 118.0, "2026": -13.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend|PRICE | 39.0 | 0.026 | 381.3 | 0.60 | 70.9 | 32.0 | {"2023": -34.0, "2024": 33.8, "2025": 56.9, "2026": 47.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 31.3 | 0.035 | 319.9 | 0.53 | 56.3 | 3.0 | {"2023": 25.8, "2024": 59.1, "2025": 27.3, "2026": 4.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|ACTIVITY | 29.2 | 0.017 | 315.4 | 0.54 | -35.3 | 11.5 | {"2023": 42.9, "2024": 14.1, "2025": 65.5, "2026": -0.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 28.6 | 0.012 | 494.4 | 0.54 | -23.3 | 16.8 | {"2023": 30.5, "2024": -10.6, "2025": 58.8, "2026": 38.7} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend (native)|TIME | 27.5 | 0.013 | 440.0 | 0.57 | 8.4 | -26.8 | {"2023": -59.9, "2024": 6.7, "2025": 114.6, "2026": -23.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | book.book_cancel.canc_follow | {"L": 50, "z": 1.0} | sym8u | both | 7366 | 2160 | 380 | 1.00 | 5 / -1132 / 135 / 1.00 | {"2023": -3094.0, "2024": -995.0, "2025": 1960.0, "2026": 4416.0} |
| 2 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | sym15u | both | 7160 | 603 | 320 | 1.00 | 5 / -1336 / 1065 / 1.00 | {"2023": 1849.0, "2024": 706.0, "2025": 273.0, "2026": 6236.0} |
| 3 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | asym10u/20u | both | 7160 | 603 | 320 | 1.00 | 5 / -1408 / 928 / 1.00 | {"2023": 1028.0, "2024": 1534.0, "2025": 607.0, "2026": 6424.0} |
| 4 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | sym30u | both | 7160 | 603 | 320 | 1.00 | 5 / -1336 / 1065 / 1.00 | {"2023": 1874.0, "2024": 972.0, "2025": 453.0, "2026": 6246.0} |
| 5 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | asym15u/30u | both | 7160 | 603 | 320 | 1.00 | 5 / -1336 / 1065 / 1.00 | {"2023": 1955.0, "2024": 1061.0, "2025": 464.0, "2026": 6236.0} |
| 6 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | asym20u/10u | both | 7026 | 469 | 321 | 1.00 | 5 / -1367 / 879 / 1.00 | {"2023": 1551.0, "2024": 676.0, "2025": -44.0, "2026": 6104.0} |
| 7 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | sym8u | both | 7024 | 477 | 323 | 1.00 | 5 / -1397 / 1289 / 1.00 | {"2023": 1973.0, "2024": 1207.0, "2025": -452.0, "2026": 5982.0} |
| 8 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | sym30u | both | 7013 | 4035 | 316 | 1.00 | 5 / -265 / 561 / 1.00 | {"2023": 272.0, "2024": -280.0, "2025": -3018.0, "2026": 5787.0} |
| 9 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | asym20u/10u | both | 7013 | 4035 | 316 | 1.00 | 5 / -265 / 561 / 1.00 | {"2023": 230.0, "2024": -352.0, "2025": -2964.0, "2026": 5787.0} |
| 10 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | asym15u/30u | both | 7013 | 4035 | 316 | 1.00 | 5 / -265 / 561 / 1.00 | {"2023": 272.0, "2024": -280.0, "2025": -3018.0, "2026": 5787.0} |
| 11 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | sym15u | both | 7013 | 4035 | 316 | 1.00 | 5 / -265 / 561 / 1.00 | {"2023": 272.0, "2024": -280.0, "2025": -3018.0, "2026": 5787.0} |
| 12 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | asym10u/20u | both | 7013 | 4035 | 316 | 1.00 | 5 / -265 / 561 / 1.00 | {"2023": 410.0, "2024": -292.0, "2025": -3018.0, "2026": 5787.0} |
| 13 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | asym10u/20u | both | 7007 | 4043 | 319 | 1.00 | 5 / -168 / 1360 / 1.00 | {"2023": -142.0, "2024": 126.0, "2025": -731.0, "2026": 5485.0} |
| 14 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | sym30u | both | 7007 | 4043 | 319 | 1.00 | 5 / -168 / 1360 / 1.00 | {"2023": -307.0, "2024": 115.0, "2025": -731.0, "2026": 5485.0} |
| 15 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | asym15u/30u | both | 7007 | 4043 | 319 | 1.00 | 5 / -168 / 1360 / 1.00 | {"2023": -307.0, "2024": 115.0, "2025": -731.0, "2026": 5485.0} |
| 16 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | asym20u/10u | both | 7007 | 4043 | 319 | 1.00 | 5 / -168 / 1360 / 1.00 | {"2023": -334.0, "2024": 36.0, "2025": -677.0, "2026": 5485.0} |
| 17 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | sym15u | both | 7007 | 4043 | 319 | 1.00 | 5 / -168 / 1360 / 1.00 | {"2023": -307.0, "2024": 115.0, "2025": -731.0, "2026": 5485.0} |
| 18 | dol_2600 | book.book_ofi.follow | {"L": 200, "z": 1.0} | sym8u | both | 6997 | 4019 | 316 | 1.00 | 5 / -254 / 586 / 1.00 | {"2023": 936.0, "2024": -146.0, "2025": -3078.0, "2026": 5771.0} |
| 19 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.75 | 5 / 991 / 2269 / 1.00 | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 20 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | sym8u | both | 6991 | 4027 | 319 | 1.00 | 5 / -231 / 1348 / 1.00 | {"2023": 121.0, "2024": 418.0, "2025": -963.0, "2026": 5469.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -16.5 | -0.014 | 1075.7 | 0.43 | -10.4 | -118.2 |  |  |  |  | -3.4 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| agreed | -16.5 | -0.014 | 1075.7 | 0.43 | -10.4 | -118.2 |  |  |  |  | -2.9 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 11.8 [no null yet] | 17.2 [no null yet] | 24.6 [no null yet] | 14.4 [no null yet] |
| bands (native) | 3.9 [no null yet] | 5.8 [no null yet] | 4.5 [no null yet] | 14.1 [no null yet] |
| barnative | 7.1 [no null yet] | -43.3 [no null yet] | -30.4 [no null yet] | -23.0 [no null yet] |
| book | -18.6 [no null yet] | -14.3 [no null yet] | -3.6 [no null yet] | -8.2 [no null yet] |
| book (native) | 4.0 [no null yet] | -39.1 [no null yet] | 1.7 [no null yet] | -28.8 [no null yet] |
| confluence | 15.1 [no null yet] | 12.3 [no null yet] | -8.3 [no null yet] | -25.6 [no null yet] |
| levels | 17.0 [no null yet] | 17.0 [no null yet] | -8.7 [no null yet] | -9.4 [no null yet] |
| levels (native) | 29.1 [no null yet] | -16.7 [no null yet] | 16.5 [no null yet] | -18.7 [no null yet] |
| live | 15.4 [no null yet] | -2.5 [no null yet] | -4.9 [no null yet] | -7.3 [no null yet] |
| manual | 7.8 [no null yet] | 15.7 [no null yet] | -1.7 [no null yet] | -19.3 [no null yet] |
| manual (native) | -10.0 [no null yet] | -23.8 [no null yet] | -15.1 [no null yet] | 6.7 [no null yet] |
| momentum | 26.4 [no null yet] | -8.2 [no null yet] | 20.9 [no null yet] | 1.3 [no null yet] |
| momentum (native) | -8.7 [no null yet] | 1.9 [no null yet] | 0.3 [no null yet] | 5.5 [no null yet] |
| pullback | 19.2 [no null yet] | -16.0 [no null yet] | -14.6 [no null yet] | -22.2 [no null yet] |
| pullback (native) | 16.5 [no null yet] | -8.6 [no null yet] | 20.5 [no null yet] | 6.1 [no null yet] |
| structure | -7.8 [no null yet] | -0.7 [no null yet] | 3.6 [no null yet] | -7.1 [no null yet] |
| structure (native) | 5.8 [no null yet] | 8.4 [no null yet] | 13.1 [no null yet] | -20.1 [no null yet] |
| tape | 4.0 [no null yet] | -12.7 [no null yet] | 3.6 [no null yet] | 10.2 [no null yet] |
| tape (native) | 3.2 [no null yet] | 21.8 [no null yet] | -11.4 [no null yet] | -1.7 [no null yet] |
| trend | 3.2 [no null yet] | 3.3 [no null yet] | -4.1 [no null yet] | -1.2 [no null yet] |
| trend (native) | -16.5 [no null yet] | 14.0 [no null yet] | -12.3 [no null yet] | -20.1 [no null yet] |
| xmarket | 6.1 [no null yet] | -31.4 [no null yet] | 10.1 [no null yet] | -26.4 [no null yet] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels (native)|ACTIVITY | 29.1 | 0.037 | 148.1 | 0.56 | 58.2 | 26.1 | {"2023": -9.8, "2024": 15.5, "2025": 42.9, "2026": 41.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|ACTIVITY | 26.4 | 0.033 | 325.3 | 0.56 | 35.8 | 6.9 | {"2023": -4.5, "2024": 26.5, "2025": 7.2, "2026": 58.7} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 24.6 | 0.023 | 215.6 | 0.57 | 36.8 | -14.0 | {"2023": 9.4, "2024": 11.1, "2025": 42.0, "2026": 24.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|INFORMATION | 21.8 | 0.021 | 523.5 | 0.52 | 64.2 | 8.1 | {"2023": -33.9, "2024": 25.2, "2025": -23.9, "2026": 89.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| momentum|PRICE | 20.9 | 0.016 | 477.3 | 0.58 | -36.5 | -2.8 | {"2023": 8.9, "2024": 38.1, "2025": 45.9, "2026": -25.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| pullback (native)|PRICE | 20.5 | 0.013 | 284.0 | 0.56 | 6.2 | 28.4 | {"2023": 51.4, "2024": 27.3, "2025": -12.6, "2026": 41.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| pullback|ACTIVITY | 19.2 | 0.020 | 384.6 | 0.58 | 62.2 | -53.7 | {"2023": 11.7, "2024": 28.5, "2025": 7.5, "2026": 24.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 17.2 | 0.017 | 375.2 | 0.57 | -3.5 | 27.5 | {"2023": 18.9, "2024": 22.6, "2025": 44.2, "2026": -21.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels|ACTIVITY | 17.0 | 0.020 | 301.3 | 0.52 | 30.8 | -29.8 | {"2023": -9.3, "2024": 14.4, "2025": -1.3, "2026": 50.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|INFORMATION | 17.0 | 0.016 | 179.5 | 0.51 | -13.8 | -27.4 | {"2023": 23.8, "2024": 11.9, "2025": 9.6, "2026": 29.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 2.0%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.4%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 10.1%); P7 tm60 L6M 66.1 pts/wk, rank 97% (top 2.6%); H7 tm60 L6M 25.1 pts/wk, rank 84% (top 15.8%); A7 tm60 L6M 6.5 pts/wk, rank 66% (top 34.4%). Rank = share of ALL Asia cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| manual|PRICE | 32.5 | 0.038 | 181.1 | 0.54 | 66.8 | -18.5 | {"2023": -18.2, "2024": 3.9, "2025": 64.1, "2026": 45.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 31.4 | 0.042 | 158.3 | 0.54 | 81.1 | 26.1 | {"2023": -12.1, "2024": 22.6, "2025": 31.6, "2026": 55.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|ACTIVITY | 29.4 | 0.035 | 172.9 | 0.58 | 60.6 | 125.0 | {"2023": -11.4, "2024": 19.3, "2025": 21.9, "2026": 63.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|INFORMATION | 27.9 | 0.036 | 261.4 | 0.56 | 68.0 | -67.6 | {"2023": 1.1, "2024": 28.6, "2025": -3.8, "2026": 72.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 23.8 | 0.030 | 205.3 | 0.54 | -55.4 | -74.9 | {"2023": -2.0, "2024": 15.2, "2025": 63.8, "2026": -4.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| levels|INFORMATION | 23.5 | 0.026 | 317.0 | 0.49 | 4.5 | 9.0 | {"2023": 21.4, "2024": 7.0, "2025": 47.4, "2026": 15.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 21.9 | 0.023 | 193.0 | 0.53 | 66.1 | 27.6 | {"2023": 12.0, "2024": 10.2, "2025": 21.7, "2026": 39.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 21.8 | 0.025 | 339.5 | 0.54 | 32.0 | -30.0 | {"2023": 29.0, "2024": -18.9, "2025": 26.6, "2026": 62.0} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| tape|ACTIVITY | 21.6 | 0.013 | 345.8 | 0.53 | -32.4 | 66.3 | {"2023": -12.1, "2024": 26.4, "2025": 43.1, "2026": 1.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|INFORMATION | 21.4 | 0.021 | 172.9 | 0.58 | 14.7 | -8.0 | {"2023": -16.0, "2024": 33.4, "2025": 23.1, "2026": 17.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | trend.trend_ma_hma.cross | {"len": 13, "width": 3, "hyst": 0.0} | sym30u | both | 7428 | 3631 | 401 | 0.83 | 5 / -601 / 763 / 1.00 | {"2023": 254.0, "2024": -1383.0, "2025": 13.0, "2026": 5811.0} |
| 2 | urenko_14 | book.book_pslope.follow_native | {"L": 1800, "z": 1.0} | plain60/60 | both | 6879 | 4405 | 1062 | 0.75 | 5 / 607 / 2495 / 1.00 | {"2023": 406.0, "2024": 466.0, "2025": -3165.0, "2026": 6685.0} |
| 3 | vol_350 | levels.levels_profile_nodes.break_native | {"n": 2, "k": 0.25} | sym8u | both | 6822 | 2719 | 315 | 1.00 | 25 / -1048 / 2016 / 1.00 | {"2023": -337.0, "2024": 673.0, "2025": 881.0, "2026": 6105.0} |
| 4 | mrenko_14 | book.book_imb.delta_follow | {"lv": 1, "thr": 0.2} | asym20u/10u | both | 6755 | 1461 | 463 | 0.67 | 5 / 276 / 1625 / 1.00 | {"2023": -8.0, "2024": 145.0, "2025": -790.0, "2026": 6225.0} |
| 5 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym15u | both | 6751 | 922 | 421 | 1.00 | 5 / 1088 / 3330 / 1.00 | {"2023": -77.0, "2024": -853.0, "2025": 1402.0, "2026": 4274.0} |
| 6 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | asym15u/30u | both | 6726 | 1912 | 361 | 1.00 | 5 / -1768 / 48 / 1.00 | {"2023": 35.0, "2024": -1811.0, "2025": -37.0, "2026": 5560.0} |
| 7 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | sym30u | both | 6726 | 1912 | 361 | 1.00 | 5 / -1769 / 48 / 1.00 | {"2023": 200.0, "2024": -1629.0, "2025": 358.0, "2026": 5560.0} |
| 8 | tib_1200 | trend.trend_adx_di.adx_cross | {"len": 28, "width": 15} | asym20u/10u | both | 6722 | 3365 | 335 | 1.00 | 5 / -1269 / 852 / 1.00 | {"2023": -605.0, "2024": -765.0, "2025": -1284.0, "2026": 6260.0} |
| 9 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | sym15u | both | 6709 | 1912 | 361 | 1.00 | 5 / -1774 / 48 / 1.00 | {"2023": 18.0, "2024": -1198.0, "2025": 523.0, "2026": 5386.0} |
| 10 | mrenko_14 | book.book_thin.spr_fade | {"w": 2, "i": 0.2} | asym10u/20u | both | 6643 | 3503 | 344 | 1.00 | 3 / -1373 / 510 / 1.00 | {"2023": 289.0, "2024": 1057.0, "2025": 623.0, "2026": 6124.0} |
| 11 | tib_240 | barnative.barnative_run.fade | {"n": 6} | sym30u | both | 6625 | 1797 | 384 | 1.00 | 5 / -28 / 1297 / 1.00 | {"2023": 28.0, "2024": -2037.0, "2025": 970.0, "2026": 4953.0} |
| 12 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | sym15u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 263.0, "2024": 1748.0, "2025": 223.0, "2026": 4461.0} |
| 13 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | sym30u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 229.0, "2024": 1726.0, "2025": 223.0, "2026": 4461.0} |
| 14 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym15u/30u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 223.0, "2024": 1748.0, "2025": 223.0, "2026": 4461.0} |
| 15 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym20u/10u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 154.0, "2024": 1956.0, "2025": 393.0, "2026": 4461.0} |
| 16 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym10u/20u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 235.0, "2024": 1394.0, "2025": 355.0, "2026": 4461.0} |
| 17 | vsess_80 | tape.tape_stack.r3_fade | {"k": 3} | sym15u | both | 6583 | 2943 | 415 | 1.00 | 5 / -966 / 216 / 1.00 | {"2023": -264.0, "2024": 444.0, "2025": -14.0, "2026": 7725.0} |
| 18 | trb_400 | bands.bands_atrchan.fade_ext | {"n": 40, "atr": 14, "k": 4.0} | sym15u | both | 6579 | 1893 | 293 | 1.00 | 5 / 194 / 2203 / 1.00 | {"2023": -573.0, "2024": 764.0, "2025": 713.0, "2026": 6673.0} |
| 19 | mrenko_14 | book.book_micro.fade_sm | {"L": 200, "z": 1.0, "sm": 3} | sym15u | both | 6571 | 3280 | 358 | 1.00 | 4 / 480 / 4271 / 1.00 | {"2023": 168.0, "2024": -1060.0, "2025": -3294.0, "2026": 6657.0} |
| 20 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | asym15u/30u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 585.0, "2024": 1361.0, "2025": 764.0, "2026": 4491.0} |

## Exit families (second result column; stage a2, screen-level): flip study and best exit family
Flip study (random 2% sample of pass-1 cells, capped): cells negative on EVERY fixed bracket that become positive with their best of 68 exit specs. A best-of-68 pick is biased upward: read it against the null3 sample / random-entry nulls (null_pctile in the candidates table), not as a gain.
| session | cells | negative on every fixed bracket | flipped positive with an exit family |
|---|---|---|---|
| Asia | 73 | 29 | 28 |
| London | 74 | 29 | 23 |
| NYAM | 70 | 21 | 19 |
| NYPM | 73 | 20 | 15 |
| session | best exit family | cells | mean exit L6M (pts) | mean gain vs best fixed bracket |
|---|---|---|---|---|
| Asia | market target | 386 | 1499 | -932 |
| Asia | order flow | 1 | 18 | 176 |
| Asia | staged | 40 | 1773 | -42 |
| Asia | stop-and-reverse | 19 | 2115 | 93 |
| Asia | structure stop | 5 | 933 | 597 |
| Asia | time / behaviour | 156 | 1850 | -487 |
| Asia | trailing | 200 | 1949 | 244 |
| London | market target | 527 | 1128 | -1217 |
| London | order flow | 15 | -44 | 442 |
| London | staged | 56 | 1783 | -362 |
| London | stop-and-reverse | 16 | 1101 | -274 |
| London | structure stop | 3 | 1139 | -52 |
| London | time / behaviour | 129 | 1212 | -850 |
| London | trailing | 117 | 1466 | -1061 |
| NYAM | market target | 240 | 1404 | -1226 |
| NYAM | order flow | 8 | 466 | 716 |
| NYAM | staged | 20 | 1640 | 270 |
| NYAM | stop-and-reverse | 37 | 2269 | -472 |
| NYAM | structure stop | 15 | 1550 | 677 |
| NYAM | time / behaviour | 382 | 1990 | -807 |
| NYAM | trailing | 124 | 1881 | 482 |
| NYPM | market target | 495 | 1767 | -234 |
| NYPM | order flow | 9 | 115 | 500 |
| NYPM | staged | 32 | 1586 | 58 |
| NYPM | stop-and-reverse | 10 | 2575 | 200 |
| NYPM | structure stop | 7 | 1172 | 133 |
| NYPM | time / behaviour | 145 | 1250 | -638 |
| NYPM | trailing | 100 | 1574 | -97 |
Family 6 (order-flow exits) by component, candidate + live-seven + book/tape cells: best flow spec vs the cell best fixed bracket / best non-flow exit
| session | component | cells | mean best flow-spec L6M (pts) | share beating best fixed bracket | share beating best exit |
|---|---|---|---|---|---|
| Asia | absorb | 210 | -1851 | 0.06 | 0.00 |
| Asia | book | 210 | -2417 | 0.02 | 0.00 |
| Asia | delta | 210 | -2747 | 0.04 | 0.00 |
| Asia | speed | 210 | -2284 | 0.03 | 0.00 |
| Asia | wall | 210 | -2394 | 0.04 | 0.00 |
| London | absorb | 214 | -1952 | 0.07 | 0.00 |
| London | book | 214 | -2242 | 0.06 | 0.00 |
| London | delta | 214 | -2408 | 0.05 | 0.00 |
| London | speed | 214 | -2248 | 0.06 | 0.00 |
| London | wall | 214 | -2380 | 0.05 | 0.01 |
| NYAM | absorb | 224 | -3389 | 0.11 | 0.00 |
| NYAM | book | 224 | -3363 | 0.13 | 0.00 |
| NYAM | delta | 224 | -3563 | 0.17 | 0.00 |
| NYAM | speed | 224 | -2918 | 0.18 | 0.02 |
| NYAM | wall | 224 | -3021 | 0.15 | 0.01 |
| NYPM | absorb | 200 | -2809 | 0.14 | 0.00 |
| NYPM | book | 200 | -2992 | 0.12 | 0.00 |
| NYPM | delta | 201 | -3709 | 0.11 | 0.00 |
| NYPM | speed | 200 | -2824 | 0.12 | 0.01 |
| NYPM | wall | 200 | -3266 | 0.12 | 0.00 |

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
| Asia | M7 | tm45 | neighbour | 49.4 | 102.7 | 29.0 | 480.3 | 0.65 | 697 | 0.94 |  |
| Asia | M7 | tm120 | neighbour | 130.5 | 160.7 | 34.4 | 344.2 | 0.59 | 438 | 1.00 |  |
| Asia | M7 | tm180 | neighbour | 50.4 | 113.2 | 25.0 | 304.0 | 0.59 | 339 | 0.95 |  |
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.90 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.39 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.88 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.11 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.24 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.97 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.92 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.47 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.14 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.84 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.86 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.87 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.92 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.66 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.43 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.32 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.82 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.89 |  |
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.08 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.40 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.12 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.10 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.83 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.84 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.61 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.33 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.03 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.78 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.78 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.26 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 0.99 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.94 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.89 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.62 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.57 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.29 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.63 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.57 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.79 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.19 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.17 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.83 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.76 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.07 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.19 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.26 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.06 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.77 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.45 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.06 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.12 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.11 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.46 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.42 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.42 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.56 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.69 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.46 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.11 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.05 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.05 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.11 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.85 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.87 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.76 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.87 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.62 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.36 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.13 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.20 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.77 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.73 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.76 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.70 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.76 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.39 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.35 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.25 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.04 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.84 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.18 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.07 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.16 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.23 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.30 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.79 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.18 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.61 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.34 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.68 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.27 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.34 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.16 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.07 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.12 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.24 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.15 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.27 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.27 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.50 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.29 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.60 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.18 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.15 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.11 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.31 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.59 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell urenko_10 momentum.momentum_stoch.zone_break_native asym15u/30u L6M 250.5 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell pnf_5 book.book_cancel.ratio_follow asym20u/10u L6M 368.6 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell time_m_1 book.book_cancel.canc_follow sym8u L6M 283.3 pts/wk vs weak baselines K7 -22.5
## LEVEL triggers per session (supply/demand first, then Fibonacci, pivots, swing S/R, level stack, others): best cell per (module, variant) over all bar rows / parameters / brackets, last 26 weeks, >= 30 trades, in-sample pick: a LEAD needs the candidates-table nulls
### London (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | urenko_56 | {"n": 1, "F": 2} | sym8u / both | 32 | 694 | -279 | -907 | 16 | 278 | 2 | 358 |
| sd5 | break_native | urenko_56 | {"n": 1, "F": 2} | sym8u / both | 32 | 694 | -279 | -907 | 16 | 278 | 2 | 358 |
| sd5 | reject | entropy_B200 | {"F": 0, "D": 15, "tol": 0.0} | sym15u / both | 33 | 900 | -59 | -353 | -551 | 1202 | 1 | 358 |
| sd5 | reject_flow | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 358 |
| sd5 | reject_flow_native | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 358 |
| sd5 | reject_native | mrenko_14 | {"F": 2, "D": 15, "tol": 0.5} | asym10u/20u / both | 40 | 1014 | 209 | 45 | -119 | 1147 | 2 | 358 |
| sdx15 | break | kagi_80 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 140 | 2579 | 645 | -535 | -454 | 2325 | 1 | 359 |
| sdx15 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 195 | 2214 | 105 | -102 | 862 | 1176 | 1 | 359 |
| sdx15 | lim_prox | kagi_112 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 156 | 1722 | -776 | 900 | -2080 | 1504 | 1 | 359 |
| sdx15 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 158 | 1967 | -30 | 572 | 2203 | 2707 | 1 | 359 |
| sdx15 | rej_flow | vnorm_150 | {"d": "A", "F": 0} | sym15u / long | 34 | 1073 | -32 | 242 | 645 | 1075 | 1 | 359 |
| sdx15 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 359 |
| sdx15 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 359 |
| sdx15 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 73 | 1895 | -252 | -737 | -146 | 1593 | 1 | 359 |
| sdx3 | break | vnorm_150 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 209 | 3117 | 98 | -196 | -24 | 3447 | 1 | 359 |
| sdx3 | lim_mid | kagi_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 276 | 3690 | 400 | 1269 | -2651 | 4082 | 1 | 359 |
| sdx3 | lim_prox | mrenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 355 | 3462 | -57 | 2000 | -1269 | 1812 | 1 | 359 |
| sdx3 | rej | vrb_240 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 293 | 2490 | 568 | 801 | -2604 | 2253 | 1 | 359 |
| sdx3 | rej_flow | vib_2000 | {"d": "A", "F": 0} | sym15u / both | 185 | 1480 | 1193 | -1298 | -1838 | 2162 | 1 | 359 |
| sdx3 | rej_native | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 245 | 3620 | 859 | 1354 | 441 | 3653 | 1 | 359 |
| sdx3 | rej_zone | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 219 | 3956 | 1228 | 1976 | -779 | 5574 | 1 | 359 |
| sdx3 | retest | vnorm_150 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 159 | 1978 | 276 | -1447 | -740 | 1886 | 1 | 359 |
| sdx30 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 75 | 1445 | 411 | -743 | -552 | 1630 | 1 | 359 |
| sdx30 | lim_mid | vnorm_150 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 112 | 2283 | 77 | 525 | 809 | 1658 | 1 | 359 |
| sdx30 | lim_prox | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 228 | 3089 | -6 | 17 | 1634 | 3464 | 1 | 359 |
| sdx30 | rej | vfp_t5m | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 94 | 933 | 675 | -904 | -456 | 1059 | 1 | 359 |
| sdx30 | rej_flow | dol_350 | {"d": "A", "F": 0} | sym15u / both | 31 | 595 | 340 | 318 | -802 | 812 | 1 | 359 |
| sdx30 | rej_native | vfp_t5m | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 123 | 1886 | 872 | -405 | 317 | 1591 | 1 | 359 |
| sdx30 | rej_zone | time_m_45 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 130 | 2103 | -471 | -5 | -430 | 2659 | 1 | 359 |
| sdx30 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 30 | 255 | -23 | 87 | -248 | -102 | 1 | 359 |
| sdx5 | break | volor_B500 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 206 | 3514 | 516 | 1174 | 2114 | 856 | 1 | 359 |
| sdx5 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 214 | 2364 | 118 | 1141 | -997 | 2486 | 1 | 359 |
| sdx5 | lim_prox | vrb_400 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 584 | 2703 | -466 | -813 | 2051 | 3816 | 1 | 359 |
| sdx5 | rej | vrb_700 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 216 | 2671 | -193 | -1603 | 1240 | 2253 | 1 | 359 |
| sdx5 | rej_flow | vfp_vol1000 | {"d": "A", "F": 0} | sym15u / both | 115 | 2098 | 859 | 978 | 26 | 1907 | 1 | 359 |
| sdx5 | rej_native | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 155 | 2126 | -203 | -436 | 139 | 981 | 1 | 359 |
| sdx5 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 102 | 1959 | 163 | 674 | -953 | 2077 | 1 | 359 |
| sdx5 | retest | kagi_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 156 | 3004 | -581 | -1198 | -562 | 1728 | 1 | 359 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 46 | 1187 | -206 | 30 | 92 | 1265 | 1 | 359 |
| sdx60 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 162 | 2417 | -215 | 125 | -1666 | 2534 | 1 | 359 |
| sdx60 | lim_prox | dol_6000 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 43 | 1665 | -258 | -544 | 57 | 2252 | 1 | 359 |
| sdx60 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 32 | 1124 | -130 | -222 | -19 | 853 | 1 | 359 |
| sdx60 | rej_flow | vfp_vol2500 | {"d": "E", "F": 9} | plain60/60 / both | 61 | 583 | 30 | 253 | 52 | 412 | 1 | 359 |
| sdx60 | rej_native | vnorm_150 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 57 | 1273 | -150 | 571 | 127 | 787 | 1 | 359 |
| sdx60 | rej_zone | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 62 | 2668 | -308 | -306 | -20 | 2502 | 2 | 359 |
| sdx_renko28 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 144 | 2263 | -119 | -618 | -1891 | 1174 | 1 | 359 |
| sdx_renko28 | lim_mid | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 157 | 2991 | -88 | -812 | -829 | 2811 | 1 | 359 |
| sdx_renko28 | lim_prox | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 156 | 3623 | -359 | -657 | -693 | 3375 | 1 | 359 |
| sdx_renko28 | rej | vrb_400 | {"d": "B", "F": 0, "tol": 0.5} | plain60/60 / both | 104 | 1060 | -479 | 152 | 1216 | 187 | 1 | 359 |
| sdx_renko28 | rej_flow | vfp_t5m | {"d": "E", "F": 0} | sym15u / both | 100 | 689 | -79 | -709 | 1424 | 1917 | 1 | 359 |
| sdx_renko28 | rej_native | volor_B030 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 242 | 1771 | -220 | -632 | -654 | 1032 | 1 | 359 |
| sdx_renko28 | rej_zone | vnorm_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 169 | 2921 | -147 | -117 | 1565 | 3866 | 1 | 359 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 183 | 1714 | 157 | -621 | -488 | 47 | 1 | 359 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 359 |
| sdx_rng28 | lim_mid | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 795 | 3282 | -633 | 132 | -4220 | 3878 | 1 | 359 |
| sdx_rng28 | lim_prox | mrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 749 | 2352 | -897 | 2558 | -1185 | 4098 | 1 | 359 |
| sdx_rng28 | rej | kagi_56 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 93 | 1361 | 603 | 353 | -205 | 971 | 1 | 359 |
| sdx_rng28 | rej_flow | vrb_700 | {"d": "E", "F": 0} | plain60/60 / both | 304 | 1173 | 22 | 186 | 46 | 1250 | 1 | 359 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 359 |
| sdx_rng28 | rej_zone | vnorm_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 179 | 3114 | -352 | -595 | 153 | 3357 | 1 | 359 |
| sdx_rng28 | retest | kagi_80 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 197 | 2393 | -337 | 390 | -2202 | 908 | 1 | 359 |
| sdx_vol1100 | break | frenko_28 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 2638 | -348 | -213 | 189 | 2953 | 1 | 359 |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 209 | 3784 | 896 | 457 | 888 | 4785 | 1 | 359 |
| sdx_vol1100 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 244 | 3123 | 198 | -474 | 859 | 3530 | 1 | 359 |
| sdx_vol1100 | rej | volor_B500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 322 | 1557 | 668 | 379 | 1376 | 2062 | 1 | 359 |
| sdx_vol1100 | rej_flow | volor_B500 | {"d": "E", "F": 0} | sym15u / both | 176 | 1646 | 190 | -179 | -1010 | 2417 | 1 | 359 |
| sdx_vol1100 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 359 |
| sdx_vol1100 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 359 |
| sdx_vol1100 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 112 | 1778 | -246 | -234 | -609 | 1473 | 1 | 359 |
| fib15 | break | pnf_5 | {"n": 3, "k": 0.5} | sym8u / both | 288 | 4201 | -619 | -2233 | -1116 | 4287 | 2 | 359 |
| fib15 | break_native | swing_atr_0.15 | {"n": 2, "k": 0.25} | sym15u / both | 241 | 3875 | -629 | -511 | 2215 | 4625 | 1 | 359 |
| fib15 | false_break | dchg_56 | {"M": 3, "k": 0.5} | sym15u / both | 243 | 4145 | 434 | 267 | -571 | 3261 | 1 | 359 |
| fib15 | false_break_native | dchg_56 | {"M": 1, "k": 0.0} | sym15u / both | 243 | 3977 | 403 | 295 | -878 | 3409 | 1 | 359 |
| fib15 | pullback | tsf_10_30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 146 | 1994 | 210 | 313 | -1254 | 2290 | 1 | 359 |
| fib15 | pullback_native | tsf_10_30 | {"tol": 0.5, "conf": "body"} | sym15u / both | 160 | 2562 | 527 | 71 | 107 | 2897 | 1 | 359 |
| fib15 | reject | vrb_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 204 | 4032 | 109 | 80 | 979 | 6002 | 1 | 359 |
| fib15 | reject_native | urenko_10 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 277 | 4378 | 246 | -820 | 694 | 6291 | 2 | 359 |
| fib15 | retest | tib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 215 | 3026 | 594 | -427 | -629 | 2938 | 1 | 359 |
| fib15 | retest_native | tib_3500 | {"M": 3, "tol": 0.0} | sym15u / both | 204 | 2963 | 937 | 328 | -1139 | 1614 | 1 | 359 |
| fib5 | break | entropy_B130 | {"n": 1, "k": 0.0} | sym15u / both | 262 | 2770 | -1307 | 1484 | -335 | 2778 | 1 | 359 |
| fib5 | break_native | trb_3500 | {"n": 2, "k": 0.25} | sym15u / both | 221 | 2984 | -125 | -737 | 2280 | 2984 | 1 | 359 |
| fib5 | false_break | dchg_80 | {"M": 2, "k": 0.5} | sym15u / both | 215 | 3386 | 719 | 315 | -1355 | 3421 | 1 | 359 |
| fib5 | false_break_native | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 232 | 3243 | 1008 | -540 | 1443 | 3077 | 1 | 359 |
| fib5 | pullback | dol_2600 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 2572 | -11 | -107 | 971 | 3053 | 1 | 359 |
| fib5 | pullback_native | lbrk_5_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 199 | 2218 | 689 | 627 | -142 | 2266 | 1 | 359 |
| fib5 | reject | cusum_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3943 | -37 | -55 | 1500 | 4956 | 1 | 359 |
| fib5 | reject_native | cusum_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3849 | -85 | 719 | -430 | 3661 | 1 | 359 |
| fib5 | retest | entropy_B320 | {"M": 10, "tol": 0.5} | sym15u / both | 262 | 3406 | 265 | 1097 | 465 | 2883 | 1 | 359 |
| fib5 | retest_native | tm2700 | {"M": 10, "tol": 0.5} | sym15u / both | 231 | 3970 | -348 | 302 | 2508 | 3180 | 1 | 359 |
| fib60 | break | urenko_10 | {"n": 2, "k": 0.0} | asym15u/30u / both | 219 | 3359 | 339 | -1093 | 322 | 3865 | 2 | 359 |
| fib60 | break_native | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 239 | 3697 | -809 | -1703 | -422 | 3980 | 1 | 359 |
| fib60 | false_break | kagi_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 222 | 3269 | 330 | 1054 | -527 | 4521 | 2 | 359 |
| fib60 | false_break_native | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2893 | 639 | 1418 | -423 | 3303 | 1 | 359 |
| fib60 | pullback | tsf_25_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 64 | 1454 | -594 | -222 | 755 | 1483 | 1 | 359 |
| fib60 | pullback_native | trend_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 124 | 1824 | 223 | -126 | -1859 | -12 | 1 | 359 |
| fib60 | reject | vib_1200 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 441 | 2856 | -318 | -1663 | 309 | 2863 | 1 | 359 |
| fib60 | reject_native | dltor_B050 | {"tol": 0.5, "conf": "body"} | sym15u / both | 188 | 3256 | 434 | -472 | -3792 | 3416 | 1 | 359 |
| fib60 | retest | vsess_300 | {"M": 3, "tol": 0.0} | sym15u / both | 179 | 3386 | -443 | -174 | -2425 | 996 | 1 | 359 |
| fib60 | retest_native | dchg_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 3614 | -723 | 596 | -705 | 4775 | 1 | 359 |
| fibr_dev | break | tm3600 | {"n": 1, "k": 0.0} | sym15u / both | 202 | 3411 | -301 | -3018 | -885 | 3990 | 1 | 359 |
| fibr_dev | break_native | tm3600 | {"n": 1, "k": 0.0} | sym15u / both | 202 | 3411 | -252 | -3018 | -885 | 3990 | 1 | 359 |
| fibr_dev | false_break | rng_14 | {"M": 2, "k": 0.0} | plain60/60 / both | 664 | 3275 | 147 | 840 | -915 | 2372 | 2 | 359 |
| fibr_dev | false_break_native | rng_14 | {"M": 2, "k": 0.0} | plain60/60 / both | 664 | 3275 | 147 | 840 | -915 | 2372 | 2 | 359 |
| fibr_dev | reject | rng_40 | {"tol": 0.0, "conf": "close"} | sym8u / both | 238 | 3876 | -228 | 278 | 379 | 3560 | 2 | 359 |
| fibr_dev | reject_native | tm180 | {"tol": 1.0, "conf": "close"} | sym30u / both | 268 | 4128 | 954 | -593 | -59 | 4838 | 2 | 359 |
| fibr_dev | retest | vib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 623 | 3322 | 130 | 1241 | -198 | 2311 | 1 | 359 |
| fibr_dev | retest_native | dib_1200 | {"M": 10, "tol": 0.5} | plain60/60 / both | 651 | 4022 | 430 | 1105 | -649 | 3133 | 1 | 359 |
| fibr_ib | break | volor_B500 | {"n": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1616 | 149 | 1 | 90 |
| fibr_ib | break_native | volor_B500 | {"n": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1616 | 149 | 1 | 90 |
| fibr_ib | false_break | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1563 | 149 | 1 | 90 |
| fibr_ib | false_break_native | dltor_B130 | {"M": 3, "k": 0.5} | sym15u / both | 95 | 1106 | -847 | 576 | 393 | 556 | 1 | 90 |
| fibr_ib | reject | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 45 | 742 | 532 | -814 | 411 | 633 | 1 | 90 |
| fibr_ib | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 47 | 963 | 1255 | -152 | -897 | 648 | 1 | 90 |
| fibr_ib | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 44 | 430 | -86 | -239 | 291 | 428 | 1 | 90 |
| fibr_ib | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 52 | 491 | -44 | -256 | 352 | 478 | 1 | 90 |
| fibr_on | break | vfp_vol2500 | {"n": 1, "k": 0.0} | sym15u / both | 84 | 1874 | -164 | 425 | 630 | 910 | 1 | 90 |
| fibr_on | break_native | vfp_vol2500 | {"n": 1, "k": 0.0} | sym15u / both | 84 | 1874 | -164 | 425 | 630 | 910 | 1 | 90 |
| fibr_on | false_break | vfp_vol2500 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1874 | -171 | 614 | 670 | 1031 | 1 | 90 |
| fibr_on | false_break_native | vfp_vol2500 | {"M": 2, "k": 0.5} | sym15u / both | 77 | 2214 | -355 | 416 | 779 | 1250 | 1 | 90 |
| fibr_on | reject | anch_L0200_B10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 36 | 250 | -55 | 157 | -259 | 211 | 1 | 90 |
| fibr_on | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 49 | 936 | 789 | -652 | -597 | 848 | 1 | 90 |
| fibr_on | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 36 | 504 | 55 | -170 | 165 | 149 | 1 | 90 |
| fibr_on | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 44 | 356 | 80 | -284 | 96 | 211 | 1 | 90 |
| fibr_or | break | vfp_vol2500 | {"n": 1, "k": 0.0} | sym15u / long | 45 | 1059 | -104 | 870 | 866 | 456 | 1 | 90 |
| fibr_or | break_native | vfp_vol2500 | {"n": 1, "k": 0.0} | sym15u / long | 45 | 1059 | -104 | 870 | 866 | 456 | 1 | 90 |
| fibr_or | false_break | vfp_vol2500 | {"M": 1, "k": 0.0} | sym15u / long | 45 | 1059 | -104 | 870 | 866 | 456 | 1 | 90 |
| fibr_or | false_break_native | vfp_vol2500 | {"M": 1, "k": 0.0} | sym15u / long | 45 | 1059 | -104 | 870 | 866 | 456 | 1 | 90 |
| fibr_or | reject | tpo_30m | {"tol": 0.5, "conf": "body"} | sym15u / both | 31 | 1032 | 508 | 85 | -339 | 1621 | 1 | 90 |
| fibr_or | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 43 | 1681 | 973 | 147 | -513 | 1666 | 1 | 90 |
| fibr_or | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 41 | 416 | -13 | -330 | 136 | 203 | 1 | 90 |
| fibr_or | retest_native | anch_L0200_B10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 36 | 477 | -37 | -292 | 40 | 245 | 1 | 90 |
| fibr_pd | break | tm240 | {"n": 3, "k": 0.5} | sym15u / both | 186 | 3753 | 257 | -4 | -1554 | 3468 | 1 | 359 |
| fibr_pd | break_native | tib_6000 | {"n": 3, "k": 0.5} | sym15u / both | 185 | 3419 | -502 | -354 | -1620 | 3200 | 1 | 359 |
| fibr_pd | false_break | vfp_rng16 | {"M": 1, "k": 0.0} | sym15u / both | 448 | 2964 | -383 | -233 | -993 | 1916 | 1 | 359 |
| fibr_pd | false_break_native | volor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 260 | 3280 | -780 | 77 | 1451 | 2750 | 1 | 359 |
| fibr_pd | reject | time_m_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 182 | 3343 | -167 | 28 | -1101 | 2457 | 1 | 359 |
| fibr_pd | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym15u / both | 234 | 4770 | -455 | 305 | -2654 | 3740 | 1 | 359 |
| fibr_pd | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 182 | 3224 | -483 | -1970 | 1308 | 3292 | 1 | 359 |
| fibr_pd | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 182 | 3224 | -483 | -1970 | 1308 | 3292 | 1 | 359 |
| piv_cama | break | tm780 | {"n": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -904 | -1274 | 1697 | 1 | 359 |
| piv_cama | break_native | tm780 | {"n": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -904 | -1274 | 1697 | 1 | 359 |
| piv_cama | false_break | tm780 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -778 | -1274 | 1600 | 1 | 359 |
| piv_cama | false_break_native | tm780 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -778 | -1274 | 1600 | 1 | 359 |
| piv_cama | reject | trb_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 149 | 2757 | -307 | -952 | -146 | 3434 | 1 | 359 |
| piv_cama | reject_native | vnorm_150 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 577 | 4012 | -191 | -1152 | -1087 | 4672 | 1 | 359 |
| piv_cama | retest | dchg_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3132 | -573 | 297 | 2088 | 1823 | 1 | 359 |
| piv_cama | retest_native | renko_20 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 187 | 3306 | -823 | 102 | -483 | 2289 | 2 | 359 |
| piv_floor | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 159 | 3362 | 14 | -442 | -2052 | 4155 | 1 | 359 |
| piv_floor | break_native | sessrng_B050 | {"n": 3, "k": 0.5} | sym15u / both | 216 | 3570 | -953 | 185 | 639 | 2916 | 1 | 359 |
| piv_floor | false_break | pasl_14 | {"M": 2, "k": 0.5} | sym15u / both | 203 | 3561 | -443 | -1227 | -389 | 4694 | 2 | 359 |
| piv_floor | false_break_native | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 195 | 3732 | -551 | -1934 | -1135 | 5263 | 1 | 359 |
| piv_floor | reject | vrb_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 163 | 2394 | 666 | 286 | -937 | 3218 | 1 | 359 |
| piv_floor | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 219 | 3389 | 177 | 449 | -550 | 3714 | 1 | 359 |
| piv_floor | retest | kagi_14 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 169 | 3970 | 252 | -952 | -637 | 3561 | 2 | 359 |
| piv_floor | retest_native | kagi_14 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 169 | 3970 | 252 | -952 | -637 | 3561 | 2 | 359 |
| piv_wf | break | time_m_13 | {"n": 3, "k": 0.5} | sym15u / both | 181 | 4213 | -1022 | -1316 | -385 | 3980 | 1 | 359 |
| piv_wf | break_native | pasl_14 | {"n": 2, "k": 0.5} | sym15u / both | 200 | 3595 | -50 | -327 | 1 | 3781 | 2 | 359 |
| piv_wf | false_break | entropy_B320 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3639 | -129 | 115 | -1911 | 1725 | 1 | 359 |
| piv_wf | false_break_native | entropy_B320 | {"M": 2, "k": 0.5} | sym15u / both | 243 | 3898 | -139 | 18 | -1695 | 2281 | 1 | 359 |
| piv_wf | reject | tick_2000 | {"tol": 0.0, "conf": "close"} | sym8u / both | 186 | 3393 | -160 | 815 | 1052 | 2237 | 2 | 359 |
| piv_wf | reject_native | vol_2600 | {"tol": 1.0, "conf": "close"} | sym8u / both | 233 | 3793 | 11 | 1257 | 183 | 3247 | 2 | 359 |
| piv_wf | retest | entropy_B200 | {"M": 3, "tol": 0.0} | sym15u / both | 194 | 2651 | -208 | -737 | -2974 | -25 | 1 | 359 |
| piv_wf | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 180 | 3612 | 618 | -634 | -723 | 4764 | 1 | 359 |
| swcluster | break | tpo_30m | {"n": 2, "k": 0.25} | sym15u / both | 59 | 1755 | 23 | 316 | -2 | 1564 | 1 | 360 |
| swcluster | break_native | time_m_1 | {"n": 1, "k": 0.5} | asym15u/30u / both | 51 | 1763 | -747 | 486 | 31 | 1800 | 2 | 360 |
| swcluster | false_break | swing_pct_20 | {"M": 2, "k": 0.5} | sym15u / both | 76 | 1820 | 75 | -944 | -705 | 1157 | 1 | 360 |
| swcluster | false_break_native | swing_pct_20 | {"M": 1, "k": 0.0} | sym15u / both | 75 | 1813 | 75 | -944 | -585 | 1149 | 1 | 360 |
| swcluster | reject | vol_1100 | {"tol": 1.0, "conf": "body"} | sym8u / both | 49 | 1735 | -451 | -219 | -223 | 1906 | 2 | 360 |
| swcluster | reject_native | tm3600 | {"tol": 1.0, "conf": "body"} | sym15u / both | 75 | 2174 | -228 | -430 | -145 | 2452 | 1 | 360 |
| swcluster | retest | vfp_vol1000 | {"M": 6, "tol": 0.5} | sym15u / both | 39 | 1668 | 261 | -71 | -578 | 1803 | 1 | 360 |
| swcluster | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 51 | 1708 | 238 | 94 | -774 | 1926 | 1 | 360 |
| swsr15 | break | tm180 | {"n": 2, "k": 0.25} | sym15u / both | 236 | 3948 | -36 | -443 | 1132 | 5269 | 1 | 360 |
| swsr15 | break_native | sessrng_B200 | {"n": 3, "k": 0.5} | sym15u / both | 250 | 3789 | -863 | 393 | 182 | 4067 | 1 | 360 |
| swsr15 | false_break | tm1800 | {"M": 3, "k": 0.5} | sym15u / both | 224 | 2590 | 871 | -57 | 1236 | 4286 | 1 | 360 |
| swsr15 | false_break_native | swing_atr_0.9 | {"M": 2, "k": 0.5} | sym15u / both | 210 | 2709 | 664 | -442 | -1328 | 1568 | 1 | 360 |
| swsr15 | reject | dlt_150 | {"tol": 0.0, "conf": "close"} | sym15u / both | 190 | 3961 | -158 | 603 | -157 | 6111 | 1 | 360 |
| swsr15 | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | sym15u / both | 236 | 4580 | 111 | 166 | -1960 | 5125 | 1 | 360 |
| swsr15 | retest | time_m_4 | {"M": 10, "tol": 0.5} | sym15u / both | 207 | 3437 | 341 | -341 | -609 | 2002 | 1 | 360 |
| swsr15 | retest_native | cusum_56 | {"M": 10, "tol": 0.5} | sym15u / both | 224 | 3304 | -601 | -765 | 1414 | 2444 | 1 | 360 |
| swsr5 | break | tm1800 | {"n": 3, "k": 0.5} | sym15u / both | 202 | 3957 | -250 | -300 | -1697 | 2972 | 1 | 359 |
| swsr5 | break_native | pasl_14 | {"n": 3, "k": 0.5} | asym10u/20u / both | 238 | 3201 | -72 | -1037 | -1784 | 3184 | 2 | 359 |
| swsr5 | false_break | rng_10 | {"M": 2, "k": 0.0} | asym20u/10u / both | 436 | 2677 | 83 | -1203 | -1141 | 1317 | 2 | 359 |
| swsr5 | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 309 | 2937 | -542 | 872 | -140 | 2896 | 2 | 359 |
| swsr5 | reject | vnorm_700 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 609 | 2674 | 459 | -255 | 90 | 3729 | 1 | 359 |
| swsr5 | reject_native | vib_15000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 232 | 3646 | 239 | 1058 | 2008 | 3609 | 1 | 359 |
| swsr5 | retest | tib_1200 | {"M": 3, "tol": 0.0} | plain60/60 / both | 550 | 3553 | 1346 | -972 | -590 | 3478 | 1 | 359 |
| swsr5 | retest_native | tib_1200 | {"M": 3, "tol": 0.0} | plain60/60 / both | 550 | 3553 | 1346 | -972 | -590 | 3478 | 1 | 359 |
| swsr60 | break | tm1200 | {"n": 3, "k": 0.5} | sym15u / both | 155 | 3042 | -320 | -1598 | -700 | 3353 | 1 | 359 |
| swsr60 | break_native | entropy_B030 | {"n": 2, "k": 0.25} | sym15u / both | 189 | 2885 | -1387 | -586 | 2620 | 2510 | 1 | 359 |
| swsr60 | false_break | tm1800 | {"M": 3, "k": 0.5} | sym15u / both | 147 | 2707 | 194 | -307 | -200 | 4178 | 1 | 359 |
| swsr60 | false_break_native | rng_56 | {"M": 1, "k": 0.5} | sym8u / both | 138 | 2828 | 107 | 255 | 1610 | 3444 | 2 | 359 |
| swsr60 | reject | vib_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 138 | 2627 | -204 | -1067 | 651 | 1457 | 1 | 359 |
| swsr60 | reject_native | vol_500 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 191 | 3184 | -1017 | -2263 | 1121 | 2705 | 2 | 359 |
| swsr60 | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 151 | 2343 | 682 | -890 | 85 | 4105 | 1 | 359 |
| swsr60 | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 196 | 2660 | -428 | 211 | -803 | 3281 | 1 | 359 |
| stack | break | swing_pct_5 | {"k": 3, "cw": 1.0} | sym15u / both | 146 | 3658 | 150 | 1374 | -1383 | 2692 | 1 | 360 |
| stack | break_native | trb_3500 | {"k": 2, "cw": 0.5} | sym15u / both | 177 | 3483 | 500 | -928 | -2461 | 5932 | 1 | 360 |
| stack | reject | urenko_28 | {"k": 2, "cw": 2.0} | sym8u / both | 173 | 3206 | 785 | 399 | 25 | 3385 | 2 | 360 |
| stack | reject_native | rngor_B050 | {"k": 3, "cw": 1.0} | sym15u / both | 243 | 4621 | 305 | 261 | 353 | 4855 | 1 | 360 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 50 | 1289 | -272 | -1504 | -9 | 988 | 1 | 355 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 50 | 1289 | -272 | -1504 | -9 | 988 | 1 | 355 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 355 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 355 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 355 |
| book_walls | reject_native | volor_B320 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 68 | 1320 | 743 | -827 | -593 | 1228 | 1 | 355 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 355 |
| book_walls | retest_native | vsess_600 | {"M": 3, "tol": 0.5} | sym15u / both | 31 | 948 | -210 | -159 | 387 | 775 | 2 | 355 |
| book_walls_loose | break | tm60 | {"n": 1, "k": 0.5} | asym20u/10u / both | 183 | 3236 | -198 | -2781 | -228 | 2860 | 2 | 357 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.25} | asym20u/10u / both | 183 | 3094 | -1657 | -1003 | -262 | 2925 | 2 | 357 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 255 | 1836 | -1493 | 606 | -1053 | 1533 | 1 | 357 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 255 | 1836 | -1493 | 606 | -1053 | 1533 | 1 | 357 |
| book_walls_loose | reject | vib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 182 | 4393 | -631 | 670 | -1174 | 4438 | 1 | 357 |
| book_walls_loose | reject_native | vib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 222 | 4062 | -115 | 655 | -1969 | 4447 | 1 | 357 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 3593 | 15 | -764 | -863 | 4117 | 1 | 357 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3442 | -152 | -1165 | 168 | 4113 | 1 | 357 |
| channel | break | urenko_20 | {"n": 2, "k": 0.5} | sym15u / both | 252 | 3809 | -719 | -923 | 1234 | 5553 | 2 | 359 |
| channel | break_native | tib_3500 | {"n": 2, "k": 0.25} | sym15u / both | 242 | 4938 | 1342 | 691 | -1153 | 4270 | 1 | 359 |
| channel | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 172 | 2912 | -145 | -287 | -2232 | 2997 | 1 | 359 |
| channel | false_break_native | dchg_80 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3347 | 377 | 1744 | 1107 | 4645 | 1 | 359 |
| channel | reject | drb_400 | {"tol": 1.0, "conf": "close"} | sym8u / both | 339 | 4166 | -730 | -2386 | -1372 | 5930 | 2 | 359 |
| channel | reject_native | drb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 265 | 5291 | -476 | 768 | 36 | 3512 | 1 | 359 |
| channel | retest | drb_400 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 245 | 4178 | 410 | 1020 | -639 | 2593 | 2 | 359 |
| channel | retest_native | tsf_5_50 | {"M": 10, "tol": 0.5} | sym15u / both | 244 | 3901 | 166 | 463 | -554 | 4061 | 1 | 359 |
| fvg15 | break | pasl_10 | {"n": 2, "k": 0.25} | sym15u / both | 134 | 2460 | -440 | 199 | -694 | 2286 | 1 | 359 |
| fvg15 | break_native | pnf_7 | {"n": 1, "k": 0.5} | sym8u / both | 178 | 3061 | -260 | -22 | -252 | 4021 | 2 | 359 |
| fvg15 | false_break | tsf_2_2000 | {"M": 3, "k": 0.5} | plain60/60 / both | 119 | 1305 | 260 | 241 | 232 | 1413 | 1 | 359 |
| fvg15 | false_break_native | pnf_10 | {"M": 2, "k": 0.0} | plain60/60 / short | 131 | 1153 | 235 | -698 | -647 | 1605 | 2 | 359 |
| fvg15 | reject | tm45 | {"tol": 1.0, "conf": "close"} | sym15u / both | 186 | 4558 | -705 | -648 | -2527 | 6105 | 2 | 359 |
| fvg15 | reject_native | dib_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 163 | 5901 | -61 | -106 | 331 | 6224 | 2 | 359 |
| fvg15 | retest | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 90 | 3210 | 507 | -733 | -913 | 3727 | 1 | 359 |
| fvg15 | retest_native | swing_atr_0.4 | {"M": 10, "tol": 0.5} | sym15u / both | 160 | 3378 | 303 | 614 | -905 | 3895 | 1 | 359 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.25} | sym15u / both | 231 | 3643 | 664 | 630 | 132 | 3824 | 2 | 359 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 2 | 359 |
| fvg5 | false_break | pasl_20 | {"M": 3, "k": 0.5} | sym15u / both | 185 | 3425 | -434 | -439 | 310 | 4342 | 1 | 359 |
| fvg5 | false_break_native | pasl_28 | {"M": 3, "k": 0.5} | sym8u / both | 161 | 3028 | 382 | -2232 | 339 | 2828 | 2 | 359 |
| fvg5 | reject | dib_25000 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 166 | 2882 | 86 | -520 | 29 | 3642 | 1 | 359 |
| fvg5 | reject_native | rng_10 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 285 | 3008 | 382 | -3550 | 277 | 3608 | 2 | 359 |
| fvg5 | retest | rng_10 | {"M": 6, "tol": 0.0} | sym15u / both | 275 | 2627 | -786 | 667 | -2294 | 2821 | 2 | 359 |
| fvg5 | retest_native | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 189 | 3090 | -276 | -1553 | 384 | 2624 | 1 | 359 |
| gaps | break | dltor_B130 | {"n": 2, "k": 0.25} | sym15u / both | 158 | 2944 | -154 | 1653 | 91 | 1981 | 1 | 359 |
| gaps | break_native | dltor_B130 | {"n": 2, "k": 0.25} | sym15u / both | 167 | 3226 | -208 | 1396 | -211 | 1755 | 1 | 359 |
| gaps | false_break | pasl_20 | {"M": 1, "k": 0.0} | sym15u / both | 124 | 2164 | 292 | -70 | -125 | 3244 | 1 | 359 |
| gaps | false_break_native | pasl_20 | {"M": 3, "k": 0.5} | sym15u / both | 120 | 2263 | -51 | -233 | 70 | 3737 | 1 | 359 |
| gaps | reject | sessrng_B050 | {"tol": 1.0, "conf": "body"} | sym15u / both | 108 | 2501 | -672 | -948 | -1438 | 2977 | 1 | 359 |
| gaps | reject_native | tm1200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 135 | 3052 | 190 | 323 | -236 | 4051 | 1 | 359 |
| gaps | retest | sessrng_B500 | {"M": 3, "tol": 0.0} | sym15u / both | 97 | 2386 | 324 | -960 | -350 | 1663 | 1 | 359 |
| gaps | retest_native | dchg_40 | {"M": 10, "tol": 0.5} | sym15u / both | 100 | 2965 | -26 | 445 | -1444 | 3373 | 1 | 359 |
| mmove | break | time_s_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 563 | 3454 | -202 | -98 | -363 | 3125 | 1 | 359 |
| mmove | break_native | tm240 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 3345 | 1130 | -642 | 997 | 3399 | 1 | 359 |
| mmove | false_break | vib_1200 | {"M": 1, "k": 0.0} | plain60/60 / both | 637 | 3289 | 490 | -690 | -2281 | 1178 | 1 | 359 |
| mmove | false_break_native | vnorm_400 | {"M": 2, "k": 0.5} | plain60/60 / both | 577 | 3846 | -272 | -1178 | 1132 | 2802 | 1 | 359 |
| mmove | reject | rng_10 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 599 | 4025 | -915 | -1615 | -366 | 4170 | 2 | 359 |
| mmove | reject_native | rng_10 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 572 | 4441 | -1068 | -581 | -1627 | 3739 | 2 | 359 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 229 | 4422 | 566 | -839 | -1285 | 5508 | 2 | 359 |
| mmove | retest_native | urenko_20 | {"M": 10, "tol": 0.0} | asym10u/20u / both | 219 | 3605 | 287 | -158 | -1618 | 2842 | 2 | 359 |
| ob15 | break | rngor_B320 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 1695 | -628 | -1096 | 132 | 2278 | 1 | 359 |
| ob15 | break_native | rngor_B200 | {"n": 3, "k": 0.5} | sym15u / both | 83 | 2147 | -435 | -1057 | 762 | 1762 | 1 | 359 |
| ob15 | false_break | dib_400 | {"M": 1, "k": 0.5} | plain60/60 / both | 73 | 1333 | 197 | -244 | 865 | 1421 | 2 | 359 |
| ob15 | false_break_native | dib_400 | {"M": 1, "k": 0.5} | sym30u / both | 59 | 1576 | -66 | -302 | 1358 | 1764 | 2 | 359 |
| ob15 | reject | sessrng_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 2223 | 620 | -603 | 451 | 2383 | 1 | 359 |
| ob15 | reject_native | sessrng_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 76 | 1939 | 458 | -656 | -148 | 1849 | 1 | 359 |
| ob15 | retest | dchg_56 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1143 | 269 | -324 | 554 | 1703 | 1 | 359 |
| ob15 | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 64 | 1241 | -318 | 28 | 247 | -790 | 1 | 359 |
| ob5 | break | entropy_B200 | {"n": 1, "k": 0.0} | sym15u / both | 145 | 2754 | 121 | 567 | 1696 | 1088 | 1 | 359 |
| ob5 | break_native | entropy_B200 | {"n": 1, "k": 0.0} | sym15u / both | 145 | 2754 | 121 | 567 | 1696 | 1088 | 1 | 359 |
| ob5 | false_break | entropy_B200 | {"M": 3, "k": 0.5} | sym15u / both | 145 | 2646 | -81 | -307 | 1857 | 1139 | 1 | 359 |
| ob5 | false_break_native | entropy_B200 | {"M": 1, "k": 0.0} | sym15u / both | 145 | 2582 | 537 | 358 | 2113 | 1170 | 1 | 359 |
| ob5 | reject | renko_14 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 103 | 1955 | -283 | -741 | -264 | 1763 | 2 | 359 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym8u / both | 109 | 1981 | -439 | -838 | -604 | 757 | 2 | 359 |
| ob5 | retest | vib_10000 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 2918 | 474 | -691 | -688 | 2305 | 1 | 359 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | asym10u/20u / both | 113 | 2684 | -357 | -1108 | 54 | 2180 | 2 | 359 |
| open_range | break | dltor_B130 | {"n": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 603 | 1453 | 158 | 1 | 90 |
| open_range | break_native | dltor_B130 | {"n": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 603 | 1453 | 158 | 1 | 90 |
| open_range | false_break | dltor_B130 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 593 | 1334 | 158 | 1 | 90 |
| open_range | false_break_native | sessrng_B030 | {"M": 3, "k": 0.5} | sym15u / both | 83 | 992 | -869 | 99 | 428 | 316 | 1 | 90 |
| open_range | reject | tpo_30m | {"tol": 0.0, "conf": "close"} | sym15u / both | 31 | 360 | 467 | 147 | -459 | 285 | 1 | 90 |
| open_range | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 45 | 1259 | 937 | 255 | -269 | 1312 | 1 | 90 |
| open_range | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 45 | 409 | -30 | -174 | 387 | 442 | 1 | 90 |
| open_range | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 52 | 191 | -68 | -256 | 46 | 223 | 1 | 90 |
| opens | break | wrenko_14 | {"n": 1, "k": 0.25} | asym10u/20u / both | 188 | 3964 | 257 | 743 | 507 | 3189 | 2 | 359 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 359 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 359 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 359 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 2 | 359 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 2 | 359 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 359 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 359 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 2 | 359 |
| prior_day | break_native | time_s_45 | {"n": 3, "k": 0.0} | asym20u/10u / both | 138 | 2725 | 52 | -398 | -1585 | 1165 | 2 | 359 |
| prior_day | false_break | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2871 | 220 | 1502 | -275 | 2410 | 1 | 359 |
| prior_day | false_break_native | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2871 | 220 | 1502 | -275 | 2410 | 1 | 359 |
| prior_day | reject | tm60 | {"tol": 0.0, "conf": "body"} | sym30u / both | 104 | 2190 | -1249 | 794 | 865 | 2404 | 2 | 359 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 359 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 2 | 359 |
| prior_day | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 119 | 3556 | -235 | -293 | -833 | 3575 | 1 | 359 |
| profile_nodes | break | volor_B080 | {"n": 1, "k": 0.0} | sym15u / both | 173 | 3157 | -39 | -257 | -1676 | 2400 | 1 | 359 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 359 |
| profile_nodes | false_break | dltor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3215 | -266 | 424 | 785 | 2028 | 1 | 359 |
| profile_nodes | false_break_native | dltor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 231 | 3337 | -127 | 59 | 585 | 2388 | 1 | 359 |
| profile_nodes | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym8u / both | 156 | 3014 | -896 | -766 | -1696 | 3023 | 2 | 359 |
| profile_nodes | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym8u / both | 156 | 3014 | -896 | -766 | -1696 | 3023 | 2 | 359 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 359 |
| profile_nodes | retest_native | dol_750 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 3248 | -111 | -1036 | -1589 | 5058 | 1 | 359 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 2 | 359 |
| profile_va | break_native | tm300 | {"n": 3, "k": 0.0} | sym8u / both | 140 | 2699 | -69 | -2143 | -949 | 1447 | 2 | 359 |
| profile_va | false_break | rngor_B500 | {"M": 3, "k": 0.5} | sym15u / both | 194 | 3979 | -184 | 386 | -294 | 4155 | 1 | 359 |
| profile_va | false_break_native | sessrng_B500 | {"M": 2, "k": 0.5} | sym15u / both | 190 | 4021 | 65 | 271 | 78 | 4692 | 1 | 359 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 359 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 359 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym8u / both | 133 | 3198 | 379 | -1464 | -342 | 2602 | 2 | 359 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 359 |
| round | break | volor_B320 | {"n": 1, "k": 0.0} | sym15u / both | 279 | 4289 | -337 | 598 | 2614 | 5233 | 1 | 477 |
| round | break_native | volor_B320 | {"n": 1, "k": 0.0} | sym15u / both | 279 | 4289 | -337 | 598 | 2614 | 5233 | 1 | 477 |
| round | false_break | sessrng_B500 | {"M": 1, "k": 0.0} | sym15u / both | 305 | 4311 | -729 | -298 | 887 | 3838 | 1 | 477 |
| round | false_break_native | typ_qmid_B080 | {"M": 3, "k": 0.5} | sym15u / both | 277 | 4927 | 217 | -2006 | -1716 | 4318 | 1 | 477 |
| round | reject | time_s_20 | {"tol": 0.0, "conf": "body"} | sym15u / both | 350 | 4952 | 55 | -457 | -569 | 5515 | 2 | 477 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 477 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 477 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 477 |
| session_hl | break | time_s_10 | {"n": 1, "k": 0.25} | asym20u/10u / both | 302 | 1967 | -451 | -883 | 870 | 1633 | 2 | 357 |
| session_hl | break_native | pasl_14 | {"n": 2, "k": 0.5} | sym15u / both | 130 | 2714 | -40 | -912 | -606 | 3328 | 2 | 357 |
| session_hl | false_break | pnf_5 | {"M": 1, "k": 0.0} | sym8u / both | 142 | 1886 | -97 | -644 | -522 | 2232 | 2 | 357 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 357 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 357 |
| session_hl | reject_native | vrb_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 1815 | 335 | -612 | -95 | 2394 | 1 | 357 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 357 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym8u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 2 | 357 |
| trendline | break | time_m_2 | {"n": 2, "k": 0.25} | sym30u / both | 221 | 3603 | 523 | 1434 | 1011 | 4050 | 2 | 360 |
| trendline | break_native | wrenko_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 232 | 3767 | -353 | -553 | -3251 | 4517 | 2 | 360 |
| trendline | false_break | pasl_28 | {"M": 3, "k": 0.5} | sym15u / both | 231 | 2852 | -904 | 507 | 900 | 2905 | 1 | 360 |
| trendline | false_break_native | pasl_14 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2554 | -1041 | -747 | -251 | 1499 | 2 | 360 |
| trendline | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 639 | 4531 | -670 | 951 | -1990 | 6834 | 2 | 360 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym8u / both | 215 | 4460 | -240 | -1707 | -184 | 4109 | 2 | 360 |
| trendline | retest | volor_B200 | {"M": 10, "tol": 0.5} | sym15u / both | 219 | 4477 | -350 | -1163 | -317 | 3562 | 1 | 360 |
| trendline | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym8u / both | 435 | 3422 | -468 | -1462 | 1198 | 3408 | 2 | 360 |
| uw_dp | break | tpo_30m | {"n": 1, "k": 0.0} | sym15u / both | 118 | 2850 | 0 | 0 | -452 | 3235 | 1 | 359 |
| uw_dp | break_native | tpo_30m | {"n": 1, "k": 0.0} | sym15u / both | 118 | 2850 | 0 | 0 | -452 | 3235 | 1 | 359 |
| uw_dp | false_break | entropy_B500 | {"M": 3, "k": 0.5} | sym15u / both | 143 | 3129 | 0 | 0 | -31 | 3967 | 1 | 359 |
| uw_dp | false_break_native | tpo_30m | {"M": 2, "k": 0.5} | sym15u / both | 123 | 3358 | 0 | 0 | -119 | 3632 | 1 | 359 |
| uw_dp | reject | lbrk_4_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2169 | 0 | 0 | -278 | 2211 | 1 | 359 |
| uw_dp | reject_native | sessrng_B050 | {"tol": 1.0, "conf": "body"} | sym15u / both | 112 | 2128 | 0 | 0 | -83 | 1462 | 1 | 359 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 359 |
| uw_dp | retest_native | pasl_14 | {"M": 3, "tol": 0.5} | sym8u / both | 88 | 2611 | 0 | 0 | 319 | 3601 | 2 | 359 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.25} | asym10u/20u / both | 113 | 3528 | 0 | 168 | -2224 | 3855 | 2 | 359 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 359 |
| uw_ndx | false_break | sessrng_B500 | {"M": 2, "k": 0.5} | plain60/60 / both | 265 | 3213 | 0 | 683 | 826 | 1221 | 1 | 359 |
| uw_ndx | false_break_native | sessrng_B500 | {"M": 2, "k": 0.5} | plain60/60 / both | 262 | 3282 | 0 | 598 | 532 | 1225 | 1 | 359 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 359 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 359 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 359 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 359 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 359 |
| uw_qqq | break_native | mom_40 | {"n": 1, "k": 0.25} | sym8u / both | 116 | 2967 | 0 | 351 | 691 | 447 | 2 | 359 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 359 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 359 |
| uw_qqq | reject | trend_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 109 | 3288 | 0 | 305 | -1998 | 1890 | 1 | 359 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 359 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 359 |
| uw_qqq | retest_native | wrenko_20 | {"M": 3, "tol": 0.5} | sym8u / both | 118 | 3048 | 0 | 302 | 191 | 1592 | 2 | 359 |
| vwap | break | urenko_20 | {"n": 3, "k": 0.5} | asym10u/20u / both | 224 | 5588 | 1041 | -2125 | -2077 | 5185 | 2 | 359 |
| vwap | break_native | mrenko_20 | {"n": 2, "k": 0.5} | asym20u/10u / both | 226 | 6284 | 120 | -1085 | -1977 | 7689 | 2 | 359 |
| vwap | false_break | trb_2000 | {"M": 2, "k": 0.5} | sym15u / both | 181 | 3231 | -238 | -642 | 725 | 1849 | 1 | 359 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 359 |
| vwap | reject | rngor_B050 | {"tol": 0.0, "conf": "close"} | sym15u / both | 207 | 4934 | 712 | -854 | 272 | 4131 | 1 | 359 |
| vwap | reject_native | trb_400 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 236 | 6219 | 755 | 898 | -212 | 5267 | 2 | 359 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 359 |
| vwap | retest_native | vfp_t5m | {"M": 10, "tol": 0.5} | sym15u / both | 208 | 4967 | 40 | 270 | 1512 | 5907 | 1 | 359 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 359 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 359 |
| vwap_bands | false_break | tm15 | {"M": 1, "k": 0.5} | plain60/60 / both | 705 | 3509 | -455 | -467 | -528 | 2159 | 2 | 359 |
| vwap_bands | false_break_native | time_s_15 | {"M": 1, "k": 0.5} | plain60/60 / both | 699 | 3575 | 865 | -1939 | 1029 | 795 | 2 | 359 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 359 |
| vwap_bands | reject_native | tm20 | {"tol": 1.0, "conf": "close"} | sym15u / both | 547 | 4046 | -1550 | -51 | -2596 | 3340 | 2 | 359 |
| vwap_bands | retest | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 210 | 3848 | 316 | 279 | -1912 | 3192 | 1 | 359 |
| vwap_bands | retest_native | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 214 | 3984 | 196 | 78 | -2025 | 3844 | 1 | 359 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 2 | 360 |
| week_month | break_native | pnf_28 | {"n": 1, "k": 0.5} | sym8u / both | 64 | 1661 | 81 | 301 | -986 | 1262 | 2 | 360 |
| week_month | false_break | vfp_t15m | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1432 | -324 | 477 | 227 | 1444 | 1 | 360 |
| week_month | false_break_native | vfp_t15m | {"M": 2, "k": 0.5} | sym15u / both | 54 | 1719 | -197 | 647 | 517 | 955 | 1 | 360 |
| week_month | reject | tib_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 34 | 1905 | -46 | -393 | -862 | 2501 | 1 | 360 |
| week_month | reject_native | tib_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 42 | 1981 | -30 | -448 | -602 | 2427 | 1 | 360 |
| week_month | retest | volor_B130 | {"M": 10, "tol": 0.5} | sym15u / both | 34 | 1407 | -167 | 227 | 691 | 2082 | 1 | 360 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym8u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 2 | 360 |
| zones | break | pnf_10 | {"n": 1, "k": 0.5} | sym15u / both | 164 | 2713 | 1125 | 1861 | -1983 | 4035 | 2 | 359 |
| zones | break_native | swing_pct_8 | {"n": 1, "k": 0.25} | sym8u / both | 179 | 4269 | 914 | 299 | 1497 | 6048 | 2 | 359 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 359 |
| zones | false_break_native | sessrng_B500 | {"M": 2, "k": 0.5} | plain60/60 / both | 299 | 1919 | -864 | 734 | -1012 | 1161 | 1 | 359 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 359 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 359 |
| zones | retest | rngor_B030 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2481 | -216 | -1079 | 670 | 2117 | 1 | 359 |
| zones | retest_native | rngor_B030 | {"M": 10, "tol": 0.5} | sym15u / both | 131 | 2426 | -424 | 61 | 1307 | 2239 | 1 | 359 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd15 | break | pnf_14 | {"n": 1, "F": 2} | plain60/60 / both | 30 | 503 | -165 | 211 | -237 | -26 | 2 | 367 |
| sd15 | break_native | pnf_14 | {"n": 1, "F": 2} | plain60/60 / both | 30 | 503 | -165 | 211 | -237 | -26 | 2 | 367 |
| sd15 | reject | rngor_B500 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 36 | 223 | 87 | -203 | -334 | 286 | 1 | 367 |
| sd15 | reject_flow | vfp_rng16 | {"F": 2, "D": 15} | plain60/60 / both | 31 | 210 | -35 | -333 | -45 | 266 | 1 | 367 |
| sd15 | reject_flow_native | vfp_rng16 | {"F": 2, "D": 15} | plain60/60 / both | 31 | 210 | -35 | -333 | -45 | 266 | 1 | 367 |
| sd15 | reject_native | rngor_B500 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 36 | 223 | 87 | -203 | -334 | 286 | 1 | 367 |
| sd5 | break | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 367 |
| sd5 | break_native | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 367 |
| sd5 | reject | wrenko_10 | {"F": 2, "D": 15, "tol": 0.5} | sym15u / both | 33 | 1327 | 442 | -169 | -629 | 1028 | 2 | 367 |
| sd5 | reject_flow | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 367 |
| sd5 | reject_flow_native | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 367 |
| sd5 | reject_native | urenko_56 | {"F": 2, "D": 15, "tol": 0.5} | sym8u / both | 31 | 1120 | 380 | 67 | -61 | 958 | 2 | 367 |
| sd5 | retest | tib_240 | {"M": 6, "tol": 0.0} | sym15u / both | 30 | -216 | 58 | 23 | 278 | -447 | 1 | 367 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 2 | 367 |
| sdx15 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 171 | 2399 | -85 | 715 | 2594 | 3384 | 1 | 367 |
| sdx15 | lim_mid | dol_500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 | 2883 | -399 | -1339 | -3208 | 2381 | 1 | 367 |
| sdx15 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 373 | 3815 | 30 | -593 | -1777 | 5127 | 1 | 367 |
| sdx15 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 68 | 2107 | -1412 | -869 | 341 | 1563 | 1 | 367 |
| sdx15 | rej_flow | vrb_400 | {"d": "A", "F": 0} | sym15u / both | 74 | 1289 | -104 | 202 | -1621 | 805 | 1 | 367 |
| sdx15 | rej_native | kagi_56 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 2039 | -160 | -2368 | -1749 | 2557 | 1 | 367 |
| sdx15 | rej_zone | trend_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 167 | 4203 | -2089 | -2089 | -1211 | 2114 | 1 | 367 |
| sdx15 | retest | vrb_15000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 59 | 1800 | 436 | 786 | 2832 | 1896 | 1 | 367 |
| sdx3 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 350 | 3483 | 1458 | 3578 | 5139 | 4750 | 1 | 367 |
| sdx3 | lim_mid | lbrk_3_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 299 | 3226 | -1441 | -1980 | -541 | 1746 | 1 | 367 |
| sdx3 | lim_prox | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 224 | 3509 | 1324 | 128 | -1502 | 4960 | 1 | 367 |
| sdx3 | rej | vfp_t5m | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 3433 | 1422 | -1125 | -1310 | 3351 | 1 | 367 |
| sdx3 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / long | 149 | 2221 | 155 | -634 | -2925 | 2569 | 1 | 367 |
| sdx3 | rej_native | vfp_t5m | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 304 | 3972 | 1368 | -2603 | -2297 | 4740 | 1 | 367 |
| sdx3 | rej_zone | vfp_t5m | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 304 | 3972 | 1368 | -2603 | -2297 | 4740 | 1 | 367 |
| sdx3 | retest | kagi_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 245 | 2392 | 2042 | 2685 | 4969 | 3185 | 1 | 367 |
| sdx30 | break | vrb_15000 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 63 | 1677 | 429 | 237 | 1386 | 1772 | 1 | 367 |
| sdx30 | lim_mid | vfp_vol2500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 93 | 1606 | -398 | -1370 | 110 | 1632 | 1 | 367 |
| sdx30 | lim_prox | trend_112 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 80 | 2215 | -1026 | 537 | -935 | 1530 | 1 | 367 |
| sdx30 | rej | vrb_70000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 52 | 1129 | 167 | -1005 | 780 | 954 | 1 | 367 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 146 | 1480 | -676 | -2116 | -2930 | 1823 | 1 | 367 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 367 |
| sdx30 | rej_zone | pasl_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / long | 88 | 2061 | 108 | -188 | -665 | 2504 | 1 | 367 |
| sdx30 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | plain60/60 / both | 59 | 971 | 228 | -723 | -36 | 825 | 1 | 367 |
| sdx5 | break | dol_350 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 113 | 1986 | -19 | 351 | 1701 | 2104 | 1 | 367 |
| sdx5 | lim_mid | kagi_56 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 225 | 2647 | 360 | -2080 | 3658 | 1491 | 1 | 367 |
| sdx5 | lim_prox | vnorm_150 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 443 | 3828 | -84 | 727 | -1994 | 6421 | 1 | 367 |
| sdx5 | rej | vfp_t5m | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 278 | 2182 | 436 | -787 | -1748 | 4332 | 1 | 367 |
| sdx5 | rej_flow | vfp_t5m | {"d": "E", "F": 9} | sym15u / both | 178 | 1492 | -1186 | -1048 | -633 | 1824 | 1 | 367 |
| sdx5 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 557 | 3047 | -1480 | -1346 | -2698 | 3975 | 1 | 367 |
| sdx5 | rej_zone | pasl_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 231 | 3243 | -997 | 523 | -622 | 2429 | 1 | 367 |
| sdx5 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 165 | 2309 | 1186 | -216 | 3671 | 2698 | 1 | 367 |
| sdx60 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 52 | 1464 | 466 | 334 | 762 | 926 | 1 | 367 |
| sdx60 | lim_mid | vfp_vol1000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 498 | 1603 | -1618 | -389 | -981 | 1968 | 1 | 367 |
| sdx60 | lim_prox | dltor_B030 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 140 | 1882 | -798 | -95 | 767 | 1669 | 1 | 367 |
| sdx60 | rej | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 124 | 2540 | -595 | -1785 | -237 | 2453 | 1 | 367 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / long | 90 | 1309 | 89 | -465 | -399 | 884 | 1 | 367 |
| sdx60 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 367 |
| sdx60 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 367 |
| sdx_renko28 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 414 | 2253 | 1371 | 1566 | 6262 | 3069 | 1 | 367 |
| sdx_renko28 | lim_mid | kagi_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 475 | 4203 | 121 | -178 | 3832 | 2308 | 1 | 367 |
| sdx_renko28 | lim_prox | volor_B030 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 406 | 3848 | -1252 | -2353 | -1675 | 3405 | 1 | 367 |
| sdx_renko28 | rej | volor_B200 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 760 | 3146 | -803 | -1693 | -2904 | 520 | 1 | 367 |
| sdx_renko28 | rej_flow | vfp_vol2500 | {"d": "E", "F": 9} | sym15u / both | 232 | 1713 | -1274 | 18 | 1696 | -905 | 1 | 367 |
| sdx_renko28 | rej_native | vfp_vol1000 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 413 | 2044 | -356 | -2092 | -5284 | 4077 | 1 | 367 |
| sdx_renko28 | rej_zone | swing_atr_0.6 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 564 | 2517 | -165 | 672 | -4923 | 685 | 1 | 367 |
| sdx_renko28 | retest | vrb_400 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 140 | 1429 | 9 | 1946 | 2070 | 360 | 1 | 367 |
| sdx_rng28 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 480 | 4135 | -249 | -747 | 7833 | 6261 | 1 | 367 |
| sdx_rng28 | lim_mid | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1515 | 4008 | -446 | -1587 | -7328 | 4734 | 1 | 367 |
| sdx_rng28 | lim_prox | vfp_vol2500 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 485 | 4480 | 1447 | 4399 | 2473 | 6450 | 1 | 367 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 243 | 2685 | 823 | -338 | 409 | 1641 | 1 | 367 |
| sdx_rng28 | rej_flow | vrb_15000 | {"d": "E", "F": 9} | plain60/60 / both | 323 | 1490 | -755 | 679 | -1301 | 617 | 1 | 367 |
| sdx_rng28 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 431 | 3332 | 1328 | -4047 | 1358 | 3443 | 1 | 367 |
| sdx_rng28 | rej_zone | frenko_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4594 | 559 | -3692 | -3237 | 3340 | 1 | 367 |
| sdx_rng28 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 449 | 3491 | -1168 | 3003 | 5388 | 3398 | 1 | 367 |
| sdx_vol1100 | break | lbrk_3_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 599 | 2954 | -817 | 879 | 1581 | 2600 | 1 | 367 |
| sdx_vol1100 | lim_mid | volor_B030 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 428 | 4293 | -1122 | 788 | -72 | 2782 | 1 | 367 |
| sdx_vol1100 | lim_prox | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1415 | 3960 | 2147 | -2379 | -9396 | 5755 | 1 | 367 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 429 | 5058 | -1453 | -1789 | -1589 | 7224 | 1 | 367 |
| sdx_vol1100 | rej_flow | vrb_700 | {"d": "E", "F": 0} | sym15u / both | 321 | 2969 | -6 | 1488 | -104 | 2957 | 1 | 367 |
| sdx_vol1100 | rej_native | vnorm_150 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 1109 | 4606 | -1663 | -1693 | -4883 | 5521 | 1 | 367 |
| sdx_vol1100 | rej_zone | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4710 | -906 | -898 | -3639 | 4361 | 1 | 367 |
| sdx_vol1100 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 375 | 4034 | 902 | 713 | 2371 | 3527 | 1 | 367 |
| fib15 | break | dchg_20 | {"n": 1, "k": 0.0} | sym15u / both | 346 | 3526 | 555 | 2339 | 3572 | 2098 | 1 | 367 |
| fib15 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 309 | 3889 | 1224 | -1144 | 3109 | 4406 | 1 | 367 |
| fib15 | false_break | pnf_5 | {"M": 1, "k": 0.5} | asym20u/10u / both | 369 | 4016 | 565 | 3166 | 2420 | 3650 | 2 | 367 |
| fib15 | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | asym20u/10u / both | 372 | 3672 | 357 | 2841 | 4060 | 3234 | 2 | 367 |
| fib15 | pullback | pnf_5 | {"tol": 1.0, "conf": "close"} | sym8u / both | 264 | 2932 | 963 | -352 | 854 | 2872 | 2 | 367 |
| fib15 | pullback_native | urenko_80 | {"tol": 1.0, "conf": "close"} | sym8u / both | 192 | 2987 | 1008 | -1831 | -2463 | 3193 | 2 | 367 |
| fib15 | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 361 | 4272 | -1022 | 147 | 2523 | 4051 | 1 | 367 |
| fib15 | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 361 | 5051 | 722 | -694 | 2601 | 3935 | 1 | 367 |
| fib15 | retest | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 367 |
| fib15 | retest_native | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 367 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.0} | sym15u / both | 387 | 5560 | -169 | -1634 | 1552 | 5305 | 2 | 367 |
| fib5 | break_native | wrenko_10 | {"n": 3, "k": 0.25} | sym8u / both | 496 | 5756 | -2306 | -3717 | -1682 | 5521 | 2 | 367 |
| fib5 | false_break | rng_28 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 5122 | 509 | -759 | 2913 | 3226 | 1 | 367 |
| fib5 | false_break_native | mrenko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 448 | 5943 | -1631 | -3809 | 1048 | 5841 | 2 | 367 |
| fib5 | pullback | urenko_14 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 353 | 4013 | -1059 | -193 | 760 | 6596 | 2 | 367 |
| fib5 | pullback_native | dlt_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 351 | 3050 | -717 | -1303 | -243 | 5196 | 1 | 367 |
| fib5 | reject | vrb_1200 | {"tol": 0.0, "conf": "body"} | sym8u / both | 375 | 4520 | -365 | -1515 | 620 | 5572 | 2 | 367 |
| fib5 | reject_native | vrb_1200 | {"tol": 0.0, "conf": "body"} | sym8u / both | 375 | 4520 | -365 | -1515 | 620 | 5572 | 2 | 367 |
| fib5 | retest | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 367 |
| fib5 | retest_native | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 367 |
| fib60 | break | vnorm_150 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 4746 | 195 | 2278 | 58 | 4400 | 1 | 367 |
| fib60 | break_native | dlt_45 | {"n": 3, "k": 0.5} | sym15u / both | 318 | 5222 | -1532 | -573 | 828 | 5732 | 1 | 367 |
| fib60 | false_break | vnorm_250 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4788 | 651 | 49 | 1652 | 3843 | 1 | 367 |
| fib60 | false_break_native | swing_pct_8 | {"M": 2, "k": 0.5} | sym15u / both | 308 | 4583 | 2331 | 2922 | 2124 | 5925 | 1 | 367 |
| fib60 | pullback | tsf_5_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 2509 | -224 | 1972 | -1446 | 1514 | 1 | 367 |
| fib60 | pullback_native | tick_5000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 2539 | -702 | 2326 | 50 | 1531 | 1 | 367 |
| fib60 | reject | tick_300 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 4010 | -1870 | -1434 | 2221 | 3583 | 1 | 367 |
| fib60 | reject_native | dib_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 303 | 4392 | 0 | -661 | -328 | 4902 | 1 | 367 |
| fib60 | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym8u / both | 291 | 4996 | 651 | -1039 | 72 | 3321 | 2 | 367 |
| fib60 | retest_native | renko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 4745 | 238 | -75 | 4108 | 2780 | 1 | 367 |
| fibr_dev | break | pnf_10 | {"n": 1, "k": 0.5} | sym15u / both | 451 | 5109 | 2053 | 1251 | 608 | 7788 | 2 | 367 |
| fibr_dev | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 417 | 4933 | -349 | 802 | 2045 | 5492 | 1 | 367 |
| fibr_dev | false_break | pasl_28 | {"M": 3, "k": 0.0} | sym8u / both | 411 | 6011 | 2568 | -1293 | 7299 | 3506 | 2 | 367 |
| fibr_dev | false_break_native | pasl_28 | {"M": 3, "k": 0.0} | sym8u / both | 411 | 6011 | 2568 | -1293 | 7299 | 3506 | 2 | 367 |
| fibr_dev | reject | vol_750 | {"tol": 1.0, "conf": "close"} | asym10u/20u / both | 441 | 4755 | 453 | -1527 | 743 | 5310 | 2 | 367 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym8u / both | 448 | 4974 | 781 | 2614 | 1121 | 4931 | 2 | 367 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym8u / both | 425 | 6500 | -433 | 1223 | 3603 | 6424 | 2 | 367 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym8u / both | 447 | 5298 | -654 | -1569 | 5048 | 6345 | 2 | 367 |
| fibr_ib | break | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 292 | 4439 | -707 | -865 | -1300 | 4236 | 1 | 365 |
| fibr_ib | break_native | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 292 | 4439 | -707 | -865 | -1300 | 4236 | 1 | 365 |
| fibr_ib | false_break | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4548 | 1798 | -1940 | 2039 | 3927 | 1 | 365 |
| fibr_ib | false_break_native | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4548 | 1798 | -1940 | 2039 | 3927 | 1 | 365 |
| fibr_ib | reject | tib_400 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 823 | 4829 | -562 | -855 | 904 | 5182 | 1 | 365 |
| fibr_ib | reject_native | tib_400 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 823 | 4829 | -562 | -855 | 904 | 5182 | 1 | 365 |
| fibr_ib | retest | anch_R0830_B25 | {"M": 6, "tol": 0.5} | sym15u / both | 202 | 3484 | 934 | -1580 | 1874 | 3228 | 1 | 365 |
| fibr_ib | retest_native | tib_240 | {"M": 6, "tol": 0.5} | plain60/60 / both | 827 | 4348 | 1609 | -2863 | -433 | 2603 | 1 | 365 |
| fibr_on | break | dol_1100 | {"n": 2, "k": 0.25} | sym15u / both | 378 | 4421 | 587 | 341 | 5542 | 5217 | 1 | 365 |
| fibr_on | break_native | dchg_20 | {"n": 3, "k": 0.5} | sym15u / both | 414 | 4798 | 1613 | 377 | 7176 | 7335 | 1 | 365 |
| fibr_on | false_break | pnf_5 | {"M": 1, "k": 0.0} | asym20u/10u / both | 422 | 5477 | 1103 | 5617 | 1085 | 7440 | 2 | 365 |
| fibr_on | false_break_native | pnf_10 | {"M": 1, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 2 | 365 |
| fibr_on | reject | dol_2600 | {"tol": 0.5, "conf": "body"} | sym15u / both | 359 | 5962 | -130 | 1420 | -849 | 7214 | 1 | 365 |
| fibr_on | reject_native | dib_15000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 412 | 5588 | -668 | 2988 | 1323 | 4894 | 1 | 365 |
| fibr_on | retest | vib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 371 | 6895 | 468 | 685 | 1681 | 6510 | 1 | 365 |
| fibr_on | retest_native | dib_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 421 | 5382 | 313 | -1869 | 4373 | 5259 | 1 | 365 |
| fibr_or | break | dlt_250 | {"n": 1, "k": 0.0} | sym15u / both | 331 | 5801 | -767 | 1687 | 1719 | 4913 | 1 | 365 |
| fibr_or | break_native | mom_28 | {"n": 1, "k": 0.25} | sym8u / both | 364 | 6268 | 166 | 1002 | 2615 | 7065 | 2 | 365 |
| fibr_or | false_break | dltor_B050 | {"M": 2, "k": 0.5} | sym15u / both | 325 | 5278 | 538 | 1649 | 424 | 5582 | 1 | 365 |
| fibr_or | false_break_native | tib_6000 | {"M": 2, "k": 0.5} | sym15u / both | 354 | 5941 | -286 | 3902 | -1175 | 4149 | 1 | 365 |
| fibr_or | reject | vib_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 343 | 4621 | -917 | 906 | -1102 | 4797 | 1 | 365 |
| fibr_or | reject_native | swing_atr_0.6 | {"tol": 1.0, "conf": "body"} | sym15u / both | 380 | 5085 | 440 | -1183 | -3296 | 8286 | 1 | 365 |
| fibr_or | retest | vsess_600 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 375 | 6822 | 26 | -2127 | 3125 | 7665 | 2 | 365 |
| fibr_or | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | asym10u/20u / both | 374 | 6648 | 711 | -1838 | 3287 | 6878 | 2 | 365 |
| fibr_pd | break | dchg_20 | {"n": 3, "k": 0.5} | sym15u / both | 363 | 6038 | -978 | 1126 | 3400 | 6256 | 1 | 367 |
| fibr_pd | break_native | swing_pct_5 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 6098 | -429 | -415 | -229 | 6578 | 1 | 367 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 2 | 367 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 2 | 367 |
| fibr_pd | reject | rng_28 | {"tol": 1.0, "conf": "close"} | sym8u / both | 374 | 5880 | -950 | -383 | -3329 | 8480 | 2 | 367 |
| fibr_pd | reject_native | dol_4000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 401 | 6885 | 992 | -343 | 3378 | 7753 | 1 | 367 |
| fibr_pd | retest | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 297 | 5743 | -250 | -23 | 1081 | 5974 | 2 | 367 |
| fibr_pd | retest_native | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 297 | 5743 | -250 | -23 | 1081 | 5974 | 2 | 367 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.5} | sym15u / both | 355 | 6151 | 1543 | 1204 | -3675 | 7073 | 2 | 367 |
| piv_cama | break_native | pnf_10 | {"n": 2, "k": 0.5} | sym15u / both | 354 | 7364 | 1679 | -3115 | -1088 | 9415 | 2 | 367 |
| piv_cama | false_break | dib_2000 | {"M": 1, "k": 0.5} | asym15u/30u / both | 384 | 3255 | -948 | 2360 | 3357 | 1776 | 2 | 367 |
| piv_cama | false_break_native | wrenko_10 | {"M": 1, "k": 0.5} | sym8u / both | 411 | 5216 | -1977 | -1550 | 1057 | 2687 | 2 | 367 |
| piv_cama | reject | vib_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 469 | 8327 | 252 | 754 | 109 | 4800 | 1 | 367 |
| piv_cama | reject_native | vib_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 469 | 8327 | 252 | 754 | 109 | 4800 | 1 | 367 |
| piv_cama | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym30u / both | 362 | 6283 | -385 | -1382 | 321 | 4058 | 2 | 367 |
| piv_cama | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 326 | 6926 | 709 | 1083 | 2673 | 9373 | 2 | 367 |
| piv_floor | break | time_s_20 | {"n": 2, "k": 0.25} | sym15u / both | 366 | 4617 | 2232 | 1684 | -940 | 4314 | 1 | 367 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 2 | 367 |
| piv_floor | false_break | swing_pct_35 | {"M": 2, "k": 0.5} | sym15u / both | 234 | 4303 | 34 | -2120 | -29 | 4914 | 1 | 367 |
| piv_floor | false_break_native | swing_pct_35 | {"M": 3, "k": 0.5} | sym15u / both | 223 | 4897 | -863 | -1594 | 296 | 5486 | 1 | 367 |
| piv_floor | reject | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 293 | 3916 | 983 | 2932 | 492 | 3221 | 1 | 367 |
| piv_floor | reject_native | tib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 358 | 4124 | -439 | 4759 | 3148 | 6290 | 1 | 367 |
| piv_floor | retest | tib_10000 | {"M": 6, "tol": 0.5} | sym15u / both | 291 | 4485 | 1649 | 989 | 2127 | 4087 | 1 | 367 |
| piv_floor | retest_native | dlt_250 | {"M": 6, "tol": 0.5} | sym15u / both | 312 | 6438 | -984 | 241 | 1279 | 7220 | 1 | 367 |
| piv_wf | break | tm15 | {"n": 3, "k": 0.5} | sym15u / both | 387 | 5413 | -241 | 2600 | -1345 | 6668 | 1 | 367 |
| piv_wf | break_native | tsf_5_200 | {"n": 3, "k": 0.5} | sym15u / both | 354 | 5333 | 64 | -2615 | 1177 | 6384 | 1 | 367 |
| piv_wf | false_break | rng_14 | {"M": 2, "k": 0.5} | sym30u / both | 369 | 3761 | 1242 | 52 | 2350 | 2491 | 2 | 367 |
| piv_wf | false_break_native | swing_pct_8 | {"M": 1, "k": 0.5} | sym8u / both | 375 | 4722 | 2001 | 963 | 4215 | 4616 | 2 | 367 |
| piv_wf | reject | frenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 439 | 4464 | -582 | -2715 | -307 | 5216 | 1 | 367 |
| piv_wf | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 1156 | 5264 | 351 | 937 | -3558 | 4568 | 2 | 367 |
| piv_wf | retest | cusum_40 | {"M": 6, "tol": 0.5} | sym15u / both | 322 | 6154 | -169 | 1020 | 879 | 6130 | 1 | 367 |
| piv_wf | retest_native | swing_atr_0.6 | {"M": 6, "tol": 0.5} | sym15u / both | 393 | 5146 | 2815 | 1011 | 430 | 4962 | 1 | 367 |
| swcluster | break | vol_350 | {"n": 1, "k": 0.5} | sym8u / both | 105 | 1917 | -751 | 551 | 191 | 1152 | 2 | 368 |
| swcluster | break_native | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 103 | 1934 | -1417 | 119 | -467 | 1021 | 1 | 368 |
| swcluster | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | plain60/60 / both | 198 | 1636 | -603 | 353 | -377 | 1347 | 1 | 368 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym8u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 2 | 368 |
| swcluster | reject | vol_750 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 73 | 1906 | 429 | -867 | -1391 | 1531 | 2 | 368 |
| swcluster | reject_native | vol_750 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 73 | 1906 | 429 | -867 | -1391 | 1531 | 2 | 368 |
| swcluster | retest | tsf_2_400 | {"M": 3, "tol": 0.0} | sym15u / both | 67 | 1887 | -6 | -284 | -232 | 1393 | 1 | 368 |
| swcluster | retest_native | swing_atr_0.15 | {"M": 10, "tol": 0.5} | sym15u / both | 86 | 1888 | -1192 | 24 | -629 | 1495 | 1 | 368 |
| swsr15 | break | tick_300 | {"n": 1, "k": 0.25} | sym8u / both | 384 | 4660 | 642 | -3437 | -929 | 3812 | 2 | 368 |
| swsr15 | break_native | vol_500 | {"n": 1, "k": 0.25} | asym10u/20u / both | 335 | 4674 | -1132 | -548 | 4235 | 5477 | 2 | 368 |
| swsr15 | false_break | swing_pct_8 | {"M": 2, "k": 0.5} | sym8u / both | 368 | 5210 | 130 | -399 | 962 | 4650 | 2 | 368 |
| swsr15 | false_break_native | urenko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 390 | 5308 | 599 | 1950 | 3177 | 6110 | 2 | 368 |
| swsr15 | reject | dchg_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 328 | 3877 | -2040 | -171 | -1124 | 4463 | 1 | 368 |
| swsr15 | reject_native | pnf_14 | {"tol": 1.0, "conf": "close"} | sym8u / both | 334 | 4437 | -1906 | 1047 | 112 | 6990 | 2 | 368 |
| swsr15 | retest | vfp_vol1000 | {"M": 10, "tol": 0.5} | sym15u / both | 313 | 5139 | -340 | 414 | 2372 | 4377 | 1 | 368 |
| swsr15 | retest_native | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 360 | 5300 | 138 | -1296 | 3633 | 2816 | 2 | 368 |
| swsr5 | break | dchg_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5687 | 883 | -668 | -1576 | 4634 | 2 | 367 |
| swsr5 | break_native | dchg_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5687 | 883 | -668 | -1576 | 4634 | 2 | 367 |
| swsr5 | false_break | dchg_28 | {"M": 1, "k": 0.5} | sym8u / both | 442 | 5680 | 480 | -1094 | -1798 | 5181 | 2 | 367 |
| swsr5 | false_break_native | dchg_28 | {"M": 2, "k": 0.5} | sym8u / both | 432 | 8191 | 1106 | -2029 | 689 | 8585 | 2 | 367 |
| swsr5 | reject | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 390 | 4483 | 1577 | -1581 | -937 | 4245 | 1 | 367 |
| swsr5 | reject_native | drb_2000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 432 | 4873 | -387 | 1582 | 3386 | 4026 | 1 | 367 |
| swsr5 | retest | vnorm_1000 | {"M": 10, "tol": 0.5} | sym15u / both | 386 | 5555 | 366 | 289 | -703 | 6502 | 1 | 367 |
| swsr5 | retest_native | tsf_2_400 | {"M": 10, "tol": 0.5} | sym15u / both | 392 | 5647 | 2386 | 2871 | 1919 | 5813 | 1 | 367 |
| swsr60 | break | dltor_B080 | {"n": 3, "k": 0.5} | sym15u / both | 246 | 5404 | -1599 | -1913 | 1151 | 4471 | 1 | 367 |
| swsr60 | break_native | tsf_5_100 | {"n": 2, "k": 0.25} | sym15u / both | 264 | 5009 | -1528 | 305 | -759 | 2393 | 1 | 367 |
| swsr60 | false_break | swing_pct_35 | {"M": 2, "k": 0.5} | sym15u / both | 212 | 3629 | -683 | -2090 | 154 | 4928 | 1 | 367 |
| swsr60 | false_break_native | swing_pct_35 | {"M": 2, "k": 0.5} | sym15u / both | 178 | 4118 | -561 | -1900 | 750 | 4417 | 1 | 367 |
| swsr60 | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 270 | 4484 | -197 | -803 | -6247 | 2405 | 1 | 367 |
| swsr60 | reject_native | vsess_120 | {"tol": 1.0, "conf": "body"} | sym30u / both | 303 | 4598 | -1518 | -2698 | -3759 | 2065 | 2 | 367 |
| swsr60 | retest | cusum_40 | {"M": 10, "tol": 0.5} | sym15u / both | 241 | 5728 | 497 | 26 | -245 | 7311 | 1 | 367 |
| swsr60 | retest_native | rng_40 | {"M": 10, "tol": 0.0} | sym8u / both | 229 | 4768 | -1143 | 863 | -880 | 4342 | 2 | 367 |
| stack | break | tm45 | {"k": 2, "cw": 0.5} | sym15u / both | 308 | 5701 | -288 | 436 | 195 | 4988 | 1 | 368 |
| stack | break_native | wrenko_10 | {"k": 3, "cw": 2.0} | asym20u/10u / both | 387 | 5844 | -1457 | 759 | 3127 | 5255 | 2 | 368 |
| stack | reject | tick_800 | {"k": 2, "cw": 2.0} | sym15u / both | 391 | 3903 | -996 | -1425 | 1988 | 3829 | 2 | 368 |
| stack | reject_native | vib_700 | {"k": 2, "cw": 0.5} | sym15u / both | 574 | 6768 | -1475 | -2487 | -2051 | 7068 | 1 | 368 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 367 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | asym10u/20u / both | 65 | 1404 | -828 | 726 | 600 | 1707 | 2 | 367 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 367 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 367 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 367 |
| book_walls_loose | reject_native | vib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 1641 | -460 | -781 | 368 | 1490 | 1 | 367 |
| book_walls_loose | retest | vib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 107 | 1294 | -426 | 1051 | 1393 | 1941 | 1 | 367 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 367 |
| channel | break | dol_1100 | {"n": 1, "k": 0.0} | sym15u / both | 408 | 5392 | 377 | 2559 | 4340 | 2433 | 1 | 367 |
| channel | break_native | dol_1100 | {"n": 1, "k": 0.0} | sym15u / both | 408 | 5392 | 377 | 2559 | 4340 | 2433 | 1 | 367 |
| channel | false_break | dol_1100 | {"M": 1, "k": 0.0} | sym15u / both | 408 | 5126 | 775 | 2752 | 3733 | 3007 | 1 | 367 |
| channel | false_break_native | dol_1100 | {"M": 1, "k": 0.0} | sym15u / both | 408 | 5126 | 775 | 2752 | 3733 | 3007 | 1 | 367 |
| channel | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 1127 | 4027 | 2194 | -2323 | -1894 | 1091 | 1 | 367 |
| channel | reject_native | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 440 | 4572 | 1255 | 143 | 2266 | 7564 | 1 | 367 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.0} | asym15u/30u / both | 434 | 5757 | -474 | 1493 | -1307 | 3940 | 2 | 367 |
| channel | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 428 | 7756 | 1440 | 3439 | 3298 | 7185 | 1 | 367 |
| fvg15 | break | swing_pct_35 | {"n": 1, "k": 0.0} | sym15u / both | 113 | 3385 | 258 | -198 | 1294 | 3715 | 1 | 367 |
| fvg15 | break_native | swing_pct_35 | {"n": 1, "k": 0.0} | sym15u / both | 113 | 3385 | 190 | -198 | 1294 | 3715 | 1 | 367 |
| fvg15 | false_break | swing_pct_35 | {"M": 3, "k": 0.5} | sym15u / both | 85 | 2838 | 226 | -109 | -701 | 2813 | 1 | 367 |
| fvg15 | false_break_native | dib_3500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 163 | 2957 | 282 | 116 | 186 | 809 | 2 | 367 |
| fvg15 | reject | time_m_1 | {"tol": 0.5, "conf": "body"} | sym15u / both | 152 | 2592 | 227 | 1406 | 1791 | 2160 | 1 | 367 |
| fvg15 | reject_native | dltor_B200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 174 | 2179 | -391 | -645 | 286 | 2088 | 1 | 367 |
| fvg15 | retest | vrb_1200 | {"M": 10, "tol": 0.0} | sym15u / both | 156 | 3753 | 530 | -71 | -1029 | 4108 | 2 | 367 |
| fvg15 | retest_native | vrb_1200 | {"M": 10, "tol": 0.0} | sym15u / both | 156 | 3753 | 530 | -71 | -1029 | 4108 | 2 | 367 |
| fvg5 | break | pasl_28 | {"n": 2, "k": 0.25} | sym8u / both | 170 | 3495 | 1867 | 1203 | 3141 | 2967 | 2 | 367 |
| fvg5 | break_native | pasl_28 | {"n": 2, "k": 0.0} | sym8u / both | 171 | 3227 | 1295 | 2184 | 2774 | 2661 | 2 | 367 |
| fvg5 | false_break | pasl_28 | {"M": 1, "k": 0.0} | sym8u / long | 104 | 2322 | 434 | 200 | -232 | 2472 | 2 | 367 |
| fvg5 | false_break_native | wrenko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 191 | 2772 | 705 | 209 | -285 | 2061 | 2 | 367 |
| fvg5 | reject | tm1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 127 | 2695 | 1075 | -645 | 767 | 2352 | 1 | 367 |
| fvg5 | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym15u / both | 300 | 2857 | 1827 | 1574 | 1148 | 2893 | 1 | 367 |
| fvg5 | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 219 | 3970 | -587 | 167 | 1432 | 2456 | 1 | 367 |
| fvg5 | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | plain60/60 / both | 465 | 2861 | 535 | 83 | 335 | 1538 | 1 | 367 |
| gaps | break | urenko_40 | {"n": 3, "k": 0.0} | sym8u / both | 202 | 3166 | 871 | 1141 | 833 | 5047 | 2 | 367 |
| gaps | break_native | vsess_600 | {"n": 2, "k": 0.25} | plain60/60 / both | 472 | 3782 | 294 | 168 | 135 | 4630 | 2 | 367 |
| gaps | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 271 | 3346 | 166 | 1506 | 60 | 2315 | 2 | 367 |
| gaps | false_break_native | vol_350 | {"M": 1, "k": 0.5} | asym20u/10u / both | 210 | 3204 | -597 | -1103 | 83 | 3216 | 2 | 367 |
| gaps | reject | mom_20 | {"tol": 0.0, "conf": "close"} | sym8u / both | 206 | 3721 | -510 | -2611 | -2607 | 2843 | 2 | 367 |
| gaps | reject_native | mom_20 | {"tol": 0.0, "conf": "close"} | sym8u / both | 206 | 3721 | -510 | -2611 | -2607 | 2843 | 2 | 367 |
| gaps | retest | tick_1300 | {"M": 10, "tol": 0.0} | sym8u / both | 171 | 3082 | 139 | -672 | -744 | 2136 | 2 | 367 |
| gaps | retest_native | tick_1300 | {"M": 10, "tol": 0.0} | sym8u / both | 171 | 3082 | 139 | -672 | -744 | 2136 | 2 | 367 |
| mmove | break | pnf_5 | {"n": 1, "k": 0.0} | sym8u / both | 420 | 4383 | 417 | 304 | 4120 | 4672 | 2 | 367 |
| mmove | break_native | pnf_5 | {"n": 1, "k": 0.0} | sym8u / both | 420 | 4383 | 417 | 304 | 4120 | 4672 | 2 | 367 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 2 | 367 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym8u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 2 | 367 |
| mmove | reject | urenko_10 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 492 | 3921 | -543 | 678 | -4065 | 3680 | 2 | 367 |
| mmove | reject_native | swing_atr_0.25 | {"tol": 0.5, "conf": "body"} | sym15u / both | 325 | 4412 | 247 | 955 | -1048 | 3434 | 1 | 367 |
| mmove | retest | cusum_56 | {"M": 10, "tol": 0.5} | sym15u / both | 279 | 4983 | 304 | -938 | 1973 | 3740 | 1 | 367 |
| mmove | retest_native | tick_5000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 635 | 4656 | -593 | 485 | 1386 | 4006 | 2 | 367 |
| ob15 | break | vsess_600 | {"n": 2, "k": 0.0} | asym15u/30u / both | 131 | 3654 | 942 | -28 | -992 | 2441 | 2 | 367 |
| ob15 | break_native | vsess_600 | {"n": 2, "k": 0.0} | asym15u/30u / both | 131 | 3654 | 942 | -28 | -992 | 2441 | 2 | 367 |
| ob15 | false_break | vol_1100 | {"M": 1, "k": 0.5} | sym8u / both | 121 | 3516 | -735 | -19 | 1507 | 2501 | 2 | 367 |
| ob15 | false_break_native | vib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 127 | 2853 | 631 | -828 | 317 | 2297 | 1 | 367 |
| ob15 | reject | sessrng_B320 | {"tol": 0.5, "conf": "body"} | sym15u / both | 128 | 3010 | 333 | -942 | -296 | 2287 | 1 | 367 |
| ob15 | reject_native | vsess_600 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 140 | 2541 | 249 | -1340 | -201 | 2194 | 2 | 367 |
| ob15 | retest | vol_350 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 125 | 3183 | -635 | 319 | -1377 | 2426 | 2 | 367 |
| ob15 | retest_native | time_s_5 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 3275 | 213 | -367 | -83 | 2869 | 1 | 367 |
| ob5 | break | wrenko_10 | {"n": 1, "k": 0.25} | asym10u/20u / both | 151 | 3647 | 525 | -46 | 1335 | 2450 | 2 | 367 |
| ob5 | break_native | renko_10 | {"n": 1, "k": 0.25} | asym20u/10u / both | 192 | 3659 | -258 | -81 | 297 | 2636 | 2 | 367 |
| ob5 | false_break | rng_10 | {"M": 2, "k": 0.5} | asym20u/10u / both | 194 | 2839 | 267 | -262 | -7 | 1793 | 2 | 367 |
| ob5 | false_break_native | rng_10 | {"M": 2, "k": 0.5} | asym20u/10u / both | 194 | 2920 | 589 | -536 | 2 | 1731 | 2 | 367 |
| ob5 | reject | tsf_2_200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 2770 | -252 | 383 | -372 | 3347 | 1 | 367 |
| ob5 | reject_native | lbrk_5_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 166 | 2609 | 201 | 26 | 639 | 2010 | 1 | 367 |
| ob5 | retest | vol_500 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 125 | 4330 | -1303 | -1284 | 422 | 3296 | 2 | 367 |
| ob5 | retest_native | vol_500 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 125 | 4330 | -1303 | -1284 | 422 | 3296 | 2 | 367 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 365 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 365 |
| open_range | false_break | urenko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 433 | 2504 | 701 | -141 | -115 | 1566 | 2 | 365 |
| open_range | false_break_native | mom_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 431 | 3224 | 712 | -370 | 3996 | 5609 | 2 | 365 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 365 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 365 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 365 |
| open_range | retest_native | dol_1700 | {"M": 10, "tol": 0.5} | sym15u / both | 396 | 4464 | 1014 | 1428 | -3237 | 2332 | 1 | 365 |
| opens | break | pnf_5 | {"n": 1, "k": 0.25} | sym8u / both | 417 | 5574 | 26 | -309 | 880 | 7975 | 2 | 367 |
| opens | break_native | vsess_600 | {"n": 1, "k": 0.25} | sym30u / both | 353 | 6071 | 649 | 200 | 2660 | 6158 | 2 | 367 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.0} | sym8u / both | 168 | 4705 | -460 | -329 | 1329 | 4754 | 2 | 367 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym8u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 2 | 367 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 349 | 5699 | -312 | 1439 | -2592 | 3753 | 2 | 367 |
| opens | reject_native | trb_400 | {"tol": 0.0, "conf": "close"} | sym15u / both | 344 | 5546 | -263 | 563 | 1910 | 8183 | 1 | 367 |
| opens | retest | vnorm_1500 | {"M": 3, "tol": 0.0} | sym15u / both | 292 | 5037 | -961 | 1561 | -339 | 4486 | 1 | 367 |
| opens | retest_native | vnorm_1500 | {"M": 3, "tol": 0.0} | sym15u / both | 292 | 5037 | -961 | 1561 | -339 | 4486 | 1 | 367 |
| prior_day | break | mrenko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 6470 | 806 | -1588 | 3353 | 5276 | 2 | 367 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 2 | 367 |
| prior_day | false_break | swing_atr_0.25 | {"M": 1, "k": 0.5} | sym15u / both | 200 | 6361 | 1485 | 894 | 6206 | 6268 | 2 | 367 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 2 | 367 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 367 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 367 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 367 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 367 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 367 |
| profile_nodes | break_native | swing_atr_0.15 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4157 | 1481 | -709 | -2748 | 3147 | 2 | 367 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 367 |
| profile_nodes | false_break_native | cusum_40 | {"M": 1, "k": 0.5} | sym8u / both | 224 | 4514 | -1520 | 711 | -645 | 4653 | 2 | 367 |
| profile_nodes | reject | urenko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 478 | 3792 | 537 | -2223 | -199 | 2712 | 2 | 367 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 367 |
| profile_nodes | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 367 |
| profile_nodes | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 367 |
| profile_va | break | time_s_15 | {"n": 3, "k": 0.0} | sym30u / both | 217 | 3996 | -373 | 2086 | 165 | 2934 | 2 | 367 |
| profile_va | break_native | urenko_14 | {"n": 1, "k": 0.5} | sym8u / both | 371 | 5148 | -151 | -940 | 863 | 5266 | 2 | 367 |
| profile_va | false_break | tm60 | {"M": 1, "k": 0.5} | asym15u/30u / both | 190 | 3555 | 543 | 90 | 1199 | 2542 | 2 | 367 |
| profile_va | false_break_native | tm60 | {"M": 1, "k": 0.5} | asym15u/30u / both | 170 | 3630 | 750 | -1770 | 1720 | 3066 | 2 | 367 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 2 | 367 |
| profile_va | reject_native | swing_atr_0.25 | {"tol": 0.5, "conf": "close"} | sym8u / both | 222 | 5177 | -1672 | -530 | -78 | 6694 | 2 | 367 |
| profile_va | retest | mom_20 | {"M": 3, "tol": 0.5} | sym15u / both | 192 | 3856 | 88 | 1356 | 1820 | 3081 | 2 | 367 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 367 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 485 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 485 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 485 |
| round | false_break_native | dib_3500 | {"M": 1, "k": 0.5} | asym20u/10u / both | 579 | 7357 | -777 | -1171 | -5154 | 8350 | 2 | 485 |
| round | reject | urenko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 656 | 8603 | -677 | -3216 | -3967 | 9974 | 2 | 485 |
| round | reject_native | micro_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 483 | 6202 | 1208 | 1809 | 6293 | 6823 | 1 | 485 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 485 |
| round | retest_native | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 475 | 6796 | 130 | -2984 | 617 | 3909 | 1 | 485 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 367 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 367 |
| session_hl | false_break | tsf_5_200 | {"M": 1, "k": 0.0} | sym15u / both | 304 | 5700 | 445 | 717 | 2007 | 4594 | 1 | 367 |
| session_hl | false_break_native | tsf_5_200 | {"M": 1, "k": 0.0} | sym15u / both | 304 | 5700 | 445 | 717 | 2007 | 4594 | 1 | 367 |
| session_hl | reject | lbrk_4_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 723 | 2762 | 1054 | -2325 | -1011 | 1727 | 1 | 367 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 367 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 367 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 367 |
| trendline | break | rng_14 | {"n": 3, "k": 0.25} | sym30u / both | 276 | 4545 | -251 | 2203 | 169 | 4114 | 2 | 368 |
| trendline | break_native | rng_14 | {"n": 1, "k": 0.5} | asym15u/30u / both | 291 | 4015 | 63 | 685 | 1792 | 3154 | 2 | 368 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.0} | sym8u / both | 287 | 4301 | 1436 | 831 | 1839 | 6117 | 2 | 368 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym8u / both | 275 | 4692 | 24 | 1618 | 1101 | 5496 | 2 | 368 |
| trendline | reject | anch_R0830_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 193 | 4365 | -1173 | -676 | 3045 | 5913 | 1 | 368 |
| trendline | reject_native | anch_R0830_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 193 | 4365 | -1117 | -676 | 3045 | 5913 | 1 | 368 |
| trendline | retest | vfp_vol2500 | {"M": 6, "tol": 0.5} | sym15u / both | 203 | 3963 | -17 | 1344 | 476 | 3910 | 1 | 368 |
| trendline | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 250 | 4133 | -1484 | 1143 | 2430 | 4860 | 2 | 368 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 367 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 367 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym8u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 2 | 367 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym8u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 2 | 367 |
| uw_dp | reject | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 129 | 4506 | 0 | 0 | 241 | 3031 | 1 | 367 |
| uw_dp | reject_native | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 129 | 4506 | 0 | 0 | 241 | 3031 | 1 | 367 |
| uw_dp | retest | wrenko_14 | {"M": 6, "tol": 0.0} | sym8u / both | 135 | 4422 | 0 | 0 | 353 | 4185 | 2 | 367 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 367 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 367 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym8u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 2 | 367 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 2 | 367 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym8u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 2 | 367 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 2 | 367 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 367 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 367 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 367 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 367 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 367 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 367 |
| uw_qqq | false_break_native | mrenko_14 | {"M": 1, "k": 0.5} | asym15u/30u / both | 196 | 3405 | 0 | -623 | 536 | 4401 | 2 | 367 |
| uw_qqq | reject | rngor_B200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 218 | 4150 | 0 | -273 | 2534 | 3126 | 1 | 367 |
| uw_qqq | reject_native | mrenko_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 199 | 4884 | 0 | -874 | 557 | 6493 | 2 | 367 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 367 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 367 |
| vwap | break | tsf_10_120 | {"n": 3, "k": 0.5} | sym15u / both | 300 | 5066 | 1744 | 2102 | 1335 | 5377 | 1 | 367 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 367 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.0} | sym8u / both | 179 | 4715 | 63 | -174 | 2542 | 4827 | 2 | 367 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.0} | sym8u / both | 179 | 4715 | 278 | -174 | 2542 | 4827 | 2 | 367 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 367 |
| vwap | reject_native | vnorm_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 379 | 6884 | 93 | -773 | 2670 | 8896 | 1 | 367 |
| vwap | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 364 | 5402 | 219 | -90 | 1699 | 5388 | 1 | 367 |
| vwap | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 369 | 4676 | 125 | 382 | 2643 | 3279 | 1 | 367 |
| vwap_bands | break | pnf_5 | {"n": 3, "k": 0.5} | asym20u/10u / both | 519 | 6687 | 634 | -1486 | 3449 | 5456 | 2 | 367 |
| vwap_bands | break_native | mrenko_20 | {"n": 2, "k": 0.5} | asym20u/10u / both | 493 | 6664 | 1465 | -811 | 6187 | 5774 | 2 | 367 |
| vwap_bands | false_break | pnf_5 | {"M": 1, "k": 0.5} | sym8u / both | 659 | 4836 | 1070 | 53 | -581 | 4220 | 2 | 367 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 367 |
| vwap_bands | reject | tm60 | {"tol": 1.0, "conf": "close"} | sym15u / both | 498 | 7209 | 138 | -1461 | -774 | 7274 | 2 | 367 |
| vwap_bands | reject_native | tm60 | {"tol": 0.5, "conf": "close"} | sym15u / both | 505 | 7078 | 213 | -421 | 4075 | 5878 | 2 | 367 |
| vwap_bands | retest | mrenko_14 | {"M": 10, "tol": 0.0} | sym30u / both | 435 | 5966 | 237 | 3875 | 1701 | 7092 | 2 | 367 |
| vwap_bands | retest_native | mrenko_14 | {"M": 10, "tol": 0.0} | sym30u / both | 435 | 5966 | 237 | 3875 | 1701 | 7092 | 2 | 367 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 368 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 368 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 368 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 368 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 71 | 1911 | 719 | -775 | 1482 | 1496 | 2 | 368 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 85 | 2215 | 295 | -226 | -1069 | 2264 | 2 | 368 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 368 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 368 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 367 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym8u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 2 | 367 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym8u / both | 172 | 3090 | 872 | 1937 | -2566 | 3074 | 2 | 367 |
| zones | false_break_native | dlt_45 | {"M": 1, "k": 0.5} | sym30u / both | 144 | 3507 | 511 | -1059 | -2712 | 2632 | 2 | 367 |
| zones | reject | tm600 | {"tol": 1.0, "conf": "close"} | sym8u / both | 152 | 2470 | 130 | -559 | 3477 | 2210 | 2 | 367 |
| zones | reject_native | anch_R0830_B25 | {"tol": 0.5, "conf": "body"} | sym15u / both | 144 | 3506 | -498 | -1740 | 2990 | 3437 | 1 | 367 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 367 |
| zones | retest_native | vrb_1200 | {"M": 10, "tol": 0.5} | sym15u / both | 148 | 3375 | 216 | -1398 | 298 | 3696 | 1 | 367 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 82 | 693 | -404 | 657 | 523 | 30 | 1 | 367 |
| sdx15 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 224 | 3544 | -617 | -813 | -1693 | 3292 | 1 | 367 |
| sdx15 | lim_prox | dib_3500 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 211 | 4594 | -142 | -1792 | -2175 | 4608 | 1 | 367 |
| sdx15 | rej | vfp_vol1000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 179 | 2639 | 1164 | -659 | -1144 | 1964 | 1 | 367 |
| sdx15 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 213 | 2090 | -694 | -931 | -1174 | 3194 | 1 | 367 |
| sdx15 | rej_native | vfp_t5m | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 193 | 3679 | 363 | -288 | -411 | 2943 | 1 | 367 |
| sdx15 | rej_zone | rng_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 190 | 4546 | 51 | 187 | -481 | 4555 | 1 | 367 |
| sdx15 | retest | kagi_112 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 36 | 497 | -432 | 398 | -150 | 70 | 1 | 367 |
| sdx3 | break | volor_B030 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 94 | 2267 | -833 | 836 | 2140 | 3086 | 1 | 367 |
| sdx3 | lim_mid | frenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 307 | 2583 | 1461 | -1461 | -5824 | 1823 | 1 | 367 |
| sdx3 | lim_prox | vib_2000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 390 | 3988 | 1994 | -1756 | -4769 | 3834 | 1 | 367 |
| sdx3 | rej | volor_B200 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 271 | 2154 | 1929 | 1474 | -4803 | 1483 | 1 | 367 |
| sdx3 | rej_flow | volor_B200 | {"d": "E", "F": 9} | sym15u / both | 214 | 2847 | -364 | -2077 | -2866 | 1757 | 1 | 367 |
| sdx3 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 367 |
| sdx3 | rej_zone | tsf_10_120 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 374 | 4249 | -1572 | 1376 | -3168 | 4800 | 1 | 367 |
| sdx3 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 68 | 1390 | 118 | 65 | 1080 | 1692 | 1 | 367 |
| sdx30 | break | kagi_112 | {"d": "A", "F": 9, "n": 1} | plain60/60 / both | 37 | 75 | -721 | 634 | -248 | -497 | 1 | 367 |
| sdx30 | lim_mid | volor_B030 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 102 | 2139 | 961 | -107 | -547 | 1084 | 1 | 367 |
| sdx30 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 3042 | -219 | -1016 | 531 | 2612 | 1 | 367 |
| sdx30 | rej | volor_B200 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 128 | 1226 | 102 | -516 | 103 | 1042 | 1 | 367 |
| sdx30 | rej_flow | volor_B500 | {"d": "E", "F": 9} | plain60/60 / short | 71 | 821 | 253 | -198 | -321 | 723 | 1 | 367 |
| sdx30 | rej_native | volor_B030 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 269 | 2452 | -355 | -979 | -138 | 1620 | 1 | 367 |
| sdx30 | rej_zone | mrenko_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 57 | 3495 | -353 | -627 | 874 | 2610 | 1 | 367 |
| sdx5 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 90 | 1699 | -702 | 485 | -4 | 835 | 1 | 367 |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 720 | 2734 | 720 | 3 | -3881 | 2478 | 1 | 367 |
| sdx5 | lim_prox | lbrk_5_10 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 438 | 2626 | -666 | -899 | 37 | 1803 | 1 | 367 |
| sdx5 | rej | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 262 | 2521 | -220 | 1136 | -393 | 2008 | 1 | 367 |
| sdx5 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 97 | 1766 | 159 | -855 | -1246 | 2358 | 1 | 367 |
| sdx5 | rej_native | vfp_vol2500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 555 | 2913 | 2097 | -199 | -3612 | 3497 | 1 | 367 |
| sdx5 | rej_zone | vol_4000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 362 | 3759 | 51 | -2567 | -2706 | 5488 | 1 | 367 |
| sdx5 | retest | kagi_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 82 | 1774 | -756 | -147 | -45 | 2087 | 1 | 367 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 384 | 10 | 407 | 778 | 289 | 1 | 367 |
| sdx60 | lim_mid | volor_B030 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 128 | 1703 | -112 | -859 | -41 | 1990 | 1 | 367 |
| sdx60 | lim_prox | vib_15000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 80 | 1753 | -140 | -1297 | 1261 | 1342 | 1 | 367 |
| sdx60 | rej | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 187 | 912 | 585 | -1368 | 705 | 1033 | 1 | 367 |
| sdx60 | rej_flow | vfp_vol1000 | {"d": "E", "F": 9} | sym15u / short | 30 | 770 | 19 | -111 | -16 | 1139 | 1 | 367 |
| sdx60 | rej_native | volor_B030 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 179 | 1327 | 494 | -778 | 130 | 1127 | 1 | 367 |
| sdx60 | rej_zone | tm3600 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 72 | 2676 | 119 | 118 | -1586 | 2417 | 1 | 367 |
| sdx_renko28 | break | vrb_15000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 179 | 1815 | -2399 | 1980 | 301 | 1679 | 1 | 367 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 367 |
| sdx_renko28 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 285 | 3300 | 213 | 469 | 2009 | 5781 | 1 | 367 |
| sdx_renko28 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 537 | 5198 | -406 | -1538 | 809 | 6421 | 1 | 367 |
| sdx_renko28 | rej_flow | vib_2000 | {"d": "E", "F": 9} | plain60/60 / both | 402 | 2137 | -190 | 525 | -491 | 1836 | 1 | 367 |
| sdx_renko28 | rej_native | volor_B500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 691 | 4153 | -458 | -1204 | 2099 | 5934 | 1 | 367 |
| sdx_renko28 | rej_zone | volor_B500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 691 | 4153 | -458 | -1204 | 2099 | 5934 | 1 | 367 |
| sdx_renko28 | retest | kagi_80 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 110 | 1224 | -284 | 799 | -759 | 384 | 1 | 367 |
| sdx_rng28 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 301 | 3408 | -2123 | 661 | -816 | 3058 | 1 | 367 |
| sdx_rng28 | lim_mid | vfp_vol2500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 330 | 3654 | 19 | 34 | 1564 | 1027 | 1 | 367 |
| sdx_rng28 | lim_prox | vfp_vol2500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 329 | 4034 | -769 | -145 | 590 | 84 | 1 | 367 |
| sdx_rng28 | rej | vfp_t5m | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 271 | 2513 | -388 | 1157 | 80 | 1065 | 1 | 367 |
| sdx_rng28 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 493 | 2558 | -783 | 2787 | -3819 | 2063 | 1 | 367 |
| sdx_rng28 | rej_native | volor_B030 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 308 | 2700 | 1852 | -140 | -1173 | 946 | 1 | 367 |
| sdx_rng28 | rej_zone | tsf_2_2000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 600 | 4769 | 448 | -442 | -1686 | 3536 | 1 | 367 |
| sdx_rng28 | retest | vfp_t5m | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 209 | 3215 | -949 | 611 | -1013 | 2615 | 1 | 367 |
| sdx_vol1100 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 299 | 3926 | -653 | -1247 | 590 | 4529 | 1 | 367 |
| sdx_vol1100 | lim_mid | kagi_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 275 | 3582 | -268 | -791 | -2605 | 4624 | 1 | 367 |
| sdx_vol1100 | lim_prox | volor_B500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1020 | 3867 | 535 | -461 | -2029 | 4907 | 1 | 367 |
| sdx_vol1100 | rej | vfp_vol2500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 580 | 3283 | -86 | 134 | -1331 | 2003 | 1 | 367 |
| sdx_vol1100 | rej_flow | vrb_400 | {"d": "E", "F": 0} | sym15u / short | 161 | 2399 | -174 | -1171 | -785 | 2439 | 1 | 367 |
| sdx_vol1100 | rej_native | volor_B030 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 675 | 3196 | 2352 | 2245 | -1111 | 2817 | 1 | 367 |
| sdx_vol1100 | rej_zone | tick_5000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 391 | 3880 | 1601 | -1293 | -1062 | 5402 | 1 | 367 |
| sdx_vol1100 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 227 | 3437 | -1140 | -704 | 968 | 4601 | 1 | 367 |
| fib15 | break | urenko_10 | {"n": 1, "k": 0.5} | sym30u / short | 139 | 4065 | -378 | 767 | 386 | 4634 | 2 | 367 |
| fib15 | break_native | urenko_10 | {"n": 1, "k": 0.5} | sym30u / short | 143 | 3931 | -807 | 1178 | 491 | 4660 | 2 | 367 |
| fib15 | false_break | time_s_45 | {"M": 1, "k": 0.0} | sym15u / short | 134 | 3485 | -685 | -905 | 709 | 4240 | 1 | 367 |
| fib15 | false_break_native | urenko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 317 | 3797 | 654 | -3612 | -545 | 3109 | 2 | 367 |
| fib15 | pullback | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 146 | 2537 | 38 | 763 | -1653 | 1759 | 1 | 367 |
| fib15 | pullback_native | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 146 | 2537 | 38 | 763 | -1653 | 1759 | 1 | 367 |
| fib15 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym8u / both | 246 | 4144 | 510 | -2720 | 2007 | 5507 | 2 | 367 |
| fib15 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 294 | 4584 | -969 | -1071 | -892 | 5424 | 2 | 367 |
| fib15 | retest | trb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 372 | 4012 | -1755 | -1138 | -2038 | 2975 | 1 | 367 |
| fib15 | retest_native | urenko_14 | {"M": 3, "tol": 0.5} | asym20u/10u / short | 134 | 4095 | -120 | -602 | -331 | 4881 | 2 | 367 |
| fib5 | break | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5454 | 1633 | 3169 | 1237 | 6533 | 1 | 367 |
| fib5 | break_native | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 294 | 5957 | 1611 | 1641 | 2147 | 5578 | 1 | 367 |
| fib5 | false_break | trb_2000 | {"M": 3, "k": 0.5} | sym15u / both | 273 | 5281 | -115 | -434 | 2246 | 5957 | 1 | 367 |
| fib5 | false_break_native | tick_800 | {"M": 3, "k": 0.5} | sym15u / both | 283 | 5266 | -894 | 115 | 1094 | 7007 | 1 | 367 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 2 | 367 |
| fib5 | pullback_native | drb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 2734 | -787 | 917 | -2068 | 1989 | 1 | 367 |
| fib5 | reject | vsess_200 | {"tol": 0.5, "conf": "body"} | sym8u / both | 285 | 6289 | -371 | 1437 | -1282 | 4830 | 2 | 367 |
| fib5 | reject_native | vol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 274 | 5828 | -819 | 224 | 1500 | 3983 | 1 | 367 |
| fib5 | retest | dol_750 | {"M": 3, "tol": 0.5} | sym8u / both | 291 | 5113 | -82 | -2297 | 382 | 3097 | 2 | 367 |
| fib5 | retest_native | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / both | 320 | 4654 | -1449 | -943 | 319 | 3902 | 1 | 367 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.25} | asym20u/10u / both | 163 | 4150 | -947 | 1466 | -1260 | 3182 | 2 | 367 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | asym10u/20u / both | 159 | 3742 | -922 | 524 | -1086 | 2576 | 2 | 367 |
| fib60 | false_break | rng_10 | {"M": 2, "k": 0.5} | sym15u / both | 242 | 3422 | -1420 | -398 | -943 | 3829 | 1 | 367 |
| fib60 | false_break_native | urenko_20 | {"M": 1, "k": 0.0} | sym8u / both | 218 | 3355 | -283 | -803 | -1879 | 2388 | 2 | 367 |
| fib60 | pullback | tick_300 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 122 | 1350 | -490 | -176 | 168 | 1147 | 1 | 367 |
| fib60 | pullback_native | tick_300 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 126 | 1344 | -501 | -373 | 364 | 1152 | 1 | 367 |
| fib60 | reject | vib_400 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 430 | 3691 | -673 | -1126 | -1933 | 3125 | 1 | 367 |
| fib60 | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 136 | 2932 | -434 | 1783 | -20 | 2164 | 1 | 367 |
| fib60 | retest | vib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 231 | 3703 | -145 | -5 | 635 | 3658 | 1 | 367 |
| fib60 | retest_native | mrenko_20 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 130 | 3401 | 423 | 522 | 781 | 1846 | 2 | 367 |
| fibr_dev | break | tm420 | {"n": 3, "k": 0.5} | sym15u / both | 286 | 5840 | -1477 | 6 | -302 | 4817 | 1 | 367 |
| fibr_dev | break_native | dlt_150 | {"n": 3, "k": 0.5} | sym15u / both | 316 | 4162 | -221 | -1240 | -22 | 4827 | 1 | 367 |
| fibr_dev | false_break | renko_10 | {"M": 3, "k": 0.5} | asym20u/10u / both | 547 | 3074 | -1447 | -1556 | -381 | 3901 | 2 | 367 |
| fibr_dev | false_break_native | vsess_120 | {"M": 1, "k": 0.5} | sym15u / both | 285 | 5351 | -16 | 3711 | -121 | 4820 | 2 | 367 |
| fibr_dev | reject | time_s_15 | {"tol": 1.0, "conf": "close"} | sym30u / both | 316 | 4564 | 160 | -1736 | 2488 | 4307 | 2 | 367 |
| fibr_dev | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | asym15u/30u / both | 362 | 4488 | -1137 | -2550 | -1280 | 5040 | 2 | 367 |
| fibr_dev | retest | tsf_5_1200 | {"M": 6, "tol": 0.5} | plain60/60 / both | 435 | 3723 | -543 | -245 | -71 | 3358 | 1 | 367 |
| fibr_dev | retest_native | rng_28 | {"M": 3, "tol": 0.5} | plain60/60 / both | 795 | 3595 | 1353 | -660 | 1806 | 1945 | 2 | 367 |
| fibr_ib | break | swing_pct_12 | {"n": 2, "k": 0.5} | sym8u / both | 225 | 5108 | -985 | 619 | -1064 | 5638 | 2 | 367 |
| fibr_ib | break_native | swing_pct_12 | {"n": 2, "k": 0.0} | sym8u / both | 228 | 4626 | -803 | 1423 | -1302 | 4173 | 2 | 367 |
| fibr_ib | false_break | trb_1200 | {"M": 1, "k": 0.0} | sym15u / both | 253 | 4121 | -1039 | -922 | -2846 | 5732 | 1 | 367 |
| fibr_ib | false_break_native | mrenko_20 | {"M": 1, "k": 0.5} | sym15u / both | 246 | 4146 | 17 | -2291 | 840 | 4923 | 2 | 367 |
| fibr_ib | reject | vol_500 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 274 | 3527 | -201 | -1200 | 4259 | 3690 | 2 | 367 |
| fibr_ib | reject_native | vol_500 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 274 | 3527 | -201 | -1200 | 4259 | 3690 | 2 | 367 |
| fibr_ib | retest | dltor_B080 | {"M": 3, "tol": 0.0} | sym15u / both | 233 | 4110 | -2991 | -1502 | -1483 | 4638 | 1 | 367 |
| fibr_ib | retest_native | tsf_2_700 | {"M": 6, "tol": 0.5} | sym15u / both | 255 | 4366 | -70 | 1138 | 79 | 4343 | 1 | 367 |
| fibr_on | break | entropy_B130 | {"n": 3, "k": 0.5} | sym15u / both | 214 | 3455 | -1251 | 1686 | 1793 | 2370 | 1 | 367 |
| fibr_on | break_native | tick_800 | {"n": 3, "k": 0.5} | asym10u/20u / both | 235 | 3698 | -1237 | 670 | 191 | 1831 | 2 | 367 |
| fibr_on | false_break | lbrk_4_40 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 2690 | -940 | -532 | -1545 | 4022 | 1 | 367 |
| fibr_on | false_break_native | lbrk_4_40 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 2690 | -940 | -532 | -1545 | 4022 | 1 | 367 |
| fibr_on | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym8u / both | 327 | 4816 | -680 | 2527 | -1725 | 4023 | 2 | 367 |
| fibr_on | reject_native | vsess_600 | {"tol": 0.0, "conf": "body"} | sym8u / both | 327 | 4816 | -680 | 2527 | -1725 | 4023 | 2 | 367 |
| fibr_on | retest | renko_14 | {"M": 3, "tol": 0.5} | sym30u / both | 159 | 3503 | -404 | 1165 | -237 | 2098 | 2 | 367 |
| fibr_on | retest_native | dol_2600 | {"M": 10, "tol": 0.5} | sym15u / both | 218 | 4101 | -1837 | 1375 | 655 | 5579 | 1 | 367 |
| fibr_or | break | volor_B320 | {"n": 2, "k": 0.25} | sym15u / both | 225 | 4262 | 817 | -334 | 2355 | 3432 | 1 | 367 |
| fibr_or | break_native | renko_28 | {"n": 1, "k": 0.5} | sym15u / both | 224 | 3680 | -210 | 829 | -66 | 4042 | 2 | 367 |
| fibr_or | false_break | renko_40 | {"M": 1, "k": 0.5} | sym8u / both | 204 | 3212 | -1525 | 96 | -2704 | 3700 | 2 | 367 |
| fibr_or | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 247 | 2906 | -72 | -55 | -1083 | 1423 | 2 | 367 |
| fibr_or | reject | dltor_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 219 | 3742 | 568 | 174 | -951 | 2888 | 1 | 367 |
| fibr_or | reject_native | vsess_200 | {"tol": 1.0, "conf": "close"} | sym8u / both | 253 | 3796 | 1309 | -711 | -2270 | 2585 | 2 | 367 |
| fibr_or | retest | mom_10 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 258 | 3403 | -851 | -330 | 380 | 2248 | 2 | 367 |
| fibr_or | retest_native | dib_15000 | {"M": 10, "tol": 0.5} | sym15u / both | 223 | 3519 | -276 | -921 | -282 | 3167 | 1 | 367 |
| fibr_pd | break | vfp_rng16 | {"n": 2, "k": 0.25} | plain60/60 / both | 439 | 2945 | -798 | 543 | -2719 | 2087 | 1 | 367 |
| fibr_pd | break_native | vfp_rng16 | {"n": 2, "k": 0.25} | sym15u / both | 434 | 3768 | -859 | 513 | -2779 | 2421 | 1 | 367 |
| fibr_pd | false_break | time_s_5 | {"M": 2, "k": 0.5} | asym20u/10u / both | 440 | 3124 | 622 | 637 | -1340 | 2235 | 2 | 367 |
| fibr_pd | false_break_native | time_s_5 | {"M": 2, "k": 0.5} | asym20u/10u / both | 455 | 2293 | 1494 | -298 | -1753 | 1235 | 2 | 367 |
| fibr_pd | reject | pnf_5 | {"tol": 1.0, "conf": "close"} | asym10u/20u / both | 204 | 3250 | -96 | 463 | -1341 | 4182 | 2 | 367 |
| fibr_pd | reject_native | dchg_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 3636 | -864 | -62 | -1157 | 2549 | 1 | 367 |
| fibr_pd | retest | rng_10 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 296 | 2852 | -998 | -1350 | -403 | 2990 | 2 | 367 |
| fibr_pd | retest_native | trend_80 | {"M": 10, "tol": 0.5} | sym15u / both | 153 | 3064 | -1434 | 1651 | -2201 | 3131 | 1 | 367 |
| piv_cama | break | tsf_2_700 | {"n": 2, "k": 0.25} | sym15u / both | 217 | 3325 | 165 | 3952 | 1671 | 4519 | 1 | 367 |
| piv_cama | break_native | time_s_15 | {"n": 3, "k": 0.5} | sym15u / both | 268 | 3763 | 1723 | 476 | -1879 | 4281 | 2 | 367 |
| piv_cama | false_break | rng_14 | {"M": 1, "k": 0.5} | sym30u / both | 217 | 3543 | -910 | 1346 | -790 | 2769 | 2 | 367 |
| piv_cama | false_break_native | rng_14 | {"M": 2, "k": 0.5} | sym30u / both | 224 | 3772 | -3046 | -425 | -1892 | 3843 | 2 | 367 |
| piv_cama | reject | tsf_2_100 | {"tol": 0.5, "conf": "body"} | sym15u / both | 247 | 3149 | 1430 | -1551 | -697 | 5269 | 1 | 367 |
| piv_cama | reject_native | rng_14 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 261 | 2897 | 486 | 1012 | -1793 | 2561 | 2 | 367 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 196 | 3238 | -198 | -709 | 2112 | 1687 | 2 | 367 |
| piv_cama | retest_native | tsf_2_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 206 | 3041 | -1051 | -245 | -1692 | 2625 | 1 | 367 |
| piv_floor | break | renko_28 | {"n": 3, "k": 0.25} | sym8u / both | 173 | 2872 | -1186 | 1998 | -2509 | 1566 | 2 | 367 |
| piv_floor | break_native | mom_56 | {"n": 3, "k": 0.5} | sym8u / both | 165 | 3215 | -1002 | 1217 | -641 | 2620 | 2 | 367 |
| piv_floor | false_break | renko_10 | {"M": 1, "k": 0.5} | asym15u/30u / both | 184 | 2213 | 737 | 114 | -2916 | 1001 | 2 | 367 |
| piv_floor | false_break_native | cusum_10 | {"M": 1, "k": 0.5} | asym15u/30u / both | 186 | 3184 | -2 | 683 | -3164 | 4800 | 2 | 367 |
| piv_floor | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym8u / both | 185 | 2861 | -914 | -554 | -706 | 2889 | 2 | 367 |
| piv_floor | reject_native | anch_L0200_B25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 215 | 4755 | 411 | 2328 | -3907 | 4862 | 1 | 367 |
| piv_floor | retest | renko_10 | {"M": 10, "tol": 0.5} | sym30u / both | 164 | 2398 | -61 | -2286 | -1219 | 1629 | 2 | 367 |
| piv_floor | retest_native | vol_1700 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 170 | 2715 | -1193 | 1959 | -4686 | 3120 | 2 | 367 |
| piv_wf | break | tick_500 | {"n": 3, "k": 0.25} | asym10u/20u / both | 222 | 4158 | -647 | 2145 | -509 | 4754 | 2 | 367 |
| piv_wf | break_native | tick_500 | {"n": 3, "k": 0.0} | asym10u/20u / both | 215 | 3787 | -1728 | 1576 | -218 | 3649 | 2 | 367 |
| piv_wf | false_break | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3485 | -963 | 778 | 942 | 2430 | 1 | 367 |
| piv_wf | false_break_native | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3485 | -963 | 778 | 942 | 2430 | 1 | 367 |
| piv_wf | reject | vrb_1200 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 418 | 3079 | 2011 | -84 | -469 | 1948 | 2 | 367 |
| piv_wf | reject_native | vrb_1200 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 418 | 3079 | 2011 | -84 | -469 | 1948 | 2 | 367 |
| piv_wf | retest | vol_350 | {"M": 3, "tol": 0.0} | asym15u/30u / both | 199 | 3078 | -743 | 3445 | 1071 | 6623 | 2 | 367 |
| piv_wf | retest_native | vrb_1200 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 214 | 3335 | -1232 | 2061 | -3025 | 3309 | 2 | 367 |
| swcluster | break | dltor_B030 | {"n": 2, "k": 0.25} | sym15u / both | 51 | 2170 | -961 | -414 | 557 | 2616 | 1 | 368 |
| swcluster | break_native | tib_1200 | {"n": 2, "k": 0.5} | asym10u/20u / both | 55 | 1981 | -413 | -250 | -75 | 2624 | 2 | 368 |
| swcluster | false_break | vsess_600 | {"M": 1, "k": 0.5} | asym10u/20u / both | 53 | 1301 | -228 | -337 | -1082 | 1001 | 2 | 368 |
| swcluster | false_break_native | mrenko_112 | {"M": 1, "k": 0.0} | sym15u / both | 37 | 1207 | -1095 | 1189 | -264 | 1110 | 1 | 368 |
| swcluster | reject | tick_500 | {"tol": 1.0, "conf": "body"} | sym8u / both | 54 | 2015 | 28 | 546 | 1068 | 2032 | 2 | 368 |
| swcluster | reject_native | mom_56 | {"tol": 1.0, "conf": "body"} | sym8u / both | 70 | 2031 | -335 | 901 | -2463 | 2811 | 2 | 368 |
| swcluster | retest | vol_750 | {"M": 10, "tol": 0.5} | sym15u / both | 40 | 1838 | -81 | 920 | 499 | 752 | 2 | 368 |
| swcluster | retest_native | drb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 43 | 1920 | 15 | 166 | 1327 | 1299 | 1 | 368 |
| swsr15 | break | time_m_20 | {"n": 1, "k": 0.0} | sym15u / both | 166 | 3668 | -2883 | -1482 | -14 | 3369 | 1 | 368 |
| swsr15 | break_native | kagi_20 | {"n": 1, "k": 0.25} | sym15u / both | 249 | 4161 | 651 | -2225 | 1363 | 3140 | 2 | 368 |
| swsr15 | false_break | pasl_56 | {"M": 2, "k": 0.5} | sym15u / both | 237 | 4412 | -1184 | 135 | 2943 | 2738 | 1 | 368 |
| swsr15 | false_break_native | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 237 | 3930 | -1061 | 239 | 2990 | 2256 | 1 | 368 |
| swsr15 | reject | rngor_B320 | {"tol": 1.0, "conf": "body"} | sym15u / short | 138 | 4307 | 106 | 117 | 923 | 4339 | 1 | 368 |
| swsr15 | reject_native | swing_pct_12 | {"tol": 1.0, "conf": "close"} | sym8u / both | 246 | 4867 | -12 | -1222 | -2039 | 4688 | 2 | 368 |
| swsr15 | retest | tsf_2_200 | {"M": 3, "tol": 0.0} | sym15u / both | 207 | 3995 | -575 | 301 | -635 | 3208 | 1 | 368 |
| swsr15 | retest_native | tsf_2_200 | {"M": 3, "tol": 0.0} | sym15u / both | 207 | 3995 | -575 | 301 | -635 | 3208 | 1 | 368 |
| swsr5 | break | vrb_1200 | {"n": 1, "k": 0.5} | sym15u / both | 270 | 5624 | 1255 | -598 | -133 | 7036 | 2 | 367 |
| swsr5 | break_native | vrb_1200 | {"n": 1, "k": 0.25} | sym8u / both | 326 | 6233 | -576 | 694 | -1807 | 7341 | 2 | 367 |
| swsr5 | false_break | dib_25000 | {"M": 2, "k": 0.5} | sym15u / both | 259 | 4542 | -2910 | -174 | 2213 | 5887 | 1 | 367 |
| swsr5 | false_break_native | dib_25000 | {"M": 1, "k": 0.0} | sym15u / both | 259 | 4454 | -3032 | 311 | 2477 | 6122 | 1 | 367 |
| swsr5 | reject | tib_2000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 290 | 4874 | 810 | -1129 | -3662 | 6000 | 1 | 367 |
| swsr5 | reject_native | dib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 316 | 4855 | -1006 | -2814 | 1 | 6421 | 1 | 367 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 233 | 4454 | -1674 | -1022 | 876 | 5025 | 2 | 367 |
| swsr5 | retest_native | drb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 331 | 4891 | 1457 | -2509 | 801 | 4161 | 1 | 367 |
| swsr60 | break | vrb_10000 | {"n": 2, "k": 0.25} | sym15u / both | 120 | 2607 | -1646 | 597 | -1904 | 2455 | 1 | 367 |
| swsr60 | break_native | dchg_40 | {"n": 3, "k": 0.5} | sym15u / both | 163 | 2881 | -1423 | 835 | -272 | 3349 | 1 | 367 |
| swsr60 | false_break | tm3600 | {"M": 1, "k": 0.0} | sym15u / short | 62 | 2189 | -354 | -178 | 388 | 1417 | 1 | 367 |
| swsr60 | false_break_native | renko_28 | {"M": 1, "k": 0.5} | sym15u / both | 160 | 2524 | -60 | -21 | -1678 | 1283 | 2 | 367 |
| swsr60 | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 193 | 2888 | -2041 | 250 | 1605 | 3883 | 2 | 367 |
| swsr60 | reject_native | vol_2600 | {"tol": 1.0, "conf": "close"} | sym15u / both | 209 | 4052 | -709 | -30 | -2144 | 3696 | 2 | 367 |
| swsr60 | retest | rng_80 | {"M": 6, "tol": 0.0} | sym8u / both | 102 | 2133 | -1615 | 317 | -156 | 1091 | 2 | 367 |
| swsr60 | retest_native | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 182 | 2617 | -2238 | 661 | -1997 | 3098 | 1 | 367 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | sym8u / both | 291 | 3412 | -1070 | 1079 | 1843 | -886 | 2 | 368 |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 191 | 4230 | -1307 | -208 | -2989 | 2613 | 1 | 368 |
| stack | reject | mom_40 | {"k": 2, "cw": 2.0} | sym8u / both | 188 | 3023 | -492 | -414 | 582 | 2819 | 2 | 368 |
| stack | reject_native | tsf_10_60 | {"k": 4, "cw": 2.0} | sym15u / both | 219 | 4390 | -454 | -790 | -4663 | 5642 | 1 | 368 |
| book_walls | break | time_s_10 | {"n": 1, "k": 0.25} | sym30u / both | 32 | 687 | -125 | -207 | 702 | 1091 | 2 | 366 |
| book_walls | break_native | time_s_10 | {"n": 1, "k": 0.5} | sym30u / both | 30 | 642 | 5 | -303 | 453 | 1019 | 2 | 366 |
| book_walls | reject | time_s_15 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 37 | 336 | -508 | -607 | -75 | 264 | 2 | 366 |
| book_walls | reject_native | time_s_15 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 32 | 385 | -383 | -525 | 239 | 311 | 2 | 366 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 32 | 440 | 43 | -28 | -187 | 570 | 1 | 366 |
| book_walls | retest_native | time_s_15 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 31 | 348 | -415 | -561 | 568 | 466 | 2 | 366 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 367 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 367 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 367 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 367 |
| book_walls_loose | reject | entropy_B500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 106 | 1224 | 126 | 972 | -75 | 716 | 1 | 367 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 367 |
| book_walls_loose | retest | rngor_B200 | {"M": 10, "tol": 0.5} | sym15u / both | 59 | 1173 | 89 | 361 | 1224 | 1614 | 1 | 367 |
| book_walls_loose | retest_native | vsess_300 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 57 | 1239 | -25 | 597 | -490 | 1058 | 2 | 367 |
| channel | break | rng_10 | {"n": 1, "k": 0.25} | asym20u/10u / both | 450 | 4301 | 421 | -1165 | 3188 | 3582 | 2 | 367 |
| channel | break_native | pnf_5 | {"n": 1, "k": 0.25} | sym30u / both | 306 | 5182 | 1362 | -2644 | 1792 | 6050 | 2 | 367 |
| channel | false_break | dib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 248 | 3805 | -2238 | 544 | 2799 | 4182 | 1 | 367 |
| channel | false_break_native | dib_25000 | {"M": 1, "k": 0.0} | sym15u / both | 249 | 3787 | -2213 | 309 | 2705 | 3976 | 1 | 367 |
| channel | reject | vib_3500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 288 | 4323 | -586 | 62 | -2219 | 2002 | 1 | 367 |
| channel | reject_native | cdr_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 301 | 5024 | -1519 | 276 | 1197 | 4968 | 1 | 367 |
| channel | retest | trend_56 | {"M": 10, "tol": 0.5} | sym15u / both | 193 | 4300 | -1313 | 2900 | -1969 | 4438 | 1 | 367 |
| channel | retest_native | dchg_40 | {"M": 6, "tol": 0.5} | sym15u / both | 279 | 4819 | -149 | -1202 | 1434 | 4949 | 1 | 367 |
| fvg15 | break | vib_400 | {"n": 1, "k": 0.0} | sym15u / both | 176 | 2199 | 256 | -727 | -390 | 779 | 1 | 367 |
| fvg15 | break_native | vib_400 | {"n": 1, "k": 0.0} | sym15u / both | 176 | 2199 | 256 | -727 | -390 | 779 | 1 | 367 |
| fvg15 | false_break | dlt_45 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 1913 | 181 | 348 | -211 | 772 | 1 | 367 |
| fvg15 | false_break_native | vol_350 | {"M": 1, "k": 0.5} | asym20u/10u / both | 97 | 2091 | 430 | -924 | 63 | 1377 | 2 | 367 |
| fvg15 | reject | vib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 113 | 2116 | 821 | -1469 | -150 | 2206 | 1 | 367 |
| fvg15 | reject_native | vib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 113 | 2116 | 821 | -1469 | -150 | 2206 | 1 | 367 |
| fvg15 | retest | mom_10 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 120 | 2607 | -523 | -217 | 713 | 2360 | 2 | 367 |
| fvg15 | retest_native | mom_10 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 120 | 2235 | -513 | -613 | 405 | 2362 | 2 | 367 |
| fvg5 | break | swing_pct_8 | {"n": 1, "k": 0.5} | sym8u / both | 205 | 3548 | -1606 | -169 | 872 | 2311 | 2 | 367 |
| fvg5 | break_native | swing_atr_0.4 | {"n": 3, "k": 0.5} | sym15u / both | 185 | 3348 | -1626 | -159 | -751 | 2006 | 1 | 367 |
| fvg5 | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / both | 197 | 2768 | 969 | -261 | -38 | 3569 | 2 | 367 |
| fvg5 | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 187 | 3262 | -48 | 1313 | -583 | 2949 | 2 | 367 |
| fvg5 | reject | cusum_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3711 | -316 | 1060 | -1467 | 5283 | 1 | 367 |
| fvg5 | reject_native | cusum_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3711 | -316 | 1060 | -1467 | 5283 | 1 | 367 |
| fvg5 | retest | tm240 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2929 | 148 | -1758 | -1309 | 2780 | 1 | 367 |
| fvg5 | retest_native | swing_pct_12 | {"M": 6, "tol": 0.5} | sym8u / both | 170 | 3038 | -497 | 75 | 1971 | 1948 | 2 | 367 |
| gaps | break | rng_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 117 | 2588 | -44 | 1005 | -1182 | 1826 | 2 | 367 |
| gaps | break_native | rng_14 | {"n": 1, "k": 0.25} | asym10u/20u / both | 117 | 2362 | -556 | 1239 | -1346 | 1099 | 2 | 367 |
| gaps | false_break | dlt_45 | {"M": 1, "k": 0.5} | asym15u/30u / both | 101 | 1892 | -743 | -751 | -540 | 1763 | 2 | 367 |
| gaps | false_break_native | vnorm_1500 | {"M": 2, "k": 0.5} | sym15u / both | 102 | 1911 | -1062 | 645 | -526 | 1686 | 1 | 367 |
| gaps | reject | rng_10 | {"tol": 0.0, "conf": "close"} | sym30u / both | 101 | 2480 | 1711 | -631 | 606 | 2611 | 2 | 367 |
| gaps | reject_native | dchg_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2843 | -341 | 133 | -834 | 2496 | 1 | 367 |
| gaps | retest | trb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 87 | 1928 | -507 | 132 | -112 | 1509 | 1 | 367 |
| gaps | retest_native | dchg_56 | {"M": 10, "tol": 0.5} | sym15u / both | 122 | 2650 | -494 | -94 | 420 | 1218 | 1 | 367 |
| mmove | break | swing_atr_0.6 | {"n": 1, "k": 0.0} | sym15u / both | 242 | 4100 | 306 | -544 | -435 | 3656 | 1 | 367 |
| mmove | break_native | swing_atr_0.6 | {"n": 1, "k": 0.0} | sym15u / both | 242 | 4100 | 306 | -544 | -435 | 3656 | 1 | 367 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | asym20u/10u / both | 326 | 5059 | -1240 | 376 | 248 | 5902 | 2 | 367 |
| mmove | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym8u / both | 290 | 5119 | -1034 | 882 | -460 | 3889 | 2 | 367 |
| mmove | reject | vib_40000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 195 | 2793 | -623 | 432 | 19 | 2577 | 1 | 367 |
| mmove | reject_native | dib_15000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 249 | 3357 | -1414 | 1186 | 893 | 2932 | 1 | 367 |
| mmove | retest | dib_10000 | {"M": 10, "tol": 0.5} | sym15u / both | 217 | 3850 | 613 | 1712 | -2599 | 3720 | 1 | 367 |
| mmove | retest_native | mrenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 190 | 4065 | -134 | 818 | -1533 | 5131 | 1 | 367 |
| ob15 | break | lbrk_5_20 | {"n": 1, "k": 0.0} | sym15u / both | 45 | 1746 | -751 | 882 | -716 | 2194 | 1 | 367 |
| ob15 | break_native | lbrk_5_20 | {"n": 1, "k": 0.0} | sym15u / both | 45 | 1746 | -751 | 882 | -716 | 2194 | 1 | 367 |
| ob15 | false_break | dib_700 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 2142 | 385 | 747 | -1212 | 2256 | 1 | 367 |
| ob15 | false_break_native | lbrk_5_20 | {"M": 1, "k": 0.0} | sym15u / both | 45 | 1860 | -569 | 600 | -852 | 2068 | 1 | 367 |
| ob15 | reject | tsf_5_100 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 75 | 1671 | -77 | -655 | 150 | 2147 | 1 | 367 |
| ob15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 61 | 1687 | 188 | 383 | 972 | 2727 | 2 | 367 |
| ob15 | retest | swing_atr_0.1 | {"M": 10, "tol": 0.5} | sym15u / both | 48 | 1957 | -323 | -586 | -292 | 2681 | 1 | 367 |
| ob15 | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | sym15u / both | 48 | 2000 | -495 | -508 | -590 | 2861 | 1 | 367 |
| ob5 | break | urenko_10 | {"n": 3, "k": 0.0} | sym15u / both | 81 | 2406 | -812 | 353 | 27 | 2783 | 2 | 367 |
| ob5 | break_native | urenko_10 | {"n": 3, "k": 0.0} | sym15u / both | 81 | 2406 | -812 | 353 | 27 | 2783 | 2 | 367 |
| ob5 | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym15u / both | 68 | 2342 | -21 | 333 | 1126 | 3177 | 2 | 367 |
| ob5 | false_break_native | tsf_10_30 | {"M": 2, "k": 0.5} | sym15u / both | 58 | 2155 | 526 | 884 | 2781 | 2434 | 1 | 367 |
| ob5 | reject | lbrk_5_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 67 | 2252 | 23 | 490 | 905 | 1409 | 1 | 367 |
| ob5 | reject_native | renko_40 | {"tol": 1.0, "conf": "body"} | sym8u / both | 48 | 2254 | -446 | 195 | 350 | 2574 | 2 | 367 |
| ob5 | retest | rng_10 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 82 | 2651 | -343 | 927 | 1549 | 3506 | 2 | 367 |
| ob5 | retest_native | rng_10 | {"M": 10, "tol": 0.5} | sym30u / both | 68 | 2555 | 59 | 406 | 2169 | 3721 | 2 | 367 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym8u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 2 | 367 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym8u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 2 | 367 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym8u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 2 | 367 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 367 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "body"} | sym30u / both | 212 | 4049 | -262 | 1287 | 558 | 2187 | 2 | 367 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "body"} | sym30u / both | 212 | 4049 | -262 | 1287 | 558 | 2187 | 2 | 367 |
| open_range | retest | vib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 227 | 3820 | -1654 | 280 | 218 | 3319 | 1 | 367 |
| open_range | retest_native | vfp_vol1000 | {"M": 10, "tol": 0.5} | sym15u / both | 226 | 3732 | -1504 | -416 | 1816 | 6180 | 1 | 367 |
| opens | break | time_s_15 | {"n": 1, "k": 0.5} | sym15u / both | 197 | 2969 | 256 | -555 | -115 | 4112 | 2 | 367 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 367 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 367 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 367 |
| opens | reject | cusum_10 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 177 | 2958 | 486 | 88 | 732 | 3754 | 2 | 367 |
| opens | reject_native | cusum_10 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 177 | 2958 | 486 | 88 | 732 | 3754 | 2 | 367 |
| opens | retest | dol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 124 | 3757 | -579 | 363 | -1171 | 2413 | 1 | 367 |
| opens | retest_native | dol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 124 | 3757 | -579 | 363 | -1171 | 2413 | 1 | 367 |
| prior_day | break | mom_40 | {"n": 1, "k": 0.5} | sym8u / both | 86 | 3413 | -961 | 303 | -723 | 3287 | 2 | 367 |
| prior_day | break_native | vib_15000 | {"n": 1, "k": 0.0} | sym15u / both | 89 | 3202 | -185 | -1001 | -2436 | 3301 | 1 | 367 |
| prior_day | false_break | vib_15000 | {"M": 3, "k": 0.5} | sym15u / both | 88 | 2976 | -294 | -308 | -2832 | 2657 | 1 | 367 |
| prior_day | false_break_native | trb_1200 | {"M": 3, "k": 0.5} | sym15u / both | 87 | 2890 | -317 | 530 | -1790 | 2494 | 1 | 367 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 367 |
| prior_day | reject_native | anch_N0930_B50 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 253 | 2826 | 393 | -1113 | -1711 | 3045 | 1 | 367 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 2 | 367 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 2 | 367 |
| profile_nodes | break | pnf_14 | {"n": 2, "k": 0.5} | sym8u / both | 133 | 2747 | -427 | -834 | -1477 | 2830 | 2 | 367 |
| profile_nodes | break_native | swing_pct_8 | {"n": 1, "k": 0.5} | sym8u / both | 150 | 3906 | 245 | -134 | -2849 | 2731 | 2 | 367 |
| profile_nodes | false_break | mrenko_20 | {"M": 1, "k": 0.5} | asym10u/20u / both | 136 | 2144 | -1882 | -443 | -3452 | 3022 | 2 | 367 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 367 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 367 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 367 |
| profile_nodes | retest | trb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 181 | 2629 | -801 | 1854 | -941 | 2491 | 1 | 367 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym8u / both | 128 | 2802 | -787 | 830 | -3084 | 3094 | 2 | 367 |
| profile_va | break | time_s_10 | {"n": 1, "k": 0.5} | plain60/60 / both | 218 | 2675 | 167 | -1352 | -1515 | 4084 | 2 | 367 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 367 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 367 |
| profile_va | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 113 | 1975 | -1229 | 386 | -282 | 2315 | 1 | 367 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 367 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 367 |
| profile_va | retest | vnorm_700 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2680 | -666 | 1165 | -2881 | 2087 | 1 | 367 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 367 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | asym10u/20u / both | 294 | 4870 | -1460 | 947 | 1665 | 5441 | 2 | 485 |
| round | break_native | mrenko_14 | {"n": 3, "k": 0.25} | asym20u/10u / both | 385 | 5120 | -1745 | -50 | 672 | 5770 | 2 | 485 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 485 |
| round | false_break_native | mrenko_20 | {"M": 1, "k": 0.5} | plain60/60 / both | 868 | 4752 | -1374 | 276 | -110 | 6982 | 2 | 485 |
| round | reject | bmsgq_B500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 320 | 4999 | 2058 | 1366 | -2038 | 4402 | 1 | 485 |
| round | reject_native | qmid_B130 | {"tol": 1.0, "conf": "body"} | sym15u / both | 332 | 5382 | 1274 | 778 | -622 | 5313 | 1 | 485 |
| round | retest | ha_bmsgq_B080 | {"M": 10, "tol": 0.5} | sym15u / both | 311 | 5156 | 6 | -401 | -1769 | 5881 | 1 | 485 |
| round | retest_native | t3_entropy_B200 | {"M": 6, "tol": 0.5} | sym15u / both | 344 | 5489 | -104 | 258 | 700 | 4619 | 1 | 485 |
| session_hl | break | frenko_80 | {"n": 2, "k": 0.25} | sym15u / both | 161 | 3527 | -570 | -235 | 1068 | 2358 | 1 | 367 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 367 |
| session_hl | false_break | pnf_5 | {"M": 2, "k": 0.0} | asym20u/10u / both | 224 | 3409 | 91 | -960 | 883 | 2536 | 2 | 367 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 367 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 2 | 367 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 367 |
| session_hl | retest | mom_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 246 | 3540 | -358 | -867 | 1451 | 4023 | 2 | 367 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 367 |
| trendline | break | rng_10 | {"n": 3, "k": 0.5} | sym30u / both | 234 | 3451 | 2114 | 2406 | 4533 | 3920 | 2 | 368 |
| trendline | break_native | dchg_14 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 3815 | 1336 | 2411 | 3343 | 5871 | 1 | 368 |
| trendline | false_break | renko_20 | {"M": 1, "k": 0.5} | sym15u / both | 228 | 3494 | 132 | -1254 | -1369 | 5819 | 2 | 368 |
| trendline | false_break_native | tm1200 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 3271 | -358 | -1129 | 1385 | 3744 | 1 | 368 |
| trendline | reject | rng_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 285 | 4159 | 1659 | 4 | 908 | 5310 | 2 | 368 |
| trendline | reject_native | tick_800 | {"tol": 1.0, "conf": "body"} | sym8u / both | 251 | 5198 | 914 | 2811 | 3897 | 4090 | 2 | 368 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 154 | 3629 | 447 | -1275 | 2 | 3249 | 2 | 368 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 154 | 3629 | 447 | -1275 | 2 | 3249 | 2 | 368 |
| uw_dp | break | vib_40000 | {"n": 2, "k": 0.25} | sym15u / both | 58 | 2267 | 0 | 0 | 169 | 1987 | 1 | 367 |
| uw_dp | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 61 | 2272 | 0 | 0 | 421 | 2655 | 1 | 367 |
| uw_dp | false_break | lbrk_4_40 | {"M": 1, "k": 0.0} | sym15u / both | 60 | 1770 | 0 | 0 | -50 | 1506 | 1 | 367 |
| uw_dp | false_break_native | lbrk_4_40 | {"M": 1, "k": 0.0} | sym15u / both | 60 | 1770 | 0 | 0 | -50 | 1506 | 1 | 367 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 74 | 1508 | 0 | 0 | -241 | 886 | 1 | 367 |
| uw_dp | reject_native | mom_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 90 | 2367 | 0 | 0 | -368 | 2274 | 2 | 367 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym30u / both | 47 | 2099 | 0 | 0 | 595 | 2318 | 2 | 367 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 367 |
| uw_ndx | break | urenko_10 | {"n": 3, "k": 0.25} | sym15u / both | 113 | 2964 | 0 | 144 | 1215 | 1992 | 2 | 367 |
| uw_ndx | break_native | urenko_10 | {"n": 3, "k": 0.25} | sym15u / both | 111 | 2452 | 0 | -191 | 1278 | 1349 | 2 | 367 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 367 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 367 |
| uw_ndx | reject | trend_28 | {"tol": 0.0, "conf": "close"} | sym15u / both | 84 | 2097 | 0 | -307 | 2131 | 1969 | 1 | 367 |
| uw_ndx | reject_native | trend_28 | {"tol": 0.0, "conf": "close"} | sym15u / both | 84 | 2097 | 0 | -307 | 2131 | 1969 | 1 | 367 |
| uw_ndx | retest | tib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 90 | 2531 | 0 | -546 | -895 | 2819 | 1 | 367 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 132 | 2673 | 0 | -588 | 1921 | 2632 | 2 | 367 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 367 |
| uw_qqq | break_native | vnorm_700 | {"n": 2, "k": 0.25} | sym15u / both | 101 | 2072 | 0 | 116 | -713 | 1810 | 1 | 367 |
| uw_qqq | false_break | vrb_15000 | {"M": 2, "k": 0.5} | sym15u / both | 76 | 1780 | 0 | 278 | -1194 | 1849 | 1 | 367 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 367 |
| uw_qqq | reject | time_s_20 | {"tol": 1.0, "conf": "close"} | asym10u/20u / both | 133 | 1648 | 0 | 326 | -1101 | 2301 | 2 | 367 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 367 |
| uw_qqq | retest | time_s_30 | {"M": 10, "tol": 0.0} | sym8u / both | 129 | 2110 | 0 | -54 | -511 | -338 | 2 | 367 |
| uw_qqq | retest_native | time_s_30 | {"M": 10, "tol": 0.0} | sym8u / both | 129 | 2110 | 0 | -54 | -511 | -338 | 2 | 367 |
| vwap | break | time_s_20 | {"n": 3, "k": 0.25} | sym15u / both | 185 | 4120 | -1414 | 957 | 986 | 6062 | 2 | 367 |
| vwap | break_native | tm60 | {"n": 1, "k": 0.25} | sym8u / both | 179 | 4235 | -1369 | 181 | 2368 | 5194 | 2 | 367 |
| vwap | false_break | lbrk_4_40 | {"M": 1, "k": 0.0} | sym15u / both | 144 | 3529 | -1031 | -768 | 634 | 3679 | 1 | 367 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 367 |
| vwap | reject | dib_400 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 482 | 2935 | -127 | -273 | 296 | 2916 | 2 | 367 |
| vwap | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 485 | 2414 | 212 | 64 | 1493 | 3582 | 2 | 367 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 367 |
| vwap | retest_native | trb_240 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 288 | 4238 | -932 | -1205 | -855 | 4630 | 2 | 367 |
| vwap_bands | break | tib_1200 | {"n": 2, "k": 0.0} | sym30u / both | 255 | 4129 | -1610 | 2277 | 1185 | 5000 | 2 | 367 |
| vwap_bands | break_native | tib_1200 | {"n": 2, "k": 0.0} | sym30u / both | 255 | 4129 | -1610 | 2277 | 1185 | 5000 | 2 | 367 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 367 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 367 |
| vwap_bands | reject | sessrng_B200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 279 | 4596 | 1018 | -618 | 946 | 3912 | 1 | 367 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 367 |
| vwap_bands | retest | tib_700 | {"M": 6, "tol": 0.0} | sym15u / both | 374 | 4322 | -815 | 336 | 467 | 3470 | 2 | 367 |
| vwap_bands | retest_native | sessrng_B200 | {"M": 10, "tol": 0.5} | sym15u / both | 247 | 4776 | -1852 | -2671 | -133 | 5279 | 1 | 367 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym8u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 2 | 368 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 368 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 368 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 368 |
| week_month | reject | tsf_2_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 42 | 1983 | -358 | -597 | 503 | 1654 | 1 | 368 |
| week_month | reject_native | trb_10000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 68 | 2713 | -386 | -893 | -814 | 2837 | 1 | 368 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 368 |
| week_month | retest_native | vrb_6000 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1755 | -436 | -491 | -744 | 2508 | 1 | 368 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 367 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 367 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 367 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 367 |
| zones | reject | tib_1200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 154 | 3694 | -964 | -900 | 240 | 4120 | 2 | 367 |
| zones | reject_native | tib_1200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 157 | 3134 | -1438 | -259 | 770 | 3260 | 2 | 367 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 367 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 367 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | pnf_5 | {"n": 1, "F": 2} | sym8u / both | 37 | 612 | -29 | -131 | 305 | 845 | 2 | 314 |
| sd5 | break_native | pnf_5 | {"n": 1, "F": 2} | sym8u / both | 37 | 612 | -29 | -131 | 305 | 845 | 2 | 314 |
| sd5 | reject | urenko_10 | {"F": 2, "D": 15, "tol": 0.5} | asym20u/10u / both | 30 | 720 | -153 | 107 | -152 | 821 | 2 | 314 |
| sd5 | reject_native | pnf_7 | {"F": 2, "D": 15, "tol": 0.5} | plain60/60 / both | 38 | 826 | -17 | -51 | -384 | 976 | 2 | 314 |
| sdx15 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 81 | 1034 | -22 | 94 | 1518 | 1330 | 1 | 315 |
| sdx15 | lim_mid | kagi_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 291 | 2261 | 49 | 203 | -841 | 597 | 1 | 315 |
| sdx15 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 309 | 3416 | 158 | 156 | -2451 | 1640 | 1 | 315 |
| sdx15 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 143 | 1639 | -197 | 375 | -1227 | 1202 | 1 | 315 |
| sdx15 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 53 | 1065 | -42 | -617 | -253 | 1086 | 1 | 315 |
| sdx15 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 170 | 2342 | -359 | -990 | -1569 | 2705 | 1 | 315 |
| sdx15 | rej_zone | tm780 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 261 | 2464 | -563 | -102 | -321 | 2560 | 1 | 315 |
| sdx15 | retest | kagi_112 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / long | 32 | 243 | -35 | 132 | -259 | 142 | 1 | 315 |
| sdx3 | break | lbrk_3_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 171 | 2893 | -514 | 1313 | 1662 | 2477 | 1 | 315 |
| sdx3 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 4777 | -1113 | 1932 | -2887 | 3527 | 1 | 315 |
| sdx3 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1050 | 6224 | -119 | -224 | -2213 | 5021 | 1 | 315 |
| sdx3 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 305 | 3708 | -457 | -454 | -1839 | 2258 | 1 | 315 |
| sdx3 | rej_flow | vnorm_150 | {"d": "E", "F": 9} | sym15u / both | 216 | 1710 | -491 | -990 | -519 | 1096 | 1 | 315 |
| sdx3 | rej_native | vnorm_150 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 293 | 4415 | -526 | 689 | -1903 | 2775 | 1 | 315 |
| sdx3 | rej_zone | cusum_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 466 | 5203 | -382 | -1657 | 232 | 3715 | 1 | 315 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 315 |
| sdx30 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 43 | 796 | -102 | 249 | 541 | 651 | 1 | 315 |
| sdx30 | lim_mid | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 172 | 2786 | -529 | -995 | -2174 | 1262 | 1 | 315 |
| sdx30 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 235 | 3126 | -531 | -248 | -462 | 2682 | 1 | 315 |
| sdx30 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 159 | 1658 | 62 | -1293 | -821 | 349 | 1 | 315 |
| sdx30 | rej_flow | vib_2000 | {"d": "E", "F": 9} | sym15u / short | 54 | 1340 | 43 | -381 | -434 | 1069 | 1 | 315 |
| sdx30 | rej_native | vnorm_150 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 175 | 2152 | -487 | -976 | 265 | 2048 | 1 | 315 |
| sdx30 | rej_zone | cusum_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 152 | 2161 | -350 | -561 | -1321 | 1399 | 1 | 315 |
| sdx5 | break | kagi_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 149 | 1973 | -301 | 663 | -646 | 1719 | 1 | 315 |
| sdx5 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 434 | 4411 | -88 | -1705 | -1193 | 3777 | 1 | 315 |
| sdx5 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 360 | 5056 | 283 | 711 | -1448 | 2414 | 1 | 315 |
| sdx5 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 258 | 5300 | -710 | -111 | -394 | 5406 | 1 | 315 |
| sdx5 | rej_flow | vrb_400 | {"d": "A", "F": 0} | sym15u / short | 85 | 1536 | 62 | 117 | -551 | 1336 | 1 | 315 |
| sdx5 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 284 | 4619 | -598 | -24 | -1073 | 5324 | 1 | 315 |
| sdx5 | rej_zone | vib_2000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 323 | 3900 | -618 | -933 | -1468 | 1471 | 1 | 315 |
| sdx5 | retest | kagi_40 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / short | 93 | 1465 | -6 | -476 | -174 | 1868 | 1 | 315 |
| sdx60 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 43 | 226 | -88 | 30 | 16 | 342 | 1 | 315 |
| sdx60 | lim_mid | vrb_240 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 39 | 1310 | -9 | -118 | -1023 | 1384 | 1 | 315 |
| sdx60 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "r2"} | OWN zone/level bracket / both | 42 | 1589 | -33 | -202 | -24 | 1504 | 2 | 315 |
| sdx60 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 46 | 2005 | -46 | -249 | 40 | 1993 | 1 | 315 |
| sdx60 | rej_flow | vib_2000 | {"d": "E", "F": 9} | sym15u / short | 43 | 1347 | -2 | -515 | -582 | 1719 | 1 | 315 |
| sdx60 | rej_native | kagi_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 49 | 1982 | -33 | -209 | -422 | 2270 | 1 | 315 |
| sdx60 | rej_zone | mrenko_20 | {"d": "A", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 68 | 2062 | 78 | -655 | 535 | 2364 | 2 | 315 |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 182 | 3218 | 348 | 613 | 1501 | 3608 | 1 | 315 |
| sdx_renko28 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 335 | 3926 | -225 | -191 | -3870 | 3498 | 1 | 315 |
| sdx_renko28 | lim_prox | lbrk_3_10 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 662 | 2912 | -201 | -940 | -2867 | 3744 | 2 | 315 |
| sdx_renko28 | rej | vnorm_150 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 249 | 2410 | -124 | 111 | -2649 | 459 | 1 | 315 |
| sdx_renko28 | rej_flow | vnorm_150 | {"d": "E", "F": 9} | sym15u / both | 147 | 2444 | 148 | -296 | -1061 | 2579 | 1 | 315 |
| sdx_renko28 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 311 | 2346 | -542 | -2719 | -1881 | 69 | 1 | 315 |
| sdx_renko28 | rej_zone | rng_10 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 715 | 3555 | 4 | -615 | -2122 | 2404 | 1 | 315 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2189 | 230 | -226 | -1251 | 1966 | 1 | 315 |
| sdx_rng28 | break | vib_2000 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 747 | 4370 | -276 | -176 | 36 | 4671 | 1 | 315 |
| sdx_rng28 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 386 | 3058 | -130 | 896 | 302 | 1004 | 1 | 315 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 315 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 180 | 4551 | 663 | 859 | -858 | 6367 | 1 | 315 |
| sdx_rng28 | rej_flow | vib_2000 | {"d": "E", "F": 9} | plain60/60 / both | 623 | 3383 | -664 | -794 | -1356 | 1930 | 1 | 315 |
| sdx_rng28 | rej_native | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 345 | 2502 | 360 | 1558 | -1448 | 196 | 1 | 315 |
| sdx_rng28 | rej_zone | dol_350 | {"d": "E", "F": 0, "tgt": "r2"} | OWN zone/level bracket / both | 1583 | 3991 | -425 | -288 | -2143 | 2791 | 2 | 315 |
| sdx_rng28 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 447 | 3522 | -103 | 677 | -611 | 2695 | 1 | 315 |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 392 | 3031 | 130 | 198 | 714 | 2880 | 1 | 315 |
| sdx_vol1100 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 344 | 2953 | 435 | 1021 | -2285 | 3126 | 1 | 315 |
| sdx_vol1100 | lim_prox | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 334 | 4466 | -175 | -58 | -998 | 5680 | 1 | 315 |
| sdx_vol1100 | rej | vib_2000 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 293 | 4080 | 627 | -676 | -695 | 3601 | 1 | 315 |
| sdx_vol1100 | rej_flow | vib_2000 | {"d": "E", "F": 0} | sym15u / both | 222 | 2313 | -438 | -179 | -910 | 3473 | 1 | 315 |
| sdx_vol1100 | rej_native | vib_2000 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 309 | 4029 | 295 | -988 | -1153 | 3222 | 1 | 315 |
| sdx_vol1100 | rej_zone | cusum_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 306 | 3386 | -436 | -440 | -706 | 2776 | 1 | 315 |
| sdx_vol1100 | retest | vib_2000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 150 | 1675 | 189 | -91 | 668 | 1607 | 1 | 315 |
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 664 | 4358 | 1020 | 111 | 108 | 5473 | 1 | 315 |
| fib15 | break_native | vrb_3500 | {"n": 1, "k": 0.0} | plain60/60 / both | 484 | 3792 | -532 | 1190 | 587 | 3068 | 1 | 315 |
| fib15 | false_break | time_s_15 | {"M": 1, "k": 0.0} | sym15u / both | 744 | 4428 | -1523 | -1122 | -984 | 4812 | 1 | 315 |
| fib15 | false_break_native | urenko_14 | {"M": 1, "k": 0.5} | asym15u/30u / both | 305 | 4705 | 531 | 513 | 309 | 5986 | 2 | 315 |
| fib15 | pullback | vsess_50 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 318 | 3324 | -457 | -527 | 77 | 2115 | 1 | 315 |
| fib15 | pullback_native | vsess_50 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 356 | 3930 | -915 | 75 | 7 | 2275 | 1 | 315 |
| fib15 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 286 | 3594 | 629 | -308 | 751 | 5758 | 2 | 315 |
| fib15 | reject_native | mrenko_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 328 | 3995 | 614 | -21 | -258 | 4164 | 2 | 315 |
| fib15 | retest | cusum_80 | {"M": 6, "tol": 0.5} | sym15u / both | 224 | 3983 | -247 | 278 | 481 | 3510 | 1 | 315 |
| fib15 | retest_native | urenko_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 314 | 4876 | 285 | -463 | 837 | 4724 | 2 | 315 |
| fib5 | break | frenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 269 | 4024 | 255 | 749 | 270 | 4948 | 1 | 315 |
| fib5 | break_native | frenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 1033 | 4222 | -685 | -939 | -690 | 3285 | 1 | 315 |
| fib5 | false_break | vsess_30 | {"M": 3, "k": 0.5} | sym15u / both | 319 | 4950 | 305 | -527 | 1711 | 5618 | 1 | 315 |
| fib5 | false_break_native | vol_4000 | {"M": 1, "k": 0.0} | sym15u / both | 294 | 4515 | -170 | 1754 | 1432 | 4673 | 1 | 315 |
| fib5 | pullback | vsess_300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 432 | 4321 | -117 | -2350 | -621 | 3568 | 2 | 315 |
| fib5 | pullback_native | mrenko_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 413 | 5095 | 129 | -1238 | -162 | 7277 | 1 | 315 |
| fib5 | reject | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 229 | 4892 | 475 | 656 | -543 | 5747 | 1 | 315 |
| fib5 | reject_native | rng_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 280 | 4572 | -215 | 889 | -1110 | 4953 | 1 | 315 |
| fib5 | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 315 |
| fib5 | retest_native | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 315 |
| fib60 | break | urenko_14 | {"n": 3, "k": 0.5} | asym20u/10u / both | 296 | 5269 | -12 | -231 | 1632 | 6299 | 2 | 315 |
| fib60 | break_native | urenko_14 | {"n": 3, "k": 0.25} | asym20u/10u / both | 297 | 5260 | -313 | -211 | 984 | 5803 | 2 | 315 |
| fib60 | false_break | lbrk_5_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 360 | 3487 | 195 | 1384 | 3 | 4074 | 1 | 315 |
| fib60 | false_break_native | vib_400 | {"M": 3, "k": 0.5} | sym15u / both | 432 | 3687 | 162 | -402 | 1352 | 4173 | 1 | 315 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 127 | 2980 | 92 | 236 | -1394 | 3644 | 2 | 315 |
| fib60 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 149 | 2871 | 380 | 344 | -1240 | 3551 | 2 | 315 |
| fib60 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 279 | 5055 | 422 | -1153 | -276 | 5536 | 2 | 315 |
| fib60 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 283 | 4177 | 118 | -368 | -74 | 5093 | 2 | 315 |
| fib60 | retest | urenko_10 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 308 | 3020 | -63 | -797 | -979 | 2840 | 2 | 315 |
| fib60 | retest_native | vol_750 | {"M": 10, "tol": 0.5} | plain60/60 / both | 499 | 3584 | -227 | -506 | -608 | 4451 | 1 | 315 |
| fibr_dev | break | pnf_14 | {"n": 1, "k": 0.5} | sym8u / both | 312 | 4017 | 303 | 1221 | 1354 | 4053 | 2 | 315 |
| fibr_dev | break_native | pasl_20 | {"n": 1, "k": 0.0} | sym15u / both | 325 | 3487 | 337 | -211 | -1561 | 3962 | 1 | 315 |
| fibr_dev | false_break | time_s_15 | {"M": 3, "k": 0.5} | asym10u/20u / both | 810 | 4294 | -943 | 1034 | -5635 | 3340 | 2 | 315 |
| fibr_dev | false_break_native | pnf_14 | {"M": 2, "k": 0.0} | sym8u / both | 315 | 3919 | 868 | 1092 | 899 | 3916 | 2 | 315 |
| fibr_dev | reject | mrenko_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 366 | 4533 | -86 | -1726 | -2992 | 5092 | 2 | 315 |
| fibr_dev | reject_native | vol_1700 | {"tol": 0.5, "conf": "close"} | sym8u / both | 322 | 4880 | 156 | -1764 | 653 | 5807 | 2 | 315 |
| fibr_dev | retest | urenko_14 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 328 | 4870 | 31 | -1544 | 1884 | 3311 | 2 | 315 |
| fibr_dev | retest_native | urenko_14 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 328 | 4870 | 31 | -1544 | 1884 | 3311 | 2 | 315 |
| fibr_ib | break | tsf_10_120 | {"n": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 315 |
| fibr_ib | break_native | tsf_10_120 | {"n": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 315 |
| fibr_ib | false_break | vnorm_40 | {"M": 3, "k": 0.5} | plain60/60 / both | 70 | 1392 | -102 | 578 | 387 | 1289 | 1 | 315 |
| fibr_ib | false_break_native | tsf_10_120 | {"M": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 315 |
| fibr_ib | reject | tib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 48 | 1387 | -172 | 179 | 115 | 1737 | 1 | 315 |
| fibr_ib | reject_native | dol_4000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 49 | 1484 | 108 | -227 | -662 | 1896 | 1 | 315 |
| fibr_ib | retest | tib_40000 | {"M": 6, "tol": 0.5} | sym15u / both | 35 | 1852 | -259 | -56 | 317 | 2356 | 1 | 315 |
| fibr_ib | retest_native | tib_40000 | {"M": 6, "tol": 0.5} | sym15u / both | 46 | 1753 | -130 | -119 | 676 | 2334 | 1 | 315 |
| fibr_on | break | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 64 | 1852 | 130 | 1064 | 1266 | 2317 | 1 | 315 |
| fibr_on | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 64 | 1852 | 130 | 1064 | 1266 | 2317 | 1 | 315 |
| fibr_on | false_break | vib_70000 | {"M": 2, "k": 0.5} | sym15u / both | 63 | 1972 | 4 | 965 | 1280 | 2438 | 1 | 315 |
| fibr_on | false_break_native | vib_70000 | {"M": 3, "k": 0.5} | sym15u / both | 59 | 1909 | 61 | 856 | 1398 | 2451 | 1 | 315 |
| fibr_on | reject | trb_10000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 51 | 1325 | 37 | 188 | 90 | 1432 | 1 | 315 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym8u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 2 | 315 |
| fibr_on | retest | time_m_60 | {"M": 10, "tol": 0.5} | sym15u / both | 50 | 1320 | 338 | 170 | -197 | 1798 | 1 | 315 |
| fibr_on | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 43 | 1379 | 241 | -496 | 279 | 1605 | 1 | 315 |
| fibr_or | break | urenko_80 | {"n": 1, "k": 0.25} | sym8u / both | 73 | 1315 | 58 | -108 | 446 | 2401 | 2 | 315 |
| fibr_or | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 352 | 342 | 362 | 760 | 1 | 315 |
| fibr_or | false_break | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 353 | 342 | 362 | 760 | 1 | 315 |
| fibr_or | false_break_native | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 353 | 342 | 362 | 760 | 1 | 315 |
| fibr_or | reject | tsf_10_250 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1219 | -13 | -154 | -144 | 1109 | 1 | 315 |
| fibr_or | reject_native | pasl_28 | {"tol": 0.5, "conf": "close"} | sym8u / both | 46 | 1249 | -196 | 286 | -615 | 1305 | 2 | 315 |
| fibr_or | retest | urenko_80 | {"M": 10, "tol": 0.0} | sym8u / both | 53 | 1198 | 240 | -1200 | 233 | 1688 | 2 | 315 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym8u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 2 | 315 |
| fibr_pd | break | urenko_14 | {"n": 1, "k": 0.25} | sym8u / both | 478 | 5765 | -299 | -887 | 917 | 6729 | 2 | 315 |
| fibr_pd | break_native | vsess_450 | {"n": 3, "k": 0.5} | sym15u / both | 350 | 5703 | 131 | 312 | -212 | 5343 | 1 | 315 |
| fibr_pd | false_break | urenko_14 | {"M": 2, "k": 0.5} | sym8u / both | 502 | 4337 | -1072 | -1283 | 1146 | 5343 | 2 | 315 |
| fibr_pd | false_break_native | urenko_14 | {"M": 1, "k": 0.0} | sym8u / both | 502 | 4241 | -1138 | -1686 | 744 | 5361 | 2 | 315 |
| fibr_pd | reject | dlt_30 | {"tol": 0.0, "conf": "close"} | sym15u / both | 315 | 5341 | -282 | -568 | 864 | 6484 | 1 | 315 |
| fibr_pd | reject_native | dlt_30 | {"tol": 0.0, "conf": "close"} | sym15u / both | 315 | 5341 | -282 | -568 | 864 | 6484 | 1 | 315 |
| fibr_pd | retest | rng_10 | {"M": 10, "tol": 0.5} | sym15u / both | 335 | 4058 | -172 | -789 | -1006 | 2492 | 2 | 315 |
| fibr_pd | retest_native | vol_4000 | {"M": 6, "tol": 0.0} | sym8u / both | 170 | 3581 | -133 | 288 | 1428 | 5231 | 2 | 315 |
| piv_cama | break | dol_1100 | {"n": 1, "k": 0.0} | plain60/60 / both | 676 | 4396 | 242 | 1245 | -711 | 4607 | 1 | 315 |
| piv_cama | break_native | dol_1100 | {"n": 1, "k": 0.0} | plain60/60 / both | 676 | 4396 | 242 | 1245 | -711 | 4607 | 1 | 315 |
| piv_cama | false_break | tm30 | {"M": 1, "k": 0.0} | plain60/60 / both | 756 | 4458 | -1001 | -1262 | -3016 | 4644 | 1 | 315 |
| piv_cama | false_break_native | tm30 | {"M": 1, "k": 0.0} | plain60/60 / both | 756 | 4458 | -1001 | -1262 | -3016 | 4644 | 1 | 315 |
| piv_cama | reject | vol_750 | {"tol": 1.0, "conf": "close"} | asym10u/20u / both | 319 | 4729 | 80 | -1224 | 383 | 5394 | 2 | 315 |
| piv_cama | reject_native | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 524 | 4514 | -959 | 162 | 2233 | 5173 | 1 | 315 |
| piv_cama | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | plain60/60 / both | 762 | 3986 | -81 | -205 | -81 | 4658 | 1 | 315 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 2 | 315 |
| piv_floor | break | urenko_14 | {"n": 1, "k": 0.0} | sym8u / both | 382 | 4710 | 141 | -334 | 1289 | 6038 | 2 | 315 |
| piv_floor | break_native | urenko_14 | {"n": 1, "k": 0.0} | sym8u / both | 382 | 4710 | 141 | -334 | 1289 | 6038 | 2 | 315 |
| piv_floor | false_break | renko_14 | {"M": 1, "k": 0.0} | sym8u / both | 421 | 4030 | -789 | -1381 | 163 | 4832 | 2 | 315 |
| piv_floor | false_break_native | vsess_600 | {"M": 2, "k": 0.5} | sym8u / both | 505 | 4114 | -1401 | -606 | 320 | 3891 | 2 | 315 |
| piv_floor | reject | time_m_13 | {"tol": 0.5, "conf": "body"} | sym15u / both | 175 | 2989 | 709 | -2785 | -305 | 2717 | 1 | 315 |
| piv_floor | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 314 | 3167 | -34 | -152 | -1376 | 4319 | 2 | 315 |
| piv_floor | retest | rng_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 256 | 4437 | -302 | -263 | 511 | 3370 | 2 | 315 |
| piv_floor | retest_native | rng_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 256 | 4437 | -302 | -263 | 511 | 3370 | 2 | 315 |
| piv_wf | break | cdr_160 | {"n": 1, "k": 0.0} | plain60/60 / both | 498 | 3875 | -460 | 975 | 1229 | 4152 | 1 | 315 |
| piv_wf | break_native | vsess_600 | {"n": 1, "k": 0.25} | asym20u/10u / both | 383 | 3937 | -644 | -270 | 86 | 4247 | 2 | 315 |
| piv_wf | false_break | mom_80 | {"M": 1, "k": 0.0} | plain60/60 / both | 463 | 3491 | -457 | 754 | 1343 | 3641 | 1 | 315 |
| piv_wf | false_break_native | vsess_200 | {"M": 2, "k": 0.5} | sym8u / both | 424 | 3756 | -1283 | -250 | -620 | 5426 | 2 | 315 |
| piv_wf | reject | rng_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 350 | 4928 | -45 | -2724 | -1189 | 4016 | 2 | 315 |
| piv_wf | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 353 | 5058 | -169 | -1885 | -1437 | 4138 | 2 | 315 |
| piv_wf | retest | rng_20 | {"M": 10, "tol": 0.0} | plain60/60 / both | 454 | 3566 | -208 | -967 | -448 | 4765 | 2 | 315 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 2 | 315 |
| swcluster | break | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 58 | 1626 | -278 | 139 | 621 | 1919 | 2 | 315 |
| swcluster | break_native | urenko_10 | {"n": 2, "k": 0.0} | sym15u / both | 56 | 1563 | -267 | -461 | -723 | 1886 | 2 | 315 |
| swcluster | false_break | vsess_450 | {"M": 2, "k": 0.5} | sym15u / both | 66 | 2023 | -73 | -439 | 1036 | 2700 | 1 | 315 |
| swcluster | false_break_native | vsess_450 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1700 | -195 | -307 | 1232 | 2370 | 1 | 315 |
| swcluster | reject | time_s_20 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 70 | 1465 | -216 | 11 | -482 | 514 | 2 | 315 |
| swcluster | reject_native | time_s_20 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 70 | 1465 | -216 | 11 | -482 | 514 | 2 | 315 |
| swcluster | retest | drb_400 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 47 | 1940 | -18 | 50 | -70 | 2287 | 2 | 315 |
| swcluster | retest_native | drb_400 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 49 | 1940 | 16 | -65 | -149 | 2378 | 2 | 315 |
| swsr15 | break | mrenko_28 | {"n": 3, "k": 0.5} | plain60/60 / both | 574 | 3791 | -645 | 1502 | -523 | 5252 | 1 | 315 |
| swsr15 | break_native | vsess_600 | {"n": 1, "k": 0.25} | sym15u / both | 392 | 3619 | 209 | -1220 | -45 | 3614 | 2 | 315 |
| swsr15 | false_break | rng_14 | {"M": 1, "k": 0.5} | sym30u / both | 306 | 3229 | -67 | -1774 | -293 | 4938 | 2 | 315 |
| swsr15 | false_break_native | rng_40 | {"M": 1, "k": 0.5} | sym8u / both | 265 | 4348 | -242 | -912 | -1026 | 5583 | 2 | 315 |
| swsr15 | reject | vnorm_80 | {"tol": 0.5, "conf": "body"} | sym15u / both | 215 | 3510 | -164 | -304 | 405 | 3543 | 1 | 315 |
| swsr15 | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 319 | 3412 | -517 | -1304 | -3026 | 1459 | 2 | 315 |
| swsr15 | retest | rng_14 | {"M": 3, "tol": 0.0} | sym8u / both | 405 | 4649 | 96 | -498 | -521 | 4416 | 2 | 315 |
| swsr15 | retest_native | rng_14 | {"M": 3, "tol": 0.0} | sym8u / both | 405 | 4649 | 96 | -498 | -521 | 4416 | 2 | 315 |
| swsr5 | break | rng_56 | {"n": 2, "k": 0.25} | sym8u / both | 307 | 4537 | 869 | 244 | 2603 | 6436 | 2 | 315 |
| swsr5 | break_native | rng_14 | {"n": 3, "k": 0.25} | asym10u/20u / both | 400 | 4526 | 332 | -615 | 3218 | 4400 | 2 | 315 |
| swsr5 | false_break | rng_56 | {"M": 1, "k": 0.5} | sym8u / both | 312 | 4751 | 75 | 91 | 2414 | 3848 | 2 | 315 |
| swsr5 | false_break_native | urenko_56 | {"M": 1, "k": 0.5} | sym8u / both | 261 | 5000 | 423 | 799 | 954 | 3906 | 2 | 315 |
| swsr5 | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym10u/20u / both | 353 | 4235 | 284 | 440 | 3082 | 2922 | 2 | 315 |
| swsr5 | reject_native | vrb_3500 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 546 | 3929 | 150 | 374 | 1458 | 4745 | 1 | 315 |
| swsr5 | retest | mom_28 | {"M": 6, "tol": 0.0} | sym8u / both | 296 | 4838 | 143 | -1042 | 322 | 5257 | 2 | 315 |
| swsr5 | retest_native | mom_28 | {"M": 6, "tol": 0.0} | sym8u / both | 296 | 4838 | 143 | -1042 | 322 | 5257 | 2 | 315 |
| swsr60 | break | dib_6000 | {"n": 2, "k": 0.25} | sym15u / both | 191 | 3147 | 12 | -785 | 841 | 3304 | 1 | 315 |
| swsr60 | break_native | frenko_10 | {"n": 1, "k": 0.0} | sym15u / both | 405 | 2846 | -549 | 57 | -663 | 3481 | 1 | 315 |
| swsr60 | false_break | rng_14 | {"M": 1, "k": 0.0} | sym8u / both | 334 | 3523 | -235 | -101 | 192 | 5242 | 2 | 315 |
| swsr60 | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 253 | 4204 | -609 | -318 | 70 | 4747 | 2 | 315 |
| swsr60 | reject | tick_300 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 193 | 2146 | -293 | -1139 | 453 | 2049 | 2 | 315 |
| swsr60 | reject_native | drb_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 138 | 2419 | 2 | 356 | -367 | 2198 | 1 | 315 |
| swsr60 | retest | tick_3200 | {"M": 3, "tol": 0.5} | sym8u / both | 101 | 2504 | 211 | 38 | -77 | 818 | 2 | 315 |
| swsr60 | retest_native | time_m_1 | {"M": 3, "tol": 0.0} | sym15u / both | 172 | 2338 | -260 | -260 | 1015 | 2495 | 1 | 315 |
| stack | break | mom_20 | {"k": 3, "cw": 1.0} | sym15u / both | 158 | 4433 | -1105 | 219 | 562 | 4615 | 1 | 315 |
| stack | break_native | tib_400 | {"k": 3, "cw": 1.0} | sym15u / both | 265 | 4834 | 101 | 499 | 821 | 5224 | 1 | 315 |
| stack | reject | vnorm_400 | {"k": 2, "cw": 0.5} | sym15u / both | 228 | 3849 | -351 | -291 | -274 | 1905 | 1 | 315 |
| stack | reject_native | vnorm_80 | {"k": 3, "cw": 1.0} | sym15u / both | 266 | 3272 | -113 | -258 | -1952 | 383 | 1 | 315 |
| book_walls | break | time_s_45 | {"n": 1, "k": 0.0} | sym30u / both | 103 | 1859 | -200 | 208 | 718 | 1460 | 2 | 312 |
| book_walls | break_native | time_s_45 | {"n": 1, "k": 0.0} | sym30u / both | 103 | 1859 | -203 | 208 | 718 | 1460 | 2 | 312 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 312 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 312 |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym30u / both | 120 | 2180 | 330 | -195 | -753 | 2111 | 2 | 312 |
| book_walls | reject_native | time_s_45 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 150 | 2087 | -108 | -849 | -1399 | 2303 | 2 | 312 |
| book_walls | retest | time_s_20 | {"M": 3, "tol": 0.5} | sym30u / both | 125 | 1646 | -535 | 663 | 1320 | 2184 | 2 | 312 |
| book_walls | retest_native | time_s_10 | {"M": 3, "tol": 0.5} | sym30u / both | 142 | 1452 | -1160 | -124 | -1041 | 2053 | 2 | 312 |
| book_walls_loose | break | time_s_20 | {"n": 3, "k": 0.5} | sym30u / both | 238 | 3990 | -795 | -1389 | 1328 | 3703 | 2 | 314 |
| book_walls_loose | break_native | time_s_20 | {"n": 2, "k": 0.25} | sym30u / both | 236 | 3824 | -918 | -1217 | -251 | 3076 | 2 | 314 |
| book_walls_loose | false_break | vib_2000 | {"M": 3, "k": 0.5} | sym15u / both | 77 | 2023 | -1249 | -345 | -729 | 1888 | 1 | 314 |
| book_walls_loose | false_break_native | vib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1916 | -467 | -943 | 49 | 1098 | 1 | 314 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 332 | 3647 | -618 | -483 | -2918 | 4293 | 1 | 314 |
| book_walls_loose | reject_native | tm45 | {"tol": 1.0, "conf": "close"} | sym8u / both | 472 | 3369 | -1222 | -1894 | -1381 | 3326 | 2 | 314 |
| book_walls_loose | retest | time_s_15 | {"M": 6, "tol": 0.5} | asym15u/30u / both | 347 | 2857 | -1073 | -2456 | -2375 | 3612 | 2 | 314 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym30u / both | 268 | 2810 | 735 | -412 | -3504 | 3056 | 2 | 314 |
| channel | break | urenko_14 | {"n": 2, "k": 0.0} | sym8u / both | 562 | 5057 | 18 | -584 | 2852 | 5080 | 2 | 315 |
| channel | break_native | urenko_14 | {"n": 2, "k": 0.0} | sym8u / both | 562 | 5057 | 18 | -584 | 2852 | 5080 | 2 | 315 |
| channel | false_break | vsess_120 | {"M": 2, "k": 0.5} | sym15u / both | 355 | 5457 | -533 | 462 | 2268 | 5288 | 2 | 315 |
| channel | false_break_native | vib_15000 | {"M": 1, "k": 0.0} | sym15u / both | 295 | 5084 | 318 | 92 | 513 | 5119 | 1 | 315 |
| channel | reject | vsess_600 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 357 | 5310 | -323 | -934 | -2058 | 4288 | 2 | 315 |
| channel | reject_native | vsess_600 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 357 | 5310 | -323 | -934 | -2058 | 4288 | 2 | 315 |
| channel | retest | vol_350 | {"M": 10, "tol": 0.5} | sym8u / both | 343 | 4297 | -202 | -15 | 1756 | 3940 | 2 | 315 |
| channel | retest_native | vsess_600 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 357 | 4849 | -332 | -141 | 70 | 5483 | 2 | 315 |
| fvg15 | break | vsess_80 | {"n": 1, "k": 0.0} | sym15u / both | 186 | 5006 | -38 | 54 | 1696 | 5214 | 1 | 315 |
| fvg15 | break_native | vsess_80 | {"n": 1, "k": 0.0} | sym15u / both | 186 | 5006 | -38 | 54 | 1696 | 5214 | 1 | 315 |
| fvg15 | false_break | vol_750 | {"M": 2, "k": 0.5} | sym8u / both | 183 | 5066 | -476 | 933 | 676 | 4875 | 2 | 315 |
| fvg15 | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 174 | 5186 | 122 | -301 | 2084 | 4374 | 1 | 315 |
| fvg15 | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym15u / both | 208 | 3047 | -638 | -728 | 667 | 3182 | 2 | 315 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 213 | 3723 | -565 | -32 | 392 | 4326 | 2 | 315 |
| fvg15 | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 4311 | -153 | 822 | -98 | 4262 | 1 | 315 |
| fvg15 | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 178 | 4081 | -555 | 1076 | -732 | 4005 | 1 | 315 |
| fvg5 | break | rng_14 | {"n": 1, "k": 0.25} | sym15u / both | 281 | 5292 | -198 | -519 | 914 | 8489 | 2 | 315 |
| fvg5 | break_native | rng_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 339 | 4284 | -249 | -531 | 555 | 5417 | 2 | 315 |
| fvg5 | false_break | time_s_15 | {"M": 1, "k": 0.5} | sym15u / both | 470 | 4365 | -507 | 416 | -1974 | 3555 | 2 | 315 |
| fvg5 | false_break_native | renko_10 | {"M": 2, "k": 0.5} | asym20u/10u / both | 374 | 4168 | -514 | -760 | -2318 | 3297 | 2 | 315 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 315 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 315 |
| fvg5 | retest | rng_14 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 295 | 3786 | -310 | -1291 | -2350 | 3812 | 2 | 315 |
| fvg5 | retest_native | rng_14 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 295 | 3786 | -310 | -1291 | -2350 | 3812 | 2 | 315 |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 203 | 4918 | 175 | 1622 | -134 | 4280 | 2 | 315 |
| gaps | break_native | rng_14 | {"n": 2, "k": 0.25} | sym30u / both | 204 | 4873 | -73 | 1174 | -1762 | 5112 | 2 | 315 |
| gaps | false_break | swing_atr_0.15 | {"M": 1, "k": 0.0} | plain60/60 / both | 427 | 4246 | -448 | -197 | 465 | 5311 | 2 | 315 |
| gaps | false_break_native | swing_atr_0.15 | {"M": 1, "k": 0.0} | plain60/60 / both | 427 | 4246 | -448 | -197 | 465 | 5311 | 2 | 315 |
| gaps | reject | renko_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 165 | 2926 | -291 | -70 | 673 | 2969 | 2 | 315 |
| gaps | reject_native | renko_14 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 171 | 3622 | -453 | 303 | 1417 | 3943 | 2 | 315 |
| gaps | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 231 | 2841 | -237 | -914 | -2219 | 2400 | 2 | 315 |
| gaps | retest_native | dchg_14 | {"M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2877 | 380 | -475 | 340 | 2584 | 1 | 315 |
| mmove | break | urenko_10 | {"n": 3, "k": 0.5} | asym20u/10u / both | 438 | 4962 | -313 | -3 | -1322 | 4980 | 2 | 315 |
| mmove | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 377 | 5162 | -997 | 528 | 750 | 4303 | 2 | 315 |
| mmove | false_break | tm780 | {"M": 1, "k": 0.0} | plain60/60 / both | 685 | 5305 | -588 | -1422 | 578 | 4075 | 1 | 315 |
| mmove | false_break_native | vrb_2000 | {"M": 3, "k": 0.5} | sym15u / both | 292 | 5632 | -129 | -106 | 297 | 3674 | 1 | 315 |
| mmove | reject | mom_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 305 | 5147 | 84 | -355 | 2449 | 5365 | 2 | 315 |
| mmove | reject_native | mom_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 305 | 5147 | 84 | -355 | 2449 | 5365 | 2 | 315 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym8u / both | 280 | 4929 | 16 | 565 | 1548 | 5613 | 2 | 315 |
| mmove | retest_native | trend_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 413 | 4300 | 229 | 822 | -1006 | 5352 | 1 | 315 |
| ob15 | break | tick_500 | {"n": 1, "k": 0.25} | sym8u / both | 67 | 1479 | 248 | 613 | 1271 | 1510 | 2 | 315 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 2 | 315 |
| ob15 | false_break | cdr_250 | {"M": 1, "k": 0.0} | plain60/60 / both | 72 | 1334 | 214 | 103 | 325 | 1341 | 1 | 315 |
| ob15 | false_break_native | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 76 | 1926 | 8 | 145 | -703 | 2058 | 2 | 315 |
| ob15 | reject | mom_10 | {"tol": 0.5, "conf": "close"} | sym30u / both | 73 | 1760 | -88 | -163 | 86 | 1776 | 2 | 315 |
| ob15 | reject_native | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 80 | 2091 | -76 | -8 | 402 | 2181 | 2 | 315 |
| ob15 | retest | trb_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 35 | 1683 | 45 | 174 | 651 | 1951 | 1 | 315 |
| ob15 | retest_native | renko_10 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 55 | 1463 | -72 | 237 | -391 | 1011 | 2 | 315 |
| ob5 | break | vrb_3500 | {"n": 2, "k": 0.25} | sym15u / both | 107 | 2726 | 9 | -342 | 562 | 2769 | 1 | 315 |
| ob5 | break_native | vrb_2000 | {"n": 3, "k": 0.5} | sym15u / both | 136 | 2692 | -66 | -214 | 1074 | 3541 | 1 | 315 |
| ob5 | false_break | lbrk_3_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 169 | 2782 | -155 | -395 | 376 | 2558 | 2 | 315 |
| ob5 | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.5} | plain60/60 / both | 193 | 2283 | -258 | -394 | -88 | 3053 | 2 | 315 |
| ob5 | reject | tib_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 216 | 2886 | -141 | -719 | 234 | 3097 | 1 | 315 |
| ob5 | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 270 | 3122 | 14 | 500 | 913 | 3865 | 1 | 315 |
| ob5 | retest | renko_10 | {"M": 10, "tol": 0.0} | asym15u/30u / both | 98 | 2501 | 212 | 19 | 662 | 2760 | 2 | 315 |
| ob5 | retest_native | renko_10 | {"M": 10, "tol": 0.0} | asym15u/30u / both | 98 | 2501 | 212 | 19 | 662 | 2760 | 2 | 315 |
| open_range | break | frenko_112 | {"n": 2, "k": 0.25} | sym15u / both | 35 | 1363 | 224 | 154 | -39 | 1453 | 1 | 315 |
| open_range | break_native | urenko_56 | {"n": 1, "k": 0.5} | sym8u / both | 57 | 1340 | 201 | 827 | 559 | 1477 | 2 | 315 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 315 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 315 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 315 |
| open_range | reject_native | dol_4000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1842 | -333 | 343 | -407 | 1712 | 1 | 315 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 315 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 315 |
| opens | break | vsess_600 | {"n": 2, "k": 0.0} | sym8u / both | 362 | 3575 | -134 | 94 | -503 | 3879 | 2 | 315 |
| opens | break_native | vsess_600 | {"n": 2, "k": 0.0} | sym8u / both | 362 | 3575 | -134 | 94 | -503 | 3879 | 2 | 315 |
| opens | false_break | vsess_600 | {"M": 1, "k": 0.0} | asym20u/10u / both | 278 | 3529 | -496 | 901 | 173 | 3200 | 2 | 315 |
| opens | false_break_native | vsess_600 | {"M": 1, "k": 0.0} | asym20u/10u / both | 278 | 3529 | -496 | 901 | 173 | 3200 | 2 | 315 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 315 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 315 |
| opens | retest | time_s_10 | {"M": 3, "tol": 0.5} | sym15u / both | 441 | 3671 | -253 | -100 | -1031 | 4725 | 2 | 315 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 315 |
| prior_day | break | time_s_15 | {"n": 1, "k": 0.0} | sym30u / both | 241 | 3779 | -42 | 445 | -273 | 3868 | 2 | 315 |
| prior_day | break_native | time_s_15 | {"n": 1, "k": 0.0} | sym30u / both | 241 | 3779 | -42 | 445 | -273 | 3868 | 2 | 315 |
| prior_day | false_break | mom_10 | {"M": 2, "k": 0.5} | sym8u / both | 350 | 3851 | -727 | -356 | 1849 | 4597 | 2 | 315 |
| prior_day | false_break_native | mom_10 | {"M": 2, "k": 0.0} | sym8u / both | 350 | 3849 | -769 | -289 | 2011 | 4596 | 2 | 315 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 315 |
| prior_day | reject_native | time_s_20 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 339 | 3195 | 212 | 105 | -860 | 2276 | 2 | 315 |
| prior_day | retest | swing_atr_0.15 | {"M": 10, "tol": 0.0} | plain60/60 / both | 342 | 2836 | -483 | -29 | 113 | 3315 | 2 | 315 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 315 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 315 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 315 |
| profile_nodes | false_break | vsess_300 | {"M": 1, "k": 0.5} | asym10u/20u / both | 329 | 4201 | -503 | -1129 | -328 | 5429 | 2 | 315 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 315 |
| profile_nodes | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | asym10u/20u / both | 330 | 3914 | -616 | 124 | 44 | 3488 | 2 | 315 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 315 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 2 | 315 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 312 | 4893 | -272 | -130 | 1463 | 6547 | 2 | 315 |
| profile_va | break | time_s_15 | {"n": 3, "k": 0.25} | asym15u/30u / both | 340 | 3917 | -403 | 33 | -419 | 4041 | 2 | 315 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 315 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 2 | 315 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 2 | 315 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 315 |
| profile_va | reject_native | vnorm_1500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 257 | 4574 | -103 | -656 | -1855 | 4146 | 1 | 315 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 315 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 2 | 315 |
| round | break | urenko_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 482 | 5011 | -279 | 136 | 687 | 3865 | 2 | 315 |
| round | break_native | urenko_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 490 | 5483 | -287 | 563 | 338 | 4687 | 2 | 315 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 315 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 315 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 315 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 315 |
| round | retest | trb_400 | {"M": 6, "tol": 0.5} | plain60/60 / both | 652 | 4376 | -446 | -203 | 687 | 3945 | 1 | 315 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 2 | 315 |
| session_hl | break | mrenko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 35 | 1223 | -91 | 74 | 143 | 1012 | 2 | 315 |
| session_hl | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 51 | 1192 | 231 | 534 | 88 | 618 | 1 | 315 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym8u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 2 | 315 |
| session_hl | false_break_native | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 50 | 1312 | 222 | 534 | 143 | 739 | 1 | 315 |
| session_hl | reject | swing_pct_20 | {"tol": 0.5, "conf": "close"} | sym8u / both | 32 | 1191 | 175 | 156 | 5 | 941 | 2 | 315 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 315 |
| session_hl | retest | pnf_40 | {"M": 3, "tol": 0.5} | sym8u / both | 32 | 951 | 132 | -13 | -94 | 676 | 2 | 315 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 2 | 315 |
| trendline | break | pnf_7 | {"n": 2, "k": 0.5} | sym8u / both | 281 | 5286 | -79 | 1093 | -1763 | 5618 | 2 | 315 |
| trendline | break_native | time_s_15 | {"n": 1, "k": 0.25} | sym30u / both | 386 | 5183 | 28 | -953 | -2002 | 5106 | 2 | 315 |
| trendline | false_break | vrb_1200 | {"M": 1, "k": 0.5} | sym8u / both | 322 | 5093 | -260 | 369 | 2446 | 4012 | 2 | 315 |
| trendline | false_break_native | vrb_1200 | {"M": 2, "k": 0.0} | sym8u / both | 334 | 4642 | -313 | 327 | 1910 | 3646 | 2 | 315 |
| trendline | reject | renko_10 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 283 | 4025 | 323 | 845 | 800 | 4111 | 2 | 315 |
| trendline | reject_native | renko_40 | {"tol": 1.0, "conf": "body"} | sym8u / both | 189 | 3437 | 168 | 1008 | 331 | 2242 | 2 | 315 |
| trendline | retest | kagi_20 | {"M": 10, "tol": 0.0} | sym15u / both | 269 | 4489 | -68 | -1301 | 1266 | 3849 | 2 | 315 |
| trendline | retest_native | kagi_20 | {"M": 10, "tol": 0.0} | sym15u / both | 269 | 4489 | -68 | -1301 | 1266 | 3849 | 2 | 315 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 314 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 314 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 314 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 314 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 314 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 2 | 314 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 314 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 314 |
| uw_ndx | break | mrenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 186 | 3379 | 0 | 665 | -253 | 4991 | 1 | 315 |
| uw_ndx | break_native | mrenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 186 | 3379 | 0 | 665 | -253 | 4991 | 1 | 315 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 315 |
| uw_ndx | false_break_native | mrenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 188 | 3056 | 0 | 475 | -173 | 5074 | 1 | 315 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 315 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 315 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 315 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 315 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 315 |
| uw_qqq | break_native | wrenko_20 | {"n": 1, "k": 0.5} | plain60/60 / both | 517 | 3858 | 0 | 45 | 1098 | 4166 | 2 | 315 |
| uw_qqq | false_break | trb_240 | {"M": 2, "k": 0.5} | sym15u / both | 236 | 2834 | 0 | -144 | 3884 | 3559 | 1 | 315 |
| uw_qqq | false_break_native | frenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 281 | 2637 | 0 | -833 | 1721 | 2795 | 1 | 315 |
| uw_qqq | reject | cusum_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 250 | 4778 | 0 | -520 | 344 | 3854 | 2 | 315 |
| uw_qqq | reject_native | cusum_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 263 | 4537 | 0 | -547 | -678 | 4103 | 2 | 315 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 315 |
| uw_qqq | retest_native | time_s_20 | {"M": 10, "tol": 0.0} | asym15u/30u / both | 272 | 2741 | 0 | -365 | 1680 | 2749 | 2 | 315 |
| vwap | break | vrb_240 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5309 | -171 | -93 | 2594 | 5153 | 1 | 315 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym8u / both | 276 | 4877 | -242 | 564 | 397 | 6808 | 2 | 315 |
| vwap | false_break | pasl_10 | {"M": 1, "k": 0.5} | sym8u / both | 285 | 4055 | -442 | -1768 | 1694 | 4612 | 2 | 315 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 315 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 315 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 315 |
| vwap | retest | vsess_600 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 324 | 4287 | -362 | -2245 | -41 | 4558 | 2 | 315 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 315 |
| vwap_bands | break | urenko_10 | {"n": 1, "k": 0.25} | sym30u / both | 309 | 4419 | -2 | -186 | 1349 | 5407 | 2 | 315 |
| vwap_bands | break_native | urenko_10 | {"n": 1, "k": 0.25} | sym30u / both | 315 | 4835 | -165 | -253 | 521 | 6064 | 2 | 315 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 315 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 315 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 315 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 315 |
| vwap_bands | retest | time_s_15 | {"M": 3, "tol": 0.5} | sym30u / both | 377 | 4108 | -527 | -1307 | -3860 | 4086 | 2 | 315 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 315 |
| week_month | break | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1357 | -472 | -345 | 67 | 873 | 1 | 315 |
| week_month | break_native | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1508 | -384 | -405 | 191 | 1025 | 1 | 315 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 315 |
| week_month | false_break_native | vsess_600 | {"M": 1, "k": 0.5} | sym30u / both | 51 | 1835 | 66 | -14 | -367 | 2252 | 2 | 315 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 315 |
| week_month | reject_native | urenko_28 | {"tol": 0.5, "conf": "close"} | sym8u / both | 35 | 1265 | -124 | 397 | -103 | 425 | 2 | 315 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 32 | 1214 | -48 | -24 | 18 | 1531 | 2 | 315 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 32 | 1214 | -48 | -24 | 18 | 1531 | 2 | 315 |
| zones | break | tib_3500 | {"n": 1, "k": 0.25} | sym15u / both | 203 | 3737 | 108 | 650 | 718 | 3536 | 2 | 315 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 315 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 315 |
| zones | false_break_native | mom_28 | {"M": 1, "k": 0.5} | sym8u / both | 170 | 3289 | -35 | 55 | 713 | 3631 | 2 | 315 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "close"} | sym8u / both | 253 | 3422 | -419 | -1262 | 1147 | 2966 | 2 | 315 |
| zones | reject_native | wrenko_10 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 169 | 3358 | -83 | -823 | -460 | 2367 | 2 | 315 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 315 |
| zones | retest_native | urenko_14 | {"M": 3, "tol": 0.5} | sym30u / both | 138 | 3160 | -470 | -589 | -815 | 2282 | 2 | 315 |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 0 of 14280 (modules x 476 bar rows); pass-1 result files written in the last hour: 834 (all modules); ETA for these at that rate if they were alone: 0.0 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

