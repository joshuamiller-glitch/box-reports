# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 18:35Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 17552 | 400 | 0.000 | -0.67 / -0.62 / -0.63 / -0.95 | YES | {"Asia": 0.826, "London": 0.824, "NYAM": 0.825, "NYPM": 0.826} |  |
| p1rand10 | 73 | 73 | 0.000 | -0.63 / -0.61 / -0.59 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand11 | 73 | 73 | 0.000 | -0.67 / -0.59 / -0.63 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand12 | 73 | 73 | 0.000 | -0.62 / -0.61 / -0.63 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand13 | 73 | 73 | 0.000 | -0.62 / -0.60 / -0.62 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand14 | 72 | 72 | 0.000 | -0.61 / -0.60 / -0.58 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand15 | 72 | 72 | 0.000 | -0.64 / -0.63 / -0.61 / -0.90 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand16 | 72 | 72 | 0.000 | -0.67 / -0.61 / -0.61 / -0.97 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand17 | 72 | 72 | 0.000 | -0.64 / -0.60 / -0.60 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand18 | 72 | 72 | 0.000 | -0.66 / -0.58 / -0.61 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand19 | 72 | 72 | 0.000 | -0.67 / -0.62 / -0.62 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand2 | 17467 | 400 | 0.000 | -0.66 / -0.60 / -0.61 / -0.95 | YES | {"Asia": 0.822, "London": 0.819, "NYAM": 0.821, "NYPM": 0.822} |  |
| p1rand20 | 72 | 72 | 0.000 | -0.63 / -0.60 / -0.62 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand21 | 72 | 72 | 0.000 | -0.64 / -0.62 / -0.59 / -0.94 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand22 | 72 | 72 | 0.000 | -0.63 / -0.60 / -0.61 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand23 | 72 | 72 | 0.000 | -0.66 / -0.59 / -0.59 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand24 | 72 | 72 | 0.000 | -0.62 / -0.61 / -0.60 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand25 | 72 | 72 | 0.000 | -0.66 / -0.58 / -0.62 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand3 | 439 | 400 | 0.000 | -0.66 / -0.61 / -0.60 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand4 | 439 | 400 | 0.000 | -0.65 / -0.60 / -0.61 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 440 | 400 | 0.000 | -0.64 / -0.61 / -0.60 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand6 | 73 | 73 | 0.000 | -0.67 / -0.62 / -0.60 / -0.96 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand7 | 73 | 73 | 0.000 | -0.69 / -0.62 / -0.62 / -0.98 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand8 | 73 | 73 | 0.000 | -0.62 / -0.62 / -0.63 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand9 | 73 | 73 | 0.000 | -0.64 / -0.61 / -0.60 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 18:35Z):** result files per tag {"acctt1": 4, "acctt2": 1, "p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1gridops_test": 0, "p1rand1": 17577, "p1rand10": 75, "p1rand11": 75, "p1rand12": 75, "p1rand13": 75, "p1rand14": 74, "p1rand15": 74, "p1rand16": 74, "p1rand17": 74, "p1rand18": 74, "p1rand19": 74, "p1rand2": 17493, "p1rand20": 74, "p1rand21": 74, "p1rand22": 74, "p1rand23": 74, "p1rand24": 74, "p1rand25": 74, "p1rand3": 476, "p1rand4": 476, "p1rand5": 476, "p1rand6": 75, "p1rand7": 75, "p1rand8": 75, "p1rand9": 75, "p1real": 30199, "p1realx": 219, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 2, "London": 2, "NYAM": 2, "NYPM": 2}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 18:35Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"acctt1": 4, "acctt2": 1, "p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1gridops_test": 0, "p1rand1": 17577, "p1rand10": 75, "p1rand11": 75, "p1rand12": 75, "p1rand13": 75, "p1rand14": 74, "p1rand15": 74, "p1rand16": 74, "p1rand17": 74, "p1rand18": 74, "p1rand19": 74, "p1rand2": 17493, "p1rand20": 74, "p1rand21": 74, "p1rand22": 74, "p1rand23": 74, "p1rand24": 74, "p1rand25": 74, "p1rand3": 476, "p1rand4": 476, "p1rand5": 476, "p1rand6": 75, "p1rand7": 75, "p1rand8": 75, "p1rand9": 75, "p1real": 30199, "p1realx": 219, "rand1": 0, "real": 1654}; loop status: 2026-11-18T18:32Z rows=322 mods=146 todo=43269 running=0. 
Cells scored per session: {"Asia": 3819720, "London": 3704255, "NYAM": 3988079, "NYPM": 4002251}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -15.8 | -0.015 | 966.7 | 0.48 | -27.7 | -78.3 | -1.4 | 16.1 | -14.3 | 0.50 | -13.5 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | -16.1 | -0.007 | 976.8 | 0.47 | -53.6 | -123.1 | 2.3 | 12.1 | -18.4 | 0.00 | -13.7 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -48.7 [-61.3; 0.00] | -28.4 [-34.0; 0.00] | -11.6 [-27.6; 0.00] | 2.5 [0.6; 0.50] |
| bands (native) | -30.3 [-7.3; 0.00] | -7.8 [-19.2; 0.00] | -19.4 [-3.2; 0.50] | -22.5 [-0.8; 0.50] |
| barnative | -14.0 [5.0; 0.50] | 8.4 [24.9; 1.00] | 6.5 [20.6; 1.00] | -14.4 [-1.4; 0.50] |
| book | 5.6 [12.3; 1.00] | 13.1 [31.4; 1.00] | 2.5 [14.3; 1.00] | -4.7 [no null yet] |
| book (native) | -10.4 [-13.0; 0.00] | 7.0 [14.8; 1.00] | -15.6 [-5.3; 0.50] | -5.7 [no null yet] |
| confluence | -16.8 [-31.3; 0.00] | -6.0 [5.1; 0.50] | 0.9 [-2.4; 0.50] | 14.7 [18.2; 1.00] |
| levels | -30.1 [-22.4; 0.00] | -23.2 [-13.6; 0.50] | 28.4 [40.3; 1.00] | 6.2 [9.6; 1.00] |
| levels (native) | -22.5 [-13.4; 0.50] | -6.2 [24.2; 1.00] | 18.9 [25.3; 1.00] | 1.1 [12.4; 0.50] |
| live | -4.6 [5.3; 0.50] | -15.7 [-13.2; 0.00] | 0.2 [22.0; 1.00] | 6.3 [-4.3; 0.50] |
| manual | -8.5 [6.1; 0.50] | -0.4 [-11.0; 0.00] | -36.6 [-25.9; 0.00] | -5.0 [5.1; 0.50] |
| manual (native) | 6.7 [10.7; 1.00] | -31.8 [-28.8; 0.00] | -18.2 [-1.6; 0.50] | -27.1 [0.7; 0.50] |
| momentum | 3.7 [11.8; 0.50] | 14.9 [8.2; 0.50] | -9.9 [0.6; 0.50] | -4.9 [1.9; 0.50] |
| momentum (native) | -38.1 [-12.9; 0.00] | -29.0 [-38.2; 0.00] | 0.2 [-4.0; 0.00] | -8.1 [1.3; 0.50] |
| pullback | -13.3 [-15.2; 0.50] | -8.6 [15.5; 1.00] | 12.3 [-16.1; 0.00] | -4.6 [19.9; 1.00] |
| pullback (native) | -3.0 [6.2; 1.00] | -0.1 [7.6; 1.00] | -2.2 [31.5; 1.00] | -39.7 [-24.6; 0.00] |
| structure | -18.1 [-18.4; 0.00] | -18.5 [-35.3; 0.00] | -32.3 [-21.6; 0.00] | -20.1 [10.7; 0.50] |
| structure (native) | -10.7 [-26.9; 0.00] | -9.5 [-14.9; 0.00] | -2.2 [4.4; 0.50] | -33.3 [-29.7; 0.00] |
| tape | 12.3 [13.0; 0.50] | -11.9 [6.0; 0.50] | -19.2 [-13.9; 0.50] | -11.6 [4.7; 0.50] |
| tape (native) | -21.7 [-34.6; 0.00] | -25.2 [10.4; 1.00] | -12.3 [5.4; 0.50] | -38.4 [-21.5; 0.00] |
| trend | -16.2 [-19.2; 0.00] | -20.8 [7.9; 0.50] | -14.8 [-7.6; 0.00] | 9.0 [35.7; 1.00] |
| trend (native) | -13.2 [-7.4; 0.50] | -8.8 [-5.1; 0.50] | -25.4 [-12.4; 0.50] | -7.2 [-8.9; 0.50] |
| xmarket | -5.1 [-24.6; 0.00] | -19.9 [-29.0; 0.00] | 10.9 [19.7; 1.00] | -8.1 [-5.9; 0.50] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels|PRICE | 28.4 | 0.021 | 179.1 | 0.69 | 16.2 | 15.6 | {"2023": 13.5, "2024": 24.4, "2025": 48.9, "2026": 13.8} | -11.9 | 40.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 18.9 | 0.021 | 281.0 | 0.53 | 36.7 | 83.2 | {"2023": 38.9, "2024": 10.9, "2025": 9.1, "2026": 33.5} | -6.4 | 25.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|INFORMATION | 14.9 | 0.024 | 304.8 | 0.57 | -26.0 | -60.3 | {"2023": -15.5, "2024": 56.6, "2025": 6.1, "2026": -14.5} | 6.7 | 8.2 | 0.50 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| confluence|TIME | 14.7 | 0.017 | 190.5 | 0.53 | 40.3 | -23.0 | {"2023": -4.8, "2024": 9.5, "2025": 13.4, "2026": 28.7} | -3.4 | 18.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|INFORMATION | 13.1 | 0.010 | 243.6 | 0.56 | -0.2 | -27.3 | {"2023": 16.4, "2024": 34.8, "2025": -13.5, "2026": 17.6} | -18.3 | 31.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape|ACTIVITY | 12.3 | 0.014 | 425.4 | 0.53 | -24.6 | -27.2 | {"2023": 34.8, "2024": 12.7, "2025": 15.8, "2026": 0.7} | -0.6 | 13.0 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|PRICE | 12.3 | 0.009 | 602.4 | 0.53 | 81.9 | 115.9 | {"2023": -7.2, "2024": -6.8, "2025": 16.2, "2026": 36.4} | 28.4 | -16.1 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|PRICE | 10.9 | 0.013 | 245.4 | 0.52 | 47.7 | 111.1 | {"2023": 10.3, "2024": -6.2, "2025": 11.3, "2026": 31.0} | -8.8 | 19.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend|TIME | 9.0 | 0.015 | 622.2 | 0.53 | -100.9 | 41.0 | {"2023": 6.9, "2024": 23.5, "2025": 30.1, "2026": -32.6} | -26.7 | 35.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| barnative|INFORMATION | 8.4 | 0.001 | 695.7 | 0.56 | 61.9 | 76.1 | {"2023": 29.5, "2024": 30.3, "2025": -12.4, "2026": 0.5} | -16.5 | 24.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.2%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.1%); U7 tm600 L6M -10.7 pts/wk, rank 32% (top 67.7%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.2%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 37.7%); A7 tm60 L6M 14.3 pts/wk, rank 80% (top 20.5%). Rank = share of ALL London cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| momentum|INFORMATION | 30.2 | 0.023 | 222.3 | 0.58 | 56.4 | -3.5 | {"2023": -25.3, "2024": 61.9, "2025": 9.1, "2026": 35.4} | 0.3 | 29.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| barnative|PRICE | 18.8 | 0.020 | 483.7 | 0.53 | 126.6 | 134.5 | {"2023": -54.1, "2024": 5.3, "2025": -0.3, "2026": 80.4} | 1.7 | 17.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| xmarket|ACTIVITY | 12.5 | 0.014 | 424.5 | 0.52 | -12.9 | -98.5 | {"2023": -10.4, "2024": -6.3, "2025": 12.5, "2026": 42.2} | 0.6 | 12.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|TIME | 12.4 | 0.022 | 512.4 | 0.56 | 73.5 | 141.0 | {"2023": 23.6, "2024": 23.0, "2025": 23.0, "2026": -16.3} | 11.7 | 0.7 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| levels (native)|PRICE | 9.1 | 0.012 | 356.4 | 0.53 | 99.4 | 151.5 | {"2023": -46.0, "2024": -3.6, "2025": 30.5, "2026": 16.4} | -20.4 | 29.5 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| pullback|PRICE | 8.4 | 0.002 | 615.3 | 0.52 | 101.2 | 115.9 | {"2023": -16.3, "2024": -6.2, "2025": 5.9, "2026": 36.6} | 27.0 | -18.6 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 8.2 | 0.007 | 447.5 | 0.51 | 32.4 | 58.3 | {"2023": -18.0, "2024": -12.4, "2025": -3.5, "2026": 54.7} | -31.8 | 40.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| manual (native)|ACTIVITY | 8.0 | 0.004 | 448.9 | 0.53 | 2.0 | -48.1 | {"2023": -8.8, "2024": 33.7, "2025": -15.4, "2026": 10.5} | -7.2 | 15.1 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| levels (native)|INFORMATION | 4.9 | -0.000 | 677.8 | 0.49 | 75.8 | 35.7 | {"2023": -38.5, "2024": 16.1, "2025": -15.4, "2026": 29.6} | -20.8 | 25.7 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape (native)|INFORMATION | 4.6 | -0.004 | 322.1 | 0.51 | 13.4 | -49.1 | {"2023": 3.8, "2024": -9.3, "2025": 42.4, "2026": -23.5} | -25.1 | 29.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | vsess_600 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | sym8u | both | 6120 | 2666 | 701 | 1.00 | 5 / -1086 / 562 / 1.00 | {"2023": -421.0, "2024": -1541.0, "2025": -1139.0, "2026": 6064.0} |
| 2 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 50} | sym8u | both | 6032 | 3321 | 643 | 1.00 | 5 / -163 / 2254 / 1.00 | {"2023": -1534.0, "2024": 277.0, "2025": 116.0, "2026": 5648.0} |
| 3 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym8u | both | 5846 | 2536 | 233 | 1.00 | 25 / -26 / 2923 / 1.00 | {"2023": 667.0, "2024": 1147.0, "2025": -135.0, "2026": 5737.0} |
| 4 | time_m_13 | tape.tape_stack.r5_follow | {"k": 2} | sym15u | both | 5803 | 3194 | 233 | 1.00 | 0 /  /  /  | {"2023": 1316.0, "2024": -862.0, "2025": -307.0, "2026": 5653.0} |
| 5 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | 5 / -290 / 857 / 1.00 | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 6 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym15u/30u | both | 5725 | 2309 | 222 | 1.00 | 5 / -324 / 869 / 1.00 | {"2023": 805.0, "2024": -945.0, "2025": -3204.0, "2026": 7489.0} |
| 7 | swing_atr_0.1 | tape.tape_speed.follow | {"f": 1.5, "L": 200} | sym8u | both | 5714 | 2851 | 645 | 1.00 | 5 / -2256 / 214 / 1.00 | {"2023": -1209.0, "2024": 895.0, "2025": -1513.0, "2026": 6526.0} |
| 8 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym20u/10u | both | 5657 | 2334 | 231 | 1.00 | 25 / -30 / 3284 / 1.00 | {"2023": 891.0, "2024": 2127.0, "2025": 454.0, "2026": 5288.0} |
| 9 | tm20 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 5614 | 2080 | 613 | 0.67 | 5 / -1401 / 1393 / 1.00 | {"2023": -1695.0, "2024": -839.0, "2025": -981.0, "2026": 7113.0} |
| 10 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | asym15u/30u | both | 5590 | 3492 | 248 | 0.50 | 5 / -1102 / 736 / 1.00 | {"2023": -19.0, "2024": -964.0, "2025": 759.0, "2026": 4720.0} |
| 11 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | asym10u/20u | both | 5590 | 3492 | 248 | 0.50 | 5 / -1105 / 723 / 1.00 | {"2023": -205.0, "2024": -1220.0, "2025": 239.0, "2026": 4765.0} |
| 12 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | sym30u | both | 5590 | 3492 | 248 | 0.50 | 5 / -1102 / 736 / 1.00 | {"2023": 117.0, "2024": -915.0, "2025": 808.0, "2026": 4720.0} |
| 13 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | sym15u | both | 5590 | 3492 | 248 | 0.50 | 5 / -1102 / 736 / 1.00 | {"2023": 3.0, "2024": -891.0, "2025": 769.0, "2026": 4654.0} |
| 14 | time_m_7 | xmarket.xmarket_commod.against_CL | {"w": 1, "thr": 1.0} | asym20u/10u | both | 5590 | 3492 | 248 | 0.50 | 5 / -1102 / 736 / 1.00 | {"2023": -438.0, "2024": -715.0, "2025": 904.0, "2026": 4877.0} |
| 15 | dlt_45 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "close"} | sym8u | both | 5555 | 1195 | 312 | 1.00 | 5 / -1109 / 3168 / 1.00 | {"2023": -1481.0, "2024": -1100.0, "2025": 62.0, "2026": 7032.0} |
| 16 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 5541 | 2215 | 231 | 1.00 | 25 / -91 / 3226 / 1.00 | {"2023": 1193.0, "2024": 760.0, "2025": -21.0, "2026": 5146.0} |
| 17 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 25 / -51 / 3255 / 1.00 | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 18 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 5529 | 2203 | 230 | 1.00 | 25 / -51 / 3255 / 1.00 | {"2023": 812.0, "2024": 1425.0, "2025": 18.0, "2026": 5170.0} |
| 19 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5529 | 2203 | 230 | 1.00 | 25 / -51 / 3255 / 1.00 | {"2023": 766.0, "2024": 1526.0, "2025": 18.0, "2026": 5170.0} |
| 20 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym30u | both | 5528 | 2119 | 220 | 1.00 | 5 / -257 / 968 / 1.00 | {"2023": 677.0, "2024": -476.0, "2025": -2538.0, "2026": 6998.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 28.4 | 0.019 | 377.0 | 0.57 | 60.5 | 91.3 | -35.3 | -34.1 | 63.7 | 1.00 | -7.6 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 31.6 | 0.023 | 336.4 | 0.57 | 46.8 | 91.3 | -19.1 | -16.9 | 50.7 | 1.00 | -0.7 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 30.6 [12.2; 1.00] | -3.4 [-14.2; 0.50] | 15.3 [9.0; 0.50] | 30.1 [21.2; 1.00] |
| bands (native) | 1.9 [-2.3; 0.50] | 1.9 [-7.1; 0.50] | 23.7 [55.6; 1.00] | 30.0 [65.6; 1.00] |
| barnative | -20.5 [2.3; 0.50] | -24.3 [-31.0; 0.00] | 44.8 [90.5; 1.00] | 11.1 [-13.6; 0.00] |
| book | 8.1 [4.8; 0.50] | 23.6 [16.6; 1.00] | -9.8 [25.1; 0.50] | 27.6 [no null yet] |
| book (native) | 3.8 [35.7; 1.00] | -18.0 [6.1; 0.50] | 19.0 [16.0; 0.50] | -15.0 [no null yet] |
| confluence | 13.7 [24.3; 1.00] | 7.5 [13.6; 0.50] | 41.9 [38.1; 1.00] | 1.9 [1.9; 0.50] |
| levels | 3.3 [33.4; 1.00] | -33.9 [-18.4; 0.50] | 3.3 [37.8; 1.00] | -0.1 [-11.0; 0.00] |
| levels (native) | 25.5 [42.2; 1.00] | 7.6 [48.5; 1.00] | 10.1 [43.2; 1.00] | 3.6 [11.6; 0.50] |
| live | 14.6 [20.3; 0.50] | 24.9 [45.0; 1.00] | 8.2 [-10.6; 0.00] | -10.3 [-5.0; 0.50] |
| manual | 29.8 [47.8; 1.00] | 43.5 [96.5; 1.00] | -14.9 [-31.6; 0.00] | 33.3 [37.0; 1.00] |
| manual (native) | -66.0 [-59.9; 0.00] | -63.6 [-69.4; 0.00] | -22.8 [-36.3; 0.00] | -16.6 [1.6; 0.50] |
| momentum | 23.2 [4.1; 0.50] | 8.4 [4.4; 0.50] | -2.7 [-30.7; 0.00] | 39.8 [27.0; 1.00] |
| momentum (native) | -2.9 [3.2; 1.00] | -2.9 [1.6; 0.50] | 41.8 [49.8; 1.00] | 36.0 [48.2; 1.00] |
| pullback | 23.8 [51.4; 1.00] | 18.5 [25.6; 1.00] | -13.7 [24.4; 1.00] | -1.4 [11.6; 1.00] |
| pullback (native) | 24.5 [57.4; 1.00] | -4.6 [-20.2; 0.00] | -2.7 [31.5; 1.00] | -18.9 [5.1; 0.50] |
| structure | 12.2 [8.0; 1.00] | -26.7 [-17.9; 0.00] | 26.5 [56.4; 1.00] | -0.9 [24.2; 0.50] |
| structure (native) | 36.8 [65.2; 1.00] | 40.8 [59.2; 1.00] | 2.9 [-3.4; 0.50] | 38.2 [42.6; 1.00] |
| tape | -17.6 [-41.5; 0.00] | -44.7 [-31.8; 0.00] | 9.0 [0.4; 0.50] | -33.5 [-29.0; 0.00] |
| tape (native) | 17.2 [20.1; 1.00] | -43.4 [-53.3; 0.00] | 4.7 [16.4; 0.50] | 0.3 [-12.4; 0.00] |
| trend | -24.8 [-27.2; 0.00] | -16.0 [2.7; 0.50] | -2.6 [9.9; 1.00] | -4.5 [18.6; 1.00] |
| trend (native) | -57.9 [-62.8; 0.00] | -21.9 [13.8; 0.50] | 15.8 [33.9; 1.00] | -23.4 [-11.6; 0.50] |
| xmarket | -19.5 [-9.4; 0.00] | -30.1 [-20.0; 0.50] | 11.2 [15.9; 1.00] | -14.9 [-14.8; 0.50] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 44.8 | 0.018 | 563.7 | 0.58 | 45.9 | -36.9 | {"2023": -29.3, "2024": -23.3, "2025": 104.9, "2026": 77.7} | -45.7 | 90.5 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 43.5 | 0.028 | 408.1 | 0.59 | 94.0 | -7.0 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 65.0} | -53.0 | 96.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| confluence|PRICE | 41.9 | 0.027 | 387.9 | 0.54 | 58.2 | -121.7 | {"2023": 89.5, "2024": -14.0, "2025": 63.5, "2026": 67.4} | 3.8 | 38.1 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 41.8 | 0.024 | 532.0 | 0.56 | -6.9 | 4.4 | {"2023": -10.0, "2024": -11.1, "2025": 87.9, "2026": 66.1} | -8.0 | 49.8 | 1.00 | {"2023": "AMBER", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 40.8 | 0.026 | 575.2 | 0.59 | 66.4 | 44.7 | {"2023": 56.8, "2024": 0.4, "2025": 94.7, "2026": 19.6} | -18.4 | 59.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 39.8 | 0.023 | 654.3 | 0.57 | 96.6 | 167.5 | {"2023": 22.0, "2024": 70.5, "2025": 52.6, "2026": -6.1} | 12.8 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} | -4.4 | 42.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 36.8 | 0.024 | 824.1 | 0.60 | -16.6 | 60.5 | {"2023": 51.5, "2024": 23.8, "2025": 94.6, "2026": -20.9} | -28.5 | 65.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 36.0 | 0.023 | 864.9 | 0.54 | 71.5 | 198.2 | {"2023": 22.0, "2024": 86.3, "2025": 52.6, "2026": -38.6} | -12.1 | 48.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | -3.7 | 37.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 6% (top 94.1%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 56.9%); U7 tm600 L6M -11.4 pts/wk, rank 40% (top 60.0%); P7 tm60 L6M -60.7 pts/wk, rank 9% (top 90.5%); H7 tm60 L6M 28.8 pts/wk, rank 86% (top 13.6%); A7 tm60 L6M -17.2 pts/wk, rank 34% (top 65.9%); O7 tm60 L6M 15.1 pts/wk, rank 77% (top 22.7%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands (native)|TIME | 48.7 | 0.024 | 585.7 | 0.52 | -30.1 | -92.1 | {"2023": 15.7, "2024": -14.5, "2025": 136.2, "2026": 30.5} | -28.5 | 77.2 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| bands|ACTIVITY | 45.4 | 0.030 | 354.0 | 0.54 | 21.7 | -17.3 | {"2023": -41.1, "2024": 55.3, "2025": 95.2, "2026": 2.4} | 34.5 | 10.9 | 0.50 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 44.9 | 0.041 | 593.4 | 0.64 | -4.7 | 9.1 | {"2023": 71.5, "2024": 6.5, "2025": 122.1, "2026": -9.4} | 2.2 | 42.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
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
| 3 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym15u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 4 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym15u/30u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 5 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym30u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 6 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym10u/20u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 7 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | asym20u/10u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1949.0, "2024": 71.0, "2025": 270.0, "2026": 9143.0} |
| 8 | tick_3200 | xmarket.xmarket_es.revert | {"w": 1, "thr": 1.0} | sym8u | both | 8330 | 2851 | 454 | 1.00 | 5 / -1219 / 1308 / 1.00 | {"2023": 1979.0, "2024": 70.0, "2025": 270.0, "2026": 9143.0} |
| 9 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym20u/10u | both | 8284 | 2906 | 505 | 1.00 | 5 / 378 / 3088 / 1.00 | {"2023": -852.0, "2024": -683.0, "2025": 2764.0, "2026": 7588.0} |
| 10 | kagi_28 | levels.levels_swsr5.false_break_native | {"M": 2, "k": 0.5} | sym15u | both | 8188 | 3060 | 432 | 1.00 | 2 / 3437 / 5586 / 1.00 | {"2023": 1948.0, "2024": -2061.0, "2025": 866.0, "2026": 8579.0} |
| 11 | swing_atr_0.1 | tape.tape_speed.follow_native | {"f": 3.0, "L": 3600} | sym15u | both | 8142 | 2340 | 562 | 1.00 | 5 / -371 / 1825 / 1.00 | {"2023": -2474.0, "2024": -2255.0, "2025": 763.0, "2026": 10386.0} |
| 12 | mrenko_14 | book.book_sweep.cnt_fade | {"thr": 1} | plain60/60 | both | 8102 | 4824 | 1744 | 1.00 | 2 / -2743 / -2138 / 1.00 | {"2023": 369.0, "2024": -2136.0, "2025": -998.0, "2026": 6430.0} |
| 13 | vol_350 | levels.levels_round.break_native | {"n": 3, "k": 0.25} | sym30u | both | 8082 | 2155 | 480 | 1.00 | 5 / 602 / 1633 / 1.00 | {"2023": 547.0, "2024": 474.0, "2025": 3963.0, "2026": 8386.0} |
| 14 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym15u/30u | both | 8038 | 3705 | 499 | 1.00 | 5 / 704 / 3235 / 1.00 | {"2023": 16.0, "2024": 1506.0, "2025": 4489.0, "2026": 6565.0} |
| 15 | renko_10 | levels.levels_round.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 8023 | 656 | 657 | 0.67 | 5 / -146 / 2906 / 1.00 | {"2023": -600.0, "2024": -3119.0, "2025": -4002.0, "2026": 8822.0} |
| 16 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym15u | both | 8013 | 3680 | 500 | 1.00 | 5 / 677 / 3228 / 1.00 | {"2023": -200.0, "2024": 1750.0, "2025": 4356.0, "2026": 6540.0} |
| 17 | vsess_450 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | asym15u/30u | both | 7960 | 3412 | 531 | 0.83 | 5 / -1909 / 1527 / 1.00 | {"2023": -1290.0, "2024": 1149.0, "2025": -12.0, "2026": 9238.0} |
| 18 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | asym10u/20u | both | 7943 | 3967 | 504 | 1.00 | 5 / 766 / 3407 / 1.00 | {"2023": 648.0, "2024": 1861.0, "2025": 5118.0, "2026": 6144.0} |
| 19 | vol_350 | levels.levels_round.break | {"n": 3, "k": 0.5} | sym8u | both | 7909 | 2632 | 645 | 1.00 | 5 / -866 / 424 / 1.00 | {"2023": -295.0, "2024": -2844.0, "2025": 582.0, "2026": 6211.0} |
| 20 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.5} | sym30u | both | 7895 | 3566 | 499 | 1.00 | 5 / 707 / 3316 / 1.00 | {"2023": -294.0, "2024": 898.0, "2025": 4173.0, "2026": 6422.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -35.5 | -0.022 | 2328.0 | 0.43 | 55.9 | 94.1 | 0.3 | 16.5 | -35.8 | 0.00 | -0.3 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -25.1 | -0.015 | 1905.4 | 0.48 | 55.9 | 94.1 | -9.7 | 4.7 | -15.4 | 0.00 | 2.4 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -15.3 [-9.7; 0.50] | 1.1 [12.6; 0.50] | 19.9 [45.2; 1.00] | -19.9 [-8.1; 0.50] |
| bands (native) | 27.1 [27.0; 1.00] | 3.9 [-8.8; 0.50] | -6.9 [27.3; 1.00] | -24.5 [-37.2; 0.00] |
| barnative | -27.0 [-39.7; 0.00] | -4.5 [14.6; 0.50] | -2.8 [10.8; 1.00] | -19.2 [-53.6; 0.00] |
| book | 3.8 [-22.3; 0.00] | 6.5 [27.7; 0.50] | 28.3 [6.4; 0.50] | -31.7 [no null yet] |
| book (native) | -50.0 [-34.3; 0.00] | -8.8 [1.6; 0.50] | -3.5 [-1.0; 0.50] | -42.6 [no null yet] |
| confluence | -5.5 [-22.1; 0.50] | -0.1 [-13.3; 0.00] | -34.9 [-12.1; 0.00] | -18.3 [-35.4; 0.00] |
| levels | 5.0 [-8.3; 0.00] | -20.7 [-5.5; 0.50] | -32.0 [-30.3; 0.00] | 11.7 [42.9; 1.00] |
| levels (native) | -9.2 [10.4; 1.00] | -23.8 [-16.1; 0.00] | -28.4 [-16.7; 0.00] | -2.1 [23.2; 1.00] |
| live | -22.8 [7.2; 0.50] | -36.5 [-17.2; 0.00] | -18.1 [-44.0; 0.00] | -16.8 [-48.1; 0.00] |
| manual | -19.7 [-55.2; 0.00] | -26.0 [-30.4; 0.00] | 6.9 [6.1; 1.00] | -12.8 [-12.1; 0.50] |
| manual (native) | 25.7 [38.7; 1.00] | 7.0 [16.1; 0.50] | 17.9 [-9.4; 0.50] | -32.2 [-14.9; 0.50] |
| momentum | -11.1 [-4.6; 0.50] | -13.4 [-5.4; 0.00] | -0.6 [35.2; 1.00] | -2.0 [-5.5; 0.50] |
| momentum (native) | 17.4 [24.9; 0.50] | -39.6 [-31.1; 0.00] | 16.5 [26.5; 1.00] | -9.9 [-5.2; 0.50] |
| pullback | -24.6 [-31.9; 0.00] | -6.4 [-39.0; 0.00] | -34.9 [-7.5; 0.00] | -10.2 [13.2; 1.00] |
| pullback (native) | -9.6 [9.4; 0.50] | -68.5 [-64.7; 0.00] | 0.8 [19.0; 1.00] | -20.2 [1.3; 0.50] |
| structure | 19.4 [21.1; 1.00] | -14.0 [11.8; 1.00] | -38.8 [-27.2; 0.00] | 22.5 [32.0; 1.00] |
| structure (native) | 5.2 [-15.3; 0.50] | -23.2 [-5.1; 0.50] | -25.2 [-6.8; 0.50] | 23.2 [40.9; 1.00] |
| tape | 0.8 [7.6; 0.50] | 35.7 [38.7; 1.00] | -10.2 [-12.9; 0.00] | -35.3 [-6.6; 0.00] |
| tape (native) | -2.3 [25.9; 1.00] | -25.3 [-28.2; 0.00] | 19.1 [30.3; 1.00] | -1.5 [0.4; 0.50] |
| trend | 5.0 [36.8; 1.00] | 6.0 [10.6; 0.50] | 15.9 [35.9; 1.00] | 17.8 [0.6; 0.50] |
| trend (native) | 35.7 [48.9; 1.00] | -10.7 [-21.9; 0.00] | -2.4 [2.8; 0.50] | 15.2 [32.7; 1.00] |
| xmarket | 15.7 [21.3; 1.00] | -28.0 [-27.5; 0.00] | 5.8 [-8.0; 0.50] | -18.8 [-2.8; 0.50] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| tape|INFORMATION | 35.7 | 0.016 | 402.1 | 0.58 | -55.5 | -11.0 | {"2023": 54.3, "2024": -19.1, "2025": 113.8, "2026": 2.5} | -3.0 | 38.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| trend (native)|ACTIVITY | 35.7 | 0.034 | 403.5 | 0.57 | 35.2 | 33.9 | {"2023": -11.0, "2024": 39.8, "2025": 64.3, "2026": 11.8} | -13.3 | 48.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book|PRICE | 28.3 | 0.023 | 416.6 | 0.56 | 132.7 | 67.0 | {"2023": -72.3, "2024": 38.9, "2025": 13.2, "2026": 65.7} | 22.0 | 6.4 | 0.50 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 27.1 | 0.033 | 293.4 | 0.56 | 11.8 | -93.6 | {"2023": 25.8, "2024": 69.2, "2025": 27.5, "2026": -22.9} | 0.1 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual (native)|ACTIVITY | 25.7 | 0.031 | 366.0 | 0.54 | 48.5 | 6.0 | {"2023": -42.5, "2024": -13.5, "2025": 82.6, "2026": 26.6} | -13.0 | 38.7 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 23.2 | 0.022 | 469.8 | 0.58 | 40.4 | -3.8 | {"2023": 49.7, "2024": 5.8, "2025": -1.5, "2026": 64.7} | -17.6 | 40.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|TIME | 22.5 | 0.020 | 875.2 | 0.57 | 127.0 | 175.4 | {"2023": -36.0, "2024": 18.3, "2025": -26.9, "2026": 104.6} | -9.5 | 32.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 19.9 | 0.013 | 536.5 | 0.49 | -64.2 | -32.6 | {"2023": 75.2, "2024": 42.8, "2025": 44.5, "2026": -53.7} | -25.2 | 45.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|ACTIVITY | 19.4 | 0.003 | 942.1 | 0.48 | 102.6 | 189.5 | {"2023": -19.1, "2024": -6.3, "2025": 2.1, "2026": 82.5} | -1.7 | 21.1 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| tape (native)|PRICE | 19.1 | 0.013 | 1001.2 | 0.48 | 111.9 | -74.3 | {"2023": -62.2, "2024": -41.5, "2025": 32.6, "2026": 100.5} | -11.2 | 30.3 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 23% (top 77.3%); M7 tm60 L6M -36.8 pts/wk, rank 14% (top 86.0%); U7 tm600 L6M 4.8 pts/wk, rank 61% (top 38.6%); P7 tm60 L6M -35.9 pts/wk, rank 14% (top 85.5%); H7 tm60 L6M -20.1 pts/wk, rank 25% (top 75.4%); A7 tm60 L6M -32.5 pts/wk, rank 16% (top 83.7%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|INFORMATION | 39.9 | 0.019 | 479.9 | 0.53 | 41.1 | 70.9 | {"2023": 69.5, "2024": -0.9, "2025": 118.0, "2026": -13.7} | 24.4 | 15.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend (native)|ACTIVITY | 35.1 | 0.033 | 324.7 | 0.51 | 92.1 | 127.8 | {"2023": -4.9, "2024": -7.8, "2025": 79.5, "2026": 46.0} | -5.6 | 40.7 | 1.00 | {"2023": "ok", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| momentum (native)|ACTIVITY | 31.3 | 0.030 | 380.0 | 0.62 | 44.5 | 111.1 | {"2023": 31.0, "2024": 31.7, "2025": 11.6, "2026": 54.2} | -15.1 | 46.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 29.4 | 0.034 | 254.0 | 0.57 | 11.8 | -93.6 | {"2023": 25.8, "2024": 69.2, "2025": 27.5, "2026": -14.3} | -2.8 | 32.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend|PRICE | 25.9 | 0.020 | 445.9 | 0.58 | 23.9 | 143.3 | {"2023": -13.8, "2024": 23.1, "2025": 26.3, "2026": 41.6} | -44.8 | 70.8 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|TIME | 23.9 | 0.023 | 538.1 | 0.56 | 7.2 | 147.4 | {"2023": 23.8, "2024": 51.0, "2025": -11.6, "2026": 33.8} | 1.2 | 22.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 22.7 | 0.014 | 692.4 | 0.57 | -6.3 | 83.3 | {"2023": 60.8, "2024": 67.0, "2025": -21.6, "2026": 10.6} | 6.3 | 16.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| tape|ACTIVITY | 21.5 | 0.003 | 673.5 | 0.58 | -96.9 | 15.9 | {"2023": 37.6, "2024": 61.6, "2025": 19.0, "2026": -28.2} | -1.5 | 23.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual (native)|ACTIVITY | 21.3 | 0.026 | 471.4 | 0.54 | 50.2 | 58.2 | {"2023": -42.5, "2024": -22.8, "2025": 82.6, "2026": 21.4} | -19.9 | 41.2 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| barnative|INFORMATION | 20.2 | 0.017 | 411.1 | 0.49 | 85.3 | 70.8 | {"2023": -16.9, "2024": -15.0, "2025": 49.6, "2026": 38.7} | -51.8 | 72.0 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.75 | 5 / 991 / 2269 / 1.00 | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 2 | tick_300 | tape.tape_stack.r3_follow | {"k": 3} | sym15u | both | 6975 | 1405 | 353 | 1.00 | 0 /  /  /  | {"2023": 598.0, "2024": 177.0, "2025": 3798.0, "2026": 6775.0} |
| 3 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym10u/20u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1046.0, "2024": -1508.0, "2025": 3102.0, "2026": 7745.0} |
| 4 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 5 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym20u/10u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1266.0, "2024": -1067.0, "2025": 3095.0, "2026": 7745.0} |
| 6 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym15u/30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 7 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 8 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym8u | both | 6722 | 2181 | 270 | 1.00 | 5 / 507 / 1497 / 1.00 | {"2023": -1094.0, "2024": -1432.0, "2025": 3159.0, "2026": 7746.0} |
| 9 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 10, "r": 0.6} | plain60/60 | both | 6610 | 590 | 1034 | 1.00 | 5 / -1524 / -356 / 1.00 | {"2023": -294.0, "2024": 1303.0, "2025": 3131.0, "2026": 6965.0} |
| 10 | rng_28 | book.book_cancel.net_follow_native | {"L": 900, "z": 1.0} | sym15u | both | 6594 | 2109 | 350 | 0.50 | 0 /  /  /  | {"2023": 507.0, "2024": 2231.0, "2025": -751.0, "2026": 6596.0} |
| 11 | pnf_20 | levels.levels_sdx_vol1100.lim_mid | {"d": "E", "F": 9, "tgt": "r2"} | sym15u | both | 6337 | 2070 | 275 | 1.00 | 2 / -899 / 240 / 1.00 | {"2023": -998.0, "2024": 71.0, "2025": 1443.0, "2026": 6397.0} |
| 12 | pnf_5 | book.book_ofi.follow | {"L": 100, "z": 1.5} | sym15u | both | 6242 | 3060 | 328 | 1.00 | 2 / 72 / 1067 / 1.00 | {"2023": 1290.0, "2024": -755.0, "2025": -3099.0, "2026": 6638.0} |
| 13 | time_m_1 | book.book_cancel.canc_follow | {"L": 50, "z": 1.0} | sym15u | both | 6170 | 1483 | 348 | 1.00 | 0 /  /  /  | {"2023": -3331.0, "2024": -511.0, "2025": 2252.0, "2026": 2888.0} |
| 14 | time_m_2 | book.book_imb.delta_follow | {"lv": 1, "thr": 0.2} | sym15u | both | 6099 | 1143 | 333 | 0.50 | 0 /  /  /  | {"2023": 249.0, "2024": -2862.0, "2025": 5581.0, "2026": 4576.0} |
| 15 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | sym30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 398 / 1855 / 1.00 | {"2023": -927.0, "2024": 1201.0, "2025": -1574.0, "2026": 6224.0} |
| 16 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym15u/30u | both | 6090 | 2402 | 301 | 1.00 | 5 / 419 / 1855 / 1.00 | {"2023": -306.0, "2024": 1499.0, "2025": -1131.0, "2026": 6319.0} |
| 17 | tm10 | trend.trend_ma_hma.cross | {"len": 21, "width": 4, "hyst": 0.0} | plain60/60 | both | 6076 | 1146 | 908 | 1.00 | 5 / 182 / 1688 / 1.00 | {"2023": -1233.0, "2024": -756.0, "2025": 2796.0, "2026": 6659.0} |
| 18 | drb_1200 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 2} | asym10u/20u | both | 6072 | 2310 | 311 | 1.00 | 5 / 453 / 1701 / 1.00 | {"2023": -508.0, "2024": 1153.0, "2025": -2178.0, "2026": 6086.0} |
| 19 | vsess_200 | levels.levels_fib5.reject | {"tol": 0.5, "conf": "body"} | sym15u | both | 6051 | 2828 | 276 | 0.67 | 5 / -640 / -204 / 1.00 | {"2023": -303.0, "2024": 1910.0, "2025": -1306.0, "2026": 5002.0} |
| 20 | tick_300 | bands.bands_bollinger.walk | {"n": 10, "k": 1.5, "N": 3} | asym15u/30u | both | 6046 | 1396 | 308 | 0.75 | 5 / -137 / 1458 / 1.00 | {"2023": -2011.0, "2024": 1321.0, "2025": -300.0, "2026": 5317.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -13.6 | -0.014 | 991.7 | 0.47 | 3.2 | -24.2 | -12.1 | -3.9 | -1.5 | 0.50 | -10.6 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -10.9 | -0.010 | 952.6 | 0.49 | -2.2 | -35.9 | 9.4 | 11.4 | -20.3 | 0.00 | -7.1 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 16.1 [20.5; 1.00] | 18.8 [2.0; 0.50] | 30.1 [47.9; 1.00] | 9.7 [9.5; 1.00] |
| bands (native) | 11.2 [16.9; 1.00] | 5.1 [-3.2; 0.00] | 23.2 [26.5; 1.00] | 8.7 [13.6; 1.00] |
| barnative | 12.7 [31.9; 1.00] | -0.3 [-16.3; 0.00] | -7.6 [3.1; 0.50] | -21.6 [-9.8; 0.50] |
| book | -9.5 [-8.1; 0.50] | -18.6 [-32.4; 0.00] | -45.7 [-36.1; 0.00] | -12.7 [no null yet] |
| book (native) | 8.4 [26.0; 1.00] | -5.5 [-5.8; 0.50] | 9.9 [23.5; 1.00] | -21.9 [no null yet] |
| confluence | 6.0 [6.4; 1.00] | -6.3 [-1.9; 0.00] | 16.7 [20.4; 1.00] | -25.6 [-11.7; 0.50] |
| levels | -1.7 [11.6; 0.50] | -5.2 [10.8; 0.50] | 10.2 [22.3; 1.00] | 7.4 [14.5; 1.00] |
| levels (native) | 24.7 [65.6; 1.00] | 35.7 [63.2; 1.00] | -2.6 [-9.1; 0.50] | 23.7 [35.6; 1.00] |
| live | 14.4 [36.8; 1.00] | -0.2 [26.9; 1.00] | -1.9 [8.4; 1.00] | 11.7 [20.3; 1.00] |
| manual | 5.7 [6.8; 1.00] | 2.5 [10.7; 0.50] | 7.8 [25.6; 1.00] | -36.0 [-18.8; 0.50] |
| manual (native) | -2.3 [8.6; 1.00] | -24.2 [3.0; 0.50] | 0.6 [4.4; 0.50] | 10.8 [20.5; 1.00] |
| momentum | 12.6 [16.8; 1.00] | 1.1 [-2.2; 0.00] | 4.8 [1.9; 0.50] | -3.1 [10.9; 1.00] |
| momentum (native) | -6.6 [-9.2; 0.00] | 17.8 [19.5; 1.00] | 24.8 [21.8; 1.00] | -1.5 [-24.1; 0.00] |
| pullback | 19.2 [28.6; 1.00] | 33.3 [38.3; 1.00] | -17.4 [4.4; 1.00] | -4.4 [-2.0; 0.50] |
| pullback (native) | 26.4 [39.0; 1.00] | 2.9 [0.3; 0.50] | 11.5 [27.3; 1.00] | -8.8 [15.7; 1.00] |
| structure | -8.7 [-21.9; 0.00] | 33.9 [36.8; 1.00] | 4.6 [10.9; 1.00] | 2.3 [12.3; 1.00] |
| structure (native) | -10.2 [-4.4; 0.50] | -4.2 [-13.1; 0.50] | 14.6 [20.0; 1.00] | -10.3 [-4.1; 0.50] |
| tape | -3.7 [-30.3; 0.00] | -4.0 [1.5; 0.50] | -26.8 [-8.3; 0.50] | -3.9 [5.8; 0.50] |
| tape (native) | -0.8 [6.2; 0.50] | -30.1 [-13.6; 0.00] | -2.9 [38.9; 1.00] | 0.4 [-8.6; 0.00] |
| trend | 7.1 [23.7; 1.00] | 2.6 [1.0; 0.50] | 0.6 [18.6; 0.50] | 6.9 [14.4; 1.00] |
| trend (native) | -6.1 [1.3; 0.50] | 6.6 [26.3; 1.00] | -21.7 [-12.4; 0.00] | -20.7 [-28.8; 0.00] |
| xmarket | -6.7 [3.8; 0.50] | -33.7 [-26.6; 0.00] | -20.6 [-28.4; 0.00] | -1.4 [-8.4; 0.50] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels (native)|INFORMATION | 35.7 | 0.044 | 178.2 | 0.63 | 114.7 | 146.8 | {"2023": 36.1, "2024": 18.1, "2025": 27.2, "2026": 66.5} | -27.4 | 63.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 33.9 | 0.032 | 201.4 | 0.56 | 106.7 | 56.1 | {"2023": 34.0, "2024": 11.4, "2025": 26.0, "2026": 70.0} | -2.8 | 36.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|INFORMATION | 33.3 | 0.033 | 204.1 | 0.63 | 63.5 | 9.4 | {"2023": 37.4, "2024": 12.4, "2025": 40.6, "2026": 48.2} | -5.0 | 38.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 30.1 | 0.032 | 203.9 | 0.58 | 48.8 | 11.8 | {"2023": 18.9, "2024": 8.9, "2025": 64.5, "2026": 18.2} | -17.8 | 47.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|ACTIVITY | 26.4 | 0.021 | 182.0 | 0.62 | -13.7 | -6.4 | {"2023": 38.4, "2024": 21.5, "2025": 37.3, "2026": 15.6} | -12.5 | 39.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 24.8 | 0.026 | 374.1 | 0.53 | 9.1 | -128.0 | {"2023": -15.0, "2024": -7.7, "2025": 61.3, "2026": 32.7} | 3.0 | 21.8 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 24.7 | 0.031 | 154.0 | 0.58 | 61.1 | 161.8 | {"2023": 10.2, "2024": 17.3, "2025": 15.9, "2026": 48.4} | -40.9 | 65.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|TIME | 23.7 | 0.001 | 340.2 | 0.57 | 66.6 | 51.9 | {"2023": -10.0, "2024": 8.6, "2025": 9.0, "2026": 69.7} | -11.9 | 35.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 23.2 | 0.025 | 201.4 | 0.56 | -43.1 | -45.2 | {"2023": 0.0, "2024": 15.6, "2025": 57.7, "2026": -1.2} | -3.3 | 26.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback|ACTIVITY | 19.2 | 0.015 | 495.6 | 0.57 | 62.2 | -53.7 | {"2023": 3.2, "2024": 28.5, "2025": 6.2, "2026": 28.5} | -9.4 | 28.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 1.8%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.2%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 9.6%); P7 tm60 L6M 66.1 pts/wk, rank 98% (top 2.4%); H7 tm60 L6M 25.1 pts/wk, rank 85% (top 15.2%); A7 tm60 L6M 6.5 pts/wk, rank 66% (top 34.2%). Rank = share of ALL Asia cells with a lower trailing-26w result.

