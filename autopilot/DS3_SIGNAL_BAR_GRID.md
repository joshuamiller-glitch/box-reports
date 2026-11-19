# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-19 02:17Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 26636 | 400 | 0.000 | -0.67 / -0.61 / -0.63 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand10 | 417 | 400 | 0.000 | -0.65 / -0.58 / -0.58 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand11 | 417 | 400 | 0.000 | -0.65 / -0.57 / -0.57 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand12 | 410 | 400 | 0.000 | -0.64 / -0.57 / -0.59 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand13 | 305 | 305 | 0.000 | -0.63 / -0.58 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand14 | 275 | 275 | 0.000 | -0.64 / -0.59 / -0.58 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand15 | 279 | 279 | 0.000 | -0.63 / -0.61 / -0.60 / -0.91 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand16 | 279 | 279 | 0.000 | -0.66 / -0.58 / -0.59 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand17 | 278 | 278 | 0.000 | -0.64 / -0.58 / -0.58 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand18 | 279 | 279 | 0.000 | -0.66 / -0.58 / -0.60 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand19 | 361 | 278 | 0.000 | -0.66 / -0.60 / -0.61 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand2 | 26588 | 400 | 0.000 | -0.68 / -0.62 / -0.63 / -0.95 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand20 | 488 | 346 | 0.000 | -0.65 / -0.59 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand21 | 97 | 97 | 0.000 | -0.65 / -0.62 / -0.61 / -0.92 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand22 | 96 | 96 | 0.000 | -0.65 / -0.61 / -0.61 / -0.95 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand23 | 96 | 96 | 0.000 | -0.66 / -0.59 / -0.59 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand24 | 99 | 99 | 0.000 | -0.63 / -0.62 / -0.61 / -0.93 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand25 | 99 | 99 | 0.000 | -0.67 / -0.60 / -0.62 / -0.95 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand26 | 2 | 2 | 0.000 | -0.35 / -0.30 / -0.63 / -0.63 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand27 | 2 | 2 | 0.000 | -0.93 / -0.57 / -0.62 / -0.64 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand28 | 2 | 2 | 0.000 | -0.53 / -0.51 / -1.04 / -0.84 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand29 | 2 | 2 | 0.000 | -0.47 / -0.77 / -0.68 / -0.71 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand3 | 2784 | 400 | 0.000 | -0.67 / -0.58 / -0.62 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand30 | 2 | 2 | 0.000 | -0.85 / -0.67 / -0.71 / -0.70 | NO | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} | fewer than 20 comparable files |
| p1rand4 | 2687 | 400 | 0.000 | -0.69 / -0.60 / -0.62 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 2570 | 400 | 0.000 | -0.66 / -0.59 / -0.60 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand6 | 423 | 400 | 0.000 | -0.66 / -0.58 / -0.58 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand7 | 423 | 400 | 0.000 | -0.65 / -0.58 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand8 | 423 | 400 | 0.000 | -0.64 / -0.59 / -0.59 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand9 | 423 | 400 | 0.000 | -0.66 / -0.58 / -0.57 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-19 02:17Z):** result files per tag {"acctt1": 4, "acctt2": 1, "p1audit": 436, "p1det": 3, "p1flow_absorbx": 184, "p1flow_bookx": 184, "p1flow_deltax": 185, "p1flow_speedx": 184, "p1flow_wallx": 184, "p1gridops_test": 0, "p1rand1": 27547, "p1rand10": 423, "p1rand11": 423, "p1rand12": 417, "p1rand13": 312, "p1rand14": 281, "p1rand15": 281, "p1rand16": 281, "p1rand17": 281, "p1rand18": 281, "p1rand19": 364, "p1rand2": 27174, "p1rand20": 491, "p1rand21": 99, "p1rand22": 99, "p1rand23": 99, "p1rand24": 99, "p1rand25": 99, "p1rand26": 2, "p1rand27": 2, "p1rand28": 2, "p1rand29": 2, "p1rand3": 2810, "p1rand30": 2, "p1rand4": 2691, "p1rand5": 2573, "p1rand6": 423, "p1rand7": 423, "p1rand8": 423, "p1rand9": 423, "p1real": 61118, "p1realx": 1029, "p1stale": 67, "p1stamptest": 1, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, ACTIVITY(book), ANCHORED, COMPOSITE, FOOTPRINT, INFORMATION, INFORMATION(book), PRICE, PROFILE, SESSION-RELATIVE, SMOOTHING, TIME, UNKNOWN; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 0, "London": 0, "NYAM": 0, "NYPM": 0}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-19 02:17Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"acctt1": 4, "acctt2": 1, "p1audit": 436, "p1det": 3, "p1flow_absorbx": 184, "p1flow_bookx": 184, "p1flow_deltax": 185, "p1flow_speedx": 184, "p1flow_wallx": 184, "p1gridops_test": 0, "p1rand1": 27547, "p1rand10": 423, "p1rand11": 423, "p1rand12": 417, "p1rand13": 312, "p1rand14": 281, "p1rand15": 281, "p1rand16": 281, "p1rand17": 281, "p1rand18": 281, "p1rand19": 364, "p1rand2": 27174, "p1rand20": 491, "p1rand21": 99, "p1rand22": 99, "p1rand23": 99, "p1rand24": 99, "p1rand25": 99, "p1rand26": 2, "p1rand27": 2, "p1rand28": 2, "p1rand29": 2, "p1rand3": 2810, "p1rand30": 2, "p1rand4": 2691, "p1rand5": 2573, "p1rand6": 423, "p1rand7": 423, "p1rand8": 423, "p1rand9": 423, "p1real": 61118, "p1realx": 1029, "p1stale": 67, "p1stamptest": 1, "rand1": 0, "real": 1654}; loop status: 2026-11-19T01:47Z rows=322 mods=146 todo=7522 running=0. 
Cells scored per session: {"Asia": 6300358, "London": 7116623, "NYAM": 7798269, "NYPM": 7813716}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -6.1 | -0.002 | 1299.5 | 0.51 | 51.9 | 60.8 |  |  |  |  | -0.1 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -11.7 | -0.008 | 1384.8 | 0.52 | 27.8 | -9.6 |  |  |  |  | -13.1 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | -27.4 [no null yet] | -19.7 [no null yet] | 3.9 [no null yet] | -7.9 [no null yet] | n/a (no signals by construction) | -28.2 [no null yet] | -19.3 [no null yet] | -27.9 [no null yet] | n/a (no signals by construction) | -24.3 [no null yet] | -9.7 [no null yet] | -15.8 [no null yet] | 1.9 [no null yet] |
| bands (native) | -41.0 [no null yet] | 1.5 [no null yet] | 16.0 [no null yet] | -18.1 [no null yet] | n/a (no signals by construction) | 2.6 [no null yet] | -10.9 [no null yet] | -21.4 [no null yet] | n/a (no signals by construction) | 5.7 [no null yet] | -16.5 [no null yet] | -9.1 [no null yet] | -9.9 [no null yet] |
| barnative | -31.4 [no null yet] | -6.5 [no null yet] | -4.8 [no null yet] | 10.1 [no null yet] | -30.2 [no null yet] | -20.5 [no null yet] | -16.2 [no null yet] | 5.7 [no null yet] | 6.0 [no null yet] | -2.4 [no null yet] | -31.2 [no null yet] | -12.0 [no null yet] | -26.3 [no null yet] |
| book | -3.5 [no null yet] | -30.8 [no null yet] | n/a (no signals by construction) | -15.8 [no null yet] | n/a (no signals by construction) | 3.3 [no null yet] | -15.4 [no null yet] | 27.2 [no null yet] | n/a (no signals by construction) | 15.7 [no null yet] | -38.3 [no null yet] | -12.6 [no null yet] | -21.6 [no null yet] |
| book (native) | -6.0 [no null yet] | -16.3 [no null yet] | n/a (no signals by construction) | -11.3 [no null yet] | n/a (no signals by construction) | -18.6 [no null yet] | -9.4 [no null yet] | 6.7 [no null yet] | n/a (no signals by construction) | -9.5 [no null yet] | 2.9 [no null yet] | -9.4 [no null yet] | -1.0 [no null yet] |
| confluence | 4.1 [no null yet] | -25.5 [no null yet] | -3.9 [no null yet] | -25.0 [no null yet] | -8.7 [no null yet] | -1.0 [no null yet] | -8.2 [no null yet] | -0.2 [no null yet] | -4.5 [no null yet] | -28.1 [no null yet] | -25.3 [no null yet] | 6.1 [no null yet] | -20.6 [no null yet] |
| levels | -16.2 [no null yet] | -13.5 [no null yet] | -7.3 [no null yet] | -8.1 [no null yet] | -2.7 [no null yet] | -0.5 [no null yet] | 1.7 [no null yet] | 17.3 [no null yet] | -6.4 [no null yet] | -15.5 [no null yet] | -16.2 [no null yet] | -3.6 [no null yet] | -25.1 [no null yet] |
| levels (native) | -21.4 [no null yet] | -26.7 [no null yet] | 0.5 [no null yet] | -22.8 [no null yet] | 6.5 [no null yet] | -8.4 [no null yet] | -18.3 [no null yet] | 30.5 [no null yet] | -24.8 [no null yet] | -24.8 [no null yet] | -10.7 [no null yet] | -3.3 [no null yet] | 5.9 [no null yet] |
| live | -7.1 [no null yet] | -28.1 [no null yet] | -1.1 [no null yet] | -44.3 [no null yet] | n/a (no signals by construction) | -13.4 [no null yet] | -19.0 [no null yet] | -4.2 [no null yet] | n/a (no signals by construction) | -13.4 [no null yet] | -5.7 [no null yet] | 6.3 [no null yet] | -0.5 [no null yet] |
| manual | -13.3 [no null yet] | -0.5 [no null yet] | -16.6 [no null yet] | -38.3 [no null yet] | -15.0 [no null yet] | -6.5 [no null yet] | -10.9 [no null yet] | -33.2 [no null yet] | 0.3 [no null yet] | -14.7 [no null yet] | -13.7 [no null yet] | -18.2 [no null yet] | -10.5 [no null yet] |
| manual (native) | 7.9 [no null yet] | -3.1 [no null yet] | 0.0 [no null yet] | 5.2 [no null yet] | n/a (no signals by construction) | -9.4 [no null yet] | -3.0 [no null yet] | -20.5 [no null yet] | n/a (no signals by construction) | -5.6 [no null yet] | -1.7 [no null yet] | -21.2 [no null yet] | -29.2 [no null yet] |
| momentum | -2.1 [no null yet] | -0.0 [no null yet] | 0.1 [no null yet] | 0.9 [no null yet] | -16.8 [no null yet] | 12.1 [no null yet] | -7.4 [no null yet] | 2.4 [no null yet] | 0.5 [no null yet] | -16.1 [no null yet] | 2.3 [no null yet] | -22.9 [no null yet] | 20.2 [no null yet] |
| momentum (native) | -29.3 [no null yet] | -0.2 [no null yet] | -20.6 [no null yet] | -12.0 [no null yet] | n/a (no signals by construction) | -26.1 [no null yet] | -18.0 [no null yet] | 1.1 [no null yet] | n/a (no signals by construction) | 6.8 [no null yet] | -4.5 [no null yet] | -12.4 [no null yet] | 2.9 [no null yet] |
| pullback | -10.9 [no null yet] | -14.9 [no null yet] | 4.9 [no null yet] | -6.4 [no null yet] | -20.8 [no null yet] | -8.1 [no null yet] | -19.4 [no null yet] | 12.1 [no null yet] | -0.4 [no null yet] | -18.9 [no null yet] | -28.3 [no null yet] | -4.2 [no null yet] | -9.1 [no null yet] |
| pullback (native) | -9.6 [no null yet] | -15.3 [no null yet] | -1.5 [no null yet] | 9.8 [no null yet] | n/a (no signals by construction) | -4.3 [no null yet] | -10.3 [no null yet] | -7.9 [no null yet] | n/a (no signals by construction) | -9.0 [no null yet] | 6.8 [no null yet] | -29.7 [no null yet] | 3.7 [no null yet] |
| structure | -23.9 [no null yet] | -14.3 [no null yet] | -11.1 [no null yet] | -7.1 [no null yet] | -19.2 [no null yet] | -18.3 [no null yet] | -16.9 [no null yet] | -35.9 [no null yet] | -1.0 [no null yet] | -15.8 [no null yet] | -2.6 [no null yet] | -4.1 [no null yet] | 15.5 [no null yet] |
| structure (native) | -20.9 [no null yet] | 28.2 [no null yet] | n/a (no signals by construction) | 12.4 [no null yet] | n/a (no signals by construction) | -21.0 [no null yet] | 2.0 [no null yet] | 6.7 [no null yet] | n/a (no signals by construction) | -10.1 [no null yet] | -0.8 [no null yet] | -19.8 [no null yet] | -6.4 [no null yet] |
| tape | 0.9 [no null yet] | -11.2 [no null yet] | -0.2 [no null yet] | -23.3 [no null yet] | -1.6 [no null yet] | -3.0 [no null yet] | -26.9 [no null yet] | -10.2 [no null yet] | -0.8 [no null yet] | -41.2 [no null yet] | -34.7 [no null yet] | -43.6 [no null yet] | -36.2 [no null yet] |
| tape (native) | -22.6 [no null yet] | -30.8 [no null yet] | -13.2 [no null yet] | 5.9 [no null yet] | n/a (no signals by construction) | -20.3 [no null yet] | -1.8 [no null yet] | -11.8 [no null yet] | -7.7 [no null yet] | -12.3 [no null yet] | -5.4 [no null yet] | -23.5 [no null yet] | -24.5 [no null yet] |
| trend | -24.9 [no null yet] | -7.7 [no null yet] | -6.4 [no null yet] | 5.8 [no null yet] | -25.1 [no null yet] | -38.6 [no null yet] | -10.0 [no null yet] | -10.4 [no null yet] | 1.2 [no null yet] | -25.1 [no null yet] | -26.2 [no null yet] | -26.0 [no null yet] | -5.3 [no null yet] |
| trend (native) | -12.0 [no null yet] | 9.7 [no null yet] | -12.8 [no null yet] | -9.9 [no null yet] | n/a (no signals by construction) | -20.7 [no null yet] | -28.2 [no null yet] | -31.4 [no null yet] | n/a (no signals by construction) | -15.3 [no null yet] | -35.1 [no null yet] | -21.1 [no null yet] | -10.1 [no null yet] |
| xmarket | -4.1 [no null yet] | 9.3 [no null yet] | 3.5 [no null yet] | -19.8 [no null yet] | -28.4 [no null yet] | 2.5 [no null yet] | -42.1 [no null yet] | 30.6 [no null yet] | 5.0 [no null yet] | -9.4 [no null yet] | 11.4 [no null yet] | -24.1 [no null yet] | 17.4 [no null yet] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| xmarket|PRICE | 30.6 | 0.025 | 352.5 | 0.58 | 145.5 | 107.1 | {"2023": -28.1, "2024": 1.7, "2025": -25.0, "2026": 148.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|PRICE | 30.5 | 0.040 | 247.3 | 0.52 | 47.4 | 58.3 | {"2023": 23.9, "2024": -4.3, "2025": 19.6, "2026": 86.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY(book) | 28.2 | 0.033 | 214.4 | 0.59 | 89.8 | -57.6 | {"2023": 31.1, "2024": 7.0, "2025": 17.6, "2026": 65.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|PRICE | 27.2 | 0.030 | 277.5 | 0.53 | 88.2 | 20.4 | {"2023": -37.4, "2024": 13.8, "2025": 41.6, "2026": 46.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|UNKNOWN | 20.2 | 0.029 | 287.9 | 0.53 | 11.9 | 10.2 | {"2023": 68.6, "2024": -10.6, "2025": 49.5, "2026": 6.6} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|UNKNOWN | 17.4 | 0.003 | 500.8 | 0.49 | 71.4 | 116.3 | {"2023": -35.8, "2024": -27.5, "2025": 44.8, "2026": 55.2} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels|PRICE | 17.3 | 0.012 | 223.7 | 0.58 | 4.8 | 15.6 | {"2023": 5.0, "2024": -7.7, "2025": 28.3, "2026": 37.9} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands (native)|ANCHORED | 16.0 | 0.255 | 8.0 | 0.40 | 18.5 | 4.9 | {"2025": 0.0, "2026": 17.1} |  |  |  | {"2025": "ok", "2026": "ok"} |
| book|SESSION-RELATIVE | 15.7 | 0.007 | 629.8 | 0.51 | 89.3 | 69.1 | {"2023": 5.5, "2024": 0.3, "2025": -18.7, "2026": 77.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure|UNKNOWN | 15.5 | 0.011 | 620.0 | 0.51 | 71.8 | 10.3 | {"2023": -24.3, "2024": 37.0, "2025": -26.9, "2026": 52.8} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 94.8%); M7 tm60 L6M -39.6 pts/wk, rank 10% (top 90.5%); U7 tm600 L6M -10.7 pts/wk, rank 33% (top 66.8%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.3%); H7 tm60 L6M 2.9 pts/wk, rank 63% (top 37.3%); A7 tm60 L6M 14.3 pts/wk, rank 79% (top 20.5%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|PRICE | 22.6 | 0.027 | 360.2 | 0.62 | -58.6 | -10.4 | {"2023": 2.1, "2024": 39.3, "2025": 58.7, "2026": -33.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels (native)|PRICE | 22.2 | 0.031 | 256.2 | 0.58 | 37.3 | 151.5 | {"2023": 22.2, "2024": 25.5, "2025": -0.2, "2026": 44.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|PRICE | 17.7 | 0.018 | 426.3 | 0.56 | 76.4 | 134.5 | {"2023": -26.0, "2024": 16.6, "2025": -17.4, "2026": 74.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| xmarket|PRICE | 14.5 | 0.022 | 236.9 | 0.63 | -26.4 | -56.1 | {"2023": 16.4, "2024": 45.7, "2025": 6.6, "2026": -13.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels (native)|COMPOSITE | 12.6 | 0.013 | 328.0 | 0.54 | 101.6 | 70.6 | {"2023": -44.6, "2024": 13.0, "2025": -4.7, "2026": 50.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels|PRICE | 12.5 | 0.018 | 391.9 | 0.52 | -3.7 | 145.2 | {"2023": -21.0, "2024": -5.7, "2025": 36.6, "2026": 16.2} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|PRICE | 9.3 | 0.013 | 674.1 | 0.53 | 48.3 | 197.8 | {"2023": 36.8, "2024": 12.6, "2025": -38.4, "2026": 53.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| pullback|PRICE | 7.9 | 0.001 | 737.5 | 0.53 | 105.8 | 115.9 | {"2023": 4.7, "2024": -9.5, "2025": 2.7, "2026": 35.8} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum|INFORMATION | 7.9 | 0.017 | 616.2 | 0.51 | -4.9 | -50.8 | {"2023": -10.3, "2024": 44.2, "2025": -34.0, "2026": 20.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| book (native)|PRICE | 6.1 | 0.006 | 351.3 | 0.44 | 30.0 | 137.5 | {"2023": -28.4, "2024": -3.9, "2025": 1.2, "2026": 34.6} |  |  |  | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | vsess_600 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | sym8u | both | 6120 | 2666 | 701 | 1.00 | 5 / -1086 / 562 / 1.00 | {"2023": -421.0, "2024": -1541.0, "2025": -1139.0, "2026": 6064.0} |
| 2 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym20u/10u | both | 6084 | 2102 | 245 | 1.00 | 5 / -256 / 3416 / 1.00 | {"2023": 76.0, "2024": 61.0, "2025": 1363.0, "2026": 7110.0} |
| 3 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 50} | sym8u | both | 6032 | 3321 | 643 | 1.00 | 5 / -163 / 2254 / 1.00 | {"2023": -1534.0, "2024": 277.0, "2025": 116.0, "2026": 5648.0} |
| 4 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 6002 | 1997 | 238 | 1.00 | 5 / -514 / 2989 / 1.00 | {"2023": 228.0, "2024": 4.0, "2025": 1073.0, "2026": 6927.0} |
| 5 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5987 | 1982 | 237 | 1.00 | 5 / -358 / 3219 / 1.00 | {"2023": 378.0, "2024": 121.0, "2025": 1041.0, "2026": 6917.0} |
| 6 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5984 | 1978 | 238 | 1.00 | 5 / -458 / 2964 / 1.00 | {"2023": 222.0, "2024": -104.0, "2025": 1188.0, "2026": 6903.0} |
| 7 | qmid_B500 | structure.structure_libpattern.rangeexp | {"k": 1.5} | sym8u | both | 5898 | 3165 | 285 | 1.00 | 5 / 529 / 2805 / 1.00 | {"2023": -182.0, "2024": 733.0, "2025": -2694.0, "2026": 5056.0} |
| 8 | trb_400 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5883 | 2756 | 237 | 1.00 | 0 /  /  /  | {"2023": 724.0, "2024": 960.0, "2025": -101.0, "2026": 4877.0} |
| 9 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym8u | both | 5846 | 2536 | 233 | 1.00 | 25 / -26 / 2923 / 1.00 | {"2023": 667.0, "2024": 1147.0, "2025": -135.0, "2026": 5737.0} |
| 10 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | sym15u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1316.0, "2024": -862.0, "2025": -307.0, "2026": 5653.0} |
| 11 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | asym10u/20u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1272.0, "2024": -697.0, "2025": -353.0, "2026": 5653.0} |
| 12 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | sym30u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1255.0, "2024": -920.0, "2025": -307.0, "2026": 5653.0} |
| 13 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | asym15u/30u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1279.0, "2024": -873.0, "2025": -307.0, "2026": 5653.0} |
| 14 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | asym20u/10u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1091.0, "2024": -717.0, "2025": -356.0, "2026": 5653.0} |
| 15 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | sym8u | both | 5803 | 3194 | 233 | 1.00 | 5 / -360 / 1035 / 1.00 | {"2023": 1388.0, "2024": -590.0, "2025": -548.0, "2026": 5662.0} |
| 16 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | 5 / -290 / 857 / 1.00 | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 17 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym15u/30u | both | 5725 | 2309 | 222 | 1.00 | 5 / -324 / 869 / 1.00 | {"2023": 805.0, "2024": -945.0, "2025": -3204.0, "2026": 7489.0} |
| 18 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 200} | sym8u | both | 5714 | 2851 | 645 | 1.00 | 5 / -2256 / 214 / 1.00 | {"2023": -1209.0, "2024": 895.0, "2025": -1513.0, "2026": 6526.0} |
| 19 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym20u/10u | both | 5657 | 2334 | 231 | 1.00 | 25 / -30 / 3284 / 1.00 | {"2023": 891.0, "2024": 2127.0, "2025": 454.0, "2026": 5288.0} |
| 20 | dltor_B130 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 5649 | 1877 | 240 | 1.00 | 5 / -169 / 2937 / 1.00 | {"2023": 671.0, "2024": -598.0, "2025": 797.0, "2026": 7022.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -41.1 | -0.029 | 1820.7 | 0.46 | -76.5 | -45.0 |  |  |  |  | 12.1 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | -31.8 | -0.019 | 1180.7 | 0.47 | -90.3 | -45.0 |  |  |  |  | 12.5 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | 27.3 [no null yet] | 30.7 [no null yet] | -4.1 [no null yet] | -10.0 [no null yet] | n/a (no signals by construction) | -19.0 [no null yet] | 15.2 [no null yet] | 15.6 [no null yet] | n/a (no signals by construction) | 18.2 [no null yet] | 22.5 [no null yet] | 52.6 [no null yet] | 20.6 [no null yet] |
| bands (native) | 23.1 [no null yet] | 10.5 [no null yet] | 10.7 [no null yet] | -14.8 [no null yet] | n/a (no signals by construction) | 18.2 [no null yet] | 4.6 [no null yet] | 18.1 [no null yet] | n/a (no signals by construction) | -10.4 [no null yet] | 3.2 [no null yet] | 38.2 [no null yet] | 14.4 [no null yet] |
| barnative | -36.8 [no null yet] | -18.4 [no null yet] | -22.8 [no null yet] | 2.9 [no null yet] | -34.9 [no null yet] | -0.5 [no null yet] | -30.7 [no null yet] | 66.1 [no null yet] | -11.4 [no null yet] | 11.7 [no null yet] | -11.4 [no null yet] | 17.2 [no null yet] | 15.8 [no null yet] |
| book | 26.5 [no null yet] | 4.8 [no null yet] | n/a (no signals by construction) | 17.1 [no null yet] | n/a (no signals by construction) | 25.9 [no null yet] | 17.6 [no null yet] | -11.1 [no null yet] | n/a (no signals by construction) | 49.1 [no null yet] | 35.3 [no null yet] | 34.5 [no null yet] | 19.6 [no null yet] |
| book (native) | -5.9 [no null yet] | 37.7 [no null yet] | n/a (no signals by construction) | -13.7 [no null yet] | n/a (no signals by construction) | -28.0 [no null yet] | 7.3 [no null yet] | 46.2 [no null yet] | n/a (no signals by construction) | 52.2 [no null yet] | 34.5 [no null yet] | -26.3 [no null yet] | 34.3 [no null yet] |
| confluence | -1.8 [no null yet] | 17.6 [no null yet] | 2.7 [no null yet] | -8.1 [no null yet] | 4.2 [no null yet] | -1.4 [no null yet] | 3.1 [no null yet] | 42.4 [no null yet] | -5.8 [no null yet] | -1.9 [no null yet] | -1.8 [no null yet] | 1.9 [no null yet] | -5.6 [no null yet] |
| levels | -2.4 [no null yet] | -4.4 [no null yet] | 18.3 [no null yet] | 7.8 [no null yet] | -41.7 [no null yet] | -19.5 [no null yet] | 3.4 [no null yet] | -2.5 [no null yet] | -21.4 [no null yet] | 30.0 [no null yet] | 24.1 [no null yet] | -15.2 [no null yet] | 32.1 [no null yet] |
| levels (native) | 28.8 [no null yet] | 4.3 [no null yet] | -10.7 [no null yet] | -6.1 [no null yet] | -33.6 [no null yet] | -17.7 [no null yet] | -11.2 [no null yet] | 8.4 [no null yet] | -40.4 [no null yet] | -11.9 [no null yet] | 31.3 [no null yet] | -3.1 [no null yet] | 22.6 [no null yet] |
| live | 9.1 [no null yet] | 16.2 [no null yet] | -8.3 [no null yet] | 4.2 [no null yet] | n/a (no signals by construction) | 13.1 [no null yet] | 38.4 [no null yet] | 8.2 [no null yet] | n/a (no signals by construction) | -2.1 [no null yet] | 9.4 [no null yet] | -10.3 [no null yet] | -6.5 [no null yet] |
| manual | 27.6 [no null yet] | 17.3 [no null yet] | -13.3 [no null yet] | 20.8 [no null yet] | -25.6 [no null yet] | 31.8 [no null yet] | 6.4 [no null yet] | -16.0 [no null yet] | -6.6 [no null yet] | -30.3 [no null yet] | 25.4 [no null yet] | 38.1 [no null yet] | 18.3 [no null yet] |
| manual (native) | -63.2 [no null yet] | -20.7 [no null yet] | 5.6 [no null yet] | -20.4 [no null yet] | n/a (no signals by construction) | -47.5 [no null yet] | -45.9 [no null yet] | -20.2 [no null yet] | n/a (no signals by construction) | -35.4 [no null yet] | -32.1 [no null yet] | -14.7 [no null yet] | -29.2 [no null yet] |
| momentum | 8.9 [no null yet] | 38.6 [no null yet] | 4.1 [no null yet] | -2.7 [no null yet] | -53.1 [no null yet] | -43.7 [no null yet] | 20.8 [no null yet] | -30.5 [no null yet] | -8.9 [no null yet] | 36.7 [no null yet] | 1.7 [no null yet] | 26.9 [no null yet] | 21.4 [no null yet] |
| momentum (native) | 10.7 [no null yet] | 19.2 [no null yet] | 9.7 [no null yet] | -8.7 [no null yet] | n/a (no signals by construction) | -3.0 [no null yet] | 5.0 [no null yet] | 30.3 [no null yet] | n/a (no signals by construction) | 8.4 [no null yet] | -2.2 [no null yet] | 32.9 [no null yet] | 19.1 [no null yet] |
| pullback | 25.7 [no null yet] | 11.9 [no null yet] | 12.8 [no null yet] | -20.3 [no null yet] | -50.2 [no null yet] | 19.0 [no null yet] | 48.6 [no null yet] | -15.0 [no null yet] | -1.8 [no null yet] | -26.5 [no null yet] | 54.2 [no null yet] | 5.6 [no null yet] | 4.9 [no null yet] |
| pullback (native) | 14.0 [no null yet] | 4.9 [no null yet] | -22.3 [no null yet] | 6.3 [no null yet] | n/a (no signals by construction) | -1.2 [no null yet] | 3.1 [no null yet] | -1.8 [no null yet] | n/a (no signals by construction) | -17.4 [no null yet] | 7.7 [no null yet] | 18.6 [no null yet] | 6.9 [no null yet] |
| structure | 4.0 [no null yet] | -0.5 [no null yet] | 7.5 [no null yet] | 9.0 [no null yet] | -6.3 [no null yet] | 36.2 [no null yet] | 27.1 [no null yet] | 28.6 [no null yet] | -17.3 [no null yet] | -17.7 [no null yet] | 33.7 [no null yet] | -2.8 [no null yet] | -7.0 [no null yet] |
| structure (native) | 40.7 [no null yet] | -4.0 [no null yet] | 5.0 [no null yet] | 2.0 [no null yet] | n/a (no signals by construction) | 11.9 [no null yet] | -20.0 [no null yet] | -2.2 [no null yet] | n/a (no signals by construction) | 1.7 [no null yet] | 21.8 [no null yet] | 25.4 [no null yet] | -10.9 [no null yet] |
| tape | -4.4 [no null yet] | 1.9 [no null yet] | -8.9 [no null yet] | -10.5 [no null yet] | -45.2 [no null yet] | 21.2 [no null yet] | -39.5 [no null yet] | 8.7 [no null yet] | -5.4 [no null yet] | -14.8 [no null yet] | -4.0 [no null yet] | -38.5 [no null yet] | -34.5 [no null yet] |
| tape (native) | 12.8 [no null yet] | 43.1 [no null yet] | -10.5 [no null yet] | -4.4 [no null yet] | n/a (no signals by construction) | -41.9 [no null yet] | 24.4 [no null yet] | 3.6 [no null yet] | -6.1 [no null yet] | 6.7 [no null yet] | -13.9 [no null yet] | -18.7 [no null yet] | -23.9 [no null yet] |
| trend | -18.1 [no null yet] | 18.3 [no null yet] | -20.3 [no null yet] | -23.8 [no null yet] | -20.0 [no null yet] | -28.6 [no null yet] | -46.8 [no null yet] | 10.0 [no null yet] | -16.3 [no null yet] | -16.9 [no null yet] | 31.5 [no null yet] | -24.2 [no null yet] | 34.8 [no null yet] |
| trend (native) | -63.7 [no null yet] | -2.4 [no null yet] | -23.6 [no null yet] | -40.8 [no null yet] | n/a (no signals by construction) | 15.9 [no null yet] | -23.3 [no null yet] | 4.1 [no null yet] | n/a (no signals by construction) | -28.3 [no null yet] | 18.7 [no null yet] | -12.0 [no null yet] | 11.0 [no null yet] |
| xmarket | -8.3 [no null yet] | -34.7 [no null yet] | 10.1 [no null yet] | -43.0 [no null yet] | -15.6 [no null yet] | -4.2 [no null yet] | -27.8 [no null yet] | -29.9 [no null yet] | -7.9 [no null yet] | -12.6 [no null yet] | -3.9 [no null yet] | 14.5 [no null yet] | 16.9 [no null yet] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 66.1 | 0.034 | 407.4 | 0.60 | 116.9 | 82.8 | {"2023": -56.1, "2024": 11.8, "2025": 108.1, "2026": 119.6} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|SMOOTHING | 54.2 | 0.046 | 309.9 | 0.57 | 81.8 | 126.7 | {"2023": 36.8, "2024": 24.3, "2025": 82.2, "2026": 62.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|TIME | 52.6 | 0.033 | 474.1 | 0.58 | 94.7 | 36.4 | {"2023": 10.3, "2024": 24.4, "2025": 63.2, "2026": 86.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|SESSION-RELATIVE | 52.2 | 0.035 | 211.0 | 0.57 | -20.3 | 2.3 | {"2023": 32.2, "2024": 38.2, "2025": 95.6, "2026": 23.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|SESSION-RELATIVE | 49.1 | 0.024 | 632.8 | 0.58 | -2.2 | -45.0 | {"2023": 26.4, "2024": -28.9, "2025": 187.6, "2026": -15.3} |  |  |  | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| pullback|INFORMATION(book) | 48.6 | 0.045 | 300.0 | 0.62 | 35.6 | 41.1 | {"2023": 28.1, "2024": 46.8, "2025": 70.2, "2026": 31.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|PRICE | 46.2 | 0.027 | 414.2 | 0.58 | 80.2 | 139.7 | {"2023": -63.7, "2024": 39.8, "2025": 77.0, "2026": 52.5} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|ACTIVITY(book) | 43.1 | 0.029 | 450.5 | 0.56 | 23.5 | 56.2 | {"2023": -5.0, "2024": 5.1, "2025": 63.8, "2026": 78.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|PRICE | 42.4 | 0.027 | 396.9 | 0.49 | 48.5 | -142.7 | {"2023": 68.0, "2024": 54.4, "2025": 31.6, "2026": 32.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 40.7 | 0.030 | 829.5 | 0.60 | -20.6 | 60.5 | {"2023": 73.2, "2024": 37.0, "2025": 89.6, "2026": -23.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 6% (top 93.6%); M7 tm60 L6M -8.9 pts/wk, rank 45% (top 55.4%); U7 tm600 L6M -11.4 pts/wk, rank 42% (top 58.4%); P7 tm60 L6M -60.7 pts/wk, rank 10% (top 89.8%); H7 tm60 L6M 28.8 pts/wk, rank 86% (top 13.9%); A7 tm60 L6M -17.2 pts/wk, rank 36% (top 64.3%); O7 tm60 L6M 15.1 pts/wk, rank 77% (top 22.9%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands|TIME | 55.0 | 0.033 | 539.0 | 0.58 | 94.7 | 36.4 | {"2023": 10.3, "2024": 22.6, "2025": 72.6, "2026": 86.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|INFORMATION | 50.8 | 0.033 | 293.1 | 0.54 | 81.9 | 93.6 | {"2023": -26.9, "2024": 62.9, "2025": 59.5, "2026": 50.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 46.6 | 0.032 | 729.4 | 0.62 | 2.7 | 60.5 | {"2023": 73.2, "2024": 39.1, "2025": 94.6, "2026": -9.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| levels (native)|ACTIVITY | 42.8 | 0.034 | 535.8 | 0.59 | -12.5 | 119.3 | {"2023": -12.4, "2024": 72.6, "2025": 55.3, "2026": 10.5} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|ACTIVITY | 41.7 | 0.024 | 356.6 | 0.52 | 21.7 | -17.3 | {"2023": -41.1, "2024": 56.3, "2025": 82.5, "2026": 2.4} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 39.5 | 0.036 | 447.2 | 0.58 | 63.8 | 54.1 | {"2023": 43.1, "2024": -4.2, "2025": 43.0, "2026": 86.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 39.0 | 0.029 | 736.7 | 0.57 | 10.1 | 189.4 | {"2023": 97.5, "2024": 3.4, "2025": 77.9, "2026": 16.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|TIME | 38.2 | 0.029 | 431.0 | 0.53 | -6.5 | 44.8 | {"2023": 15.7, "2024": 0.8, "2025": 97.0, "2026": 20.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|TIME | 38.2 | 0.026 | 626.8 | 0.63 | 27.7 | 281.0 | {"2023": -23.4, "2024": 18.5, "2025": 69.5, "2026": 43.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|INFORMATION | 35.9 | 0.020 | 502.5 | 0.57 | 113.2 | 201.2 | {"2023": -49.5, "2024": 15.1, "2025": 82.5, "2026": 32.5} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | pnf_5 | book.book_cancel.ratio_follow | {"L": 100, "z": 2.0} | asym20u/10u | both | 9583 | 3157 | 460 | 0.75 | 0 /  /  /  | {"2023": -15.0, "2024": -2940.0, "2025": 2189.0, "2026": 11746.0} |
| 2 | frenko_28 | tape.tape_delta.cvd_fade | {"N": 10, "L": 100, "z": 1.0} | asym10u/20u | both | 9365 | 2858 | 566 | 0.67 | 0 /  /  /  | {"2023": -3459.0, "2024": 2614.0, "2025": -2110.0, "2026": 8465.0} |
| 3 | vib_25000 | tape.tape_delta.fade | {"L": 50, "z": 1.0} | plain60/60 | both | 8835 | 4421 | 979 | 1.00 | 0 /  /  /  | {"2023": -1810.0, "2024": -908.0, "2025": -5425.0, "2026": 9879.0} |
| 4 | vib_3500 | book.book_cancel.canc_follow | {"L": 100, "z": 1.5} | sym30u | both | 8817 | 2554 | 498 | 1.00 | 5 / -1924 / 1198 / 1.00 | {"2023": 3332.0, "2024": 59.0, "2025": 4568.0, "2026": 9599.0} |
| 5 | vib_3500 | book.book_cancel.canc_follow | {"L": 100, "z": 1.5} | asym15u/30u | both | 8803 | 2624 | 500 | 1.00 | 5 / -1805 / 1637 / 1.00 | {"2023": 2563.0, "2024": -665.0, "2025": 3163.0, "2026": 9314.0} |
| 6 | pnf_5 | book.book_cancel.ratio_follow | {"L": 200, "z": 2.0} | asym20u/10u | both | 8787 | 2421 | 460 | 0.67 | 0 /  /  /  | {"2023": -243.0, "2024": -2348.0, "2025": 5773.0, "2026": 9826.0} |
| 7 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | sym15u | both | 8704 | 3814 | 509 | 1.00 | 0 /  /  /  | {"2023": -91.0, "2024": -1608.0, "2025": 3335.0, "2026": 10363.0} |
| 8 | vib_3500 | book.book_cancel.canc_follow | {"L": 100, "z": 1.5} | asym20u/10u | both | 8629 | 2492 | 556 | 1.00 | 5 / -1743 / -585 / 1.00 | {"2023": 2048.0, "2024": -771.0, "2025": 2680.0, "2026": 8789.0} |
| 9 | lbrk_4_10 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 8520 | 3011 | 1635 | 1.00 | 0 /  /  /  | {"2023": 911.0, "2024": 1308.0, "2025": -5892.0, "2026": 11502.0} |
| 10 | volor_B500 | tape.tape_run.runv_fade | {"thr": 15} | plain60/60 | both | 8517 | 2708 | 1511 | 1.00 | 5 / -1733 / 104 / 1.00 | {"2023": -228.0, "2024": -2941.0, "2025": -4636.0, "2026": 6130.0} |
| 11 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | asym15u/30u | both | 8456 | 3566 | 508 | 1.00 | 0 /  /  /  | {"2023": 15.0, "2024": 239.0, "2025": 2832.0, "2026": 9992.0} |
| 12 | dib_700 | bands.bands_bollinger.break | {"n": 14, "k": 1.5} | asym20u/10u | both | 8440 | 3980 | 1152 | 0.60 | 5 / -950 / 759 / 1.00 | {"2023": -1554.0, "2024": 596.0, "2025": 771.0, "2026": 6996.0} |
| 13 | pnf_5 | book.book_cancel.ratio_follow | {"L": 50, "z": 1.0} | sym30u | both | 8430 | 3540 | 508 | 1.00 | 0 /  /  /  | {"2023": 1715.0, "2024": -318.0, "2025": 3183.0, "2026": 10176.0} |
| 14 | vib_3500 | book.book_cancel.canc_follow | {"L": 100, "z": 1.5} | sym15u | both | 8416 | 2627 | 501 | 1.00 | 5 / -2052 / 1005 / 1.00 | {"2023": 1324.0, "2024": 919.0, "2025": 2941.0, "2026": 8342.0} |
| 15 | time_s_20 | xmarket.xmarket_fast.follow_RTY | {"w": 5, "thr": 1.0} | sym15u | both | 8370 | 2950 | 570 | 0.75 | 5 / -1518 / 1839 / 1.00 | {"2023": 2445.0, "2024": -2021.0, "2025": 3099.0, "2026": 9901.0} |
| 16 | pnf_5 | book.book_cancel.ratio_follow | {"L": 200, "z": 2.0} | sym15u | both | 8334 | 2137 | 439 | 0.67 | 0 /  /  /  | {"2023": -974.0, "2024": 373.0, "2025": 5390.0, "2026": 6562.0} |
| 17 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym10u/20u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 18 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym20u/10u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 19 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym15u/30u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 20 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym30u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -27.6 | -0.016 | 2018.6 | 0.46 | 81.3 | 35.9 |  |  |  |  | -13.5 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -9.7 | -0.007 | 1474.8 | 0.51 | 105.9 | 89.2 |  |  |  |  | -11.6 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | ACTIVITY(book) | ANCHORED | COMPOSITE | FOOTPRINT | INFORMATION | INFORMATION(book) | PRICE | PROFILE | SESSION-RELATIVE | SMOOTHING | TIME | UNKNOWN |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| bands | 8.8 [no null yet] | -9.3 [no null yet] | -17.6 [no null yet] | 5.4 [no null yet] | n/a (no signals by construction) | 9.1 [no null yet] | 5.8 [no null yet] | -20.4 [no null yet] | n/a (no signals by construction) | 6.7 [no null yet] | 5.0 [no null yet] | -44.1 [no null yet] | -48.5 [no null yet] |
| bands (native) | 39.6 [no null yet] | -23.0 [no null yet] | 5.6 [no null yet] | -24.4 [no null yet] | n/a (no signals by construction) | -44.8 [no null yet] | -16.9 [no null yet] | 28.6 [no null yet] | n/a (no signals by construction) | -20.4 [no null yet] | -21.4 [no null yet] | -9.0 [no null yet] | -18.4 [no null yet] |
| barnative | -2.8 [no null yet] | 25.5 [no null yet] | -8.2 [no null yet] | 4.7 [no null yet] | 10.9 [no null yet] | -15.5 [no null yet] | -19.4 [no null yet] | 20.3 [no null yet] | 4.0 [no null yet] | -13.5 [no null yet] | 2.5 [no null yet] | -37.5 [no null yet] | 17.1 [no null yet] |
| book | -2.2 [no null yet] | -27.2 [no null yet] | n/a (no signals by construction) | 7.7 [no null yet] | n/a (no signals by construction) | -8.7 [no null yet] | -25.2 [no null yet] | 13.5 [no null yet] | n/a (no signals by construction) | 0.8 [no null yet] | -7.8 [no null yet] | -23.7 [no null yet] | -8.5 [no null yet] |
| book (native) | -11.1 [no null yet] | 0.6 [no null yet] | n/a (no signals by construction) | 28.8 [no null yet] | n/a (no signals by construction) | -18.6 [no null yet] | -32.4 [no null yet] | -12.4 [no null yet] | n/a (no signals by construction) | -17.4 [no null yet] | 46.5 [no null yet] | -31.7 [no null yet] | 37.4 [no null yet] |
| confluence | -9.1 [no null yet] | 3.9 [no null yet] | -6.9 [no null yet] | -12.6 [no null yet] | -17.9 [no null yet] | -6.2 [no null yet] | -29.8 [no null yet] | -27.5 [no null yet] | 1.8 [no null yet] | -15.6 [no null yet] | -27.1 [no null yet] | -18.3 [no null yet] | -8.4 [no null yet] |
| levels | -7.9 [no null yet] | 14.3 [no null yet] | -0.7 [no null yet] | 22.3 [no null yet] | 27.6 [no null yet] | -34.5 [no null yet] | 16.7 [no null yet] | -22.6 [no null yet] | -16.5 [no null yet] | -19.3 [no null yet] | -7.1 [no null yet] | -21.1 [no null yet] | -44.4 [no null yet] |
| levels (native) | -6.7 [no null yet] | 22.1 [no null yet] | -1.8 [no null yet] | -0.3 [no null yet] | -3.9 [no null yet] | -21.6 [no null yet] | 44.3 [no null yet] | -29.1 [no null yet] | 8.9 [no null yet] | -10.1 [no null yet] | -10.3 [no null yet] | -22.3 [no null yet] | -39.0 [no null yet] |
| live | -16.3 [no null yet] | -2.1 [no null yet] | -29.2 [no null yet] | -8.2 [no null yet] | n/a (no signals by construction) | -34.6 [no null yet] | -50.0 [no null yet] | -21.2 [no null yet] | n/a (no signals by construction) | -40.4 [no null yet] | 28.9 [no null yet] | -16.8 [no null yet] | -2.6 [no null yet] |
| manual | -14.4 [no null yet] | -24.7 [no null yet] | -51.0 [no null yet] | -29.2 [no null yet] | -5.8 [no null yet] | -28.0 [no null yet] | -3.2 [no null yet] | 7.2 [no null yet] | -7.5 [no null yet] | -6.4 [no null yet] | -8.2 [no null yet] | 5.6 [no null yet] | -9.0 [no null yet] |
| manual (native) | 19.0 [no null yet] | 5.1 [no null yet] | -25.2 [no null yet] | 21.7 [no null yet] | n/a (no signals by construction) | 13.8 [no null yet] | -25.3 [no null yet] | 17.9 [no null yet] | n/a (no signals by construction) | 32.0 [no null yet] | -8.0 [no null yet] | -17.8 [no null yet] | -23.6 [no null yet] |
| momentum | 1.0 [no null yet] | -10.9 [no null yet] | -10.7 [no null yet] | -25.6 [no null yet] | 16.5 [no null yet] | -8.0 [no null yet] | -30.8 [no null yet] | -11.0 [no null yet] | -15.0 [no null yet] | -5.8 [no null yet] | -34.9 [no null yet] | -4.7 [no null yet] | -26.0 [no null yet] |
| momentum (native) | 3.4 [no null yet] | 7.1 [no null yet] | -0.6 [no null yet] | -21.6 [no null yet] | n/a (no signals by construction) | -28.1 [no null yet] | -10.9 [no null yet] | 0.0 [no null yet] | n/a (no signals by construction) | -2.7 [no null yet] | -17.4 [no null yet] | -12.4 [no null yet] | -29.5 [no null yet] |
| pullback | -35.6 [no null yet] | -53.7 [no null yet] | 28.3 [no null yet] | 18.5 [no null yet] | -30.2 [no null yet] | -30.1 [no null yet] | 6.5 [no null yet] | -10.5 [no null yet] | 6.0 [no null yet] | -60.0 [no null yet] | -37.0 [no null yet] | -17.4 [no null yet] | -7.5 [no null yet] |
| pullback (native) | -11.5 [no null yet] | -51.9 [no null yet] | -21.5 [no null yet] | -13.3 [no null yet] | n/a (no signals by construction) | -6.8 [no null yet] | 4.5 [no null yet] | -14.4 [no null yet] | n/a (no signals by construction) | -15.3 [no null yet] | -7.7 [no null yet] | -14.0 [no null yet] | -16.4 [no null yet] |
| structure | 6.9 [no null yet] | -13.0 [no null yet] | -25.2 [no null yet] | -14.6 [no null yet] | -41.4 [no null yet] | -10.5 [no null yet] | 12.5 [no null yet] | -41.2 [no null yet] | -6.4 [no null yet] | -14.6 [no null yet] | -31.9 [no null yet] | 16.1 [no null yet] | -37.9 [no null yet] |
| structure (native) | 4.3 [no null yet] | -37.3 [no null yet] | -9.9 [no null yet] | -38.4 [no null yet] | n/a (no signals by construction) | -40.4 [no null yet] | 3.2 [no null yet] | -19.2 [no null yet] | n/a (no signals by construction) | -18.2 [no null yet] | 17.3 [no null yet] | 31.5 [no null yet] | -9.1 [no null yet] |
| tape | -14.6 [no null yet] | 17.8 [no null yet] | -7.8 [no null yet] | 7.5 [no null yet] | -2.7 [no null yet] | 24.1 [no null yet] | 42.6 [no null yet] | -6.9 [no null yet] | -8.0 [no null yet] | -22.2 [no null yet] | -26.0 [no null yet] | -4.5 [no null yet] | 17.2 [no null yet] |
| tape (native) | 11.1 [no null yet] | -0.5 [no null yet] | -26.2 [no null yet] | -11.4 [no null yet] | n/a (no signals by construction) | -19.8 [no null yet] | -30.2 [no null yet] | 18.1 [no null yet] | n/a (no signals by construction) | 6.5 [no null yet] | -34.1 [no null yet] | 6.2 [no null yet] | -15.2 [no null yet] |
| trend | -20.4 [no null yet] | 13.2 [no null yet] | -12.5 [no null yet] | -34.1 [no null yet] | -13.8 [no null yet] | 26.3 [no null yet] | -20.5 [no null yet] | 12.1 [no null yet] | -9.0 [no null yet] | 26.3 [no null yet] | -36.4 [no null yet] | 35.4 [no null yet] | -30.7 [no null yet] |
| trend (native) | 8.3 [no null yet] | -32.5 [no null yet] | 4.0 [no null yet] | -10.9 [no null yet] | n/a (no signals by construction) | 10.5 [no null yet] | -13.9 [no null yet] | -8.2 [no null yet] | n/a (no signals by construction) | 7.6 [no null yet] | -20.1 [no null yet] | 23.1 [no null yet] | -6.7 [no null yet] |
| xmarket | 29.6 [no null yet] | -3.9 [no null yet] | -16.8 [no null yet] | -5.1 [no null yet] | -23.7 [no null yet] | -31.5 [no null yet] | -23.1 [no null yet] | -33.1 [no null yet] | 14.7 [no null yet] | -19.2 [no null yet] | -2.0 [no null yet] | -35.7 [no null yet] | -1.5 [no null yet] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| book (native)|SMOOTHING | 46.5 | 0.037 | 335.7 | 0.57 | 93.2 | -17.2 | {"2023": -4.2, "2024": 1.5, "2025": 37.5, "2026": 126.3} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION(book) | 44.3 | 0.040 | 210.8 | 0.59 | 70.2 | -80.0 | {"2023": 11.9, "2024": 36.3, "2025": 52.0, "2026": 54.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|INFORMATION(book) | 42.6 | 0.028 | 301.6 | 0.54 | 158.6 | 151.8 | {"2023": -95.7, "2024": 30.8, "2025": 37.0, "2026": 107.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 39.6 | 0.040 | 259.1 | 0.56 | 62.6 | 16.5 | {"2023": 62.0, "2024": 59.6, "2025": 27.8, "2026": 22.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|UNKNOWN | 37.4 | 0.036 | 443.0 | 0.53 | 91.9 | 13.6 | {"2023": 1.3, "2024": 8.0, "2025": 2.0, "2026": 125.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|TIME | 35.4 | 0.023 | 375.2 | 0.54 | 98.7 | -47.7 | {"2023": -58.2, "2024": -4.4, "2025": 73.9, "2026": 66.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual (native)|SESSION-RELATIVE | 32.0 | 0.033 | 418.9 | 0.54 | 79.6 | 173.0 | {"2023": 6.7, "2024": 11.9, "2025": 27.8, "2026": 68.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 31.5 | 0.026 | 328.1 | 0.59 | 21.9 | -43.7 | {"2023": 49.7, "2024": -2.0, "2025": 41.2, "2026": 53.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| xmarket|ACTIVITY | 29.6 | 0.033 | 318.1 | 0.56 | 3.8 | -34.4 | {"2023": -4.8, "2024": 14.9, "2025": 77.9, "2026": 0.9} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| live|SMOOTHING | 28.9 | 0.030 | 314.4 | 0.58 | 105.9 | 63.2 | {"2023": -15.4, "2024": 6.4, "2025": 24.7, "2026": 74.5} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 24% (top 75.5%); M7 tm60 L6M -36.8 pts/wk, rank 15% (top 84.6%); U7 tm600 L6M 4.8 pts/wk, rank 62% (top 38.3%); P7 tm60 L6M -35.9 pts/wk, rank 16% (top 84.1%); H7 tm60 L6M -20.1 pts/wk, rank 26% (top 73.7%); A7 tm60 L6M -32.5 pts/wk, rank 18% (top 82.3%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| trend|PRICE | 48.1 | 0.032 | 329.9 | 0.60 | 70.9 | 32.0 | {"2023": -34.0, "2024": 33.8, "2025": 85.3, "2026": 47.1} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|ACTIVITY | 43.4 | 0.042 | 379.7 | 0.62 | 10.5 | 40.4 | {"2023": 89.1, "2024": 16.8, "2025": 55.3, "2026": 46.1} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|INFORMATION | 42.5 | 0.015 | 362.5 | 0.62 | 5.0 | 119.9 | {"2023": 14.4, "2024": 32.3, "2025": 62.8, "2026": 39.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|TIME | 42.0 | 0.026 | 323.5 | 0.57 | 98.7 | -47.7 | {"2023": -34.1, "2024": -2.6, "2025": 86.1, "2026": 66.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|INFORMATION | 38.4 | 0.019 | 502.0 | 0.52 | 41.1 | 70.9 | {"2023": 69.5, "2024": -5.4, "2025": 118.0, "2026": -13.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| bands (native)|ACTIVITY | 30.3 | 0.035 | 300.0 | 0.54 | 17.6 | -81.0 | {"2023": 25.8, "2024": 69.2, "2025": 27.3, "2026": -10.8} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend (native)|TIME | 27.5 | 0.013 | 440.0 | 0.57 | 8.4 | -26.8 | {"2023": -59.9, "2024": 6.7, "2025": 114.6, "2026": -23.0} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend (native)|ACTIVITY | 27.0 | 0.027 | 357.0 | 0.53 | 60.0 | 89.7 | {"2023": 22.5, "2024": -6.7, "2025": 56.4, "2026": 33.7} |  |  |  | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| book (native)|INFORMATION | 26.1 | 0.026 | 300.6 | 0.53 | 53.2 | 19.2 | {"2023": 16.4, "2024": 18.9, "2025": 23.8, "2026": 40.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|ACTIVITY | 25.4 | 0.025 | 411.9 | 0.60 | 55.8 | 111.1 | {"2023": 14.0, "2024": 28.4, "2025": -4.6, "2026": 60.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "AMBER", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | book.book_cancel.canc_follow | {"L": 50, "z": 1.0} | sym8u | both | 7366 | 2160 | 380 | 1.00 | 5 / -1132 / 135 / 1.00 | {"2023": -3094.0, "2024": -995.0, "2025": 1960.0, "2026": 4416.0} |
| 2 | tsf_5_200 | book.book_ofi.norm_follow | {"L": 50, "z": 1.0} | sym15u | both | 7160 | 603 | 320 | 1.00 | 0 /  /  /  | {"2023": 1849.0, "2024": 706.0, "2025": 273.0, "2026": 6236.0} |
| 3 | dol_2600 | book.book_ofi.follow | {"L": 50, "z": 1.0} | sym15u | both | 7007 | 4043 | 319 | 1.00 | 0 /  /  /  | {"2023": -307.0, "2024": 115.0, "2025": -731.0, "2026": 5485.0} |
| 4 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.75 | 5 / 991 / 2269 / 1.00 | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 5 | tick_300 | tape.tape_stack.r3_follow | {"k": 3} | sym15u | both | 6975 | 1405 | 353 | 1.00 | 5 / -1233 / 2865 / 1.00 | {"2023": 598.0, "2024": 177.0, "2025": 3798.0, "2026": 6775.0} |
| 6 | dib_240 | trend.trend_heikin.run | {"len": 4, "width": 0.0} | sym15u | both | 6891 | 2495 | 1640 | 1.00 | 5 / -3332 / -350 / 1.00 | {"2023": -1257.0, "2024": -2365.0, "2025": 548.0, "2026": 6215.0} |
| 7 | dib_240 | trend.trend_heikin.run_native | {"len": 4, "width": 0.0} | sym15u | both | 6891 | 2495 | 1640 | 1.00 | 5 / -403 / 1479 / 1.00 | {"2023": -1257.0, "2024": -2365.0, "2025": 548.0, "2026": 6215.0} |
| 8 | tick_300 | tape.tape_stack.r3_follow | {"k": 3} | asym15u/30u | both | 6807 | 1237 | 352 | 1.00 | 5 / -1270 / 2922 / 1.00 | {"2023": 671.0, "2024": 1010.0, "2025": 3843.0, "2026": 6718.0} |
| 9 | tick_300 | tape.tape_stack.r3_follow | {"k": 3} | sym30u | both | 6737 | 1167 | 352 | 1.00 | 5 / -1169 / 3039 / 1.00 | {"2023": 313.0, "2024": 460.0, "2025": 4752.0, "2026": 6634.0} |
| 10 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 11 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 12 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym10u/20u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1046.0, "2024": -1508.0, "2025": 3102.0, "2026": 7745.0} |
| 13 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym15u/30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 14 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym20u/10u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1266.0, "2024": -1067.0, "2025": 3095.0, "2026": 7745.0} |
| 15 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym8u | both | 6722 | 2181 | 270 | 1.00 | 5 / 507 / 1497 / 1.00 | {"2023": -1094.0, "2024": -1432.0, "2025": 3159.0, "2026": 7746.0} |
| 16 | tick_300 | tape.tape_stack.r3_follow | {"k": 3} | asym20u/10u | both | 6680 | 1688 | 363 | 1.00 | 5 / -1956 / 1762 / 1.00 | {"2023": 991.0, "2024": 587.0, "2025": 3942.0, "2026": 6202.0} |
| 17 | tib_15000 | book.book_dwm.drift_follow | {"L": 50, "z": 1.0} | asym10u/20u | both | 6611 | 2061 | 308 | 1.00 | 5 / 512 / 4179 / 1.00 | {"2023": 754.0, "2024": 1292.0, "2025": -1072.0, "2026": 7590.0} |
| 18 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 10, "r": 0.6} | plain60/60 | both | 6610 | 590 | 1034 | 1.00 | 5 / -1524 / -356 / 1.00 | {"2023": -294.0, "2024": 1303.0, "2025": 3131.0, "2026": 6965.0} |
| 19 | tib_15000 | book.book_dwm.drift_follow | {"L": 50, "z": 1.0} | asym15u/30u | both | 6606 | 2056 | 308 | 1.00 | 5 / 568 / 4196 / 1.00 | {"2023": 865.0, "2024": 1011.0, "2025": -1256.0, "2026": 7537.0} |
| 20 | tib_15000 | book.book_dwm.drift_follow | {"L": 50, "z": 1.0} | sym15u | both | 6606 | 2056 | 308 | 1.00 | 5 / 568 / 4196 / 1.00 | {"2023": 691.0, "2024": 1001.0, "2025": -1256.0, "2026": 7537.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -14.7 | -0.015 | 804.2 | 0.47 | -55.9 | -170.4 |  |  |  |  | -5.0 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -14.1 | -0.012 | 790.4 | 0.46 | -48.0 | -153.2 |  |  |  |  | -1.4 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 8.8 [no null yet] | 18.2 [no null yet] | 34.9 [no null yet] | 14.4 [no null yet] |
| bands (native) | -0.3 [no null yet] | 4.9 [no null yet] | 16.6 [no null yet] | 14.1 [no null yet] |
| barnative | 7.1 [no null yet] | -15.8 [no null yet] | -25.9 [no null yet] | -23.0 [no null yet] |
| book | -11.1 [no null yet] | -1.4 [no null yet] | -3.2 [no null yet] | -8.2 [no null yet] |
| book (native) | 2.4 [no null yet] | -27.9 [no null yet] | -5.3 [no null yet] | -28.8 [no null yet] |
| confluence | 9.3 [no null yet] | -10.9 [no null yet] | 21.0 [no null yet] | -25.6 [no null yet] |
| levels | -5.2 [no null yet] | -0.6 [no null yet] | 15.3 [no null yet] | -0.1 [no null yet] |
| levels (native) | 7.4 [no null yet] | -9.0 [no null yet] | 3.7 [no null yet] | -0.3 [no null yet] |
| live | 18.1 [no null yet] | -1.7 [no null yet] | -1.9 [no null yet] | 11.7 [no null yet] |
| manual | 8.2 [no null yet] | -3.5 [no null yet] | -1.7 [no null yet] | -19.3 [no null yet] |
| manual (native) | -3.2 [no null yet] | -28.5 [no null yet] | -9.6 [no null yet] | 6.7 [no null yet] |
| momentum | 23.7 [no null yet] | 15.2 [no null yet] | 25.7 [no null yet] | -1.2 [no null yet] |
| momentum (native) | -5.8 [no null yet] | 4.1 [no null yet] | 11.8 [no null yet] | 3.2 [no null yet] |
| pullback | 16.6 [no null yet] | -0.5 [no null yet] | -20.7 [no null yet] | -22.2 [no null yet] |
| pullback (native) | 19.4 [no null yet] | 3.0 [no null yet] | 10.9 [no null yet] | 6.1 [no null yet] |
| structure | -10.7 [no null yet] | 11.4 [no null yet] | -0.7 [no null yet] | -11.4 [no null yet] |
| structure (native) | 5.8 [no null yet] | 17.3 [no null yet] | 17.1 [no null yet] | -20.1 [no null yet] |
| tape | 10.4 [no null yet] | -13.1 [no null yet] | -13.7 [no null yet] | 1.3 [no null yet] |
| tape (native) | 3.2 [no null yet] | -14.6 [no null yet] | -11.2 [no null yet] | -3.5 [no null yet] |
| trend | 1.2 [no null yet] | -7.1 [no null yet] | 7.1 [no null yet] | -1.2 [no null yet] |
| trend (native) | -9.0 [no null yet] | 17.0 [no null yet] | -6.8 [no null yet] | -20.1 [no null yet] |
| xmarket | -3.8 [no null yet] | -27.6 [no null yet] | -17.7 [no null yet] | -26.4 [no null yet] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands|PRICE | 34.9 | 0.034 | 189.3 | 0.58 | 48.8 | 11.8 | {"2023": 9.4, "2024": 19.8, "2025": 59.3, "2026": 31.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|PRICE | 25.7 | 0.021 | 379.4 | 0.59 | -76.5 | -22.7 | {"2023": 2.6, "2024": 35.8, "2025": 64.2, "2026": -24.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum|ACTIVITY | 23.7 | 0.026 | 361.2 | 0.53 | 35.8 | 6.9 | {"2023": -4.5, "2024": 14.9, "2025": 10.4, "2026": 58.7} |  |  |  | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|PRICE | 21.0 | 0.026 | 319.0 | 0.53 | 43.7 | -37.2 | {"2023": 7.2, "2024": 20.7, "2025": 13.1, "2026": 35.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|ACTIVITY | 19.4 | 0.005 | 483.8 | 0.62 | -63.2 | -132.6 | {"2023": 38.4, "2024": 22.6, "2025": 31.7, "2026": -5.0} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| bands|INFORMATION | 18.2 | 0.024 | 267.4 | 0.54 | 78.7 | 27.5 | {"2023": 18.9, "2024": 6.1, "2025": 29.3, "2026": 19.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| live|ACTIVITY | 18.1 | 0.028 | 267.1 | 0.59 | 9.4 | 31.3 | {"2023": 26.3, "2024": 16.6, "2025": 13.4, "2026": 22.6} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 17.3 | 0.029 | 440.9 | 0.56 | 95.7 | 137.0 | {"2023": 2.4, "2024": 22.0, "2025": 7.2, "2026": 28.5} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|PRICE | 17.1 | 0.018 | 236.4 | 0.54 | -9.4 | -97.3 | {"2023": -8.3, "2024": 37.9, "2025": 10.4, "2026": 8.3} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|INFORMATION | 17.0 | 0.008 | 317.0 | 0.60 | 23.2 | -22.2 | {"2023": -6.8, "2024": 20.9, "2025": 32.6, "2026": 1.7} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 2.0%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.3%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 10.1%); P7 tm60 L6M 66.1 pts/wk, rank 97% (top 2.6%); H7 tm60 L6M 25.1 pts/wk, rank 84% (top 15.7%); A7 tm60 L6M 6.5 pts/wk, rank 66% (top 34.4%). Rank = share of ALL Asia cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|INFORMATION | 45.6 | 0.042 | 166.0 | 0.67 | 60.3 | -22.7 | {"2023": -4.7, "2024": 63.3, "2025": 29.9, "2026": 59.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend (native)|INFORMATION | 35.9 | 0.043 | 138.1 | 0.63 | 85.5 | 73.2 | {"2023": -15.1, "2024": 33.9, "2025": 22.7, "2026": 69.9} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 33.8 | 0.037 | 182.7 | 0.57 | 56.6 | 27.6 | {"2023": 12.0, "2024": 17.2, "2025": 41.0, "2026": 51.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|PRICE | 32.5 | 0.038 | 181.1 | 0.54 | 66.8 | -18.5 | {"2023": -18.2, "2024": 3.9, "2025": 64.1, "2026": 45.2} |  |  |  | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|INFORMATION | 30.8 | 0.038 | 300.3 | 0.57 | 29.0 | 9.0 | {"2023": 35.2, "2024": 13.9, "2025": 47.4, "2026": 29.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 30.3 | 0.037 | 154.1 | 0.53 | 57.8 | -34.1 | {"2023": 10.0, "2024": 4.4, "2025": 40.4, "2026": 55.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|INFORMATION | 30.3 | 0.044 | 219.6 | 0.63 | 91.0 | 60.8 | {"2023": 18.8, "2024": 26.4, "2025": 39.4, "2026": 27.7} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|PRICE | 27.8 | 0.032 | 195.2 | 0.60 | 81.0 | 16.1 | {"2023": 27.7, "2024": -1.1, "2025": 30.1, "2026": 59.2} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|INFORMATION | 26.5 | 0.037 | 606.5 | 0.62 | -68.3 | -76.0 | {"2023": 53.9, "2024": 51.6, "2025": 71.3, "2026": -64.9} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| pullback (native)|PRICE | 25.1 | 0.024 | 289.4 | 0.52 | 32.9 | -35.9 | {"2023": 51.4, "2024": 32.9, "2025": -17.2, "2026": 57.4} |  |  |  | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | trend.trend_ma_hma.cross | {"len": 13, "width": 3, "hyst": 0.0} | sym30u | both | 7428 | 3631 | 401 | 0.83 | 5 / -601 / 763 / 1.00 | {"2023": 254.0, "2024": -1383.0, "2025": 13.0, "2026": 5811.0} |
| 2 | vol_350 | levels.levels_profile_nodes.break_native | {"n": 2, "k": 0.25} | sym8u | both | 6822 | 2719 | 315 | 1.00 | 25 / -1048 / 2016 / 1.00 | {"2023": -337.0, "2024": 673.0, "2025": 881.0, "2026": 6105.0} |
| 3 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym15u | both | 6751 | 922 | 421 | 1.00 | 5 / 1088 / 3330 / 1.00 | {"2023": -77.0, "2024": -853.0, "2025": 1402.0, "2026": 4274.0} |
| 4 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | sym30u | both | 6726 | 1912 | 361 | 1.00 | 5 / -1769 / 48 / 1.00 | {"2023": 200.0, "2024": -1629.0, "2025": 358.0, "2026": 5560.0} |
| 5 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | asym15u/30u | both | 6726 | 1912 | 361 | 1.00 | 5 / -1768 / 48 / 1.00 | {"2023": 35.0, "2024": -1811.0, "2025": -37.0, "2026": 5560.0} |
| 6 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | sym15u | both | 6709 | 1912 | 361 | 1.00 | 5 / -1774 / 48 / 1.00 | {"2023": 18.0, "2024": -1198.0, "2025": 523.0, "2026": 5386.0} |
| 7 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | sym15u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 263.0, "2024": 1748.0, "2025": 223.0, "2026": 4461.0} |
| 8 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym10u/20u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 235.0, "2024": 1394.0, "2025": 355.0, "2026": 4461.0} |
| 9 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | sym30u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 229.0, "2024": 1726.0, "2025": 223.0, "2026": 4461.0} |
| 10 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym20u/10u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 154.0, "2024": 1956.0, "2025": 393.0, "2026": 4461.0} |
| 11 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | asym15u/30u | both | 6597 | 3447 | 333 | 1.00 | 5 / -608 / 2211 / 1.00 | {"2023": 223.0, "2024": 1748.0, "2025": 223.0, "2026": 4461.0} |
| 12 | vsess_80 | tape.tape_stack.r3_fade | {"k": 3} | sym15u | both | 6583 | 2943 | 415 | 1.00 | 5 / -966 / 216 / 1.00 | {"2023": -264.0, "2024": 444.0, "2025": -14.0, "2026": 7725.0} |
| 13 | trb_400 | bands.bands_atrchan.fade_ext | {"n": 40, "atr": 14, "k": 4.0} | sym15u | both | 6579 | 1893 | 293 | 1.00 | 0 /  /  /  | {"2023": -573.0, "2024": 764.0, "2025": 713.0, "2026": 6673.0} |
| 14 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | asym20u/10u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 485.0, "2024": 1538.0, "2025": 1104.0, "2026": 4465.0} |
| 15 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | sym15u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 604.0, "2024": 1361.0, "2025": 790.0, "2026": 4491.0} |
| 16 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | asym10u/20u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 534.0, "2024": 1140.0, "2025": 939.0, "2026": 4610.0} |
| 17 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | sym30u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 490.0, "2024": 1374.0, "2025": 764.0, "2026": 4491.0} |
| 18 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | asym15u/30u | both | 6537 | 3532 | 335 | 1.00 | 5 / -780 / 1040 / 1.00 | {"2023": 585.0, "2024": 1361.0, "2025": 764.0, "2026": 4491.0} |
| 19 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | sym8u | both | 6497 | 3478 | 344 | 1.00 | 5 / -872 / 882 / 1.00 | {"2023": 575.0, "2024": 914.0, "2025": -310.0, "2026": 6455.0} |
| 20 | cusum_28 | tape.tape_stack.r5_fade | {"k": 4} | sym8u | both | 6472 | 3328 | 339 | 1.00 | 5 / -650 / 2059 / 1.00 | {"2023": 143.0, "2024": 988.0, "2025": -616.0, "2026": 5650.0} |

## Exit families (second result column; stage a2, screen-level): flip study and best exit family
Flip study (random 2% sample of pass-1 cells, capped): cells negative on EVERY fixed bracket that become positive with their best of 68 exit specs. A best-of-68 pick is biased upward: read it against the null3 sample / random-entry nulls (null_pctile in the candidates table), not as a gain.
| session | cells | negative on every fixed bracket | flipped positive with an exit family |
|---|---|---|---|
| Asia | 71 | 29 | 28 |
| London | 71 | 28 | 22 |
| NYAM | 67 | 20 | 18 |
| NYPM | 71 | 19 | 14 |
| session | best exit family | cells | mean exit L6M (pts) | mean gain vs best fixed bracket |
|---|---|---|---|---|
| Asia | market target | 355 | 1517 | -924 |
| Asia | order flow | 1 | 18 | 176 |
| Asia | staged | 35 | 1750 | 18 |
| Asia | stop-and-reverse | 17 | 1976 | 202 |
| Asia | structure stop | 5 | 933 | 597 |
| Asia | time / behaviour | 143 | 1860 | -466 |
| Asia | trailing | 186 | 1902 | 204 |
| London | market target | 464 | 1041 | -1322 |
| London | order flow | 15 | -44 | 442 |
| London | staged | 51 | 1844 | -323 |
| London | stop-and-reverse | 13 | 1170 | -110 |
| London | structure stop | 3 | 1139 | -52 |
| London | time / behaviour | 120 | 1203 | -853 |
| London | trailing | 102 | 1389 | -1217 |
| NYAM | market target | 225 | 1380 | -1215 |
| NYAM | order flow | 7 | 248 | 640 |
| NYAM | staged | 19 | 1528 | 209 |
| NYAM | stop-and-reverse | 34 | 2288 | -414 |
| NYAM | structure stop | 13 | 1559 | 858 |
| NYAM | time / behaviour | 346 | 1980 | -793 |
| NYAM | trailing | 112 | 1751 | 456 |
| NYPM | market target | 469 | 1743 | -280 |
| NYPM | order flow | 9 | 115 | 500 |
| NYPM | staged | 30 | 1565 | 16 |
| NYPM | stop-and-reverse | 9 | 2574 | 297 |
| NYPM | structure stop | 7 | 1172 | 133 |
| NYPM | time / behaviour | 137 | 1171 | -707 |
| NYPM | trailing | 88 | 1453 | -164 |
Family 6 (order-flow exits) by component, candidate + live-seven + book/tape cells: best flow spec vs the cell best fixed bracket / best non-flow exit
| session | component | cells | mean best flow-spec L6M (pts) | share beating best fixed bracket | share beating best exit |
|---|---|---|---|---|---|
| Asia | absorb | 199 | -1856 | 0.06 | 0.01 |
| Asia | book | 199 | -2388 | 0.03 | 0.00 |
| Asia | delta | 199 | -2733 | 0.05 | 0.00 |
| Asia | speed | 199 | -2264 | 0.04 | 0.00 |
| Asia | wall | 199 | -2376 | 0.04 | 0.00 |
| London | absorb | 205 | -1962 | 0.08 | 0.00 |
| London | book | 205 | -2262 | 0.06 | 0.00 |
| London | delta | 205 | -2431 | 0.05 | 0.00 |
| London | speed | 205 | -2262 | 0.06 | 0.00 |
| London | wall | 205 | -2395 | 0.05 | 0.01 |
| NYAM | absorb | 218 | -3372 | 0.11 | 0.00 |
| NYAM | book | 218 | -3321 | 0.14 | 0.00 |
| NYAM | delta | 218 | -3537 | 0.17 | 0.00 |
| NYAM | speed | 218 | -2879 | 0.18 | 0.02 |
| NYAM | wall | 218 | -2975 | 0.15 | 0.01 |
| NYPM | absorb | 199 | -2814 | 0.15 | 0.00 |
| NYPM | book | 199 | -2997 | 0.13 | 0.00 |
| NYPM | delta | 200 | -3714 | 0.12 | 0.01 |
| NYPM | speed | 199 | -2836 | 0.12 | 0.01 |
| NYPM | wall | 199 | -3269 | 0.13 | 0.00 |

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
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.88 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.11 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.23 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.97 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.92 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.46 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.14 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.84 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.86 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.87 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.92 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.66 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.42 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.31 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.83 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.89 |  |
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.08 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.40 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.11 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.10 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.84 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.84 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.62 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.33 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.03 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.79 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.78 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.26 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 0.99 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.94 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.89 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.63 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.58 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.29 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.63 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.58 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.79 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.19 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.17 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.83 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.77 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.06 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.19 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.25 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.06 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.77 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.45 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.05 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.11 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.11 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.46 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.42 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.41 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.57 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.70 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.45 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.10 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.05 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.05 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.11 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.86 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.87 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.76 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.88 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.62 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.36 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.13 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.19 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.78 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.74 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.77 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.70 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.77 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.38 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.34 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.24 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.04 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.84 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.18 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.07 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.15 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.23 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.30 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.79 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.18 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.62 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.33 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.69 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.27 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.34 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.16 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.07 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.12 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.23 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.14 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.26 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.26 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.50 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.29 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.61 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.18 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.15 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.11 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.31 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.59 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell vsess_600 trend.trend_ma_hma.cross sym8u L6M 235.4 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell pnf_5 book.book_cancel.ratio_follow asym20u/10u L6M 368.6 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell time_m_1 book.book_cancel.canc_follow sym8u L6M 283.3 pts/wk vs weak baselines K7 -22.5
## LEVEL triggers per session (supply/demand first, then Fibonacci, pivots, swing S/R, level stack, others): best cell per (module, variant) over all bar rows / parameters / brackets, last 26 weeks, >= 30 trades, in-sample pick: a LEAD needs the candidates-table nulls
### London (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | dltor_B050 | {"n": 1, "F": 0} | sym15u / both | 30 | 54 | 209 | -208 | 1133 | 202 | 1 | 318 |
| sd5 | break_native | dltor_B050 | {"n": 1, "F": 0} | sym15u / both | 30 | 54 | 209 | -208 | 1133 | 202 | 1 | 318 |
| sd5 | reject | entropy_B200 | {"F": 0, "D": 15, "tol": 0.0} | sym15u / both | 33 | 900 | -59 | -353 | -551 | 1202 | 1 | 318 |
| sd5 | reject_flow | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 318 |
| sd5 | reject_flow_native | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 318 |
| sd5 | reject_native | entropy_B200 | {"F": 0, "D": 15, "tol": 0.0} | sym15u / both | 33 | 900 | -59 | -353 | -551 | 1202 | 1 | 318 |
| sdx15 | break | kagi_80 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 140 | 2579 | 645 | -535 | -454 | 2325 | 1 | 318 |
| sdx15 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 195 | 2214 | 105 | -102 | 862 | 1176 | 1 | 318 |
| sdx15 | lim_prox | kagi_112 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 156 | 1722 | -776 | 900 | -2080 | 1504 | 1 | 318 |
| sdx15 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 158 | 1967 | -30 | 572 | 2203 | 2707 | 1 | 318 |
| sdx15 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / both | 200 | 1025 | 1001 | -160 | -409 | -111 | 1 | 318 |
| sdx15 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 318 |
| sdx15 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 318 |
| sdx15 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 73 | 1895 | -252 | -737 | -146 | 1593 | 1 | 318 |
| sdx3 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 3088 | -168 | 318 | -923 | 2963 | 1 | 318 |
| sdx3 | lim_mid | kagi_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 276 | 3690 | 400 | 1269 | -2651 | 4082 | 1 | 318 |
| sdx3 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 358 | 4320 | 49 | 1608 | -1461 | 3654 | 1 | 318 |
| sdx3 | rej | vrb_240 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 293 | 2490 | 568 | 801 | -2604 | 2253 | 1 | 318 |
| sdx3 | rej_flow | wrenko_20 | {"d": "B", "F": 9} | sym15u / both | 71 | 1238 | -32 | -410 | -333 | 1105 | 1 | 318 |
| sdx3 | rej_native | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 245 | 3620 | 859 | 1354 | 441 | 3653 | 1 | 318 |
| sdx3 | rej_zone | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 219 | 3956 | 1228 | 1976 | -779 | 5574 | 1 | 318 |
| sdx3 | retest | urenko_28 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 1786 | -723 | -195 | 1688 | 2539 | 1 | 318 |
| sdx30 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 75 | 1445 | 411 | -743 | -552 | 1630 | 1 | 319 |
| sdx30 | lim_mid | kagi_56 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 112 | 1852 | -92 | 580 | -256 | 1934 | 1 | 319 |
| sdx30 | lim_prox | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 228 | 3089 | -6 | 17 | 1634 | 3464 | 1 | 319 |
| sdx30 | rej | volor_B500 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 115 | 856 | -196 | -984 | -800 | 918 | 1 | 319 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 31 | 633 | -473 | 306 | 239 | 176 | 1 | 319 |
| sdx30 | rej_native | kagi_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / long | 51 | 1413 | 260 | -189 | -77 | 1398 | 1 | 319 |
| sdx30 | rej_zone | time_m_45 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 130 | 2103 | -471 | -5 | -430 | 2659 | 1 | 319 |
| sdx30 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 30 | 570 | 110 | -6 | 144 | 250 | 1 | 319 |
| sdx5 | break | volor_B500 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 206 | 3514 | 516 | 1174 | 2114 | 856 | 1 | 318 |
| sdx5 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 214 | 2364 | 118 | 1141 | -997 | 2486 | 1 | 318 |
| sdx5 | lim_prox | vrb_400 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 584 | 2703 | -466 | -813 | 2051 | 3816 | 1 | 318 |
| sdx5 | rej | vrb_700 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 216 | 2671 | -193 | -1603 | 1240 | 2253 | 1 | 318 |
| sdx5 | rej_flow | vrb_700 | {"d": "B", "F": 9} | plain60/60 / both | 83 | 1379 | -251 | -555 | 1072 | 759 | 1 | 318 |
| sdx5 | rej_native | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 155 | 2126 | -203 | -436 | 139 | 981 | 1 | 318 |
| sdx5 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 102 | 1959 | 163 | 674 | -953 | 2077 | 1 | 318 |
| sdx5 | retest | kagi_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 156 | 3004 | -581 | -1198 | -562 | 1728 | 1 | 318 |
| sdx60 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 31 | 1222 | -351 | -320 | 116 | 1749 | 1 | 318 |
| sdx60 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 162 | 2417 | -215 | 125 | -1666 | 2534 | 1 | 318 |
| sdx60 | lim_prox | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 3080 | 290 | 236 | -323 | 3089 | 1 | 318 |
| sdx60 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 32 | 1124 | -130 | -222 | -19 | 853 | 1 | 318 |
| sdx60 | rej_flow | vrb_400 | {"d": "E", "F": 9} | sym15u / long | 30 | 462 | 225 | 259 | 54 | 288 | 1 | 318 |
| sdx60 | rej_native | pnf_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 318 |
| sdx60 | rej_zone | tm900 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 104 | 2554 | -688 | -379 | 73 | 2243 | 1 | 318 |
| sdx_renko28 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 144 | 2263 | -119 | -618 | -1891 | 1174 | 1 | 317 |
| sdx_renko28 | lim_mid | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 157 | 2991 | -88 | -812 | -829 | 2811 | 1 | 317 |
| sdx_renko28 | lim_prox | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 156 | 3623 | -359 | -657 | -693 | 3375 | 1 | 317 |
| sdx_renko28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 1095 | 778 | -472 | 371 | -403 | 1 | 317 |
| sdx_renko28 | rej_flow | vrb_15000 | {"d": "E", "F": 9} | plain60/60 / long | 32 | 542 | 162 | 146 | 533 | 484 | 1 | 317 |
| sdx_renko28 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 244 | 1564 | -622 | 717 | -706 | 1249 | 1 | 317 |
| sdx_renko28 | rej_zone | swing_pct_12 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 164 | 1703 | -149 | 463 | -1122 | 1532 | 1 | 317 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 85 | 1772 | -155 | -1444 | -732 | 1006 | 1 | 317 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 317 |
| sdx_rng28 | lim_mid | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 795 | 3282 | -633 | 132 | -4220 | 3878 | 1 | 317 |
| sdx_rng28 | lim_prox | wrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 281 | 2565 | -697 | 820 | 191 | 5046 | 1 | 317 |
| sdx_rng28 | rej | kagi_56 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 93 | 1361 | 603 | 353 | -205 | 971 | 1 | 317 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / both | 166 | 1446 | 811 | -32 | 1520 | 715 | 1 | 317 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 317 |
| sdx_rng28 | rej_zone | tm15 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 1360 | 2116 | -1371 | -1023 | -2934 | 1860 | 1 | 317 |
| sdx_rng28 | retest | kagi_80 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 197 | 2393 | -337 | 390 | -2202 | 908 | 1 | 317 |
| sdx_vol1100 | break | frenko_28 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 2638 | -348 | -213 | 189 | 2953 | 1 | 317 |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 209 | 3784 | 896 | 457 | 888 | 4785 | 1 | 317 |
| sdx_vol1100 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 244 | 3123 | 198 | -474 | 859 | 3530 | 1 | 317 |
| sdx_vol1100 | rej | volor_B500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 322 | 1557 | 668 | 379 | 1376 | 2062 | 1 | 317 |
| sdx_vol1100 | rej_flow | volor_B500 | {"d": "E", "F": 0} | sym15u / both | 176 | 1646 | 190 | -179 | -1010 | 2417 | 1 | 317 |
| sdx_vol1100 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 317 |
| sdx_vol1100 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 317 |
| sdx_vol1100 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 112 | 1778 | -246 | -234 | -609 | 1473 | 1 | 317 |
| fib15 | break | pnf_5 | {"n": 3, "k": 0.5} | sym8u / both | 288 | 4201 | -619 | -2233 | -1116 | 4287 | 2 | 318 |
| fib15 | break_native | swing_atr_0.15 | {"n": 2, "k": 0.25} | sym15u / both | 241 | 3875 | -629 | -511 | 2215 | 4625 | 1 | 318 |
| fib15 | false_break | dchg_56 | {"M": 3, "k": 0.5} | sym15u / both | 243 | 4145 | 434 | 267 | -571 | 3261 | 1 | 318 |
| fib15 | false_break_native | dchg_56 | {"M": 1, "k": 0.0} | sym15u / both | 243 | 3977 | 403 | 295 | -878 | 3409 | 1 | 318 |
| fib15 | pullback | tsf_10_30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 146 | 1994 | 210 | 313 | -1254 | 2290 | 1 | 318 |
| fib15 | pullback_native | tsf_10_30 | {"tol": 0.5, "conf": "body"} | sym15u / both | 160 | 2562 | 527 | 71 | 107 | 2897 | 1 | 318 |
| fib15 | reject | cusum_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 234 | 3738 | 129 | -213 | 1394 | 3664 | 1 | 318 |
| fib15 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3703 | -555 | 839 | 2164 | 4988 | 1 | 318 |
| fib15 | retest | tib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 215 | 3026 | 594 | -427 | -629 | 2938 | 1 | 318 |
| fib15 | retest_native | tib_3500 | {"M": 3, "tol": 0.0} | sym15u / both | 204 | 2963 | 937 | 328 | -1139 | 1614 | 1 | 318 |
| fib5 | break | entropy_B130 | {"n": 1, "k": 0.0} | sym15u / both | 262 | 2770 | -1307 | 1484 | -335 | 2778 | 1 | 319 |
| fib5 | break_native | trb_3500 | {"n": 2, "k": 0.25} | sym15u / both | 221 | 2984 | -125 | -737 | 2280 | 2984 | 1 | 319 |
| fib5 | false_break | dchg_80 | {"M": 2, "k": 0.5} | sym15u / both | 215 | 3386 | 719 | 315 | -1355 | 3421 | 1 | 319 |
| fib5 | false_break_native | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 232 | 3243 | 1008 | -540 | 1443 | 3077 | 1 | 319 |
| fib5 | pullback | dol_2600 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 2572 | -11 | -107 | 971 | 3053 | 1 | 319 |
| fib5 | pullback_native | dol_2600 | {"tol": 0.5, "conf": "body"} | sym15u / both | 184 | 1875 | 293 | 354 | 299 | 1925 | 1 | 319 |
| fib5 | reject | cusum_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3943 | -37 | -55 | 1500 | 4956 | 1 | 319 |
| fib5 | reject_native | cusum_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3849 | -85 | 719 | -430 | 3661 | 1 | 319 |
| fib5 | retest | tm2700 | {"M": 10, "tol": 0.5} | sym15u / both | 229 | 3220 | -742 | 398 | 1339 | 2419 | 1 | 319 |
| fib5 | retest_native | tm2700 | {"M": 10, "tol": 0.5} | sym15u / both | 231 | 3970 | -348 | 302 | 2508 | 3180 | 1 | 319 |
| fib60 | break | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 239 | 3070 | -415 | -857 | -1083 | 3353 | 1 | 319 |
| fib60 | break_native | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 239 | 3697 | -809 | -1703 | -422 | 3980 | 1 | 319 |
| fib60 | false_break | kagi_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 222 | 3269 | 330 | 1054 | -527 | 4521 | 2 | 319 |
| fib60 | false_break_native | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2893 | 639 | 1418 | -423 | 3303 | 1 | 319 |
| fib60 | pullback | tsf_25_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 64 | 1454 | -594 | -222 | 755 | 1483 | 1 | 319 |
| fib60 | pullback_native | trend_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 124 | 1824 | 223 | -126 | -1859 | -12 | 1 | 319 |
| fib60 | reject | vib_1200 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 441 | 2856 | -318 | -1663 | 309 | 2863 | 1 | 319 |
| fib60 | reject_native | dltor_B050 | {"tol": 0.5, "conf": "body"} | sym15u / both | 188 | 3256 | 434 | -472 | -3792 | 3416 | 1 | 319 |
| fib60 | retest | vsess_300 | {"M": 3, "tol": 0.0} | sym15u / both | 179 | 3386 | -443 | -174 | -2425 | 996 | 1 | 319 |
| fib60 | retest_native | dchg_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 3614 | -723 | 596 | -705 | 4775 | 1 | 319 |
| fibr_dev | break | tm3600 | {"n": 1, "k": 0.0} | sym15u / both | 202 | 3411 | -301 | -3018 | -885 | 3990 | 1 | 209 |
| fibr_dev | break_native | tm3600 | {"n": 1, "k": 0.0} | sym15u / both | 202 | 3411 | -252 | -3018 | -885 | 3990 | 1 | 209 |
| fibr_dev | false_break | tm3600 | {"M": 3, "k": 0.5} | sym15u / both | 205 | 3141 | 129 | -1246 | -12 | 3417 | 1 | 209 |
| fibr_dev | false_break_native | cusum_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 681 | 3132 | 86 | -15 | -1295 | 1547 | 1 | 209 |
| fibr_dev | reject | cusum_40 | {"tol": 0.0, "conf": "close"} | sym8u / both | 239 | 3841 | -486 | -311 | -1107 | 2422 | 2 | 209 |
| fibr_dev | reject_native | cusum_40 | {"tol": 0.0, "conf": "close"} | sym8u / both | 239 | 3841 | -486 | -311 | -1107 | 2422 | 2 | 209 |
| fibr_dev | retest | cusum_40 | {"M": 3, "tol": 0.5} | sym8u / both | 241 | 2922 | -346 | -229 | -1274 | 4122 | 2 | 209 |
| fibr_dev | retest_native | dol_750 | {"M": 10, "tol": 0.5} | sym15u / both | 256 | 3242 | -899 | -1573 | -1319 | 3065 | 1 | 209 |
| fibr_ib | break | volor_B500 | {"n": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1616 | 149 | 1 | 55 |
| fibr_ib | break_native | volor_B500 | {"n": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1616 | 149 | 1 | 55 |
| fibr_ib | false_break | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 99 | 1067 | -431 | 845 | 1563 | 149 | 1 | 55 |
| fibr_ib | false_break_native | dltor_B130 | {"M": 3, "k": 0.5} | sym15u / both | 95 | 1106 | -847 | 576 | 393 | 556 | 1 | 55 |
| fibr_ib | reject | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 45 | 742 | 532 | -814 | 411 | 633 | 1 | 55 |
| fibr_ib | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 47 | 963 | 1255 | -152 | -897 | 648 | 1 | 55 |
| fibr_ib | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 44 | 430 | -86 | -239 | 291 | 428 | 1 | 55 |
| fibr_ib | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 52 | 491 | -44 | -256 | 352 | 478 | 1 | 55 |
| fibr_on | break | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 80 | 1601 | -103 | 742 | 1715 | 905 | 1 | 55 |
| fibr_on | break_native | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 80 | 1601 | -103 | 742 | 1715 | 905 | 1 | 55 |
| fibr_on | false_break | entropy_B080 | {"M": 1, "k": 0.0} | sym15u / both | 80 | 1601 | -83 | 742 | 1715 | 905 | 1 | 55 |
| fibr_on | false_break_native | entropy_B080 | {"M": 3, "k": 0.5} | sym15u / both | 75 | 1725 | -334 | 733 | 1953 | 894 | 1 | 55 |
| fibr_on | reject | anch_L0200_B10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 36 | 250 | -55 | 157 | -259 | 211 | 1 | 55 |
| fibr_on | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 49 | 936 | 789 | -652 | -597 | 848 | 1 | 55 |
| fibr_on | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 36 | 504 | 55 | -170 | 165 | 149 | 1 | 55 |
| fibr_on | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 44 | 356 | 80 | -284 | 96 | 211 | 1 | 55 |
| fibr_or | break | dltor_B500 | {"n": 1, "k": 0.0} | sym15u / long | 44 | 873 | -287 | 898 | 1198 | 417 | 1 | 55 |
| fibr_or | break_native | dltor_B500 | {"n": 1, "k": 0.0} | sym15u / long | 44 | 873 | -287 | 898 | 1198 | 417 | 1 | 55 |
| fibr_or | false_break | dltor_B500 | {"M": 1, "k": 0.0} | sym15u / long | 44 | 873 | -287 | 898 | 1198 | 538 | 1 | 55 |
| fibr_or | false_break_native | dltor_B500 | {"M": 1, "k": 0.0} | sym15u / long | 44 | 873 | -287 | 898 | 1198 | 538 | 1 | 55 |
| fibr_or | reject | tpo_30m | {"tol": 0.5, "conf": "body"} | sym15u / both | 31 | 1032 | 508 | 85 | -339 | 1621 | 1 | 55 |
| fibr_or | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 43 | 1681 | 973 | 147 | -513 | 1666 | 1 | 55 |
| fibr_or | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 41 | 416 | -13 | -330 | 136 | 203 | 1 | 55 |
| fibr_or | retest_native | anch_L0200_B10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 36 | 477 | -37 | -292 | 40 | 245 | 1 | 55 |
| fibr_pd | break | tm240 | {"n": 3, "k": 0.5} | sym15u / both | 186 | 3753 | 257 | -4 | -1554 | 3468 | 1 | 206 |
| fibr_pd | break_native | tib_6000 | {"n": 3, "k": 0.5} | sym15u / both | 185 | 3419 | -502 | -354 | -1620 | 3200 | 1 | 206 |
| fibr_pd | false_break | vfp_rng16 | {"M": 1, "k": 0.0} | sym15u / both | 448 | 2964 | -383 | -233 | -993 | 1916 | 1 | 206 |
| fibr_pd | false_break_native | volor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 260 | 3280 | -780 | 77 | 1451 | 2750 | 1 | 206 |
| fibr_pd | reject | tm240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 191 | 2969 | 726 | -987 | -1096 | 3684 | 1 | 206 |
| fibr_pd | reject_native | cusum_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 229 | 4417 | 235 | 1247 | -1993 | 3460 | 1 | 206 |
| fibr_pd | retest | vsess_50 | {"M": 3, "tol": 0.0} | sym15u / both | 158 | 3177 | -750 | 204 | 11 | 3232 | 1 | 206 |
| fibr_pd | retest_native | vsess_50 | {"M": 3, "tol": 0.0} | sym15u / both | 158 | 3177 | -750 | 204 | 11 | 3232 | 1 | 206 |
| piv_cama | break | tm780 | {"n": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -904 | -1274 | 1697 | 1 | 208 |
| piv_cama | break_native | tm780 | {"n": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -904 | -1274 | 1697 | 1 | 208 |
| piv_cama | false_break | tm780 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -778 | -1274 | 1600 | 1 | 208 |
| piv_cama | false_break_native | tm780 | {"M": 1, "k": 0.0} | sym15u / both | 201 | 3247 | -541 | -778 | -1274 | 1600 | 1 | 208 |
| piv_cama | reject | trb_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 149 | 2757 | -307 | -952 | -146 | 3434 | 1 | 208 |
| piv_cama | reject_native | vnorm_150 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 577 | 4012 | -191 | -1152 | -1087 | 4672 | 1 | 208 |
| piv_cama | retest | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 208 |
| piv_cama | retest_native | renko_20 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 187 | 3306 | -823 | 102 | -483 | 2289 | 2 | 208 |
| piv_floor | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 159 | 3362 | 14 | -442 | -2052 | 4155 | 1 | 206 |
| piv_floor | break_native | sessrng_B050 | {"n": 3, "k": 0.5} | sym15u / both | 216 | 3570 | -953 | 185 | 639 | 2916 | 1 | 206 |
| piv_floor | false_break | pasl_14 | {"M": 2, "k": 0.5} | sym15u / both | 203 | 3561 | -443 | -1227 | -389 | 4694 | 2 | 206 |
| piv_floor | false_break_native | vsess_600 | {"M": 3, "k": 0.5} | sym30u / both | 177 | 3724 | -147 | -668 | -2040 | 2236 | 2 | 206 |
| piv_floor | reject | time_m_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 133 | 2041 | 960 | -194 | 155 | 3677 | 1 | 206 |
| piv_floor | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 219 | 3389 | 177 | 449 | -550 | 3714 | 1 | 206 |
| piv_floor | retest | kagi_14 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 169 | 3970 | 252 | -952 | -637 | 3561 | 2 | 206 |
| piv_floor | retest_native | kagi_14 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 169 | 3970 | 252 | -952 | -637 | 3561 | 2 | 206 |
| piv_wf | break | time_m_13 | {"n": 3, "k": 0.5} | sym15u / both | 181 | 4213 | -1022 | -1316 | -385 | 3980 | 1 | 207 |
| piv_wf | break_native | pasl_14 | {"n": 2, "k": 0.5} | sym15u / both | 200 | 3595 | -50 | -327 | 1 | 3781 | 2 | 207 |
| piv_wf | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 199 | 2887 | -211 | -1555 | -414 | 1976 | 1 | 207 |
| piv_wf | false_break_native | rngor_B320 | {"M": 2, "k": 0.5} | sym15u / both | 244 | 3106 | -83 | 816 | -1439 | 1662 | 1 | 207 |
| piv_wf | reject | tick_2000 | {"tol": 0.0, "conf": "close"} | sym8u / both | 186 | 3393 | -160 | 815 | 1052 | 2237 | 2 | 207 |
| piv_wf | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 230 | 3435 | -674 | 1015 | -1014 | 4860 | 1 | 207 |
| piv_wf | retest | entropy_B200 | {"M": 3, "tol": 0.0} | sym15u / both | 194 | 2651 | -208 | -737 | -2974 | -25 | 1 | 207 |
| piv_wf | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 180 | 3612 | 618 | -634 | -723 | 4764 | 1 | 207 |
| swcluster | break | tpo_30m | {"n": 2, "k": 0.25} | sym15u / both | 59 | 1755 | 23 | 316 | -2 | 1564 | 1 | 209 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1656 | -586 | -594 | -193 | 450 | 1 | 209 |
| swcluster | false_break | entropy_B500 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1474 | 763 | 778 | 818 | 1240 | 1 | 209 |
| swcluster | false_break_native | entropy_B500 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1474 | 678 | 675 | 801 | 1240 | 1 | 209 |
| swcluster | reject | vol_1100 | {"tol": 1.0, "conf": "body"} | sym8u / both | 49 | 1735 | -451 | -219 | -223 | 1906 | 2 | 209 |
| swcluster | reject_native | tm3600 | {"tol": 1.0, "conf": "body"} | sym15u / both | 75 | 2174 | -228 | -430 | -145 | 2452 | 1 | 209 |
| swcluster | retest | vfp_vol1000 | {"M": 6, "tol": 0.5} | sym15u / both | 39 | 1668 | 261 | -71 | -578 | 1803 | 1 | 209 |
| swcluster | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 51 | 1708 | 238 | 94 | -774 | 1926 | 1 | 209 |
| swsr15 | break | tm180 | {"n": 2, "k": 0.25} | sym15u / both | 236 | 3948 | -36 | -443 | 1132 | 5269 | 1 | 208 |
| swsr15 | break_native | rngor_B200 | {"n": 3, "k": 0.5} | sym15u / both | 251 | 3621 | -772 | 361 | 620 | 3573 | 1 | 208 |
| swsr15 | false_break | tm900 | {"M": 2, "k": 0.5} | sym15u / both | 227 | 2268 | 285 | 219 | 1485 | 2418 | 1 | 208 |
| swsr15 | false_break_native | swing_atr_0.9 | {"M": 2, "k": 0.5} | sym15u / both | 210 | 2709 | 664 | -442 | -1328 | 1568 | 1 | 208 |
| swsr15 | reject | dlt_150 | {"tol": 0.0, "conf": "close"} | sym15u / both | 190 | 3961 | -158 | 603 | -157 | 6111 | 1 | 208 |
| swsr15 | reject_native | rngor_B050 | {"tol": 0.5, "conf": "body"} | sym15u / both | 240 | 4173 | -301 | 56 | -1733 | 3939 | 1 | 208 |
| swsr15 | retest | time_m_4 | {"M": 10, "tol": 0.5} | sym15u / both | 207 | 3437 | 341 | -341 | -609 | 2002 | 1 | 208 |
| swsr15 | retest_native | time_m_4 | {"M": 10, "tol": 0.5} | sym15u / both | 213 | 3102 | 432 | 99 | 1167 | 1331 | 1 | 208 |
| swsr5 | break | time_m_30 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 3106 | 444 | -441 | -910 | 3037 | 1 | 210 |
| swsr5 | break_native | pasl_14 | {"n": 3, "k": 0.5} | asym10u/20u / both | 238 | 3201 | -72 | -1037 | -1784 | 3184 | 2 | 210 |
| swsr5 | false_break | rng_10 | {"M": 2, "k": 0.0} | asym20u/10u / both | 436 | 2677 | 83 | -1203 | -1141 | 1317 | 2 | 210 |
| swsr5 | false_break_native | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 168 | 2788 | 236 | -264 | -2437 | 2402 | 1 | 210 |
| swsr5 | reject | rng_10 | {"tol": 0.5, "conf": "close"} | sym30u / both | 262 | 2637 | -346 | 1449 | -811 | 4072 | 2 | 210 |
| swsr5 | reject_native | vib_15000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 232 | 3646 | 239 | 1058 | 2008 | 3609 | 1 | 210 |
| swsr5 | retest | tm1200 | {"M": 3, "tol": 0.0} | sym15u / both | 210 | 2903 | 107 | -1225 | -291 | 4323 | 1 | 210 |
| swsr5 | retest_native | tm1200 | {"M": 3, "tol": 0.0} | sym15u / both | 210 | 2903 | 107 | -1225 | -291 | 4323 | 1 | 210 |
| swsr60 | break | tm1200 | {"n": 3, "k": 0.5} | sym15u / both | 155 | 3042 | -320 | -1598 | -700 | 3353 | 1 | 208 |
| swsr60 | break_native | time_m_30 | {"n": 2, "k": 0.25} | sym15u / both | 139 | 2552 | -919 | -883 | 749 | 2316 | 1 | 208 |
| swsr60 | false_break | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 130 | 2339 | 179 | -971 | -440 | 3394 | 1 | 208 |
| swsr60 | false_break_native | vib_70000 | {"M": 2, "k": 0.5} | sym15u / both | 126 | 2712 | 387 | -860 | -610 | 3232 | 1 | 208 |
| swsr60 | reject | vib_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 138 | 2627 | -204 | -1067 | 651 | 1457 | 1 | 208 |
| swsr60 | reject_native | rng_10 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 207 | 2701 | -1156 | -79 | 2326 | 2840 | 2 | 208 |
| swsr60 | retest | tm780 | {"M": 3, "tol": 0.0} | sym15u / both | 111 | 2308 | -1503 | 825 | 1046 | 2805 | 1 | 208 |
| swsr60 | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 166 | 2367 | -533 | -15 | -85 | 3016 | 1 | 208 |
| stack | break | dchg_20 | {"k": 3, "cw": 1.0} | sym15u / both | 148 | 3439 | 180 | 1398 | -13 | 1975 | 1 | 317 |
| stack | break_native | trb_3500 | {"k": 2, "cw": 0.5} | sym15u / both | 177 | 3483 | 500 | -928 | -2461 | 5932 | 1 | 317 |
| stack | reject | vol_500 | {"k": 2, "cw": 1.0} | sym8u / both | 246 | 2850 | 123 | -1949 | 1764 | 3730 | 2 | 317 |
| stack | reject_native | rngor_B050 | {"k": 3, "cw": 1.0} | sym15u / both | 243 | 4621 | 305 | 261 | 353 | 4855 | 1 | 317 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 315 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 315 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 315 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 315 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 315 |
| book_walls | reject_native | vrb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 53 | 1284 | -323 | 34 | 293 | 1359 | 1 | 315 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 315 |
| book_walls | retest_native | vsess_600 | {"M": 3, "tol": 0.5} | sym15u / both | 31 | 948 | -210 | -159 | 387 | 775 | 2 | 315 |
| book_walls_loose | break | time_s_30 | {"n": 2, "k": 0.0} | sym15u / both | 196 | 2412 | -1392 | -1316 | -827 | 3160 | 2 | 317 |
| book_walls_loose | break_native | time_s_30 | {"n": 2, "k": 0.0} | sym15u / both | 196 | 2412 | -1392 | -1316 | -827 | 3160 | 2 | 317 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 255 | 1836 | -1493 | 606 | -1053 | 1533 | 1 | 317 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 255 | 1836 | -1493 | 606 | -1053 | 1533 | 1 | 317 |
| book_walls_loose | reject | vib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 182 | 4393 | -631 | 670 | -1174 | 4438 | 1 | 317 |
| book_walls_loose | reject_native | vib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 222 | 4062 | -115 | 655 | -1969 | 4447 | 1 | 317 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3516 | 15 | -764 | -863 | 4040 | 1 | 317 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1 | 317 |
| channel | break | vol_1100 | {"n": 2, "k": 0.5} | sym8u / both | 240 | 3379 | -397 | 74 | -365 | 2741 | 2 | 211 |
| channel | break_native | tib_3500 | {"n": 2, "k": 0.25} | sym15u / both | 242 | 4938 | 1342 | 691 | -1153 | 4270 | 1 | 211 |
| channel | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 172 | 2909 | -148 | -291 | -2237 | 2992 | 1 | 211 |
| channel | false_break_native | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3344 | 373 | 1739 | 1102 | 4639 | 1 | 211 |
| channel | reject | vib_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 270 | 3964 | 739 | -927 | 920 | 6025 | 1 | 211 |
| channel | reject_native | tib_2000 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 716 | 4354 | 78 | -447 | 660 | 3634 | 1 | 211 |
| channel | retest | mom_14 | {"M": 3, "tol": 0.0} | sym15u / both | 259 | 3329 | -46 | 160 | -815 | 3455 | 1 | 211 |
| channel | retest_native | tsf_5_50 | {"M": 10, "tol": 0.5} | sym15u / both | 244 | 3901 | 166 | 463 | -554 | 4061 | 1 | 211 |
| fvg15 | break | pasl_14 | {"n": 2, "k": 0.0} | sym8u / both | 131 | 2224 | -174 | 731 | -1742 | 1993 | 2 | 211 |
| fvg15 | break_native | pasl_14 | {"n": 2, "k": 0.0} | sym8u / both | 131 | 2224 | -174 | 731 | -1742 | 1993 | 2 | 211 |
| fvg15 | false_break | tsf_2_2000 | {"M": 3, "k": 0.5} | plain60/60 / both | 119 | 1305 | 260 | 241 | 232 | 1413 | 1 | 211 |
| fvg15 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | plain60/60 / short | 130 | 1094 | 257 | -577 | -633 | 1723 | 1 | 211 |
| fvg15 | reject | tm60 | {"tol": 1.0, "conf": "body"} | sym15u / both | 171 | 3746 | 117 | -599 | -2542 | 5297 | 1 | 211 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 167 | 4419 | -178 | 432 | 336 | 5177 | 1 | 211 |
| fvg15 | retest | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 90 | 3210 | 507 | -733 | -913 | 3727 | 1 | 211 |
| fvg15 | retest_native | dlt_100 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 3243 | 186 | 116 | -430 | 4261 | 1 | 211 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 208 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 208 |
| fvg5 | false_break | pasl_14 | {"M": 3, "k": 0.5} | sym8u / both | 196 | 2711 | 105 | -857 | 1646 | 3048 | 2 | 208 |
| fvg5 | false_break_native | pasl_28 | {"M": 3, "k": 0.5} | sym8u / both | 161 | 3028 | 382 | -2232 | 339 | 2828 | 2 | 208 |
| fvg5 | reject | dib_25000 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 166 | 2882 | 86 | -520 | 29 | 3642 | 1 | 208 |
| fvg5 | reject_native | rng_10 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 285 | 3008 | 382 | -3550 | 277 | 3608 | 2 | 208 |
| fvg5 | retest | rng_10 | {"M": 6, "tol": 0.0} | sym15u / both | 275 | 2627 | -786 | 667 | -2294 | 2821 | 2 | 208 |
| fvg5 | retest_native | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 189 | 3090 | -276 | -1553 | 384 | 2624 | 1 | 208 |
| gaps | break | dltor_B130 | {"n": 2, "k": 0.25} | sym15u / both | 158 | 2944 | -154 | 1653 | 91 | 1981 | 1 | 319 |
| gaps | break_native | dltor_B130 | {"n": 2, "k": 0.25} | sym15u / both | 167 | 3226 | -208 | 1396 | -211 | 1755 | 1 | 319 |
| gaps | false_break | pasl_20 | {"M": 1, "k": 0.0} | sym15u / both | 124 | 2164 | 292 | -70 | -125 | 3244 | 1 | 319 |
| gaps | false_break_native | pasl_20 | {"M": 3, "k": 0.5} | sym15u / both | 120 | 2263 | -51 | -233 | 70 | 3737 | 1 | 319 |
| gaps | reject | sessrng_B050 | {"tol": 1.0, "conf": "body"} | sym15u / both | 108 | 2501 | -672 | -948 | -1438 | 2977 | 1 | 319 |
| gaps | reject_native | tm1200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 135 | 3052 | 190 | 323 | -236 | 4051 | 1 | 319 |
| gaps | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 91 | 2306 | -171 | -1188 | -1389 | 2410 | 1 | 319 |
| gaps | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 100 | 2963 | -29 | 441 | -1448 | 3370 | 1 | 319 |
| mmove | break | time_s_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 563 | 3454 | -202 | -98 | -363 | 3125 | 1 | 212 |
| mmove | break_native | tm240 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 3345 | 1130 | -642 | 997 | 3399 | 1 | 212 |
| mmove | false_break | vib_1200 | {"M": 1, "k": 0.0} | plain60/60 / both | 637 | 3289 | 490 | -690 | -2281 | 1178 | 1 | 212 |
| mmove | false_break_native | rng_10 | {"M": 1, "k": 0.5} | plain60/60 / both | 628 | 3328 | 103 | -148 | -3385 | 3840 | 2 | 212 |
| mmove | reject | rng_10 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 599 | 4025 | -915 | -1615 | -366 | 4170 | 2 | 212 |
| mmove | reject_native | rng_10 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 572 | 4441 | -1068 | -581 | -1627 | 3739 | 2 | 212 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 212 |
| mmove | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 212 |
| ob15 | break | rngor_B320 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 1695 | -628 | -1096 | 132 | 2278 | 1 | 211 |
| ob15 | break_native | rngor_B200 | {"n": 3, "k": 0.5} | sym15u / both | 83 | 2147 | -435 | -1057 | 762 | 1762 | 1 | 211 |
| ob15 | false_break | vib_1200 | {"M": 1, "k": 0.0} | plain60/60 / both | 83 | 1095 | -793 | -470 | 65 | 1369 | 1 | 211 |
| ob15 | false_break_native | cusum_14 | {"M": 2, "k": 0.5} | plain60/60 / both | 87 | 1134 | -400 | -74 | -38 | 1045 | 1 | 211 |
| ob15 | reject | sessrng_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 2223 | 620 | -603 | 451 | 2383 | 1 | 211 |
| ob15 | reject_native | sessrng_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 76 | 1939 | 458 | -656 | -148 | 1849 | 1 | 211 |
| ob15 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1142 | 267 | -325 | 553 | 1702 | 1 | 211 |
| ob15 | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 64 | 1241 | -318 | 28 | 247 | -790 | 1 | 211 |
| ob5 | break | entropy_B200 | {"n": 1, "k": 0.0} | sym15u / both | 145 | 2754 | 121 | 567 | 1696 | 1088 | 1 | 212 |
| ob5 | break_native | entropy_B200 | {"n": 1, "k": 0.0} | sym15u / both | 145 | 2754 | 121 | 567 | 1696 | 1088 | 1 | 212 |
| ob5 | false_break | entropy_B200 | {"M": 3, "k": 0.5} | sym15u / both | 145 | 2646 | -81 | -307 | 1857 | 1139 | 1 | 212 |
| ob5 | false_break_native | entropy_B200 | {"M": 1, "k": 0.0} | sym15u / both | 145 | 2582 | 537 | 358 | 2113 | 1170 | 1 | 212 |
| ob5 | reject | trend_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 104 | 1634 | 303 | -1278 | -1957 | 995 | 1 | 212 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 | 1981 | -488 | -1059 | -729 | 757 | 1 | 212 |
| ob5 | retest | vib_10000 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 2918 | 474 | -691 | -688 | 2305 | 1 | 212 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | asym10u/20u / both | 113 | 2684 | -357 | -1108 | 54 | 2180 | 2 | 212 |
| open_range | break | dltor_B130 | {"n": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 603 | 1453 | 158 | 1 | 68 |
| open_range | break_native | dltor_B130 | {"n": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 603 | 1453 | 158 | 1 | 68 |
| open_range | false_break | dltor_B130 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 593 | 1334 | 158 | 1 | 68 |
| open_range | false_break_native | dltor_B130 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 893 | -920 | 593 | 1334 | 158 | 1 | 68 |
| open_range | reject | tpo_30m | {"tol": 0.0, "conf": "close"} | sym15u / both | 31 | 360 | 467 | 147 | -459 | 285 | 1 | 68 |
| open_range | reject_native | tpo_30m | {"tol": 1.0, "conf": "body"} | sym15u / both | 45 | 1259 | 937 | 255 | -269 | 1312 | 1 | 68 |
| open_range | retest | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 45 | 409 | -30 | -174 | 387 | 442 | 1 | 68 |
| open_range | retest_native | anch_L0200_B10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 52 | 191 | -68 | -256 | 46 | 223 | 1 | 68 |
| opens | break | renko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 3946 | 43 | 1332 | 422 | 3112 | 2 | 318 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 318 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 318 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 318 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 318 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 318 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 318 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 318 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1 | 319 |
| prior_day | break_native | dltor_B130 | {"n": 2, "k": 0.25} | sym15u / both | 183 | 2659 | -224 | 258 | 137 | 401 | 1 | 319 |
| prior_day | false_break | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2871 | 220 | 1502 | -275 | 2410 | 1 | 319 |
| prior_day | false_break_native | volor_B500 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2871 | 220 | 1502 | -275 | 2410 | 1 | 319 |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 105 | 1827 | -426 | -804 | -662 | 720 | 1 | 319 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 319 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 1 | 319 |
| prior_day | retest_native | dltor_B050 | {"M": 10, "tol": 0.5} | sym15u / both | 119 | 3556 | -235 | -293 | -833 | 3575 | 1 | 319 |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 162 | 2957 | -620 | 59 | -1689 | 2002 | 1 | 318 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 318 |
| profile_nodes | false_break | dltor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3215 | -266 | 424 | 785 | 2028 | 1 | 318 |
| profile_nodes | false_break_native | dltor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 231 | 3337 | -127 | 59 | 585 | 2388 | 1 | 318 |
| profile_nodes | reject | trend_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 152 | 2819 | -414 | -1221 | -2496 | 1650 | 1 | 318 |
| profile_nodes | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | sym15u / both | 204 | 2821 | -98 | -360 | 235 | 2346 | 2 | 318 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 318 |
| profile_nodes | retest_native | dol_750 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 3248 | -111 | -1036 | -1589 | 5058 | 1 | 318 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 2 | 319 |
| profile_va | break_native | tm300 | {"n": 3, "k": 0.0} | sym8u / both | 140 | 2699 | -69 | -2143 | -949 | 1447 | 2 | 319 |
| profile_va | false_break | dltor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 206 | 3601 | -302 | 689 | 1152 | 4150 | 1 | 319 |
| profile_va | false_break_native | volor_B500 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3874 | -137 | -603 | 770 | 4625 | 1 | 319 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 319 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 319 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym15u / both | 133 | 3198 | 93 | -1886 | -354 | 2602 | 1 | 319 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 319 |
| round | break | pasl_14 | {"n": 1, "k": 0.25} | sym15u / both | 264 | 3509 | -602 | 1209 | -2407 | 5135 | 2 | 423 |
| round | break_native | micro_B080 | {"n": 2, "k": 0.25} | sym15u / both | 250 | 4100 | -3 | -649 | -2235 | 3672 | 1 | 423 |
| round | false_break | typ_qmid_B080 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 3905 | -315 | -392 | -1352 | 2804 | 1 | 423 |
| round | false_break_native | typ_qmid_B080 | {"M": 3, "k": 0.5} | sym15u / both | 277 | 4927 | 217 | -2006 | -1716 | 4318 | 1 | 423 |
| round | reject | time_s_20 | {"tol": 0.0, "conf": "body"} | sym15u / both | 350 | 4952 | 55 | -457 | -569 | 5515 | 2 | 423 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 423 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 423 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 423 |
| session_hl | break | tsf_5_400 | {"n": 2, "k": 0.25} | sym15u / both | 105 | 1790 | -699 | -897 | -558 | 1861 | 1 | 315 |
| session_hl | break_native | pasl_14 | {"n": 2, "k": 0.5} | sym15u / both | 130 | 2714 | -40 | -912 | -606 | 3328 | 2 | 315 |
| session_hl | false_break | dol_2600 | {"M": 3, "k": 0.5} | sym15u / both | 99 | 1706 | -85 | -2017 | -1348 | 2209 | 1 | 315 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 315 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 315 |
| session_hl | reject_native | vrb_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 127 | 1815 | 335 | -612 | -95 | 2394 | 1 | 315 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 315 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 1 | 315 |
| trendline | break | tib_2000 | {"n": 2, "k": 0.25} | sym15u / both | 217 | 3572 | 1307 | -1072 | -804 | 4451 | 1 | 207 |
| trendline | break_native | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 226 | 3203 | -70 | 311 | 652 | 4615 | 1 | 207 |
| trendline | false_break | pasl_28 | {"M": 3, "k": 0.5} | sym15u / both | 231 | 2852 | -904 | 507 | 900 | 2905 | 1 | 207 |
| trendline | false_break_native | pasl_14 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2554 | -1041 | -747 | -251 | 1499 | 2 | 207 |
| trendline | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 207 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 207 |
| trendline | retest | drb_1200 | {"M": 10, "tol": 0.5} | plain60/60 / both | 356 | 3006 | -8 | 473 | 219 | 2382 | 1 | 207 |
| trendline | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym8u / both | 435 | 3422 | -468 | -1462 | 1198 | 3408 | 2 | 207 |
| uw_dp | break | tpo_30m | {"n": 1, "k": 0.0} | sym15u / both | 118 | 2850 | 0 | 0 | -452 | 3235 | 1 | 318 |
| uw_dp | break_native | tpo_30m | {"n": 1, "k": 0.0} | sym15u / both | 118 | 2850 | 0 | 0 | -452 | 3235 | 1 | 318 |
| uw_dp | false_break | entropy_B500 | {"M": 3, "k": 0.5} | sym15u / both | 143 | 3129 | 0 | 0 | -31 | 3967 | 1 | 318 |
| uw_dp | false_break_native | tpo_30m | {"M": 2, "k": 0.5} | sym15u / both | 123 | 3358 | 0 | 0 | -119 | 3632 | 1 | 318 |
| uw_dp | reject | lbrk_4_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2169 | 0 | 0 | -278 | 2211 | 1 | 318 |
| uw_dp | reject_native | sessrng_B050 | {"tol": 1.0, "conf": "body"} | sym15u / both | 112 | 2128 | 0 | 0 | -83 | 1462 | 1 | 318 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 318 |
| uw_dp | retest_native | pasl_14 | {"M": 3, "tol": 0.5} | sym8u / both | 88 | 2611 | 0 | 0 | 319 | 3601 | 2 | 318 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1 | 317 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 317 |
| uw_ndx | false_break | dltor_B500 | {"M": 1, "k": 0.0} | plain60/60 / both | 269 | 3124 | 0 | 812 | 970 | 1097 | 1 | 317 |
| uw_ndx | false_break_native | dltor_B500 | {"M": 3, "k": 0.5} | plain60/60 / both | 267 | 3126 | 0 | 876 | 898 | 1280 | 1 | 317 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 317 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 317 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 317 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 317 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 317 |
| uw_qqq | break_native | renko_20 | {"n": 2, "k": 0.0} | sym8u / both | 145 | 2846 | 0 | 48 | 263 | 2703 | 2 | 317 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 317 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 317 |
| uw_qqq | reject | trend_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 109 | 3288 | 0 | 305 | -1998 | 1890 | 1 | 317 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 317 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 317 |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1 | 317 |
| vwap | break | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 5484 | 276 | -1123 | -2301 | 6752 | 2 | 317 |
| vwap | break_native | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 227 | 5738 | 534 | -1080 | -3184 | 7299 | 2 | 317 |
| vwap | false_break | trb_2000 | {"M": 2, "k": 0.5} | sym15u / both | 181 | 3231 | -238 | -642 | 725 | 1849 | 1 | 317 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 317 |
| vwap | reject | rngor_B050 | {"tol": 0.0, "conf": "close"} | sym15u / both | 207 | 4934 | 712 | -854 | 272 | 4131 | 1 | 317 |
| vwap | reject_native | dltor_B130 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 245 | 6084 | 76 | 61 | 1363 | 7110 | 2 | 317 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 317 |
| vwap | retest_native | vfp_t5m | {"M": 10, "tol": 0.5} | sym15u / both | 208 | 4967 | 40 | 270 | 1512 | 5907 | 1 | 317 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 317 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 317 |
| vwap_bands | false_break | tm15 | {"M": 1, "k": 0.5} | plain60/60 / both | 705 | 3509 | -455 | -467 | -528 | 2159 | 2 | 317 |
| vwap_bands | false_break_native | time_s_15 | {"M": 1, "k": 0.5} | plain60/60 / both | 699 | 3575 | 865 | -1939 | 1029 | 795 | 2 | 317 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 317 |
| vwap_bands | reject_native | tm20 | {"tol": 1.0, "conf": "close"} | sym15u / both | 547 | 4046 | -1550 | -51 | -2596 | 3340 | 2 | 317 |
| vwap_bands | retest | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 210 | 3848 | 316 | 279 | -1912 | 3192 | 1 | 317 |
| vwap_bands | retest_native | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 214 | 3984 | 196 | 78 | -2025 | 3844 | 1 | 317 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 1 | 318 |
| week_month | break_native | swing_atr_0.25 | {"n": 2, "k": 0.25} | sym15u / both | 43 | 1508 | -111 | -183 | -1226 | 1563 | 1 | 318 |
| week_month | false_break | sessrng_B080 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1325 | -269 | 574 | 305 | 503 | 1 | 318 |
| week_month | false_break_native | tpo_30m | {"M": 2, "k": 0.5} | sym15u / both | 53 | 1707 | -123 | 726 | -167 | 1387 | 1 | 318 |
| week_month | reject | tib_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 34 | 1905 | -46 | -393 | -862 | 2501 | 1 | 318 |
| week_month | reject_native | tib_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 42 | 1981 | -30 | -448 | -602 | 2427 | 1 | 318 |
| week_month | retest | sessrng_B130 | {"M": 10, "tol": 0.5} | sym15u / both | 33 | 1234 | 35 | 393 | 1166 | 1610 | 1 | 318 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 1 | 318 |
| zones | break | vib_40000 | {"n": 1, "k": 0.0} | sym15u / both | 111 | 2479 | -298 | 723 | -497 | 2718 | 1 | 317 |
| zones | break_native | swing_pct_8 | {"n": 1, "k": 0.25} | sym8u / both | 179 | 4269 | 914 | 299 | 1497 | 6048 | 2 | 317 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 317 |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 112 | 1825 | -112 | -996 | 314 | 2093 | 2 | 317 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 317 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 317 |
| zones | retest | rngor_B030 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2481 | -216 | -1079 | 670 | 2117 | 1 | 317 |
| zones | retest_native | rngor_B030 | {"M": 10, "tol": 0.5} | sym15u / both | 131 | 2426 | -424 | 61 | 1307 | 2239 | 1 | 317 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd15 | reject | volor_B500 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 36 | 182 | 177 | -385 | -356 | 171 | 1 | 327 |
| sd15 | reject_flow | vfp_rng16 | {"F": 2, "D": 15} | plain60/60 / both | 31 | 210 | -35 | -333 | -45 | 266 | 1 | 327 |
| sd15 | reject_flow_native | vfp_rng16 | {"F": 2, "D": 15} | plain60/60 / both | 31 | 210 | -35 | -333 | -45 | 266 | 1 | 327 |
| sd15 | reject_native | volor_B500 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 36 | 182 | 177 | -385 | -356 | 171 | 1 | 327 |
| sd5 | break | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 327 |
| sd5 | break_native | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 327 |
| sd5 | reject | dib_1200 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 32 | 978 | 63 | -174 | -560 | 1085 | 1 | 327 |
| sd5 | reject_flow | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 327 |
| sd5 | reject_flow_native | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 327 |
| sd5 | reject_native | dib_1200 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 32 | 978 | 63 | -174 | -560 | 1085 | 1 | 327 |
| sd5 | retest | tib_240 | {"M": 6, "tol": 0.0} | sym15u / both | 30 | -216 | 58 | 23 | 278 | -447 | 1 | 327 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 1 | 327 |
| sdx15 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 171 | 2399 | -85 | 715 | 2594 | 3384 | 1 | 326 |
| sdx15 | lim_mid | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 333 | 2976 | -2286 | -2403 | -427 | 2983 | 1 | 326 |
| sdx15 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 373 | 3815 | 30 | -593 | -1777 | 5127 | 1 | 326 |
| sdx15 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 68 | 2107 | -1412 | -869 | 341 | 1563 | 1 | 326 |
| sdx15 | rej_flow | vrb_400 | {"d": "A", "F": 0} | sym15u / both | 74 | 1289 | -104 | 202 | -1621 | 805 | 1 | 326 |
| sdx15 | rej_native | kagi_56 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 2039 | -160 | -2368 | -1749 | 2557 | 1 | 326 |
| sdx15 | rej_zone | trend_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 167 | 4203 | -2089 | -2089 | -1211 | 2114 | 1 | 326 |
| sdx15 | retest | vrb_15000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 59 | 1800 | 436 | 786 | 2832 | 1896 | 1 | 326 |
| sdx3 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 350 | 3483 | 1458 | 3578 | 5139 | 4750 | 1 | 326 |
| sdx3 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 182 | 3365 | 26 | 2134 | 1935 | 3244 | 1 | 326 |
| sdx3 | lim_prox | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 224 | 3509 | 1324 | 128 | -1502 | 4960 | 1 | 326 |
| sdx3 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 475 | 3002 | -2715 | -1978 | -5508 | 1958 | 1 | 326 |
| sdx3 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / long | 156 | 3037 | 6 | 1057 | -3441 | 2950 | 1 | 326 |
| sdx3 | rej_native | vrb_400 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 1183 | 2943 | -2282 | -4825 | -8101 | 4300 | 1 | 326 |
| sdx3 | rej_zone | pasl_10 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 542 | 3335 | -1472 | -1840 | -3991 | 3170 | 1 | 326 |
| sdx3 | retest | kagi_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 245 | 2392 | 2042 | 2685 | 4969 | 3185 | 1 | 326 |
| sdx30 | break | pnf_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 79 | 1933 | -372 | 1333 | 866 | 1755 | 1 | 327 |
| sdx30 | lim_mid | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 52 | 1565 | 12 | -897 | 111 | 634 | 1 | 327 |
| sdx30 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 142 | 2308 | -245 | -373 | 1505 | 5248 | 1 | 327 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 73 | 1261 | -467 | -838 | -1738 | 1427 | 1 | 327 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 146 | 1480 | -676 | -2116 | -2930 | 1823 | 1 | 327 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 327 |
| sdx30 | rej_zone | pasl_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / long | 88 | 2061 | 108 | -188 | -665 | 2504 | 1 | 327 |
| sdx30 | retest | pnf_28 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 35 | 976 | -101 | -1016 | 521 | 952 | 1 | 327 |
| sdx5 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 128 | 2348 | 760 | 872 | 1375 | 1924 | 1 | 326 |
| sdx5 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 4263 | -912 | -271 | 1146 | 4807 | 1 | 326 |
| sdx5 | lim_prox | urenko_80 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 214 | 4370 | 1480 | 714 | 2473 | 2468 | 1 | 326 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 216 | 2627 | -830 | 131 | -3477 | 4401 | 1 | 326 |
| sdx5 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / both | 258 | 1062 | -1205 | -898 | -1943 | 1771 | 1 | 326 |
| sdx5 | rej_native | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 326 |
| sdx5 | rej_zone | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 326 |
| sdx5 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 165 | 2309 | 1186 | -216 | 3671 | 2698 | 1 | 326 |
| sdx60 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 52 | 1464 | 466 | 334 | 762 | 926 | 1 | 326 |
| sdx60 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 417 | 1570 | -1168 | -222 | -1705 | 689 | 1 | 326 |
| sdx60 | lim_prox | sessrng_B130 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 157 | 1699 | -814 | 147 | -53 | 1682 | 1 | 326 |
| sdx60 | rej | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 124 | 2540 | -595 | -1785 | -237 | 2453 | 1 | 326 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / long | 90 | 1309 | 89 | -465 | -399 | 884 | 1 | 326 |
| sdx60 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 326 |
| sdx60 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 326 |
| sdx_renko28 | break | wrenko_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 339 | 2291 | 953 | -446 | 6066 | 2557 | 1 | 325 |
| sdx_renko28 | lim_mid | kagi_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 475 | 4203 | 121 | -178 | 3832 | 2308 | 1 | 325 |
| sdx_renko28 | lim_prox | pnf_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 264 | 3229 | 883 | -1326 | -486 | 1723 | 1 | 325 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 417 | 2601 | -2519 | -2626 | -4344 | 2070 | 1 | 325 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 202 | 2765 | 740 | -3083 | 894 | 2859 | 1 | 325 |
| sdx_renko28 | rej_native | urenko_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 325 |
| sdx_renko28 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 325 |
| sdx_renko28 | retest | pnf_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 288 | 2991 | 1782 | 2559 | 1355 | 2869 | 1 | 325 |
| sdx_rng28 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 480 | 4135 | -249 | -747 | 7833 | 6261 | 1 | 325 |
| sdx_rng28 | lim_mid | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1515 | 4008 | -446 | -1587 | -7328 | 4734 | 1 | 325 |
| sdx_rng28 | lim_prox | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 493 | 5342 | 520 | 1267 | -40 | 7530 | 1 | 325 |
| sdx_rng28 | rej | mrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 504 | 2856 | -984 | -1842 | -5463 | 2791 | 1 | 325 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / long | 172 | 2052 | 2014 | -466 | -281 | 3800 | 1 | 325 |
| sdx_rng28 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 431 | 3332 | 1328 | -4047 | 1358 | 3443 | 1 | 325 |
| sdx_rng28 | rej_zone | frenko_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4594 | 559 | -3692 | -3237 | 3340 | 1 | 325 |
| sdx_rng28 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 449 | 3491 | -1168 | 3003 | 5388 | 3398 | 1 | 325 |
| sdx_vol1100 | break | lbrk_3_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 599 | 2954 | -817 | 879 | 1581 | 2600 | 1 | 325 |
| sdx_vol1100 | lim_mid | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1444 | 5146 | -307 | -267 | -7260 | 5686 | 1 | 325 |
| sdx_vol1100 | lim_prox | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1412 | 4616 | 1989 | -3 | -5487 | 5378 | 1 | 325 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 429 | 5058 | -1453 | -1789 | -1589 | 7224 | 1 | 325 |
| sdx_vol1100 | rej_flow | vrb_700 | {"d": "E", "F": 0} | sym15u / both | 321 | 2969 | -6 | 1488 | -104 | 2957 | 1 | 325 |
| sdx_vol1100 | rej_native | kagi_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 477 | 3771 | -172 | -664 | -3831 | 5515 | 1 | 325 |
| sdx_vol1100 | rej_zone | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4710 | -906 | -898 | -3639 | 4361 | 1 | 325 |
| sdx_vol1100 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 398 | 4494 | -381 | -1960 | 2674 | 5777 | 1 | 325 |
| fib15 | break | dchg_20 | {"n": 1, "k": 0.0} | sym15u / both | 346 | 3526 | 555 | 2339 | 3572 | 2098 | 1 | 326 |
| fib15 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 309 | 3889 | 1224 | -1144 | 3109 | 4406 | 1 | 326 |
| fib15 | false_break | pnf_5 | {"M": 1, "k": 0.5} | asym20u/10u / both | 369 | 4016 | 565 | 3166 | 2420 | 3650 | 2 | 326 |
| fib15 | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | asym20u/10u / both | 372 | 3672 | 357 | 2841 | 4060 | 3234 | 2 | 326 |
| fib15 | pullback | pnf_5 | {"tol": 1.0, "conf": "close"} | sym8u / both | 264 | 2932 | 963 | -352 | 854 | 2872 | 2 | 326 |
| fib15 | pullback_native | vrb_1200 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 257 | 2897 | 1005 | -414 | -2028 | 3600 | 2 | 326 |
| fib15 | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 361 | 4272 | -1022 | 147 | 2523 | 4051 | 1 | 326 |
| fib15 | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 361 | 5051 | 722 | -694 | 2601 | 3935 | 1 | 326 |
| fib15 | retest | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 326 |
| fib15 | retest_native | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 326 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 392 | 4876 | -635 | -1541 | 2534 | 5721 | 1 | 327 |
| fib5 | break_native | tsf_5_100 | {"n": 2, "k": 0.25} | sym15u / both | 365 | 4292 | 745 | -2450 | 1424 | 1265 | 1 | 327 |
| fib5 | false_break | rng_28 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 5122 | 509 | -759 | 2913 | 3226 | 1 | 327 |
| fib5 | false_break_native | rng_28 | {"M": 2, "k": 0.5} | sym15u / both | 386 | 5486 | 100 | -1323 | 1351 | 3593 | 1 | 327 |
| fib5 | pullback | pnf_7 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 267 | 2842 | -178 | -563 | -1999 | 5780 | 2 | 327 |
| fib5 | pullback_native | dlt_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 351 | 3050 | -717 | -1303 | -243 | 5196 | 1 | 327 |
| fib5 | reject | vrb_1200 | {"tol": 0.0, "conf": "body"} | sym8u / both | 375 | 4520 | -365 | -1515 | 620 | 5572 | 2 | 327 |
| fib5 | reject_native | vrb_1200 | {"tol": 0.0, "conf": "body"} | sym8u / both | 375 | 4520 | -365 | -1515 | 620 | 5572 | 2 | 327 |
| fib5 | retest | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 327 |
| fib5 | retest_native | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 327 |
| fib60 | break | vnorm_150 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 4746 | 195 | 2278 | 58 | 4400 | 1 | 327 |
| fib60 | break_native | dlt_45 | {"n": 3, "k": 0.5} | sym15u / both | 318 | 5222 | -1532 | -573 | 828 | 5732 | 1 | 327 |
| fib60 | false_break | vnorm_250 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4788 | 651 | 49 | 1652 | 3843 | 1 | 327 |
| fib60 | false_break_native | swing_pct_8 | {"M": 2, "k": 0.5} | sym15u / both | 308 | 4583 | 2331 | 2922 | 2124 | 5925 | 1 | 327 |
| fib60 | pullback | tsf_5_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 2509 | -224 | 1972 | -1446 | 1514 | 1 | 327 |
| fib60 | pullback_native | tick_5000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 2539 | -702 | 2326 | 50 | 1531 | 1 | 327 |
| fib60 | reject | tick_300 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 4010 | -1870 | -1434 | 2221 | 3583 | 1 | 327 |
| fib60 | reject_native | dib_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 303 | 4392 | 0 | -661 | -328 | 4902 | 1 | 327 |
| fib60 | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 272 | 4507 | 25 | 415 | -3066 | 4468 | 1 | 327 |
| fib60 | retest_native | renko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 4745 | 238 | -75 | 4108 | 2780 | 1 | 327 |
| fibr_dev | break | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 417 | 4933 | -349 | 802 | 2045 | 5492 | 1 | 217 |
| fibr_dev | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 417 | 4933 | -349 | 802 | 2045 | 5492 | 1 | 217 |
| fibr_dev | false_break | pasl_28 | {"M": 3, "k": 0.0} | sym8u / both | 411 | 6011 | 2568 | -1293 | 7299 | 3506 | 2 | 217 |
| fibr_dev | false_break_native | pasl_28 | {"M": 3, "k": 0.0} | sym8u / both | 411 | 6011 | 2568 | -1293 | 7299 | 3506 | 2 | 217 |
| fibr_dev | reject | tsf_5_200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 406 | 3910 | 1893 | 3558 | 1641 | 2058 | 1 | 217 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 448 | 4974 | 1168 | 2667 | 817 | 4931 | 1 | 217 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym8u / both | 425 | 6500 | -433 | 1223 | 3603 | 6424 | 2 | 217 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym8u / both | 447 | 5298 | -654 | -1569 | 5048 | 6345 | 2 | 217 |
| fibr_ib | break | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 292 | 4439 | -707 | -865 | -1300 | 4236 | 1 | 215 |
| fibr_ib | break_native | entropy_B080 | {"n": 1, "k": 0.0} | sym15u / both | 292 | 4439 | -707 | -865 | -1300 | 4236 | 1 | 215 |
| fibr_ib | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 215 |
| fibr_ib | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 215 |
| fibr_ib | reject | tib_700 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 805 | 4356 | 127 | -2646 | -2461 | 4723 | 1 | 215 |
| fibr_ib | reject_native | tib_700 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 805 | 4356 | 127 | -2646 | -2461 | 4723 | 1 | 215 |
| fibr_ib | retest | anch_R0830_B25 | {"M": 6, "tol": 0.5} | sym15u / both | 202 | 3484 | 934 | -1580 | 1874 | 3228 | 1 | 215 |
| fibr_ib | retest_native | time_s_5 | {"M": 3, "tol": 0.0} | sym15u / both | 392 | 3301 | 622 | 588 | 414 | 3677 | 1 | 215 |
| fibr_on | break | dol_1100 | {"n": 2, "k": 0.25} | sym15u / both | 378 | 4421 | 587 | 341 | 5542 | 5217 | 1 | 217 |
| fibr_on | break_native | dchg_20 | {"n": 3, "k": 0.5} | sym15u / both | 414 | 4798 | 1613 | 377 | 7176 | 7335 | 1 | 217 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 383 | 5252 | 1464 | 1013 | 2918 | 7973 | 1 | 217 |
| fibr_on | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 1 | 217 |
| fibr_on | reject | dol_2600 | {"tol": 0.5, "conf": "body"} | sym15u / both | 359 | 5962 | -130 | 1420 | -849 | 7214 | 1 | 217 |
| fibr_on | reject_native | tsf_5_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 372 | 4487 | 1300 | -4169 | 1376 | 3449 | 1 | 217 |
| fibr_on | retest | vib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 371 | 6895 | 468 | 685 | 1681 | 6510 | 1 | 217 |
| fibr_on | retest_native | dib_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 421 | 5382 | 313 | -1869 | 4373 | 5259 | 1 | 217 |
| fibr_or | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 213 |
| fibr_or | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 213 |
| fibr_or | false_break | dltor_B050 | {"M": 2, "k": 0.5} | sym15u / both | 325 | 5278 | 538 | 1649 | 424 | 5582 | 1 | 213 |
| fibr_or | false_break_native | tib_6000 | {"M": 2, "k": 0.5} | sym15u / both | 354 | 5941 | -286 | 3902 | -1175 | 4149 | 1 | 213 |
| fibr_or | reject | vib_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 343 | 4621 | -917 | 906 | -1102 | 4797 | 1 | 213 |
| fibr_or | reject_native | vib_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 343 | 4621 | -917 | 906 | -1102 | 4797 | 1 | 213 |
| fibr_or | retest | vsess_600 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 375 | 6822 | 26 | -2127 | 3125 | 7665 | 2 | 213 |
| fibr_or | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | asym10u/20u / both | 374 | 6648 | 711 | -1838 | 3287 | 6878 | 2 | 213 |
| fibr_pd | break | dchg_20 | {"n": 3, "k": 0.5} | sym15u / both | 363 | 6038 | -978 | 1126 | 3400 | 6256 | 1 | 214 |
| fibr_pd | break_native | dchg_20 | {"n": 2, "k": 0.25} | sym15u / both | 365 | 5429 | -676 | 163 | 2305 | 6847 | 1 | 214 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 1 | 214 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 1 | 214 |
| fibr_pd | reject | tick_2000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 358 | 5740 | -667 | -122 | 1156 | 7825 | 2 | 214 |
| fibr_pd | reject_native | dol_4000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 401 | 6885 | 992 | -343 | 3378 | 7753 | 1 | 214 |
| fibr_pd | retest | dol_2600 | {"M": 3, "tol": 0.0} | sym15u / both | 267 | 5294 | 577 | -278 | 2050 | 4217 | 1 | 214 |
| fibr_pd | retest_native | dol_2600 | {"M": 3, "tol": 0.0} | sym15u / both | 267 | 5294 | 577 | -278 | 2050 | 4217 | 1 | 214 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 357 | 5210 | 1949 | 420 | -2741 | 6204 | 1 | 216 |
| piv_cama | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym8u / both | 394 | 6591 | 632 | 469 | 1785 | 6329 | 2 | 216 |
| piv_cama | false_break | dib_2000 | {"M": 1, "k": 0.5} | asym15u/30u / both | 384 | 3255 | -948 | 2360 | 3357 | 1776 | 2 | 216 |
| piv_cama | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 187 | 3276 | 454 | 729 | 1972 | 3605 | 1 | 216 |
| piv_cama | reject | vib_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 469 | 8327 | 252 | 754 | 109 | 4800 | 1 | 216 |
| piv_cama | reject_native | vib_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 469 | 8327 | 252 | 754 | 109 | 4800 | 1 | 216 |
| piv_cama | retest | dib_2000 | {"M": 6, "tol": 0.0} | asym15u/30u / both | 374 | 4845 | -1036 | -505 | 2780 | 1607 | 2 | 216 |
| piv_cama | retest_native | dib_2000 | {"M": 6, "tol": 0.0} | asym15u/30u / both | 374 | 4845 | -1036 | -505 | 2780 | 1607 | 2 | 216 |
| piv_floor | break | tsf_2_2000 | {"n": 3, "k": 0.5} | sym15u / both | 317 | 4227 | 995 | -1336 | 1773 | 4902 | 1 | 214 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 2 | 214 |
| piv_floor | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 186 | 3796 | -476 | 286 | 3151 | 3316 | 2 | 214 |
| piv_floor | false_break_native | kagi_40 | {"M": 3, "k": 0.5} | sym15u / both | 377 | 4160 | 1164 | 1611 | 1824 | 5277 | 1 | 214 |
| piv_floor | reject | vrb_15000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 245 | 3194 | -1531 | -134 | -309 | 2743 | 1 | 214 |
| piv_floor | reject_native | rngor_B080 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 950 | 3419 | 667 | 3144 | -446 | 3042 | 1 | 214 |
| piv_floor | retest | tib_10000 | {"M": 6, "tol": 0.5} | sym15u / both | 291 | 4485 | 1649 | 989 | 2127 | 4087 | 1 | 214 |
| piv_floor | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym8u / both | 151 | 3913 | 1673 | 239 | 2389 | 4656 | 2 | 214 |
| piv_wf | break | pnf_5 | {"n": 3, "k": 0.25} | asym20u/10u / both | 383 | 4258 | -1663 | 256 | 2523 | 4896 | 2 | 215 |
| piv_wf | break_native | tsf_5_200 | {"n": 3, "k": 0.5} | sym15u / both | 354 | 5333 | 64 | -2615 | 1177 | 6384 | 1 | 215 |
| piv_wf | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 3750 | 2632 | 2336 | 1588 | 3570 | 1 | 215 |
| piv_wf | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | sym8u / both | 468 | 3749 | 1668 | -472 | 3895 | 2961 | 2 | 215 |
| piv_wf | reject | vrb_1200 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 324 | 3485 | 856 | 946 | -450 | 881 | 2 | 215 |
| piv_wf | reject_native | dol_4000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 394 | 4207 | 250 | -257 | 197 | 4626 | 1 | 215 |
| piv_wf | retest | cusum_40 | {"M": 6, "tol": 0.5} | sym15u / both | 322 | 6154 | -169 | 1020 | 879 | 6130 | 1 | 215 |
| piv_wf | retest_native | sessrng_B130 | {"M": 3, "tol": 0.0} | plain60/60 / both | 555 | 5123 | 201 | 873 | 2419 | 3059 | 1 | 215 |
| swcluster | break | rng_10 | {"n": 2, "k": 0.25} | asym20u/10u / both | 116 | 1617 | -55 | -1127 | -1451 | 380 | 2 | 217 |
| swcluster | break_native | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 103 | 1934 | -1417 | 119 | -467 | 1021 | 1 | 217 |
| swcluster | false_break | pnf_40 | {"M": 1, "k": 0.0} | sym15u / both | 93 | 1551 | -519 | -769 | 385 | 1862 | 1 | 217 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 1 | 217 |
| swcluster | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym30u / both | 85 | 1803 | -240 | 498 | -1243 | 857 | 2 | 217 |
| swcluster | reject_native | vsess_600 | {"tol": 0.0, "conf": "body"} | sym30u / both | 85 | 1803 | -240 | 498 | -1243 | 857 | 2 | 217 |
| swcluster | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 62 | 1657 | -160 | 686 | -693 | 1956 | 1 | 217 |
| swcluster | retest_native | swing_atr_0.15 | {"M": 10, "tol": 0.5} | sym15u / both | 86 | 1888 | -1192 | 24 | -629 | 1495 | 1 | 217 |
| swsr15 | break | vnorm_250 | {"n": 1, "k": 0.0} | sym15u / both | 316 | 3811 | 886 | 1067 | 2985 | 87 | 1 | 216 |
| swsr15 | break_native | pnf_5 | {"n": 3, "k": 0.5} | asym15u/30u / both | 347 | 3818 | 1195 | 3009 | 3723 | 6639 | 2 | 216 |
| swsr15 | false_break | cusum_10 | {"M": 1, "k": 0.0} | sym15u / both | 444 | 5176 | 1090 | 2009 | 831 | 4774 | 1 | 216 |
| swsr15 | false_break_native | cusum_10 | {"M": 1, "k": 0.0} | sym15u / both | 444 | 5176 | 1090 | 2009 | 831 | 4774 | 1 | 216 |
| swsr15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 328 | 3874 | -2044 | -176 | -1129 | 4458 | 1 | 216 |
| swsr15 | reject_native | drb_2000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 378 | 3847 | -1674 | 1422 | -1815 | 5525 | 1 | 216 |
| swsr15 | retest | vfp_vol1000 | {"M": 10, "tol": 0.5} | sym15u / both | 313 | 5139 | -340 | 414 | 2372 | 4377 | 1 | 216 |
| swsr15 | retest_native | urenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 333 | 4907 | 1503 | -111 | 2647 | 3519 | 1 | 216 |
| swsr5 | break | dchg_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5687 | 883 | -668 | -1576 | 4634 | 2 | 218 |
| swsr5 | break_native | dchg_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5687 | 883 | -668 | -1576 | 4634 | 2 | 218 |
| swsr5 | false_break | dchg_28 | {"M": 1, "k": 0.5} | sym8u / both | 442 | 5680 | 480 | -1094 | -1798 | 5181 | 2 | 218 |
| swsr5 | false_break_native | dchg_28 | {"M": 2, "k": 0.5} | sym8u / both | 432 | 8191 | 1106 | -2029 | 689 | 8585 | 2 | 218 |
| swsr5 | reject | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 390 | 4483 | 1577 | -1581 | -937 | 4245 | 1 | 218 |
| swsr5 | reject_native | drb_2000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 432 | 4873 | -387 | 1582 | 3386 | 4026 | 1 | 218 |
| swsr5 | retest | vnorm_250 | {"M": 3, "tol": 0.0} | sym15u / both | 294 | 4911 | -50 | 2393 | -2185 | 3590 | 1 | 218 |
| swsr5 | retest_native | vnorm_250 | {"M": 3, "tol": 0.0} | sym15u / both | 294 | 4911 | -50 | 2393 | -2185 | 3590 | 1 | 218 |
| swsr60 | break | dltor_B080 | {"n": 3, "k": 0.5} | sym15u / both | 246 | 5404 | -1599 | -1913 | 1151 | 4471 | 1 | 216 |
| swsr60 | break_native | tsf_5_100 | {"n": 2, "k": 0.25} | sym15u / both | 264 | 5009 | -1528 | 305 | -759 | 2393 | 1 | 216 |
| swsr60 | false_break | time_s_45 | {"M": 1, "k": 0.0} | sym15u / both | 259 | 3002 | 1728 | 656 | 1781 | 1208 | 1 | 216 |
| swsr60 | false_break_native | tib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 281 | 3439 | -522 | -1505 | 2146 | 4113 | 1 | 216 |
| swsr60 | reject | dol_4000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 211 | 3868 | -1179 | 954 | -1143 | 1551 | 1 | 216 |
| swsr60 | reject_native | cusum_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 279 | 3423 | -126 | -480 | -2780 | -46 | 1 | 216 |
| swsr60 | retest | cusum_40 | {"M": 10, "tol": 0.5} | sym15u / both | 241 | 5728 | 497 | 26 | -245 | 7311 | 1 | 216 |
| swsr60 | retest_native | vnorm_250 | {"M": 10, "tol": 0.5} | sym15u / both | 248 | 4732 | 858 | -183 | 2065 | 2118 | 1 | 216 |
| stack | break | time_s_45 | {"k": 2, "cw": 0.5} | sym15u / both | 306 | 4379 | 480 | -339 | -64 | 4857 | 1 | 325 |
| stack | break_native | tick_300 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 429 | 5686 | -727 | 673 | 3693 | 2741 | 2 | 325 |
| stack | reject | tick_800 | {"k": 2, "cw": 2.0} | sym15u / both | 391 | 3903 | -996 | -1425 | 1988 | 3829 | 2 | 325 |
| stack | reject_native | trb_240 | {"k": 2, "cw": 0.5} | sym15u / both | 484 | 4685 | 556 | -66 | -3505 | 5213 | 1 | 325 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 327 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1335 | -822 | 539 | 550 | 1717 | 1 | 327 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 327 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 327 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 327 |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 126 | 1601 | -738 | -637 | 518 | 1605 | 1 | 327 |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1266 | -894 | 749 | 1751 | 1947 | 1 | 327 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 327 |
| channel | break | dol_1100 | {"n": 1, "k": 0.0} | sym15u / both | 408 | 5392 | 377 | 2559 | 4340 | 2433 | 1 | 220 |
| channel | break_native | dol_1100 | {"n": 1, "k": 0.0} | sym15u / both | 408 | 5392 | 377 | 2559 | 4340 | 2433 | 1 | 220 |
| channel | false_break | dol_1100 | {"M": 1, "k": 0.0} | sym15u / both | 408 | 5126 | 775 | 2752 | 3733 | 3007 | 1 | 220 |
| channel | false_break_native | dol_1100 | {"M": 1, "k": 0.0} | sym15u / both | 408 | 5126 | 775 | 2752 | 3733 | 3007 | 1 | 220 |
| channel | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 1127 | 4027 | 2194 | -2323 | -1894 | 1091 | 1 | 220 |
| channel | reject_native | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 440 | 4572 | 1255 | 143 | 2266 | 7564 | 1 | 220 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 527 | 5168 | 1396 | -726 | 235 | 2951 | 1 | 220 |
| channel | retest_native | dchg_20 | {"M": 10, "tol": 0.5} | sym15u / both | 420 | 6423 | 1980 | 2728 | 3732 | 6353 | 1 | 220 |
| fvg15 | break | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 330 | -695 | 1898 | 2097 | 1 | 219 |
| fvg15 | break_native | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 408 | -695 | 1898 | 2097 | 1 | 219 |
| fvg15 | false_break | cusum_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2164 | -198 | -1519 | -1692 | -669 | 1 | 219 |
| fvg15 | false_break_native | rng_10 | {"M": 2, "k": 0.5} | sym30u / both | 173 | 2428 | -372 | -857 | -1389 | 573 | 2 | 219 |
| fvg15 | reject | time_m_1 | {"tol": 0.5, "conf": "body"} | sym15u / both | 152 | 2592 | 227 | 1406 | 1791 | 2160 | 1 | 219 |
| fvg15 | reject_native | dltor_B200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 174 | 2179 | -391 | -645 | 286 | 2088 | 1 | 219 |
| fvg15 | retest | vrb_1200 | {"M": 10, "tol": 0.0} | sym15u / both | 156 | 3753 | 530 | -71 | -1029 | 4108 | 2 | 219 |
| fvg15 | retest_native | vrb_1200 | {"M": 10, "tol": 0.0} | sym15u / both | 156 | 3753 | 530 | -71 | -1029 | 4108 | 2 | 219 |
| fvg5 | break | pasl_28 | {"n": 2, "k": 0.25} | sym8u / both | 170 | 3495 | 1867 | 1203 | 3141 | 2967 | 2 | 216 |
| fvg5 | break_native | pasl_28 | {"n": 2, "k": 0.0} | sym8u / both | 171 | 3227 | 1295 | 2184 | 2774 | 2661 | 2 | 216 |
| fvg5 | false_break | pasl_28 | {"M": 1, "k": 0.0} | sym8u / long | 104 | 2322 | 434 | 200 | -232 | 2472 | 2 | 216 |
| fvg5 | false_break_native | pasl_28 | {"M": 1, "k": 0.0} | sym8u / long | 104 | 2322 | 434 | 200 | -232 | 2472 | 2 | 216 |
| fvg5 | reject | tm1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 127 | 2695 | 1075 | -645 | 767 | 2352 | 1 | 216 |
| fvg5 | reject_native | tm1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 127 | 2695 | 1075 | -645 | 767 | 2352 | 1 | 216 |
| fvg5 | retest | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 222 | 3806 | -1035 | -262 | -445 | 2561 | 1 | 216 |
| fvg5 | retest_native | dol_2600 | {"M": 10, "tol": 0.5} | sym15u / both | 231 | 2689 | -115 | -494 | 801 | 2553 | 1 | 216 |
| gaps | break | vsess_600 | {"n": 2, "k": 0.5} | plain60/60 / both | 472 | 3102 | -161 | -930 | -533 | 3972 | 2 | 327 |
| gaps | break_native | vsess_600 | {"n": 2, "k": 0.25} | plain60/60 / both | 472 | 3782 | 294 | 168 | 135 | 4630 | 2 | 327 |
| gaps | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 271 | 3346 | 166 | 1506 | 60 | 2315 | 2 | 327 |
| gaps | false_break_native | vol_350 | {"M": 1, "k": 0.5} | asym20u/10u / both | 210 | 3204 | -597 | -1103 | 83 | 3216 | 2 | 327 |
| gaps | reject | mom_20 | {"tol": 0.0, "conf": "close"} | sym8u / both | 206 | 3721 | -510 | -2611 | -2607 | 2843 | 2 | 327 |
| gaps | reject_native | mom_20 | {"tol": 0.0, "conf": "close"} | sym8u / both | 206 | 3721 | -510 | -2611 | -2607 | 2843 | 2 | 327 |
| gaps | retest | tsf_10_400 | {"M": 6, "tol": 0.5} | sym15u / both | 137 | 3056 | -366 | 789 | -925 | 3279 | 1 | 327 |
| gaps | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 221 | 3004 | 496 | -2177 | 458 | 3709 | 1 | 327 |
| mmove | break | vib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 315 | 3567 | 2226 | -780 | 5580 | 1460 | 1 | 220 |
| mmove | break_native | tsf_2_200 | {"n": 2, "k": 0.25} | sym15u / both | 329 | 3608 | 188 | -2832 | 4053 | 1480 | 1 | 220 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 1 | 220 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 1 | 220 |
| mmove | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym30u / long | 92 | 2897 | 890 | 323 | 1859 | 3238 | 2 | 220 |
| mmove | reject_native | tick_2000 | {"tol": 1.0, "conf": "close"} | sym8u / both | 390 | 4339 | 1350 | 260 | -1932 | 4624 | 2 | 220 |
| mmove | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 329 | 3092 | 1424 | 140 | 3397 | 3171 | 1 | 220 |
| mmove | retest_native | vib_40000 | {"M": 10, "tol": 0.5} | sym15u / long | 155 | 3212 | 437 | 1771 | 1280 | 4489 | 1 | 220 |
| ob15 | break | vsess_600 | {"n": 2, "k": 0.0} | asym15u/30u / both | 131 | 3654 | 942 | -28 | -992 | 2441 | 2 | 219 |
| ob15 | break_native | vsess_600 | {"n": 2, "k": 0.0} | asym15u/30u / both | 131 | 3654 | 942 | -28 | -992 | 2441 | 2 | 219 |
| ob15 | false_break | vol_1100 | {"M": 1, "k": 0.5} | sym8u / both | 121 | 3516 | -735 | -19 | 1507 | 2501 | 2 | 219 |
| ob15 | false_break_native | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 129 | 2492 | 346 | -737 | 1315 | 1684 | 1 | 219 |
| ob15 | reject | tm10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2793 | -283 | -769 | -2386 | 2573 | 1 | 219 |
| ob15 | reject_native | vsess_600 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 140 | 2541 | 249 | -1340 | -201 | 2194 | 2 | 219 |
| ob15 | retest | vsess_600 | {"M": 10, "tol": 0.5} | sym8u / both | 144 | 3002 | -554 | -409 | 182 | 2874 | 2 | 219 |
| ob15 | retest_native | time_s_5 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 3275 | 213 | -367 | -83 | 2869 | 1 | 219 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 220 |
| ob5 | break_native | lbrk_3_10 | {"n": 1, "k": 0.5} | sym15u / both | 169 | 3478 | -143 | -1008 | 1362 | 2120 | 2 | 220 |
| ob5 | false_break | rng_10 | {"M": 2, "k": 0.5} | asym20u/10u / both | 194 | 2839 | 267 | -262 | -7 | 1793 | 2 | 220 |
| ob5 | false_break_native | rng_10 | {"M": 2, "k": 0.5} | asym20u/10u / both | 194 | 2920 | 589 | -536 | 2 | 1731 | 2 | 220 |
| ob5 | reject | tsf_2_200 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 2770 | -252 | 383 | -372 | 3347 | 1 | 220 |
| ob5 | reject_native | anch_R0830_B25 | {"tol": 0.5, "conf": "body"} | sym15u / both | 145 | 2594 | -654 | 574 | 1475 | 3041 | 1 | 220 |
| ob5 | retest | trb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 4010 | -1026 | 1294 | -321 | 5598 | 1 | 220 |
| ob5 | retest_native | trb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 4010 | -1026 | 1294 | -321 | 5598 | 1 | 220 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 324 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 324 |
| open_range | false_break | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 435 | 2425 | 23 | -145 | -730 | 1542 | 2 | 324 |
| open_range | false_break_native | renko_20 | {"M": 1, "k": 0.5} | sym8u / both | 420 | 2670 | 231 | -183 | -1477 | 2468 | 2 | 324 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 324 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 324 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 324 |
| open_range | retest_native | dol_1700 | {"M": 10, "tol": 0.5} | sym15u / both | 396 | 4464 | 1014 | 1428 | -3237 | 2332 | 1 | 324 |
| opens | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 360 | 5490 | -643 | 803 | 229 | 6745 | 1 | 326 |
| opens | break_native | vsess_600 | {"n": 1, "k": 0.25} | sym30u / both | 353 | 6071 | 649 | 200 | 2660 | 6158 | 2 | 326 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 168 | 4705 | -649 | -420 | 1329 | 4754 | 1 | 326 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 1 | 326 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 349 | 5699 | -312 | 1439 | -2592 | 3753 | 2 | 326 |
| opens | reject_native | trb_400 | {"tol": 0.0, "conf": "close"} | sym15u / both | 344 | 5546 | -263 | 563 | 1910 | 8183 | 1 | 326 |
| opens | retest | vnorm_1500 | {"M": 3, "tol": 0.0} | sym15u / both | 292 | 5037 | -961 | 1561 | -339 | 4486 | 1 | 326 |
| opens | retest_native | vnorm_1500 | {"M": 3, "tol": 0.0} | sym15u / both | 292 | 5037 | -961 | 1561 | -339 | 4486 | 1 | 326 |
| prior_day | break | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 327 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 327 |
| prior_day | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 6120 | 1169 | 654 | 6266 | 6027 | 1 | 327 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 1 | 327 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 327 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 327 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 327 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 327 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 326 |
| profile_nodes | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 277 | 3995 | 2467 | -1651 | 1370 | 3940 | 1 | 326 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 326 |
| profile_nodes | false_break_native | cusum_40 | {"M": 1, "k": 0.5} | sym8u / both | 224 | 4514 | -1520 | 711 | -645 | 4653 | 2 | 326 |
| profile_nodes | reject | renko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 483 | 3360 | 110 | -1175 | 115 | 1930 | 2 | 326 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 326 |
| profile_nodes | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 326 |
| profile_nodes | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 326 |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 2 | 327 |
| profile_va | break_native | time_s_20 | {"n": 1, "k": 0.5} | asym15u/30u / both | 222 | 4214 | -228 | -1285 | 1598 | 2830 | 2 | 327 |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 198 | 3091 | 543 | 151 | 2346 | 3855 | 2 | 327 |
| profile_va | false_break_native | vrb_15000 | {"M": 3, "k": 0.5} | sym15u / both | 136 | 3168 | 1599 | 897 | 751 | 4360 | 1 | 327 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 1 | 327 |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 263 | 4791 | -360 | 58 | 2424 | 3455 | 1 | 327 |
| profile_va | retest | volor_B500 | {"M": 6, "tol": 0.5} | sym15u / both | 219 | 3728 | -176 | 1986 | 876 | 4478 | 1 | 327 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 327 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 431 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 431 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 431 |
| round | false_break_native | dib_3500 | {"M": 1, "k": 0.5} | asym20u/10u / both | 579 | 7357 | -777 | -1171 | -5154 | 8350 | 2 | 431 |
| round | reject | renko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 657 | 8023 | -600 | -3119 | -4002 | 8822 | 2 | 431 |
| round | reject_native | micro_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 483 | 6202 | 1208 | 1809 | 6293 | 6823 | 1 | 431 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 431 |
| round | retest_native | vib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 475 | 6796 | 130 | -2984 | 617 | 3909 | 1 | 431 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 325 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 325 |
| session_hl | false_break | tsf_5_200 | {"M": 1, "k": 0.0} | sym15u / both | 304 | 5700 | 445 | 717 | 2007 | 4594 | 1 | 325 |
| session_hl | false_break_native | tsf_5_200 | {"M": 1, "k": 0.0} | sym15u / both | 304 | 5700 | 445 | 717 | 2007 | 4594 | 1 | 325 |
| session_hl | reject | lbrk_4_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 723 | 2762 | 1054 | -2325 | -1011 | 1727 | 1 | 325 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 325 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 325 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 325 |
| trendline | break | vrb_240 | {"n": 3, "k": 0.5} | sym15u / both | 357 | 4291 | -656 | -98 | 1644 | 4319 | 1 | 215 |
| trendline | break_native | pnf_10 | {"n": 2, "k": 0.0} | sym15u / both | 268 | 3755 | 1245 | -556 | 3006 | 4346 | 2 | 215 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 285 | 4062 | 1560 | 1127 | 1434 | 5996 | 1 | 215 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4692 | 42 | 1654 | 1101 | 5496 | 1 | 215 |
| trendline | reject | anch_R0830_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 193 | 4365 | -1173 | -676 | 3045 | 5913 | 1 | 215 |
| trendline | reject_native | anch_R0830_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 193 | 4365 | -1117 | -676 | 3045 | 5913 | 1 | 215 |
| trendline | retest | tsf_5_1200 | {"M": 10, "tol": 0.5} | sym15u / both | 179 | 3503 | 720 | -1732 | 465 | 3130 | 1 | 215 |
| trendline | retest_native | drb_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 254 | 3633 | -1297 | 410 | 1788 | 2674 | 1 | 215 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 326 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 326 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 326 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 326 |
| uw_dp | reject | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 129 | 4506 | 0 | 0 | 241 | 3031 | 1 | 326 |
| uw_dp | reject_native | vfp_rng40 | {"tol": 0.0, "conf": "close"} | sym15u / both | 129 | 4506 | 0 | 0 | 241 | 3031 | 1 | 326 |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 153 | 3839 | 0 | 0 | 1297 | 3514 | 2 | 326 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 326 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 325 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 1 | 325 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 1 | 325 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 1 | 325 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 1 | 325 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 325 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 325 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 325 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 325 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 325 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 325 |
| uw_qqq | false_break_native | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3384 | 0 | 197 | 3751 | 4321 | 1 | 325 |
| uw_qqq | reject | rngor_B200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 218 | 4150 | 0 | -273 | 2534 | 3126 | 1 | 325 |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 325 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 325 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 325 |
| vwap | break | tsf_10_120 | {"n": 3, "k": 0.5} | sym15u / both | 300 | 5066 | 1744 | 2102 | 1335 | 5377 | 1 | 325 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 325 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 178 | 4696 | 63 | -174 | 2422 | 5048 | 1 | 325 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 166 | 4411 | -108 | -214 | 2319 | 4241 | 1 | 325 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 325 |
| vwap | reject_native | vnorm_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 379 | 6884 | 93 | -773 | 2670 | 8896 | 1 | 325 |
| vwap | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 364 | 5402 | 219 | -90 | 1699 | 5388 | 1 | 325 |
| vwap | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 369 | 4676 | 125 | 382 | 2643 | 3279 | 1 | 325 |
| vwap_bands | break | mom_20 | {"n": 3, "k": 0.5} | sym15u / both | 475 | 6544 | 86 | 1981 | 5311 | 8312 | 1 | 325 |
| vwap_bands | break_native | trb_400 | {"n": 2, "k": 0.25} | sym15u / both | 528 | 6544 | 628 | -1660 | 456 | 6948 | 1 | 325 |
| vwap_bands | false_break | swing_atr_0.6 | {"M": 3, "k": 0.5} | sym15u / both | 477 | 3977 | 1234 | -534 | 5712 | 3574 | 1 | 325 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 325 |
| vwap_bands | reject | tm60 | {"tol": 1.0, "conf": "close"} | sym15u / both | 498 | 7209 | 138 | -1461 | -774 | 7274 | 2 | 325 |
| vwap_bands | reject_native | tm60 | {"tol": 0.5, "conf": "close"} | sym15u / both | 505 | 7078 | 213 | -421 | 4075 | 5878 | 2 | 325 |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 475 | 5871 | -47 | -3369 | -2356 | 8027 | 2 | 325 |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 452 | 5820 | -431 | 1126 | 1466 | 4714 | 1 | 325 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 326 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 326 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 326 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 326 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 | 1812 | 674 | -92 | 992 | 1655 | 1 | 326 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 82 | 2131 | 988 | -272 | -1646 | 1573 | 1 | 326 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 326 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 326 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 325 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym8u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 2 | 325 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 3068 | 829 | 2566 | -2302 | 3067 | 1 | 325 |
| zones | false_break_native | dlt_45 | {"M": 1, "k": 0.5} | sym30u / both | 144 | 3507 | 511 | -1059 | -2712 | 2632 | 2 | 325 |
| zones | reject | anch_R0830_B25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 2457 | -357 | -2238 | 298 | 1747 | 1 | 325 |
| zones | reject_native | anch_R0830_B25 | {"tol": 0.5, "conf": "body"} | sym15u / both | 144 | 3506 | -498 | -1740 | 2990 | 3437 | 1 | 325 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 325 |
| zones | retest_native | vrb_1200 | {"M": 10, "tol": 0.5} | sym15u / both | 148 | 3375 | 216 | -1398 | 298 | 3696 | 1 | 325 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 63 | 745 | -750 | 713 | 55 | 78 | 1 | 326 |
| sdx15 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 218 | 3979 | 866 | -1611 | -3817 | 3589 | 1 | 326 |
| sdx15 | lim_prox | dib_3500 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 211 | 4594 | -142 | -1792 | -2175 | 4608 | 1 | 326 |
| sdx15 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 151 | 2838 | 1403 | -67 | -500 | 3343 | 1 | 326 |
| sdx15 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 213 | 2090 | -694 | -931 | -1174 | 3194 | 1 | 326 |
| sdx15 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 326 |
| sdx15 | rej_zone | rng_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 190 | 4546 | 51 | 187 | -481 | 4555 | 1 | 326 |
| sdx15 | retest | pnf_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 31 | 526 | -752 | 859 | -350 | 61 | 1 | 326 |
| sdx3 | break | pnf_7 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 103 | 1995 | -691 | -13 | 2296 | 1834 | 1 | 326 |
| sdx3 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 319 | 2759 | 1671 | -235 | -5084 | 1786 | 1 | 326 |
| sdx3 | lim_prox | vrb_240 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 595 | 3214 | -1162 | 2156 | -2845 | 392 | 1 | 326 |
| sdx3 | rej | pnf_7 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 108 | 2223 | 1029 | -286 | -877 | 2043 | 1 | 326 |
| sdx3 | rej_flow | vrb_400 | {"d": "E", "F": 9} | sym15u / both | 274 | 1608 | 600 | -1658 | -1988 | 272 | 1 | 326 |
| sdx3 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 326 |
| sdx3 | rej_zone | tsf_10_120 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 374 | 4249 | -1572 | 1376 | -3168 | 4800 | 1 | 326 |
| sdx3 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 68 | 1390 | 118 | 65 | 1080 | 1692 | 1 | 326 |
| sdx30 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 34 | 466 | -431 | 870 | -122 | 440 | 1 | 327 |
| sdx30 | lim_mid | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 103 | 1951 | 721 | -406 | -107 | 947 | 1 | 327 |
| sdx30 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 3042 | -219 | -1016 | 531 | 2612 | 1 | 327 |
| sdx30 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 38 | 1091 | -267 | -1452 | -151 | 712 | 1 | 327 |
| sdx30 | rej_flow | volor_B500 | {"d": "E", "F": 9} | plain60/60 / short | 71 | 821 | 253 | -198 | -321 | 723 | 1 | 327 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 327 |
| sdx30 | rej_zone | tsf_25_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 107 | 3453 | -1273 | -2043 | -1903 | 1465 | 1 | 327 |
| sdx5 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 90 | 1699 | -702 | 485 | -4 | 835 | 1 | 326 |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 720 | 2734 | 720 | 3 | -3881 | 2478 | 1 | 326 |
| sdx5 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 746 | 2572 | -102 | -1530 | -5419 | 2741 | 1 | 326 |
| sdx5 | rej | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 262 | 2521 | -220 | 1136 | -393 | 2008 | 1 | 326 |
| sdx5 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 97 | 1766 | 159 | -855 | -1246 | 2358 | 1 | 326 |
| sdx5 | rej_native | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 259 | 2842 | -263 | 1629 | -600 | 2273 | 1 | 326 |
| sdx5 | rej_zone | vol_4000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 362 | 3759 | 51 | -2567 | -2706 | 5488 | 1 | 326 |
| sdx5 | retest | kagi_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 82 | 1774 | -756 | -147 | -45 | 2087 | 1 | 326 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 384 | 10 | 407 | 778 | 289 | 1 | 326 |
| sdx60 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 73 | 1628 | 155 | 544 | -311 | 1363 | 1 | 326 |
| sdx60 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 259 | 1933 | -320 | -699 | -24 | 2535 | 1 | 326 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 76 | 986 | -87 | -92 | 901 | 1294 | 1 | 326 |
| sdx60 | rej_flow | volor_B500 | {"d": "E", "F": 9} | plain60/60 / short | 49 | 668 | 535 | 395 | 112 | 862 | 1 | 326 |
| sdx60 | rej_native | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 193 | 1131 | 262 | -1162 | 885 | 1239 | 1 | 326 |
| sdx60 | rej_zone | tm3600 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 72 | 2676 | 119 | 118 | -1586 | 2417 | 1 | 326 |
| sdx_renko28 | break | pnf_10 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 124 | 1893 | -1115 | 906 | 833 | 1183 | 1 | 325 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 325 |
| sdx_renko28 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 285 | 3300 | 213 | 469 | 2009 | 5781 | 1 | 325 |
| sdx_renko28 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 537 | 5198 | -406 | -1538 | 809 | 6421 | 1 | 325 |
| sdx_renko28 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / short | 102 | 1940 | 787 | 26 | -743 | 1348 | 1 | 325 |
| sdx_renko28 | rej_native | volor_B500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 691 | 4153 | -458 | -1204 | 2099 | 5934 | 1 | 325 |
| sdx_renko28 | rej_zone | volor_B500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 691 | 4153 | -458 | -1204 | 2099 | 5934 | 1 | 325 |
| sdx_renko28 | retest | kagi_80 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 110 | 1224 | -284 | 799 | -759 | 384 | 1 | 325 |
| sdx_rng28 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 301 | 3408 | -2123 | 661 | -816 | 3058 | 1 | 325 |
| sdx_rng28 | lim_mid | frenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 331 | 3377 | 299 | -3020 | -3304 | 3142 | 1 | 325 |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1024 | 4026 | -947 | 896 | -3778 | 6473 | 1 | 325 |
| sdx_rng28 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 462 | 2252 | -1322 | -833 | -1038 | 2734 | 1 | 325 |
| sdx_rng28 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 493 | 2558 | -783 | 2787 | -3819 | 2063 | 1 | 325 |
| sdx_rng28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 325 |
| sdx_rng28 | rej_zone | tsf_2_2000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 600 | 4769 | 448 | -442 | -1686 | 3536 | 1 | 325 |
| sdx_rng28 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 117 | 2944 | -978 | 239 | 485 | 3365 | 1 | 325 |
| sdx_vol1100 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 314 | 4031 | -1409 | -503 | 658 | 4201 | 1 | 325 |
| sdx_vol1100 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 275 | 6337 | -998 | 71 | 1443 | 6397 | 1 | 325 |
| sdx_vol1100 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 278 | 5565 | -679 | -26 | -465 | 6171 | 1 | 325 |
| sdx_vol1100 | rej | frenko_28 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 308 | 3089 | -275 | -2567 | -1719 | 2706 | 1 | 325 |
| sdx_vol1100 | rej_flow | vrb_400 | {"d": "E", "F": 0} | sym15u / short | 161 | 2399 | -174 | -1171 | -785 | 2439 | 1 | 325 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 768 | 3970 | -570 | -433 | -756 | 4714 | 1 | 325 |
| sdx_vol1100 | rej_zone | tick_5000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 391 | 3880 | 1601 | -1293 | -1062 | 5402 | 1 | 325 |
| sdx_vol1100 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 227 | 3437 | -1140 | -704 | 968 | 4601 | 1 | 325 |
| fib15 | break | dib_2000 | {"n": 3, "k": 0.5} | sym15u / short | 142 | 3835 | -591 | -539 | -1451 | 3789 | 1 | 326 |
| fib15 | break_native | tm45 | {"n": 1, "k": 0.0} | sym15u / short | 119 | 3822 | -8 | -287 | 470 | 3804 | 1 | 326 |
| fib15 | false_break | time_s_45 | {"M": 1, "k": 0.0} | sym15u / short | 134 | 3485 | -685 | -905 | 709 | 4240 | 1 | 326 |
| fib15 | false_break_native | vib_3500 | {"M": 2, "k": 0.5} | sym15u / short | 131 | 3617 | -414 | -1411 | -1658 | 4145 | 1 | 326 |
| fib15 | pullback | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 146 | 2537 | 38 | 763 | -1653 | 1759 | 1 | 326 |
| fib15 | pullback_native | anch_L0200_B50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 146 | 2537 | 38 | 763 | -1653 | 1759 | 1 | 326 |
| fib15 | reject | rng_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 255 | 3925 | 1276 | 1265 | 1391 | 4665 | 1 | 326 |
| fib15 | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 326 |
| fib15 | retest | trb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 372 | 4012 | -1755 | -1138 | -2038 | 2975 | 1 | 326 |
| fib15 | retest_native | trb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 372 | 4012 | -1755 | -1138 | -2038 | 2975 | 1 | 326 |
| fib5 | break | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5454 | 1633 | 3169 | 1237 | 6533 | 1 | 327 |
| fib5 | break_native | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 294 | 5957 | 1611 | 1641 | 2147 | 5578 | 1 | 327 |
| fib5 | false_break | trb_2000 | {"M": 3, "k": 0.5} | sym15u / both | 273 | 5281 | -115 | -434 | 2246 | 5957 | 1 | 327 |
| fib5 | false_break_native | tick_800 | {"M": 3, "k": 0.5} | sym15u / both | 283 | 5266 | -894 | 115 | 1094 | 7007 | 1 | 327 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 1 | 327 |
| fib5 | pullback_native | drb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 2734 | -787 | 917 | -2068 | 1989 | 1 | 327 |
| fib5 | reject | vsess_200 | {"tol": 0.5, "conf": "body"} | sym8u / both | 285 | 6289 | -371 | 1437 | -1282 | 4830 | 2 | 327 |
| fib5 | reject_native | vol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 274 | 5828 | -819 | 224 | 1500 | 3983 | 1 | 327 |
| fib5 | retest | vol_750 | {"M": 6, "tol": 0.5} | sym15u / both | 262 | 4869 | 543 | -1080 | -972 | 6334 | 1 | 327 |
| fib5 | retest_native | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / both | 320 | 4654 | -1449 | -943 | 319 | 3902 | 1 | 327 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 327 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 327 |
| fib60 | false_break | rng_10 | {"M": 2, "k": 0.5} | sym15u / both | 242 | 3422 | -1420 | -398 | -943 | 3829 | 1 | 327 |
| fib60 | false_break_native | cdr_250 | {"M": 2, "k": 0.5} | sym15u / both | 175 | 3320 | -801 | 220 | -127 | 4246 | 1 | 327 |
| fib60 | pullback | tick_300 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 122 | 1350 | -490 | -176 | 168 | 1147 | 1 | 327 |
| fib60 | pullback_native | tick_300 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 126 | 1344 | -501 | -373 | 364 | 1152 | 1 | 327 |
| fib60 | reject | vib_400 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 430 | 3691 | -673 | -1126 | -1933 | 3125 | 1 | 327 |
| fib60 | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 136 | 2932 | -434 | 1783 | -20 | 2164 | 1 | 327 |
| fib60 | retest | vib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 231 | 3703 | -145 | -5 | 635 | 3658 | 1 | 327 |
| fib60 | retest_native | mrenko_20 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 130 | 3401 | 423 | 522 | 781 | 1846 | 2 | 327 |
| fibr_dev | break | tm780 | {"n": 2, "k": 0.25} | sym15u / both | 271 | 3705 | -1094 | -49 | -2094 | 3159 | 1 | 217 |
| fibr_dev | break_native | dlt_150 | {"n": 3, "k": 0.5} | sym15u / both | 316 | 4162 | -221 | -1240 | -22 | 4827 | 1 | 217 |
| fibr_dev | false_break | dlt_150 | {"M": 3, "k": 0.5} | sym15u / both | 304 | 3043 | -1386 | -258 | -52 | 5113 | 1 | 217 |
| fibr_dev | false_break_native | dol_1100 | {"M": 1, "k": 0.0} | plain60/60 / both | 827 | 2989 | -64 | -241 | -1055 | 382 | 1 | 217 |
| fibr_dev | reject | rng_10 | {"tol": 0.0, "conf": "body"} | asym15u/30u / both | 362 | 4488 | -1137 | -2550 | -1280 | 5040 | 2 | 217 |
| fibr_dev | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | asym15u/30u / both | 362 | 4488 | -1137 | -2550 | -1280 | 5040 | 2 | 217 |
| fibr_dev | retest | tsf_5_1200 | {"M": 6, "tol": 0.5} | plain60/60 / both | 435 | 3723 | -543 | -245 | -71 | 3358 | 1 | 217 |
| fibr_dev | retest_native | anch_N0930_B10 | {"M": 10, "tol": 0.5} | sym15u / both | 224 | 2870 | -1835 | -2044 | -1340 | 1664 | 1 | 217 |
| fibr_ib | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 261 | 5071 | -680 | -216 | 1018 | 5290 | 1 | 215 |
| fibr_ib | break_native | rng_10 | {"n": 3, "k": 0.0} | sym30u / both | 266 | 4204 | -441 | -937 | 1237 | 6348 | 2 | 215 |
| fibr_ib | false_break | trb_1200 | {"M": 1, "k": 0.0} | sym15u / both | 253 | 4121 | -1039 | -922 | -2846 | 5732 | 1 | 215 |
| fibr_ib | false_break_native | trb_1200 | {"M": 1, "k": 0.0} | sym15u / both | 253 | 4121 | -1039 | -922 | -2846 | 5732 | 1 | 215 |
| fibr_ib | reject | vrb_25000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 151 | 2981 | -701 | 817 | -116 | 3496 | 1 | 215 |
| fibr_ib | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 267 | 3485 | 245 | 3147 | -1000 | 2581 | 1 | 215 |
| fibr_ib | retest | dltor_B080 | {"M": 3, "tol": 0.0} | sym15u / both | 233 | 4110 | -2991 | -1502 | -1483 | 4638 | 1 | 215 |
| fibr_ib | retest_native | dltor_B080 | {"M": 3, "tol": 0.0} | sym15u / both | 233 | 4110 | -2991 | -1502 | -1483 | 4638 | 1 | 215 |
| fibr_on | break | entropy_B130 | {"n": 3, "k": 0.5} | sym15u / both | 214 | 3455 | -1251 | 1686 | 1793 | 2370 | 1 | 217 |
| fibr_on | break_native | tm780 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 3652 | -1384 | -120 | -1555 | 2090 | 1 | 217 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 232 | 2221 | -828 | 1006 | -1840 | 1304 | 1 | 217 |
| fibr_on | false_break_native | vsess_600 | {"M": 1, "k": 0.5} | sym15u / both | 210 | 2639 | 417 | -2453 | -232 | 2182 | 2 | 217 |
| fibr_on | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym8u / both | 327 | 4816 | -680 | 2527 | -1725 | 4023 | 2 | 217 |
| fibr_on | reject_native | vsess_600 | {"tol": 0.0, "conf": "body"} | sym8u / both | 327 | 4816 | -680 | 2527 | -1725 | 4023 | 2 | 217 |
| fibr_on | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 275 | 3036 | -95 | -156 | -2903 | 3382 | 1 | 217 |
| fibr_on | retest_native | dol_2600 | {"M": 10, "tol": 0.5} | sym15u / both | 218 | 4101 | -1837 | 1375 | 655 | 5579 | 1 | 217 |
| fibr_or | break | mrenko_20 | {"n": 2, "k": 0.25} | asym20u/10u / both | 226 | 3795 | 135 | 208 | 1874 | 4023 | 2 | 213 |
| fibr_or | break_native | vsess_600 | {"n": 2, "k": 0.5} | asym20u/10u / both | 273 | 3486 | -175 | 711 | 1127 | 3005 | 2 | 213 |
| fibr_or | false_break | kagi_10 | {"M": 2, "k": 0.5} | sym15u / both | 227 | 3162 | -2539 | 1556 | 88 | 4085 | 1 | 213 |
| fibr_or | false_break_native | pasl_28 | {"M": 1, "k": 0.0} | sym8u / both | 241 | 2890 | -1702 | 165 | -1132 | 1442 | 2 | 213 |
| fibr_or | reject | dltor_B080 | {"tol": 0.5, "conf": "body"} | sym15u / both | 219 | 3742 | 568 | 174 | -951 | 2888 | 1 | 213 |
| fibr_or | reject_native | lbrk_4_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 168 | 3712 | 266 | 1434 | -910 | 4280 | 1 | 213 |
| fibr_or | retest | tm1200 | {"M": 10, "tol": 0.5} | sym15u / short | 90 | 2900 | -109 | 274 | -1833 | 3297 | 1 | 213 |
| fibr_or | retest_native | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 226 | 3433 | -1079 | 1971 | 1090 | 4690 | 1 | 213 |
| fibr_pd | break | vfp_rng16 | {"n": 2, "k": 0.25} | plain60/60 / both | 439 | 2945 | -798 | 543 | -2719 | 2087 | 1 | 214 |
| fibr_pd | break_native | vfp_rng16 | {"n": 2, "k": 0.25} | sym15u / both | 434 | 3768 | -859 | 513 | -2779 | 2421 | 1 | 214 |
| fibr_pd | false_break | anch_N0930_B10 | {"M": 3, "k": 0.5} | sym15u / short | 83 | 2346 | -672 | 249 | 254 | 1226 | 1 | 214 |
| fibr_pd | false_break_native | tm780 | {"M": 1, "k": 0.0} | sym15u / short | 94 | 2177 | -92 | 210 | -1121 | 2225 | 1 | 214 |
| fibr_pd | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 197 | 3093 | 14 | 1008 | -2214 | 3340 | 1 | 214 |
| fibr_pd | reject_native | kagi_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 3634 | -868 | -66 | -1162 | 2545 | 1 | 214 |
| fibr_pd | retest | rng_10 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 296 | 2852 | -998 | -1350 | -403 | 2990 | 2 | 214 |
| fibr_pd | retest_native | trend_80 | {"M": 10, "tol": 0.5} | sym15u / both | 153 | 3064 | -1434 | 1651 | -2201 | 3131 | 1 | 214 |
| piv_cama | break | vrb_1200 | {"n": 2, "k": 0.25} | sym15u / both | 213 | 2903 | 1780 | -413 | -1589 | 3070 | 1 | 216 |
| piv_cama | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 229 | 3002 | -798 | 88 | -642 | 3792 | 1 | 216 |
| piv_cama | false_break | drb_1200 | {"M": 2, "k": 0.5} | sym15u / both | 219 | 2878 | -1322 | 277 | 281 | 1697 | 1 | 216 |
| piv_cama | false_break_native | tsf_2_2000 | {"M": 1, "k": 0.0} | sym15u / both | 198 | 2542 | -2506 | 1061 | -488 | 2495 | 1 | 216 |
| piv_cama | reject | tsf_2_100 | {"tol": 0.5, "conf": "body"} | sym15u / both | 247 | 3149 | 1430 | -1551 | -697 | 5269 | 1 | 216 |
| piv_cama | reject_native | dol_750 | {"tol": 0.0, "conf": "close"} | sym15u / both | 226 | 2814 | 1284 | -139 | 1418 | 2715 | 1 | 216 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 3017 | 1323 | -981 | 973 | 1360 | 1 | 216 |
| piv_cama | retest_native | tsf_2_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 206 | 3041 | -1051 | -245 | -1692 | 2625 | 1 | 216 |
| piv_floor | break | trend_28 | {"n": 3, "k": 0.5} | sym15u / both | 177 | 2612 | -423 | 3421 | -592 | 819 | 1 | 214 |
| piv_floor | break_native | tsf_10_120 | {"n": 3, "k": 0.5} | sym15u / both | 182 | 2835 | -395 | 2737 | -262 | 1438 | 1 | 214 |
| piv_floor | false_break | tm3600 | {"M": 2, "k": 0.5} | sym15u / short | 66 | 2144 | -466 | 180 | 959 | 1921 | 1 | 214 |
| piv_floor | false_break_native | cusum_10 | {"M": 1, "k": 0.5} | asym15u/30u / both | 186 | 3184 | -2 | 683 | -3164 | 4800 | 2 | 214 |
| piv_floor | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym8u / both | 185 | 2861 | -914 | -554 | -706 | 2889 | 2 | 214 |
| piv_floor | reject_native | anch_L0200_B25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 215 | 4755 | 411 | 2328 | -3907 | 4862 | 1 | 214 |
| piv_floor | retest | trend_80 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2273 | 241 | 1683 | 462 | 2812 | 1 | 214 |
| piv_floor | retest_native | vrb_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 146 | 2310 | -1697 | 1982 | -676 | 1780 | 1 | 214 |
| piv_wf | break | vib_70000 | {"n": 2, "k": 0.25} | sym15u / both | 179 | 3676 | -1551 | 64 | -1302 | 3744 | 1 | 215 |
| piv_wf | break_native | pasl_56 | {"n": 1, "k": 0.0} | sym15u / both | 227 | 3485 | -946 | 955 | 942 | 2430 | 1 | 215 |
| piv_wf | false_break | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3485 | -963 | 778 | 942 | 2430 | 1 | 215 |
| piv_wf | false_break_native | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3485 | -963 | 778 | 942 | 2430 | 1 | 215 |
| piv_wf | reject | vrb_1200 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 418 | 3079 | 2011 | -84 | -469 | 1948 | 2 | 215 |
| piv_wf | reject_native | vrb_1200 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 418 | 3079 | 2011 | -84 | -469 | 1948 | 2 | 215 |
| piv_wf | retest | drb_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 196 | 2831 | -1666 | 1171 | -4880 | 3253 | 1 | 215 |
| piv_wf | retest_native | vrb_1200 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 214 | 3335 | -1232 | 2061 | -3025 | 3309 | 2 | 215 |
| swcluster | break | vib_40000 | {"n": 3, "k": 0.5} | sym15u / both | 47 | 1952 | 518 | 415 | -988 | 2552 | 1 | 217 |
| swcluster | break_native | tsf_5_50 | {"n": 3, "k": 0.5} | sym15u / both | 53 | 1803 | 236 | 449 | 192 | 1597 | 1 | 217 |
| swcluster | false_break | vsess_600 | {"M": 1, "k": 0.5} | asym10u/20u / both | 53 | 1301 | -228 | -337 | -1082 | 1001 | 2 | 217 |
| swcluster | false_break_native | mrenko_112 | {"M": 1, "k": 0.0} | sym15u / both | 37 | 1207 | -1095 | 1189 | -264 | 1110 | 1 | 217 |
| swcluster | reject | vib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 48 | 1962 | -53 | 325 | 1252 | 2677 | 1 | 217 |
| swcluster | reject_native | trend_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 49 | 1930 | -206 | 275 | -424 | 1894 | 1 | 217 |
| swcluster | retest | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1635 | 68 | 1694 | -1137 | 1335 | 1 | 217 |
| swcluster | retest_native | anch_R0830_B50 | {"M": 10, "tol": 0.5} | sym15u / both | 38 | 1773 | -1040 | -444 | -81 | 1320 | 1 | 217 |
| swsr15 | break | time_m_20 | {"n": 1, "k": 0.0} | sym15u / both | 166 | 3668 | -2883 | -1482 | -14 | 3369 | 1 | 216 |
| swsr15 | break_native | kagi_20 | {"n": 1, "k": 0.25} | sym15u / both | 249 | 4161 | 651 | -2225 | 1363 | 3140 | 2 | 216 |
| swsr15 | false_break | pasl_56 | {"M": 2, "k": 0.5} | sym15u / both | 237 | 4412 | -1184 | 135 | 2943 | 2738 | 1 | 216 |
| swsr15 | false_break_native | pasl_56 | {"M": 1, "k": 0.0} | sym15u / both | 237 | 3930 | -1061 | 239 | 2990 | 2256 | 1 | 216 |
| swsr15 | reject | rngor_B320 | {"tol": 1.0, "conf": "body"} | sym15u / short | 138 | 4307 | 106 | 117 | 923 | 4339 | 1 | 216 |
| swsr15 | reject_native | rngor_B320 | {"tol": 0.5, "conf": "body"} | sym15u / both | 240 | 4358 | -173 | 629 | 342 | 4324 | 1 | 216 |
| swsr15 | retest | tsf_2_200 | {"M": 3, "tol": 0.0} | sym15u / both | 207 | 3995 | -575 | 301 | -635 | 3208 | 1 | 216 |
| swsr15 | retest_native | tsf_2_200 | {"M": 3, "tol": 0.0} | sym15u / both | 207 | 3995 | -575 | 301 | -635 | 3208 | 1 | 216 |
| swsr5 | break | vrb_1200 | {"n": 1, "k": 0.5} | sym15u / both | 270 | 5624 | 1255 | -598 | -133 | 7036 | 2 | 218 |
| swsr5 | break_native | vrb_1200 | {"n": 1, "k": 0.25} | sym8u / both | 326 | 6233 | -576 | 694 | -1807 | 7341 | 2 | 218 |
| swsr5 | false_break | dib_25000 | {"M": 2, "k": 0.5} | sym15u / both | 259 | 4542 | -2910 | -174 | 2213 | 5887 | 1 | 218 |
| swsr5 | false_break_native | dib_25000 | {"M": 1, "k": 0.0} | sym15u / both | 259 | 4454 | -3032 | 311 | 2477 | 6122 | 1 | 218 |
| swsr5 | reject | tib_2000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 290 | 4874 | 810 | -1129 | -3662 | 6000 | 1 | 218 |
| swsr5 | reject_native | dib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 316 | 4855 | -1006 | -2814 | 1 | 6421 | 1 | 218 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 233 | 4454 | -1674 | -1022 | 876 | 5025 | 2 | 218 |
| swsr5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 291 | 4019 | -261 | -2125 | 4208 | 2958 | 1 | 218 |
| swsr60 | break | anch_N0930_B50 | {"n": 2, "k": 0.25} | sym15u / both | 135 | 2519 | -2819 | 9 | -39 | 3153 | 1 | 216 |
| swsr60 | break_native | kagi_40 | {"n": 3, "k": 0.5} | sym15u / both | 163 | 2879 | -1426 | 831 | -277 | 3346 | 1 | 216 |
| swsr60 | false_break | tm3600 | {"M": 1, "k": 0.0} | sym15u / short | 62 | 2189 | -354 | -178 | 388 | 1417 | 1 | 216 |
| swsr60 | false_break_native | rng_10 | {"M": 1, "k": 0.5} | sym15u / short | 96 | 2391 | -96 | 2 | 204 | 2484 | 2 | 216 |
| swsr60 | reject | vsess_600 | {"tol": 0.5, "conf": "close"} | sym8u / both | 227 | 2677 | -521 | -297 | 709 | 2930 | 2 | 216 |
| swsr60 | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 212 | 3196 | -733 | 1116 | -3739 | 3316 | 1 | 216 |
| swsr60 | retest | rng_80 | {"M": 6, "tol": 0.0} | sym8u / both | 102 | 2133 | -1615 | 317 | -156 | 1091 | 2 | 216 |
| swsr60 | retest_native | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 182 | 2617 | -2238 | 661 | -1997 | 3098 | 1 | 216 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | sym8u / both | 291 | 3412 | -1070 | 1079 | 1843 | -886 | 2 | 325 |
| stack | break_native | rng_20 | {"k": 2, "cw": 1.0} | sym8u / both | 301 | 3535 | -387 | 126 | -977 | -466 | 2 | 325 |
| stack | reject | rng_20 | {"k": 3, "cw": 2.0} | plain60/60 / both | 334 | 2793 | -356 | 119 | -1156 | 2530 | 2 | 325 |
| stack | reject_native | tsf_10_60 | {"k": 4, "cw": 2.0} | sym15u / both | 219 | 4390 | -454 | -790 | -4663 | 5642 | 1 | 325 |
| book_walls | break | time_s_20 | {"n": 1, "k": 0.0} | sym15u / both | 31 | 540 | -298 | -289 | 137 | 543 | 1 | 326 |
| book_walls | break_native | tib_240 | {"n": 2, "k": 0.25} | plain60/60 / both | 36 | 577 | 557 | 633 | -519 | 646 | 1 | 326 |
| book_walls | reject | time_s_15 | {"tol": 0.0, "conf": "close"} | sym15u / both | 30 | 301 | -817 | 1354 | 354 | 163 | 1 | 326 |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 34 | 561 | 55 | -204 | -128 | 492 | 1 | 326 |
| book_walls | retest | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 39 | 491 | -648 | -45 | 771 | 399 | 1 | 326 |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 34 | 627 | -374 | 538 | 3 | 600 | 1 | 326 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 327 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 327 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 327 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 327 |
| book_walls_loose | reject | entropy_B500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 106 | 1224 | 126 | 972 | -75 | 716 | 1 | 327 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 327 |
| book_walls_loose | retest | rngor_B200 | {"M": 10, "tol": 0.5} | sym15u / both | 59 | 1173 | 89 | 361 | 1224 | 1614 | 1 | 327 |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 1146 | 212 | 787 | -261 | 941 | 1 | 327 |
| channel | break | rng_10 | {"n": 1, "k": 0.25} | asym20u/10u / both | 450 | 4301 | 421 | -1165 | 3188 | 3582 | 2 | 220 |
| channel | break_native | rng_10 | {"n": 1, "k": 0.25} | asym20u/10u / both | 455 | 4968 | -1237 | -82 | 2469 | 4380 | 2 | 220 |
| channel | false_break | dib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 248 | 3805 | -2238 | 544 | 2799 | 4182 | 1 | 220 |
| channel | false_break_native | dib_25000 | {"M": 1, "k": 0.0} | sym15u / both | 249 | 3787 | -2213 | 309 | 2705 | 3976 | 1 | 220 |
| channel | reject | vib_3500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 288 | 4323 | -586 | 62 | -2219 | 2002 | 1 | 220 |
| channel | reject_native | entropy_B080 | {"tol": 1.0, "conf": "body"} | sym15u / both | 309 | 5014 | 368 | 1543 | -2979 | 6466 | 1 | 220 |
| channel | retest | trend_56 | {"M": 10, "tol": 0.5} | sym15u / both | 193 | 4300 | -1313 | 2900 | -1969 | 4438 | 1 | 220 |
| channel | retest_native | kagi_40 | {"M": 6, "tol": 0.5} | sym15u / both | 279 | 4816 | -153 | -1208 | 1427 | 4943 | 1 | 220 |
| fvg15 | break | vib_400 | {"n": 1, "k": 0.0} | sym15u / both | 176 | 2199 | 256 | -727 | -390 | 779 | 1 | 219 |
| fvg15 | break_native | vib_400 | {"n": 1, "k": 0.0} | sym15u / both | 176 | 2199 | 256 | -727 | -390 | 779 | 1 | 219 |
| fvg15 | false_break | time_s_10 | {"M": 1, "k": 0.0} | sym15u / both | 129 | 1721 | -508 | -342 | -858 | 738 | 1 | 219 |
| fvg15 | false_break_native | time_s_10 | {"M": 1, "k": 0.0} | sym15u / both | 129 | 1721 | -508 | -342 | -858 | 738 | 1 | 219 |
| fvg15 | reject | vsess_600 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 124 | 2115 | 601 | -1006 | -1830 | 1338 | 2 | 219 |
| fvg15 | reject_native | vsess_600 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 131 | 1993 | 316 | -622 | -1824 | 1698 | 2 | 219 |
| fvg15 | retest | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 120 | 2032 | -538 | -1332 | -2444 | 1430 | 1 | 219 |
| fvg15 | retest_native | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 119 | 2194 | -495 | -740 | -2250 | 1785 | 1 | 219 |
| fvg5 | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2941 | -43 | 529 | 74 | 1047 | 1 | 216 |
| fvg5 | break_native | rngor_B080 | {"n": 3, "k": 0.5} | sym15u / both | 208 | 3271 | -1580 | -1271 | -1286 | 3071 | 1 | 216 |
| fvg5 | false_break | tm780 | {"M": 3, "k": 0.5} | sym15u / both | 137 | 1829 | -984 | 1358 | 2019 | 1654 | 1 | 216 |
| fvg5 | false_break_native | tsf_5_200 | {"M": 2, "k": 0.5} | sym15u / both | 168 | 2182 | 500 | 876 | -68 | 2255 | 1 | 216 |
| fvg5 | reject | cusum_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3711 | -316 | 1060 | -1467 | 5283 | 1 | 216 |
| fvg5 | reject_native | cusum_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3711 | -316 | 1060 | -1467 | 5283 | 1 | 216 |
| fvg5 | retest | tm240 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2929 | 148 | -1758 | -1309 | 2780 | 1 | 216 |
| fvg5 | retest_native | trend_112 | {"M": 10, "tol": 0.5} | sym15u / both | 91 | 2574 | -755 | 1247 | -372 | 3432 | 1 | 216 |
| gaps | break | rng_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 117 | 2588 | -44 | 1005 | -1182 | 1826 | 2 | 327 |
| gaps | break_native | rng_14 | {"n": 1, "k": 0.25} | asym10u/20u / both | 117 | 2362 | -556 | 1239 | -1346 | 1099 | 2 | 327 |
| gaps | false_break | mom_10 | {"M": 1, "k": 0.5} | asym15u/30u / both | 105 | 1741 | -692 | -1175 | -940 | 2386 | 2 | 327 |
| gaps | false_break_native | vnorm_1500 | {"M": 2, "k": 0.5} | sym15u / both | 102 | 1911 | -1062 | 645 | -526 | 1686 | 1 | 327 |
| gaps | reject | rng_10 | {"tol": 0.0, "conf": "close"} | sym30u / both | 101 | 2480 | 1711 | -631 | 606 | 2611 | 2 | 327 |
| gaps | reject_native | dchg_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2843 | -341 | 133 | -834 | 2496 | 1 | 327 |
| gaps | retest | trb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 87 | 1928 | -507 | 132 | -112 | 1509 | 1 | 327 |
| gaps | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 122 | 2649 | -496 | -97 | 417 | 1216 | 1 | 327 |
| mmove | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 220 |
| mmove | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 220 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | asym20u/10u / both | 326 | 5059 | -1240 | 376 | 248 | 5902 | 2 | 220 |
| mmove | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym8u / both | 290 | 5119 | -1034 | 882 | -460 | 3889 | 2 | 220 |
| mmove | reject | vib_40000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 195 | 2793 | -623 | 432 | 19 | 2577 | 1 | 220 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | asym10u/20u / short | 134 | 2512 | -477 | 493 | 1370 | 2397 | 2 | 220 |
| mmove | retest | trend_28 | {"M": 6, "tol": 0.5} | sym15u / both | 209 | 3446 | -1126 | 1155 | 843 | 4317 | 1 | 220 |
| mmove | retest_native | pnf_7 | {"M": 3, "tol": 0.5} | sym8u / both | 216 | 3742 | 888 | 1114 | -13 | 4474 | 2 | 220 |
| ob15 | break | tsf_5_100 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1387 | -606 | 2004 | 999 | 2133 | 1 | 219 |
| ob15 | break_native | tsf_5_100 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1387 | -606 | 2004 | 999 | 2133 | 1 | 219 |
| ob15 | false_break | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 40 | 1707 | -322 | 1070 | -340 | 592 | 2 | 219 |
| ob15 | false_break_native | vsess_600 | {"M": 1, "k": 0.5} | sym8u / both | 43 | 1711 | -305 | 199 | -484 | 1741 | 2 | 219 |
| ob15 | reject | tsf_5_100 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 75 | 1671 | -77 | -655 | 150 | 2147 | 1 | 219 |
| ob15 | reject_native | vol_1100 | {"tol": 1.0, "conf": "body"} | sym8u / both | 69 | 1543 | -98 | -727 | 486 | 2295 | 2 | 219 |
| ob15 | retest | dltor_B200 | {"M": 6, "tol": 0.5} | sym15u / both | 47 | 1515 | -896 | 1313 | -912 | 1709 | 1 | 219 |
| ob15 | retest_native | dltor_B200 | {"M": 10, "tol": 0.5} | plain60/60 / both | 86 | 1652 | -482 | 1035 | -2144 | 1625 | 1 | 219 |
| ob5 | break | urenko_10 | {"n": 3, "k": 0.0} | sym15u / both | 81 | 2406 | -812 | 353 | 27 | 2783 | 2 | 220 |
| ob5 | break_native | urenko_10 | {"n": 3, "k": 0.0} | sym15u / both | 81 | 2406 | -812 | 353 | 27 | 2783 | 2 | 220 |
| ob5 | false_break | tsf_10_120 | {"M": 1, "k": 0.0} | sym15u / both | 57 | 2154 | -368 | 515 | 931 | 2532 | 1 | 220 |
| ob5 | false_break_native | tsf_10_30 | {"M": 2, "k": 0.5} | sym15u / both | 58 | 2155 | 526 | 884 | 2781 | 2434 | 1 | 220 |
| ob5 | reject | renko_20 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 38 | 1701 | -586 | -5 | -891 | 1392 | 2 | 220 |
| ob5 | reject_native | renko_20 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 63 | 1876 | -654 | 399 | 1261 | 2421 | 2 | 220 |
| ob5 | retest | rng_10 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 82 | 2651 | -343 | 927 | 1549 | 3506 | 2 | 220 |
| ob5 | retest_native | rng_10 | {"M": 10, "tol": 0.5} | sym30u / both | 68 | 2555 | 59 | 406 | 2169 | 3721 | 2 | 220 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 326 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 326 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym15u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 1 | 326 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 326 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "body"} | sym30u / both | 212 | 4049 | -262 | 1287 | 558 | 2187 | 2 | 326 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "body"} | sym30u / both | 212 | 4049 | -262 | 1287 | 558 | 2187 | 2 | 326 |
| open_range | retest | vib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 227 | 3820 | -1654 | 280 | 218 | 3319 | 1 | 326 |
| open_range | retest_native | vfp_vol1000 | {"M": 10, "tol": 0.5} | sym15u / both | 226 | 3732 | -1504 | -416 | 1816 | 6180 | 1 | 326 |
| opens | break | time_s_15 | {"n": 1, "k": 0.5} | sym15u / both | 197 | 2969 | 256 | -555 | -115 | 4112 | 2 | 326 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 326 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 326 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 326 |
| opens | reject | cusum_10 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 177 | 2958 | 486 | 88 | 732 | 3754 | 2 | 326 |
| opens | reject_native | cusum_10 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 177 | 2958 | 486 | 88 | 732 | 3754 | 2 | 326 |
| opens | retest | dol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 124 | 3757 | -579 | 363 | -1171 | 2413 | 1 | 326 |
| opens | retest_native | dol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 124 | 3757 | -579 | 363 | -1171 | 2413 | 1 | 326 |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 2 | 327 |
| prior_day | break_native | vib_15000 | {"n": 1, "k": 0.0} | sym15u / both | 89 | 3202 | -185 | -1001 | -2436 | 3301 | 1 | 327 |
| prior_day | false_break | vib_15000 | {"M": 3, "k": 0.5} | sym15u / both | 88 | 2976 | -294 | -308 | -2832 | 2657 | 1 | 327 |
| prior_day | false_break_native | trb_1200 | {"M": 3, "k": 0.5} | sym15u / both | 87 | 2890 | -317 | 530 | -1790 | 2494 | 1 | 327 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 327 |
| prior_day | reject_native | anch_N0930_B50 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 253 | 2826 | 393 | -1113 | -1711 | 3045 | 1 | 327 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 1 | 327 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 1 | 327 |
| profile_nodes | break | dltor_B080 | {"n": 3, "k": 0.5} | sym15u / both | 134 | 2491 | -196 | 1864 | -3075 | 1897 | 1 | 326 |
| profile_nodes | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 146 | 2992 | -647 | 1127 | -2618 | 2123 | 1 | 326 |
| profile_nodes | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 180 | 2054 | -1160 | -714 | -3668 | 2648 | 2 | 326 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 326 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 326 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 326 |
| profile_nodes | retest | trb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 181 | 2629 | -801 | 1854 | -941 | 2491 | 1 | 326 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 128 | 2802 | -508 | 830 | -3084 | 3094 | 1 | 326 |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 93 | 2285 | -957 | 2055 | -845 | 2570 | 2 | 327 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 327 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 327 |
| profile_va | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 113 | 1975 | -1229 | 386 | -282 | 2315 | 1 | 327 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 327 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 327 |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 327 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 327 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 290 | 4837 | -1805 | 1243 | 3655 | 5119 | 1 | 431 |
| round | break_native | sessrng_B080 | {"n": 2, "k": 0.25} | sym15u / both | 290 | 4406 | -487 | 2662 | 2387 | 4824 | 1 | 431 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 431 |
| round | false_break_native | urenko_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 965 | 4358 | -1829 | -1460 | 284 | 6297 | 1 | 431 |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 2 | 431 |
| round | reject_native | qmid_B130 | {"tol": 1.0, "conf": "body"} | sym15u / both | 332 | 5382 | 1274 | 778 | -622 | 5313 | 1 | 431 |
| round | retest | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 302 | 4728 | -399 | 513 | -1661 | 5351 | 2 | 431 |
| round | retest_native | qmid_B500 | {"M": 10, "tol": 0.5} | sym15u / both | 333 | 5018 | 731 | -988 | 116 | 3423 | 1 | 431 |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 171 | 3430 | -820 | 2114 | -94 | 2764 | 1 | 325 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 325 |
| session_hl | false_break | time_s_20 | {"M": 1, "k": 0.5} | sym30u / short | 94 | 3320 | 541 | -878 | 1725 | 3900 | 2 | 325 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 325 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 1 | 325 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 325 |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 95 | 3205 | -819 | -845 | -75 | 4545 | 2 | 325 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 325 |
| trendline | break | rng_10 | {"n": 3, "k": 0.5} | sym30u / both | 234 | 3451 | 2114 | 2406 | 4533 | 3920 | 2 | 215 |
| trendline | break_native | kagi_14 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 3812 | 1332 | 2406 | 3337 | 5866 | 1 | 215 |
| trendline | false_break | renko_20 | {"M": 1, "k": 0.5} | sym15u / both | 228 | 3494 | 132 | -1254 | -1369 | 5819 | 2 | 215 |
| trendline | false_break_native | tm1200 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 3271 | -358 | -1129 | 1385 | 3744 | 1 | 215 |
| trendline | reject | dol_1100 | {"tol": 1.0, "conf": "body"} | sym8u / both | 229 | 2960 | 291 | 3662 | 3113 | 2789 | 2 | 215 |
| trendline | reject_native | dol_1100 | {"tol": 1.0, "conf": "body"} | sym8u / both | 258 | 4196 | 625 | 3412 | 3413 | 3359 | 2 | 215 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 215 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 215 |
| uw_dp | break | vib_40000 | {"n": 2, "k": 0.25} | sym15u / both | 58 | 2267 | 0 | 0 | 169 | 1987 | 1 | 326 |
| uw_dp | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 61 | 2272 | 0 | 0 | 421 | 2655 | 1 | 326 |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1430 | 0 | 0 | 210 | 1085 | 1 | 326 |
| uw_dp | false_break_native | vsess_600 | {"M": 2, "k": 0.5} | asym20u/10u / both | 64 | 1601 | 0 | 0 | -396 | 1813 | 2 | 326 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 74 | 1508 | 0 | 0 | -241 | 886 | 1 | 326 |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 92 | 2286 | 0 | 0 | -217 | 1948 | 2 | 326 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 56 | 1926 | 0 | 0 | 295 | 2044 | 1 | 326 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 326 |
| uw_ndx | break | rngor_B080 | {"n": 2, "k": 0.25} | sym15u / both | 87 | 2387 | 0 | 72 | -11 | 1547 | 1 | 325 |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 102 | 2167 | 0 | -30 | -1920 | 1473 | 2 | 325 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 325 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 325 |
| uw_ndx | reject | trend_28 | {"tol": 0.0, "conf": "close"} | sym15u / both | 84 | 2097 | 0 | -307 | 2131 | 1969 | 1 | 325 |
| uw_ndx | reject_native | trend_28 | {"tol": 0.0, "conf": "close"} | sym15u / both | 84 | 2097 | 0 | -307 | 2131 | 1969 | 1 | 325 |
| uw_ndx | retest | tib_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 90 | 2531 | 0 | -546 | -895 | 2819 | 1 | 325 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 110 | 2464 | 0 | -631 | 475 | 2424 | 1 | 325 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 325 |
| uw_qqq | break_native | renko_10 | {"n": 2, "k": 0.0} | sym8u / both | 261 | 1644 | 0 | -302 | -257 | 171 | 2 | 325 |
| uw_qqq | false_break | vrb_15000 | {"M": 2, "k": 0.5} | sym15u / both | 76 | 1780 | 0 | 278 | -1194 | 1849 | 1 | 325 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 325 |
| uw_qqq | reject | sessrng_B080 | {"tol": 1.0, "conf": "body"} | sym15u / both | 103 | 1629 | 0 | -698 | 81 | 2011 | 1 | 325 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 325 |
| uw_qqq | retest | tsf_10_30 | {"M": 6, "tol": 0.5} | sym15u / both | 88 | 1948 | 0 | 13 | -2008 | 771 | 1 | 325 |
| uw_qqq | retest_native | dchg_20 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1938 | 0 | 452 | -985 | 1145 | 1 | 325 |
| vwap | break | renko_40 | {"n": 1, "k": 0.25} | sym8u / both | 149 | 3681 | -1617 | 765 | 724 | 2951 | 2 | 325 |
| vwap | break_native | tm60 | {"n": 1, "k": 0.25} | sym8u / both | 179 | 4235 | -1369 | 181 | 2368 | 5194 | 2 | 325 |
| vwap | false_break | dib_400 | {"M": 1, "k": 0.5} | sym30u / both | 182 | 3516 | -173 | -88 | 1389 | 3720 | 2 | 325 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 325 |
| vwap | reject | dib_400 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 482 | 2935 | -127 | -273 | 296 | 2916 | 2 | 325 |
| vwap | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 485 | 2414 | 212 | 64 | 1493 | 3582 | 2 | 325 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 325 |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 171 | 4078 | 605 | -156 | 1901 | 3767 | 2 | 325 |
| vwap_bands | break | tib_1200 | {"n": 2, "k": 0.0} | sym30u / both | 255 | 4129 | -1610 | 2277 | 1185 | 5000 | 2 | 325 |
| vwap_bands | break_native | tib_1200 | {"n": 2, "k": 0.0} | sym30u / both | 255 | 4129 | -1610 | 2277 | 1185 | 5000 | 2 | 325 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 325 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 325 |
| vwap_bands | reject | tm15 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 342 | 4292 | -31 | -470 | 1482 | 2814 | 2 | 325 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 325 |
| vwap_bands | retest | tib_700 | {"M": 6, "tol": 0.0} | sym15u / both | 374 | 4322 | -815 | 336 | 467 | 3470 | 2 | 325 |
| vwap_bands | retest_native | tib_700 | {"M": 6, "tol": 0.0} | sym15u / both | 374 | 4322 | -815 | 336 | 467 | 3470 | 2 | 325 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym15u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 1 | 326 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 326 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 326 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 326 |
| week_month | reject | tsf_2_1200 | {"tol": 0.0, "conf": "close"} | sym15u / both | 42 | 1983 | -358 | -597 | 503 | 1654 | 1 | 326 |
| week_month | reject_native | trb_10000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 68 | 2713 | -386 | -893 | -814 | 2837 | 1 | 326 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 326 |
| week_month | retest_native | vrb_6000 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1755 | -436 | -491 | -744 | 2508 | 1 | 326 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 325 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 325 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 325 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 325 |
| zones | reject | tib_1200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 154 | 3694 | -964 | -900 | 240 | 4120 | 2 | 325 |
| zones | reject_native | tib_1200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 157 | 3134 | -1438 | -259 | 770 | 3260 | 2 | 325 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 325 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 325 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | dchg_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 486 | -54 | -16 | 717 | 995 | 1 | 289 |
| sd5 | break_native | dchg_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 486 | -54 | -16 | 717 | 995 | 1 | 289 |
| sd5 | reject | time_m_10 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 400 | -299 | 61 | 34 | 638 | 1 | 289 |
| sd5 | reject_native | time_m_10 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 400 | -299 | 61 | 34 | 638 | 1 | 289 |
| sdx15 | break | urenko_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 70 | 1077 | -200 | -153 | 1318 | 1345 | 1 | 289 |
| sdx15 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 303 | 3630 | -249 | -670 | -1170 | 3468 | 1 | 289 |
| sdx15 | lim_prox | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 271 | 3613 | 443 | 1635 | -503 | 3126 | 1 | 289 |
| sdx15 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 98 | 2164 | 235 | -369 | -1160 | 1645 | 1 | 289 |
| sdx15 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / both | 111 | 2275 | 39 | -418 | -673 | 3243 | 1 | 289 |
| sdx15 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 289 |
| sdx15 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 289 |
| sdx15 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 58 | 532 | -167 | -117 | 90 | 610 | 1 | 289 |
| sdx3 | break | wrenko_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 174 | 2989 | -298 | 492 | 507 | 2803 | 1 | 289 |
| sdx3 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 4777 | -1113 | 1932 | -2887 | 3527 | 1 | 289 |
| sdx3 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1050 | 6224 | -119 | -224 | -2213 | 5021 | 1 | 289 |
| sdx3 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 305 | 3708 | -457 | -454 | -1839 | 2258 | 1 | 289 |
| sdx3 | rej_flow | vrb_240 | {"d": "A", "F": 0} | sym15u / both | 203 | 1376 | 200 | -1655 | 983 | 3364 | 1 | 289 |
| sdx3 | rej_native | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 289 |
| sdx3 | rej_zone | cusum_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 466 | 5203 | -382 | -1657 | 232 | 3715 | 1 | 289 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 289 |
| sdx30 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 43 | 796 | -102 | 249 | 541 | 651 | 1 | 290 |
| sdx30 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 206 | 3133 | -150 | -817 | -949 | 1695 | 1 | 290 |
| sdx30 | lim_prox | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 232 | 3270 | -189 | -1338 | -13 | 2950 | 1 | 290 |
| sdx30 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 159 | 1658 | 62 | -1293 | -821 | 349 | 1 | 290 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 44 | 1278 | -32 | -42 | -652 | 899 | 1 | 290 |
| sdx30 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 290 |
| sdx30 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 290 |
| sdx5 | break | urenko_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 113 | 2472 | -146 | -590 | 1239 | 2914 | 1 | 289 |
| sdx5 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 434 | 4411 | -88 | -1705 | -1193 | 3777 | 1 | 289 |
| sdx5 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 360 | 5056 | 283 | 711 | -1448 | 2414 | 1 | 289 |
| sdx5 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 258 | 5300 | -710 | -111 | -394 | 5406 | 1 | 289 |
| sdx5 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 213 | 2801 | 412 | -179 | -668 | 1032 | 1 | 289 |
| sdx5 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 284 | 4619 | -598 | -24 | -1073 | 5324 | 1 | 289 |
| sdx5 | rej_zone | vib_25000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 388 | 3835 | -539 | 298 | -234 | 3281 | 1 | 289 |
| sdx5 | retest | kagi_40 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / short | 93 | 1465 | -6 | -476 | -174 | 1868 | 1 | 289 |
| sdx60 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 246 | -54 | 16 | 405 | -586 | 1 | 289 |
| sdx60 | lim_mid | urenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 144 | 1330 | 181 | -523 | -342 | 1028 | 1 | 289 |
| sdx60 | lim_prox | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 87 | 1502 | -62 | -1032 | -516 | 1170 | 1 | 289 |
| sdx60 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 46 | 2005 | -46 | -249 | 40 | 1993 | 1 | 289 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | sym15u / short | 30 | 913 | 12 | -370 | -367 | 777 | 1 | 289 |
| sdx60 | rej_native | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 56 | 2048 | -3 | -244 | -270 | 2246 | 1 | 289 |
| sdx60 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 64 | 1710 | 25 | -264 | -895 | 1797 | 1 | 289 |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 182 | 3218 | 348 | 613 | 1501 | 3608 | 1 | 288 |
| sdx_renko28 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 335 | 3926 | -225 | -191 | -3870 | 3498 | 1 | 288 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 332 | 3491 | 102 | -741 | -4298 | 1272 | 1 | 288 |
| sdx_renko28 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 289 | 2322 | -347 | -2305 | -1815 | 504 | 1 | 288 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 105 | 2509 | -260 | -487 | -1295 | 1700 | 1 | 288 |
| sdx_renko28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 308 | 2821 | -262 | -1656 | -4365 | 1021 | 1 | 288 |
| sdx_renko28 | rej_zone | rng_10 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 715 | 3555 | 4 | -615 | -2122 | 2404 | 1 | 288 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2189 | 230 | -226 | -1251 | 1966 | 1 | 288 |
| sdx_rng28 | break | mrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 803 | 5407 | 129 | 1213 | -529 | 4740 | 1 | 288 |
| sdx_rng28 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 386 | 3058 | -130 | 896 | 302 | 1004 | 1 | 288 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 288 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 180 | 4551 | 663 | 859 | -858 | 6367 | 1 | 288 |
| sdx_rng28 | rej_flow | vrb_400 | {"d": "E", "F": 0} | sym15u / both | 238 | 2255 | -129 | -737 | -175 | 2887 | 1 | 288 |
| sdx_rng28 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 817 | 2929 | -775 | -407 | -1591 | 2117 | 1 | 288 |
| sdx_rng28 | rej_zone | dol_350 | {"d": "E", "F": 0, "tgt": "r2"} | OWN zone/level bracket / both | 1583 | 3991 | -425 | -288 | -2143 | 2791 | 2 | 288 |
| sdx_rng28 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 447 | 3522 | -103 | 677 | -611 | 2695 | 1 | 288 |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 392 | 3031 | 130 | 198 | 714 | 2880 | 1 | 288 |
| sdx_vol1100 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 351 | 3043 | -308 | 140 | -2784 | 1952 | 1 | 288 |
| sdx_vol1100 | lim_prox | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 334 | 4466 | -175 | -58 | -998 | 5680 | 1 | 288 |
| sdx_vol1100 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 200 | 3099 | -487 | 66 | -2363 | 3160 | 1 | 288 |
| sdx_vol1100 | rej_flow | dol_6000 | {"d": "E", "F": 9} | plain60/60 / both | 204 | 2004 | -631 | 200 | -652 | 1775 | 1 | 288 |
| sdx_vol1100 | rej_native | kagi_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 292 | 3389 | -344 | -1220 | -2227 | 4421 | 1 | 288 |
| sdx_vol1100 | rej_zone | cusum_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 306 | 3386 | -436 | -440 | -706 | 2776 | 1 | 288 |
| sdx_vol1100 | retest | urenko_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 273 | 2414 | 61 | -321 | 464 | 2757 | 1 | 288 |
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 664 | 4358 | 1020 | 111 | 108 | 5473 | 1 | 289 |
| fib15 | break_native | vol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 445 | 3679 | -182 | 435 | 199 | 3816 | 1 | 289 |
| fib15 | false_break | time_s_15 | {"M": 1, "k": 0.0} | sym15u / both | 744 | 4428 | -1523 | -1122 | -984 | 4812 | 1 | 289 |
| fib15 | false_break_native | time_s_15 | {"M": 1, "k": 0.0} | sym15u / both | 744 | 4428 | -1523 | -1122 | -984 | 4812 | 1 | 289 |
| fib15 | pullback | vsess_50 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 318 | 3324 | -457 | -527 | 77 | 2115 | 1 | 289 |
| fib15 | pullback_native | vsess_50 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 356 | 3930 | -915 | 75 | 7 | 2275 | 1 | 289 |
| fib15 | reject | cusum_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 693 | 3298 | -110 | -69 | 2021 | 3121 | 1 | 289 |
| fib15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 3684 | 770 | -1991 | 1912 | 3118 | 1 | 289 |
| fib15 | retest | cusum_80 | {"M": 6, "tol": 0.5} | sym15u / both | 224 | 3983 | -247 | 278 | 481 | 3510 | 1 | 289 |
| fib15 | retest_native | tm45 | {"M": 6, "tol": 0.5} | sym15u / both | 347 | 4680 | -438 | -1393 | -873 | 4139 | 1 | 289 |
| fib5 | break | vol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 491 | 3973 | 91 | 1547 | 4 | 5198 | 1 | 290 |
| fib5 | break_native | cusum_56 | {"n": 2, "k": 0.25} | sym15u / both | 298 | 4186 | 261 | 1556 | 413 | 6989 | 1 | 290 |
| fib5 | false_break | vsess_30 | {"M": 3, "k": 0.5} | sym15u / both | 319 | 4950 | 305 | -527 | 1711 | 5618 | 1 | 290 |
| fib5 | false_break_native | vol_4000 | {"M": 1, "k": 0.0} | sym15u / both | 294 | 4515 | -170 | 1754 | 1432 | 4673 | 1 | 290 |
| fib5 | pullback | vsess_300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 432 | 4321 | -117 | -2350 | -621 | 3568 | 2 | 290 |
| fib5 | pullback_native | vsess_300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 432 | 4321 | -117 | -2350 | -621 | 3568 | 2 | 290 |
| fib5 | reject | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 229 | 4892 | 475 | 656 | -543 | 5747 | 1 | 290 |
| fib5 | reject_native | rng_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 280 | 4572 | -215 | 889 | -1110 | 4953 | 1 | 290 |
| fib5 | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 290 |
| fib5 | retest_native | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 290 |
| fib60 | break | vol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 562 | 4258 | -69 | -393 | -103 | 3678 | 1 | 290 |
| fib60 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 556 | 4408 | -100 | 188 | -541 | 3433 | 1 | 290 |
| fib60 | false_break | lbrk_5_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 360 | 3487 | 195 | 1384 | 3 | 4074 | 1 | 290 |
| fib60 | false_break_native | vib_400 | {"M": 3, "k": 0.5} | sym15u / both | 432 | 3687 | 162 | -402 | 1352 | 4173 | 1 | 290 |
| fib60 | pullback | tsf_10_30 | {"tol": 0.5, "conf": "body"} | sym15u / both | 96 | 2647 | 307 | -270 | -1301 | 2451 | 1 | 290 |
| fib60 | pullback_native | mom_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 190 | 2738 | 33 | 315 | 981 | 2462 | 1 | 290 |
| fib60 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 279 | 5055 | 422 | -1153 | -276 | 5536 | 2 | 290 |
| fib60 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 283 | 4177 | 118 | -368 | -74 | 5093 | 2 | 290 |
| fib60 | retest | tib_1200 | {"M": 10, "tol": 0.5} | plain60/60 / both | 501 | 2949 | -219 | 915 | -1997 | 2604 | 1 | 290 |
| fib60 | retest_native | vol_750 | {"M": 10, "tol": 0.5} | plain60/60 / both | 499 | 3584 | -227 | -506 | -608 | 4451 | 1 | 290 |
| fibr_dev | break | lbrk_4_10 | {"n": 2, "k": 0.25} | sym15u / both | 422 | 3223 | -240 | -36 | -1607 | 3020 | 1 | 180 |
| fibr_dev | break_native | lbrk_4_10 | {"n": 2, "k": 0.25} | sym15u / both | 424 | 3346 | 5 | -87 | -1048 | 3296 | 1 | 180 |
| fibr_dev | false_break | tsf_10_120 | {"M": 2, "k": 0.5} | plain60/60 / both | 466 | 3802 | -217 | 820 | 1602 | 4205 | 1 | 180 |
| fibr_dev | false_break_native | tsf_10_120 | {"M": 3, "k": 0.5} | plain60/60 / both | 443 | 3564 | -433 | 665 | 1357 | 3618 | 1 | 180 |
| fibr_dev | reject | renko_20 | {"tol": 1.0, "conf": "body"} | sym8u / both | 308 | 4073 | 74 | 498 | -4250 | 4261 | 2 | 180 |
| fibr_dev | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 4083 | -588 | 684 | -1434 | 4699 | 1 | 180 |
| fibr_dev | retest | vsess_600 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 451 | 3650 | -953 | 488 | 357 | 4432 | 2 | 180 |
| fibr_dev | retest_native | cusum_80 | {"M": 10, "tol": 0.5} | sym15u / both | 283 | 4101 | 204 | 806 | -133 | 4885 | 1 | 180 |
| fibr_ib | break | tsf_10_120 | {"n": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 178 |
| fibr_ib | break_native | tsf_10_120 | {"n": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 178 |
| fibr_ib | false_break | tsf_10_120 | {"M": 2, "k": 0.5} | plain60/60 / both | 68 | 1379 | -258 | 295 | 300 | 1679 | 1 | 178 |
| fibr_ib | false_break_native | tsf_10_120 | {"M": 1, "k": 0.0} | plain60/60 / both | 69 | 1378 | -230 | 257 | 192 | 1556 | 1 | 178 |
| fibr_ib | reject | dol_4000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 41 | 1278 | -10 | -297 | -159 | 1611 | 1 | 178 |
| fibr_ib | reject_native | dol_4000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 49 | 1484 | 108 | -227 | -662 | 1896 | 1 | 178 |
| fibr_ib | retest | time_m_60 | {"M": 10, "tol": 0.5} | sym15u / both | 64 | 1297 | 251 | 154 | -263 | 1402 | 1 | 178 |
| fibr_ib | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 60 | 1416 | 2 | -1461 | -161 | 2126 | 1 | 178 |
| fibr_on | break | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 64 | 1852 | 130 | 1064 | 1266 | 2317 | 1 | 180 |
| fibr_on | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 64 | 1852 | 130 | 1064 | 1266 | 2317 | 1 | 180 |
| fibr_on | false_break | vib_70000 | {"M": 2, "k": 0.5} | sym15u / both | 63 | 1972 | 4 | 965 | 1280 | 2438 | 1 | 180 |
| fibr_on | false_break_native | vib_70000 | {"M": 3, "k": 0.5} | sym15u / both | 59 | 1909 | 61 | 856 | 1398 | 2451 | 1 | 180 |
| fibr_on | reject | trb_10000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 51 | 1325 | 37 | 188 | 90 | 1432 | 1 | 180 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 1 | 180 |
| fibr_on | retest | time_m_60 | {"M": 10, "tol": 0.5} | sym15u / both | 50 | 1320 | 338 | 170 | -197 | 1798 | 1 | 180 |
| fibr_on | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 50 | 1220 | -2 | 140 | 639 | 1292 | 1 | 180 |
| fibr_or | break | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 352 | 342 | 362 | 760 | 1 | 176 |
| fibr_or | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 352 | 342 | 362 | 760 | 1 | 176 |
| fibr_or | false_break | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 353 | 342 | 362 | 760 | 1 | 176 |
| fibr_or | false_break_native | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 72 | 1254 | 353 | 342 | 362 | 760 | 1 | 176 |
| fibr_or | reject | tsf_10_250 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1219 | -13 | -154 | -144 | 1109 | 1 | 176 |
| fibr_or | reject_native | pasl_28 | {"tol": 0.5, "conf": "close"} | sym8u / both | 46 | 1249 | -196 | 286 | -615 | 1305 | 2 | 176 |
| fibr_or | retest | urenko_80 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1143 | 260 | -956 | -170 | 1606 | 1 | 176 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 1 | 176 |
| fibr_pd | break | time_s_30 | {"n": 2, "k": 0.25} | sym15u / both | 410 | 4761 | -249 | 214 | -617 | 3932 | 1 | 177 |
| fibr_pd | break_native | vsess_300 | {"n": 2, "k": 0.25} | sym15u / both | 336 | 5148 | -2 | 640 | 314 | 4926 | 1 | 177 |
| fibr_pd | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 678 | 3579 | -1005 | -279 | 981 | 5723 | 1 | 177 |
| fibr_pd | false_break_native | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 666 | 3464 | -1047 | -220 | 995 | 5358 | 1 | 177 |
| fibr_pd | reject | rng_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 368 | 5269 | -338 | -243 | -2927 | 4463 | 2 | 177 |
| fibr_pd | reject_native | tsf_2_100 | {"tol": 1.0, "conf": "body"} | sym15u / both | 321 | 4598 | -132 | -1095 | -956 | 6235 | 1 | 177 |
| fibr_pd | retest | rng_10 | {"M": 10, "tol": 0.5} | sym15u / both | 335 | 4058 | -172 | -789 | -1006 | 2492 | 2 | 177 |
| fibr_pd | retest_native | dchg_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 686 | 3118 | 314 | 267 | 806 | 3299 | 1 | 177 |
| piv_cama | break | dol_1100 | {"n": 1, "k": 0.0} | plain60/60 / both | 676 | 4396 | 242 | 1245 | -711 | 4607 | 1 | 179 |
| piv_cama | break_native | dol_1100 | {"n": 1, "k": 0.0} | plain60/60 / both | 676 | 4396 | 242 | 1245 | -711 | 4607 | 1 | 179 |
| piv_cama | false_break | time_s_30 | {"M": 1, "k": 0.0} | plain60/60 / both | 766 | 4130 | -895 | -471 | -1584 | 4785 | 1 | 179 |
| piv_cama | false_break_native | time_s_30 | {"M": 1, "k": 0.0} | plain60/60 / both | 766 | 4130 | -895 | -471 | -1584 | 4785 | 1 | 179 |
| piv_cama | reject | tsf_10_30 | {"tol": 0.5, "conf": "body"} | sym15u / both | 257 | 3915 | 292 | 193 | 1382 | 3245 | 1 | 179 |
| piv_cama | reject_native | vrb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 343 | 3789 | -60 | -267 | -488 | 5147 | 1 | 179 |
| piv_cama | retest | time_s_5 | {"M": 3, "tol": 0.0} | plain60/60 / both | 680 | 3103 | -298 | -1435 | -718 | 4537 | 1 | 179 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 1 | 179 |
| piv_floor | break | vsess_600 | {"n": 1, "k": 0.0} | sym30u / both | 251 | 3905 | -833 | 175 | 869 | 4380 | 2 | 177 |
| piv_floor | break_native | vsess_600 | {"n": 1, "k": 0.0} | sym30u / both | 251 | 3905 | -833 | 175 | 869 | 4380 | 2 | 177 |
| piv_floor | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 552 | 3654 | -727 | -863 | 251 | 3755 | 1 | 177 |
| piv_floor | false_break_native | vsess_600 | {"M": 2, "k": 0.5} | sym8u / both | 505 | 4114 | -1401 | -606 | 320 | 3891 | 2 | 177 |
| piv_floor | reject | time_m_13 | {"tol": 0.5, "conf": "body"} | sym15u / both | 175 | 2989 | 709 | -2785 | -305 | 2717 | 1 | 177 |
| piv_floor | reject_native | lbrk_4_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 167 | 2874 | 86 | -19 | -362 | 4378 | 1 | 177 |
| piv_floor | retest | cusum_10 | {"M": 6, "tol": 0.5} | sym30u / both | 227 | 3896 | -85 | 378 | -1236 | 4849 | 2 | 177 |
| piv_floor | retest_native | cusum_10 | {"M": 6, "tol": 0.5} | sym30u / both | 227 | 4039 | -265 | 182 | -1498 | 4992 | 2 | 177 |
| piv_wf | break | vsess_600 | {"n": 1, "k": 0.25} | asym20u/10u / both | 387 | 3702 | -495 | -808 | -136 | 3606 | 2 | 178 |
| piv_wf | break_native | vsess_600 | {"n": 1, "k": 0.25} | asym20u/10u / both | 383 | 3937 | -644 | -270 | 86 | 4247 | 2 | 178 |
| piv_wf | false_break | mom_80 | {"M": 1, "k": 0.0} | plain60/60 / both | 463 | 3491 | -457 | 754 | 1343 | 3641 | 1 | 178 |
| piv_wf | false_break_native | trb_400 | {"M": 3, "k": 0.5} | sym15u / both | 316 | 3723 | -1249 | -1651 | 2310 | 4403 | 1 | 178 |
| piv_wf | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 605 | 3469 | 170 | -811 | -3847 | 2254 | 1 | 178 |
| piv_wf | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 312 | 3881 | 154 | -858 | -2214 | 3109 | 1 | 178 |
| piv_wf | retest | vsess_600 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 331 | 3266 | -887 | 93 | 2384 | 1349 | 2 | 178 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 1 | 178 |
| swcluster | break | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 58 | 1626 | -278 | 139 | 621 | 1919 | 2 | 180 |
| swcluster | break_native | rng_10 | {"n": 2, "k": 0.0} | sym30u / both | 53 | 1481 | -377 | 118 | 715 | 2511 | 2 | 180 |
| swcluster | false_break | pnf_7 | {"M": 1, "k": 0.0} | asym20u/10u / both | 67 | 1322 | -172 | -259 | 1217 | 2014 | 2 | 180 |
| swcluster | false_break_native | tm900 | {"M": 2, "k": 0.5} | sym15u / both | 52 | 1528 | -94 | 350 | 392 | 2188 | 1 | 180 |
| swcluster | reject | vsess_300 | {"tol": 0.5, "conf": "body"} | sym15u / short | 34 | 1109 | 190 | -478 | 199 | 1085 | 1 | 180 |
| swcluster | reject_native | tsf_5_100 | {"tol": 0.5, "conf": "body"} | sym15u / both | 52 | 1389 | 78 | -389 | -349 | 1565 | 1 | 180 |
| swcluster | retest | rng_10 | {"M": 3, "tol": 0.5} | sym30u / both | 51 | 1713 | -60 | -4 | -401 | 2510 | 2 | 180 |
| swcluster | retest_native | rng_10 | {"M": 3, "tol": 0.5} | sym30u / both | 50 | 1525 | -73 | -93 | -369 | 2322 | 2 | 180 |
| swsr15 | break | renko_20 | {"n": 3, "k": 0.0} | plain60/60 / both | 597 | 2916 | -617 | 1464 | -139 | 3725 | 2 | 179 |
| swsr15 | break_native | vsess_600 | {"n": 1, "k": 0.25} | sym15u / both | 392 | 3619 | 209 | -1220 | -45 | 3614 | 2 | 179 |
| swsr15 | false_break | vsess_600 | {"M": 1, "k": 0.5} | sym8u / both | 583 | 3214 | -850 | -1721 | -1551 | 2513 | 2 | 179 |
| swsr15 | false_break_native | pnf_7 | {"M": 1, "k": 0.5} | sym8u / both | 325 | 3478 | 939 | -110 | -62 | 4603 | 2 | 179 |
| swsr15 | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 301 | 3075 | -273 | -553 | -612 | 4062 | 1 | 179 |
| swsr15 | reject_native | frenko_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 508 | 3389 | -699 | 719 | 400 | 3238 | 1 | 179 |
| swsr15 | retest | rng_10 | {"M": 3, "tol": 0.0} | sym30u / both | 266 | 4207 | -210 | 104 | 227 | 3584 | 2 | 179 |
| swsr15 | retest_native | rng_10 | {"M": 3, "tol": 0.0} | sym30u / both | 266 | 4207 | -210 | 104 | 227 | 3584 | 2 | 179 |
| swsr5 | break | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 264 | 4318 | -263 | 1632 | 102 | 6294 | 2 | 181 |
| swsr5 | break_native | renko_20 | {"n": 1, "k": 0.25} | sym15u / both | 334 | 3919 | 164 | -878 | 809 | 4919 | 2 | 181 |
| swsr5 | false_break | vsess_600 | {"M": 1, "k": 0.5} | asym10u/20u / both | 517 | 4337 | -563 | 32 | -2004 | 3797 | 2 | 181 |
| swsr5 | false_break_native | pasl_14 | {"M": 1, "k": 0.5} | sym15u / both | 328 | 3713 | -822 | 1370 | -2486 | 3352 | 2 | 181 |
| swsr5 | reject | dol_4000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 231 | 4164 | -78 | 1471 | -115 | 5699 | 1 | 181 |
| swsr5 | reject_native | tsf_10_120 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 425 | 3778 | 48 | 77 | 1211 | 5880 | 1 | 181 |
| swsr5 | retest | cusum_40 | {"M": 10, "tol": 0.5} | sym15u / both | 308 | 4720 | 678 | -490 | -858 | 6174 | 1 | 181 |
| swsr5 | retest_native | dol_1100 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 4139 | -379 | 437 | -908 | 4511 | 1 | 181 |
| swsr60 | break | vib_6000 | {"n": 2, "k": 0.25} | plain60/60 / both | 346 | 2294 | 78 | 371 | -335 | 2656 | 1 | 179 |
| swsr60 | break_native | tib_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 367 | 2149 | 397 | 325 | 1073 | 4245 | 1 | 179 |
| swsr60 | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 179 |
| swsr60 | false_break_native | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 179 |
| swsr60 | reject | vib_25000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 155 | 1692 | -192 | -218 | -887 | 887 | 1 | 179 |
| swsr60 | reject_native | drb_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 138 | 2419 | 2 | 356 | -367 | 2198 | 1 | 179 |
| swsr60 | retest | time_m_1 | {"M": 3, "tol": 0.0} | sym15u / both | 172 | 2338 | -260 | -260 | 1015 | 2495 | 1 | 179 |
| swsr60 | retest_native | time_m_1 | {"M": 3, "tol": 0.0} | sym15u / both | 172 | 2338 | -260 | -260 | 1015 | 2495 | 1 | 179 |
| stack | break | tib_6000 | {"k": 3, "cw": 1.0} | sym15u / both | 140 | 4296 | -317 | 381 | -84 | 3710 | 1 | 288 |
| stack | break_native | tib_400 | {"k": 3, "cw": 1.0} | sym15u / both | 265 | 4834 | 101 | 499 | 821 | 5224 | 1 | 288 |
| stack | reject | vib_1200 | {"k": 2, "cw": 0.5} | sym15u / both | 307 | 3285 | 128 | 404 | -2922 | 2044 | 1 | 288 |
| stack | reject_native | tick_300 | {"k": 2, "cw": 0.5} | asym10u/20u / both | 328 | 3179 | -205 | -945 | -3107 | 752 | 2 | 288 |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 791 | 86 | 772 | 1607 | 2 | 287 |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 841 | 86 | 772 | 1607 | 2 | 287 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 287 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 287 |
| book_walls | reject | vsess_600 | {"tol": 0.5, "conf": "body"} | sym30u / both | 90 | 1539 | 572 | -315 | 721 | 2091 | 2 | 287 |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1443 | 732 | 638 | 74 | 699 | 1 | 287 |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 899 | -1465 | 616 | 147 | 1417 | 1 | 287 |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 821 | -381 | -305 | -21 | 226 | 1 | 287 |
| book_walls_loose | break | time_s_15 | {"n": 2, "k": 0.5} | sym30u / both | 280 | 3637 | -506 | -90 | -1550 | 2337 | 2 | 289 |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 194 | 3527 | 411 | 137 | 581 | 4299 | 2 | 289 |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 1856 | -61 | -317 | 372 | 986 | 1 | 289 |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 62 | 1806 | 153 | -209 | 562 | 1133 | 1 | 289 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 332 | 3647 | -618 | -483 | -2918 | 4293 | 1 | 289 |
| book_walls_loose | reject_native | tm45 | {"tol": 1.0, "conf": "close"} | sym8u / both | 472 | 3369 | -1222 | -1894 | -1381 | 3326 | 2 | 289 |
| book_walls_loose | retest | time_s_15 | {"M": 6, "tol": 0.5} | asym15u/30u / both | 347 | 2857 | -1073 | -2456 | -2375 | 3612 | 2 | 289 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym30u / both | 268 | 2810 | 735 | -412 | -3504 | 3056 | 2 | 289 |
| channel | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 371 | 4780 | -1125 | 1735 | 903 | 5186 | 2 | 182 |
| channel | break_native | vsess_600 | {"n": 3, "k": 0.0} | asym10u/20u / both | 443 | 4615 | -940 | -1450 | 2199 | 5701 | 2 | 182 |
| channel | false_break | vib_15000 | {"M": 1, "k": 0.0} | sym15u / both | 295 | 5084 | 318 | 92 | 513 | 5119 | 1 | 182 |
| channel | false_break_native | vib_15000 | {"M": 1, "k": 0.0} | sym15u / both | 295 | 5084 | 318 | 92 | 513 | 5119 | 1 | 182 |
| channel | reject | vsess_600 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 357 | 5310 | -323 | -934 | -2058 | 4288 | 2 | 182 |
| channel | reject_native | vsess_600 | {"tol": 0.0, "conf": "close"} | asym15u/30u / both | 357 | 5310 | -323 | -934 | -2058 | 4288 | 2 | 182 |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 488 | 3847 | -658 | -725 | -31 | 3628 | 1 | 182 |
| channel | retest_native | vsess_600 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 357 | 4849 | -332 | -141 | 70 | 5483 | 2 | 182 |
| fvg15 | break | tsf_5_50 | {"n": 1, "k": 0.0} | sym15u / both | 171 | 4895 | 20 | -198 | 1446 | 5209 | 1 | 182 |
| fvg15 | break_native | tsf_5_50 | {"n": 1, "k": 0.0} | sym15u / both | 171 | 4895 | 20 | -198 | 1446 | 5209 | 1 | 182 |
| fvg15 | false_break | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 179 | 4460 | -421 | 153 | 1819 | 3544 | 1 | 182 |
| fvg15 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 172 | 4624 | -258 | 241 | 2280 | 3548 | 1 | 182 |
| fvg15 | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym15u / both | 208 | 3047 | -638 | -728 | 667 | 3182 | 2 | 182 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 192 | 3238 | -531 | 176 | 1230 | 3572 | 1 | 182 |
| fvg15 | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 4311 | -153 | 822 | -98 | 4262 | 1 | 182 |
| fvg15 | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 178 | 4081 | -555 | 1076 | -732 | 4005 | 1 | 182 |
| fvg5 | break | renko_20 | {"n": 2, "k": 0.0} | asym20u/10u / both | 249 | 4104 | 191 | 686 | 552 | 4433 | 2 | 179 |
| fvg5 | break_native | renko_20 | {"n": 2, "k": 0.0} | asym20u/10u / both | 249 | 4104 | 191 | 686 | 552 | 4433 | 2 | 179 |
| fvg5 | false_break | tick_2000 | {"M": 3, "k": 0.0} | sym8u / both | 178 | 3596 | -147 | 45 | -1120 | 3926 | 2 | 179 |
| fvg5 | false_break_native | vsess_600 | {"M": 2, "k": 0.5} | sym30u / both | 300 | 3753 | -427 | -164 | -1566 | 2286 | 2 | 179 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 179 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 179 |
| fvg5 | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3156 | -584 | -548 | -2079 | 4493 | 1 | 179 |
| fvg5 | retest_native | trend_10 | {"M": 6, "tol": 0.5} | sym15u / both | 271 | 3689 | -525 | -298 | -233 | 4918 | 1 | 179 |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 203 | 4918 | 175 | 1622 | -134 | 4280 | 2 | 290 |
| gaps | break_native | rng_14 | {"n": 2, "k": 0.25} | sym30u / both | 204 | 4873 | -73 | 1174 | -1762 | 5112 | 2 | 290 |
| gaps | false_break | swing_atr_0.15 | {"M": 1, "k": 0.0} | plain60/60 / both | 427 | 4246 | -448 | -197 | 465 | 5311 | 1 | 290 |
| gaps | false_break_native | swing_atr_0.15 | {"M": 1, "k": 0.0} | plain60/60 / both | 427 | 4246 | -448 | -197 | 465 | 5311 | 1 | 290 |
| gaps | reject | renko_14 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 165 | 2926 | -291 | -70 | 673 | 2969 | 2 | 290 |
| gaps | reject_native | renko_14 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 171 | 3622 | -453 | 303 | 1417 | 3943 | 2 | 290 |
| gaps | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 231 | 2841 | -237 | -914 | -2219 | 2400 | 2 | 290 |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2887 | -129 | 409 | 967 | 2191 | 1 | 290 |
| mmove | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 435 | 3665 | -890 | 1057 | -382 | 3746 | 2 | 183 |
| mmove | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 377 | 5162 | -997 | 528 | 750 | 4303 | 2 | 183 |
| mmove | false_break | tm780 | {"M": 1, "k": 0.0} | plain60/60 / both | 685 | 5305 | -588 | -1422 | 578 | 4075 | 1 | 183 |
| mmove | false_break_native | tm780 | {"M": 3, "k": 0.5} | plain60/60 / both | 665 | 5434 | -775 | -1525 | 280 | 4374 | 1 | 183 |
| mmove | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | sym30u / both | 271 | 4493 | -1188 | -913 | 4061 | 5600 | 2 | 183 |
| mmove | reject_native | vsess_600 | {"tol": 0.0, "conf": "body"} | sym30u / both | 271 | 4493 | -1188 | -913 | 4061 | 5600 | 2 | 183 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym8u / both | 280 | 4929 | 16 | 565 | 1548 | 5613 | 2 | 183 |
| mmove | retest_native | trend_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 413 | 4300 | 229 | 822 | -1006 | 5352 | 1 | 183 |
| ob15 | break | trb_6000 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1303 | 95 | 109 | 887 | 1710 | 1 | 182 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 1 | 182 |
| ob15 | false_break | tsf_10_60 | {"M": 1, "k": 0.0} | plain60/60 / both | 73 | 1300 | 306 | 173 | 921 | 1492 | 1 | 182 |
| ob15 | false_break_native | tsf_10_60 | {"M": 1, "k": 0.0} | plain60/60 / both | 73 | 1300 | 306 | 173 | 921 | 1492 | 1 | 182 |
| ob15 | reject | tm10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 118 | 1452 | -172 | -1035 | 384 | 1160 | 1 | 182 |
| ob15 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 79 | 1546 | -161 | -222 | 273 | 1825 | 1 | 182 |
| ob15 | retest | trb_2000 | {"M": 6, "tol": 0.5} | sym15u / both | 35 | 1683 | 45 | 174 | 651 | 1951 | 1 | 182 |
| ob15 | retest_native | rng_10 | {"M": 3, "tol": 0.0} | asym10u/20u / both | 57 | 1087 | 100 | 42 | 188 | 914 | 2 | 182 |
| ob5 | break | dol_1700 | {"n": 3, "k": 0.5} | sym15u / long | 78 | 2485 | 180 | 363 | 617 | 2419 | 1 | 183 |
| ob5 | break_native | vsess_30 | {"n": 1, "k": 0.5} | plain60/60 / both | 191 | 2419 | 11 | 381 | 560 | 3061 | 2 | 183 |
| ob5 | false_break | lbrk_3_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 169 | 2782 | -155 | -395 | 376 | 2558 | 2 | 183 |
| ob5 | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.5} | plain60/60 / both | 193 | 2283 | -258 | -394 | -88 | 3053 | 2 | 183 |
| ob5 | reject | vib_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 235 | 2424 | -172 | -1323 | -58 | 1963 | 1 | 183 |
| ob5 | reject_native | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 241 | 2766 | -174 | -303 | 752 | 2844 | 1 | 183 |
| ob5 | retest | dchg_28 | {"M": 6, "tol": 0.5} | sym15u / both | 114 | 2120 | -449 | -358 | 1878 | 1891 | 1 | 183 |
| ob5 | retest_native | pasl_28 | {"M": 3, "tol": 0.5} | sym8u / both | 101 | 2342 | -31 | 410 | 209 | 1534 | 2 | 183 |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 289 |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 53 | 1298 | 117 | 673 | 306 | 1466 | 2 | 289 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 289 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 289 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 289 |
| open_range | reject_native | dol_4000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1842 | -333 | 343 | -407 | 1712 | 1 | 289 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 289 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 289 |
| opens | break | vsess_600 | {"n": 2, "k": 0.0} | sym8u / both | 362 | 3575 | -134 | 94 | -503 | 3879 | 2 | 289 |
| opens | break_native | vsess_600 | {"n": 2, "k": 0.0} | sym8u / both | 362 | 3575 | -134 | 94 | -503 | 3879 | 2 | 289 |
| opens | false_break | vsess_600 | {"M": 1, "k": 0.0} | asym20u/10u / both | 278 | 3529 | -496 | 901 | 173 | 3200 | 2 | 289 |
| opens | false_break_native | vsess_600 | {"M": 1, "k": 0.0} | asym20u/10u / both | 278 | 3529 | -496 | 901 | 173 | 3200 | 2 | 289 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 289 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 289 |
| opens | retest | time_s_10 | {"M": 3, "tol": 0.5} | sym15u / both | 441 | 3671 | -253 | -100 | -1031 | 4725 | 2 | 289 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 289 |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 290 |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 290 |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 2 | 290 |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 2 | 290 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 290 |
| prior_day | reject_native | time_s_20 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 339 | 3195 | 212 | 105 | -860 | 2276 | 2 | 290 |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 2 | 290 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 290 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 289 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 289 |
| profile_nodes | false_break | vsess_300 | {"M": 1, "k": 0.5} | asym10u/20u / both | 329 | 4201 | -503 | -1129 | -328 | 5429 | 2 | 289 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 289 |
| profile_nodes | reject | vsess_600 | {"tol": 0.0, "conf": "body"} | asym10u/20u / both | 330 | 3914 | -616 | 124 | 44 | 3488 | 2 | 289 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 289 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 2 | 289 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | asym10u/20u / both | 312 | 4893 | -272 | -130 | 1463 | 6547 | 2 | 289 |
| profile_va | break | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 3734 | 98 | -1260 | -135 | 2075 | 1 | 290 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 290 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 2 | 290 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 2 | 290 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 290 |
| profile_va | reject_native | vnorm_1500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 257 | 4574 | -103 | -656 | -1855 | 4146 | 1 | 290 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 290 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 1 | 290 |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2 | 290 |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 2 | 290 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 290 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 290 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 290 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 290 |
| round | retest | trb_400 | {"M": 6, "tol": 0.5} | plain60/60 / both | 652 | 4376 | -446 | -203 | 687 | 3945 | 1 | 290 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 2 | 290 |
| session_hl | break | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 51 | 1192 | 231 | 534 | 88 | 618 | 1 | 288 |
| session_hl | break_native | vib_70000 | {"n": 1, "k": 0.0} | sym15u / both | 51 | 1192 | 231 | 534 | 88 | 618 | 1 | 288 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym15u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 1 | 288 |
| session_hl | false_break_native | vib_70000 | {"M": 1, "k": 0.0} | sym15u / both | 50 | 1312 | 222 | 534 | 143 | 739 | 1 | 288 |
| session_hl | reject | swing_pct_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 31 | 966 | 156 | 215 | 82 | 717 | 1 | 288 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 288 |
| session_hl | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 930 | 394 | -159 | 104 | 1490 | 1 | 288 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 1 | 288 |
| trendline | break | time_m_1 | {"n": 2, "k": 0.25} | sym15u / both | 337 | 5099 | -605 | -918 | -1394 | 6464 | 1 | 178 |
| trendline | break_native | kagi_20 | {"n": 2, "k": 0.0} | sym8u / both | 283 | 4663 | 661 | -560 | -799 | 2266 | 2 | 178 |
| trendline | false_break | vrb_1200 | {"M": 1, "k": 0.5} | sym8u / both | 322 | 5093 | -260 | 369 | 2446 | 4012 | 2 | 178 |
| trendline | false_break_native | vrb_1200 | {"M": 2, "k": 0.0} | sym8u / both | 334 | 4642 | -313 | 327 | 1910 | 3646 | 2 | 178 |
| trendline | reject | vrb_1200 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 253 | 3353 | -74 | 1221 | -97 | 3620 | 2 | 178 |
| trendline | reject_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 3233 | -304 | 1786 | -548 | 2457 | 1 | 178 |
| trendline | retest | kagi_20 | {"M": 10, "tol": 0.0} | sym15u / both | 269 | 4489 | -68 | -1301 | 1266 | 3849 | 2 | 178 |
| trendline | retest_native | kagi_20 | {"M": 10, "tol": 0.0} | sym15u / both | 269 | 4489 | -68 | -1301 | 1266 | 3849 | 2 | 178 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 287 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 287 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 287 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 287 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 287 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 1 | 287 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 287 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 287 |
| uw_ndx | break | renko_14 | {"n": 2, "k": 0.5} | sym8u / both | 331 | 2910 | 0 | -114 | 269 | 2774 | 2 | 288 |
| uw_ndx | break_native | vsess_600 | {"n": 1, "k": 0.25} | asym20u/10u / both | 310 | 3021 | 0 | 428 | -358 | 3622 | 2 | 288 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 288 |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 296 | 2751 | 0 | 605 | 329 | 2931 | 2 | 288 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 288 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 288 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 288 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 288 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 288 |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 444 | 3333 | 0 | 825 | 798 | 2619 | 2 | 288 |
| uw_qqq | false_break | trb_240 | {"M": 2, "k": 0.5} | sym15u / both | 236 | 2834 | 0 | -144 | 3884 | 3559 | 1 | 288 |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 228 | 2553 | 0 | -518 | 1669 | 3080 | 2 | 288 |
| uw_qqq | reject | cusum_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 250 | 4778 | 0 | -520 | 344 | 3854 | 2 | 288 |
| uw_qqq | reject_native | cusum_14 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 263 | 4537 | 0 | -547 | -678 | 4103 | 2 | 288 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 288 |
| uw_qqq | retest_native | renko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 252 | 2711 | 0 | -192 | 815 | 3673 | 2 | 288 |
| vwap | break | vrb_240 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5309 | -171 | -93 | 2594 | 5153 | 1 | 288 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym8u / both | 276 | 4877 | -242 | 564 | 397 | 6808 | 2 | 288 |
| vwap | false_break | time_s_45 | {"M": 1, "k": 0.5} | sym15u / both | 322 | 3941 | -37 | -2220 | -980 | 2966 | 2 | 288 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 288 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 288 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 288 |
| vwap | retest | vsess_600 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 324 | 4287 | -362 | -2245 | -41 | 4558 | 2 | 288 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 288 |
| vwap_bands | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 618 | 4055 | 470 | -88 | 753 | 4340 | 1 | 288 |
| vwap_bands | break_native | tm20 | {"n": 3, "k": 0.25} | asym15u/30u / both | 436 | 4079 | -537 | -1426 | -2939 | 4423 | 2 | 288 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 288 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 288 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 288 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 288 |
| vwap_bands | retest | time_s_15 | {"M": 3, "tol": 0.5} | sym30u / both | 377 | 4108 | -527 | -1307 | -3860 | 4086 | 2 | 288 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 288 |
| week_month | break | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1357 | -472 | -345 | 67 | 873 | 1 | 288 |
| week_month | break_native | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1508 | -384 | -405 | 191 | 1025 | 1 | 288 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 288 |
| week_month | false_break_native | vsess_600 | {"M": 1, "k": 0.5} | sym30u / both | 51 | 1835 | 66 | -14 | -367 | 2252 | 2 | 288 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 288 |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | 1233 | -161 | 407 | -240 | 443 | 1 | 288 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 288 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 288 |
| zones | break | tib_3500 | {"n": 1, "k": 0.25} | sym15u / both | 203 | 3737 | 108 | 650 | 718 | 3536 | 2 | 288 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 288 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 288 |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 177 | 2863 | -154 | 660 | -299 | 2423 | 2 | 288 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 196 | 3254 | -73 | -1065 | -502 | 3105 | 1 | 288 |
| zones | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 278 | 3157 | -1008 | -1664 | -1608 | 2818 | 2 | 288 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 288 |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 161 | 2948 | -119 | -238 | 150 | 2390 | 2 | 288 |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 1739 of 14280 (modules x 476 bar rows); pass-1 result files written in the last hour: 1285 (all modules); ETA for these at that rate if they were alone: 1.4 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