### PASS 2 (full grid, 7 brackets, selected pairs, own nulls): 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| bands (native)|PRICE | 40.7 | 0.044 | 132.3 | 0.63 | -5.1 | -43.4 | {"2023": -22.5, "2024": 39.8, "2025": 72.0, "2026": 24.8} | -27.5 | 68.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 40.4 | 0.065 | 180.0 | 0.64 | 47.6 | 5.0 | {"2023": 7.1, "2024": 46.0, "2025": 53.9, "2026": 28.4} | -17.9 | 58.3 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|PRICE | 32.5 | 0.038 | 181.1 | 0.54 | 66.8 | -18.5 | {"2023": -18.2, "2024": 3.9, "2025": 64.1, "2026": 45.2} | -6.8 | 39.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 30.5 | 0.038 | 144.0 | 0.58 | 95.3 | 161.8 | {"2023": 30.6, "2024": 20.4, "2025": 10.8, "2026": 65.8} | -43.4 | 73.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| trend|PRICE | 27.7 | 0.031 | 339.6 | 0.59 | 87.0 | 191.3 | {"2023": 5.3, "2024": 2.9, "2025": 47.3, "2026": 40.7} | -18.8 | 46.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 25.0 | 0.033 | 234.7 | 0.60 | 13.7 | 5.5 | {"2023": 10.0, "2024": 23.2, "2025": 40.6, "2026": 13.6} | 0.6 | 24.4 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|INFORMATION | 24.8 | 0.036 | 251.8 | 0.60 | 16.9 | 11.1 | {"2023": 28.8, "2024": 19.1, "2025": 8.7, "2026": 49.2} | 0.6 | 24.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 24.7 | 0.029 | 208.4 | 0.53 | 23.9 | 36.1 | {"2023": 3.4, "2024": 27.9, "2025": 36.5, "2026": 13.8} | -21.4 | 46.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|PRICE | 24.1 | 0.023 | 190.1 | 0.52 | -3.0 | -12.0 | {"2023": 17.0, "2024": 35.9, "2025": 4.0, "2026": 36.2} | -19.9 | 44.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels|PRICE | 22.8 | 0.027 | 175.9 | 0.57 | 14.1 | 15.1 | {"2023": 21.4, "2024": 11.7, "2025": 38.0, "2026": 18.4} | -7.2 | 30.1 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |

### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_400 | trend.trend_ma_hma.cross | {"len": 13, "width": 3, "hyst": 0.0} | sym30u | both | 7428 | 3631 | 401 | 0.83 | 5 / -601 / 763 / 1.00 | {"2023": 254.0, "2024": -1383.0, "2025": 13.0, "2026": 5811.0} |
| 2 | vol_350 | levels.levels_profile_nodes.break_native | {"n": 2, "k": 0.25} | sym8u | both | 6822 | 2719 | 315 | 1.00 | 25 / -1048 / 2016 / 1.00 | {"2023": -337.0, "2024": 673.0, "2025": 881.0, "2026": 6105.0} |
| 3 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | sym15u | both | 6751 | 922 | 421 | 1.00 | 5 / 1088 / 3330 / 1.00 | {"2023": -77.0, "2024": -853.0, "2025": 1402.0, "2026": 4274.0} |
| 4 | rng_20 | book.book_pslope.follow_native | {"L": 1800, "z": 1.5} | sym15u | both | 6709 | 1912 | 361 | 1.00 | 0 /  /  /  | {"2023": 18.0, "2024": -1198.0, "2025": 523.0, "2026": 5386.0} |
| 5 | vsess_80 | tape.tape_stack.r3_fade | {"k": 3} | sym15u | both | 6583 | 2943 | 415 | 1.00 | 0 /  /  /  | {"2023": -264.0, "2024": 444.0, "2025": -14.0, "2026": 7725.0} |
| 6 | rng_28 | tape.tape_stack.r5_fade | {"k": 4} | sym15u | both | 6537 | 3532 | 335 | 1.00 | 0 /  /  /  | {"2023": 604.0, "2024": 1361.0, "2025": 790.0, "2026": 4491.0} |
| 7 | mrenko_14 | book.book_imb.fade_native | {"lv": 1, "thr": 0.35, "sm": 60} | sym15u | both | 6464 | 3197 | 346 | 1.00 | 2 / -625 / 348 / 1.00 | {"2023": -276.0, "2024": 509.0, "2025": -3208.0, "2026": 6787.0} |
| 8 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym8u | both | 6461 | 2123 | 278 | 0.75 | 5 / -868 / -70 / 1.00 | {"2023": -19.0, "2024": -2170.0, "2025": 2679.0, "2026": 6279.0} |
| 9 | drb_240 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.01} | asym15u/30u | both | 6369 | 1236 | 398 | 0.80 | 5 / 904 / 3238 / 1.00 | {"2023": -38.0, "2024": -1031.0, "2025": 1666.0, "2026": 3644.0} |
| 10 | urenko_14 | book.book_pslope.follow_native | {"L": 900, "z": 1.0} | plain60/60 | both | 6194 | 2575 | 1058 | 1.00 | 2 / -1366 / -13 / 1.00 | {"2023": 241.0, "2024": -762.0, "2025": -4489.0, "2026": 6137.0} |
| 11 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 6125 | 2643 | 259 | 1.00 | 5 / -2371 / -215 / 1.00 | {"2023": -66.0, "2024": 51.0, "2025": -560.0, "2026": 6208.0} |
| 12 | vsess_120 | trend.trend_ma_t3.cross_native | {"len": 4, "width": 0.25, "ratio": 3} | sym8u | both | 6113 | 2645 | 424 | 1.00 | 5 / 696 / 2116 / 1.00 | {"2023": -698.0, "2024": -1679.0, "2025": 315.0, "2026": 5443.0} |
| 13 | vsess_600 | trend.trend_ma_hma.cross_native | {"len": 21, "width": 0.25, "ratio": 3} | asym15u/30u | both | 6097 | 2830 | 350 | 1.00 | 5 / 400 / 1654 / 1.00 | {"2023": -317.0, "2024": -2123.0, "2025": -897.0, "2026": 6782.0} |
| 14 | rng_56 | tape.tape_run.run_follow | {"thr": 6} | sym15u | both | 6078 | 1420 | 338 | 1.00 | 0 /  /  /  | {"2023": 130.0, "2024": 756.0, "2025": -302.0, "2026": 6988.0} |
| 15 | vsess_120 | bands.bands_atrchan.break_ext | {"n": 10, "atr": 14, "k": 2.0} | asym20u/10u | both | 6035 | 2241 | 408 | 0.75 | 5 / 88 / 424 / 1.00 | {"2023": -912.0, "2024": -2332.0, "2025": 99.0, "2026": 3938.0} |
| 16 | dib_400 | trend.trend_ma_hma.price | {"len": 50, "width": 0.25} | sym30u | both | 6019 | 1995 | 402 | 1.00 | 5 / 5 / 4244 / 1.00 | {"2023": 360.0, "2024": -1389.0, "2025": -886.0, "2026": 2708.0} |
| 17 | dib_1200 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | plain60/60 | both | 6002 | 2374 | 888 | 1.00 | 5 / -1154 / 720 / 1.00 | {"2023": -602.0, "2024": 1979.0, "2025": 1051.0, "2026": 7294.0} |
| 18 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 19 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym15u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -120.0, "2024": -2395.0, "2025": 2657.0, "2026": 5184.0} |
| 20 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym15u/30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |

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
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.46 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.14 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.85 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.86 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.88 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.93 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.66 |  |
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
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.32 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.79 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.79 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.25 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 0.99 | WEAK |
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
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.44 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.40 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.39 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.56 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.70 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.44 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.09 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.04 | WEAK |
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
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.36 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.32 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.23 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.03 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.84 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.17 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.06 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.14 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.22 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.28 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.80 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.17 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.61 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.32 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.69 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.25 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.32 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.14 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.06 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.11 |  |
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
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.59 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell vsess_600 trend.trend_ma_hma.cross sym8u L6M 235.4 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell pnf_5 book.book_cancel.ratio_follow sym15u L6M 334.8 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell dib_2000 barnative.barnative_speed.burst_fade plain60/60 L6M 269.0 pts/wk vs weak baselines K7 -22.5
## LEVEL triggers per session (supply/demand first, then Fibonacci, pivots, swing S/R, level stack, others): best cell per (module, variant) over all bar rows / parameters / brackets, last 26 weeks, >= 30 trades, in-sample pick: a LEAD needs the candidates-table nulls
### London (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | swing_atr_0.9 | {"n": 1, "F": 0} | sym15u / both | 35 | 4 | 174 | -696 | 158 | -362 | 1 | 208 |
| sd5 | break_native | swing_atr_0.9 | {"n": 1, "F": 0} | sym15u / both | 35 | 4 | 210 | -696 | 158 | -362 | 1 | 208 |
| sd5 | reject | vsess_600 | {"F": 0, "D": 15, "tol": 0.0} | sym15u / both | 35 | 875 | 40 | -111 | -353 | 1400 | 1 | 208 |
| sd5 | reject_flow | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 208 |
| sd5 | reject_flow_native | time_s_20 | {"F": 2, "D": 15} | sym15u / both | 32 | 659 | 82 | 156 | -196 | 765 | 1 | 208 |
| sd5 | reject_native | vsess_600 | {"F": 0, "D": 15, "tol": 0.0} | sym15u / both | 35 | 875 | 40 | -111 | -353 | 1400 | 1 | 208 |
| sdx15 | break | kagi_80 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 140 | 2579 | 645 | -535 | -454 | 2325 | 1 | 210 |
| sdx15 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 195 | 2214 | 105 | -102 | 862 | 1176 | 1 | 210 |
| sdx15 | lim_prox | kagi_112 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 156 | 1722 | -776 | 900 | -2080 | 1504 | 1 | 210 |
| sdx15 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 158 | 1967 | -30 | 572 | 2203 | 2707 | 1 | 210 |
| sdx15 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / both | 200 | 1025 | 1001 | -160 | -409 | -111 | 1 | 210 |
| sdx15 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 210 |
| sdx15 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 210 |
| sdx15 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 73 | 1895 | -252 | -737 | -146 | 1593 | 1 | 210 |
| sdx3 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 3088 | -168 | 318 | -923 | 2963 | 1 | 209 |
| sdx3 | lim_mid | kagi_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 276 | 3690 | 400 | 1269 | -2651 | 4082 | 1 | 209 |
| sdx3 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 358 | 4320 | 49 | 1608 | -1461 | 3654 | 1 | 209 |
| sdx3 | rej | vrb_240 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 293 | 2490 | 568 | 801 | -2604 | 2253 | 1 | 209 |
| sdx3 | rej_flow | wrenko_20 | {"d": "B", "F": 9} | sym15u / both | 71 | 1238 | -32 | -410 | -333 | 1105 | 1 | 209 |
| sdx3 | rej_native | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 245 | 3620 | 859 | 1354 | 441 | 3653 | 1 | 209 |
| sdx3 | rej_zone | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 219 | 3956 | 1228 | 1976 | -779 | 5574 | 1 | 209 |
| sdx3 | retest | mrenko_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 195 | 1881 | -279 | 106 | 782 | 2331 | 1 | 209 |
| sdx30 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 75 | 1445 | 411 | -743 | -552 | 1630 | 1 | 210 |
| sdx30 | lim_mid | kagi_56 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 112 | 1852 | -92 | 580 | -256 | 1934 | 1 | 210 |
| sdx30 | lim_prox | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 228 | 3089 | -6 | 17 | 1634 | 3464 | 1 | 210 |
| sdx30 | rej | frenko_28 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 35 | 712 | -95 | -341 | 622 | -109 | 1 | 210 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 31 | 633 | -473 | 306 | 239 | 176 | 1 | 210 |
| sdx30 | rej_native | kagi_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / long | 51 | 1413 | 260 | -189 | -77 | 1398 | 1 | 210 |
| sdx30 | rej_zone | time_m_45 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 130 | 2103 | -471 | -5 | -430 | 2659 | 1 | 210 |
| sdx30 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 30 | 570 | 110 | -6 | 144 | 250 | 1 | 210 |
| sdx5 | break | urenko_14 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 179 | 3068 | 197 | 1069 | 1759 | 2498 | 1 | 210 |
| sdx5 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 214 | 2364 | 118 | 1141 | -997 | 2486 | 1 | 210 |
| sdx5 | lim_prox | vrb_400 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 584 | 2703 | -466 | -813 | 2051 | 3816 | 1 | 210 |
| sdx5 | rej | vrb_700 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 216 | 2671 | -193 | -1603 | 1240 | 2253 | 1 | 210 |
| sdx5 | rej_flow | vrb_700 | {"d": "B", "F": 9} | plain60/60 / both | 83 | 1379 | -251 | -555 | 1072 | 759 | 1 | 210 |
| sdx5 | rej_native | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 155 | 2126 | -203 | -436 | 139 | 981 | 1 | 210 |
| sdx5 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 102 | 1959 | 163 | 674 | -953 | 2077 | 1 | 210 |
| sdx5 | retest | kagi_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 156 | 3004 | -581 | -1198 | -562 | 1728 | 1 | 210 |
| sdx60 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 31 | 1222 | -351 | -320 | 116 | 1749 | 1 | 209 |
| sdx60 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 162 | 2417 | -215 | 125 | -1666 | 2534 | 1 | 209 |
| sdx60 | lim_prox | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 3080 | 290 | 236 | -323 | 3089 | 1 | 209 |
| sdx60 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 32 | 1124 | -130 | -222 | -19 | 853 | 1 | 209 |
| sdx60 | rej_flow | vrb_400 | {"d": "E", "F": 9} | sym15u / long | 30 | 462 | 225 | 259 | 54 | 288 | 1 | 209 |
| sdx60 | rej_native | pnf_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 209 |
| sdx60 | rej_zone | tm900 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 104 | 2554 | -688 | -379 | 73 | 2243 | 1 | 209 |
| sdx_renko28 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 144 | 2263 | -119 | -618 | -1891 | 1174 | 1 | 209 |
| sdx_renko28 | lim_mid | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 157 | 2991 | -88 | -812 | -829 | 2811 | 1 | 209 |
| sdx_renko28 | lim_prox | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 156 | 3623 | -359 | -657 | -693 | 3375 | 1 | 209 |
| sdx_renko28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 1095 | 778 | -472 | 371 | -403 | 1 | 209 |
| sdx_renko28 | rej_flow | dol_350 | {"d": "E", "F": 0} | plain60/60 / both | 137 | 639 | 351 | -677 | 1111 | 521 | 1 | 209 |
| sdx_renko28 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 244 | 1564 | -622 | 717 | -706 | 1249 | 1 | 209 |
| sdx_renko28 | rej_zone | swing_pct_12 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 164 | 1703 | -149 | 463 | -1122 | 1532 | 1 | 209 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 85 | 1772 | -155 | -1444 | -732 | 1006 | 1 | 209 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 209 |
| sdx_rng28 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 261 | 3467 | -998 | 2482 | -838 | 2583 | 1 | 209 |
| sdx_rng28 | lim_prox | wrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 281 | 2565 | -697 | 820 | 191 | 5046 | 1 | 209 |
| sdx_rng28 | rej | kagi_56 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 93 | 1361 | 603 | 353 | -205 | 971 | 1 | 209 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / both | 166 | 1446 | 811 | -32 | 1520 | 715 | 1 | 209 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 209 |
| sdx_rng28 | rej_zone | tm15 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 1360 | 2116 | -1371 | -1023 | -2934 | 1860 | 1 | 209 |
| sdx_rng28 | retest | pnf_7 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 235 | 2538 | 635 | -1058 | -796 | 2576 | 1 | 209 |
| sdx_vol1100 | break | frenko_28 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 2638 | -348 | -213 | 189 | 2953 | 1 | 209 |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 209 | 3784 | 896 | 457 | 888 | 4785 | 1 | 209 |
| sdx_vol1100 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 244 | 3123 | 198 | -474 | 859 | 3530 | 1 | 209 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 285 | 1551 | -175 | 755 | -1556 | 357 | 1 | 209 |
| sdx_vol1100 | rej_flow | dol_350 | {"d": "E", "F": 0} | sym15u / short | 67 | 1136 | -141 | -656 | 353 | 1458 | 1 | 209 |
| sdx_vol1100 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 209 |
| sdx_vol1100 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 209 |
| sdx_vol1100 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 112 | 1778 | -246 | -234 | -609 | 1473 | 1 | 209 |
| fib15 | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 241 | 3378 | -219 | -1272 | -1703 | 4961 | 1 | 206 |
| fib15 | break_native | swing_atr_0.15 | {"n": 2, "k": 0.25} | sym15u / both | 241 | 3875 | -629 | -511 | 2215 | 4625 | 1 | 206 |
| fib15 | false_break | dchg_56 | {"M": 3, "k": 0.5} | sym15u / both | 243 | 4145 | 434 | 267 | -571 | 3261 | 1 | 206 |
| fib15 | false_break_native | dchg_56 | {"M": 1, "k": 0.0} | sym15u / both | 243 | 3977 | 403 | 295 | -878 | 3409 | 1 | 206 |
| fib15 | pullback | tm20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 353 | 1757 | -648 | -137 | -1019 | 339 | 1 | 206 |
| fib15 | pullback_native | dchg_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 199 | 2556 | -501 | -2108 | -1137 | 2771 | 1 | 206 |
| fib15 | reject | cusum_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 234 | 3738 | 129 | -213 | 1394 | 3664 | 1 | 206 |
| fib15 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3703 | -555 | 839 | 2164 | 4988 | 1 | 206 |
| fib15 | retest | dchg_80 | {"M": 6, "tol": 0.5} | sym15u / both | 203 | 3015 | -325 | 680 | -1531 | 4674 | 1 | 206 |
| fib15 | retest_native | time_m_30 | {"M": 6, "tol": 0.5} | sym15u / both | 195 | 2935 | -140 | -630 | -1409 | 3277 | 1 | 206 |
| fib5 | break | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 230 | 2681 | 1923 | 1384 | 1439 | 3364 | 1 | 206 |
| fib5 | break_native | swing_pct_12 | {"n": 3, "k": 0.5} | sym15u / both | 194 | 2808 | 120 | 166 | 886 | 3992 | 1 | 206 |
| fib5 | false_break | dchg_80 | {"M": 2, "k": 0.5} | sym15u / both | 215 | 3386 | 719 | 315 | -1355 | 3421 | 1 | 206 |
| fib5 | false_break_native | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 232 | 3243 | 1008 | -540 | 1443 | 3077 | 1 | 206 |
| fib5 | pullback | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 194 | 1590 | 1243 | 113 | 223 | 1728 | 1 | 206 |
| fib5 | pullback_native | time_m_20 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 321 | 1569 | 145 | -16 | 2079 | 2307 | 1 | 206 |
| fib5 | reject | cusum_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3943 | -37 | -55 | 1500 | 4956 | 1 | 206 |
| fib5 | reject_native | cusum_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 231 | 3849 | -85 | 719 | -430 | 3661 | 1 | 206 |
| fib5 | retest | tm2700 | {"M": 10, "tol": 0.5} | sym15u / both | 229 | 3220 | -742 | 398 | 1339 | 2419 | 1 | 206 |
| fib5 | retest_native | tm2700 | {"M": 10, "tol": 0.5} | sym15u / both | 231 | 3970 | -348 | 302 | 2508 | 3180 | 1 | 206 |
| fib60 | break | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 239 | 3070 | -415 | -857 | -1083 | 3353 | 1 | 207 |
| fib60 | break_native | cusum_10 | {"n": 2, "k": 0.25} | sym15u / both | 239 | 3697 | -809 | -1703 | -422 | 3980 | 1 | 207 |
| fib60 | false_break | kagi_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 222 | 3269 | 330 | 1054 | -527 | 4521 | 2 | 207 |
| fib60 | false_break_native | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2893 | 639 | 1418 | -423 | 3303 | 1 | 207 |
| fib60 | pullback | dchg_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 1207 | -624 | -75 | -649 | -545 | 1 | 207 |
| fib60 | pullback_native | swing_atr_0.9 | {"tol": 1.0, "conf": "body"} | sym15u / both | 116 | 1318 | 176 | 799 | -1861 | 1103 | 1 | 207 |
| fib60 | reject | cusum_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 182 | 2670 | -780 | -1183 | -730 | 2475 | 1 | 207 |
| fib60 | reject_native | drb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 202 | 3189 | -415 | -1238 | -218 | 2986 | 1 | 207 |
| fib60 | retest | vsess_300 | {"M": 3, "tol": 0.0} | sym15u / both | 179 | 3386 | -443 | -174 | -2425 | 996 | 1 | 207 |
| fib60 | retest_native | dchg_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 3614 | -723 | 596 | -705 | 4775 | 1 | 207 |
| fibr_dev | break | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 43 |
| fibr_dev | break_native | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 43 |
| fibr_dev | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 180 | 1774 | 127 | -330 | -1672 | 2055 | 1 | 43 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 640 | 2530 | -963 | -884 | -3116 | 2367 | 1 | 43 |
| fibr_dev | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 256 | 3197 | 564 | -144 | -10 | 1750 | 1 | 43 |
| fibr_dev | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 685 | 2174 | -110 | -1858 | -2517 | -951 | 1 | 43 |
| fibr_dev | retest | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 622 | 2751 | 131 | -652 | -1202 | 838 | 1 | 43 |
| fibr_dev | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 212 | 2228 | -96 | -768 | -515 | 2316 | 1 | 43 |
| fibr_pd | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 211 | 2784 | 1325 | -554 | -802 | 3958 | 1 | 43 |
| fibr_pd | break_native | pnf_5 | {"n": 2, "k": 0.25} | sym15u / both | 207 | 3135 | 51 | 239 | -950 | 2891 | 1 | 43 |
| fibr_pd | false_break | pnf_28 | {"M": 1, "k": 0.5} | sym8u / both | 176 | 1922 | -623 | -75 | -165 | 2455 | 2 | 43 |
| fibr_pd | false_break_native | pnf_28 | {"M": 3, "k": 0.5} | sym8u / both | 174 | 1857 | -580 | 114 | -478 | 2515 | 2 | 43 |
| fibr_pd | reject | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 203 | 2146 | 523 | -1414 | -889 | 2858 | 1 | 43 |
| fibr_pd | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 237 | 3803 | 503 | 321 | -2364 | 2894 | 1 | 43 |
| fibr_pd | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 155 | 2461 | 865 | 467 | -2371 | 816 | 1 | 43 |
| fibr_pd | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 202 | 2979 | -199 | -788 | -742 | 2241 | 1 | 43 |
| piv_cama | break | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -355 | -657 | -3166 | 2471 | 1 | 43 |
| piv_cama | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -439 | -657 | -3166 | 2471 | 1 | 43 |
| piv_cama | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -589 | -486 | -3125 | 2453 | 1 | 43 |
| piv_cama | false_break_native | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -536 | -486 | -3125 | 2453 | 1 | 43 |
| piv_cama | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 1882 | -418 | 222 | -1471 | 1356 | 1 | 43 |
| piv_cama | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 500 | 2839 | -84 | -1811 | 959 | 3224 | 1 | 43 |
| piv_cama | retest | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 43 |
| piv_cama | retest_native | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 43 |
| piv_floor | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 43 |
| piv_floor | break_native | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 43 |
| piv_floor | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 43 |
| piv_floor | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 43 |
| piv_floor | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / long | 48 | 1156 | 133 | 855 | 1142 | 2067 | 1 | 43 |
| piv_floor | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 2321 | 417 | 1571 | -187 | 1903 | 1 | 43 |
| piv_floor | retest | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 43 |
| piv_floor | retest_native | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 43 |
| piv_wf | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 199 | 2656 | -333 | -1729 | -430 | 1511 | 1 | 43 |
| piv_wf | break_native | urenko_40 | {"n": 3, "k": 0.5} | sym15u / both | 202 | 2880 | -608 | -890 | -364 | 3606 | 1 | 43 |
| piv_wf | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 199 | 2887 | -211 | -1555 | -414 | 1976 | 1 | 43 |
| piv_wf | false_break_native | kagi_80 | {"M": 1, "k": 0.0} | sym15u / both | 199 | 2636 | -144 | -1563 | -448 | 1481 | 1 | 43 |
| piv_wf | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 147 | 1472 | 651 | 362 | -430 | 1487 | 1 | 43 |
| piv_wf | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 230 | 3435 | -674 | 1015 | -1014 | 4860 | 1 | 43 |
| piv_wf | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 174 | 2164 | -5 | -1635 | -1545 | 1610 | 1 | 43 |
| piv_wf | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3307 | -134 | -1185 | -1620 | 3176 | 1 | 43 |
| swcluster | break | kagi_56 | {"n": 2, "k": 0.25} | sym15u / both | 50 | 1670 | -518 | -793 | -14 | 465 | 1 | 44 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1656 | -586 | -594 | -193 | 450 | 1 | 44 |
| swcluster | false_break | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 74 | 1459 | -140 | -948 | 37 | 490 | 1 | 44 |
| swcluster | false_break_native | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 68 | 1438 | -192 | -927 | 429 | 1017 | 1 | 44 |
| swcluster | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | -808 | 524 | -708 | 198 | 1 | 44 |
| swcluster | reject_native | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 53 | 1389 | 5 | -698 | -300 | 1666 | 1 | 44 |
| swcluster | retest | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 47 | 1509 | -132 | -310 | -291 | 794 | 1 | 44 |
| swcluster | retest_native | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 48 | 1304 | -249 | -194 | -305 | 331 | 1 | 44 |
| swsr15 | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 2311 | 223 | -327 | -8 | 3157 | 1 | 44 |
| swsr15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 247 | 2675 | -145 | -1131 | -495 | 2962 | 1 | 44 |
| swsr15 | false_break | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 170 | 1830 | -590 | -550 | -3102 | 2238 | 1 | 44 |
| swsr15 | false_break_native | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 92 | 1864 | -177 | 269 | -551 | 3234 | 1 | 44 |
| swsr15 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 241 | 2478 | 214 | -863 | -296 | 4375 | 1 | 44 |
| swsr15 | reject_native | vrb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 275 | 3265 | 226 | -1654 | -1857 | 3406 | 1 | 44 |
| swsr15 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3116 | -742 | -538 | 263 | 2136 | 1 | 44 |
| swsr15 | retest_native | pnf_28 | {"M": 6, "tol": 0.5} | sym15u / both | 188 | 2587 | -36 | 852 | 31 | 1170 | 1 | 44 |
| swsr5 | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 1969 | -49 | 176 | -191 | 2616 | 1 | 44 |
| swsr5 | break_native | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 2084 | -669 | -1018 | 182 | 1811 | 1 | 44 |
| swsr5 | false_break | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 171 | 2538 | 48 | 76 | -1945 | 2966 | 1 | 44 |
| swsr5 | false_break_native | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 168 | 2788 | 236 | -264 | -2437 | 2402 | 1 | 44 |
| swsr5 | reject | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 143 | 1638 | -293 | -1179 | -1318 | 1907 | 1 | 44 |
| swsr5 | reject_native | kagi_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 236 | 3237 | 265 | 1368 | 654 | 2042 | 1 | 44 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | plain60/60 / both | 529 | 2659 | -716 | -995 | -709 | 3038 | 1 | 44 |
| swsr5 | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 268 | 2360 | 398 | -1263 | -1865 | 3266 | 1 | 44 |
| swsr60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 173 | 2714 | -1019 | -989 | 1889 | 3578 | 1 | 44 |
| swsr60 | break_native | kagi_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 287 | 2084 | -313 | -2637 | -700 | 2284 | 1 | 44 |
| swsr60 | false_break | vrb_240 | {"M": 3, "k": 0.5} | sym15u / both | 193 | 1724 | -21 | -761 | -1166 | 2949 | 1 | 44 |
| swsr60 | false_break_native | vrb_240 | {"M": 1, "k": 0.0} | sym15u / both | 192 | 1695 | 426 | -888 | -896 | 2746 | 1 | 44 |
| swsr60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 171 | 2075 | -1036 | -2049 | -1412 | 1142 | 1 | 44 |
| swsr60 | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 193 | 2648 | -423 | -1524 | 1834 | 2876 | 1 | 44 |
| swsr60 | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 137 | 1667 | -201 | 137 | 1485 | 3122 | 1 | 44 |
| swsr60 | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 166 | 2367 | -533 | -15 | -85 | 3016 | 1 | 44 |
| stack | break | kagi_20 | {"k": 3, "cw": 1.0} | sym15u / both | 148 | 3437 | 176 | 1393 | -17 | 1971 | 1 | 214 |
| stack | break_native | frenko_28 | {"k": 2, "cw": 0.5} | sym15u / both | 236 | 2805 | -674 | 49 | 2094 | 1768 | 1 | 214 |
| stack | reject | vsess_120 | {"k": 2, "cw": 0.5} | sym8u / both | 94 | 2473 | 270 | -72 | -962 | 2621 | 2 | 214 |
| stack | reject_native | pnf_14 | {"k": 2, "cw": 0.5} | sym15u / both | 194 | 3864 | -615 | -258 | -63 | 4021 | 1 | 214 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 212 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 212 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 212 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 212 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 212 |
| book_walls | reject_native | vrb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 53 | 1284 | -323 | 34 | 293 | 1359 | 1 | 212 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 212 |
| book_walls | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym15u / both | 31 | 948 | -230 | -711 | 334 | 598 | 1 | 212 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 197 | 2357 | -978 | -1528 | -3048 | 1807 | 2 | 214 |
| book_walls_loose | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 2309 | -1415 | 296 | -1880 | 2748 | 2 | 214 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 214 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 214 |
| book_walls_loose | reject | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 170 | 3163 | -1118 | 31 | -1206 | 3714 | 1 | 214 |
| book_walls_loose | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 208 | 3375 | -1082 | -93 | -1302 | 3631 | 1 | 214 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3516 | 15 | -764 | -863 | 4040 | 1 | 214 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1 | 214 |
| channel | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 253 | 3125 | -354 | -1559 | 474 | 4044 | 1 | 44 |
| channel | break_native | vrb_400 | {"n": 3, "k": 0.5} | sym15u / both | 254 | 3281 | 380 | 1107 | 291 | 3588 | 1 | 44 |
| channel | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 172 | 2909 | -148 | -291 | -2237 | 2992 | 1 | 44 |
| channel | false_break_native | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3344 | 373 | 1739 | 1102 | 4639 | 1 | 44 |
| channel | reject | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 118 | 2681 | 332 | 48 | -1806 | 2627 | 1 | 44 |
| channel | reject_native | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3978 | -529 | -363 | -2591 | 3263 | 1 | 44 |
| channel | retest | vrb_400 | {"M": 6, "tol": 0.5} | plain60/60 / both | 587 | 2708 | 74 | -1196 | -1245 | 1159 | 1 | 44 |
| channel | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 44 |
| fvg15 | break | kagi_80 | {"n": 3, "k": 0.5} | sym15u / both | 83 | 1769 | -239 | 176 | 876 | 1390 | 1 | 44 |
| fvg15 | break_native | wrenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2142 | 699 | 1173 | -2521 | 1701 | 1 | 44 |
| fvg15 | false_break | pnf_10 | {"M": 3, "k": 0.5} | plain60/60 / short | 131 | 1273 | 165 | -386 | -465 | 1786 | 1 | 44 |
| fvg15 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | plain60/60 / short | 130 | 1094 | 257 | -577 | -633 | 1723 | 1 | 44 |
| fvg15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 3384 | -99 | 1317 | -307 | 4690 | 1 | 44 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 167 | 4419 | -178 | 432 | 336 | 5177 | 1 | 44 |
| fvg15 | retest | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 1682 | -181 | -793 | -565 | 1944 | 1 | 44 |
| fvg15 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 158 | 2957 | 1199 | 1020 | -199 | 3816 | 1 | 44 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 44 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 44 |
| fvg5 | false_break | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 44 |
| fvg5 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 44 |
| fvg5 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 239 | 2756 | 214 | -1882 | -387 | 2095 | 1 | 44 |
| fvg5 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 242 | 2182 | 193 | -1316 | -820 | 1313 | 1 | 44 |
| fvg5 | retest | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 172 | 2473 | -230 | -1137 | -66 | 1925 | 1 | 44 |
| fvg5 | retest_native | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 189 | 3090 | -276 | -1553 | 384 | 2624 | 1 | 44 |
| gaps | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 93 | 2458 | 515 | -722 | -3227 | 1532 | 1 | 215 |
| gaps | break_native | pnf_7 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2868 | -251 | -161 | -3421 | 2136 | 1 | 215 |
| gaps | false_break | pasl_20 | {"M": 1, "k": 0.0} | sym15u / both | 124 | 2164 | 292 | -70 | -125 | 3244 | 1 | 215 |
| gaps | false_break_native | pasl_20 | {"M": 3, "k": 0.5} | sym15u / both | 120 | 2263 | -51 | -233 | 70 | 3737 | 1 | 215 |
| gaps | reject | dlt_70 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2488 | 821 | -78 | -1259 | 2706 | 1 | 215 |
| gaps | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 147 | 2332 | -600 | 3 | -1106 | 2770 | 1 | 215 |
| gaps | retest | vrb_240 | {"M": 3, "tol": 0.0} | plain60/60 / both | 151 | 1947 | 258 | -934 | 35 | 1200 | 1 | 215 |
| gaps | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 100 | 2963 | -29 | 441 | -1448 | 3370 | 1 | 215 |
| mmove | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 210 | 2588 | -853 | -45 | -2503 | 1001 | 1 | 44 |
| mmove | break_native | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 202 | 2486 | -450 | 418 | -1675 | 1326 | 1 | 44 |
| mmove | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2557 | -462 | -577 | -579 | 2977 | 1 | 44 |
| mmove | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 225 | 2897 | -838 | -578 | -949 | 3394 | 1 | 44 |
| mmove | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 481 | 3098 | 409 | 646 | -265 | 2767 | 1 | 44 |
| mmove | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 214 | 3153 | -70 | 1060 | -1089 | 3669 | 1 | 44 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 44 |
| mmove | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 44 |
| ob15 | break | wrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 81 | 1091 | 244 | -107 | 133 | 1385 | 1 | 44 |
| ob15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 75 | 1244 | 663 | -890 | -72 | 1890 | 1 | 44 |
| ob15 | false_break | vrb_240 | {"M": 1, "k": 0.0} | plain60/60 / both | 86 | 851 | -489 | -513 | -273 | 1547 | 1 | 44 |
| ob15 | false_break_native | vrb_240 | {"M": 1, "k": 0.0} | plain60/60 / both | 86 | 851 | -489 | -513 | -273 | 1547 | 1 | 44 |
| ob15 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 1376 | 323 | -1331 | 1080 | 1930 | 1 | 44 |
| ob15 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 71 | 1184 | 775 | -274 | 61 | 2027 | 1 | 44 |
| ob15 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1142 | 267 | -325 | 553 | 1702 | 1 | 44 |
| ob15 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 87 | 1197 | 155 | -638 | 61 | 1172 | 1 | 44 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 44 |
| ob5 | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 44 |
| ob5 | false_break | pnf_5 | {"M": 3, "k": 0.5} | plain60/60 / both | 200 | 1963 | -56 | 924 | 346 | 1463 | 1 | 44 |
| ob5 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 126 | 2383 | -849 | -727 | 1517 | 1531 | 1 | 44 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 129 | 1424 | 71 | -876 | -916 | 1490 | 1 | 44 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 | 1981 | -488 | -1059 | -729 | 757 | 1 | 44 |
| ob5 | retest | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 97 | 2215 | -850 | -680 | 932 | 2095 | 1 | 44 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 111 | 2232 | -468 | -959 | 1160 | 2143 | 1 | 44 |
| opens | break | renko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 3946 | 43 | 1332 | 422 | 3112 | 2 | 215 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 215 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 215 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 215 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 215 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 215 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 215 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 215 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1 | 215 |
| prior_day | break_native | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 103 | 2083 | 433 | -525 | -990 | 3127 | 1 | 215 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 2376 | 649 | -33 | -1668 | 3829 | 1 | 215 |
| prior_day | false_break_native | swing_atr_0.1 | {"M": 3, "k": 0.5} | sym15u / both | 126 | 2405 | 621 | -246 | -702 | 3078 | 1 | 215 |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 105 | 1827 | -426 | -804 | -662 | 720 | 1 | 215 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 215 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 1 | 215 |
| prior_day | retest_native | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 191 | 2712 | -110 | -383 | 424 | 2187 | 1 | 215 |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 162 | 2957 | -620 | 59 | -1689 | 2002 | 1 | 214 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 214 |
| profile_nodes | false_break | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 2292 | -55 | -984 | -1066 | 1894 | 1 | 214 |
| profile_nodes | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 208 | 2676 | -200 | -70 | 183 | 1964 | 2 | 214 |
| profile_nodes | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 152 | 2817 | -450 | -1140 | -2494 | 1640 | 1 | 214 |
| profile_nodes | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | sym15u / both | 204 | 2821 | -98 | -360 | 235 | 2346 | 2 | 214 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 214 |
| profile_nodes | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 214 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 1 | 215 |
| profile_va | break_native | renko_28 | {"n": 1, "k": 0.5} | sym8u / both | 143 | 2591 | -66 | -1416 | -848 | 2717 | 2 | 215 |
| profile_va | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 120 | 2493 | -419 | -437 | -1179 | 2786 | 1 | 215 |
| profile_va | false_break_native | tm30 | {"M": 2, "k": 0.5} | sym15u / both | 162 | 2584 | 299 | -691 | -241 | 3689 | 1 | 215 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 215 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 215 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym15u / both | 133 | 3198 | 93 | -1886 | -354 | 2602 | 1 | 215 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 215 |
| round | break | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 215 |
| round | break_native | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 215 |
| round | false_break | pasl_10 | {"M": 3, "k": 0.5} | plain60/60 / both | 717 | 3076 | -134 | 387 | -1885 | 3447 | 1 | 215 |
| round | false_break_native | dchg_112 | {"M": 2, "k": 0.5} | sym15u / both | 166 | 3286 | 139 | -661 | -1168 | 2614 | 1 | 215 |
| round | reject | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 405 | 3731 | -1516 | 737 | 448 | 5872 | 1 | 215 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 215 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 215 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 215 |
| session_hl | break | pasl_56 | {"n": 1, "k": 0.0} | sym15u / both | 139 | 1771 | -1102 | -336 | -292 | 2220 | 1 | 211 |
| session_hl | break_native | pasl_20 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2654 | -107 | 389 | -378 | 3494 | 1 | 211 |
| session_hl | false_break | renko_14 | {"M": 2, "k": 0.5} | asym20u/10u / both | 130 | 1640 | -516 | 85 | -1030 | 1483 | 2 | 211 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 211 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 211 |
| session_hl | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 1805 | -162 | -987 | -1228 | -754 | 1 | 211 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 211 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 1 | 211 |
| trendline | break | mrenko_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 490 | 2957 | -338 | -167 | -927 | 697 | 1 | 44 |
| trendline | break_native | mrenko_14 | {"n": 2, "k": 0.25} | sym15u / both | 234 | 3004 | 8 | 371 | -320 | 5564 | 1 | 44 |
| trendline | false_break | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / both | 540 | 1894 | 260 | -1042 | -2133 | -658 | 1 | 44 |
| trendline | false_break_native | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / long | 281 | 1886 | 383 | -246 | -48 | 1129 | 1 | 44 |
| trendline | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 44 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 44 |
| trendline | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 225 | 2709 | 329 | -350 | 447 | 2557 | 1 | 44 |
| trendline | retest_native | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 220 | 3008 | -48 | -1940 | 1275 | 1937 | 1 | 44 |
| uw_dp | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 215 |
| uw_dp | break_native | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 215 |
| uw_dp | false_break | dchg_40 | {"M": 2, "k": 0.5} | sym15u / both | 109 | 2734 | 0 | 0 | 530 | 3624 | 1 | 215 |
| uw_dp | false_break_native | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 215 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 112 | 1964 | 0 | 0 | 365 | 1874 | 1 | 215 |
| uw_dp | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 122 | 2086 | 0 | 0 | -468 | 1673 | 1 | 215 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 215 |
| uw_dp | retest_native | dchg_40 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2424 | 0 | 0 | 561 | 1869 | 1 | 215 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1 | 214 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 214 |
| uw_ndx | false_break | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 214 |
| uw_ndx | false_break_native | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 214 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 214 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 214 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 214 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 214 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 214 |
| uw_qqq | break_native | renko_20 | {"n": 2, "k": 0.0} | sym8u / both | 145 | 2846 | 0 | 48 | 263 | 2703 | 2 | 214 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 214 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 214 |
| uw_qqq | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 116 | 2612 | 0 | 241 | -787 | -337 | 1 | 214 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 214 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 214 |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1 | 214 |
| vwap | break | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 5484 | 276 | -1123 | -2301 | 6752 | 2 | 214 |
| vwap | break_native | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 227 | 5738 | 534 | -1080 | -3184 | 7299 | 2 | 214 |
| vwap | false_break | dchg_56 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2837 | 298 | -962 | 1185 | 2960 | 1 | 214 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 214 |
| vwap | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 248 | 4751 | -37 | -1718 | 768 | 7179 | 2 | 214 |
| vwap | reject_native | cdr_100 | {"tol": 0.5, "conf": "body"} | sym8u / both | 233 | 5846 | 667 | 1147 | -135 | 5737 | 2 | 214 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 214 |
| vwap | retest_native | cdr_100 | {"M": 10, "tol": 0.5} | sym8u / both | 218 | 4634 | 959 | 362 | -947 | 5800 | 2 | 214 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 213 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 213 |
| vwap_bands | false_break | tm15 | {"M": 1, "k": 0.5} | plain60/60 / both | 705 | 3509 | -455 | -467 | -528 | 2159 | 2 | 213 |
| vwap_bands | false_break_native | tm15 | {"M": 1, "k": 0.5} | plain60/60 / both | 706 | 3500 | 1222 | -1157 | 1401 | 1262 | 2 | 213 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 213 |
| vwap_bands | reject_native | tm20 | {"tol": 1.0, "conf": "close"} | sym15u / both | 547 | 4046 | -1550 | -51 | -2596 | 3340 | 2 | 213 |
| vwap_bands | retest | drb_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 684 | 3403 | 537 | -777 | -29 | 2793 | 1 | 213 |
| vwap_bands | retest_native | vsess_30 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 3675 | 581 | -1198 | -2832 | 5778 | 1 | 213 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 1 | 215 |
| week_month | break_native | swing_atr_0.25 | {"n": 2, "k": 0.25} | sym15u / both | 43 | 1508 | -111 | -183 | -1226 | 1563 | 1 | 215 |
| week_month | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 215 |
| week_month | false_break_native | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 215 |
| week_month | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 38 | 1618 | 133 | -162 | -2232 | 2609 | 1 | 215 |
| week_month | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 32 | 1579 | -70 | -765 | -196 | 1671 | 1 | 215 |
| week_month | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 33 | 1229 | 124 | -30 | -141 | 1120 | 1 | 215 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 1 | 215 |
| zones | break | tm1200 | {"n": 3, "k": 0.0} | sym8u / both | 102 | 2258 | 351 | 90 | -1805 | 2876 | 2 | 214 |
| zones | break_native | renko_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 195 | 2650 | -114 | -424 | -736 | 2949 | 2 | 214 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 214 |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 112 | 1825 | -112 | -996 | 314 | 2093 | 2 | 214 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 214 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 214 |
| zones | retest | tib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 128 | 2375 | -1292 | 285 | 258 | 2085 | 1 | 214 |
| zones | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 102 | 2223 | -765 | 332 | -877 | 1559 | 1 | 214 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd15 | reject | vol_750 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 56 | 67 | -346 | -258 | 279 | 1 | 208 |
| sd15 | reject_native | vol_750 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 56 | 67 | -346 | -258 | 279 | 1 | 208 |
| sd5 | break | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 208 |
| sd5 | break_native | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 208 |
| sd5 | reject | dib_1200 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 32 | 978 | 63 | -174 | -560 | 1085 | 1 | 208 |
| sd5 | reject_flow | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 208 |
| sd5 | reject_flow_native | drb_240 | {"F": 2, "D": 15} | sym15u / both | 31 | 689 | -139 | 92 | -489 | 882 | 1 | 208 |
| sd5 | reject_native | dib_1200 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 32 | 978 | 63 | -174 | -560 | 1085 | 1 | 208 |
| sd5 | retest | rng_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 31 | -236 | -98 | 243 | -179 | -182 | 1 | 208 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 1 | 208 |
| sdx15 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 171 | 2399 | -85 | 715 | 2594 | 3384 | 1 | 209 |
| sdx15 | lim_mid | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 333 | 2976 | -2286 | -2403 | -427 | 2983 | 1 | 209 |
| sdx15 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 373 | 3815 | 30 | -593 | -1777 | 5127 | 1 | 209 |
| sdx15 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 68 | 2107 | -1412 | -869 | 341 | 1563 | 1 | 209 |
| sdx15 | rej_flow | vrb_400 | {"d": "A", "F": 0} | sym15u / both | 74 | 1289 | -104 | 202 | -1621 | 805 | 1 | 209 |
| sdx15 | rej_native | kagi_56 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 2039 | -160 | -2368 | -1749 | 2557 | 1 | 209 |
| sdx15 | rej_zone | drb_3500 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 328 | 3842 | -1486 | 372 | -1207 | 1281 | 1 | 209 |
| sdx15 | retest | kagi_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 87 | 1671 | 1303 | -626 | 3804 | 2010 | 1 | 209 |
| sdx3 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 350 | 3483 | 1458 | 3578 | 5139 | 4750 | 1 | 208 |
| sdx3 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 182 | 3365 | 26 | 2134 | 1935 | 3244 | 1 | 208 |
| sdx3 | lim_prox | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 224 | 3509 | 1324 | 128 | -1502 | 4960 | 1 | 208 |
| sdx3 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 475 | 3002 | -2715 | -1978 | -5508 | 1958 | 1 | 208 |
| sdx3 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / long | 156 | 3037 | 6 | 1057 | -3441 | 2950 | 1 | 208 |
| sdx3 | rej_native | mrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 208 |
| sdx3 | rej_zone | pasl_10 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 542 | 3335 | -1472 | -1840 | -3991 | 3170 | 1 | 208 |
| sdx3 | retest | kagi_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 245 | 2392 | 2042 | 2685 | 4969 | 3185 | 1 | 208 |
| sdx30 | break | pnf_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 79 | 1933 | -372 | 1333 | 866 | 1755 | 1 | 209 |
| sdx30 | lim_mid | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 52 | 1565 | 12 | -897 | 111 | 634 | 1 | 209 |
| sdx30 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 142 | 2308 | -245 | -373 | 1505 | 5248 | 1 | 209 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 73 | 1261 | -467 | -838 | -1738 | 1427 | 1 | 209 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 146 | 1480 | -676 | -2116 | -2930 | 1823 | 1 | 209 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 209 |
| sdx30 | rej_zone | pasl_40 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / long | 88 | 2061 | 108 | -188 | -665 | 2504 | 1 | 209 |
| sdx30 | retest | pnf_28 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 35 | 976 | -101 | -1016 | 521 | 952 | 1 | 209 |
| sdx5 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 128 | 2348 | 760 | 872 | 1375 | 1924 | 1 | 209 |
| sdx5 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 4263 | -912 | -271 | 1146 | 4807 | 1 | 209 |
| sdx5 | lim_prox | urenko_80 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 214 | 4370 | 1480 | 714 | 2473 | 2468 | 1 | 209 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 216 | 2627 | -830 | 131 | -3477 | 4401 | 1 | 209 |
| sdx5 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / both | 258 | 1062 | -1205 | -898 | -1943 | 1771 | 1 | 209 |
| sdx5 | rej_native | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 209 |
| sdx5 | rej_zone | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 209 |
| sdx5 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 165 | 2309 | 1186 | -216 | 3671 | 2698 | 1 | 209 |
| sdx60 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 52 | 1464 | 466 | 334 | 762 | 926 | 1 | 208 |
| sdx60 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 417 | 1570 | -1168 | -222 | -1705 | 689 | 1 | 208 |
| sdx60 | lim_prox | renko_28 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 155 | 1357 | -527 | -1413 | 925 | 778 | 1 | 208 |
| sdx60 | rej | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 124 | 2540 | -595 | -1785 | -237 | 2453 | 1 | 208 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / long | 90 | 1309 | 89 | -465 | -399 | 884 | 1 | 208 |
| sdx60 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 208 |
| sdx60 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 208 |
| sdx_renko28 | break | wrenko_10 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 339 | 2291 | 953 | -446 | 6066 | 2557 | 1 | 208 |
| sdx_renko28 | lim_mid | kagi_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 475 | 4203 | 121 | -178 | 3832 | 2308 | 1 | 208 |
| sdx_renko28 | lim_prox | pnf_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 264 | 3229 | 883 | -1326 | -486 | 1723 | 1 | 208 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 417 | 2601 | -2519 | -2626 | -4344 | 2070 | 1 | 208 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 202 | 2765 | 740 | -3083 | 894 | 2859 | 1 | 208 |
| sdx_renko28 | rej_native | urenko_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 208 |
| sdx_renko28 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 208 |
| sdx_renko28 | retest | pnf_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 288 | 2991 | 1782 | 2559 | 1355 | 2869 | 1 | 208 |
| sdx_rng28 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 487 | 4615 | 1288 | 2874 | 6639 | 8079 | 1 | 208 |
| sdx_rng28 | lim_mid | kagi_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 502 | 4204 | -595 | -701 | -2 | 1835 | 1 | 208 |
| sdx_rng28 | lim_prox | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 493 | 5342 | 520 | 1267 | -40 | 7530 | 1 | 208 |
| sdx_rng28 | rej | mrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 504 | 2856 | -984 | -1842 | -5463 | 2791 | 1 | 208 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / long | 172 | 2052 | 2014 | -466 | -281 | 3800 | 1 | 208 |
| sdx_rng28 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 431 | 3332 | 1328 | -4047 | 1358 | 3443 | 1 | 208 |
| sdx_rng28 | rej_zone | frenko_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4594 | 559 | -3692 | -3237 | 3340 | 1 | 208 |
| sdx_rng28 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 445 | 3741 | 1098 | -711 | 4872 | 5506 | 1 | 208 |
| sdx_vol1100 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 432 | 3924 | -781 | 1019 | 5689 | 4212 | 1 | 208 |
| sdx_vol1100 | lim_mid | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1444 | 5146 | -307 | -267 | -7260 | 5686 | 1 | 208 |
| sdx_vol1100 | lim_prox | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1412 | 4616 | 1989 | -3 | -5487 | 5378 | 1 | 208 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 429 | 5058 | -1453 | -1789 | -1589 | 7224 | 1 | 208 |
| sdx_vol1100 | rej_flow | vrb_700 | {"d": "E", "F": 0} | sym15u / both | 321 | 2969 | -6 | 1488 | -104 | 2957 | 1 | 208 |
| sdx_vol1100 | rej_native | kagi_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 477 | 3771 | -172 | -664 | -3831 | 5515 | 1 | 208 |
| sdx_vol1100 | rej_zone | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4710 | -906 | -898 | -3639 | 4361 | 1 | 208 |
| sdx_vol1100 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 398 | 4494 | -381 | -1960 | 2674 | 5777 | 1 | 208 |
| fib15 | break | dchg_20 | {"n": 1, "k": 0.0} | sym15u / both | 346 | 3526 | 555 | 2339 | 3572 | 2098 | 1 | 205 |
| fib15 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 309 | 3889 | 1224 | -1144 | 3109 | 4406 | 1 | 205 |
| fib15 | false_break | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 356 | 3289 | -131 | 2456 | 3878 | 2191 | 1 | 205 |
| fib15 | false_break_native | dchg_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 985 | 3299 | 448 | 1917 | -2094 | 2890 | 1 | 205 |
| fib15 | pullback | cusum_20 | {"tol": 0.5, "conf": "body"} | sym15u / long | 114 | 2641 | 1691 | -120 | -875 | 3772 | 1 | 205 |
| fib15 | pullback_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / long | 106 | 2608 | 1196 | 45 | -914 | 4367 | 1 | 205 |
| fib15 | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 361 | 4272 | -1022 | 147 | 2523 | 4051 | 1 | 205 |
| fib15 | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 361 | 5051 | 722 | -694 | 2601 | 3935 | 1 | 205 |
| fib15 | retest | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 205 |
| fib15 | retest_native | time_s_10 | {"M": 3, "tol": 0.0} | sym15u / both | 353 | 5325 | 2094 | 2404 | 1544 | 5364 | 1 | 205 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 392 | 4876 | -635 | -1541 | 2534 | 5721 | 1 | 205 |
| fib5 | break_native | tick_500 | {"n": 2, "k": 0.25} | sym15u / both | 379 | 3626 | 626 | -2593 | 4475 | 4380 | 1 | 205 |
| fib5 | false_break | rng_28 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 5122 | 509 | -759 | 2913 | 3226 | 1 | 205 |
| fib5 | false_break_native | rng_28 | {"M": 2, "k": 0.5} | sym15u / both | 386 | 5486 | 100 | -1323 | 1351 | 3593 | 1 | 205 |
| fib5 | pullback | time_m_4 | {"tol": 0.0, "conf": "close"} | sym15u / both | 245 | 2553 | -502 | 793 | 193 | 4526 | 1 | 205 |
| fib5 | pullback_native | dlt_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 351 | 3050 | -717 | -1303 | -243 | 5196 | 1 | 205 |
| fib5 | reject | mom_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 390 | 4482 | 1115 | -1670 | 884 | 7049 | 1 | 205 |
| fib5 | reject_native | drb_240 | {"tol": 0.0, "conf": "close"} | sym15u / both | 511 | 4078 | 750 | 204 | -1171 | 5685 | 1 | 205 |
| fib5 | retest | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 205 |
| fib5 | retest_native | vsess_120 | {"M": 3, "tol": 0.0} | asym20u/10u / both | 349 | 5845 | -496 | -1256 | 2672 | 6272 | 2 | 205 |
| fib60 | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 291 | 4260 | 834 | -351 | -346 | 2844 | 1 | 206 |
| fib60 | break_native | dlt_45 | {"n": 3, "k": 0.5} | sym15u / both | 318 | 5222 | -1532 | -573 | 828 | 5732 | 1 | 206 |
| fib60 | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 318 | 4397 | 1494 | 2356 | 2535 | 5981 | 1 | 206 |
| fib60 | false_break_native | swing_pct_8 | {"M": 2, "k": 0.5} | sym15u / both | 308 | 4583 | 2331 | 2922 | 2124 | 5925 | 1 | 206 |
| fib60 | pullback | drb_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 1829 | -926 | 1810 | -1577 | 1577 | 1 | 206 |
| fib60 | pullback_native | tick_5000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 2539 | -702 | 2326 | 50 | 1531 | 1 | 206 |
| fib60 | reject | tick_300 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 4010 | -1870 | -1434 | 2221 | 3583 | 1 | 206 |
| fib60 | reject_native | dib_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 303 | 4392 | 0 | -661 | -328 | 4902 | 1 | 206 |
| fib60 | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 272 | 4507 | 25 | 415 | -3066 | 4468 | 1 | 206 |
| fib60 | retest_native | renko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 4745 | 238 | -75 | 4108 | 2780 | 1 | 206 |
| fibr_dev | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 43 |
| fibr_dev | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 43 |
| fibr_dev | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 460 | 3921 | 2689 | 822 | 2042 | 4742 | 1 | 43 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 452 | 4732 | 2585 | -852 | 3835 | 5674 | 1 | 43 |
| fibr_dev | reject | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 3087 | 936 | 1508 | -135 | 2125 | 1 | 43 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 448 | 4974 | 1168 | 2667 | 817 | 4931 | 1 | 43 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 414 | 5720 | -316 | 1766 | 2350 | 3254 | 1 | 43 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 427 | 4867 | -1061 | -570 | 4293 | 5344 | 1 | 43 |
| fibr_ib | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 314 | 2855 | -277 | 881 | 4137 | 3297 | 1 | 43 |
| fibr_ib | break_native | frenko_28 | {"n": 3, "k": 0.5} | sym15u / both | 336 | 2812 | 1115 | -212 | 3599 | 1490 | 1 | 43 |
| fibr_ib | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 43 |
| fibr_ib | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 43 |
| fibr_ib | reject | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 710 | 3281 | -283 | -506 | 2843 | 3230 | 1 | 43 |
| fibr_ib | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 313 | 3225 | 598 | 890 | -471 | 3776 | 1 | 43 |
| fibr_ib | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 222 | 2506 | 180 | -429 | 3 | 1221 | 1 | 43 |
| fibr_ib | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 333 | 2991 | 863 | 1825 | 1106 | 3425 | 1 | 43 |
| fibr_on | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 390 | 3646 | 879 | 2200 | 7144 | 3961 | 1 | 43 |
| fibr_on | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 414 | 4795 | 1610 | 372 | 7170 | 7330 | 1 | 43 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 383 | 5252 | 1464 | 1013 | 2918 | 7973 | 1 | 43 |
| fibr_on | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 1 | 43 |
| fibr_on | reject | lbrk_3_10 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 626 | 3341 | 98 | -2682 | 669 | 4947 | 2 | 43 |
| fibr_on | reject_native | kagi_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 286 | 3620 | 579 | -1335 | -1835 | 3947 | 1 | 43 |
| fibr_on | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 2663 | -1647 | 883 | 1488 | 3069 | 1 | 43 |
| fibr_on | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 3227 | 1904 | -823 | -47 | 375 | 1 | 43 |
| fibr_or | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 43 |
| fibr_or | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 43 |
| fibr_or | false_break | urenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 349 | 3867 | 432 | 1403 | -216 | 2811 | 1 | 43 |
| fibr_or | false_break_native | kagi_14 | {"M": 1, "k": 0.0} | sym15u / both | 383 | 3852 | 98 | 1427 | 1769 | 3344 | 1 | 43 |
| fibr_or | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 374 | 3996 | -233 | 328 | 4247 | 4044 | 1 | 43 |
| fibr_or | reject_native | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 490 | 3288 | 56 | 1396 | 513 | -467 | 1 | 43 |
| fibr_or | retest | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 2 | 43 |
| fibr_or | retest_native | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 2 | 43 |
| fibr_pd | break | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 363 | 6035 | -981 | 1122 | 3395 | 6251 | 1 | 43 |
| fibr_pd | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 365 | 5426 | -679 | 158 | 2300 | 6842 | 1 | 43 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 1 | 43 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 1 | 43 |
| fibr_pd | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 43 |
| fibr_pd | reject_native | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 43 |
| fibr_pd | retest | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 43 |
| fibr_pd | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 43 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 357 | 5210 | 1949 | 420 | -2741 | 6204 | 1 | 43 |
| piv_cama | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 379 | 6524 | 489 | 1354 | 649 | 7212 | 1 | 43 |
| piv_cama | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 194 | 3092 | 319 | 526 | 2048 | 2764 | 1 | 43 |
| piv_cama | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 187 | 3276 | 454 | 729 | 1972 | 3605 | 1 | 43 |
| piv_cama | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 381 | 3907 | -760 | 253 | 597 | 3463 | 1 | 43 |
| piv_cama | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 412 | 4654 | -2040 | -878 | -4527 | 4643 | 1 | 43 |
| piv_cama | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 43 |
| piv_cama | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 43 |
| piv_floor | break | pnf_56 | {"n": 1, "k": 0.5} | sym8u / both | 185 | 3673 | -541 | 174 | 2597 | 2912 | 2 | 43 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 1 | 43 |
| piv_floor | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym8u / both | 186 | 3796 | -476 | 286 | 3151 | 3316 | 2 | 43 |
| piv_floor | false_break_native | kagi_40 | {"M": 3, "k": 0.5} | sym15u / both | 377 | 4160 | 1164 | 1611 | 1824 | 5277 | 1 | 43 |
| piv_floor | reject | vrb_25000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 189 | 2967 | -545 | 1207 | 34 | 4021 | 1 | 43 |
| piv_floor | reject_native | vrb_25000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 189 | 2967 | -545 | 1207 | 34 | 4021 | 1 | 43 |
| piv_floor | retest | pnf_56 | {"M": 10, "tol": 0.5} | sym8u / both | 136 | 3307 | 1674 | 1218 | 2007 | 4474 | 2 | 43 |
| piv_floor | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym8u / both | 151 | 3913 | 1673 | 239 | 2389 | 4656 | 2 | 43 |
| piv_wf | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3685 | 42 | 27 | 876 | 2866 | 1 | 43 |
| piv_wf | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 394 | 3769 | -323 | 382 | 4352 | 7535 | 1 | 43 |
| piv_wf | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 3750 | 2632 | 2336 | 1588 | 3570 | 1 | 43 |
| piv_wf | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 373 | 3736 | 2381 | 2146 | 1178 | 2963 | 1 | 43 |
| piv_wf | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 306 | 2772 | -874 | -732 | 1160 | 5492 | 1 | 43 |
| piv_wf | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 404 | 2303 | -833 | 3724 | 3038 | 2931 | 1 | 43 |
| piv_wf | retest | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 361 | 4657 | 320 | 3797 | -729 | 5338 | 1 | 43 |
| piv_wf | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 323 | 4338 | 1465 | 1240 | 2816 | 3449 | 1 | 43 |
| swcluster | break | urenko_112 | {"n": 3, "k": 0.5} | sym15u / both | 54 | 1306 | 832 | -672 | 48 | 1510 | 1 | 44 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / long | 56 | 1203 | -745 | -84 | -805 | 1222 | 1 | 44 |
| swcluster | false_break | pnf_40 | {"M": 1, "k": 0.0} | sym15u / both | 93 | 1551 | -519 | -769 | 385 | 1862 | 1 | 44 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 1 | 44 |
| swcluster | reject | vrb_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 | 1681 | -1109 | -353 | -1304 | 2494 | 1 | 44 |
| swcluster | reject_native | vrb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1695 | -31 | -215 | -1648 | 964 | 1 | 44 |
| swcluster | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 47 | 1317 | -512 | -727 | -288 | 1601 | 1 | 44 |
| swcluster | retest_native | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1293 | 791 | -1867 | 192 | 1950 | 1 | 44 |
| swsr15 | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 44 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 44 |
| swsr15 | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 372 | 3937 | 1163 | 182 | 1458 | 3348 | 1 | 44 |
| swsr15 | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 343 | 5020 | 338 | -1450 | 5190 | 5244 | 1 | 44 |
| swsr15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 328 | 3874 | -2044 | -176 | -1129 | 4458 | 1 | 44 |
| swsr15 | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 354 | 3290 | -1693 | 687 | -2566 | 6013 | 1 | 44 |
| swsr15 | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 290 | 5015 | -392 | -944 | 1428 | 4099 | 1 | 44 |
| swsr15 | retest_native | urenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 333 | 4907 | 1503 | -111 | 2647 | 3519 | 1 | 44 |
| swsr5 | break | kagi_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5683 | 879 | -674 | -1582 | 4628 | 2 | 44 |
| swsr5 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym8u / both | 435 | 5683 | 879 | -674 | -1582 | 4628 | 2 | 44 |
| swsr5 | false_break | kagi_28 | {"M": 1, "k": 0.5} | sym8u / both | 442 | 5677 | 477 | -1099 | -1804 | 5175 | 2 | 44 |
| swsr5 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | sym8u / both | 432 | 8188 | 1102 | -2034 | 684 | 8579 | 2 | 44 |
| swsr5 | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 407 | 3165 | -776 | 1166 | 1559 | 3156 | 1 | 44 |
| swsr5 | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 452 | 4120 | -609 | 1554 | 3190 | 5222 | 1 | 44 |
| swsr5 | retest | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 665 | 2200 | 3212 | 5780 | 1 | 44 |
| swsr5 | retest_native | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 691 | 2200 | 3212 | 5780 | 1 | 44 |
| swsr60 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3965 | 36 | 158 | -2380 | 1344 | 1 | 44 |
| swsr60 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 254 | 4303 | 338 | -270 | -2273 | 3058 | 1 | 44 |
| swsr60 | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 290 | 2588 | 1112 | -417 | 1728 | 2743 | 1 | 44 |
| swsr60 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 286 | 2726 | 385 | -291 | 3026 | 3397 | 1 | 44 |
| swsr60 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 240 | 2871 | -893 | -1110 | -691 | 4303 | 1 | 44 |
| swsr60 | reject_native | pnf_7 | {"tol": 0.5, "conf": "body"} | sym15u / both | 207 | 2996 | -223 | 738 | -2958 | 2749 | 1 | 44 |
| swsr60 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 264 | 3367 | 417 | 713 | 2105 | 2877 | 1 | 44 |
| swsr60 | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 235 | 3947 | -295 | 1712 | 542 | 2019 | 1 | 44 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 251 | 5486 | 738 | 818 | 1504 | 1968 | 2 | 213 |
| stack | break_native | rng_80 | {"k": 2, "cw": 2.0} | sym8u / both | 307 | 6590 | -1020 | 397 | 79 | 3936 | 2 | 213 |
| stack | reject | mom_28 | {"k": 2, "cw": 0.5} | sym15u / both | 301 | 3518 | 400 | 1911 | 1013 | 4829 | 1 | 213 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | asym20u/10u / both | 248 | 3290 | -789 | 971 | -1202 | 4802 | 2 | 213 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 214 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1335 | -822 | 539 | 550 | 1717 | 1 | 214 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 214 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 214 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 214 |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 126 | 1601 | -738 | -637 | 518 | 1605 | 1 | 214 |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1266 | -894 | 749 | 1751 | 1947 | 1 | 214 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 214 |
| channel | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 44 |
| channel | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 44 |
| channel | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 44 |
| channel | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 44 |
| channel | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 1127 | 4027 | 2194 | -2323 | -1894 | 1091 | 1 | 44 |
| channel | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 463 | 4187 | 146 | -2476 | 4036 | 4709 | 1 | 44 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 527 | 5168 | 1396 | -726 | 235 | 2951 | 1 | 44 |
| channel | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 420 | 6420 | 1977 | 2723 | 3726 | 6347 | 1 | 44 |
| fvg15 | break | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 330 | -695 | 1898 | 2097 | 1 | 44 |
| fvg15 | break_native | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 408 | -695 | 1898 | 2097 | 1 | 44 |
| fvg15 | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 63 | 2026 | 106 | -1123 | 207 | 1397 | 1 | 44 |
| fvg15 | false_break_native | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 108 | 2100 | -895 | 84 | -297 | 1921 | 1 | 44 |
| fvg15 | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 176 | 1407 | -534 | 1658 | -536 | 571 | 1 | 44 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 354 | 1253 | 175 | 1053 | 1876 | 1196 | 1 | 44 |
| fvg15 | retest | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 44 |
| fvg15 | retest_native | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 44 |
| fvg5 | break | pnf_20 | {"n": 2, "k": 0.5} | sym8u / long | 92 | 2269 | 925 | 886 | 714 | 2837 | 2 | 44 |
| fvg5 | break_native | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 2280 | 649 | 1613 | 1744 | 1553 | 1 | 44 |
| fvg5 | false_break | pnf_20 | {"M": 2, "k": 0.0} | sym8u / both | 204 | 2032 | -445 | -1680 | 1732 | 1812 | 2 | 44 |
| fvg5 | false_break_native | pnf_20 | {"M": 2, "k": 0.0} | sym8u / both | 204 | 2032 | -438 | -1680 | 1732 | 1812 | 2 | 44 |
| fvg5 | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / long | 204 | 1946 | 672 | -175 | 374 | 2222 | 1 | 44 |
| fvg5 | reject_native | vrb_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / long | 220 | 2193 | 228 | 12 | 309 | 2356 | 1 | 44 |
| fvg5 | retest | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 222 | 3806 | -1035 | -262 | -445 | 2561 | 1 | 44 |
| fvg5 | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 2329 | -55 | -245 | -934 | 2721 | 1 | 44 |
| gaps | break | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 104 | -1328 | 2128 | 1944 | 1 | 214 |
| gaps | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 142 | -1328 | 2128 | 1944 | 1 | 214 |
| gaps | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -820 | -86 | 2898 | 2982 | 1 | 214 |
| gaps | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -762 | -86 | 2898 | 2982 | 1 | 214 |
| gaps | reject | mom_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 199 | 3018 | -346 | -686 | -1185 | 3192 | 1 | 214 |
| gaps | reject_native | mom_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 199 | 3018 | -346 | -686 | -1185 | 3192 | 1 | 214 |
| gaps | retest | dchg_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 494 | 2984 | -130 | -121 | -348 | 1969 | 1 | 214 |
| gaps | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 221 | 3004 | 496 | -2177 | 458 | 3709 | 1 | 214 |
| mmove | break | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 44 |
| mmove | break_native | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 44 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 1 | 44 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 1 | 44 |
| mmove | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 95 | 2790 | 1939 | 398 | 1792 | 3227 | 1 | 44 |
| mmove | reject_native | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 317 | 3372 | -70 | 595 | -1300 | 2698 | 1 | 44 |
| mmove | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 329 | 3092 | 1424 | 140 | 3397 | 3171 | 1 | 44 |
| mmove | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 170 | 3030 | 552 | -385 | 1137 | 4321 | 1 | 44 |
| ob15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 143 | 2715 | -364 | 1077 | -198 | 2970 | 1 | 44 |
| ob15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 144 | 2579 | -490 | 437 | 440 | 3050 | 1 | 44 |
| ob15 | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 120 | 1724 | 1840 | 757 | 2754 | 1249 | 1 | 44 |
| ob15 | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | sym15u / both | 128 | 1730 | 694 | -773 | 1270 | -274 | 1 | 44 |
| ob15 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 125 | 2280 | -762 | 112 | 499 | 2143 | 1 | 44 |
| ob15 | reject_native | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2140 | 289 | -157 | 1697 | 330 | 1 | 44 |
| ob15 | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 110 | 2538 | -231 | 102 | 2014 | 2666 | 1 | 44 |
| ob15 | retest_native | vrb_240 | {"M": 3, "tol": 0.0} | sym15u / both | 132 | 2329 | 183 | -137 | 51 | 1381 | 1 | 44 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 44 |
| ob5 | break_native | lbrk_3_10 | {"n": 1, "k": 0.5} | sym15u / both | 169 | 3478 | -143 | -1008 | 1362 | 2120 | 2 | 44 |
| ob5 | false_break | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 44 |
| ob5 | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 44 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 139 | 1592 | 443 | -1429 | -219 | 1037 | 1 | 44 |
| ob5 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 140 | 2232 | -724 | -50 | -411 | 97 | 1 | 44 |
| ob5 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 2614 | -885 | -1043 | -1778 | 2222 | 1 | 44 |
| ob5 | retest_native | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 159 | 2560 | 1247 | 265 | 209 | 2475 | 1 | 44 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 210 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 210 |
| open_range | false_break | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 435 | 2425 | 23 | -145 | -730 | 1542 | 2 | 210 |
| open_range | false_break_native | renko_20 | {"M": 1, "k": 0.5} | sym8u / both | 420 | 2670 | 231 | -183 | -1477 | 2468 | 2 | 210 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 210 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 210 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 210 |
| open_range | retest_native | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 298 | 4014 | 703 | 324 | -1734 | 2744 | 2 | 210 |
| opens | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 360 | 5490 | -643 | 803 | 229 | 6745 | 1 | 214 |
| opens | break_native | pnf_20 | {"n": 1, "k": 0.5} | sym8u / both | 378 | 6037 | 1093 | -1255 | 975 | 9884 | 2 | 214 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 168 | 4705 | -649 | -420 | 1329 | 4754 | 1 | 214 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 1 | 214 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 367 | 5218 | -809 | 1237 | -891 | 2404 | 1 | 214 |
| opens | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 315 | 4982 | -996 | -570 | 2619 | 6379 | 1 | 214 |
| opens | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 306 | 4952 | 1079 | -2912 | 3174 | 4784 | 1 | 214 |
| opens | retest_native | pnf_20 | {"M": 6, "tol": 0.5} | sym8u / both | 294 | 4635 | 1331 | 899 | 2801 | 6670 | 2 | 214 |
| prior_day | break | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 214 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 214 |
| prior_day | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 6120 | 1169 | 654 | 6266 | 6027 | 1 | 214 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 1 | 214 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 214 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 214 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 214 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 214 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 213 |
| profile_nodes | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 277 | 3995 | 2467 | -1651 | 1370 | 3940 | 1 | 213 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 213 |
| profile_nodes | false_break_native | cusum_40 | {"M": 1, "k": 0.5} | sym8u / both | 224 | 4514 | -1520 | 711 | -645 | 4653 | 2 | 213 |
| profile_nodes | reject | renko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 483 | 3360 | 110 | -1175 | 115 | 1930 | 2 | 213 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 213 |
| profile_nodes | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 213 |
| profile_nodes | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 213 |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 2 | 214 |
| profile_va | break_native | rng_28 | {"n": 2, "k": 0.5} | sym15u / both | 217 | 4047 | 449 | 1260 | 3137 | 4304 | 2 | 214 |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 198 | 3091 | 543 | 151 | 2346 | 3855 | 2 | 214 |
| profile_va | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | plain60/60 / both | 548 | 2993 | 1062 | 46 | 172 | 1929 | 1 | 214 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 1 | 214 |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 263 | 4791 | -360 | 58 | 2424 | 3455 | 1 | 214 |
| profile_va | retest | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 465 | 3564 | -541 | -277 | 960 | 1989 | 1 | 214 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 214 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 214 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 214 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 214 |
| round | false_break_native | dib_3500 | {"M": 1, "k": 0.5} | asym20u/10u / both | 579 | 7357 | -777 | -1171 | -5154 | 8350 | 2 | 214 |
| round | reject | renko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 657 | 8023 | -600 | -3119 | -4002 | 8822 | 2 | 214 |
| round | reject_native | vsess_200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 540 | 6009 | 257 | -1854 | -806 | 4925 | 2 | 214 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 214 |
| round | retest_native | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 617 | 6587 | -614 | 2075 | 217 | 5937 | 2 | 214 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 212 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 212 |
| session_hl | false_break | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 346 | 4857 | 1820 | -135 | 2442 | 2702 | 1 | 212 |
| session_hl | false_break_native | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 344 | 5417 | 1497 | 47 | 2767 | 3055 | 1 | 212 |
| session_hl | reject | tick_5000 | {"tol": 0.0, "conf": "body"} | sym8u / both | 257 | 2738 | -362 | 1005 | -702 | 2504 | 2 | 212 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 212 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 212 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 212 |
| trendline | break | vrb_240 | {"n": 3, "k": 0.5} | sym15u / both | 357 | 4291 | -656 | -98 | 1644 | 4319 | 1 | 44 |
| trendline | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 297 | 3534 | 1905 | 1508 | -2673 | 3553 | 1 | 44 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 285 | 4062 | 1560 | 1127 | 1434 | 5996 | 1 | 44 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4692 | 42 | 1654 | 1101 | 5496 | 1 | 44 |
| trendline | reject | vrb_240 | {"tol": 0.0, "conf": "close"} | sym15u / both | 342 | 2365 | -360 | 309 | 1403 | 1279 | 1 | 44 |
| trendline | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 272 | 3205 | 233 | 64 | 1560 | 4027 | 1 | 44 |
| trendline | retest | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 234 | 3192 | -7 | -266 | -583 | 2917 | 1 | 44 |
| trendline | retest_native | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 283 | 3545 | 204 | 994 | 2670 | 3978 | 1 | 44 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 214 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 214 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 214 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 214 |
| uw_dp | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 94 | 3468 | 0 | 0 | 524 | 3496 | 1 | 214 |
| uw_dp | reject_native | mom_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 135 | 3130 | 0 | 0 | 439 | 2925 | 1 | 214 |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 153 | 3839 | 0 | 0 | 1297 | 3514 | 2 | 214 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 214 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 213 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 1 | 213 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 1 | 213 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 1 | 213 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 1 | 213 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 213 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 213 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 213 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 213 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 213 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 213 |
| uw_qqq | false_break_native | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3384 | 0 | 197 | 3751 | 4321 | 1 | 213 |
| uw_qqq | reject | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 213 |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 213 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 213 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 213 |
| vwap | break | rng_80 | {"n": 2, "k": 0.5} | sym8u / both | 294 | 4569 | 929 | 247 | 3761 | 4575 | 2 | 213 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 213 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 178 | 4696 | 63 | -174 | 2422 | 5048 | 1 | 213 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 166 | 4411 | -108 | -214 | 2319 | 4241 | 1 | 213 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 213 |
| vwap | reject_native | tm60 | {"tol": 0.0, "conf": "close"} | sym15u / both | 302 | 5838 | -1468 | 1495 | -1469 | 6714 | 1 | 213 |
| vwap | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 364 | 5402 | 219 | -90 | 1699 | 5388 | 1 | 213 |
| vwap | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 369 | 4676 | 125 | 382 | 2643 | 3279 | 1 | 213 |
| vwap_bands | break | mom_20 | {"n": 3, "k": 0.5} | sym15u / both | 475 | 6544 | 86 | 1981 | 5311 | 8312 | 1 | 212 |
| vwap_bands | break_native | tm15 | {"n": 2, "k": 0.5} | sym30u / both | 494 | 6214 | 1544 | -505 | -4673 | 6353 | 2 | 212 |
| vwap_bands | false_break | swing_atr_0.6 | {"M": 3, "k": 0.5} | sym15u / both | 477 | 3977 | 1234 | -534 | 5712 | 3574 | 1 | 212 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 212 |
| vwap_bands | reject | tick_300 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 481 | 6944 | 1737 | -351 | 2059 | 7316 | 2 | 212 |
| vwap_bands | reject_native | vol_500 | {"tol": 0.5, "conf": "close"} | asym10u/20u / both | 512 | 6769 | -741 | 751 | 2018 | 2515 | 2 | 212 |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 475 | 5871 | -47 | -3369 | -2356 | 8027 | 2 | 212 |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 452 | 5820 | -431 | 1126 | 1466 | 4714 | 1 | 212 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 214 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 214 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 214 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 214 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 | 1812 | 674 | -92 | 992 | 1655 | 1 | 214 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 82 | 2131 | 988 | -272 | -1646 | 1573 | 1 | 214 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 214 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 214 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 213 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym15u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 1 | 213 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 3068 | 829 | 2566 | -2302 | 3067 | 1 | 213 |
| zones | false_break_native | urenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 169 | 3155 | 720 | 2082 | -2078 | 3224 | 1 | 213 |
| zones | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 96 | 2134 | 178 | -1365 | -390 | 3312 | 1 | 213 |
| zones | reject_native | dlt_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 2882 | -1835 | -913 | -60 | 3270 | 1 | 213 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 213 |
| zones | retest_native | cusum_28 | {"M": 3, "tol": 0.5} | sym15u / both | 139 | 2749 | 981 | 908 | -2275 | 3551 | 2 | 213 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 63 | 745 | -750 | 713 | 55 | 78 | 1 | 209 |
| sdx15 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 218 | 3979 | 866 | -1611 | -3817 | 3589 | 1 | 209 |
| sdx15 | lim_prox | dib_3500 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 211 | 4594 | -142 | -1792 | -2175 | 4608 | 1 | 209 |
| sdx15 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 151 | 2838 | 1403 | -67 | -500 | 3343 | 1 | 209 |
| sdx15 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 213 | 2090 | -694 | -931 | -1174 | 3194 | 1 | 209 |
| sdx15 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 209 |
| sdx15 | rej_zone | rng_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 190 | 4546 | 51 | 187 | -481 | 4555 | 1 | 209 |
| sdx15 | retest | pnf_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 31 | 526 | -752 | 859 | -350 | 61 | 1 | 209 |
| sdx3 | break | pnf_7 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 103 | 1995 | -691 | -13 | 2296 | 1834 | 1 | 208 |
| sdx3 | lim_mid | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 315 | 3243 | 1073 | -1181 | -5173 | 1197 | 1 | 208 |
| sdx3 | lim_prox | vrb_240 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 595 | 3214 | -1162 | 2156 | -2845 | 392 | 1 | 208 |
| sdx3 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 251 | 2478 | 724 | 613 | -327 | 1370 | 1 | 208 |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 218 | 3964 | 768 | 815 | -3268 | 3684 | 1 | 208 |
| sdx3 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 208 |
| sdx3 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 208 |
| sdx3 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 68 | 1390 | 118 | 65 | 1080 | 1692 | 1 | 208 |
| sdx30 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 34 | 466 | -431 | 870 | -122 | 440 | 1 | 209 |
| sdx30 | lim_mid | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 103 | 1951 | 721 | -406 | -107 | 947 | 1 | 209 |
| sdx30 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 3042 | -219 | -1016 | 531 | 2612 | 1 | 209 |
| sdx30 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 38 | 1091 | -267 | -1452 | -151 | 712 | 1 | 209 |
| sdx30 | rej_flow | vrb_400 | {"d": "E", "F": 9} | sym15u / short | 62 | 659 | -164 | 425 | -623 | -391 | 1 | 209 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 209 |
| sdx30 | rej_zone | mom_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 80 | 3062 | -715 | -1250 | 657 | 1225 | 1 | 209 |
| sdx5 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 91 | 2323 | -533 | 988 | 255 | 1749 | 1 | 209 |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 720 | 2734 | 720 | 3 | -3881 | 2478 | 1 | 209 |
| sdx5 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 746 | 2572 | -102 | -1530 | -5419 | 2741 | 1 | 209 |
| sdx5 | rej | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 262 | 2521 | -220 | 1136 | -393 | 2008 | 1 | 209 |
| sdx5 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 97 | 1766 | 159 | -855 | -1246 | 2358 | 1 | 209 |
| sdx5 | rej_native | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 259 | 2842 | -263 | 1629 | -600 | 2273 | 1 | 209 |
| sdx5 | rej_zone | vol_4000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 362 | 3759 | 51 | -2567 | -2706 | 5488 | 1 | 209 |
| sdx5 | retest | kagi_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 82 | 1774 | -756 | -147 | -45 | 2087 | 1 | 209 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 384 | 10 | 407 | 778 | 289 | 1 | 208 |
| sdx60 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 73 | 1628 | 155 | 544 | -311 | 1363 | 1 | 208 |
| sdx60 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 259 | 1933 | -320 | -699 | -24 | 2535 | 1 | 208 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 76 | 986 | -87 | -92 | 901 | 1294 | 1 | 208 |
| sdx60 | rej_flow | vrb_400 | {"d": "E", "F": 9} | plain60/60 / short | 44 | 662 | -86 | 74 | -63 | 568 | 1 | 208 |
| sdx60 | rej_native | vrb_240 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 193 | 1131 | 262 | -1162 | 885 | 1239 | 1 | 208 |
| sdx60 | rej_zone | tm3600 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 72 | 2676 | 119 | 118 | -1586 | 2417 | 1 | 208 |
| sdx_renko28 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 129 | 2292 | -1534 | 786 | -391 | 1043 | 1 | 208 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 208 |
| sdx_renko28 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 285 | 3300 | 213 | 469 | 2009 | 5781 | 1 | 208 |
| sdx_renko28 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 537 | 5198 | -406 | -1538 | 809 | 6421 | 1 | 208 |
| sdx_renko28 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / short | 102 | 1940 | 787 | 26 | -743 | 1348 | 1 | 208 |
| sdx_renko28 | rej_native | vrb_400 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 636 | 3835 | -352 | -51 | 774 | 6561 | 1 | 208 |
| sdx_renko28 | rej_zone | pnf_5 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 208 |
| sdx_renko28 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 89 | 1596 | -851 | 795 | 41 | 977 | 1 | 208 |
| sdx_rng28 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 301 | 3408 | -2123 | 661 | -816 | 3058 | 1 | 208 |
| sdx_rng28 | lim_mid | frenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 331 | 3377 | 299 | -3020 | -3304 | 3142 | 1 | 208 |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1024 | 4026 | -947 | 896 | -3778 | 6473 | 1 | 208 |
| sdx_rng28 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 462 | 2252 | -1322 | -833 | -1038 | 2734 | 1 | 208 |
| sdx_rng28 | rej_flow | vrb_240 | {"d": "E", "F": 9} | sym15u / both | 493 | 2558 | -783 | 2787 | -3819 | 2063 | 1 | 208 |
| sdx_rng28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 208 |
| sdx_rng28 | rej_zone | tm1200 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 288 | 4433 | -643 | 223 | -1140 | 6262 | 1 | 208 |
| sdx_rng28 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 117 | 2944 | -978 | 239 | 485 | 3365 | 1 | 208 |
| sdx_vol1100 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 314 | 4031 | -1409 | -503 | 658 | 4201 | 1 | 208 |
| sdx_vol1100 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 275 | 6337 | -998 | 71 | 1443 | 6397 | 1 | 208 |
| sdx_vol1100 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 278 | 5565 | -679 | -26 | -465 | 6171 | 1 | 208 |
| sdx_vol1100 | rej | frenko_28 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 308 | 3089 | -275 | -2567 | -1719 | 2706 | 1 | 208 |
| sdx_vol1100 | rej_flow | vrb_400 | {"d": "E", "F": 0} | sym15u / short | 161 | 2399 | -174 | -1171 | -785 | 2439 | 1 | 208 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 768 | 3970 | -570 | -433 | -756 | 4714 | 1 | 208 |
| sdx_vol1100 | rej_zone | tick_5000 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 391 | 3880 | 1601 | -1293 | -1062 | 5402 | 1 | 208 |
| sdx_vol1100 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 227 | 3437 | -1140 | -704 | 968 | 4601 | 1 | 208 |
| fib15 | break | dib_2000 | {"n": 3, "k": 0.5} | sym15u / short | 142 | 3835 | -591 | -539 | -1451 | 3789 | 1 | 205 |
| fib15 | break_native | tm45 | {"n": 1, "k": 0.0} | sym15u / short | 119 | 3822 | -8 | -287 | 470 | 3804 | 1 | 205 |
| fib15 | false_break | time_s_45 | {"M": 1, "k": 0.0} | sym15u / short | 134 | 3485 | -685 | -905 | 709 | 4240 | 1 | 205 |
| fib15 | false_break_native | time_s_45 | {"M": 3, "k": 0.5} | sym15u / short | 138 | 3534 | -988 | -567 | 3 | 3971 | 1 | 205 |
| fib15 | pullback | time_s_5 | {"tol": 0.5, "conf": "body"} | sym15u / short | 250 | 2485 | 253 | -188 | 142 | 2433 | 1 | 205 |
| fib15 | pullback_native | tm10 | {"tol": 0.0, "conf": "close"} | sym15u / short | 152 | 2403 | 3 | 277 | -165 | 3138 | 1 | 205 |
| fib15 | reject | rng_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 255 | 3925 | 1276 | 1265 | 1391 | 4665 | 1 | 205 |
| fib15 | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 205 |
| fib15 | retest | time_m_20 | {"M": 6, "tol": 0.5} | sym15u / both | 180 | 4004 | -655 | 340 | 306 | 3269 | 1 | 205 |
| fib15 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 208 | 3836 | 116 | -100 | -2461 | 3206 | 1 | 205 |
| fib5 | break | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5454 | 1633 | 3169 | 1237 | 6533 | 1 | 205 |
| fib5 | break_native | drb_700 | {"n": 2, "k": 0.25} | sym15u / both | 294 | 5957 | 1611 | 1641 | 2147 | 5578 | 1 | 205 |
| fib5 | false_break | tick_800 | {"M": 3, "k": 0.5} | sym15u / both | 286 | 5185 | -1038 | 940 | 257 | 6016 | 1 | 205 |
| fib5 | false_break_native | tick_800 | {"M": 3, "k": 0.5} | sym15u / both | 283 | 5266 | -894 | 115 | 1094 | 7007 | 1 | 205 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 1 | 205 |
| fib5 | pullback_native | drb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 2734 | -787 | 917 | -2068 | 1989 | 1 | 205 |
| fib5 | reject | vsess_200 | {"tol": 0.5, "conf": "body"} | sym8u / both | 285 | 6289 | -371 | 1437 | -1282 | 4830 | 2 | 205 |
| fib5 | reject_native | vol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 274 | 5828 | -819 | 224 | 1500 | 3983 | 1 | 205 |
| fib5 | retest | vol_750 | {"M": 6, "tol": 0.5} | sym15u / both | 262 | 4869 | 543 | -1080 | -972 | 6334 | 1 | 205 |
| fib5 | retest_native | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / both | 320 | 4654 | -1449 | -943 | 319 | 3902 | 1 | 205 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 206 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 206 |
| fib60 | false_break | rng_10 | {"M": 2, "k": 0.5} | sym15u / both | 242 | 3422 | -1420 | -398 | -943 | 3829 | 1 | 206 |
| fib60 | false_break_native | cdr_250 | {"M": 2, "k": 0.5} | sym15u / both | 175 | 3320 | -801 | 220 | -127 | 4246 | 1 | 206 |
| fib60 | pullback | tick_300 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 122 | 1350 | -490 | -176 | 168 | 1147 | 1 | 206 |
| fib60 | pullback_native | tick_300 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 126 | 1344 | -501 | -373 | 364 | 1152 | 1 | 206 |
| fib60 | reject | rng_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 431 | 2650 | -126 | 992 | -348 | 1911 | 1 | 206 |
| fib60 | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 136 | 2932 | -434 | 1783 | -20 | 2164 | 1 | 206 |
| fib60 | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym15u / both | 212 | 2504 | -138 | -18 | 1176 | 2607 | 1 | 206 |
| fib60 | retest_native | mrenko_20 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 130 | 3401 | 423 | 522 | 781 | 1846 | 2 | 206 |
| fibr_dev | break | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 323 | 3270 | -463 | 160 | 151 | 3127 | 1 | 43 |
| fibr_dev | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 318 | 3177 | 292 | 1852 | -1651 | 4840 | 1 | 43 |
| fibr_dev | false_break | vrb_25000 | {"M": 3, "k": 0.5} | sym15u / both | 224 | 2339 | -2279 | -303 | -1284 | 2203 | 1 | 43 |
| fibr_dev | false_break_native | vrb_25000 | {"M": 1, "k": 0.0} | sym15u / both | 224 | 2325 | -2186 | -188 | -738 | 2177 | 1 | 43 |
| fibr_dev | reject | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 111 | 3039 | -906 | -439 | 785 | 4073 | 1 | 43 |
| fibr_dev | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 310 | 2919 | -21 | 3751 | 295 | 2947 | 1 | 43 |
| fibr_dev | retest | kagi_112 | {"M": 10, "tol": 0.5} | sym15u / both | 209 | 2769 | -1419 | 969 | 78 | 2576 | 1 | 43 |
| fibr_dev | retest_native | kagi_112 | {"M": 3, "tol": 0.0} | sym15u / both | 193 | 2734 | -611 | -1064 | -1498 | 2411 | 1 | 43 |
| fibr_ib | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 251 | 3612 | 92 | -1032 | -493 | 1859 | 1 | 43 |
| fibr_ib | break_native | frenko_40 | {"n": 2, "k": 0.25} | sym15u / both | 245 | 3856 | -1527 | 184 | -1787 | 3643 | 1 | 43 |
| fibr_ib | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 231 | 2998 | -1461 | -465 | -1676 | 5234 | 1 | 43 |
| fibr_ib | false_break_native | mrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 258 | 3604 | -782 | -1742 | -1366 | 5952 | 1 | 43 |
| fibr_ib | reject | vrb_25000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 151 | 2981 | -701 | 817 | -116 | 3496 | 1 | 43 |
| fibr_ib | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 267 | 3485 | 245 | 3147 | -1000 | 2581 | 1 | 43 |
| fibr_ib | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 43 |
| fibr_ib | retest_native | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 43 |
| fibr_on | break | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 235 | 2308 | -806 | 3069 | -2296 | 3200 | 1 | 43 |
| fibr_on | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 235 | 2613 | 83 | 1407 | 1700 | 2276 | 1 | 43 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 232 | 2221 | -828 | 1006 | -1840 | 1304 | 1 | 43 |
| fibr_on | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 233 | 2219 | -607 | 594 | -2194 | 1699 | 1 | 43 |
| fibr_on | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 224 | 4457 | -1590 | -30 | -30 | 3118 | 1 | 43 |
| fibr_on | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 224 | 4457 | -1590 | -30 | -30 | 3118 | 1 | 43 |
| fibr_on | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 228 | 2547 | -512 | 810 | -273 | 485 | 1 | 43 |
| fibr_on | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 217 | 2587 | -133 | 2095 | -1145 | 3420 | 1 | 43 |
| fibr_or | break | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 223 | 3722 | 1679 | 177 | 2896 | 4918 | 1 | 43 |
| fibr_or | break_native | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 235 | 3359 | -844 | 380 | -352 | 3018 | 1 | 43 |
| fibr_or | false_break | kagi_10 | {"M": 2, "k": 0.5} | sym15u / both | 227 | 3162 | -2539 | 1556 | 88 | 4085 | 1 | 43 |
| fibr_or | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 2711 | -2616 | 999 | 797 | 3303 | 1 | 43 |
| fibr_or | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 43 |
| fibr_or | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 43 |
| fibr_or | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / short | 106 | 2541 | -582 | -25 | -891 | 2914 | 1 | 43 |
| fibr_or | retest_native | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 226 | 3433 | -1079 | 1971 | 1090 | 4690 | 1 | 43 |
| fibr_pd | break | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 43 |
| fibr_pd | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 43 |
| fibr_pd | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym8u / both | 208 | 1998 | -346 | 1339 | -3324 | 2735 | 2 | 43 |
| fibr_pd | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 38 | -1381 | 1884 | 1 | 43 |
| fibr_pd | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 197 | 3093 | 14 | 1008 | -2214 | 3340 | 1 | 43 |
| fibr_pd | reject_native | kagi_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 3634 | -868 | -66 | -1162 | 2545 | 1 | 43 |
| fibr_pd | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 88 | 2090 | 436 | -59 | -1075 | 1885 | 1 | 43 |
| fibr_pd | retest_native | kagi_56 | {"M": 6, "tol": 0.5} | sym15u / short | 101 | 2104 | 27 | 796 | -2196 | 1839 | 1 | 43 |
| piv_cama | break | kagi_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 529 | 2062 | 1743 | 913 | -1667 | 1448 | 1 | 43 |
| piv_cama | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 229 | 3002 | -798 | 88 | -642 | 3792 | 1 | 43 |
| piv_cama | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 205 | 1211 | -1613 | 1135 | 1006 | 996 | 1 | 43 |
| piv_cama | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 1497 | -1854 | 1699 | -3056 | 2291 | 1 | 43 |
| piv_cama | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 536 | 2838 | 205 | -269 | -2327 | 3249 | 1 | 43 |
| piv_cama | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 551 | 2235 | 495 | -257 | -1384 | 2735 | 1 | 43 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 3017 | 1323 | -981 | 973 | 1360 | 1 | 43 |
| piv_cama | retest_native | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 209 | 2890 | -621 | -741 | 2051 | 2186 | 1 | 43 |
| piv_floor | break | urenko_80 | {"n": 2, "k": 0.25} | sym15u / both | 146 | 2104 | 89 | 2484 | 144 | 1328 | 1 | 43 |
| piv_floor | break_native | urenko_56 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2598 | 440 | 2679 | 586 | 1925 | 1 | 43 |
| piv_floor | false_break | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 43 |
| piv_floor | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 43 |
| piv_floor | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 174 | 2732 | 312 | 945 | 1219 | 3340 | 1 | 43 |
| piv_floor | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 4162 | -247 | 2182 | -410 | 2889 | 1 | 43 |
| piv_floor | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 2261 | -762 | -663 | -1617 | 2246 | 1 | 43 |
| piv_floor | retest_native | lbrk_3_10 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 2174 | 539 | -433 | 264 | 1551 | 1 | 43 |
| piv_wf | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 43 |
| piv_wf | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 43 |
| piv_wf | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 225 | 2201 | -2119 | 1210 | 156 | 75 | 1 | 43 |
| piv_wf | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1842 | 1094 | 416 | -154 | 1 | 43 |
| piv_wf | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 88 | 1762 | -1585 | -62 | -1571 | 3382 | 1 | 43 |
| piv_wf | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 265 | 3055 | -151 | -947 | -2159 | 1619 | 1 | 43 |
| piv_wf | retest | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 43 |
| piv_wf | retest_native | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 43 |
| swcluster | break | pnf_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 78 | 1434 | -579 | -308 | -267 | 1378 | 1 | 44 |
| swcluster | break_native | lbrk_3_20 | {"n": 3, "k": 0.5} | sym15u / both | 47 | 1484 | -898 | 212 | -2023 | 2300 | 1 | 44 |
| swcluster | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 66 | 711 | -608 | 898 | -670 | 546 | 1 | 44 |
| swcluster | false_break_native | urenko_112 | {"M": 3, "k": 0.5} | sym15u / both | 33 | 948 | -1573 | 501 | -496 | 1074 | 1 | 44 |
| swcluster | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1368 | -235 | -439 | 744 | 1365 | 1 | 44 |
| swcluster | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 51 | 1544 | 242 | 371 | -1281 | 1329 | 1 | 44 |
| swcluster | retest | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1635 | 68 | 1694 | -1137 | 1335 | 1 | 44 |
| swcluster | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1618 | -3 | 1405 | 681 | 911 | 1 | 44 |
| swsr15 | break | kagi_28 | {"n": 1, "k": 0.25} | sym8u / short | 110 | 3542 | -588 | 602 | 565 | 3644 | 2 | 44 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / short | 117 | 3147 | -556 | 558 | 71 | 3221 | 1 | 44 |
| swsr15 | false_break | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 247 | 2905 | -826 | 1401 | 1932 | 1475 | 1 | 44 |
| swsr15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / short | 117 | 2948 | 43 | -480 | 1191 | 3055 | 1 | 44 |
| swsr15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 118 | 3340 | 255 | -524 | 1304 | 2502 | 1 | 44 |
| swsr15 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 271 | 4013 | 690 | 61 | -2201 | 2481 | 1 | 44 |
| swsr15 | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 176 | 2920 | 1261 | 1356 | -1090 | 2148 | 1 | 44 |
| swsr15 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 246 | 2938 | -421 | -968 | 2213 | 2463 | 1 | 44 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 44 |
| swsr5 | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 44 |
| swsr5 | false_break | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 44 |
| swsr5 | false_break_native | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 44 |
| swsr5 | reject | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / short | 131 | 2900 | 435 | -192 | 1157 | 4072 | 1 | 44 |
| swsr5 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 165 | 2981 | 290 | 1019 | 19 | 3754 | 1 | 44 |
| swsr5 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 260 | 4440 | -950 | -3103 | 1054 | 1787 | 1 | 44 |
| swsr5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 291 | 4019 | -261 | -2125 | 4208 | 2958 | 1 | 44 |
| swsr60 | break | pnf_40 | {"n": 2, "k": 0.25} | sym15u / short | 38 | 1767 | 558 | -107 | 48 | 2005 | 1 | 44 |
| swsr60 | break_native | kagi_40 | {"n": 3, "k": 0.5} | sym15u / both | 163 | 2879 | -1426 | 831 | -277 | 3346 | 1 | 44 |
| swsr60 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2016 | 888 | -971 | -1148 | 2792 | 1 | 44 |
| swsr60 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2016 | 888 | -971 | -1148 | 2792 | 1 | 44 |
| swsr60 | reject | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 81 | 1934 | -1464 | 154 | -1935 | 2404 | 1 | 44 |
| swsr60 | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 212 | 3196 | -733 | 1116 | -3739 | 3316 | 1 | 44 |
| swsr60 | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / short | 129 | 1496 | 335 | -641 | -63 | 1628 | 1 | 44 |
| swsr60 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 1967 | -1647 | 1506 | -2401 | 1541 | 1 | 44 |
| stack | break | urenko_28 | {"k": 2, "cw": 0.5} | sym15u / short | 86 | 2291 | 234 | -41 | 1145 | 1866 | 1 | 213 |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 107 | 3072 | 144 | 769 | -10 | 2485 | 1 | 213 |
| stack | reject | rng_20 | {"k": 2, "cw": 1.0} | asym10u/20u / both | 101 | 2187 | -447 | 1473 | -506 | 1062 | 2 | 213 |
| stack | reject_native | dol_350 | {"k": 4, "cw": 2.0} | plain60/60 / short | 192 | 3062 | -384 | 254 | 556 | 2627 | 1 | 213 |
| book_walls | break | time_s_5 | {"n": 2, "k": 0.25} | plain60/60 / both | 42 | 894 | -489 | -382 | 220 | 1042 | 1 | 212 |
| book_walls | break_native | tm15 | {"n": 1, "k": 0.0} | plain60/60 / both | 30 | 605 | -584 | -435 | -96 | 784 | 1 | 212 |
| book_walls | reject | time_s_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 47 | 475 | -958 | -263 | -638 | 569 | 1 | 212 |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 34 | 561 | 55 | -204 | -128 | 492 | 1 | 212 |
| book_walls | retest | time_s_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 499 | -402 | -181 | 44 | 592 | 1 | 212 |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 34 | 627 | -374 | 538 | 3 | 600 | 1 | 212 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 214 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 214 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 214 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 214 |
| book_walls_loose | reject | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 57 | 1173 | 963 | -1384 | -1489 | 994 | 2 | 214 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 214 |
| book_walls_loose | retest | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / short | 41 | 962 | -161 | -663 | 174 | 1475 | 1 | 214 |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 1146 | 212 | 787 | -261 | 941 | 1 | 214 |
| channel | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / short | 131 | 2891 | -746 | -580 | 1666 | 2590 | 1 | 44 |
| channel | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 275 | 3932 | -2003 | 2173 | -8 | 4372 | 1 | 44 |
| channel | false_break | pnf_7 | {"M": 3, "k": 0.5} | sym15u / both | 293 | 3216 | -1127 | 782 | 1821 | 3617 | 1 | 44 |
| channel | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 269 | 3285 | -130 | 684 | 4085 | 3749 | 1 | 44 |
| channel | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 200 | 3044 | -754 | 780 | -1553 | 4489 | 1 | 44 |
| channel | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 227 | 3124 | -1460 | -819 | -1409 | 4809 | 1 | 44 |
| channel | retest | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 2884 | -1066 | -819 | -1144 | 2504 | 1 | 44 |
| channel | retest_native | kagi_40 | {"M": 6, "tol": 0.5} | sym15u / both | 279 | 4816 | -153 | -1208 | 1427 | 4943 | 1 | 44 |
| fvg15 | break | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 44 |
| fvg15 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 44 |
| fvg15 | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 44 |
| fvg15 | false_break_native | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 44 |
| fvg15 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 59 | 1177 | 560 | -604 | 190 | 541 | 1 | 44 |
| fvg15 | reject_native | vrb_40000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 34 | 1545 | -182 | 363 | -346 | 1563 | 1 | 44 |
| fvg15 | retest | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 120 | 2032 | -538 | -1332 | -2444 | 1430 | 1 | 44 |
| fvg15 | retest_native | vrb_400 | {"M": 10, "tol": 0.5} | sym15u / both | 119 | 2194 | -495 | -740 | -2250 | 1785 | 1 | 44 |
| fvg5 | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2941 | -43 | 529 | 74 | 1047 | 1 | 44 |
| fvg5 | break_native | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 2590 | -1104 | -310 | -224 | 1211 | 1 | 44 |
| fvg5 | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / short | 97 | 1497 | 237 | -1092 | -344 | 965 | 1 | 44 |
| fvg5 | false_break_native | kagi_28 | {"M": 3, "k": 0.5} | sym15u / short | 110 | 1603 | -227 | -235 | -464 | 1975 | 1 | 44 |
| fvg5 | reject | vrb_240 | {"tol": 0.0, "conf": "close"} | sym15u / both | 280 | 2046 | 1203 | 974 | 1086 | 561 | 1 | 44 |
| fvg5 | reject_native | vrb_240 | {"tol": 0.0, "conf": "close"} | sym15u / both | 280 | 2046 | 1203 | 974 | 1086 | 561 | 1 | 44 |
| fvg5 | retest | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / both | 311 | 2041 | -507 | -733 | 178 | 770 | 1 | 44 |
| fvg5 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 148 | 1893 | 54 | 15 | -175 | 1618 | 1 | 44 |
| gaps | break | dchg_28 | {"n": 3, "k": 0.5} | sym15u / both | 106 | 2352 | -1948 | -327 | -1853 | 1832 | 1 | 214 |
| gaps | break_native | kagi_14 | {"n": 3, "k": 0.5} | sym8u / both | 121 | 2062 | -1463 | -1205 | 137 | 1637 | 2 | 214 |
| gaps | false_break | time_s_5 | {"M": 1, "k": 0.0} | sym30u / both | 39 | 1447 | -588 | 325 | -1319 | 918 | 2 | 214 |
| gaps | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 113 | 1904 | -1039 | 978 | -175 | 1124 | 1 | 214 |
| gaps | reject | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 189 | 1492 | 731 | -1239 | -821 | 493 | 1 | 214 |
| gaps | reject_native | dchg_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2843 | -341 | 133 | -834 | 2496 | 1 | 214 |
| gaps | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 102 | 1919 | -539 | 412 | 1770 | 768 | 1 | 214 |
| gaps | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 122 | 2649 | -496 | -97 | 417 | 1216 | 1 | 214 |
| mmove | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 44 |
| mmove | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 44 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 44 |
| mmove | false_break_native | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 44 |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 242 | 2230 | 761 | -280 | -16 | 1468 | 1 | 44 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / short | 134 | 2490 | -534 | 260 | 1315 | 2427 | 1 | 44 |
| mmove | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 44 |
| mmove | retest_native | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 44 |
| ob15 | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1311 | -552 | 809 | -735 | 1890 | 1 | 44 |
| ob15 | break_native | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1311 | -552 | 809 | -735 | 1890 | 1 | 44 |
| ob15 | false_break | vrb_240 | {"M": 3, "k": 0.5} | sym15u / both | 54 | 1434 | 144 | 444 | -609 | 1363 | 1 | 44 |
| ob15 | false_break_native | vrb_240 | {"M": 2, "k": 0.5} | sym15u / both | 54 | 1435 | 342 | 288 | 240 | 1431 | 1 | 44 |
| ob15 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 55 | 925 | -325 | -377 | 1269 | 2009 | 1 | 44 |
| ob15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 55 | 1100 | 158 | 617 | 1076 | 2402 | 1 | 44 |
| ob15 | retest | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1312 | -71 | 347 | 114 | 1901 | 1 | 44 |
| ob15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1242 | -237 | 630 | -361 | 1947 | 1 | 44 |
| ob5 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 80 | 1964 | -227 | -120 | 1433 | 2441 | 1 | 44 |
| ob5 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 2181 | -420 | 239 | 1123 | 2407 | 1 | 44 |
| ob5 | false_break | lbrk_3_10 | {"M": 1, "k": 0.5} | sym30u / both | 68 | 2134 | 402 | -1308 | 205 | 3165 | 2 | 44 |
| ob5 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1771 | -70 | 552 | 1555 | 2673 | 1 | 44 |
| ob5 | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 65 | 1662 | -485 | -147 | 457 | 1158 | 2 | 44 |
| ob5 | reject_native | lbrk_3_10 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 70 | 1611 | 4 | -505 | -635 | 2377 | 2 | 44 |
| ob5 | retest | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 77 | 2171 | -115 | 238 | -314 | 2762 | 1 | 44 |
| ob5 | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 78 | 2276 | 28 | 288 | 302 | 2581 | 1 | 44 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 212 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 212 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym15u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 1 | 212 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 212 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 212 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 212 |
| open_range | retest | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 212 |
| open_range | retest_native | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 212 |
| opens | break | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 214 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 214 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 214 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 214 |
| opens | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 214 |
| opens | reject_native | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 214 |
| opens | retest | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 214 |
| opens | retest_native | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 214 |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 2 | 214 |
| prior_day | break_native | vsess_120 | {"n": 3, "k": 0.0} | sym15u / both | 91 | 2959 | -204 | -697 | -3330 | 1835 | 2 | 214 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 115 | 2873 | -837 | 323 | -2884 | 1490 | 1 | 214 |
| prior_day | false_break_native | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 88 | 2868 | -302 | 511 | -1840 | 2689 | 2 | 214 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 214 |
| prior_day | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 2665 | 149 | 475 | -2001 | 1894 | 2 | 214 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 1 | 214 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 1 | 214 |
| profile_nodes | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2489 | -45 | -739 | -7388 | 1667 | 1 | 213 |
| profile_nodes | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 146 | 2992 | -647 | 1127 | -2618 | 2123 | 1 | 213 |
| profile_nodes | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 180 | 2054 | -1160 | -714 | -3668 | 2648 | 2 | 213 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 213 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 213 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 213 |
| profile_nodes | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 109 | 2447 | -490 | 89 | -3842 | 2750 | 1 | 213 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 128 | 2802 | -508 | 830 | -3084 | 3094 | 1 | 213 |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 93 | 2285 | -957 | 2055 | -845 | 2570 | 2 | 214 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 214 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 214 |
| profile_va | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 113 | 1975 | -1229 | 386 | -282 | 2315 | 1 | 214 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 214 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 214 |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 214 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 214 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 290 | 4837 | -1805 | 1243 | 3655 | 5119 | 1 | 214 |
| round | break_native | cusum_28 | {"n": 3, "k": 0.0} | sym15u / both | 295 | 4314 | -1504 | 354 | 1724 | 3855 | 2 | 214 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 214 |
| round | false_break_native | urenko_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 965 | 4358 | -1829 | -1460 | 284 | 6297 | 1 | 214 |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 2 | 214 |
| round | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 313 | 4704 | -419 | 268 | -1458 | 3186 | 1 | 214 |
| round | retest | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 302 | 4728 | -399 | 513 | -1661 | 5351 | 2 | 214 |
| round | retest_native | renko_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 319 | 4722 | -107 | 506 | 309 | 2985 | 2 | 214 |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 171 | 3430 | -820 | 2114 | -94 | 2764 | 1 | 212 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 212 |
| session_hl | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 237 | 2956 | 1816 | 1583 | -123 | 2794 | 2 | 212 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 212 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 1 | 212 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 212 |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 95 | 3205 | -819 | -845 | -75 | 4545 | 2 | 212 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 212 |
| trendline | break | vrb_240 | {"n": 3, "k": 0.5} | plain60/60 / both | 462 | 2505 | 756 | -230 | -1423 | 2603 | 1 | 44 |
| trendline | break_native | kagi_14 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 3812 | 1332 | 2406 | 3337 | 5866 | 1 | 44 |
| trendline | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3067 | 348 | -1809 | 440 | 2553 | 1 | 44 |
| trendline | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 2770 | 640 | -2164 | 534 | 2407 | 1 | 44 |
| trendline | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 154 | 1991 | 1175 | -2319 | 1129 | 389 | 1 | 44 |
| trendline | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 254 | 4010 | 1369 | 1988 | 1894 | 2118 | 1 | 44 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 44 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 44 |
| uw_dp | break | swing_atr_0.4 | {"n": 2, "k": 0.25} | sym15u / both | 63 | 2095 | 0 | 0 | 399 | 1949 | 1 | 214 |
| uw_dp | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 61 | 2272 | 0 | 0 | 421 | 2655 | 1 | 214 |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1430 | 0 | 0 | 210 | 1085 | 1 | 214 |
| uw_dp | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 61 | 1448 | 0 | 0 | 28 | 1366 | 2 | 214 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 74 | 1508 | 0 | 0 | -241 | 886 | 1 | 214 |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 92 | 2286 | 0 | 0 | -217 | 1948 | 2 | 214 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 56 | 1926 | 0 | 0 | 295 | 2044 | 1 | 214 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 214 |
| uw_ndx | break | rng_40 | {"n": 3, "k": 0.25} | sym8u / both | 95 | 2347 | 0 | -1001 | -2044 | 1016 | 2 | 213 |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 102 | 2167 | 0 | -30 | -1920 | 1473 | 2 | 213 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 213 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 213 |
| uw_ndx | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 101 | 1925 | 0 | -40 | -1237 | 2405 | 2 | 213 |
| uw_ndx | reject_native | swing_atr_0.25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 123 | 1867 | 0 | -44 | -84 | 927 | 1 | 213 |
| uw_ndx | retest | swing_atr_0.15 | {"M": 6, "tol": 0.5} | sym15u / both | 95 | 2055 | 0 | 271 | -781 | 2249 | 1 | 213 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 110 | 2464 | 0 | -631 | 475 | 2424 | 1 | 213 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 213 |
| uw_qqq | break_native | renko_10 | {"n": 2, "k": 0.0} | sym8u / both | 261 | 1644 | 0 | -302 | -257 | 171 | 2 | 213 |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 129 | 1746 | 0 | 169 | -358 | 956 | 2 | 213 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 213 |
| uw_qqq | reject | vol_750 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 239 | 1562 | 0 | 34 | -577 | 1228 | 2 | 213 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 213 |
| uw_qqq | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 93 | 1917 | 0 | 437 | -582 | 1450 | 1 | 213 |
| uw_qqq | retest_native | dchg_20 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1938 | 0 | 452 | -985 | 1145 | 1 | 213 |
| vwap | break | renko_40 | {"n": 1, "k": 0.25} | sym8u / both | 149 | 3681 | -1617 | 765 | 724 | 2951 | 2 | 213 |
| vwap | break_native | time_m_1 | {"n": 1, "k": 0.25} | sym8u / both | 178 | 3781 | -1232 | 727 | 3089 | 3780 | 2 | 213 |
| vwap | false_break | mom_40 | {"M": 1, "k": 0.0} | sym15u / both | 152 | 3221 | -789 | 1199 | 397 | 1850 | 1 | 213 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 213 |
| vwap | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 91 | 2424 | -43 | 12 | 1717 | 1574 | 1 | 213 |
| vwap | reject_native | lbrk_3_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 141 | 2247 | 589 | -748 | -179 | 1775 | 1 | 213 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 213 |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 171 | 4078 | 605 | -156 | 1901 | 3767 | 2 | 213 |
| vwap_bands | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 267 | 4022 | -815 | -2816 | 1718 | 4334 | 1 | 212 |
| vwap_bands | break_native | tm10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 430 | 4064 | 400 | -845 | -1061 | 3975 | 2 | 212 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 212 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 212 |
| vwap_bands | reject | tm15 | {"tol": 0.0, "conf": "body"} | asym20u/10u / both | 342 | 4292 | -31 | -470 | 1482 | 2814 | 2 | 212 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 212 |
| vwap_bands | retest | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 238 | 4091 | -2704 | -152 | -2144 | 3461 | 2 | 212 |
| vwap_bands | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 279 | 4137 | 353 | -1853 | 636 | 4160 | 1 | 212 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym15u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 1 | 214 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 214 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 214 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 214 |
| week_month | reject | time_m_2 | {"tol": 0.5, "conf": "body"} | sym15u / both | 38 | 1814 | -158 | -245 | 711 | 1727 | 2 | 214 |
| week_month | reject_native | tick_8000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 72 | 1892 | -134 | -795 | -399 | 2132 | 2 | 214 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 214 |
| week_month | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 38 | 1687 | -215 | -1383 | 15 | 2423 | 2 | 214 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 213 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 213 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 213 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 213 |
| zones | reject | rng_14 | {"tol": 1.0, "conf": "body"} | sym30u / both | 133 | 3041 | 2935 | -1064 | 682 | 3212 | 2 | 213 |
| zones | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | sym30u / both | 134 | 2702 | 2260 | -2018 | 250 | 3460 | 2 | 213 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 213 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 213 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | dchg_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 486 | -54 | -16 | 717 | 995 | 1 | 208 |
| sd5 | break_native | dchg_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 486 | -54 | -16 | 717 | 995 | 1 | 208 |
| sd5 | reject | time_m_10 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 400 | -299 | 61 | 34 | 638 | 1 | 208 |
| sd5 | reject_native | time_m_10 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 400 | -299 | 61 | 34 | 638 | 1 | 208 |
| sdx15 | break | urenko_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 70 | 1077 | -200 | -153 | 1318 | 1345 | 1 | 210 |
| sdx15 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 303 | 3630 | -249 | -670 | -1170 | 3468 | 1 | 210 |
| sdx15 | lim_prox | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 318 | 4155 | 759 | 194 | -1585 | 2577 | 1 | 210 |
| sdx15 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 98 | 2164 | 235 | -369 | -1160 | 1645 | 1 | 210 |
| sdx15 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / both | 111 | 2275 | 39 | -418 | -673 | 3243 | 1 | 210 |
| sdx15 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 210 |
| sdx15 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 210 |
| sdx15 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 58 | 532 | -167 | -117 | 90 | 610 | 1 | 210 |
| sdx3 | break | wrenko_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 174 | 2989 | -298 | 492 | 507 | 2803 | 1 | 209 |
| sdx3 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 4777 | -1113 | 1932 | -2887 | 3527 | 1 | 209 |
| sdx3 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1050 | 6224 | -119 | -224 | -2213 | 5021 | 1 | 209 |
| sdx3 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 305 | 3708 | -457 | -454 | -1839 | 2258 | 1 | 209 |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 117 | 2069 | -220 | -709 | -1314 | 3044 | 1 | 209 |
| sdx3 | rej_native | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 209 |
| sdx3 | rej_zone | cusum_56 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 466 | 5203 | -382 | -1657 | 232 | 3715 | 1 | 209 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 209 |
| sdx30 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 43 | 796 | -102 | 249 | 541 | 651 | 1 | 210 |
| sdx30 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 206 | 3133 | -150 | -817 | -949 | 1695 | 1 | 210 |
| sdx30 | lim_prox | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 232 | 3270 | -189 | -1338 | -13 | 2950 | 1 | 210 |
| sdx30 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 159 | 1658 | 62 | -1293 | -821 | 349 | 1 | 210 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 44 | 1278 | -32 | -42 | -652 | 899 | 1 | 210 |
| sdx30 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 210 |
| sdx30 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 210 |
| sdx5 | break | urenko_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 113 | 2472 | -146 | -590 | 1239 | 2914 | 1 | 210 |
| sdx5 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 434 | 4411 | -88 | -1705 | -1193 | 3777 | 1 | 210 |
| sdx5 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 360 | 5056 | 283 | 711 | -1448 | 2414 | 1 | 210 |
| sdx5 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 258 | 5300 | -710 | -111 | -394 | 5406 | 1 | 210 |
| sdx5 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 213 | 2801 | 412 | -179 | -668 | 1032 | 1 | 210 |
| sdx5 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 284 | 4619 | -598 | -24 | -1073 | 5324 | 1 | 210 |
| sdx5 | rej_zone | mom_28 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 570 | 3704 | -809 | -471 | -2513 | 3980 | 1 | 210 |
| sdx5 | retest | kagi_40 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / short | 93 | 1465 | -6 | -476 | -174 | 1868 | 1 | 210 |
| sdx60 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 246 | -54 | 16 | 405 | -586 | 1 | 209 |
| sdx60 | lim_mid | urenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 144 | 1330 | 181 | -523 | -342 | 1028 | 1 | 209 |
| sdx60 | lim_prox | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 87 | 1502 | -62 | -1032 | -516 | 1170 | 1 | 209 |
| sdx60 | rej | vrb_400 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 46 | 2005 | -46 | -249 | 40 | 1993 | 1 | 209 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | sym15u / short | 30 | 913 | 12 | -370 | -367 | 777 | 1 | 209 |
| sdx60 | rej_native | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 56 | 2048 | -3 | -244 | -270 | 2246 | 1 | 209 |
| sdx60 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 64 | 1710 | 25 | -264 | -895 | 1797 | 1 | 209 |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 182 | 3218 | 348 | 613 | 1501 | 3608 | 1 | 209 |
| sdx_renko28 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 335 | 3926 | -225 | -191 | -3870 | 3498 | 1 | 209 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 332 | 3491 | 102 | -741 | -4298 | 1272 | 1 | 209 |
| sdx_renko28 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 289 | 2322 | -347 | -2305 | -1815 | 504 | 1 | 209 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 105 | 2509 | -260 | -487 | -1295 | 1700 | 1 | 209 |
| sdx_renko28 | rej_native | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 290 | 3009 | -86 | -3096 | -4876 | 1290 | 1 | 209 |
| sdx_renko28 | rej_zone | rng_10 | {"d": "E", "F": 0, "tgt": "opp"} | OWN zone/level bracket / both | 715 | 3555 | 4 | -615 | -2122 | 2404 | 1 | 209 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2189 | 230 | -226 | -1251 | 1966 | 1 | 209 |
| sdx_rng28 | break | mrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 803 | 5407 | 129 | 1213 | -529 | 4740 | 1 | 209 |
| sdx_rng28 | lim_mid | vrb_400 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 386 | 3058 | -130 | 896 | 302 | 1004 | 1 | 209 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 209 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 180 | 4551 | 663 | 859 | -858 | 6367 | 1 | 209 |
| sdx_rng28 | rej_flow | vrb_400 | {"d": "E", "F": 0} | sym15u / both | 238 | 2255 | -129 | -737 | -175 | 2887 | 1 | 209 |
| sdx_rng28 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 817 | 2929 | -775 | -407 | -1591 | 2117 | 1 | 209 |
| sdx_rng28 | rej_zone | drb_3500 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 270 | 3342 | 99 | 47 | 654 | 4264 | 1 | 209 |
| sdx_rng28 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 447 | 3522 | -103 | 677 | -611 | 2695 | 1 | 209 |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 392 | 3031 | 130 | 198 | 714 | 2880 | 1 | 209 |
| sdx_vol1100 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 351 | 3043 | -308 | 140 | -2784 | 1952 | 1 | 209 |
| sdx_vol1100 | lim_prox | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 334 | 4466 | -175 | -58 | -998 | 5680 | 1 | 209 |
| sdx_vol1100 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 281 | 4086 | 117 | -233 | -2354 | 3347 | 1 | 209 |
| sdx_vol1100 | rej_flow | dol_6000 | {"d": "E", "F": 9} | plain60/60 / both | 204 | 2004 | -631 | 200 | -652 | 1775 | 1 | 209 |
| sdx_vol1100 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 315 | 4153 | -19 | -209 | -2233 | 3638 | 1 | 209 |
| sdx_vol1100 | rej_zone | cusum_80 | {"d": "E", "F": 9, "tgt": "r2"} | OWN zone/level bracket / both | 306 | 3386 | -436 | -440 | -706 | 2776 | 1 | 209 |
| sdx_vol1100 | retest | urenko_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 273 | 2414 | 61 | -321 | 464 | 2757 | 1 | 209 |
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 664 | 4358 | 1020 | 111 | 108 | 5473 | 1 | 206 |
| fib15 | break_native | vol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 445 | 3679 | -182 | 435 | 199 | 3816 | 1 | 206 |
| fib15 | false_break | time_s_15 | {"M": 1, "k": 0.0} | sym15u / both | 744 | 4428 | -1523 | -1122 | -984 | 4812 | 1 | 206 |
| fib15 | false_break_native | time_s_15 | {"M": 1, "k": 0.0} | sym15u / both | 744 | 4428 | -1523 | -1122 | -984 | 4812 | 1 | 206 |
| fib15 | pullback | vsess_50 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 318 | 3324 | -457 | -527 | 77 | 2115 | 1 | 206 |
| fib15 | pullback_native | vsess_50 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 356 | 3930 | -915 | 75 | 7 | 2275 | 1 | 206 |
| fib15 | reject | cusum_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 693 | 3298 | -110 | -69 | 2021 | 3121 | 1 | 206 |
| fib15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 3684 | 770 | -1991 | 1912 | 3118 | 1 | 206 |
| fib15 | retest | cusum_80 | {"M": 6, "tol": 0.5} | sym15u / both | 224 | 3983 | -247 | 278 | 481 | 3510 | 1 | 206 |
| fib15 | retest_native | tm45 | {"M": 6, "tol": 0.5} | sym15u / both | 347 | 4680 | -438 | -1393 | -873 | 4139 | 1 | 206 |
| fib5 | break | vol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 491 | 3973 | 91 | 1547 | 4 | 5198 | 1 | 206 |
| fib5 | break_native | cusum_56 | {"n": 2, "k": 0.25} | sym15u / both | 298 | 4186 | 261 | 1556 | 413 | 6989 | 1 | 206 |
| fib5 | false_break | vsess_30 | {"M": 3, "k": 0.5} | sym15u / both | 319 | 4950 | 305 | -527 | 1711 | 5618 | 1 | 206 |
| fib5 | false_break_native | vol_4000 | {"M": 1, "k": 0.0} | sym15u / both | 294 | 4515 | -170 | 1754 | 1432 | 4673 | 1 | 206 |
| fib5 | pullback | vsess_300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 432 | 4321 | -117 | -2350 | -621 | 3568 | 2 | 206 |
| fib5 | pullback_native | vsess_300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 432 | 4321 | -117 | -2350 | -621 | 3568 | 2 | 206 |
| fib5 | reject | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 229 | 4892 | 475 | 656 | -543 | 5747 | 1 | 206 |
| fib5 | reject_native | rng_56 | {"tol": 0.0, "conf": "close"} | sym15u / both | 280 | 4572 | -215 | 889 | -1110 | 4953 | 1 | 206 |
| fib5 | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 206 |
| fib5 | retest_native | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5442 | 127 | -748 | -4550 | 7020 | 1 | 206 |
| fib60 | break | vol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 562 | 4258 | -69 | -393 | -103 | 3678 | 1 | 207 |
| fib60 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 556 | 4408 | -100 | 188 | -541 | 3433 | 1 | 207 |
| fib60 | false_break | dib_400 | {"M": 3, "k": 0.5} | sym15u / both | 440 | 3161 | 124 | -742 | 6 | 3328 | 1 | 207 |
| fib60 | false_break_native | tm45 | {"M": 1, "k": 0.0} | plain60/60 / both | 576 | 3152 | 140 | 511 | -438 | 2957 | 1 | 207 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 133 | 2500 | 277 | -321 | -1857 | 3041 | 1 | 207 |
| fib60 | pullback_native | mom_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 190 | 2738 | 33 | 315 | 981 | 2462 | 1 | 207 |
| fib60 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 279 | 5055 | 422 | -1153 | -276 | 5536 | 2 | 207 |
| fib60 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 283 | 4177 | 118 | -368 | -74 | 5093 | 2 | 207 |
| fib60 | retest | drb_400 | {"M": 10, "tol": 0.5} | plain60/60 / both | 477 | 2489 | -495 | -53 | -783 | 3440 | 1 | 207 |
| fib60 | retest_native | vol_750 | {"M": 10, "tol": 0.5} | plain60/60 / both | 499 | 3584 | -227 | -506 | -608 | 4451 | 1 | 207 |
| fibr_dev | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 492 | 1108 | 1598 | 3481 | 1 | 43 |
| fibr_dev | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 515 | 1108 | 1598 | 3481 | 1 | 43 |
| fibr_dev | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 316 | 3799 | 772 | 931 | 1745 | 3779 | 1 | 43 |
| fibr_dev | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3556 | 1165 | 401 | 1540 | 3473 | 1 | 43 |
| fibr_dev | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 268 | 3144 | -189 | 873 | -2406 | 3760 | 1 | 43 |
| fibr_dev | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 4083 | -588 | 684 | -1434 | 4699 | 1 | 43 |
| fibr_dev | retest | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 43 |
| fibr_dev | retest_native | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 43 |
| fibr_ib | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 43 |
| fibr_ib | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 43 |
| fibr_ib | false_break | vrb_25000 | {"M": 2, "k": 0.5} | sym15u / short | 39 | 992 | 39 | 325 | -146 | 918 | 1 | 43 |
| fibr_ib | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 218 | 954 | 2426 | 1 | 43 |
| fibr_ib | reject | vrb_25000 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 54 | 697 | -111 | 11 | 67 | 435 | 1 | 43 |
| fibr_ib | reject_native | pnf_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | 460 | -101 | 173 | 929 | 1 | 43 |
| fibr_ib | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 1139 | 116 | -501 | 309 | 1475 | 1 | 43 |
| fibr_ib | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 60 | 1416 | 2 | -1461 | -161 | 2126 | 1 | 43 |
| fibr_on | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 43 |
| fibr_on | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 43 |
| fibr_on | false_break | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 31 | 1342 | 57 | 761 | 588 | 2157 | 1 | 43 |
| fibr_on | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 43 | 1558 | 176 | 575 | 928 | 2229 | 1 | 43 |
| fibr_on | reject | kagi_112 | {"tol": 0.0, "conf": "close"} | sym15u / both | 39 | 769 | 6 | 260 | 62 | 989 | 1 | 43 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 1 | 43 |
| fibr_on | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 37 | 1166 | -61 | -3 | 830 | 1123 | 1 | 43 |
| fibr_on | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 50 | 1220 | -2 | 140 | 639 | 1292 | 1 | 43 |
| fibr_or | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 43 |
| fibr_or | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 43 |
| fibr_or | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 43 |
| fibr_or | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 43 |
| fibr_or | reject | vrb_400 | {"tol": 0.0, "conf": "close"} | sym15u / both | 31 | 708 | 124 | -1003 | -717 | 358 | 1 | 43 |
| fibr_or | reject_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / short | 36 | 808 | 243 | -645 | -131 | 1067 | 1 | 43 |
| fibr_or | retest | urenko_80 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1143 | 260 | -956 | -170 | 1606 | 1 | 43 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 1 | 43 |
| fibr_pd | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 43 |
| fibr_pd | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 43 |
| fibr_pd | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 678 | 3579 | -1005 | -279 | 981 | 5723 | 1 | 43 |
| fibr_pd | false_break_native | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 666 | 3464 | -1047 | -220 | 995 | 5358 | 1 | 43 |
| fibr_pd | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 349 | 2746 | -87 | -674 | -1595 | 3667 | 1 | 43 |
| fibr_pd | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 342 | 2899 | 228 | -466 | 1300 | 2291 | 1 | 43 |
| fibr_pd | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / both | 603 | 2661 | 78 | 584 | 477 | 2260 | 1 | 43 |
| fibr_pd | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 686 | 3100 | 305 | 253 | 787 | 3272 | 1 | 43 |
| piv_cama | break | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 697 | 3237 | 208 | 306 | -1672 | 2963 | 1 | 43 |
| piv_cama | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 306 | 3386 | 269 | 1492 | 959 | 3771 | 1 | 43 |
| piv_cama | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 718 | 2761 | -500 | -98 | -1350 | 3065 | 1 | 43 |
| piv_cama | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 832 | 3200 | -1113 | -1440 | 84 | 4151 | 1 | 43 |
| piv_cama | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 319 | 3165 | -462 | -874 | 1496 | 3297 | 1 | 43 |
| piv_cama | reject_native | vrb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 343 | 3789 | -60 | -267 | -488 | 5147 | 1 | 43 |
| piv_cama | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 787 | 2950 | -169 | -864 | 823 | 3736 | 1 | 43 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 1 | 43 |
| piv_floor | break | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 43 |
| piv_floor | break_native | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 43 |
| piv_floor | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 552 | 3654 | -727 | -863 | 251 | 3755 | 1 | 43 |
| piv_floor | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 553 | 3592 | -577 | -783 | 419 | 3557 | 1 | 43 |
| piv_floor | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 259 | 2195 | -719 | -1237 | -497 | 3369 | 1 | 43 |
| piv_floor | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 222 | 2515 | 703 | -945 | -1135 | 3210 | 1 | 43 |
| piv_floor | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 468 | 3194 | -7 | 722 | -1698 | 3884 | 1 | 43 |
| piv_floor | retest_native | mrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 2992 | 134 | -1048 | 1326 | 4059 | 1 | 43 |
| piv_wf | break | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 43 |
| piv_wf | break_native | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 43 |
| piv_wf | false_break | frenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 299 | 2465 | -1481 | -1157 | 560 | 2742 | 1 | 43 |
| piv_wf | false_break_native | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 288 | 2691 | -648 | -1103 | 567 | 3937 | 1 | 43 |
| piv_wf | reject | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 278 | 2564 | -131 | -855 | 521 | 3098 | 1 | 43 |
| piv_wf | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 294 | 3050 | -355 | -1518 | -2651 | 4373 | 1 | 43 |
| piv_wf | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 265 | 3002 | -306 | -16 | -2883 | 4150 | 1 | 43 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 1 | 43 |
| swcluster | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1027 | -344 | -315 | -623 | 734 | 1 | 44 |
| swcluster | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1024 | -227 | -349 | -670 | 879 | 1 | 44 |
| swcluster | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 44 |
| swcluster | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 44 |
| swcluster | reject | vrb_400 | {"tol": 1.0, "conf": "body"} | sym15u / short | 30 | 685 | 22 | -671 | -117 | 826 | 1 | 44 |
| swcluster | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1097 | 102 | -253 | -33 | 902 | 1 | 44 |
| swcluster | retest | dol_350 | {"M": 10, "tol": 0.5} | sym15u / both | 50 | 1005 | -370 | 289 | 169 | 1869 | 1 | 44 |
| swcluster | retest_native | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 52 | 973 | -319 | 31 | 1182 | 1353 | 1 | 44 |
| swsr15 | break | urenko_28 | {"n": 3, "k": 0.5} | plain60/60 / both | 607 | 2835 | -125 | 665 | 1504 | 4520 | 1 | 44 |
| swsr15 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 639 | 2579 | 273 | 977 | -86 | 2926 | 1 | 44 |
| swsr15 | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 283 | 2324 | -223 | -60 | -629 | 1560 | 1 | 44 |
| swsr15 | false_break_native | kagi_20 | {"M": 2, "k": 0.5} | sym15u / both | 322 | 2961 | 743 | -10 | -136 | 4162 | 1 | 44 |
| swsr15 | reject | vrb_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 301 | 3075 | -273 | -553 | -612 | 4062 | 1 | 44 |
| swsr15 | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 754 | 3070 | 146 | 508 | -2024 | 2007 | 1 | 44 |
| swsr15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 44 |
| swsr15 | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 44 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 306 | 3427 | -11 | 1352 | -1241 | 2548 | 1 | 44 |
| swsr5 | break_native | wrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 789 | 3514 | 80 | 1736 | 1316 | 4658 | 1 | 44 |
| swsr5 | false_break | vrb_240 | {"M": 2, "k": 0.5} | sym15u / both | 410 | 2867 | 43 | -139 | -1415 | 1886 | 1 | 44 |
| swsr5 | false_break_native | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 272 | 3016 | 270 | 578 | -45 | 3124 | 1 | 44 |
| swsr5 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 228 | 4159 | 82 | 315 | 42 | 4336 | 1 | 44 |
| swsr5 | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 899 | 3040 | 121 | -370 | 48 | 3663 | 2 | 44 |
| swsr5 | retest | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 261 | 4292 | -147 | -323 | -3129 | 3722 | 1 | 44 |
| swsr5 | retest_native | urenko_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 592 | 3645 | -130 | 1122 | 406 | 2944 | 1 | 44 |
| swsr60 | break | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 44 |
| swsr60 | break_native | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 44 |
| swsr60 | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 44 |
| swsr60 | false_break_native | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 44 |
| swsr60 | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / short | 63 | 901 | 155 | -797 | 359 | 831 | 1 | 44 |
| swsr60 | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 1613 | 196 | 417 | -574 | 1076 | 1 | 44 |
| swsr60 | retest | vrb_700 | {"M": 10, "tol": 0.5} | plain60/60 / both | 278 | 2336 | -13 | -70 | -477 | 2897 | 1 | 44 |
| swsr60 | retest_native | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 254 | 2089 | 120 | -274 | -719 | 2097 | 1 | 44 |
| stack | break | mom_14 | {"k": 3, "cw": 1.0} | sym15u / both | 169 | 3999 | -465 | -485 | -583 | 3205 | 1 | 214 |
| stack | break_native | frenko_28 | {"k": 2, "cw": 0.5} | sym15u / both | 268 | 4216 | 269 | 854 | 910 | 5395 | 1 | 214 |
| stack | reject | tick_300 | {"k": 2, "cw": 2.0} | asym10u/20u / both | 186 | 2906 | 61 | 648 | 73 | 1352 | 2 | 214 |
| stack | reject_native | vrb_240 | {"k": 4, "cw": 2.0} | sym15u / both | 213 | 2786 | -123 | 249 | -1159 | 3633 | 1 | 214 |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 791 | 86 | 772 | 1607 | 2 | 212 |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 841 | 86 | 772 | 1607 | 2 | 212 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 212 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 212 |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 1480 | -474 | -213 | -350 | 2822 | 1 | 212 |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1443 | 732 | 638 | 74 | 699 | 1 | 212 |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 899 | -1465 | 616 | 147 | 1417 | 1 | 212 |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 821 | -381 | -305 | -21 | 226 | 1 | 212 |
| book_walls_loose | break | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 461 | 137 | 581 | 4298 | 2 | 214 |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 411 | 137 | 581 | 4298 | 2 | 214 |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 1856 | -61 | -317 | 372 | 986 | 1 | 214 |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 62 | 1806 | 153 | -209 | 562 | 1133 | 1 | 214 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 329 | 3303 | -618 | -483 | -2918 | 3949 | 1 | 214 |
| book_walls_loose | reject_native | cusum_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 260 | 3242 | 405 | -680 | 458 | 3643 | 1 | 214 |
| book_walls_loose | retest | tm20 | {"M": 6, "tol": 0.5} | sym15u / both | 353 | 2344 | -963 | -496 | 59 | 3790 | 1 | 214 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 438 | 1781 | -951 | -565 | -1164 | 2912 | 1 | 214 |
| channel | break | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 44 |
| channel | break_native | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 44 |
| channel | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 44 |
| channel | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 44 |
| channel | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 319 | 2451 | -40 | -904 | 1980 | 74 | 1 | 44 |
| channel | reject_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 690 | 2704 | -28 | 101 | 2034 | 3732 | 1 | 44 |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 488 | 3847 | -658 | -725 | -31 | 3628 | 1 | 44 |
| channel | retest_native | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 488 | 3847 | -658 | -725 | -31 | 3628 | 1 | 44 |
| fvg15 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 191 | 4507 | -198 | 255 | 2301 | 3589 | 1 | 44 |
| fvg15 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 191 | 4507 | -198 | 255 | 2301 | 3589 | 1 | 44 |
| fvg15 | false_break | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 179 | 4460 | -421 | 153 | 1819 | 3544 | 1 | 44 |
| fvg15 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 172 | 4624 | -258 | 241 | 2280 | 3548 | 1 | 44 |
| fvg15 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 172 | 2211 | -152 | 845 | -1066 | 1952 | 1 | 44 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 192 | 3238 | -531 | 176 | 1230 | 3572 | 1 | 44 |
| fvg15 | retest | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 4311 | -153 | 822 | -98 | 4262 | 1 | 44 |
| fvg15 | retest_native | vrb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 178 | 4081 | -555 | 1076 | -732 | 4005 | 1 | 44 |
| fvg5 | break | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 450 | 3449 | 423 | 609 | -1560 | 5044 | 1 | 44 |
| fvg5 | break_native | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 461 | 3420 | 327 | 253 | -1454 | 4831 | 1 | 44 |
| fvg5 | false_break | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 333 | 2970 | -57 | -288 | -1769 | 3049 | 1 | 44 |
| fvg5 | false_break_native | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 332 | 3092 | -31 | -408 | -1857 | 3270 | 1 | 44 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 44 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 44 |
| fvg5 | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3156 | -584 | -548 | -2079 | 4493 | 1 | 44 |
| fvg5 | retest_native | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 270 | 3569 | -603 | -322 | -233 | 4778 | 1 | 44 |
| gaps | break | vsess_300 | {"n": 1, "k": 0.0} | sym8u / both | 315 | 3765 | -628 | 110 | 958 | 3153 | 2 | 214 |
| gaps | break_native | vsess_300 | {"n": 1, "k": 0.0} | sym8u / both | 315 | 3765 | -628 | 110 | 958 | 3153 | 2 | 214 |
| gaps | false_break | dchg_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 435 | 3848 | -306 | -211 | 1012 | 4675 | 1 | 214 |
| gaps | false_break_native | dchg_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 435 | 3838 | -349 | 236 | 1031 | 4424 | 1 | 214 |
| gaps | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2273 | 361 | 369 | -613 | 1685 | 1 | 214 |
| gaps | reject_native | renko_20 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 89 | 2688 | -72 | -741 | 685 | 2799 | 2 | 214 |
| gaps | retest | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 2373 | -138 | 438 | 1115 | 1777 | 1 | 214 |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2887 | -129 | 409 | 967 | 2191 | 1 | 214 |
| mmove | break | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 575 | 3266 | -125 | -274 | 199 | 3622 | 1 | 44 |
| mmove | break_native | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 581 | 2913 | -307 | -72 | 462 | 3355 | 1 | 44 |
| mmove | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 322 | 4674 | -803 | 888 | 1620 | 3258 | 1 | 44 |
| mmove | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 322 | 5031 | -813 | 1377 | 2286 | 3597 | 1 | 44 |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 274 | 2229 | -215 | -135 | -986 | 3788 | 1 | 44 |
| mmove | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 494 | 2494 | -127 | -205 | -307 | 3948 | 1 | 44 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 270 | 4009 | -265 | 707 | 166 | 4154 | 1 | 44 |
| mmove | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 3501 | 153 | -509 | -661 | 2363 | 1 | 44 |
| ob15 | break | mrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 87 | 1145 | -110 | 211 | 463 | 1243 | 1 | 44 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 1 | 44 |
| ob15 | false_break | vrb_240 | {"M": 1, "k": 0.0} | plain60/60 / both | 100 | 869 | 387 | 312 | 224 | 988 | 1 | 44 |
| ob15 | false_break_native | vrb_240 | {"M": 1, "k": 0.0} | plain60/60 / both | 100 | 869 | 387 | 312 | 224 | 988 | 1 | 44 |
| ob15 | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 59 | 1016 | -445 | -109 | 212 | 1364 | 1 | 44 |
| ob15 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 79 | 1546 | -161 | -222 | 273 | 1825 | 1 | 44 |
| ob15 | retest | mrenko_10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 | 729 | 168 | 295 | -73 | 1126 | 1 | 44 |
| ob15 | retest_native | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 79 | 942 | 14 | -160 | 421 | 1025 | 1 | 44 |
| ob5 | break | lbrk_3_10 | {"n": 2, "k": 0.5} | sym15u / both | 159 | 2060 | -208 | 613 | 1742 | 2427 | 2 | 44 |
| ob5 | break_native | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 118 | 1866 | 238 | 603 | 530 | 2260 | 1 | 44 |
| ob5 | false_break | lbrk_3_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 169 | 2782 | -155 | -395 | 376 | 2558 | 2 | 44 |
| ob5 | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.5} | plain60/60 / both | 193 | 2283 | -258 | -394 | -88 | 3053 | 2 | 44 |
| ob5 | reject | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 81 | 2035 | 288 | -683 | -526 | 2219 | 1 | 44 |
| ob5 | reject_native | vrb_400 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 241 | 2766 | -174 | -303 | 752 | 2844 | 1 | 44 |
| ob5 | retest | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 114 | 2116 | -453 | -364 | 1873 | 1885 | 1 | 44 |
| ob5 | retest_native | mrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1697 | 111 | -230 | 324 | 2333 | 1 | 44 |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 213 |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 53 | 1298 | 117 | 673 | 306 | 1466 | 2 | 213 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 213 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 213 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 213 |
| open_range | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 1841 | -107 | -871 | 61 | 1790 | 1 | 213 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 213 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 213 |
| opens | break | vrb_240 | {"n": 1, "k": 0.0} | plain60/60 / both | 368 | 3121 | -294 | 675 | 1044 | 3453 | 1 | 215 |
| opens | break_native | vrb_240 | {"n": 1, "k": 0.0} | plain60/60 / both | 368 | 3121 | -294 | 675 | 1044 | 3453 | 1 | 215 |
| opens | false_break | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 215 |
| opens | false_break_native | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 215 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 215 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 215 |
| opens | retest | tm10 | {"M": 3, "tol": 0.5} | sym15u / both | 435 | 3568 | -310 | -114 | -1092 | 4604 | 2 | 215 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 215 |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 215 |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 215 |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 2 | 215 |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 2 | 215 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 215 |
| prior_day | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 215 |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 2 | 215 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 215 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 214 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 214 |
| profile_nodes | false_break | vsess_300 | {"M": 1, "k": 0.5} | asym10u/20u / both | 329 | 4201 | -503 | -1129 | -328 | 5429 | 2 | 214 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 214 |
| profile_nodes | reject | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 217 | 3451 | -794 | -877 | -1862 | 3671 | 2 | 214 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 214 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 1 | 214 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 295 | 4808 | -512 | 139 | 1484 | 5809 | 1 | 214 |
| profile_va | break | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 3734 | 98 | -1260 | -135 | 2075 | 1 | 215 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 215 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 1 | 215 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 1 | 215 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 215 |
| profile_va | reject_native | rng_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 523 | 3959 | 232 | -523 | -699 | 2840 | 2 | 215 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 215 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 1 | 215 |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2 | 215 |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 2 | 215 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 215 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 215 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 215 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 215 |
| round | retest | vsess_50 | {"M": 3, "tol": 0.0} | plain60/60 / both | 480 | 4161 | -390 | -850 | -175 | 4245 | 1 | 215 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 1 | 215 |
| session_hl | break | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 213 |
| session_hl | break_native | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 213 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym15u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 1 | 213 |
| session_hl | false_break_native | mom_112 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1310 | 345 | -28 | -555 | 1077 | 1 | 213 |
| session_hl | reject | swing_pct_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 31 | 966 | 156 | 215 | 82 | 717 | 1 | 213 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 213 |
| session_hl | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 930 | 394 | -159 | 104 | 1490 | 1 | 213 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 1 | 213 |
| trendline | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 281 | 4047 | -334 | -565 | -398 | 3647 | 1 | 44 |
| trendline | break_native | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 281 | 4047 | -334 | -565 | -398 | 3647 | 1 | 44 |
| trendline | false_break | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 2652 | 5 | 374 | -456 | 3314 | 1 | 44 |
| trendline | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 290 | 2491 | 555 | -381 | 1308 | 960 | 1 | 44 |
| trendline | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 249 | 2489 | -856 | 1637 | -467 | 1528 | 1 | 44 |
| trendline | reject_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 3233 | -304 | 1786 | -548 | 2457 | 1 | 44 |
| trendline | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / short | 107 | 2672 | -76 | -1151 | -251 | 3477 | 1 | 44 |
| trendline | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / short | 110 | 2940 | -11 | -899 | -333 | 3003 | 1 | 44 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 214 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 214 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 214 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 214 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 214 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 1 | 214 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 214 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 214 |
| uw_ndx | break | renko_14 | {"n": 2, "k": 0.5} | sym8u / both | 331 | 2910 | 0 | -114 | 269 | 2774 | 2 | 214 |
| uw_ndx | break_native | renko_28 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 2821 | 0 | 832 | 1783 | 4375 | 2 | 214 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 214 |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 296 | 2751 | 0 | 605 | 329 | 2931 | 2 | 214 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 214 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 214 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 214 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 214 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 214 |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 444 | 3333 | 0 | 825 | 798 | 2619 | 2 | 214 |
| uw_qqq | false_break | cusum_112 | {"M": 1, "k": 0.0} | sym15u / both | 189 | 2553 | 0 | -215 | 1193 | 2621 | 1 | 214 |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 228 | 2553 | 0 | -518 | 1669 | 3080 | 2 | 214 |
| uw_qqq | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 211 | 4506 | 0 | -170 | -57 | 4909 | 1 | 214 |
| uw_qqq | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 585 | 4310 | 0 | 145 | -321 | 3898 | 2 | 214 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 214 |
| uw_qqq | retest_native | renko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 252 | 2711 | 0 | -192 | 815 | 3673 | 2 | 214 |
| vwap | break | vrb_240 | {"n": 2, "k": 0.25} | sym15u / both | 288 | 5309 | -171 | -93 | 2594 | 5153 | 1 | 214 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 214 |
| vwap | false_break | pasl_10 | {"M": 1, "k": 0.0} | sym15u / both | 272 | 3707 | 24 | -1009 | 1272 | 5049 | 1 | 214 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 214 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 214 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 214 |
| vwap | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym30u / both | 244 | 3984 | 745 | -933 | 4153 | 6617 | 2 | 214 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 214 |
| vwap_bands | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 618 | 4055 | 470 | -88 | 753 | 4340 | 1 | 213 |
| vwap_bands | break_native | tm20 | {"n": 3, "k": 0.25} | asym15u/30u / both | 436 | 4079 | -537 | -1426 | -2939 | 4423 | 2 | 213 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 213 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 213 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 213 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 213 |
| vwap_bands | retest | tm15 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 506 | 4018 | -916 | -1658 | -2940 | 3753 | 2 | 213 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 213 |
| week_month | break | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1357 | -472 | -345 | 67 | 873 | 1 | 215 |
| week_month | break_native | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1508 | -384 | -405 | 191 | 1025 | 1 | 215 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 215 |
| week_month | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 53 | 1816 | -233 | -4 | 426 | 2452 | 1 | 215 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 215 |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | 1233 | -161 | 407 | -240 | 443 | 1 | 215 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 215 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 215 |
| zones | break | rng_40 | {"n": 1, "k": 0.5} | sym8u / both | 199 | 3211 | 33 | 78 | 580 | 2604 | 2 | 214 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 214 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 214 |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 177 | 2863 | -154 | 660 | -299 | 2423 | 2 | 214 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 196 | 3254 | -73 | -1065 | -502 | 3105 | 1 | 214 |
| zones | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 278 | 3157 | -1008 | -1664 | -1608 | 2818 | 2 | 214 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 214 |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 161 | 2948 | -119 | -238 | 150 | 2390 | 2 | 214 |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 3357 of 9120 (modules x 304 bar rows); pass-1 result files written in the last hour: 5153 (all modules); ETA for these at that rate if they were alone: 0.7 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

