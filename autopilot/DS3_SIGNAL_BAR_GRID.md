# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN

## NOTICE 1 (W-LEVEL, 13:20Z) - POINT-AND-FIGURE (pnf_*) LOOK-AHEAD CHECK: NO LOOK-AHEAD IN THE BAR CONSTRUCTION
- Test: an independent causal replay of the P&F rule (box = p x trailing-20-day median range scale, excluding today; 3-box reversal) on 4 trading days of NQ prints (202606), session by session, versus the stored pnf_14 bars: column count, column extreme (close) and the bar's known_ts (= the print that confirms the reversal) agree in every complete session (20 of 20; the 21st is a session cut by my day-file window, not a bar error). The fill (fpx/fts) is the first print strictly after known_ts in every checked bar.
- What the bar IS: a column is emitted only when price has moved 3 boxes against it; its close is the column EXTREME and its time is the confirming print. So at the signal the market is already 3 boxes away from the "close" and the entry is taken there (first print after known_ts + slippage). That is causal but it makes every pnf signal a "after a 3-box reversal" entry, so break-type triggers on pnf bars enter after the reversal, not at the break. No future information is used.
- Still to test (W-LEVEL): robustness of the pnf level cells to a 1 s / 5 s fill delay, and whether the pnf winners are just "enter 3 boxes after the extreme" (a momentum-after-reversal effect that other bar types do not have). Until then pnf level cells carry the caution flag "construction-specific".

VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 13:33Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**CORRECTION 02:30Z (read first): every random-entry null file produced by the fast path before 02:30Z was an exact COPY of the real result (the fast runner did not recognise the tag p1randN), so all earlier excess / percentile / null columns and the claim of null draws were INVALID (excess 0.0, percentile 1.00 = no null). 31,413 such files were deleted; the 1,411 legacy-runner null files are valid. Nulls are being regenerated; a null column is shown only when the null pool covers >= 80% of the real pool, otherwise it reads NO NULL YET. Real results are unaffected.**

**NULL AUDIT (assertions: a null file must differ from its real file; null mean pts/trade at plain 60/60 must be negative and above -6; a tag failing is rejected and its columns read NO NULL YET):**
| null tag | files | sampled | identical to real | mean pts/trade London / NYAM / NYPM / Asia | accepted | share of real cells covered (per session) | note |
|---|---|---|---|---|---|---|---|
| p1rand1 | 15906 | 400 | 0.000 | -0.68 / -0.62 / -0.64 / -0.97 | YES | {"Asia": 0.841, "London": 0.839, "NYAM": 0.839, "NYPM": 0.84} |  |
| p1rand2 | 15849 | 400 | 0.000 | -0.67 / -0.61 / -0.59 / -0.96 | YES | {"Asia": 0.836, "London": 0.834, "NYAM": 0.834, "NYPM": 0.835} |  |
| p1rand3 | 222 | 222 | 0.000 | -0.67 / -0.59 / -0.60 / -1.00 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand4 | 222 | 222 | 0.000 | -0.66 / -0.59 / -0.60 / -0.99 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
| p1rand5 | 222 | 222 | 0.000 | -0.68 / -0.61 / -0.59 / -1.02 | YES | {"Asia": null, "London": null, "NYAM": null, "NYPM": null} |  |
Draws per cell = number of accepted null tags covering the pool (see per-session null_cover); needs >= 5 before any LEAD label.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 13:33Z):** result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 16109, "p1rand10": 3, "p1rand11": 3, "p1rand12": 3, "p1rand13": 3, "p1rand14": 4, "p1rand15": 3, "p1rand16": 4, "p1rand17": 3, "p1rand18": 3, "p1rand19": 3, "p1rand2": 16104, "p1rand20": 4, "p1rand21": 3, "p1rand22": 3, "p1rand23": 3, "p1rand24": 3, "p1rand25": 3, "p1rand3": 245, "p1rand4": 245, "p1rand5": 244, "p1rand6": 4, "p1rand7": 4, "p1rand8": 4, "p1rand9": 4, "p1real": 23331, "p1realx": 219, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"Asia": 2, "London": 2, "NYAM": 2, "NYPM": 2}; live-seven baseline: IN (125 rows). Sessions published: Asia, London, NYAM, NYPM (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 13:33Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1flow_absorbx": 71, "p1flow_bookx": 71, "p1flow_deltax": 72, "p1flow_speedx": 71, "p1flow_wallx": 71, "p1rand1": 16109, "p1rand10": 3, "p1rand11": 3, "p1rand12": 3, "p1rand13": 3, "p1rand14": 4, "p1rand15": 3, "p1rand16": 4, "p1rand17": 3, "p1rand18": 3, "p1rand19": 3, "p1rand2": 16104, "p1rand20": 4, "p1rand21": 3, "p1rand22": 3, "p1rand23": 3, "p1rand24": 3, "p1rand25": 3, "p1rand3": 245, "p1rand4": 245, "p1rand5": 244, "p1rand6": 4, "p1rand7": 4, "p1rand8": 4, "p1rand9": 4, "p1real": 23331, "p1realx": 219, "rand1": 0, "real": 1654}; loop status: 2026-11-18T13:26Z rows=322 mods=146 todo=76689 running=0. 
Cells scored per session: {"Asia": 3550478, "London": 3438282, "NYAM": 3712966, "NYPM": 3727746}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -18.5 | -0.017 | 1072.8 | 0.43 | -27.7 | -78.3 | 1.2 | 18.0 | -19.7 | 0.00 | -20.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -16.9 | -0.010 | 999.5 | 0.43 | -26.5 | -64.3 | 6.1 | 12.1 | -23.0 | 0.00 | -19.5 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -52.8 [-68.3; 0.00] | -29.6 [-34.0; 0.00] | -11.6 [-27.6; 0.00] | 2.5 [0.6; 0.50] |
| bands (native) | -29.4 [-5.3; 0.50] | -9.7 [-16.3; 0.00] | -19.4 [-3.2; 0.50] | -22.5 [-0.8; 0.50] |
| barnative | -14.0 [5.0; 0.50] | 5.3 [26.5; 1.00] | 6.5 [20.6; 1.00] | -14.4 [-1.4; 0.50] |
| book | -46.6 [-39.9; 0.00] | n/a (no signals by construction) | -2.7 [9.2; 0.50] | n/a (no signals by construction) |
| book (native) | 15.0 [12.5; 1.00] | n/a (no signals by construction) | 10.2 [20.5; 1.00] | n/a (no signals by construction) |
| confluence | -16.8 [-31.3; 0.00] | -14.0 [-1.9; 0.50] | 0.9 [-2.4; 0.50] | 14.7 [18.2; 1.00] |
| levels | -25.6 [-20.7; 0.00] | -28.0 [-37.4; 0.00] | 27.9 [42.5; 1.00] | -23.2 [-29.5; 0.00] |
| levels (native) | -31.9 [-28.7; 0.00] | 2.1 [18.9; 1.00] | 13.0 [13.9; 1.00] | -14.9 [17.3; 1.00] |
| live | -4.6 [5.3; 0.50] | -16.9 [-24.3; 0.00] | 0.2 [22.0; 1.00] | 6.3 [-4.3; 0.50] |
| manual | -8.5 [6.1; 0.50] | -5.2 [-19.9; 0.00] | -36.6 [-25.9; 0.00] | -5.0 [5.1; 0.50] |
| manual (native) | 6.7 [10.7; 1.00] | -30.5 [-37.5; 0.00] | -18.2 [-1.6; 0.50] | -27.1 [0.7; 0.50] |
| momentum | 3.7 [11.8; 0.50] | 14.9 [23.4; 1.00] | -9.9 [0.6; 0.50] | -4.9 [1.9; 0.50] |
| momentum (native) | -38.1 [-12.9; 0.00] | -29.0 [-37.4; 0.00] | 0.2 [-4.0; 0.00] | -8.1 [1.3; 0.50] |
| pullback | -13.3 [-15.2; 0.50] | -9.2 [0.8; 0.50] | 12.3 [-16.1; 0.00] | -4.6 [19.9; 1.00] |
| pullback (native) | -3.0 [6.2; 1.00] | -0.1 [10.1; 1.00] | -2.2 [31.5; 1.00] | -39.7 [-24.6; 0.00] |
| structure | -18.1 [-18.4; 0.00] | -18.0 [-27.5; 0.00] | -32.3 [-21.6; 0.00] | -20.1 [10.7; 0.50] |
| structure (native) | -10.7 [-26.9; 0.00] | -19.7 [-4.1; 0.00] | -2.2 [4.4; 0.50] | -33.3 [-29.7; 0.00] |
| tape | 2.8 [3.4; 0.50] | -17.3 [2.5; 1.00] | -19.7 [-14.4; 0.50] | -14.9 [1.4; 0.50] |
| tape (native) | -21.7 [-34.6; 0.00] | -18.3 [16.7; 1.00] | -12.3 [5.4; 0.50] | -38.4 [-21.5; 0.00] |
| trend | -16.2 [-19.2; 0.00] | -16.7 [14.7; 0.50] | -14.8 [-7.6; 0.00] | 9.0 [35.7; 1.00] |
| trend (native) | -13.2 [-7.4; 0.50] | -8.8 [-6.5; 0.00] | -25.4 [-12.4; 0.50] | -7.2 [-8.9; 0.50] |
| xmarket | -5.1 [-25.5; 0.00] | -23.0 [-19.2; 0.00] | 10.9 [19.7; 1.00] | -8.9 [-7.1; 0.50] |
### PASS 1: 10 best family cells in London (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| levels|PRICE | 27.9 | 0.021 | 179.9 | 0.69 | 16.2 | 15.6 | {"2023": 13.5, "2024": 24.4, "2025": 47.4, "2026": 13.8} | -14.6 | 42.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| book (native)|ACTIVITY | 15.0 | 0.016 | 366.1 | 0.58 | -53.6 | 74.2 | {"2023": 10.6, "2024": 32.9, "2025": 3.8, "2026": 8.7} | 2.6 | 12.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|INFORMATION | 14.9 | 0.024 | 304.8 | 0.57 | -26.0 | -60.3 | {"2023": -15.5, "2024": 56.6, "2025": 6.1, "2026": -14.5} | -8.6 | 23.4 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| confluence|TIME | 14.7 | 0.017 | 190.5 | 0.53 | 40.3 | -23.0 | {"2023": -4.8, "2024": 9.5, "2025": 13.4, "2026": 28.7} | -3.4 | 18.2 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|PRICE | 13.0 | 0.015 | 481.6 | 0.53 | 36.7 | 83.2 | {"2023": 38.9, "2024": 13.1, "2025": -11.4, "2026": 33.5} | -0.9 | 13.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} |
| pullback|PRICE | 12.3 | 0.009 | 602.4 | 0.53 | 81.9 | 115.9 | {"2023": -7.2, "2024": -6.8, "2025": 16.2, "2026": 36.4} | 28.4 | -16.1 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| xmarket|PRICE | 10.9 | 0.013 | 245.4 | 0.52 | 47.7 | 111.1 | {"2023": 10.3, "2024": -6.2, "2025": 11.3, "2026": 31.0} | -8.8 | 19.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| book (native)|PRICE | 10.2 | 0.007 | 375.5 | 0.53 | 14.2 | -170.5 | {"2023": -11.4, "2024": 7.1, "2025": -7.7, "2026": 42.0} | -10.3 | 20.5 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| trend|TIME | 9.0 | 0.015 | 622.2 | 0.53 | -100.9 | 41.0 | {"2023": 6.9, "2024": 23.5, "2025": 30.1, "2026": -32.6} | -26.7 | 35.7 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual (native)|ACTIVITY | 6.7 | -0.003 | 738.7 | 0.47 | 25.1 | -48.1 | {"2023": -8.8, "2024": 31.5, "2025": -34.0, "2026": 30.3} | -4.0 | 10.7 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
Live books in London on their live bars (same screen, plain 60/60): K7 tm180 L6M -52.7 pts/wk, rank 5% (top 95.2%); M7 tm60 L6M -39.6 pts/wk, rank 9% (top 91.2%); U7 tm600 L6M -10.7 pts/wk, rank 32% (top 67.5%); P7 tm60 L6M 65.6 pts/wk, rank 99% (top 1.2%); H7 tm60 L6M 2.9 pts/wk, rank 62% (top 37.9%); A7 tm60 L6M 14.3 pts/wk, rank 79% (top 20.6%). Rank = share of ALL London cells with a lower trailing-26w result.

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
| 12 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | asym15u/30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 812.0, "2024": 1425.0, "2025": 18.0, "2026": 5170.0} |
| 13 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym30u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 766.0, "2024": 1526.0, "2025": 18.0, "2026": 5170.0} |
| 14 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | 5 / -476 / 2360 / 1.00 | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 15 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym30u | both | 5528 | 2119 | 220 | 1.00 | 5 / -257 / 968 / 1.00 | {"2023": 677.0, "2024": -476.0, "2025": -2538.0, "2026": 6998.0} |
| 16 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | asym10u/20u | both | 5527 | 1802 | 260 | 1.00 | 5 / -84 / 712 / 1.00 | {"2023": 418.0, "2024": -2082.0, "2025": -1357.0, "2026": 6422.0} |
| 17 | dol_350 | tape.tape_stack.r3_fade | {"k": 4} | plain60/60 | both | 5522 | 2823 | 774 | 1.00 | 2 / 851 / 1568 / 1.00 | {"2023": -500.0, "2024": -689.0, "2025": -1649.0, "2026": 5281.0} |
| 18 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | 5 / -350 / 2382 / 1.00 | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 19 | swing_atr_0.1 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -469 / 2733 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |
| 20 | swing_atr_0.1 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym15u | both | 5481 | 2602 | 245 | 1.00 | 5 / -397 / 391 / 1.00 | {"2023": 1023.0, "2024": -654.0, "2025": 962.0, "2026": 5336.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 42.7 | 0.027 | 334.7 | 0.59 | 60.5 | 91.3 | -30.3 | -26.6 | 73.0 | 1.00 | 0.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 43.8 | 0.029 | 307.8 | 0.59 | 46.8 | 91.3 | -17.6 | -14.0 | 61.4 | 1.00 | -1.2 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 29.3 [17.5; 1.00] | 1.6 [-8.7; 0.50] | 15.3 [9.0; 0.50] | 30.1 [21.2; 1.00] |
| bands (native) | 3.2 [-0.2; 0.50] | 1.9 [3.6; 0.50] | 23.7 [55.6; 1.00] | 30.0 [65.6; 1.00] |
| barnative | -20.5 [2.3; 0.50] | -25.9 [-38.4; 0.00] | 44.8 [90.5; 1.00] | 11.1 [-13.6; 0.00] |
| book | 31.4 [28.1; 1.00] | -1.0 [-14.7; 0.00] | -6.0 [28.9; 1.00] | n/a (no signals by construction) |
| book (native) | 7.5 [39.5; 1.00] | 5.0 [14.9; 1.00] | 14.0 [11.0; 0.50] | n/a (no signals by construction) |
| confluence | 13.7 [24.3; 1.00] | -6.4 [12.1; 1.00] | 41.9 [38.1; 1.00] | 1.9 [1.9; 0.50] |
| levels | 3.8 [29.6; 1.00] | -25.5 [23.7; 1.00] | 3.3 [31.6; 1.00] | -1.3 [-22.3; 0.50] |
| levels (native) | 23.8 [37.9; 1.00] | 16.0 [46.7; 1.00] | 10.1 [42.0; 1.00] | -9.2 [6.7; 0.50] |
| live | 14.6 [20.3; 0.50] | 4.6 [21.5; 1.00] | 8.2 [-10.6; 0.00] | -10.3 [-5.0; 0.50] |
| manual | 29.8 [47.8; 1.00] | 40.1 [107.8; 1.00] | -14.9 [-31.6; 0.00] | 33.3 [37.0; 1.00] |
| manual (native) | -66.0 [-59.9; 0.00] | -58.7 [-74.4; 0.00] | -22.8 [-36.3; 0.00] | -16.6 [1.6; 0.50] |
| momentum | 23.2 [4.1; 0.50] | 8.4 [16.8; 0.50] | -2.7 [-30.7; 0.00] | 39.8 [27.0; 1.00] |
| momentum (native) | -2.9 [3.2; 1.00] | 4.0 [12.8; 1.00] | 41.8 [49.8; 1.00] | 36.0 [48.2; 1.00] |
| pullback | 23.8 [51.4; 1.00] | 22.6 [52.0; 1.00] | -13.7 [24.4; 1.00] | -1.4 [11.6; 1.00] |
| pullback (native) | 24.5 [57.4; 1.00] | -4.6 [4.2; 0.50] | -2.7 [31.5; 1.00] | -18.9 [5.1; 0.50] |
| structure | 12.2 [8.0; 1.00] | -6.3 [7.7; 1.00] | 26.5 [56.4; 1.00] | -0.9 [24.2; 0.50] |
| structure (native) | 36.8 [65.2; 1.00] | 40.8 [53.6; 1.00] | 2.9 [-3.4; 0.50] | 38.2 [42.6; 1.00] |
| tape | 23.7 [-0.2; 0.50] | -37.2 [-38.0; 0.00] | 7.1 [-1.5; 0.50] | 22.6 [27.1; 1.00] |
| tape (native) | 17.2 [20.1; 1.00] | -24.2 [-41.2; 0.00] | 4.7 [16.4; 0.50] | 0.3 [-12.4; 0.00] |
| trend | -24.8 [-27.2; 0.00] | -6.0 [4.9; 0.50] | -2.6 [9.9; 1.00] | -4.5 [18.6; 1.00] |
| trend (native) | -57.9 [-62.8; 0.00] | -21.9 [14.4; 1.00] | 15.8 [33.9; 1.00] | -23.4 [-11.6; 0.50] |
| xmarket | -16.2 [-4.2; 0.50] | -24.9 [-17.8; 0.50] | 11.2 [15.9; 1.00] | -19.2 [-19.1; 0.50] |
### PASS 1: 10 best family cells in NYAM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|PRICE | 44.8 | 0.018 | 563.7 | 0.58 | 45.9 | -36.9 | {"2023": -29.3, "2024": -23.3, "2025": 104.9, "2026": 77.7} | -45.7 | 90.5 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| confluence|PRICE | 41.9 | 0.027 | 387.9 | 0.54 | 58.2 | -121.7 | {"2023": 89.5, "2024": -14.0, "2025": 63.5, "2026": 67.4} | 3.8 | 38.1 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 41.8 | 0.024 | 532.0 | 0.56 | -6.9 | 4.4 | {"2023": -10.0, "2024": -11.1, "2025": 87.9, "2026": 66.1} | -8.0 | 49.8 | 1.00 | {"2023": "AMBER", "2024": "AMBER", "2025": "ok", "2026": "ok"} |
| structure (native)|INFORMATION | 40.8 | 0.026 | 575.2 | 0.59 | 66.4 | 44.7 | {"2023": 56.8, "2024": 0.4, "2025": 94.7, "2026": 19.6} | -12.8 | 53.6 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|INFORMATION | 40.1 | 0.025 | 425.4 | 0.59 | 73.0 | -52.6 | {"2023": 5.5, "2024": 3.9, "2025": 75.2, "2026": 52.5} | -67.6 | 107.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 39.8 | 0.023 | 654.3 | 0.57 | 96.6 | 167.5 | {"2023": 22.0, "2024": 70.5, "2025": 52.6, "2026": -6.1} | 12.8 | 27.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure (native)|TIME | 38.2 | 0.025 | 551.9 | 0.59 | 92.4 | 185.9 | {"2023": -14.3, "2024": 13.7, "2025": 59.5, "2026": 58.8} | -4.4 | 42.6 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|ACTIVITY | 36.8 | 0.024 | 824.1 | 0.60 | -16.6 | 60.5 | {"2023": 51.5, "2024": 23.8, "2025": 94.6, "2026": -20.9} | -28.5 | 65.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum (native)|TIME | 36.0 | 0.023 | 864.9 | 0.54 | 71.5 | 198.2 | {"2023": 22.0, "2024": 86.3, "2025": 52.6, "2026": -38.6} | -12.1 | 48.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 33.3 | 0.018 | 623.4 | 0.58 | 27.7 | 281.0 | {"2023": 8.9, "2024": 19.4, "2025": 44.7, "2026": 43.9} | -3.7 | 37.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in NYAM on their live bars (same screen, plain 60/60): K7 tm180 L6M -75.5 pts/wk, rank 6% (top 94.0%); M7 tm60 L6M -8.9 pts/wk, rank 43% (top 56.5%); U7 tm600 L6M -11.4 pts/wk, rank 40% (top 59.6%); P7 tm60 L6M -60.7 pts/wk, rank 10% (top 90.4%); H7 tm60 L6M 28.8 pts/wk, rank 86% (top 13.7%); A7 tm60 L6M -17.2 pts/wk, rank 34% (top 65.6%); O7 tm60 L6M 15.1 pts/wk, rank 77% (top 22.9%). Rank = share of ALL NYAM cells with a lower trailing-26w result.

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
| free | -29.8 | -0.015 | 2010.6 | 0.43 | 44.8 | 69.9 | -1.4 | 10.2 | -28.4 | 0.00 | 7.0 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | -21.3 | -0.010 | 1723.4 | 0.47 | 44.8 | 69.9 | -11.7 | -0.6 | -9.6 | 0.50 | 11.7 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -15.3 [-10.9; 0.50] | 3.1 [16.0; 1.00] | 19.9 [45.2; 1.00] | -19.9 [-8.1; 0.50] |
| bands (native) | 22.6 [22.5; 1.00] | 2.3 [-20.7; 0.00] | -6.9 [27.3; 1.00] | -24.5 [-37.2; 0.00] |
| barnative | -27.0 [-39.7; 0.00] | -6.5 [4.8; 0.50] | -2.8 [10.8; 1.00] | -19.2 [-53.6; 0.00] |
| book | -11.6 [-37.7; 0.00] | 5.7 [25.7; 1.00] | 13.5 [-8.5; 0.50] | n/a (no signals by construction) |
| book (native) | -17.0 [-1.4; 0.50] | 18.8 [19.6; 1.00] | -5.0 [-2.6; 0.50] | n/a (no signals by construction) |
| confluence | -5.5 [-22.1; 0.50] | 4.6 [-17.5; 0.00] | -34.9 [-12.1; 0.00] | -18.3 [-35.4; 0.00] |
| levels | -1.2 [-13.3; 0.00] | -40.4 [-33.3; 0.00] | -31.6 [-27.6; 0.50] | 9.4 [25.3; 1.00] |
| levels (native) | -10.6 [15.4; 1.00] | -11.8 [-12.0; 0.00] | -28.4 [-13.4; 0.50] | -31.2 [-5.8; 0.50] |
| live | -22.8 [7.2; 0.50] | -33.5 [-16.7; 0.50] | -18.1 [-44.0; 0.00] | -16.8 [-48.1; 0.00] |
| manual | -19.7 [-55.2; 0.00] | -27.7 [-19.1; 0.00] | 6.9 [6.1; 1.00] | -12.8 [-12.1; 0.50] |
| manual (native) | 25.7 [38.7; 1.00] | 7.4 [16.1; 0.50] | 17.9 [-9.4; 0.50] | -32.2 [-14.9; 0.50] |
| momentum | -11.1 [-4.6; 0.50] | -11.6 [7.6; 0.50] | -0.6 [35.2; 1.00] | -2.0 [-5.5; 0.50] |
| momentum (native) | 17.4 [24.9; 0.50] | -41.6 [-36.6; 0.00] | 16.5 [26.5; 1.00] | -9.9 [-5.2; 0.50] |
| pullback | -24.6 [-31.9; 0.00] | -6.7 [-20.6; 0.00] | -34.9 [-7.5; 0.00] | -10.2 [13.2; 1.00] |
| pullback (native) | -9.6 [9.4; 0.50] | -69.1 [-69.7; 0.00] | 0.8 [19.0; 1.00] | -20.2 [1.3; 0.50] |
| structure | 19.4 [21.1; 1.00] | -14.0 [14.7; 1.00] | -38.8 [-27.2; 0.00] | 22.5 [32.0; 1.00] |
| structure (native) | 5.2 [-15.3; 0.50] | -23.2 [-8.8; 0.50] | -25.2 [-6.8; 0.50] | 23.2 [40.9; 1.00] |
| tape | 19.3 [26.0; 1.00] | 31.5 [16.7; 1.00] | -13.2 [-15.9; 0.00] | -37.4 [-8.8; 0.00] |
| tape (native) | -2.3 [25.9; 1.00] | -23.1 [-22.5; 0.00] | 19.1 [30.3; 1.00] | -1.5 [0.4; 0.50] |
| trend | 5.0 [36.8; 1.00] | -5.7 [2.1; 0.50] | 15.9 [35.9; 1.00] | 17.8 [0.6; 0.50] |
| trend (native) | 35.7 [48.9; 1.00] | -10.3 [-28.9; 0.00] | -2.4 [2.8; 0.50] | 15.2 [32.7; 1.00] |
| xmarket | 14.2 [19.7; 1.00] | -26.9 [-34.2; 0.00] | 5.8 [-8.0; 0.50] | -16.5 [0.3; 0.50] |
### PASS 1: 10 best family cells in NYPM (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| trend (native)|ACTIVITY | 35.7 | 0.034 | 403.5 | 0.57 | 35.2 | 33.9 | {"2023": -11.0, "2024": 39.8, "2025": 64.3, "2026": 11.8} | -13.3 | 48.9 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|INFORMATION | 31.5 | 0.013 | 422.8 | 0.57 | -42.2 | 22.3 | {"2023": 54.3, "2024": -20.8, "2025": 95.6, "2026": 10.3} | 14.8 | 16.7 | 1.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual (native)|ACTIVITY | 25.7 | 0.031 | 366.0 | 0.54 | 48.5 | 6.0 | {"2023": -42.5, "2024": -13.5, "2025": 82.6, "2026": 26.6} | -13.0 | 38.7 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 23.2 | 0.022 | 469.8 | 0.58 | 40.4 | -3.8 | {"2023": 49.7, "2024": 5.8, "2025": -1.5, "2026": 64.7} | -17.6 | 40.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands (native)|ACTIVITY | 22.6 | 0.030 | 294.3 | 0.54 | 11.8 | -93.6 | {"2023": 25.8, "2024": 55.4, "2025": 27.5, "2026": -22.9} | 0.1 | 22.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|TIME | 22.5 | 0.020 | 875.2 | 0.57 | 127.0 | 175.4 | {"2023": -36.0, "2024": 18.3, "2025": -26.9, "2026": 104.6} | -9.5 | 32.0 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| bands|PRICE | 19.9 | 0.013 | 536.5 | 0.49 | -64.2 | -32.6 | {"2023": 75.2, "2024": 42.8, "2025": 44.5, "2026": -53.7} | -25.2 | 45.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| structure|ACTIVITY | 19.4 | 0.003 | 942.1 | 0.48 | 102.6 | 189.5 | {"2023": -19.1, "2024": -6.3, "2025": 2.1, "2026": 82.5} | -1.7 | 21.1 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| tape|ACTIVITY | 19.3 | 0.007 | 471.8 | 0.57 | -36.4 | 15.9 | {"2023": 37.6, "2024": 30.5, "2025": 2.3, "2026": 20.2} | -6.8 | 26.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape (native)|PRICE | 19.1 | 0.013 | 1001.2 | 0.48 | 111.9 | -74.3 | {"2023": -62.2, "2024": -41.5, "2025": 32.6, "2026": 100.5} | -11.2 | 30.3 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
Live books in NYPM on their live bars (same screen, plain 60/60): K7 tm180 L6M -22.5 pts/wk, rank 23% (top 77.3%); M7 tm60 L6M -36.8 pts/wk, rank 14% (top 86.0%); U7 tm600 L6M 4.8 pts/wk, rank 61% (top 39.0%); P7 tm60 L6M -35.9 pts/wk, rank 14% (top 85.6%); H7 tm60 L6M -20.1 pts/wk, rank 25% (top 75.4%); A7 tm60 L6M -32.5 pts/wk, rank 16% (top 83.8%). Rank = share of ALL NYPM cells with a lower trailing-26w result.

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
| 2 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym15u/30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 3 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym30u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 4 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 5 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym10u/20u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1046.0, "2024": -1508.0, "2025": 3102.0, "2026": 7745.0} |
| 6 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | asym20u/10u | both | 6729 | 2188 | 270 | 1.00 | 5 / 508 / 1497 / 1.00 | {"2023": -1266.0, "2024": -1067.0, "2025": 3095.0, "2026": 7745.0} |
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
| 19 | dol_500 | book.book_ofi.follow_sm | {"L": 50, "z": 1.0, "sm": 3} | sym15u | both | 5943 | 1567 | 355 | 0.50 | 2 / 1986 / 2893 / 1.00 | {"2023": -1221.0, "2024": 1479.0, "2025": 917.0, "2026": 4277.0} |
| 20 | cusum_28 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym8u | both | 5937 | 1863 | 338 | 1.00 | 5 / 380 / 2239 / 1.00 | {"2023": -46.0, "2024": -2789.0, "2025": 246.0, "2026": 7789.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -7.6 | -0.005 | 852.4 | 0.51 | -24.4 | -82.2 | -12.1 | -3.9 | 4.5 | 0.50 | -1.9 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -5.7 | -0.003 | 743.5 | 0.52 | -24.4 | -82.2 | 6.8 | 9.0 | -12.5 | 0.00 | -1.4 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 9.1 [14.1; 1.00] | 26.9 [9.6; 0.50] | 30.1 [47.9; 1.00] | 9.7 [9.5; 1.00] |
| bands (native) | 12.0 [11.0; 1.00] | 4.1 [-4.1; 0.50] | 23.2 [26.5; 1.00] | 8.7 [13.6; 1.00] |
| barnative | 12.7 [31.9; 1.00] | 1.0 [-14.7; 0.00] | -7.6 [3.1; 0.50] | -21.6 [-9.8; 0.50] |
| book | -12.4 [-11.0; 0.00] | n/a (no signals by construction) | -35.7 [-26.1; 0.00] | n/a (no signals by construction) |
| book (native) | 6.0 [23.6; 1.00] | n/a (no signals by construction) | 17.5 [31.1; 1.00] | n/a (no signals by construction) |
| confluence | 6.0 [6.4; 1.00] | -14.7 [-16.1; 0.00] | 16.7 [20.4; 1.00] | -25.6 [-11.7; 0.50] |
| levels | 0.1 [10.9; 0.50] | -3.4 [8.3; 0.50] | 13.3 [28.0; 1.00] | -4.0 [13.3; 1.00] |
| levels (native) | 30.1 [63.2; 1.00] | 30.8 [60.8; 1.00] | -2.7 [-10.6; 0.50] | 11.0 [22.9; 1.00] |
| live | 14.4 [36.8; 1.00] | -4.1 [14.9; 1.00] | -1.9 [8.4; 1.00] | 11.7 [20.3; 1.00] |
| manual | 5.7 [6.8; 1.00] | 3.5 [7.9; 0.50] | 7.8 [25.6; 1.00] | -36.0 [-18.8; 0.50] |
| manual (native) | -2.3 [8.6; 1.00] | -24.2 [-14.6; 0.00] | 0.6 [4.4; 0.50] | 10.8 [20.5; 1.00] |
| momentum | 12.6 [16.8; 1.00] | 6.0 [6.6; 1.00] | 4.8 [1.9; 0.50] | -3.1 [10.9; 1.00] |
| momentum (native) | -6.6 [-9.2; 0.00] | 17.8 [18.1; 1.00] | 24.8 [21.8; 1.00] | -1.5 [-24.1; 0.00] |
| pullback | 19.2 [28.6; 1.00] | 34.2 [42.8; 1.00] | -17.4 [4.4; 1.00] | -4.4 [-2.0; 0.50] |
| pullback (native) | 26.4 [39.0; 1.00] | -1.1 [-1.8; 0.50] | 11.5 [27.3; 1.00] | -8.8 [15.7; 1.00] |
| structure | -8.7 [-21.9; 0.00] | 31.3 [31.2; 1.00] | 4.6 [10.9; 1.00] | 2.3 [12.3; 1.00] |
| structure (native) | -10.2 [-4.4; 0.50] | -4.8 [-17.0; 0.50] | 14.6 [20.0; 1.00] | -10.3 [-4.1; 0.50] |
| tape | -11.7 [-38.3; 0.00] | -3.1 [13.9; 0.50] | -30.9 [-12.3; 0.50] | 20.5 [30.3; 1.00] |
| tape (native) | -0.8 [6.2; 0.50] | -22.4 [-11.2; 0.00] | -2.9 [38.9; 1.00] | 0.4 [-8.6; 0.00] |
| trend | 7.1 [23.7; 1.00] | 4.4 [0.7; 0.50] | 0.6 [18.6; 0.50] | 6.9 [14.4; 1.00] |
| trend (native) | -6.1 [1.3; 0.50] | 6.6 [25.4; 1.00] | -21.7 [-12.4; 0.00] | -20.7 [-28.8; 0.00] |
| xmarket | -6.7 [3.8; 0.50] | -33.7 [-25.1; 0.00] | -20.6 [-28.4; 0.00] | 0.1 [-6.5; 0.50] |
### PASS 1: 10 best family cells in Asia (trigger family x bar family; neighbour-agreed rolling pick, out of sample, pts/week per lot)
| family cell | OOS pts/wk | R/trade | ulcer | persistence | L6M | L3M | by year (pts/wk) | null mean | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pullback|INFORMATION | 34.2 | 0.031 | 142.3 | 0.62 | 63.5 | 9.4 | {"2023": 37.4, "2024": 19.8, "2025": 36.0, "2026": 48.2} | -8.5 | 42.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|INFORMATION | 31.3 | 0.030 | 203.6 | 0.56 | 106.7 | 56.1 | {"2023": 34.0, "2024": 11.4, "2025": 17.9, "2026": 70.0} | 0.2 | 31.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|INFORMATION | 30.8 | 0.043 | 271.5 | 0.62 | 121.5 | 146.8 | {"2023": 36.1, "2024": 26.9, "2025": 5.2, "2026": 63.9} | -30.0 | 60.8 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|PRICE | 30.1 | 0.032 | 203.9 | 0.58 | 48.8 | 11.8 | {"2023": 18.9, "2024": 8.9, "2025": 64.5, "2026": 18.2} | -17.8 | 47.9 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| levels (native)|ACTIVITY | 30.1 | 0.038 | 132.3 | 0.57 | 95.3 | 161.8 | {"2023": 18.2, "2024": 20.1, "2025": 15.9, "2026": 62.4} | -33.1 | 63.2 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| bands|INFORMATION | 26.9 | 0.037 | 230.9 | 0.58 | 29.0 | -53.9 | {"2023": 16.8, "2024": 15.0, "2025": 32.5, "2026": 37.5} | 17.3 | 9.6 | 0.50 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|ACTIVITY | 26.4 | 0.021 | 182.0 | 0.62 | -13.7 | -6.4 | {"2023": 38.4, "2024": 21.5, "2025": 37.3, "2026": 15.6} | -12.5 | 39.0 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum (native)|PRICE | 24.8 | 0.026 | 374.1 | 0.53 | 9.1 | -128.0 | {"2023": -15.0, "2024": -7.7, "2025": 61.3, "2026": 32.7} | 3.0 | 21.8 | 1.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| bands (native)|PRICE | 23.2 | 0.025 | 201.4 | 0.56 | -43.1 | -45.2 | {"2023": 0.0, "2024": 15.6, "2025": 57.7, "2026": -1.2} | -3.3 | 26.5 | 1.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| tape|TIME | 20.5 | 0.014 | 391.8 | 0.51 | 49.3 | -7.6 | {"2023": -12.4, "2024": 14.6, "2025": 38.4, "2026": 16.9} | -9.8 | 30.3 | 1.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
Live books in Asia on their live bars (same screen, plain 60/60): K7 tm180 L6M 72.1 pts/wk, rank 98% (top 1.8%); M7 tm60 L6M 80.8 pts/wk, rank 99% (top 1.2%); U7 tm600 L6M 35.4 pts/wk, rank 90% (top 9.6%); P7 tm60 L6M 66.1 pts/wk, rank 98% (top 2.4%); H7 tm60 L6M 25.1 pts/wk, rank 85% (top 15.3%); A7 tm60 L6M 6.5 pts/wk, rank 66% (top 34.5%). Rank = share of ALL Asia cells with a lower trailing-26w result.

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
| 14 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym10u/20u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -114.0, "2024": -2478.0, "2025": 2600.0, "2026": 5184.0} |
| 15 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 16 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym15u/30u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -122.0, "2024": -2373.0, "2025": 2657.0, "2026": 5184.0} |
| 17 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | asym20u/10u | both | 5982 | 1769 | 272 | 0.50 | 5 / -1155 / -237 / 1.00 | {"2023": -136.0, "2024": -2419.0, "2025": 3110.0, "2026": 5184.0} |
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
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.63 |  |
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
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.17 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.61 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.32 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.68 |  |
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
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.58 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell vsess_600 trend.trend_ma_hma.cross sym8u L6M 235.4 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell pnf_5 book.book_cancel.ratio_follow sym15u L6M 334.8 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell dib_2000 barnative.barnative_speed.burst_fade plain60/60 L6M 269.0 pts/wk vs weak baselines K7 -22.5
## LEVEL triggers per session (supply/demand first, then Fibonacci, pivots, swing S/R, level stack, others): best cell per (module, variant) over all bar rows / parameters / brackets, last 26 weeks, >= 30 trades, in-sample pick: a LEAD needs the candidates-table nulls
### London (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 17 | -252 | -206 | -351 | 1 | 41 |
| sd5 | break_native | pnf_20 | {"n": 1, "F": 0} | plain60/60 / both | 30 | -156 | 52 | -252 | -206 | -351 | 1 | 41 |
| sd5 | reject | vrb_700 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / long | 32 | 619 | -187 | -147 | -283 | 567 | 1 | 41 |
| sd5 | reject_native | vrb_700 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / long | 32 | 619 | -187 | -147 | -283 | 567 | 1 | 41 |
| sdx15 | break | kagi_80 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 140 | 2579 | 645 | -535 | -454 | 2325 | 1 | 41 |
| sdx15 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 195 | 2214 | 105 | -102 | 862 | 1176 | 1 | 41 |
| sdx15 | lim_prox | kagi_112 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 156 | 1722 | -776 | 900 | -2080 | 1504 | 1 | 41 |
| sdx15 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 386 | 1867 | 1258 | 1001 | 193 | 1192 | 1 | 41 |
| sdx15 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / both | 200 | 1025 | 1001 | -160 | -409 | -111 | 1 | 41 |
| sdx15 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 41 |
| sdx15 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 460 | 2407 | 914 | -42 | -1257 | 1411 | 1 | 41 |
| sdx15 | retest | kagi_80 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 73 | 1895 | -252 | -737 | -146 | 1593 | 1 | 41 |
| sdx3 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 3088 | -168 | 318 | -923 | 2963 | 1 | 41 |
| sdx3 | lim_mid | kagi_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 276 | 3690 | 400 | 1269 | -2651 | 4082 | 1 | 41 |
| sdx3 | lim_prox | urenko_10 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 358 | 4320 | 49 | 1608 | -1461 | 3654 | 1 | 41 |
| sdx3 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 238 | 2142 | 2164 | 1162 | -922 | 2240 | 1 | 41 |
| sdx3 | rej_flow | wrenko_20 | {"d": "B", "F": 9} | sym15u / both | 71 | 1238 | -32 | -410 | -333 | 1105 | 1 | 41 |
| sdx3 | rej_native | kagi_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 245 | 3620 | 859 | 1354 | 441 | 3653 | 1 | 41 |
| sdx3 | rej_zone | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 219 | 3956 | 1228 | 1976 | -779 | 5574 | 1 | 41 |
| sdx3 | retest | mrenko_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 195 | 1881 | -279 | 106 | 782 | 2331 | 1 | 41 |
| sdx30 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 75 | 1445 | 411 | -743 | -552 | 1630 | 1 | 41 |
| sdx30 | lim_mid | kagi_56 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 112 | 1852 | -92 | 580 | -256 | 1934 | 1 | 41 |
| sdx30 | lim_prox | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 228 | 3089 | -6 | 17 | 1634 | 3464 | 1 | 41 |
| sdx30 | rej | frenko_28 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 35 | 712 | -95 | -341 | 622 | -109 | 1 | 41 |
| sdx30 | rej_flow | wrenko_14 | {"d": "A", "F": 0} | sym15u / both | 31 | 633 | -473 | 306 | 239 | 176 | 1 | 41 |
| sdx30 | rej_native | kagi_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / long | 51 | 1413 | 260 | -189 | -77 | 1398 | 1 | 41 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 64 | 1016 | -341 | 208 | 498 | 718 | 1 | 41 |
| sdx30 | retest | pnf_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 30 | 570 | 110 | -6 | 144 | 250 | 1 | 41 |
| sdx5 | break | urenko_14 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 179 | 3068 | 197 | 1069 | 1759 | 2498 | 1 | 41 |
| sdx5 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 214 | 2364 | 118 | 1141 | -997 | 2486 | 1 | 41 |
| sdx5 | lim_prox | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 572 | 2492 | -318 | -767 | 467 | 2734 | 1 | 41 |
| sdx5 | rej | vrb_700 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 216 | 2671 | -193 | -1603 | 1240 | 2253 | 1 | 41 |
| sdx5 | rej_flow | vrb_700 | {"d": "B", "F": 9} | plain60/60 / both | 83 | 1379 | -251 | -555 | 1072 | 759 | 1 | 41 |
| sdx5 | rej_native | frenko_40 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 155 | 2126 | -203 | -436 | 139 | 981 | 1 | 41 |
| sdx5 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 102 | 1959 | 163 | 674 | -953 | 2077 | 1 | 41 |
| sdx5 | retest | kagi_20 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 156 | 3004 | -581 | -1198 | -562 | 1728 | 1 | 41 |
| sdx60 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 31 | 1222 | -351 | -320 | 116 | 1749 | 1 | 41 |
| sdx60 | lim_mid | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 162 | 2417 | -215 | 125 | -1666 | 2534 | 1 | 41 |
| sdx60 | lim_prox | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 3080 | 290 | 236 | -323 | 3089 | 1 | 41 |
| sdx60 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 32 | 1124 | -130 | -222 | -19 | 853 | 1 | 41 |
| sdx60 | rej_flow | dol_6000 | {"d": "E", "F": 9} | sym15u / both | 33 | 411 | -239 | -225 | -389 | 457 | 1 | 41 |
| sdx60 | rej_native | pnf_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 41 |
| sdx60 | rej_zone | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 66 | 2072 | -291 | 171 | -795 | 1823 | 1 | 41 |
| sdx_renko28 | break | kagi_112 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 144 | 2263 | -119 | -618 | -1891 | 1174 | 1 | 41 |
| sdx_renko28 | lim_mid | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 157 | 2991 | -88 | -812 | -829 | 2811 | 1 | 41 |
| sdx_renko28 | lim_prox | kagi_112 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 156 | 3623 | -359 | -657 | -693 | 3375 | 1 | 41 |
| sdx_renko28 | rej | mrenko_14 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 83 | 1095 | 778 | -472 | 371 | -403 | 1 | 41 |
| sdx_renko28 | rej_flow | dol_350 | {"d": "E", "F": 0} | plain60/60 / both | 137 | 639 | 351 | -677 | 1111 | 521 | 1 | 41 |
| sdx_renko28 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 41 |
| sdx_renko28 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 108 | 1940 | -28 | 921 | -908 | 1237 | 1 | 41 |
| sdx_renko28 | retest | pnf_5 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 85 | 1772 | -155 | -1444 | -732 | 1006 | 1 | 41 |
| sdx_rng28 | break | lbrk_3_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 233 | 3527 | 904 | -349 | 756 | 2289 | 1 | 41 |
| sdx_rng28 | lim_mid | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 261 | 3467 | -998 | 2482 | -838 | 2583 | 1 | 41 |
| sdx_rng28 | lim_prox | wrenko_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 281 | 2565 | -697 | 820 | 191 | 5046 | 1 | 41 |
| sdx_rng28 | rej | kagi_56 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 93 | 1361 | 603 | 353 | -205 | 971 | 1 | 41 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 0} | sym15u / both | 166 | 1446 | 811 | -32 | 1520 | 715 | 1 | 41 |
| sdx_rng28 | rej_native | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 41 |
| sdx_rng28 | rej_zone | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 362 | 2075 | -573 | -292 | 1394 | 3024 | 1 | 41 |
| sdx_rng28 | retest | pnf_7 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 235 | 2538 | 635 | -1058 | -796 | 2576 | 1 | 41 |
| sdx_vol1100 | break | frenko_28 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 197 | 2638 | -348 | -213 | 189 | 2953 | 1 | 41 |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 209 | 3784 | 896 | 457 | 888 | 4785 | 1 | 41 |
| sdx_vol1100 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 244 | 3123 | 198 | -474 | 859 | 3530 | 1 | 41 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 285 | 1551 | -175 | 755 | -1556 | 357 | 1 | 41 |
| sdx_vol1100 | rej_flow | dol_350 | {"d": "E", "F": 0} | sym15u / short | 67 | 1136 | -141 | -656 | 353 | 1458 | 1 | 41 |
| sdx_vol1100 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 41 |
| sdx_vol1100 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 190 | 2477 | 1072 | -510 | -2133 | 1187 | 1 | 41 |
| sdx_vol1100 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 112 | 1778 | -246 | -234 | -609 | 1473 | 1 | 41 |
| fib15 | break | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 249 | 3282 | -364 | -1291 | 590 | 4632 | 1 | 41 |
| fib15 | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 164 | 2716 | -400 | -119 | -1799 | 2918 | 1 | 41 |
| fib15 | false_break | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 243 | 4142 | 430 | 262 | -578 | 3255 | 1 | 41 |
| fib15 | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | sym15u / both | 243 | 3974 | 399 | 289 | -884 | 3402 | 1 | 41 |
| fib15 | pullback | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 194 | 1410 | -108 | -107 | -1066 | 1100 | 1 | 41 |
| fib15 | pullback_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 199 | 2553 | -505 | -2114 | -1143 | 2766 | 1 | 41 |
| fib15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 525 | 3712 | -473 | -683 | 2041 | 4718 | 1 | 41 |
| fib15 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3703 | -555 | 839 | 2164 | 4988 | 1 | 41 |
| fib15 | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 203 | 3012 | -328 | 676 | -1536 | 4669 | 1 | 41 |
| fib15 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 210 | 2792 | 329 | 815 | -1874 | 3907 | 1 | 41 |
| fib5 | break | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 209 | 2478 | 923 | 588 | -748 | 3301 | 1 | 41 |
| fib5 | break_native | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 2474 | 665 | -63 | 652 | 2753 | 1 | 41 |
| fib5 | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 215 | 3383 | 715 | 310 | -1361 | 3415 | 1 | 41 |
| fib5 | false_break_native | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 214 | 3196 | 963 | 251 | -520 | 2826 | 1 | 41 |
| fib5 | pullback | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 194 | 1590 | 1243 | 113 | 223 | 1728 | 1 | 41 |
| fib5 | pullback_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 1176 | -372 | 177 | 1730 | 655 | 1 | 41 |
| fib5 | reject | urenko_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 243 | 2344 | 186 | -2299 | -368 | 3117 | 1 | 41 |
| fib5 | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 265 | 2146 | 246 | -1025 | 366 | 781 | 1 | 41 |
| fib5 | retest | urenko_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 525 | 2243 | 323 | 944 | -1709 | 1936 | 1 | 41 |
| fib5 | retest_native | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 207 | 3002 | 919 | 626 | -2031 | 4002 | 1 | 41 |
| fib60 | break | lbrk_3_10 | {"n": 3, "k": 0.5} | plain60/60 / both | 430 | 2830 | 528 | -2082 | 186 | 1880 | 1 | 41 |
| fib60 | break_native | lbrk_3_10 | {"n": 3, "k": 0.5} | plain60/60 / both | 436 | 2648 | 1046 | -1546 | -110 | 1502 | 1 | 41 |
| fib60 | false_break | kagi_14 | {"M": 2, "k": 0.5} | sym15u / both | 210 | 2654 | 1181 | 1317 | -829 | 2273 | 1 | 41 |
| fib60 | false_break_native | kagi_14 | {"M": 2, "k": 0.5} | sym15u / both | 209 | 2749 | 1588 | 1316 | -68 | 2351 | 1 | 41 |
| fib60 | pullback | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 1205 | -627 | -79 | -654 | -548 | 1 | 41 |
| fib60 | pullback_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 102 | 1231 | -694 | 107 | -2246 | 1353 | 1 | 41 |
| fib60 | reject | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 107 | 2314 | -527 | -402 | -2571 | 2192 | 1 | 41 |
| fib60 | reject_native | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 178 | 2299 | -228 | -443 | -3051 | 2199 | 1 | 41 |
| fib60 | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 3143 | 228 | 413 | -1867 | 3391 | 1 | 41 |
| fib60 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 3612 | -726 | 592 | -710 | 4771 | 1 | 41 |
| fibr_dev | break | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 41 |
| fibr_dev | break_native | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 671 | 2661 | -156 | 1064 | -57 | 1842 | 1 | 41 |
| fibr_dev | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 180 | 1774 | 127 | -330 | -1672 | 2055 | 1 | 41 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 640 | 2530 | -963 | -884 | -3116 | 2367 | 1 | 41 |
| fibr_dev | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 256 | 3197 | 564 | -144 | -10 | 1750 | 1 | 41 |
| fibr_dev | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 685 | 2174 | -110 | -1858 | -2517 | -951 | 1 | 41 |
| fibr_dev | retest | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 622 | 2751 | 131 | -652 | -1202 | 838 | 1 | 41 |
| fibr_dev | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 212 | 2228 | -96 | -768 | -515 | 2316 | 1 | 41 |
| fibr_pd | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 211 | 2784 | 1325 | -554 | -802 | 3958 | 1 | 41 |
| fibr_pd | break_native | pnf_5 | {"n": 2, "k": 0.25} | sym15u / both | 207 | 3135 | 51 | 239 | -950 | 2891 | 1 | 41 |
| fibr_pd | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 176 | 1922 | -666 | -75 | -1 | 2455 | 1 | 41 |
| fibr_pd | false_break_native | pnf_28 | {"M": 3, "k": 0.5} | sym15u / both | 174 | 1857 | -580 | 114 | -478 | 2515 | 1 | 41 |
| fibr_pd | reject | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 203 | 2146 | 523 | -1414 | -889 | 2858 | 1 | 41 |
| fibr_pd | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 237 | 3803 | 503 | 321 | -2364 | 2894 | 1 | 41 |
| fibr_pd | retest | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 155 | 2461 | 865 | 467 | -2371 | 816 | 1 | 41 |
| fibr_pd | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 202 | 2979 | -199 | -788 | -742 | 2241 | 1 | 41 |
| piv_cama | break | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -355 | -657 | -3166 | 2471 | 1 | 41 |
| piv_cama | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 167 | 2487 | -439 | -657 | -3166 | 2471 | 1 | 41 |
| piv_cama | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -589 | -486 | -3125 | 2453 | 1 | 41 |
| piv_cama | false_break_native | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 164 | 2442 | -536 | -486 | -3125 | 2453 | 1 | 41 |
| piv_cama | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 175 | 1882 | -418 | 222 | -1471 | 1356 | 1 | 41 |
| piv_cama | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 500 | 2839 | -84 | -1811 | 959 | 3224 | 1 | 41 |
| piv_cama | retest | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 41 |
| piv_cama | retest_native | kagi_40 | {"M": 3, "tol": 0.0} | sym15u / both | 201 | 3129 | -577 | 292 | 2082 | 1817 | 1 | 41 |
| piv_floor | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 41 |
| piv_floor | break_native | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 189 | 2773 | -876 | -2336 | -4004 | 1980 | 1 | 41 |
| piv_floor | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 41 |
| piv_floor | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 179 | 2587 | 226 | -1570 | -3011 | 2099 | 1 | 41 |
| piv_floor | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / long | 48 | 1156 | 133 | 855 | 1142 | 2067 | 1 | 41 |
| piv_floor | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 2321 | 417 | 1571 | -187 | 1903 | 1 | 41 |
| piv_floor | retest | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 41 |
| piv_floor | retest_native | kagi_14 | {"M": 3, "tol": 0.0} | sym15u / both | 169 | 3948 | 347 | -890 | -497 | 3361 | 1 | 41 |
| piv_wf | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 199 | 2656 | -333 | -1729 | -430 | 1511 | 1 | 41 |
| piv_wf | break_native | urenko_40 | {"n": 3, "k": 0.5} | sym15u / both | 202 | 2880 | -608 | -890 | -364 | 3606 | 1 | 41 |
| piv_wf | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 199 | 2887 | -211 | -1555 | -414 | 1976 | 1 | 41 |
| piv_wf | false_break_native | kagi_80 | {"M": 1, "k": 0.0} | sym15u / both | 199 | 2636 | -144 | -1563 | -448 | 1481 | 1 | 41 |
| piv_wf | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 147 | 1472 | 651 | 362 | -430 | 1487 | 1 | 41 |
| piv_wf | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 230 | 3435 | -674 | 1015 | -1014 | 4860 | 1 | 41 |
| piv_wf | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 174 | 2164 | -5 | -1635 | -1545 | 1610 | 1 | 41 |
| piv_wf | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3307 | -134 | -1185 | -1620 | 3176 | 1 | 41 |
| swcluster | break | kagi_56 | {"n": 2, "k": 0.25} | sym15u / both | 50 | 1670 | -518 | -793 | -14 | 465 | 1 | 41 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1656 | -586 | -594 | -193 | 450 | 1 | 41 |
| swcluster | false_break | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 74 | 1459 | -140 | -948 | 37 | 490 | 1 | 41 |
| swcluster | false_break_native | kagi_80 | {"M": 3, "k": 0.5} | sym15u / both | 68 | 1438 | -192 | -927 | 429 | 1017 | 1 | 41 |
| swcluster | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | -808 | 524 | -708 | 198 | 1 | 41 |
| swcluster | reject_native | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 53 | 1389 | 5 | -698 | -300 | 1666 | 1 | 41 |
| swcluster | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 72 | 1227 | -296 | 686 | 80 | 817 | 1 | 41 |
| swcluster | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | plain60/60 / both | 117 | 1228 | 47 | -874 | -370 | 1269 | 1 | 41 |
| swsr15 | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 2311 | 223 | -327 | -8 | 3157 | 1 | 41 |
| swsr15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 247 | 2675 | -145 | -1131 | -495 | 2962 | 1 | 41 |
| swsr15 | false_break | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 170 | 1830 | -590 | -550 | -3102 | 2238 | 1 | 41 |
| swsr15 | false_break_native | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 92 | 1864 | -177 | 269 | -551 | 3234 | 1 | 41 |
| swsr15 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 241 | 2478 | 214 | -863 | -296 | 4375 | 1 | 41 |
| swsr15 | reject_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 234 | 2619 | -292 | -295 | -2422 | 1243 | 1 | 41 |
| swsr15 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 192 | 3116 | -742 | -538 | 263 | 2136 | 1 | 41 |
| swsr15 | retest_native | pnf_28 | {"M": 6, "tol": 0.5} | sym15u / both | 188 | 2587 | -36 | 852 | 31 | 1170 | 1 | 41 |
| swsr5 | break | kagi_80 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 1969 | -49 | 176 | -191 | 2616 | 1 | 41 |
| swsr5 | break_native | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 274 | 2084 | -669 | -1018 | 182 | 1811 | 1 | 41 |
| swsr5 | false_break | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 171 | 2538 | 48 | 76 | -1945 | 2966 | 1 | 41 |
| swsr5 | false_break_native | kagi_112 | {"M": 2, "k": 0.5} | sym15u / both | 168 | 2788 | 236 | -264 | -2437 | 2402 | 1 | 41 |
| swsr5 | reject | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 143 | 1638 | -293 | -1179 | -1318 | 1907 | 1 | 41 |
| swsr5 | reject_native | kagi_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 236 | 3237 | 265 | 1368 | 654 | 2042 | 1 | 41 |
| swsr5 | retest | mrenko_20 | {"M": 10, "tol": 0.5} | plain60/60 / both | 529 | 2659 | -716 | -995 | -709 | 3038 | 1 | 41 |
| swsr5 | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 268 | 2360 | 398 | -1263 | -1865 | 3266 | 1 | 41 |
| swsr60 | break | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 173 | 2714 | -1019 | -989 | 1889 | 3578 | 1 | 41 |
| swsr60 | break_native | kagi_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 287 | 2084 | -313 | -2637 | -700 | 2284 | 1 | 41 |
| swsr60 | false_break | pnf_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 182 | 1557 | -946 | -1881 | -885 | 915 | 1 | 41 |
| swsr60 | false_break_native | frenko_40 | {"M": 2, "k": 0.5} | sym15u / both | 169 | 1673 | 1094 | -445 | -324 | 3542 | 1 | 41 |
| swsr60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 171 | 2075 | -1036 | -2049 | -1412 | 1142 | 1 | 41 |
| swsr60 | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 193 | 2648 | -423 | -1524 | 1834 | 2876 | 1 | 41 |
| swsr60 | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 137 | 1667 | -201 | 137 | 1485 | 3122 | 1 | 41 |
| swsr60 | retest_native | pnf_14 | {"M": 6, "tol": 0.5} | sym15u / both | 166 | 2367 | -533 | -15 | -85 | 3016 | 1 | 41 |
| stack | break | kagi_20 | {"k": 3, "cw": 1.0} | sym15u / both | 148 | 3437 | 176 | 1393 | -17 | 1971 | 1 | 211 |
| stack | break_native | frenko_28 | {"k": 2, "cw": 0.5} | sym15u / both | 236 | 2805 | -674 | 49 | 2094 | 1768 | 1 | 211 |
| stack | reject | vsess_120 | {"k": 2, "cw": 0.5} | sym8u / both | 94 | 2473 | 270 | -72 | -962 | 2621 | 2 | 211 |
| stack | reject_native | pnf_14 | {"k": 2, "cw": 0.5} | sym15u / both | 194 | 3864 | -615 | -258 | -63 | 4021 | 1 | 211 |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 209 |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 59 | 1238 | -272 | -1504 | -9 | 988 | 1 | 209 |
| book_walls | false_break | swing_atr_0.1 | {"M": 1, "k": 0.0} | sym15u / both | 32 | 809 | 547 | -1665 | -90 | 1101 | 1 | 209 |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 56 | 1019 | -536 | -1198 | -714 | 848 | 1 | 209 |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1 | 209 |
| book_walls | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 55 | 1152 | 209 | -451 | 107 | 688 | 1 | 209 |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 46 | 978 | -549 | -37 | -855 | 476 | 1 | 209 |
| book_walls | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym15u / both | 31 | 948 | -230 | -711 | 334 | 598 | 1 | 209 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 197 | 2357 | -978 | -1528 | -3048 | 1807 | 2 | 211 |
| book_walls_loose | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 2309 | -1415 | 296 | -1880 | 2748 | 2 | 211 |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 211 |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1 | 211 |
| book_walls_loose | reject | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 170 | 3163 | -1118 | 31 | -1206 | 3714 | 1 | 211 |
| book_walls_loose | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 208 | 3375 | -1082 | -93 | -1302 | 3631 | 1 | 211 |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 3516 | 15 | -764 | -863 | 4040 | 1 | 211 |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1 | 211 |
| channel | break | urenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 253 | 3125 | -354 | -1559 | 474 | 4044 | 1 | 41 |
| channel | break_native | kagi_112 | {"n": 1, "k": 0.0} | sym15u / both | 173 | 2782 | -78 | -142 | -1977 | 2827 | 1 | 41 |
| channel | false_break | kagi_112 | {"M": 1, "k": 0.0} | sym15u / both | 172 | 2909 | -148 | -291 | -2237 | 2992 | 1 | 41 |
| channel | false_break_native | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 3344 | 373 | 1739 | 1102 | 4639 | 1 | 41 |
| channel | reject | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 118 | 2681 | 332 | 48 | -1806 | 2627 | 1 | 41 |
| channel | reject_native | kagi_56 | {"tol": 0.5, "conf": "body"} | sym15u / both | 229 | 3978 | -529 | -363 | -2591 | 3263 | 1 | 41 |
| channel | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 41 |
| channel | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 250 | 2499 | 248 | -1221 | -688 | 2208 | 1 | 41 |
| fvg15 | break | kagi_80 | {"n": 3, "k": 0.5} | sym15u / both | 83 | 1769 | -239 | 176 | 876 | 1390 | 1 | 41 |
| fvg15 | break_native | wrenko_10 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2142 | 699 | 1173 | -2521 | 1701 | 1 | 41 |
| fvg15 | false_break | pnf_10 | {"M": 3, "k": 0.5} | plain60/60 / short | 131 | 1273 | 165 | -386 | -465 | 1786 | 1 | 41 |
| fvg15 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | plain60/60 / short | 130 | 1094 | 257 | -577 | -633 | 1723 | 1 | 41 |
| fvg15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 3384 | -99 | 1317 | -307 | 4690 | 1 | 41 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 167 | 4419 | -178 | 432 | 336 | 5177 | 1 | 41 |
| fvg15 | retest | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 107 | 1682 | -181 | -793 | -565 | 1944 | 1 | 41 |
| fvg15 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 158 | 2957 | 1199 | 1020 | -199 | 3816 | 1 | 41 |
| fvg5 | break | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 41 |
| fvg5 | break_native | pnf_10 | {"n": 1, "k": 0.0} | sym15u / both | 228 | 3565 | 411 | 793 | 1067 | 3507 | 1 | 41 |
| fvg5 | false_break | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 41 |
| fvg5 | false_break_native | pnf_10 | {"M": 1, "k": 0.0} | sym15u / both | 209 | 2223 | 925 | 729 | 320 | 2590 | 1 | 41 |
| fvg5 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 239 | 2756 | 214 | -1882 | -387 | 2095 | 1 | 41 |
| fvg5 | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 242 | 2182 | 193 | -1316 | -820 | 1313 | 1 | 41 |
| fvg5 | retest | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 172 | 2473 | -230 | -1137 | -66 | 1925 | 1 | 41 |
| fvg5 | retest_native | frenko_40 | {"M": 10, "tol": 0.5} | sym15u / both | 189 | 3090 | -276 | -1553 | 384 | 2624 | 1 | 41 |
| gaps | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 93 | 2458 | 515 | -722 | -3227 | 1532 | 1 | 212 |
| gaps | break_native | pnf_7 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2868 | -251 | -161 | -3421 | 2136 | 1 | 212 |
| gaps | false_break | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 1779 | 18 | -19 | 344 | 2112 | 1 | 212 |
| gaps | false_break_native | pnf_28 | {"M": 2, "k": 0.5} | sym15u / both | 99 | 1843 | -87 | 76 | 307 | 2380 | 1 | 212 |
| gaps | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 191 | 2035 | -730 | -1775 | 708 | 1690 | 1 | 212 |
| gaps | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 147 | 2332 | -600 | 3 | -1106 | 2770 | 1 | 212 |
| gaps | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1584 | -348 | -820 | -994 | 1765 | 1 | 212 |
| gaps | retest_native | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 100 | 2963 | -29 | 441 | -1448 | 3370 | 1 | 212 |
| mmove | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 210 | 2588 | -853 | -45 | -2503 | 1001 | 1 | 41 |
| mmove | break_native | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 202 | 2486 | -450 | 418 | -1675 | 1326 | 1 | 41 |
| mmove | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 227 | 2557 | -462 | -577 | -579 | 2977 | 1 | 41 |
| mmove | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 225 | 2897 | -838 | -578 | -949 | 3394 | 1 | 41 |
| mmove | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 481 | 3098 | 409 | 646 | -265 | 2767 | 1 | 41 |
| mmove | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 214 | 3153 | -70 | 1060 | -1089 | 3669 | 1 | 41 |
| mmove | retest | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 41 |
| mmove | retest_native | pnf_5 | {"M": 3, "tol": 0.0} | sym15u / both | 221 | 3290 | 700 | 11 | -758 | 3384 | 1 | 41 |
| ob15 | break | wrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 81 | 1091 | 244 | -107 | 133 | 1385 | 1 | 41 |
| ob15 | break_native | kagi_10 | {"n": 3, "k": 0.5} | sym15u / both | 75 | 1244 | 663 | -890 | -72 | 1890 | 1 | 41 |
| ob15 | false_break | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 82 | 787 | -429 | -443 | -506 | 1161 | 1 | 41 |
| ob15 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 82 | 787 | -429 | -443 | -506 | 1161 | 1 | 41 |
| ob15 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 63 | 1376 | 323 | -1331 | 1080 | 1930 | 1 | 41 |
| ob15 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 71 | 1184 | 775 | -274 | 61 | 2027 | 1 | 41 |
| ob15 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1142 | 267 | -325 | 553 | 1702 | 1 | 41 |
| ob15 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 87 | 1197 | 155 | -638 | 61 | 1172 | 1 | 41 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 41 |
| ob5 | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 211 | 2331 | 256 | 1088 | 649 | 2053 | 1 | 41 |
| ob5 | false_break | pnf_5 | {"M": 3, "k": 0.5} | plain60/60 / both | 200 | 1963 | -56 | 924 | 346 | 1463 | 1 | 41 |
| ob5 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 126 | 2383 | -849 | -727 | 1517 | 1531 | 1 | 41 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 129 | 1424 | 71 | -876 | -916 | 1490 | 1 | 41 |
| ob5 | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 | 1981 | -488 | -1059 | -729 | 757 | 1 | 41 |
| ob5 | retest | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 97 | 2215 | -850 | -680 | 932 | 2095 | 1 | 41 |
| ob5 | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 111 | 2232 | -468 | -959 | 1160 | 2143 | 1 | 41 |
| opens | break | renko_14 | {"n": 1, "k": 0.25} | sym30u / both | 188 | 3946 | 43 | 1332 | 422 | 3112 | 2 | 212 |
| opens | break_native | renko_14 | {"n": 1, "k": 0.25} | asym20u/10u / both | 213 | 4141 | 36 | 1264 | 62 | 3545 | 2 | 212 |
| opens | false_break | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 212 |
| opens | false_break_native | pasl_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 429 | 3114 | 444 | -588 | -837 | 2750 | 1 | 212 |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 212 |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 214 | 4551 | -246 | 238 | 430 | 3334 | 1 | 212 |
| opens | retest | pasl_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 365 | 3307 | 120 | -78 | -1413 | 3961 | 1 | 212 |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1 | 212 |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1 | 212 |
| prior_day | break_native | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 103 | 2083 | 433 | -525 | -990 | 3127 | 1 | 212 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 2376 | 649 | -33 | -1668 | 3829 | 1 | 212 |
| prior_day | false_break_native | swing_atr_0.1 | {"M": 3, "k": 0.5} | sym15u / both | 126 | 2405 | 621 | -246 | -702 | 3078 | 1 | 212 |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 105 | 1827 | -426 | -804 | -662 | 720 | 1 | 212 |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 281 | 2224 | 66 | -917 | -270 | 1824 | 1 | 212 |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 167 | 2609 | 12 | -329 | 707 | 2514 | 1 | 212 |
| prior_day | retest_native | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 191 | 2712 | -110 | -383 | 424 | 2187 | 1 | 212 |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 162 | 2957 | -620 | 59 | -1689 | 2002 | 1 | 211 |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 165 | 3227 | -565 | 323 | -1499 | 2266 | 2 | 211 |
| profile_nodes | false_break | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 2292 | -55 | -984 | -1066 | 1894 | 1 | 211 |
| profile_nodes | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 208 | 2676 | -200 | -70 | 183 | 1964 | 2 | 211 |
| profile_nodes | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 152 | 2817 | -450 | -1140 | -2494 | 1640 | 1 | 211 |
| profile_nodes | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | sym15u / both | 204 | 2821 | -98 | -360 | 235 | 2346 | 2 | 211 |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 211 |
| profile_nodes | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 1 | 211 |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2970 | -121 | -1950 | -524 | 1758 | 1 | 212 |
| profile_va | break_native | renko_28 | {"n": 1, "k": 0.5} | sym8u / both | 143 | 2591 | -66 | -1416 | -848 | 2717 | 2 | 212 |
| profile_va | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 120 | 2493 | -419 | -437 | -1179 | 2786 | 1 | 212 |
| profile_va | false_break_native | tm30 | {"M": 2, "k": 0.5} | sym15u / both | 162 | 2584 | 299 | -691 | -241 | 3689 | 1 | 212 |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 128 | 2405 | -523 | 863 | 668 | 2266 | 1 | 212 |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 131 | 2493 | 295 | -1054 | 183 | 1120 | 1 | 212 |
| profile_va | retest | mom_28 | {"M": 10, "tol": 0.5} | sym15u / both | 133 | 3198 | 93 | -1886 | -354 | 2602 | 1 | 212 |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 3224 | -311 | -329 | -209 | 2404 | 1 | 212 |
| round | break | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 212 |
| round | break_native | mom_28 | {"n": 1, "k": 0.0} | sym15u / both | 252 | 3115 | 485 | -528 | -148 | 2152 | 1 | 212 |
| round | false_break | pasl_10 | {"M": 3, "k": 0.5} | plain60/60 / both | 717 | 3076 | -134 | 387 | -1885 | 3447 | 1 | 212 |
| round | false_break_native | dchg_112 | {"M": 2, "k": 0.5} | sym15u / both | 166 | 3286 | 139 | -661 | -1168 | 2614 | 1 | 212 |
| round | reject | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 405 | 3731 | -1516 | 737 | 448 | 5872 | 1 | 212 |
| round | reject_native | swing_atr_0.4 | {"tol": 1.0, "conf": "body"} | sym8u / both | 264 | 5128 | -1178 | 438 | 2006 | 5678 | 2 | 212 |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 212 |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 246 | 4477 | -191 | -320 | -645 | 5031 | 2 | 212 |
| session_hl | break | pasl_56 | {"n": 1, "k": 0.0} | sym15u / both | 139 | 1771 | -1102 | -336 | -292 | 2220 | 1 | 208 |
| session_hl | break_native | pasl_20 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2654 | -107 | 389 | -378 | 3494 | 1 | 208 |
| session_hl | false_break | renko_14 | {"M": 2, "k": 0.5} | asym20u/10u / both | 130 | 1640 | -516 | 85 | -1030 | 1483 | 2 | 208 |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 114 | 2154 | 41 | 535 | 418 | 2967 | 2 | 208 |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 130 | 1634 | -79 | 16 | 319 | 1221 | 2 | 208 |
| session_hl | reject_native | swing_pct_5 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 1805 | -162 | -987 | -1228 | -754 | 1 | 208 |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1 | 208 |
| session_hl | retest_native | swing_pct_12 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2330 | -299 | -559 | 604 | 3117 | 1 | 208 |
| trendline | break | mrenko_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 490 | 2957 | -338 | -167 | -927 | 697 | 1 | 41 |
| trendline | break_native | mrenko_14 | {"n": 2, "k": 0.25} | sym15u / both | 234 | 3004 | 8 | 371 | -320 | 5564 | 1 | 41 |
| trendline | false_break | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / both | 540 | 1894 | 260 | -1042 | -2133 | -658 | 1 | 41 |
| trendline | false_break_native | kagi_14 | {"M": 2, "k": 0.5} | plain60/60 / long | 281 | 1886 | 383 | -246 | -48 | 1129 | 1 | 41 |
| trendline | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 41 |
| trendline | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 3780 | -431 | -284 | 730 | 4408 | 1 | 41 |
| trendline | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 225 | 2709 | 329 | -350 | 447 | 2557 | 1 | 41 |
| trendline | retest_native | wrenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 220 | 3008 | -48 | -1940 | 1275 | 1937 | 1 | 41 |
| uw_dp | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 212 |
| uw_dp | break_native | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 212 |
| uw_dp | false_break | dchg_40 | {"M": 2, "k": 0.5} | sym15u / both | 109 | 2734 | 0 | 0 | 530 | 3624 | 1 | 212 |
| uw_dp | false_break_native | dchg_40 | {"M": 1, "k": 0.0} | sym15u / both | 109 | 2727 | 0 | 0 | 546 | 3376 | 1 | 212 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 112 | 1964 | 0 | 0 | 365 | 1874 | 1 | 212 |
| uw_dp | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 122 | 2086 | 0 | 0 | -468 | 1673 | 1 | 212 |
| uw_dp | retest | pasl_20 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2915 | 0 | 0 | -57 | 3691 | 1 | 212 |
| uw_dp | retest_native | dchg_40 | {"M": 10, "tol": 0.5} | sym15u / both | 104 | 2424 | 0 | 0 | 561 | 1869 | 1 | 212 |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1 | 211 |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 112 | 3662 | 0 | -280 | -459 | 3598 | 2 | 211 |
| uw_ndx | false_break | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 211 |
| uw_ndx | false_break_native | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 88 | 2347 | 0 | -175 | -2312 | 2034 | 1 | 211 |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 103 | 3115 | 0 | -345 | 406 | 1676 | 1 | 211 |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 96 | 2723 | 0 | -340 | 1465 | 2885 | 2 | 211 |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2949 | 0 | -109 | -693 | 2727 | 1 | 211 |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 141 | 2796 | 0 | 85 | -715 | 2712 | 1 | 211 |
| uw_qqq | break | renko_20 | {"n": 2, "k": 0.25} | sym8u / both | 144 | 2987 | 0 | -70 | -7 | 3329 | 2 | 211 |
| uw_qqq | break_native | renko_20 | {"n": 2, "k": 0.0} | sym8u / both | 145 | 2846 | 0 | 48 | 263 | 2703 | 2 | 211 |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 122 | 3111 | 0 | 268 | -100 | 2849 | 2 | 211 |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 125 | 2832 | 0 | -304 | -463 | 2243 | 2 | 211 |
| uw_qqq | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 116 | 2612 | 0 | 241 | -787 | -337 | 1 | 211 |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 121 | 3084 | 0 | 263 | -571 | 3471 | 1 | 211 |
| uw_qqq | retest | pasl_56 | {"M": 10, "tol": 0.5} | sym15u / both | 124 | 3332 | 0 | 198 | -544 | 3834 | 1 | 211 |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1 | 211 |
| vwap | break | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 230 | 5484 | 276 | -1123 | -2301 | 6752 | 2 | 211 |
| vwap | break_native | renko_14 | {"n": 3, "k": 0.5} | sym15u / both | 227 | 5738 | 534 | -1080 | -3184 | 7299 | 2 | 211 |
| vwap | false_break | dchg_56 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 2837 | 298 | -962 | 1185 | 2960 | 1 | 211 |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 160 | 2710 | 122 | 637 | 249 | 2886 | 1 | 211 |
| vwap | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 248 | 4751 | -37 | -1718 | 768 | 7179 | 2 | 211 |
| vwap | reject_native | cdr_100 | {"tol": 0.5, "conf": "body"} | sym8u / both | 233 | 5846 | 667 | 1147 | -135 | 5737 | 2 | 211 |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2 | 211 |
| vwap | retest_native | cdr_100 | {"M": 10, "tol": 0.5} | sym8u / both | 218 | 4634 | 959 | 362 | -947 | 5800 | 2 | 211 |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 245 | 4128 | 539 | -1135 | -304 | 5386 | 1 | 210 |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3642 | 1104 | 410 | -1140 | 1707 | 1 | 210 |
| vwap_bands | false_break | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 724 | 2432 | 689 | -2155 | 618 | 2198 | 1 | 210 |
| vwap_bands | false_break_native | lbrk_3_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 724 | 2432 | 689 | -2155 | 618 | 2198 | 1 | 210 |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 249 | 3847 | -1624 | 1607 | 609 | 3094 | 1 | 210 |
| vwap_bands | reject_native | dib_1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 280 | 3027 | 61 | -795 | 419 | 5272 | 1 | 210 |
| vwap_bands | retest | drb_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 684 | 3403 | 537 | -777 | -29 | 2793 | 1 | 210 |
| vwap_bands | retest_native | vsess_30 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 3675 | 581 | -1198 | -2832 | 5778 | 1 | 210 |
| week_month | break | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 42 | 1567 | 304 | -30 | -1454 | 1575 | 1 | 212 |
| week_month | break_native | swing_atr_0.25 | {"n": 2, "k": 0.25} | sym15u / both | 43 | 1508 | -111 | -183 | -1226 | 1563 | 1 | 212 |
| week_month | false_break | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 212 |
| week_month | false_break_native | dchg_112 | {"M": 1, "k": 0.0} | sym15u / both | 48 | 1229 | -532 | 225 | -375 | 1337 | 1 | 212 |
| week_month | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 38 | 1618 | 133 | -162 | -2232 | 2609 | 1 | 212 |
| week_month | reject_native | urenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 32 | 1579 | -70 | -765 | -196 | 1671 | 1 | 212 |
| week_month | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 33 | 1229 | 124 | -30 | -141 | 1120 | 1 | 212 |
| week_month | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 30 | 1759 | 102 | -138 | -542 | 2195 | 1 | 212 |
| zones | break | vol_4000 | {"n": 1, "k": 0.5} | sym8u / both | 113 | 2090 | 229 | 143 | 393 | 2008 | 2 | 211 |
| zones | break_native | renko_14 | {"n": 1, "k": 0.5} | asym10u/20u / both | 195 | 2650 | -114 | -424 | -736 | 2949 | 2 | 211 |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 162 | 2098 | -451 | -622 | -1038 | 3686 | 2 | 211 |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 112 | 1825 | -112 | -996 | 314 | 2093 | 2 | 211 |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 211 |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 201 | 3168 | 225 | -131 | -1006 | 2880 | 2 | 211 |
| zones | retest | tib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 128 | 2375 | -1292 | 285 | 258 | 2085 | 1 | 211 |
| zones | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 102 | 2223 | -765 | 332 | -877 | 1559 | 1 | 211 |

### NYAM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd15 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 33 | -234 | 67 | -448 | -269 | -2 | 1 | 41 |
| sd15 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 33 | -234 | 67 | -448 | -269 | -2 | 1 | 41 |
| sd5 | break | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 41 |
| sd5 | break_native | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 30 | -93 | -177 | 306 | -382 | -313 | 1 | 41 |
| sd5 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 34 | 316 | 265 | -707 | -255 | 653 | 1 | 41 |
| sd5 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 34 | 316 | 265 | -707 | -255 | 653 | 1 | 41 |
| sd5 | retest | kagi_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 31 | -237 | -183 | 312 | -408 | -277 | 1 | 41 |
| sd5 | retest_native | wrenko_20 | {"M": 6, "tol": 0.5} | plain60/60 / both | 30 | -115 | -213 | 319 | -270 | -121 | 1 | 41 |
| sdx15 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 171 | 2399 | -85 | 715 | 2594 | 3384 | 1 | 41 |
| sdx15 | lim_mid | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 333 | 2976 | -2286 | -2403 | -427 | 2983 | 1 | 41 |
| sdx15 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 373 | 3815 | 30 | -593 | -1777 | 5127 | 1 | 41 |
| sdx15 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 68 | 2107 | -1412 | -869 | 341 | 1563 | 1 | 41 |
| sdx15 | rej_flow | wrenko_10 | {"d": "A", "F": 0} | sym15u / both | 58 | 1194 | -483 | 1191 | -1486 | 1139 | 1 | 41 |
| sdx15 | rej_native | kagi_56 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 121 | 2039 | -160 | -2368 | -1749 | 2557 | 1 | 41 |
| sdx15 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 386 | 1956 | -1553 | -1374 | -943 | 1143 | 1 | 41 |
| sdx15 | retest | kagi_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 87 | 1671 | 1303 | -626 | 3804 | 2010 | 1 | 41 |
| sdx3 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 350 | 3483 | 1458 | 3578 | 5139 | 4750 | 1 | 41 |
| sdx3 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 182 | 3365 | 26 | 2134 | 1935 | 3244 | 1 | 41 |
| sdx3 | lim_prox | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 224 | 3509 | 1324 | 128 | -1502 | 4960 | 1 | 41 |
| sdx3 | rej | mrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 475 | 3002 | -2715 | -1978 | -5508 | 1958 | 1 | 41 |
| sdx3 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / long | 156 | 3037 | 6 | 1057 | -3441 | 2950 | 1 | 41 |
| sdx3 | rej_native | mrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 41 |
| sdx3 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 356 | 3139 | 271 | -969 | -2462 | 4768 | 1 | 41 |
| sdx3 | retest | kagi_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 245 | 2392 | 2042 | 2685 | 4969 | 3185 | 1 | 41 |
| sdx30 | break | pnf_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 79 | 1933 | -372 | 1333 | 866 | 1755 | 1 | 41 |
| sdx30 | lim_mid | wrenko_20 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 52 | 1565 | 12 | -897 | 111 | 634 | 1 | 41 |
| sdx30 | lim_prox | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 142 | 2308 | -245 | -373 | 1505 | 5248 | 1 | 41 |
| sdx30 | rej | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 73 | 1261 | -467 | -838 | -1738 | 1427 | 1 | 41 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 146 | 1480 | -676 | -2116 | -2930 | 1823 | 1 | 41 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 41 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 189 | 1748 | -1904 | -3586 | -1161 | 2207 | 1 | 41 |
| sdx30 | retest | pnf_28 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 35 | 976 | -101 | -1016 | 521 | 952 | 1 | 41 |
| sdx5 | break | wrenko_20 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 128 | 2348 | 760 | 872 | 1375 | 1924 | 1 | 41 |
| sdx5 | lim_mid | pnf_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 179 | 4263 | -912 | -271 | 1146 | 4807 | 1 | 41 |
| sdx5 | lim_prox | urenko_80 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 214 | 4370 | 1480 | 714 | 2473 | 2468 | 1 | 41 |
| sdx5 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 216 | 2627 | -830 | 131 | -3477 | 4401 | 1 | 41 |
| sdx5 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / both | 258 | 1062 | -1205 | -898 | -1943 | 1771 | 1 | 41 |
| sdx5 | rej_native | wrenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 41 |
| sdx5 | rej_zone | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 385 | 3244 | 1053 | 165 | -5880 | 4433 | 1 | 41 |
| sdx5 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 165 | 2309 | 1186 | -216 | 3671 | 2698 | 1 | 41 |
| sdx60 | break | kagi_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 52 | 1464 | 466 | 334 | 762 | 926 | 1 | 41 |
| sdx60 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 417 | 1570 | -1168 | -222 | -1705 | 689 | 1 | 41 |
| sdx60 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 429 | 1099 | -814 | -1355 | -3002 | 1374 | 1 | 41 |
| sdx60 | rej | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 124 | 2540 | -595 | -1785 | -237 | 2453 | 1 | 41 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / long | 90 | 1309 | 89 | -465 | -399 | 884 | 1 | 41 |
| sdx60 | rej_native | lbrk_3_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 41 |
| sdx60 | rej_zone | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 145 | 2102 | -330 | -834 | -199 | 1844 | 1 | 41 |
| sdx_renko28 | break | pnf_56 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 158 | 2617 | -1111 | 1032 | 1543 | 2235 | 1 | 41 |
| sdx_renko28 | lim_mid | kagi_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 475 | 4203 | 121 | -178 | 3832 | 2308 | 1 | 41 |
| sdx_renko28 | lim_prox | pnf_56 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 188 | 4526 | 216 | 1871 | -67 | 4152 | 1 | 41 |
| sdx_renko28 | rej | mrenko_10 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 417 | 2601 | -2519 | -2626 | -4344 | 2070 | 1 | 41 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 202 | 2765 | 740 | -3083 | 894 | 2859 | 1 | 41 |
| sdx_renko28 | rej_native | urenko_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 41 |
| sdx_renko28 | rej_zone | urenko_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 295 | 2552 | -84 | -3676 | -2682 | 553 | 1 | 41 |
| sdx_renko28 | retest | pnf_56 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 135 | 2994 | -717 | 618 | 233 | 2746 | 1 | 41 |
| sdx_rng28 | break | kagi_20 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 487 | 4615 | 1288 | 2874 | 6639 | 8079 | 1 | 41 |
| sdx_rng28 | lim_mid | kagi_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 502 | 4204 | -595 | -701 | -2 | 1835 | 1 | 41 |
| sdx_rng28 | lim_prox | wrenko_20 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 493 | 5342 | 520 | 1267 | -40 | 7530 | 1 | 41 |
| sdx_rng28 | rej | mrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 504 | 2856 | -984 | -1842 | -5463 | 2791 | 1 | 41 |
| sdx_rng28 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / long | 172 | 2052 | 2014 | -466 | -281 | 3800 | 1 | 41 |
| sdx_rng28 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 431 | 3332 | 1328 | -4047 | 1358 | 3443 | 1 | 41 |
| sdx_rng28 | rej_zone | frenko_40 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4594 | 559 | -3692 | -3237 | 3340 | 1 | 41 |
| sdx_rng28 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 445 | 3741 | 1098 | -711 | 4872 | 5506 | 1 | 41 |
| sdx_vol1100 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 432 | 3924 | -781 | 1019 | 5689 | 4212 | 1 | 41 |
| sdx_vol1100 | lim_mid | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1444 | 5146 | -307 | -267 | -7260 | 5686 | 1 | 41 |
| sdx_vol1100 | lim_prox | mrenko_14 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 1412 | 4616 | 1989 | -3 | -5487 | 5378 | 1 | 41 |
| sdx_vol1100 | rej | kagi_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 429 | 5058 | -1453 | -1789 | -1589 | 7224 | 1 | 41 |
| sdx_vol1100 | rej_flow | vrb_700 | {"d": "E", "F": 0} | sym15u / both | 321 | 2969 | -6 | 1488 | -104 | 2957 | 1 | 41 |
| sdx_vol1100 | rej_native | kagi_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 477 | 3771 | -172 | -664 | -3831 | 5515 | 1 | 41 |
| sdx_vol1100 | rej_zone | frenko_28 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 284 | 4710 | -906 | -898 | -3639 | 4361 | 1 | 41 |
| sdx_vol1100 | retest | wrenko_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 398 | 4494 | -381 | -1960 | 2674 | 5777 | 1 | 41 |
| fib15 | break | kagi_20 | {"n": 1, "k": 0.0} | sym15u / both | 346 | 3524 | 552 | 2335 | 3568 | 2093 | 1 | 41 |
| fib15 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 309 | 3889 | 1224 | -1144 | 3109 | 4406 | 1 | 41 |
| fib15 | false_break | pnf_5 | {"M": 3, "k": 0.5} | sym15u / both | 356 | 3289 | -131 | 2456 | 3878 | 2191 | 1 | 41 |
| fib15 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 985 | 3291 | 444 | 1910 | -2104 | 2878 | 1 | 41 |
| fib15 | pullback | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / long | 116 | 2115 | 1754 | 472 | -1463 | 3636 | 1 | 41 |
| fib15 | pullback_native | pnf_5 | {"tol": 0.5, "conf": "body"} | sym15u / long | 106 | 2608 | 1196 | 45 | -914 | 4367 | 1 | 41 |
| fib15 | reject | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 294 | 2531 | 868 | -585 | 3010 | 3488 | 1 | 41 |
| fib15 | reject_native | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 4502 | 87 | 1288 | 1778 | 4269 | 1 | 41 |
| fib15 | retest | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 328 | 4147 | -1385 | 2285 | 2790 | 3457 | 1 | 41 |
| fib15 | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 342 | 3490 | -840 | 1601 | -161 | 3295 | 1 | 41 |
| fib5 | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 392 | 4876 | -635 | -1541 | 2534 | 5721 | 1 | 41 |
| fib5 | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 187 | 3101 | 1263 | -128 | 1540 | 1917 | 1 | 41 |
| fib5 | false_break | kagi_20 | {"M": 3, "k": 0.5} | sym15u / both | 403 | 4940 | 944 | 1313 | 3307 | 5844 | 1 | 41 |
| fib5 | false_break_native | wrenko_10 | {"M": 2, "k": 0.5} | sym15u / both | 394 | 5399 | 68 | -2894 | 1385 | 3042 | 1 | 41 |
| fib5 | pullback | lbrk_3_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 254 | 2243 | -33 | -959 | -883 | 2909 | 1 | 41 |
| fib5 | pullback_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 311 | 2409 | 129 | 147 | 363 | 4528 | 1 | 41 |
| fib5 | reject | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 34 | 1877 | -184 | 434 | -161 | 2037 | 1 | 41 |
| fib5 | reject_native | pnf_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 284 | 2753 | -140 | 262 | 1608 | 2820 | 1 | 41 |
| fib5 | retest | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 375 | 4340 | 561 | -571 | 2129 | 2299 | 1 | 41 |
| fib5 | retest_native | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 392 | 4261 | 1104 | -1881 | 3422 | 2396 | 1 | 41 |
| fib60 | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 291 | 4260 | 834 | -351 | -346 | 2844 | 1 | 41 |
| fib60 | break_native | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 291 | 4260 | 834 | -351 | -346 | 2844 | 1 | 41 |
| fib60 | false_break | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 288 | 4302 | 869 | 588 | 1330 | 5241 | 1 | 41 |
| fib60 | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 304 | 4321 | 2499 | 3022 | 1035 | 4383 | 1 | 41 |
| fib60 | pullback | lbrk_3_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 111 | 1315 | -353 | 2477 | 284 | 602 | 1 | 41 |
| fib60 | pullback_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 144 | 1953 | 409 | 2239 | 1366 | 1976 | 1 | 41 |
| fib60 | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 297 | 3853 | 197 | -2307 | -1069 | 5413 | 1 | 41 |
| fib60 | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 309 | 3595 | -544 | -1575 | -629 | 3065 | 1 | 41 |
| fib60 | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 283 | 4034 | 1024 | 761 | 814 | 3982 | 1 | 41 |
| fib60 | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 350 | 3645 | -129 | 298 | 273 | 3427 | 1 | 41 |
| fibr_dev | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 41 |
| fibr_dev | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 458 | 3837 | 4233 | 2856 | 953 | 4322 | 1 | 41 |
| fibr_dev | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 460 | 3921 | 2689 | 822 | 2042 | 4742 | 1 | 41 |
| fibr_dev | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 452 | 4732 | 2585 | -852 | 3835 | 5674 | 1 | 41 |
| fibr_dev | reject | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / both | 169 | 3087 | 936 | 1508 | -135 | 2125 | 1 | 41 |
| fibr_dev | reject_native | pnf_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 448 | 4974 | 1168 | 2667 | 817 | 4931 | 1 | 41 |
| fibr_dev | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 414 | 5720 | -316 | 1766 | 2350 | 3254 | 1 | 41 |
| fibr_dev | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | sym15u / both | 427 | 4867 | -1061 | -570 | 4293 | 5344 | 1 | 41 |
| fibr_ib | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 314 | 2855 | -277 | 881 | 4137 | 3297 | 1 | 41 |
| fibr_ib | break_native | frenko_28 | {"n": 3, "k": 0.5} | sym15u / both | 336 | 2812 | 1115 | -212 | 3599 | 1490 | 1 | 41 |
| fibr_ib | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 41 |
| fibr_ib | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 325 | 4545 | 1796 | -1944 | 2034 | 3922 | 1 | 41 |
| fibr_ib | reject | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 710 | 3281 | -283 | -506 | 2843 | 3230 | 1 | 41 |
| fibr_ib | reject_native | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 313 | 3225 | 598 | 890 | -471 | 3776 | 1 | 41 |
| fibr_ib | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 222 | 2506 | 180 | -429 | 3 | 1221 | 1 | 41 |
| fibr_ib | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 333 | 2991 | 863 | 1825 | 1106 | 3425 | 1 | 41 |
| fibr_on | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 390 | 3646 | 879 | 2200 | 7144 | 3961 | 1 | 41 |
| fibr_on | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 414 | 4795 | 1610 | 372 | 7170 | 7330 | 1 | 41 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 383 | 5252 | 1464 | 1013 | 2918 | 7973 | 1 | 41 |
| fibr_on | false_break_native | pnf_10 | {"M": 2, "k": 0.5} | sym15u / both | 381 | 5512 | 761 | 1389 | 392 | 8972 | 1 | 41 |
| fibr_on | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 1073 | 2934 | 854 | -766 | 249 | 1445 | 1 | 41 |
| fibr_on | reject_native | kagi_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 286 | 3620 | 579 | -1335 | -1835 | 3947 | 1 | 41 |
| fibr_on | retest | lbrk_3_20 | {"M": 6, "tol": 0.5} | sym15u / both | 273 | 2663 | -1647 | 883 | 1488 | 3069 | 1 | 41 |
| fibr_on | retest_native | pnf_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 3227 | 1904 | -823 | -47 | 375 | 1 | 41 |
| fibr_or | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 41 |
| fibr_or | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 391 | 5520 | -1080 | -710 | -2013 | 5470 | 1 | 41 |
| fibr_or | false_break | urenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 349 | 3867 | 432 | 1403 | -216 | 2811 | 1 | 41 |
| fibr_or | false_break_native | kagi_14 | {"M": 1, "k": 0.0} | sym15u / both | 383 | 3852 | 98 | 1427 | 1769 | 3344 | 1 | 41 |
| fibr_or | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 374 | 3996 | -233 | 328 | 4247 | 4044 | 1 | 41 |
| fibr_or | reject_native | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 490 | 3288 | 56 | 1396 | 513 | -467 | 1 | 41 |
| fibr_or | retest | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 1 | 41 |
| fibr_or | retest_native | kagi_20 | {"M": 3, "tol": 0.0} | sym15u / both | 361 | 5330 | -762 | -231 | -3898 | 3669 | 1 | 41 |
| fibr_pd | break | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 363 | 6035 | -981 | 1122 | 3395 | 6251 | 1 | 41 |
| fibr_pd | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 365 | 5426 | -679 | 158 | 2300 | 6842 | 1 | 41 |
| fibr_pd | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -320 | 484 | 1967 | 1800 | 1 | 41 |
| fibr_pd | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 3574 | -278 | 484 | 1967 | 1800 | 1 | 41 |
| fibr_pd | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 41 |
| fibr_pd | reject_native | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 340 | 5238 | -1748 | 1982 | 2411 | 6394 | 1 | 41 |
| fibr_pd | retest | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 41 |
| fibr_pd | retest_native | mrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 322 | 4397 | -248 | -304 | -18 | 2442 | 1 | 41 |
| piv_cama | break | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 357 | 5210 | 1949 | 420 | -2741 | 6204 | 1 | 41 |
| piv_cama | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 379 | 6524 | 489 | 1354 | 649 | 7212 | 1 | 41 |
| piv_cama | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 194 | 3092 | 319 | 526 | 2048 | 2764 | 1 | 41 |
| piv_cama | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 187 | 3276 | 454 | 729 | 1972 | 3605 | 1 | 41 |
| piv_cama | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 381 | 3907 | -760 | 253 | 597 | 3463 | 1 | 41 |
| piv_cama | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 412 | 4654 | -2040 | -878 | -4527 | 4643 | 1 | 41 |
| piv_cama | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 41 |
| piv_cama | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 369 | 3890 | -15 | 859 | 1334 | 3096 | 1 | 41 |
| piv_floor | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3553 | -161 | 488 | 2430 | 2793 | 1 | 41 |
| piv_floor | break_native | pnf_10 | {"n": 2, "k": 0.25} | sym15u / both | 354 | 4181 | 1622 | 504 | 3964 | 2860 | 1 | 41 |
| piv_floor | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 186 | 3796 | -476 | 286 | 3151 | 3316 | 1 | 41 |
| piv_floor | false_break_native | kagi_40 | {"M": 3, "k": 0.5} | sym15u / both | 377 | 4160 | 1164 | 1611 | 1824 | 5277 | 1 | 41 |
| piv_floor | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 351 | 2917 | 1884 | -488 | -3275 | 2870 | 1 | 41 |
| piv_floor | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 351 | 2917 | 1884 | -488 | -3275 | 2870 | 1 | 41 |
| piv_floor | retest | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 136 | 3307 | 1674 | 1218 | 2007 | 4474 | 1 | 41 |
| piv_floor | retest_native | pnf_56 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 3913 | 1673 | 239 | 2389 | 4656 | 1 | 41 |
| piv_wf | break | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 3685 | 42 | 27 | 876 | 2866 | 1 | 41 |
| piv_wf | break_native | kagi_20 | {"n": 3, "k": 0.5} | sym15u / both | 394 | 3769 | -323 | 382 | 4352 | 7535 | 1 | 41 |
| piv_wf | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 395 | 3750 | 2632 | 2336 | 1588 | 3570 | 1 | 41 |
| piv_wf | false_break_native | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 373 | 3736 | 2381 | 2146 | 1178 | 2963 | 1 | 41 |
| piv_wf | reject | urenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 306 | 2772 | -874 | -732 | 1160 | 5492 | 1 | 41 |
| piv_wf | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 404 | 2303 | -833 | 3724 | 3038 | 2931 | 1 | 41 |
| piv_wf | retest | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 361 | 4657 | 320 | 3797 | -729 | 5338 | 1 | 41 |
| piv_wf | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 323 | 4338 | 1465 | 1240 | 2816 | 3449 | 1 | 41 |
| swcluster | break | urenko_112 | {"n": 3, "k": 0.5} | sym15u / both | 54 | 1306 | 832 | -672 | 48 | 1510 | 1 | 41 |
| swcluster | break_native | kagi_80 | {"n": 1, "k": 0.0} | sym15u / long | 56 | 1203 | -745 | -84 | -805 | 1222 | 1 | 41 |
| swcluster | false_break | pnf_40 | {"M": 1, "k": 0.0} | sym15u / both | 93 | 1551 | -519 | -769 | 385 | 1862 | 1 | 41 |
| swcluster | false_break_native | pnf_40 | {"M": 3, "k": 0.5} | sym15u / both | 84 | 1583 | -538 | -389 | -652 | 2255 | 1 | 41 |
| swcluster | reject | wrenko_20 | {"tol": 0.0, "conf": "close"} | sym15u / both | 78 | 994 | -808 | 727 | -1417 | 573 | 1 | 41 |
| swcluster | reject_native | kagi_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 115 | 1254 | -69 | -238 | 607 | 824 | 1 | 41 |
| swcluster | retest | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 47 | 1317 | -512 | -727 | -288 | 1601 | 1 | 41 |
| swcluster | retest_native | kagi_80 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1293 | 791 | -1867 | 192 | 1950 | 1 | 41 |
| swsr15 | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 41 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / both | 358 | 3793 | 2163 | 1177 | 3112 | 4443 | 1 | 41 |
| swsr15 | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 372 | 3937 | 1163 | 182 | 1458 | 3348 | 1 | 41 |
| swsr15 | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 343 | 5020 | 338 | -1450 | 5190 | 5244 | 1 | 41 |
| swsr15 | reject | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 328 | 3874 | -2044 | -176 | -1129 | 4458 | 1 | 41 |
| swsr15 | reject_native | pnf_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 354 | 3290 | -1693 | 687 | -2566 | 6013 | 1 | 41 |
| swsr15 | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 290 | 5015 | -392 | -944 | 1428 | 4099 | 1 | 41 |
| swsr15 | retest_native | urenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 333 | 4907 | 1503 | -111 | 2647 | 3519 | 1 | 41 |
| swsr5 | break | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 435 | 5683 | 1075 | -778 | -1404 | 4628 | 1 | 41 |
| swsr5 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 435 | 5683 | 1075 | -778 | -1404 | 4628 | 1 | 41 |
| swsr5 | false_break | kagi_28 | {"M": 1, "k": 0.0} | sym15u / both | 444 | 5625 | 880 | -288 | -1389 | 4925 | 1 | 41 |
| swsr5 | false_break_native | kagi_28 | {"M": 2, "k": 0.5} | sym15u / both | 432 | 8188 | 1948 | -2061 | 866 | 8579 | 1 | 41 |
| swsr5 | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 407 | 3165 | -776 | 1166 | 1559 | 3156 | 1 | 41 |
| swsr5 | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 452 | 4120 | -609 | 1554 | 3190 | 5222 | 1 | 41 |
| swsr5 | retest | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 665 | 2200 | 3212 | 5780 | 1 | 41 |
| swsr5 | retest_native | pnf_20 | {"M": 3, "tol": 0.0} | sym15u / both | 283 | 4493 | 691 | 2200 | 3212 | 5780 | 1 | 41 |
| swsr60 | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 292 | 3965 | 36 | 158 | -2380 | 1344 | 1 | 41 |
| swsr60 | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 254 | 4303 | 338 | -270 | -2273 | 3058 | 1 | 41 |
| swsr60 | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 290 | 2588 | 1112 | -417 | 1728 | 2743 | 1 | 41 |
| swsr60 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / both | 286 | 2726 | 385 | -291 | 3026 | 3397 | 1 | 41 |
| swsr60 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 240 | 2871 | -893 | -1110 | -691 | 4303 | 1 | 41 |
| swsr60 | reject_native | pnf_7 | {"tol": 0.5, "conf": "body"} | sym15u / both | 207 | 2996 | -223 | 738 | -2958 | 2749 | 1 | 41 |
| swsr60 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 264 | 3367 | 417 | 713 | 2105 | 2877 | 1 | 41 |
| swsr60 | retest_native | urenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 235 | 3947 | -295 | 1712 | 542 | 2019 | 1 | 41 |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 251 | 5486 | 738 | 818 | 1504 | 1968 | 2 | 210 |
| stack | break_native | rng_80 | {"k": 2, "cw": 2.0} | sym8u / both | 307 | 6590 | -1020 | 397 | 79 | 3936 | 2 | 210 |
| stack | reject | pnf_5 | {"k": 2, "cw": 0.5} | sym15u / both | 152 | 2969 | -1754 | -1412 | -638 | 2326 | 1 | 210 |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | asym20u/10u / both | 248 | 3290 | -789 | 971 | -1202 | 4802 | 2 | 210 |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 101 | 1642 | -1133 | 498 | 721 | 2376 | 2 | 211 |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 65 | 1335 | -822 | 539 | 550 | 1717 | 1 | 211 |
| book_walls_loose | false_break | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 211 |
| book_walls_loose | false_break_native | dchg_10 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1436 | -1803 | -2147 | -1329 | 2140 | 1 | 211 |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 93 | 1730 | 66 | 6 | 2266 | 2356 | 2 | 211 |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 126 | 1601 | -738 | -637 | 518 | 1605 | 1 | 211 |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1266 | -894 | 749 | 1751 | 1947 | 1 | 211 |
| book_walls_loose | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | sym15u / both | 46 | 1406 | -798 | -684 | 1371 | 1763 | 1 | 211 |
| channel | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 41 |
| channel | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 411 | 4675 | -645 | 4537 | 4359 | 5761 | 1 | 41 |
| channel | false_break | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 41 |
| channel | false_break_native | wrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 411 | 3460 | -132 | 4073 | 3994 | 3495 | 1 | 41 |
| channel | reject | wrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 401 | 3917 | -208 | 972 | 4672 | 2881 | 1 | 41 |
| channel | reject_native | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 463 | 4187 | 146 | -2476 | 4036 | 4709 | 1 | 41 |
| channel | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 527 | 5168 | 1396 | -726 | 235 | 2951 | 1 | 41 |
| channel | retest_native | kagi_20 | {"M": 10, "tol": 0.5} | sym15u / both | 420 | 6420 | 1977 | 2723 | 3726 | 6347 | 1 | 41 |
| fvg15 | break | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 330 | -695 | 1898 | 2097 | 1 | 41 |
| fvg15 | break_native | pnf_40 | {"n": 1, "k": 0.0} | sym15u / both | 134 | 2491 | 408 | -695 | 1898 | 2097 | 1 | 41 |
| fvg15 | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 63 | 2026 | 106 | -1123 | 207 | 1397 | 1 | 41 |
| fvg15 | false_break_native | kagi_112 | {"M": 3, "k": 0.5} | sym15u / both | 108 | 2100 | -895 | 84 | -297 | 1921 | 1 | 41 |
| fvg15 | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 176 | 1407 | -534 | 1658 | -536 | 571 | 1 | 41 |
| fvg15 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 354 | 1253 | 175 | 1053 | 1876 | 1196 | 1 | 41 |
| fvg15 | retest | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 41 |
| fvg15 | retest_native | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 108 | 2444 | 878 | 1057 | -281 | 2788 | 1 | 41 |
| fvg5 | break | lbrk_3_40 | {"n": 3, "k": 0.5} | sym15u / both | 161 | 2212 | 932 | -1000 | -902 | -520 | 1 | 41 |
| fvg5 | break_native | pnf_14 | {"n": 2, "k": 0.25} | sym15u / both | 233 | 2280 | 649 | 1613 | 1744 | 1553 | 1 | 41 |
| fvg5 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 201 | 1913 | -47 | -1966 | 1134 | 1338 | 1 | 41 |
| fvg5 | false_break_native | pnf_20 | {"M": 1, "k": 0.0} | sym15u / both | 193 | 1676 | -1207 | -1321 | 1577 | 1248 | 1 | 41 |
| fvg5 | reject | kagi_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 126 | 1934 | 248 | 21 | 1054 | 1217 | 1 | 41 |
| fvg5 | reject_native | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 131 | 1899 | 677 | 400 | -1831 | 3448 | 1 | 41 |
| fvg5 | retest | kagi_40 | {"M": 10, "tol": 0.5} | sym15u / both | 222 | 3806 | -1035 | -262 | -445 | 2561 | 1 | 41 |
| fvg5 | retest_native | pnf_40 | {"M": 10, "tol": 0.5} | sym15u / both | 144 | 2329 | -55 | -245 | -934 | 2721 | 1 | 41 |
| gaps | break | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 104 | -1328 | 2128 | 1944 | 1 | 211 |
| gaps | break_native | pnf_28 | {"n": 1, "k": 0.0} | sym15u / both | 215 | 2587 | 142 | -1328 | 2128 | 1944 | 1 | 211 |
| gaps | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -820 | -86 | 2898 | 2982 | 1 | 211 |
| gaps | false_break_native | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 138 | 3123 | -762 | -86 | 2898 | 2982 | 1 | 211 |
| gaps | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 211 |
| gaps | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 208 | 2674 | -544 | 2257 | 2203 | 2999 | 1 | 211 |
| gaps | retest | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 494 | 2981 | -132 | -126 | -354 | 1963 | 1 | 211 |
| gaps | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 221 | 3004 | 496 | -2177 | 458 | 3709 | 1 | 211 |
| mmove | break | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 41 |
| mmove | break_native | kagi_14 | {"n": 1, "k": 0.0} | sym15u / both | 336 | 3567 | 239 | -51 | 4187 | 5149 | 1 | 41 |
| mmove | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 177 | 2201 | 17 | 122 | 1471 | 1317 | 1 | 41 |
| mmove | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 175 | 2638 | 531 | -330 | 1424 | 1843 | 1 | 41 |
| mmove | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / long | 95 | 2790 | 1939 | 398 | 1792 | 3227 | 1 | 41 |
| mmove | reject_native | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 317 | 3372 | -70 | 595 | -1300 | 2698 | 1 | 41 |
| mmove | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 329 | 3092 | 1424 | 140 | 3397 | 3171 | 1 | 41 |
| mmove | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / long | 170 | 3030 | 552 | -385 | 1137 | 4321 | 1 | 41 |
| ob15 | break | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 143 | 2715 | -364 | 1077 | -198 | 2970 | 1 | 41 |
| ob15 | break_native | mrenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 144 | 2579 | -490 | 437 | 440 | 3050 | 1 | 41 |
| ob15 | false_break | kagi_80 | {"M": 2, "k": 0.5} | sym15u / both | 120 | 1724 | 1840 | 757 | 2754 | 1249 | 1 | 41 |
| ob15 | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | sym15u / both | 128 | 1730 | 694 | -773 | 1270 | -274 | 1 | 41 |
| ob15 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 125 | 2280 | -762 | 112 | 499 | 2143 | 1 | 41 |
| ob15 | reject_native | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2140 | 289 | -157 | 1697 | 330 | 1 | 41 |
| ob15 | retest | urenko_14 | {"M": 10, "tol": 0.5} | sym15u / both | 110 | 2538 | -231 | 102 | 2014 | 2666 | 1 | 41 |
| ob15 | retest_native | pnf_7 | {"M": 6, "tol": 0.5} | plain60/60 / both | 200 | 2091 | 649 | -1044 | 32 | 1538 | 1 | 41 |
| ob5 | break | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 41 |
| ob5 | break_native | kagi_10 | {"n": 1, "k": 0.0} | sym15u / both | 150 | 3190 | -50 | -560 | -1480 | 43 | 1 | 41 |
| ob5 | false_break | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 41 |
| ob5 | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 150 | 2647 | 367 | 57 | -284 | 936 | 1 | 41 |
| ob5 | reject | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 139 | 1592 | 443 | -1429 | -219 | 1037 | 1 | 41 |
| ob5 | reject_native | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 140 | 2232 | -724 | -50 | -411 | 97 | 1 | 41 |
| ob5 | retest | kagi_14 | {"M": 10, "tol": 0.5} | sym15u / both | 151 | 2614 | -885 | -1043 | -1778 | 2222 | 1 | 41 |
| ob5 | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | sym15u / both | 150 | 2537 | -637 | -296 | -515 | 1382 | 1 | 41 |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | 1 | 207 |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 394 | 5790 | 809 | -1370 | 684 | 4105 | 2 | 207 |
| open_range | false_break | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 435 | 2425 | 23 | -145 | -730 | 1542 | 2 | 207 |
| open_range | false_break_native | renko_20 | {"M": 1, "k": 0.5} | sym8u / both | 420 | 2670 | 231 | -183 | -1477 | 2468 | 2 | 207 |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 403 | 6353 | 476 | -605 | -960 | 4974 | 2 | 207 |
| open_range | reject_native | renko_40 | {"tol": 1.0, "conf": "close"} | sym8u / both | 391 | 6274 | -1585 | 1562 | -2188 | 5176 | 2 | 207 |
| open_range | retest | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 360 | 4800 | 1260 | 1255 | -2074 | 5665 | 1 | 207 |
| open_range | retest_native | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 298 | 4014 | 703 | 324 | -1734 | 2744 | 2 | 207 |
| opens | break | dchg_40 | {"n": 1, "k": 0.0} | sym15u / both | 360 | 5490 | -643 | 803 | 229 | 6745 | 1 | 211 |
| opens | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 338 | 5821 | 1364 | -659 | -1602 | 6521 | 1 | 211 |
| opens | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 168 | 4705 | -649 | -420 | 1329 | 4754 | 1 | 211 |
| opens | false_break_native | pnf_56 | {"M": 2, "k": 0.5} | sym15u / both | 139 | 4781 | -690 | 144 | 2901 | 3989 | 1 | 211 |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 367 | 5218 | -809 | 1237 | -891 | 2404 | 1 | 211 |
| opens | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 315 | 4982 | -996 | -570 | 2619 | 6379 | 1 | 211 |
| opens | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 306 | 4952 | 1079 | -2912 | 3174 | 4784 | 1 | 211 |
| opens | retest_native | pnf_20 | {"M": 6, "tol": 0.5} | sym15u / both | 294 | 4635 | 1331 | 789 | 2801 | 6670 | 1 | 211 |
| prior_day | break | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 211 |
| prior_day | break_native | swing_atr_0.25 | {"n": 1, "k": 0.0} | sym15u / both | 203 | 5918 | 1300 | 387 | 6559 | 6302 | 1 | 211 |
| prior_day | false_break | swing_atr_0.25 | {"M": 2, "k": 0.5} | sym15u / both | 200 | 6120 | 1169 | 654 | 6266 | 6027 | 1 | 211 |
| prior_day | false_break_native | swing_atr_0.25 | {"M": 1, "k": 0.0} | sym15u / both | 202 | 5639 | 1638 | 523 | 6789 | 6233 | 1 | 211 |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 170 | 3323 | 195 | -118 | 844 | 3659 | 1 | 211 |
| prior_day | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 236 | 3941 | -100 | 955 | 4507 | 4286 | 2 | 211 |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 211 |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1 | 211 |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 1 | 210 |
| profile_nodes | break_native | pnf_7 | {"n": 2, "k": 0.25} | sym15u / both | 277 | 3995 | 2467 | -1651 | 1370 | 3940 | 1 | 210 |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 1 | 210 |
| profile_nodes | false_break_native | rng_40 | {"M": 1, "k": 0.5} | sym8u / both | 226 | 3965 | -671 | 942 | 823 | 4444 | 2 | 210 |
| profile_nodes | reject | renko_20 | {"tol": 1.0, "conf": "close"} | plain60/60 / both | 483 | 3360 | 110 | -1175 | 115 | 1930 | 2 | 210 |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 305 | 4170 | 488 | -242 | -812 | 3982 | 1 | 210 |
| profile_nodes | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 210 |
| profile_nodes | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 242 | 4251 | -587 | -1214 | 1954 | 2715 | 1 | 210 |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 2 | 211 |
| profile_va | break_native | rng_28 | {"n": 2, "k": 0.5} | sym15u / both | 217 | 4047 | 449 | 1260 | 3137 | 4304 | 2 | 211 |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 198 | 3091 | 543 | 151 | 2346 | 3855 | 2 | 211 |
| profile_va | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | plain60/60 / both | 548 | 2993 | 1062 | 46 | 172 | 1929 | 1 | 211 |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 487 | 4134 | 580 | -764 | 1549 | 4242 | 1 | 211 |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 263 | 4791 | -360 | 58 | 2424 | 3455 | 1 | 211 |
| profile_va | retest | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 465 | 3564 | -541 | -277 | 960 | 1989 | 1 | 211 |
| profile_va | retest_native | swing_atr_0.1 | {"M": 10, "tol": 0.5} | plain60/60 / both | 472 | 5646 | -87 | 79 | 1170 | 3842 | 1 | 211 |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 505 | 8284 | -852 | -683 | 2764 | 7588 | 2 | 211 |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 480 | 8082 | 547 | 474 | 3963 | 8386 | 2 | 211 |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 531 | 6712 | -926 | -3185 | 1543 | 6684 | 2 | 211 |
| round | false_break_native | vol_500 | {"M": 2, "k": 0.5} | asym10u/20u / both | 543 | 5669 | -1429 | -2821 | 263 | 7059 | 2 | 211 |
| round | reject | renko_10 | {"tol": 1.0, "conf": "close"} | sym15u / both | 657 | 8023 | -600 | -3119 | -4002 | 8822 | 2 | 211 |
| round | reject_native | vsess_200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 540 | 6009 | 257 | -1854 | -806 | 4925 | 2 | 211 |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 2 | 211 |
| round | retest_native | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 617 | 6587 | -614 | 2075 | 217 | 5937 | 2 | 211 |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 455 | 152 | -732 | 4801 | 1 | 209 |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 289 | 5222 | 391 | 152 | -732 | 4801 | 1 | 209 |
| session_hl | false_break | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 346 | 4857 | 1820 | -135 | 2442 | 2702 | 1 | 209 |
| session_hl | false_break_native | dchg_10 | {"M": 2, "k": 0.5} | sym15u / both | 344 | 5417 | 1497 | 47 | 2767 | 3055 | 1 | 209 |
| session_hl | reject | tick_5000 | {"tol": 0.0, "conf": "body"} | sym8u / both | 257 | 2738 | -362 | 1005 | -702 | 2504 | 2 | 209 |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | 1 | 209 |
| session_hl | retest | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 209 |
| session_hl | retest_native | renko_10 | {"M": 6, "tol": 0.0} | asym20u/10u / both | 398 | 5395 | -994 | -1033 | -525 | 5963 | 2 | 209 |
| trendline | break | kagi_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 538 | 3996 | 289 | 1595 | -1677 | 2376 | 1 | 41 |
| trendline | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 297 | 3534 | 1905 | 1508 | -2673 | 3553 | 1 | 41 |
| trendline | false_break | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 285 | 4062 | 1560 | 1127 | 1434 | 5996 | 1 | 41 |
| trendline | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 275 | 4692 | 42 | 1654 | 1101 | 5496 | 1 | 41 |
| trendline | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 206 | 2009 | -383 | -16 | 2214 | 954 | 1 | 41 |
| trendline | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 272 | 3205 | 233 | 64 | 1560 | 4027 | 1 | 41 |
| trendline | retest | wrenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 234 | 3192 | -7 | -266 | -583 | 2917 | 1 | 41 |
| trendline | retest_native | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 283 | 3545 | 204 | 994 | 2670 | 3978 | 1 | 41 |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 222 | 3431 | 0 | 0 | 374 | 2879 | 2 | 211 |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 324 | 3901 | 0 | 0 | -440 | 3278 | 2 | 211 |
| uw_dp | false_break | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 211 |
| uw_dp | false_break_native | swing_pct_8 | {"M": 1, "k": 0.0} | sym15u / both | 166 | 2760 | 0 | 0 | 430 | 2509 | 1 | 211 |
| uw_dp | reject | urenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 94 | 3468 | 0 | 0 | 524 | 3496 | 1 | 211 |
| uw_dp | reject_native | mom_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 135 | 3130 | 0 | 0 | 439 | 2925 | 1 | 211 |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 153 | 3839 | 0 | 0 | 1297 | 3514 | 2 | 211 |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 155 | 4448 | 0 | 0 | 599 | 5392 | 2 | 211 |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 164 | 3136 | 0 | -374 | 1450 | 3813 | 2 | 210 |
| uw_ndx | break_native | pnf_56 | {"n": 1, "k": 0.0} | sym15u / both | 127 | 3128 | 0 | -546 | 405 | 3823 | 1 | 210 |
| uw_ndx | false_break | pnf_56 | {"M": 1, "k": 0.0} | sym15u / both | 132 | 3610 | 0 | -751 | 396 | 4581 | 1 | 210 |
| uw_ndx | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 123 | 3723 | 0 | -835 | 637 | 4863 | 1 | 210 |
| uw_ndx | reject | wrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 164 | 2550 | 0 | -500 | 237 | 5607 | 1 | 210 |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 102 | 2410 | 0 | -964 | 135 | 3727 | 1 | 210 |
| uw_ndx | retest | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 210 |
| uw_ndx | retest_native | dchg_20 | {"M": 3, "tol": 0.0} | sym15u / both | 157 | 3552 | 0 | 364 | 3186 | 2732 | 1 | 210 |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 210 |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 197 | 4488 | 0 | -934 | 2894 | 3826 | 2 | 210 |
| uw_qqq | false_break | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 3700 | 0 | 196 | 4339 | 4603 | 1 | 210 |
| uw_qqq | false_break_native | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 3384 | 0 | 197 | 3751 | 4321 | 1 | 210 |
| uw_qqq | reject | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 210 |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 177 | 3843 | 0 | -504 | 1611 | 4151 | 2 | 210 |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 210 |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2 | 210 |
| vwap | break | rng_80 | {"n": 2, "k": 0.5} | sym8u / both | 294 | 4569 | 929 | 247 | 3761 | 4575 | 2 | 210 |
| vwap | break_native | swing_pct_5 | {"n": 1, "k": 0.25} | sym8u / both | 356 | 6256 | -15 | 937 | -331 | 5107 | 2 | 210 |
| vwap | false_break | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 178 | 4696 | 63 | -174 | 2422 | 5048 | 1 | 210 |
| vwap | false_break_native | pnf_56 | {"M": 3, "k": 0.5} | sym15u / both | 166 | 4411 | -108 | -214 | 2319 | 4241 | 1 | 210 |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 336 | 6019 | 1125 | -146 | -239 | 7732 | 2 | 210 |
| vwap | reject_native | tm60 | {"tol": 0.0, "conf": "close"} | sym15u / both | 302 | 5838 | -1468 | 1495 | -1469 | 6714 | 1 | 210 |
| vwap | retest | tm15 | {"M": 10, "tol": 0.5} | sym15u / both | 353 | 4113 | 1019 | 662 | 1923 | 5583 | 1 | 210 |
| vwap | retest_native | tm15 | {"M": 6, "tol": 0.5} | sym15u / both | 352 | 4260 | 459 | 1038 | 2222 | 6362 | 1 | 210 |
| vwap_bands | break | mom_20 | {"n": 3, "k": 0.5} | sym15u / both | 475 | 6544 | 86 | 1981 | 5311 | 8312 | 1 | 209 |
| vwap_bands | break_native | drb_400 | {"n": 2, "k": 0.25} | sym15u / both | 545 | 5721 | -772 | -2232 | 2651 | 4494 | 1 | 209 |
| vwap_bands | false_break | swing_atr_0.6 | {"M": 3, "k": 0.5} | sym15u / both | 477 | 3977 | 1234 | -534 | 5712 | 3574 | 1 | 209 |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 419 | 5308 | -523 | -797 | 1777 | 7540 | 2 | 209 |
| vwap_bands | reject | tick_300 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 481 | 6944 | 1737 | -351 | 2059 | 7316 | 2 | 209 |
| vwap_bands | reject_native | vol_500 | {"tol": 0.5, "conf": "close"} | asym10u/20u / both | 512 | 6769 | -741 | 751 | 2018 | 2515 | 2 | 209 |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 475 | 5871 | -47 | -3369 | -2356 | 8027 | 2 | 209 |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 452 | 5820 | -431 | 1126 | 1466 | 4714 | 1 | 209 |
| week_month | break | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 2684 | 577 | 625 | -670 | 1745 | 2 | 211 |
| week_month | break_native | renko_14 | {"n": 1, "k": 0.5} | asym20u/10u / both | 81 | 3092 | 228 | -190 | -164 | 2293 | 2 | 211 |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 211 |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1 | 211 |
| week_month | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 | 1812 | 674 | -92 | 992 | 1655 | 1 | 211 |
| week_month | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 82 | 2131 | 988 | -272 | -1646 | 1573 | 1 | 211 |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 2 | 211 |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 68 | 2858 | 1034 | 105 | -852 | 1578 | 2 | 211 |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 258 | 3168 | -553 | -1075 | -778 | 2957 | 2 | 210 |
| zones | break_native | swing_pct_8 | {"n": 3, "k": 0.5} | sym15u / both | 157 | 3433 | -813 | -1533 | -456 | 4515 | 1 | 210 |
| zones | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 171 | 3068 | 829 | 2566 | -2302 | 3067 | 1 | 210 |
| zones | false_break_native | urenko_28 | {"M": 3, "k": 0.5} | sym15u / both | 169 | 3155 | 720 | 2082 | -2078 | 3224 | 1 | 210 |
| zones | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 96 | 2134 | 178 | -1365 | -390 | 3312 | 1 | 210 |
| zones | reject_native | dlt_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 2882 | -1835 | -913 | -60 | 3270 | 1 | 210 |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2 | 210 |
| zones | retest_native | rng_14 | {"M": 6, "tol": 0.5} | sym8u / both | 217 | 2669 | -1529 | -653 | -535 | 2164 | 2 | 210 |

### NYPM (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 63 | 745 | -750 | 713 | 55 | 78 | 1 | 41 |
| sdx15 | lim_mid | urenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 218 | 3979 | 866 | -1611 | -3817 | 3589 | 1 | 41 |
| sdx15 | lim_prox | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 276 | 3753 | 213 | -649 | -2699 | 2977 | 1 | 41 |
| sdx15 | rej | wrenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 151 | 2838 | 1403 | -67 | -500 | 3343 | 1 | 41 |
| sdx15 | rej_flow | wrenko_14 | {"d": "E", "F": 9} | sym15u / both | 103 | 1888 | -308 | 1188 | 1098 | 2361 | 1 | 41 |
| sdx15 | rej_native | kagi_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 41 |
| sdx15 | rej_zone | kagi_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 164 | 3230 | -109 | -1094 | -602 | 2788 | 1 | 41 |
| sdx15 | retest | pnf_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 31 | 526 | -752 | 859 | -350 | 61 | 1 | 41 |
| sdx3 | break | pnf_7 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 103 | 1995 | -691 | -13 | 2296 | 1834 | 1 | 41 |
| sdx3 | lim_mid | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 315 | 3243 | 1073 | -1181 | -5173 | 1197 | 1 | 41 |
| sdx3 | lim_prox | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 405 | 3173 | -505 | 837 | -3633 | 2384 | 1 | 41 |
| sdx3 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 251 | 2478 | 724 | 613 | -327 | 1370 | 1 | 41 |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 218 | 3964 | 768 | 815 | -3268 | 3684 | 1 | 41 |
| sdx3 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 41 |
| sdx3 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 213 | 3617 | -84 | 3155 | -2428 | 3839 | 1 | 41 |
| sdx3 | retest | kagi_10 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 68 | 1390 | 118 | 65 | 1080 | 1692 | 1 | 41 |
| sdx30 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 34 | 466 | -431 | 870 | -122 | 440 | 1 | 41 |
| sdx30 | lim_mid | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 103 | 1951 | 721 | -406 | -107 | 947 | 1 | 41 |
| sdx30 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 3042 | -219 | -1016 | 531 | 2612 | 1 | 41 |
| sdx30 | rej | urenko_14 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 38 | 1091 | -267 | -1452 | -151 | 712 | 1 | 41 |
| sdx30 | rej_flow | dol_500 | {"d": "E", "F": 9} | plain60/60 / short | 62 | 592 | -282 | -737 | -409 | 420 | 1 | 41 |
| sdx30 | rej_native | kagi_56 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 41 |
| sdx30 | rej_zone | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 152 | 1505 | 53 | -888 | -1269 | 1903 | 1 | 41 |
| sdx5 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 91 | 2323 | -533 | 988 | 255 | 1749 | 1 | 41 |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 720 | 2734 | 720 | 3 | -3881 | 2478 | 1 | 41 |
| sdx5 | lim_prox | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 746 | 2572 | -102 | -1530 | -5419 | 2741 | 1 | 41 |
| sdx5 | rej | kagi_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 143 | 2330 | 3481 | 902 | -3209 | 2420 | 1 | 41 |
| sdx5 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 97 | 1766 | 159 | -855 | -1246 | 2358 | 1 | 41 |
| sdx5 | rej_native | urenko_10 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 178 | 2412 | -1189 | 369 | -649 | 2087 | 1 | 41 |
| sdx5 | rej_zone | mrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 198 | 2334 | -819 | -884 | -1076 | 2111 | 1 | 41 |
| sdx5 | retest | kagi_20 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 82 | 1774 | -756 | -147 | -45 | 2087 | 1 | 41 |
| sdx60 | break | kagi_80 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 384 | 10 | 407 | 778 | 289 | 1 | 41 |
| sdx60 | lim_mid | kagi_80 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 73 | 1628 | 155 | 544 | -311 | 1363 | 1 | 41 |
| sdx60 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 259 | 1933 | -320 | -699 | -24 | 2535 | 1 | 41 |
| sdx60 | rej | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 76 | 986 | -87 | -92 | 901 | 1294 | 1 | 41 |
| sdx60 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | plain60/60 / short | 37 | 432 | -131 | 314 | 665 | 397 | 1 | 41 |
| sdx60 | rej_native | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 41 |
| sdx60 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 59 | 1065 | 125 | -191 | 644 | 993 | 1 | 41 |
| sdx_renko28 | break | pnf_14 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 129 | 2292 | -1534 | 786 | -391 | 1043 | 1 | 41 |
| sdx_renko28 | lim_mid | mrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 430 | 3882 | -32 | 158 | -242 | 4284 | 1 | 41 |
| sdx_renko28 | lim_prox | kagi_56 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 285 | 3300 | 213 | 469 | 2009 | 5781 | 1 | 41 |
| sdx_renko28 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 537 | 5198 | -406 | -1538 | 809 | 6421 | 1 | 41 |
| sdx_renko28 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / short | 102 | 1940 | 787 | 26 | -743 | 1348 | 1 | 41 |
| sdx_renko28 | rej_native | pnf_5 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 41 |
| sdx_renko28 | rej_zone | pnf_5 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 541 | 3581 | -461 | -885 | -96 | 3905 | 1 | 41 |
| sdx_renko28 | retest | pnf_14 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 89 | 1596 | -851 | 795 | 41 | 977 | 1 | 41 |
| sdx_rng28 | break | frenko_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 301 | 3408 | -2123 | 661 | -816 | 3058 | 1 | 41 |
| sdx_rng28 | lim_mid | frenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 331 | 3377 | 299 | -3020 | -3304 | 3142 | 1 | 41 |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1024 | 4026 | -947 | 896 | -3778 | 6473 | 1 | 41 |
| sdx_rng28 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 462 | 2252 | -1322 | -833 | -1038 | 2734 | 1 | 41 |
| sdx_rng28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 224 | 2295 | 245 | -1493 | 2758 | 457 | 1 | 41 |
| sdx_rng28 | rej_native | wrenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 41 |
| sdx_rng28 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 353 | 3234 | 2062 | -100 | 5954 | 1890 | 1 | 41 |
| sdx_rng28 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 117 | 2944 | -978 | 239 | 485 | 3365 | 1 | 41 |
| sdx_vol1100 | break | pnf_5 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 314 | 4031 | -1409 | -503 | 658 | 4201 | 1 | 41 |
| sdx_vol1100 | lim_mid | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 275 | 6337 | -998 | 71 | 1443 | 6397 | 1 | 41 |
| sdx_vol1100 | lim_prox | pnf_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 278 | 5565 | -679 | -26 | -465 | 6171 | 1 | 41 |
| sdx_vol1100 | rej | frenko_28 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 308 | 3089 | -275 | -2567 | -1719 | 2706 | 1 | 41 |
| sdx_vol1100 | rej_flow | wrenko_20 | {"d": "E", "F": 0} | sym15u / short | 90 | 2232 | -129 | -218 | 268 | 1907 | 1 | 41 |
| sdx_vol1100 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 768 | 3970 | -570 | -433 | -756 | 4714 | 1 | 41 |
| sdx_vol1100 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 162 | 3444 | 914 | 374 | -624 | 4290 | 1 | 41 |
| sdx_vol1100 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 227 | 3437 | -1140 | -704 | 968 | 4601 | 1 | 41 |
| fib15 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3386 | -215 | -1066 | -1338 | 3676 | 1 | 41 |
| fib15 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / short | 182 | 3296 | 118 | -747 | -1540 | 3799 | 1 | 41 |
| fib15 | false_break | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 41 |
| fib15 | false_break_native | urenko_28 | {"M": 1, "k": 0.0} | sym15u / short | 130 | 3285 | -897 | -1602 | 168 | 3662 | 1 | 41 |
| fib15 | pullback | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 92 | 1869 | -30 | -12 | -37 | 2298 | 1 | 41 |
| fib15 | pullback_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / short | 83 | 2154 | 184 | -420 | -152 | 2586 | 1 | 41 |
| fib15 | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 41 |
| fib15 | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 239 | 3784 | -345 | -1343 | 2139 | 4737 | 1 | 41 |
| fib15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / short | 125 | 3286 | 93 | -404 | 983 | 3482 | 1 | 41 |
| fib15 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 208 | 3836 | 116 | -100 | -2461 | 3206 | 1 | 41 |
| fib5 | break | kagi_14 | {"n": 2, "k": 0.25} | sym15u / both | 287 | 4326 | 634 | -449 | -5249 | 4348 | 1 | 41 |
| fib5 | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 278 | 3324 | -704 | -1927 | 652 | 3009 | 1 | 41 |
| fib5 | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 41 |
| fib5 | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 3891 | -953 | -2389 | 59 | 4508 | 1 | 41 |
| fib5 | pullback | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 177 | 2745 | 927 | 815 | -218 | 2230 | 1 | 41 |
| fib5 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / short | 135 | 1865 | -693 | 1105 | -22 | 1426 | 1 | 41 |
| fib5 | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 389 | 5190 | 867 | 1104 | 100 | 5716 | 1 | 41 |
| fib5 | reject_native | urenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 295 | 3775 | -1517 | 2905 | 1380 | 4817 | 1 | 41 |
| fib5 | retest | kagi_80 | {"M": 3, "tol": 0.0} | sym15u / both | 213 | 2669 | -792 | 1234 | -3864 | 4158 | 1 | 41 |
| fib5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 282 | 2959 | -1605 | -750 | -58 | 3452 | 1 | 41 |
| fib60 | break | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 41 |
| fib60 | break_native | urenko_20 | {"n": 1, "k": 0.0} | sym15u / both | 158 | 3622 | -931 | 339 | -776 | 3501 | 1 | 41 |
| fib60 | false_break | frenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 185 | 2975 | -251 | -49 | -2488 | 2245 | 1 | 41 |
| fib60 | false_break_native | frenko_28 | {"M": 1, "k": 0.0} | sym15u / both | 185 | 2975 | -251 | -49 | -2488 | 2245 | 1 | 41 |
| fib60 | pullback | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 112 | 1154 | -168 | 33 | 1030 | 1211 | 1 | 41 |
| fib60 | pullback_native | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 124 | 1147 | -154 | -514 | 855 | 1018 | 1 | 41 |
| fib60 | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 160 | 1847 | -862 | 2531 | 1525 | 2927 | 1 | 41 |
| fib60 | reject_native | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 181 | 2566 | -602 | -1595 | -766 | 3167 | 1 | 41 |
| fib60 | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 124 | 2392 | -360 | 1609 | -959 | 2711 | 1 | 41 |
| fib60 | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 142 | 2972 | -1194 | 195 | 1413 | 1856 | 1 | 41 |
| fibr_dev | break | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 323 | 3270 | -463 | 160 | 151 | 3127 | 1 | 41 |
| fibr_dev | break_native | kagi_20 | {"n": 2, "k": 0.25} | sym15u / both | 318 | 3177 | 292 | 1852 | -1651 | 4840 | 1 | 41 |
| fibr_dev | false_break | mrenko_20 | {"M": 1, "k": 0.0} | sym15u / short | 135 | 2113 | -1084 | 533 | -722 | 1248 | 1 | 41 |
| fibr_dev | false_break_native | pnf_14 | {"M": 2, "k": 0.5} | sym15u / short | 147 | 2266 | -564 | -453 | 81 | 2314 | 1 | 41 |
| fibr_dev | reject | kagi_56 | {"tol": 1.0, "conf": "body"} | sym15u / short | 111 | 3039 | -906 | -439 | 785 | 4073 | 1 | 41 |
| fibr_dev | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 310 | 2919 | -21 | 3751 | 295 | 2947 | 1 | 41 |
| fibr_dev | retest | kagi_112 | {"M": 10, "tol": 0.5} | sym15u / both | 209 | 2769 | -1419 | 969 | 78 | 2576 | 1 | 41 |
| fibr_dev | retest_native | kagi_112 | {"M": 3, "tol": 0.0} | sym15u / both | 193 | 2734 | -611 | -1064 | -1498 | 2411 | 1 | 41 |
| fibr_ib | break | pnf_5 | {"n": 3, "k": 0.5} | sym15u / both | 251 | 3612 | 92 | -1032 | -493 | 1859 | 1 | 41 |
| fibr_ib | break_native | frenko_40 | {"n": 2, "k": 0.25} | sym15u / both | 245 | 3856 | -1527 | 184 | -1787 | 3643 | 1 | 41 |
| fibr_ib | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / both | 231 | 2998 | -1461 | -465 | -1676 | 5234 | 1 | 41 |
| fibr_ib | false_break_native | mrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 258 | 3604 | -782 | -1742 | -1366 | 5952 | 1 | 41 |
| fibr_ib | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 103 | 2850 | -295 | -373 | -692 | 2170 | 1 | 41 |
| fibr_ib | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 267 | 3485 | 245 | 3147 | -1000 | 2581 | 1 | 41 |
| fibr_ib | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 41 |
| fibr_ib | retest_native | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 258 | 3021 | -364 | 170 | 78 | 6256 | 1 | 41 |
| fibr_on | break | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 235 | 2308 | -806 | 3069 | -2296 | 3200 | 1 | 41 |
| fibr_on | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 235 | 2613 | 83 | 1407 | 1700 | 2276 | 1 | 41 |
| fibr_on | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 232 | 2221 | -828 | 1006 | -1840 | 1304 | 1 | 41 |
| fibr_on | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 233 | 2219 | -607 | 594 | -2194 | 1699 | 1 | 41 |
| fibr_on | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 224 | 4457 | -1590 | -30 | -30 | 3118 | 1 | 41 |
| fibr_on | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 224 | 4457 | -1590 | -30 | -30 | 3118 | 1 | 41 |
| fibr_on | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 228 | 2547 | -512 | 810 | -273 | 485 | 1 | 41 |
| fibr_on | retest_native | pnf_14 | {"M": 10, "tol": 0.5} | sym15u / both | 217 | 2587 | -133 | 2095 | -1145 | 3420 | 1 | 41 |
| fibr_or | break | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 223 | 3722 | 1679 | 177 | 2896 | 4918 | 1 | 41 |
| fibr_or | break_native | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 235 | 3359 | -844 | 380 | -352 | 3018 | 1 | 41 |
| fibr_or | false_break | kagi_10 | {"M": 2, "k": 0.5} | sym15u / both | 227 | 3162 | -2539 | 1556 | 88 | 4085 | 1 | 41 |
| fibr_or | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | sym15u / both | 227 | 2711 | -2616 | 999 | 797 | 3303 | 1 | 41 |
| fibr_or | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 41 |
| fibr_or | reject_native | wrenko_14 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 454 | 2671 | -626 | -664 | -1437 | 760 | 1 | 41 |
| fibr_or | retest | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / short | 106 | 2541 | -582 | -25 | -891 | 2914 | 1 | 41 |
| fibr_or | retest_native | wrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 226 | 3433 | -1079 | 1971 | 1090 | 4690 | 1 | 41 |
| fibr_pd | break | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 41 |
| fibr_pd | break_native | lbrk_3_40 | {"n": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 42 | -1381 | 1884 | 1 | 41 |
| fibr_pd | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 208 | 1998 | -349 | 1339 | -3324 | 2735 | 1 | 41 |
| fibr_pd | false_break_native | lbrk_3_40 | {"M": 1, "k": 0.0} | sym15u / short | 93 | 1967 | -914 | 38 | -1381 | 1884 | 1 | 41 |
| fibr_pd | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 197 | 3093 | 14 | 1008 | -2214 | 3340 | 1 | 41 |
| fibr_pd | reject_native | kagi_112 | {"tol": 0.5, "conf": "body"} | sym15u / both | 132 | 3634 | -868 | -66 | -1162 | 2545 | 1 | 41 |
| fibr_pd | retest | pnf_10 | {"M": 3, "tol": 0.0} | sym15u / short | 88 | 2090 | 436 | -59 | -1075 | 1885 | 1 | 41 |
| fibr_pd | retest_native | kagi_56 | {"M": 6, "tol": 0.5} | sym15u / short | 101 | 2104 | 27 | 796 | -2196 | 1839 | 1 | 41 |
| piv_cama | break | kagi_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 529 | 2062 | 1743 | 913 | -1667 | 1448 | 1 | 41 |
| piv_cama | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 229 | 3002 | -798 | 88 | -642 | 3792 | 1 | 41 |
| piv_cama | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 205 | 1211 | -1613 | 1135 | 1006 | 996 | 1 | 41 |
| piv_cama | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 1497 | -1854 | 1699 | -3056 | 2291 | 1 | 41 |
| piv_cama | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 536 | 2838 | 205 | -269 | -2327 | 3249 | 1 | 41 |
| piv_cama | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 551 | 2235 | 495 | -257 | -1384 | 2735 | 1 | 41 |
| piv_cama | retest | urenko_20 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 3017 | 1323 | -981 | 973 | 1360 | 1 | 41 |
| piv_cama | retest_native | wrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 209 | 2890 | -621 | -741 | 2051 | 2186 | 1 | 41 |
| piv_floor | break | urenko_80 | {"n": 2, "k": 0.25} | sym15u / both | 146 | 2104 | 89 | 2484 | 144 | 1328 | 1 | 41 |
| piv_floor | break_native | urenko_56 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2598 | 440 | 2679 | 586 | 1925 | 1 | 41 |
| piv_floor | false_break | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 41 |
| piv_floor | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | plain60/60 / both | 420 | 1091 | -1194 | 1149 | -191 | 582 | 1 | 41 |
| piv_floor | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 174 | 2732 | 312 | 945 | 1219 | 3340 | 1 | 41 |
| piv_floor | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 243 | 4162 | -247 | 2182 | -410 | 2889 | 1 | 41 |
| piv_floor | retest | mrenko_20 | {"M": 6, "tol": 0.5} | sym15u / both | 123 | 2261 | -762 | -663 | -1617 | 2246 | 1 | 41 |
| piv_floor | retest_native | lbrk_3_10 | {"M": 10, "tol": 0.5} | sym15u / both | 194 | 2174 | 539 | -433 | 264 | 1551 | 1 | 41 |
| piv_wf | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 41 |
| piv_wf | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1824 | 1272 | 416 | -154 | 1 | 41 |
| piv_wf | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 225 | 2201 | -2119 | 1210 | 156 | 75 | 1 | 41 |
| piv_wf | false_break_native | kagi_56 | {"M": 1, "k": 0.0} | sym15u / both | 226 | 2012 | -1842 | 1094 | 416 | -154 | 1 | 41 |
| piv_wf | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 88 | 1762 | -1585 | -62 | -1571 | 3382 | 1 | 41 |
| piv_wf | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 265 | 3055 | -151 | -947 | -2159 | 1619 | 1 | 41 |
| piv_wf | retest | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 41 |
| piv_wf | retest_native | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 186 | 2470 | -1242 | 354 | 915 | 3629 | 1 | 41 |
| swcluster | break | pnf_5 | {"n": 3, "k": 0.5} | plain60/60 / both | 78 | 1434 | -579 | -308 | -267 | 1378 | 1 | 41 |
| swcluster | break_native | lbrk_3_20 | {"n": 3, "k": 0.5} | sym15u / both | 47 | 1484 | -898 | 212 | -2023 | 2300 | 1 | 41 |
| swcluster | false_break | lbrk_3_40 | {"M": 1, "k": 0.0} | plain60/60 / both | 66 | 711 | -608 | 898 | -670 | 546 | 1 | 41 |
| swcluster | false_break_native | urenko_112 | {"M": 3, "k": 0.5} | sym15u / both | 33 | 948 | -1573 | 501 | -496 | 1074 | 1 | 41 |
| swcluster | reject | wrenko_14 | {"tol": 0.0, "conf": "close"} | sym15u / both | 43 | 1368 | -235 | -439 | 744 | 1365 | 1 | 41 |
| swcluster | reject_native | urenko_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 51 | 1544 | 242 | 371 | -1281 | 1329 | 1 | 41 |
| swcluster | retest | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 41 | 1442 | -759 | 86 | 271 | 908 | 1 | 41 |
| swcluster | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1618 | -3 | 1405 | 681 | 911 | 1 | 41 |
| swsr15 | break | kagi_40 | {"n": 1, "k": 0.0} | sym15u / short | 117 | 3147 | -556 | 558 | 71 | 3221 | 1 | 41 |
| swsr15 | break_native | kagi_40 | {"n": 1, "k": 0.0} | sym15u / short | 117 | 3147 | -556 | 558 | 71 | 3221 | 1 | 41 |
| swsr15 | false_break | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 247 | 2905 | -826 | 1401 | 1932 | 1475 | 1 | 41 |
| swsr15 | false_break_native | pnf_5 | {"M": 2, "k": 0.5} | sym15u / short | 117 | 2948 | 43 | -480 | 1191 | 3055 | 1 | 41 |
| swsr15 | reject | kagi_14 | {"tol": 1.0, "conf": "body"} | sym15u / short | 118 | 3340 | 255 | -524 | 1304 | 2502 | 1 | 41 |
| swsr15 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 271 | 4013 | 690 | 61 | -2201 | 2481 | 1 | 41 |
| swsr15 | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 176 | 2920 | 1261 | 1356 | -1090 | 2148 | 1 | 41 |
| swsr15 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 246 | 2938 | -421 | -968 | 2213 | 2463 | 1 | 41 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 41 |
| swsr5 | break_native | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 286 | 3444 | -2207 | -1559 | 1262 | 1616 | 1 | 41 |
| swsr5 | false_break | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 41 |
| swsr5 | false_break_native | urenko_10 | {"M": 1, "k": 0.0} | sym15u / short | 192 | 3895 | -1112 | -1283 | 613 | 3121 | 1 | 41 |
| swsr5 | reject | kagi_14 | {"tol": 0.5, "conf": "body"} | sym15u / short | 131 | 2900 | 435 | -192 | 1157 | 4072 | 1 | 41 |
| swsr5 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 165 | 2981 | 290 | 1019 | 19 | 3754 | 1 | 41 |
| swsr5 | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 260 | 4440 | -950 | -3103 | 1054 | 1787 | 1 | 41 |
| swsr5 | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 291 | 4019 | -261 | -2125 | 4208 | 2958 | 1 | 41 |
| swsr60 | break | pnf_40 | {"n": 2, "k": 0.25} | sym15u / short | 38 | 1767 | 558 | -107 | 48 | 2005 | 1 | 41 |
| swsr60 | break_native | kagi_40 | {"n": 3, "k": 0.5} | sym15u / both | 163 | 2879 | -1426 | 831 | -277 | 3346 | 1 | 41 |
| swsr60 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2016 | 888 | -971 | -1148 | 2792 | 1 | 41 |
| swsr60 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 187 | 2016 | 888 | -971 | -1148 | 2792 | 1 | 41 |
| swsr60 | reject | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 81 | 1934 | -1464 | 154 | -1935 | 2404 | 1 | 41 |
| swsr60 | reject_native | kagi_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 212 | 3196 | -733 | 1116 | -3739 | 3316 | 1 | 41 |
| swsr60 | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / short | 129 | 1496 | 335 | -641 | -63 | 1628 | 1 | 41 |
| swsr60 | retest_native | kagi_80 | {"M": 10, "tol": 0.5} | sym15u / both | 170 | 1967 | -1647 | 1506 | -2401 | 1541 | 1 | 41 |
| stack | break | urenko_28 | {"k": 2, "cw": 0.5} | sym15u / short | 86 | 2291 | 234 | -41 | 1145 | 1866 | 1 | 210 |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 107 | 3072 | 144 | 769 | -10 | 2485 | 1 | 210 |
| stack | reject | rng_20 | {"k": 2, "cw": 1.0} | asym10u/20u / both | 101 | 2187 | -447 | 1473 | -506 | 1062 | 2 | 210 |
| stack | reject_native | dol_350 | {"k": 4, "cw": 2.0} | plain60/60 / short | 192 | 3062 | -384 | 254 | 556 | 2627 | 1 | 210 |
| book_walls | break | time_s_5 | {"n": 2, "k": 0.25} | plain60/60 / both | 42 | 894 | -489 | -382 | 220 | 1042 | 1 | 209 |
| book_walls | break_native | tm15 | {"n": 1, "k": 0.0} | plain60/60 / both | 30 | 605 | -584 | -435 | -96 | 784 | 1 | 209 |
| book_walls | reject | time_s_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 47 | 475 | -958 | -263 | -638 | 569 | 1 | 209 |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 34 | 561 | 55 | -204 | -128 | 492 | 1 | 209 |
| book_walls | retest | time_s_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 499 | -402 | -181 | 44 | 592 | 1 | 209 |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 34 | 627 | -374 | 538 | 3 | 600 | 1 | 209 |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 96 | 1984 | 477 | -129 | -417 | 3812 | 1 | 211 |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 2 | 211 |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1 | 211 |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 86 | 1871 | -345 | 574 | 531 | 1850 | 1 | 211 |
| book_walls_loose | reject | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 57 | 1173 | 963 | -1384 | -1489 | 994 | 2 | 211 |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 2 | 211 |
| book_walls_loose | retest | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / short | 41 | 962 | -161 | -663 | 174 | 1475 | 1 | 211 |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 72 | 1146 | 212 | 787 | -261 | 941 | 1 | 211 |
| channel | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / short | 131 | 2891 | -746 | -580 | 1666 | 2590 | 1 | 41 |
| channel | break_native | mrenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 275 | 3932 | -2003 | 2173 | -8 | 4372 | 1 | 41 |
| channel | false_break | pnf_7 | {"M": 3, "k": 0.5} | sym15u / both | 293 | 3216 | -1127 | 782 | 1821 | 3617 | 1 | 41 |
| channel | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 269 | 3285 | -130 | 684 | 4085 | 3749 | 1 | 41 |
| channel | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 200 | 3044 | -754 | 780 | -1553 | 4489 | 1 | 41 |
| channel | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 227 | 3124 | -1460 | -819 | -1409 | 4809 | 1 | 41 |
| channel | retest | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 280 | 2884 | -1066 | -819 | -1144 | 2504 | 1 | 41 |
| channel | retest_native | kagi_40 | {"M": 6, "tol": 0.5} | sym15u / both | 279 | 4816 | -153 | -1208 | 1427 | 4943 | 1 | 41 |
| fvg15 | break | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 41 |
| fvg15 | break_native | kagi_28 | {"n": 1, "k": 0.0} | sym15u / both | 109 | 1564 | -1302 | 388 | 1546 | 698 | 1 | 41 |
| fvg15 | false_break | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 41 |
| fvg15 | false_break_native | pnf_28 | {"M": 1, "k": 0.0} | sym15u / both | 66 | 1383 | -786 | 196 | 311 | 1422 | 1 | 41 |
| fvg15 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 59 | 1177 | 560 | -604 | 190 | 541 | 1 | 41 |
| fvg15 | reject_native | vrb_40000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 34 | 1545 | -182 | 363 | -346 | 1563 | 1 | 41 |
| fvg15 | retest | urenko_28 | {"M": 10, "tol": 0.5} | sym15u / both | 81 | 1488 | -659 | 345 | -893 | 1193 | 1 | 41 |
| fvg15 | retest_native | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 97 | 2069 | -451 | 295 | -1907 | 1585 | 1 | 41 |
| fvg5 | break | kagi_40 | {"n": 2, "k": 0.25} | sym15u / both | 172 | 2941 | -43 | 529 | 74 | 1047 | 1 | 41 |
| fvg5 | break_native | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 189 | 2590 | -1104 | -310 | -224 | 1211 | 1 | 41 |
| fvg5 | false_break | kagi_40 | {"M": 1, "k": 0.0} | sym15u / short | 97 | 1497 | 237 | -1092 | -344 | 965 | 1 | 41 |
| fvg5 | false_break_native | kagi_28 | {"M": 3, "k": 0.5} | sym15u / short | 110 | 1603 | -227 | -235 | -464 | 1975 | 1 | 41 |
| fvg5 | reject | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 157 | 1877 | 86 | 1529 | -360 | 2685 | 1 | 41 |
| fvg5 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 218 | 1978 | -13 | -449 | -1512 | 1297 | 1 | 41 |
| fvg5 | retest | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / both | 311 | 2041 | -507 | -733 | 178 | 770 | 1 | 41 |
| fvg5 | retest_native | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 148 | 1893 | 54 | 15 | -175 | 1618 | 1 | 41 |
| gaps | break | kagi_28 | {"n": 3, "k": 0.5} | sym15u / both | 106 | 2351 | -1950 | -331 | -1857 | 1830 | 1 | 211 |
| gaps | break_native | wrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 108 | 1966 | -1477 | 311 | -678 | 1813 | 1 | 211 |
| gaps | false_break | time_s_5 | {"M": 1, "k": 0.0} | sym30u / both | 39 | 1447 | -588 | 325 | -1319 | 918 | 2 | 211 |
| gaps | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 113 | 1904 | -1039 | 978 | -175 | 1124 | 1 | 211 |
| gaps | reject | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 189 | 1492 | 731 | -1239 | -821 | 493 | 1 | 211 |
| gaps | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 132 | 2841 | -343 | 129 | -838 | 2493 | 1 | 211 |
| gaps | retest | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 102 | 1919 | -539 | 412 | 1770 | 768 | 1 | 211 |
| gaps | retest_native | kagi_56 | {"M": 10, "tol": 0.5} | sym15u / both | 122 | 2649 | -496 | -97 | 417 | 1216 | 1 | 211 |
| mmove | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 41 |
| mmove | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 241 | 3555 | -25 | -1259 | -1777 | 3095 | 1 | 41 |
| mmove | false_break | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 41 |
| mmove | false_break_native | mrenko_14 | {"M": 1, "k": 0.0} | sym15u / both | 280 | 4681 | -1015 | 591 | -1419 | 3520 | 1 | 41 |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 242 | 2230 | 761 | -280 | -16 | 1468 | 1 | 41 |
| mmove | reject_native | pnf_7 | {"tol": 1.0, "conf": "body"} | sym15u / short | 134 | 2490 | -534 | 260 | 1315 | 2427 | 1 | 41 |
| mmove | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 41 |
| mmove | retest_native | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 220 | 3260 | -205 | -1462 | 726 | 2729 | 1 | 41 |
| ob15 | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1311 | -552 | 809 | -735 | 1890 | 1 | 41 |
| ob15 | break_native | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 44 | 1311 | -552 | 809 | -735 | 1890 | 1 | 41 |
| ob15 | false_break | pnf_20 | {"M": 2, "k": 0.5} | sym15u / both | 55 | 1383 | -438 | 971 | 66 | 1341 | 1 | 41 |
| ob15 | false_break_native | pnf_20 | {"M": 3, "k": 0.5} | sym15u / both | 51 | 1394 | -674 | 804 | 277 | 1544 | 1 | 41 |
| ob15 | reject | wrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 55 | 925 | -325 | -377 | 1269 | 2009 | 1 | 41 |
| ob15 | reject_native | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 55 | 1100 | 158 | 617 | 1076 | 2402 | 1 | 41 |
| ob15 | retest | kagi_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1312 | -71 | 347 | 114 | 1901 | 1 | 41 |
| ob15 | retest_native | wrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 45 | 1242 | -237 | 630 | -361 | 1947 | 1 | 41 |
| ob5 | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 80 | 1964 | -227 | -120 | 1433 | 2441 | 1 | 41 |
| ob5 | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 79 | 2181 | -420 | 239 | 1123 | 2407 | 1 | 41 |
| ob5 | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1771 | -70 | 552 | 1555 | 2673 | 1 | 41 |
| ob5 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1771 | -70 | 552 | 1555 | 2673 | 1 | 41 |
| ob5 | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 72 | 1483 | -588 | -295 | -66 | 561 | 1 | 41 |
| ob5 | reject_native | urenko_40 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 125 | 1452 | -364 | -720 | -1186 | 1708 | 1 | 41 |
| ob5 | retest | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 77 | 2171 | -115 | 238 | -314 | 2762 | 1 | 41 |
| ob5 | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 78 | 2276 | 28 | 288 | 302 | 2581 | 1 | 41 |
| open_range | break | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 209 |
| open_range | break_native | swing_pct_8 | {"n": 1, "k": 0.0} | sym15u / both | 234 | 3999 | -973 | 293 | 1639 | 4350 | 1 | 209 |
| open_range | false_break | swing_pct_8 | {"M": 3, "k": 0.5} | sym15u / both | 234 | 3833 | -796 | 831 | 1402 | 4184 | 1 | 209 |
| open_range | false_break_native | swing_atr_0.6 | {"M": 2, "k": 0.5} | sym15u / both | 233 | 3862 | -340 | 1191 | 2887 | 4260 | 1 | 209 |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 209 |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 1 | 209 |
| open_range | retest | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 209 |
| open_range | retest_native | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 2 | 209 |
| opens | break | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 211 |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 161 | 2766 | -1910 | -784 | -471 | 2936 | 2 | 211 |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 111 | 2859 | -993 | 34 | -12 | 3095 | 1 | 211 |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 125 | 2780 | -851 | -477 | -259 | 2715 | 1 | 211 |
| opens | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 211 |
| opens | reject_native | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 151 | 2916 | 760 | -1324 | -957 | 2033 | 2 | 211 |
| opens | retest | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 211 |
| opens | retest_native | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 2 | 211 |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 2 | 211 |
| prior_day | break_native | vsess_120 | {"n": 3, "k": 0.0} | sym15u / both | 91 | 2959 | -204 | -697 | -3330 | 1835 | 2 | 211 |
| prior_day | false_break | pasl_10 | {"M": 2, "k": 0.5} | sym15u / both | 115 | 2873 | -837 | 323 | -2884 | 1490 | 1 | 211 |
| prior_day | false_break_native | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 88 | 2868 | -302 | 511 | -1840 | 2689 | 2 | 211 |
| prior_day | reject | renko_10 | {"tol": 1.0, "conf": "body"} | sym30u / both | 85 | 2231 | -401 | -852 | 528 | 1653 | 2 | 211 |
| prior_day | reject_native | renko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 77 | 2665 | 149 | 475 | -2001 | 1894 | 2 | 211 |
| prior_day | retest | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 88 | 2704 | -415 | -138 | -1222 | 3080 | 1 | 211 |
| prior_day | retest_native | swing_atr_0.25 | {"M": 10, "tol": 0.5} | sym15u / both | 93 | 2940 | 75 | -924 | -980 | 2719 | 1 | 211 |
| profile_nodes | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 137 | 2489 | -45 | -739 | -7388 | 1667 | 1 | 210 |
| profile_nodes | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 146 | 2992 | -647 | 1127 | -2618 | 2123 | 1 | 210 |
| profile_nodes | false_break | renko_10 | {"M": 1, "k": 0.5} | asym10u/20u / both | 180 | 2054 | -1160 | -714 | -3668 | 2648 | 2 | 210 |
| profile_nodes | false_break_native | renko_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 145 | 2340 | -341 | 580 | -1695 | 1244 | 2 | 210 |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 202 | 2560 | -341 | -814 | -361 | 4081 | 2 | 210 |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2 | 210 |
| profile_nodes | retest | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 109 | 2447 | -490 | 89 | -3842 | 2750 | 1 | 210 |
| profile_nodes | retest_native | pnf_20 | {"M": 10, "tol": 0.5} | sym15u / both | 128 | 2802 | -508 | 830 | -3084 | 3094 | 1 | 210 |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 93 | 2285 | -957 | 2055 | -845 | 2570 | 2 | 211 |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 107 | 2219 | -494 | 117 | -111 | 3321 | 2 | 211 |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 2 | 211 |
| profile_va | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 113 | 1975 | -1229 | 386 | -282 | 2315 | 1 | 211 |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3015 | -84 | 570 | -1275 | 3231 | 1 | 211 |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1 | 211 |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 211 |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 138 | 2551 | 282 | 812 | -308 | 1772 | 1 | 211 |
| round | break | urenko_20 | {"n": 3, "k": 0.5} | sym15u / both | 290 | 4837 | -1805 | 1243 | 3655 | 5119 | 1 | 211 |
| round | break_native | mrenko_20 | {"n": 2, "k": 0.25} | sym15u / both | 292 | 3869 | -1678 | -471 | -86 | 2338 | 1 | 211 |
| round | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 419 | 4685 | -629 | -2293 | -206 | 6549 | 2 | 211 |
| round | false_break_native | urenko_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 965 | 4358 | -1829 | -1460 | 284 | 6297 | 1 | 211 |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 2 | 211 |
| round | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 313 | 4704 | -419 | 268 | -1458 | 3186 | 1 | 211 |
| round | retest | renko_14 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 302 | 4728 | -399 | 513 | -1661 | 5351 | 2 | 211 |
| round | retest_native | renko_14 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 319 | 4722 | -107 | 506 | 309 | 2985 | 2 | 211 |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 171 | 3430 | -820 | 2114 | -94 | 2764 | 1 | 209 |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 176 | 3625 | -2152 | 404 | 326 | 3669 | 1 | 209 |
| session_hl | false_break | renko_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 237 | 2956 | 1816 | 1583 | -123 | 2794 | 2 | 209 |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 173 | 3424 | -20 | -574 | 863 | 2619 | 2 | 209 |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 1 | 209 |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 1 | 209 |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 95 | 3205 | -819 | -845 | -75 | 4545 | 2 | 209 |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | 2 | 209 |
| trendline | break | lbrk_3_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 397 | 2404 | -1368 | -1341 | -1311 | 2339 | 1 | 41 |
| trendline | break_native | kagi_14 | {"n": 3, "k": 0.5} | sym15u / both | 244 | 3812 | 1332 | 2406 | 3337 | 5866 | 1 | 41 |
| trendline | false_break | kagi_40 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3067 | 348 | -1809 | 440 | 2553 | 1 | 41 |
| trendline | false_break_native | kagi_40 | {"M": 1, "k": 0.0} | sym15u / both | 245 | 2770 | 640 | -2164 | 534 | 2407 | 1 | 41 |
| trendline | reject | urenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 154 | 1991 | 1175 | -2319 | 1129 | 389 | 1 | 41 |
| trendline | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 254 | 4010 | 1369 | 1988 | 1894 | 2118 | 1 | 41 |
| trendline | retest | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 41 |
| trendline | retest_native | urenko_20 | {"M": 3, "tol": 0.0} | sym15u / both | 154 | 3496 | 392 | -2357 | 725 | 3295 | 1 | 41 |
| uw_dp | break | swing_atr_0.4 | {"n": 2, "k": 0.25} | sym15u / both | 63 | 2095 | 0 | 0 | 399 | 1949 | 1 | 211 |
| uw_dp | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 61 | 2272 | 0 | 0 | 421 | 2655 | 1 | 211 |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 56 | 1430 | 0 | 0 | 210 | 1085 | 1 | 211 |
| uw_dp | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 61 | 1448 | 0 | 0 | 28 | 1366 | 2 | 211 |
| uw_dp | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 74 | 1508 | 0 | 0 | -241 | 886 | 1 | 211 |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 92 | 2286 | 0 | 0 | -217 | 1948 | 2 | 211 |
| uw_dp | retest | urenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 56 | 1926 | 0 | 0 | 295 | 2044 | 1 | 211 |
| uw_dp | retest_native | swing_atr_0.25 | {"M": 6, "tol": 0.5} | sym15u / both | 65 | 2346 | 0 | 0 | -187 | 1520 | 1 | 211 |
| uw_ndx | break | rng_40 | {"n": 3, "k": 0.25} | sym8u / both | 95 | 2347 | 0 | -1001 | -2044 | 1016 | 2 | 210 |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 102 | 2167 | 0 | -30 | -1920 | 1473 | 2 | 210 |
| uw_ndx | false_break | renko_10 | {"M": 1, "k": 0.5} | asym20u/10u / both | 131 | 1789 | 0 | -138 | 1771 | 2103 | 2 | 210 |
| uw_ndx | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym15u / both | 110 | 1695 | 0 | -451 | 1017 | 2018 | 2 | 210 |
| uw_ndx | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 101 | 1925 | 0 | -40 | -1237 | 2405 | 2 | 210 |
| uw_ndx | reject_native | swing_atr_0.25 | {"tol": 1.0, "conf": "body"} | sym15u / both | 123 | 1867 | 0 | -44 | -84 | 927 | 1 | 210 |
| uw_ndx | retest | swing_atr_0.15 | {"M": 6, "tol": 0.5} | sym15u / both | 95 | 2055 | 0 | 271 | -781 | 2249 | 1 | 210 |
| uw_ndx | retest_native | urenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 110 | 2464 | 0 | -631 | 475 | 2424 | 1 | 210 |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 107 | 2086 | 0 | 199 | -1304 | 2295 | 2 | 210 |
| uw_qqq | break_native | renko_10 | {"n": 2, "k": 0.0} | sym8u / both | 261 | 1644 | 0 | -302 | -257 | 171 | 2 | 210 |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 129 | 1746 | 0 | 169 | -358 | 956 | 2 | 210 |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 103 | 2069 | 0 | 764 | -695 | 1273 | 1 | 210 |
| uw_qqq | reject | vol_750 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 239 | 1562 | 0 | 34 | -577 | 1228 | 2 | 210 |
| uw_qqq | reject_native | dchg_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 105 | 2076 | 0 | 175 | -871 | 3021 | 1 | 210 |
| uw_qqq | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 93 | 1917 | 0 | 437 | -582 | 1450 | 1 | 210 |
| uw_qqq | retest_native | dchg_20 | {"M": 6, "tol": 0.5} | sym15u / both | 108 | 1938 | 0 | 452 | -985 | 1145 | 1 | 210 |
| vwap | break | renko_40 | {"n": 1, "k": 0.25} | sym8u / both | 149 | 3681 | -1617 | 765 | 724 | 2951 | 2 | 210 |
| vwap | break_native | time_m_1 | {"n": 1, "k": 0.25} | sym8u / both | 178 | 3781 | -1232 | 727 | 3089 | 3780 | 2 | 210 |
| vwap | false_break | mom_40 | {"M": 1, "k": 0.0} | sym15u / both | 152 | 3221 | -789 | 1199 | 397 | 1850 | 1 | 210 |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 148 | 4046 | -392 | -617 | -202 | 3159 | 2 | 210 |
| vwap | reject | mrenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 91 | 2424 | -43 | 12 | 1717 | 1574 | 1 | 210 |
| vwap | reject_native | lbrk_3_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 141 | 2247 | 589 | -748 | -179 | 1775 | 1 | 210 |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 167 | 4103 | 315 | 215 | 2521 | 4281 | 2 | 210 |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 171 | 4078 | 605 | -156 | 1901 | 3767 | 2 | 210 |
| vwap_bands | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 267 | 4022 | -815 | -2816 | 1718 | 4334 | 1 | 209 |
| vwap_bands | break_native | cusum_56 | {"n": 3, "k": 0.5} | sym15u / both | 242 | 3923 | -2077 | -681 | 2975 | 4369 | 1 | 209 |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 209 |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 2 | 209 |
| vwap_bands | reject | wrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 270 | 3357 | -1402 | -865 | 800 | 1869 | 1 | 209 |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 232 | 4941 | -869 | 1336 | -856 | 4552 | 1 | 209 |
| vwap_bands | retest | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 238 | 4091 | -2704 | -152 | -2144 | 3461 | 2 | 209 |
| vwap_bands | retest_native | swing_atr_0.6 | {"M": 10, "tol": 0.5} | sym15u / both | 279 | 4137 | 353 | -1853 | 636 | 4160 | 1 | 209 |
| week_month | break | swing_pct_8 | {"n": 2, "k": 0.25} | sym15u / both | 54 | 1996 | -302 | -1266 | -107 | 1728 | 1 | 211 |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 51 | 1935 | -323 | -717 | -1028 | 2200 | 2 | 211 |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 211 |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 33 | 1414 | 387 | 43 | -551 | 1838 | 1 | 211 |
| week_month | reject | time_m_2 | {"tol": 0.5, "conf": "body"} | sym15u / both | 38 | 1814 | -158 | -245 | 711 | 1727 | 2 | 211 |
| week_month | reject_native | tick_8000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 72 | 1892 | -134 | -795 | -399 | 2132 | 2 | 211 |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 43 | 1765 | 87 | -540 | 870 | 1874 | 1 | 211 |
| week_month | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 38 | 1687 | -215 | -1383 | 15 | 2423 | 2 | 211 |
| zones | break | mom_14 | {"n": 3, "k": 0.5} | sym15u / both | 63 | 2369 | -404 | 426 | 270 | 3020 | 1 | 210 |
| zones | break_native | mom_10 | {"n": 3, "k": 0.5} | sym15u / both | 95 | 2794 | -344 | 462 | -516 | 3524 | 1 | 210 |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 53 | 1806 | 238 | 747 | -44 | 1799 | 2 | 210 |
| zones | false_break_native | renko_10 | {"M": 1, "k": 0.5} | sym30u / both | 106 | 1849 | -1626 | 1128 | -516 | 2138 | 2 | 210 |
| zones | reject | rng_14 | {"tol": 1.0, "conf": "body"} | sym30u / both | 133 | 3041 | 2935 | -1064 | 682 | 3212 | 2 | 210 |
| zones | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | sym30u / both | 134 | 2702 | 2260 | -2018 | 250 | 3460 | 2 | 210 |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 85 | 1789 | -304 | -1453 | -436 | 1882 | 2 | 210 |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 52 | 1806 | 541 | -739 | -371 | 2106 | 2 | 210 |

### Asia (level modules)
| module | variant (entry type / definition) | best bar row | params | bracket / side | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | pass | bar rows with data |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | break | kagi_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 485 | -56 | -17 | 715 | 994 | 1 | 41 |
| sd5 | break_native | kagi_40 | {"n": 1, "F": 0} | sym15u / both | 30 | 485 | -56 | -17 | 715 | 994 | 1 | 41 |
| sd5 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 195 | -34 | -11 | -200 | 446 | 1 | 41 |
| sd5 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 31 | 195 | -34 | -11 | -200 | 446 | 1 | 41 |
| sdx15 | break | urenko_56 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 70 | 1077 | -200 | -153 | 1318 | 1345 | 1 | 41 |
| sdx15 | lim_mid | wrenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 303 | 3630 | -249 | -670 | -1170 | 3468 | 1 | 41 |
| sdx15 | lim_prox | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 318 | 4155 | 759 | 194 | -1585 | 2577 | 1 | 41 |
| sdx15 | rej | urenko_20 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 98 | 2164 | 235 | -369 | -1160 | 1645 | 1 | 41 |
| sdx15 | rej_flow | wrenko_20 | {"d": "E", "F": 9} | sym15u / both | 111 | 2275 | 39 | -418 | -673 | 3243 | 1 | 41 |
| sdx15 | rej_native | pnf_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 41 |
| sdx15 | rej_zone | pnf_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 199 | 2499 | 143 | -843 | -1768 | 2027 | 1 | 41 |
| sdx15 | retest | pnf_28 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 44 | 546 | -90 | -274 | 367 | 375 | 1 | 41 |
| sdx3 | break | wrenko_20 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 174 | 2989 | -298 | 492 | 507 | 2803 | 1 | 41 |
| sdx3 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 461 | 3840 | -653 | -1268 | -1861 | 3838 | 1 | 41 |
| sdx3 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 1050 | 6224 | -119 | -224 | -2213 | 5021 | 1 | 41 |
| sdx3 | rej | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 305 | 3708 | -457 | -454 | -1839 | 2258 | 1 | 41 |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 117 | 2069 | -220 | -709 | -1314 | 3044 | 1 | 41 |
| sdx3 | rej_native | urenko_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 41 |
| sdx3 | rej_zone | urenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 397 | 4669 | 123 | 34 | -3034 | 1867 | 1 | 41 |
| sdx3 | retest | lbrk_3_20 | {"d": "B", "M": 6, "tol": 0.5} | sym15u / both | 80 | 2387 | -339 | -259 | 1887 | 3616 | 1 | 41 |
| sdx30 | break | kagi_56 | {"d": "E", "F": 9, "n": 1} | sym15u / long | 43 | 796 | -102 | 249 | 541 | 651 | 1 | 41 |
| sdx30 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 206 | 3133 | -150 | -817 | -949 | 1695 | 1 | 41 |
| sdx30 | lim_prox | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 232 | 3270 | -189 | -1338 | -13 | 2950 | 1 | 41 |
| sdx30 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 159 | 1658 | 62 | -1293 | -821 | 349 | 1 | 41 |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 44 | 1278 | -32 | -42 | -652 | 899 | 1 | 41 |
| sdx30 | rej_native | pnf_28 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 41 |
| sdx30 | rej_zone | pnf_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 74 | 2502 | 8 | 245 | -348 | 2369 | 1 | 41 |
| sdx5 | break | urenko_56 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 113 | 2472 | -146 | -590 | 1239 | 2914 | 1 | 41 |
| sdx5 | lim_mid | lbrk_3_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 434 | 4411 | -88 | -1705 | -1193 | 3777 | 1 | 41 |
| sdx5 | lim_prox | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 360 | 5056 | 283 | 711 | -1448 | 2414 | 1 | 41 |
| sdx5 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 258 | 5300 | -710 | -111 | -394 | 5406 | 1 | 41 |
| sdx5 | rej_flow | wrenko_10 | {"d": "E", "F": 9} | sym15u / both | 213 | 2801 | 412 | -179 | -668 | 1032 | 1 | 41 |
| sdx5 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 284 | 4619 | -598 | -24 | -1073 | 5324 | 1 | 41 |
| sdx5 | rej_zone | mrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 279 | 3304 | -209 | -1861 | 763 | 177 | 1 | 41 |
| sdx5 | retest | kagi_40 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / short | 93 | 1465 | -6 | -476 | -174 | 1868 | 1 | 41 |
| sdx60 | break | pnf_40 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 30 | 246 | -54 | 16 | 405 | -586 | 1 | 41 |
| sdx60 | lim_mid | urenko_40 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 144 | 1330 | 181 | -523 | -342 | 1028 | 1 | 41 |
| sdx60 | lim_prox | urenko_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 87 | 1502 | -62 | -1032 | -516 | 1170 | 1 | 41 |
| sdx60 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 46 | 2001 | -43 | -297 | -277 | 2024 | 1 | 41 |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | sym15u / short | 30 | 913 | 12 | -370 | -367 | 777 | 1 | 41 |
| sdx60 | rej_native | wrenko_14 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 56 | 2048 | -3 | -244 | -270 | 2246 | 1 | 41 |
| sdx60 | rej_zone | wrenko_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 64 | 1710 | 25 | -264 | -895 | 1797 | 1 | 41 |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 182 | 3218 | 348 | 613 | 1501 | 3608 | 1 | 41 |
| sdx_renko28 | lim_mid | kagi_28 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 335 | 3926 | -225 | -191 | -3870 | 3498 | 1 | 41 |
| sdx_renko28 | lim_prox | pnf_7 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 332 | 3491 | 102 | -741 | -4298 | 1272 | 1 | 41 |
| sdx_renko28 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 289 | 2322 | -347 | -2305 | -1815 | 504 | 1 | 41 |
| sdx_renko28 | rej_flow | wrenko_10 | {"d": "E", "F": 0} | sym15u / both | 105 | 2509 | -260 | -487 | -1295 | 1700 | 1 | 41 |
| sdx_renko28 | rej_native | kagi_10 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 290 | 3009 | -86 | -3096 | -4876 | 1290 | 1 | 41 |
| sdx_renko28 | rej_zone | kagi_10 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 290 | 3009 | -86 | -3096 | -4876 | 1290 | 1 | 41 |
| sdx_renko28 | retest | kagi_56 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 377 | 2189 | 230 | -226 | -1251 | 1966 | 1 | 41 |
| sdx_rng28 | break | mrenko_20 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 803 | 5407 | 129 | 1213 | -529 | 4740 | 1 | 41 |
| sdx_rng28 | lim_mid | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 358 | 3033 | 349 | -535 | 1306 | 3345 | 1 | 41 |
| sdx_rng28 | lim_prox | lbrk_3_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 361 | 2705 | 51 | -193 | -1074 | 2710 | 1 | 41 |
| sdx_rng28 | rej | frenko_40 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 180 | 4551 | 663 | 859 | -858 | 6367 | 1 | 41 |
| sdx_rng28 | rej_flow | dol_6000 | {"d": "E", "F": 0} | sym15u / both | 165 | 1758 | -160 | -423 | -740 | 2040 | 1 | 41 |
| sdx_rng28 | rej_native | wrenko_20 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 817 | 2929 | -775 | -407 | -1591 | 2117 | 1 | 41 |
| sdx_rng28 | rej_zone | urenko_20 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 325 | 2693 | -208 | -802 | -2507 | 1921 | 1 | 41 |
| sdx_rng28 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 447 | 3522 | -103 | 677 | -611 | 2695 | 1 | 41 |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 392 | 3031 | 130 | 198 | 714 | 2880 | 1 | 41 |
| sdx_vol1100 | lim_mid | wrenko_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 351 | 3043 | -308 | 140 | -2784 | 1952 | 1 | 41 |
| sdx_vol1100 | lim_prox | kagi_10 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 334 | 4466 | -175 | -58 | -998 | 5680 | 1 | 41 |
| sdx_vol1100 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 281 | 4086 | 117 | -233 | -2354 | 3347 | 1 | 41 |
| sdx_vol1100 | rej_flow | dol_6000 | {"d": "E", "F": 9} | plain60/60 / both | 204 | 2004 | -631 | 200 | -652 | 1775 | 1 | 41 |
| sdx_vol1100 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 315 | 4153 | -19 | -209 | -2233 | 3638 | 1 | 41 |
| sdx_vol1100 | rej_zone | pnf_14 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 241 | 3356 | 427 | -643 | -1132 | 2743 | 1 | 41 |
| sdx_vol1100 | retest | urenko_40 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 273 | 2414 | 61 | -321 | 464 | 2757 | 1 | 41 |
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 664 | 4358 | 1020 | 111 | 108 | 5473 | 1 | 41 |
| fib15 | break_native | lbrk_3_10 | {"n": 1, "k": 0.0} | sym15u / both | 357 | 3199 | -503 | 800 | 2149 | 1847 | 1 | 41 |
| fib15 | false_break | urenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 305 | 3531 | -251 | 204 | 302 | 3497 | 1 | 41 |
| fib15 | false_break_native | urenko_80 | {"M": 2, "k": 0.5} | sym15u / both | 246 | 3386 | -101 | -338 | 505 | 2207 | 1 | 41 |
| fib15 | pullback | frenko_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 187 | 2905 | -586 | 78 | -1531 | 2041 | 1 | 41 |
| fib15 | pullback_native | frenko_28 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 327 | 2602 | -56 | 387 | -221 | 1036 | 1 | 41 |
| fib15 | reject | urenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 583 | 3114 | 323 | -624 | 1153 | 3098 | 1 | 41 |
| fib15 | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 367 | 3684 | 770 | -1991 | 1912 | 3118 | 1 | 41 |
| fib15 | retest | frenko_28 | {"M": 6, "tol": 0.5} | sym15u / both | 240 | 3328 | 623 | 999 | -465 | 4425 | 1 | 41 |
| fib15 | retest_native | frenko_28 | {"M": 10, "tol": 0.5} | sym15u / both | 258 | 3269 | 420 | -791 | 495 | 3369 | 1 | 41 |
| fib5 | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 780 | 3710 | 255 | 1241 | -1391 | 4410 | 1 | 41 |
| fib5 | break_native | urenko_80 | {"n": 1, "k": 0.0} | plain60/60 / both | 496 | 3121 | -59 | 232 | 1286 | 2488 | 1 | 41 |
| fib5 | false_break | pnf_14 | {"M": 2, "k": 0.5} | sym15u / both | 312 | 2831 | -211 | 899 | -3174 | 3833 | 1 | 41 |
| fib5 | false_break_native | kagi_56 | {"M": 3, "k": 0.5} | sym15u / both | 298 | 3381 | 57 | 598 | -2618 | 1711 | 1 | 41 |
| fib5 | pullback | mrenko_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 217 | 3450 | -194 | -957 | 412 | 4059 | 1 | 41 |
| fib5 | pullback_native | kagi_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 613 | 3577 | -99 | 252 | -1371 | 4557 | 1 | 41 |
| fib5 | reject | urenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 248 | 3634 | 32 | -710 | -768 | 4336 | 1 | 41 |
| fib5 | reject_native | pnf_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 291 | 3481 | 593 | -1004 | -1778 | 5364 | 1 | 41 |
| fib5 | retest | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5432 | 117 | -762 | -4567 | 7004 | 1 | 41 |
| fib5 | retest_native | kagi_28 | {"M": 3, "tol": 0.0} | sym15u / both | 305 | 5432 | 117 | -762 | -4567 | 7004 | 1 | 41 |
| fib60 | break | urenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 263 | 4046 | -15 | -506 | 1369 | 4306 | 1 | 41 |
| fib60 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 556 | 4408 | -100 | 188 | -541 | 3433 | 1 | 41 |
| fib60 | false_break | lbrk_3_40 | {"M": 2, "k": 0.5} | plain60/60 / both | 430 | 2589 | -24 | 1523 | -232 | 2171 | 1 | 41 |
| fib60 | false_break_native | lbrk_3_40 | {"M": 3, "k": 0.5} | plain60/60 / both | 415 | 2559 | -102 | 1257 | -523 | 1966 | 1 | 41 |
| fib60 | pullback | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 133 | 2500 | 277 | -321 | -1857 | 3041 | 1 | 41 |
| fib60 | pullback_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 156 | 2403 | 331 | -240 | -1482 | 3044 | 1 | 41 |
| fib60 | reject | kagi_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 254 | 3600 | 321 | -1524 | -787 | 4078 | 1 | 41 |
| fib60 | reject_native | urenko_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 598 | 3269 | 101 | -14 | 853 | 3533 | 1 | 41 |
| fib60 | retest | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 303 | 2269 | 379 | -1909 | -1529 | 2945 | 1 | 41 |
| fib60 | retest_native | urenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 308 | 2705 | 324 | -1493 | -867 | 2814 | 1 | 41 |
| fibr_dev | break | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 492 | 1108 | 1598 | 3481 | 1 | 41 |
| fibr_dev | break_native | pnf_14 | {"n": 1, "k": 0.0} | sym15u / both | 314 | 3094 | 515 | 1108 | 1598 | 3481 | 1 | 41 |
| fibr_dev | false_break | pnf_14 | {"M": 3, "k": 0.5} | sym15u / both | 316 | 3799 | 772 | 931 | 1745 | 3779 | 1 | 41 |
| fibr_dev | false_break_native | pnf_14 | {"M": 1, "k": 0.0} | sym15u / both | 315 | 3556 | 1165 | 401 | 1540 | 3473 | 1 | 41 |
| fibr_dev | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 268 | 3144 | -189 | 873 | -2406 | 3760 | 1 | 41 |
| fibr_dev | reject_native | frenko_40 | {"tol": 0.5, "conf": "body"} | sym15u / both | 285 | 4083 | -588 | 684 | -1434 | 4699 | 1 | 41 |
| fibr_dev | retest | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 41 |
| fibr_dev | retest_native | urenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 271 | 3210 | 14 | -1791 | 2306 | 2232 | 1 | 41 |
| fibr_ib | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 41 |
| fibr_ib | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 119 | 967 | 2426 | 1 | 41 |
| fibr_ib | false_break | urenko_80 | {"M": 2, "k": 0.5} | sym15u / long | 31 | 987 | 109 | 245 | 994 | 2440 | 1 | 41 |
| fibr_ib | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / long | 32 | 973 | -5 | 218 | 954 | 2426 | 1 | 41 |
| fibr_ib | reject | pnf_28 | {"tol": 1.0, "conf": "body"} | sym15u / both | 32 | 624 | 386 | 146 | -104 | 606 | 1 | 41 |
| fibr_ib | reject_native | pnf_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 45 | 1206 | 460 | -101 | 173 | 929 | 1 | 41 |
| fibr_ib | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 47 | 1139 | 116 | -501 | 309 | 1475 | 1 | 41 |
| fibr_ib | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 60 | 1416 | 2 | -1461 | -161 | 2126 | 1 | 41 |
| fibr_on | break | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 41 |
| fibr_on | break_native | wrenko_14 | {"n": 1, "k": 0.0} | sym15u / both | 35 | 1099 | 45 | 789 | 149 | 1865 | 1 | 41 |
| fibr_on | false_break | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 31 | 1342 | 57 | 761 | 588 | 2157 | 1 | 41 |
| fibr_on | false_break_native | pnf_7 | {"M": 2, "k": 0.5} | sym15u / both | 43 | 1558 | 176 | 575 | 928 | 2229 | 1 | 41 |
| fibr_on | reject | kagi_112 | {"tol": 0.0, "conf": "close"} | sym15u / both | 39 | 769 | 6 | 260 | 62 | 989 | 1 | 41 |
| fibr_on | reject_native | pnf_56 | {"tol": 1.0, "conf": "body"} | sym15u / both | 37 | 1587 | -6 | 47 | -1673 | 1060 | 1 | 41 |
| fibr_on | retest | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 37 | 1166 | -61 | -3 | 830 | 1123 | 1 | 41 |
| fibr_on | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 50 | 1220 | -2 | 140 | 639 | 1292 | 1 | 41 |
| fibr_or | break | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 41 |
| fibr_or | break_native | urenko_80 | {"n": 1, "k": 0.0} | sym15u / both | 74 | 1194 | 169 | -60 | 437 | 2215 | 1 | 41 |
| fibr_or | false_break | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 41 |
| fibr_or | false_break_native | urenko_80 | {"M": 1, "k": 0.0} | sym15u / both | 73 | 1075 | 184 | 90 | 361 | 2096 | 1 | 41 |
| fibr_or | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 33 | 489 | 144 | -523 | -654 | 44 | 1 | 41 |
| fibr_or | reject_native | kagi_80 | {"tol": 1.0, "conf": "body"} | sym15u / short | 36 | 808 | 243 | -645 | -131 | 1067 | 1 | 41 |
| fibr_or | retest | urenko_80 | {"M": 6, "tol": 0.5} | sym15u / both | 44 | 1143 | 260 | -956 | -170 | 1606 | 1 | 41 |
| fibr_or | retest_native | urenko_80 | {"M": 10, "tol": 0.5} | sym15u / both | 63 | 1342 | 216 | -1025 | -198 | 1902 | 1 | 41 |
| fibr_pd | break | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 41 |
| fibr_pd | break_native | kagi_10 | {"n": 1, "k": 0.0} | plain60/60 / both | 660 | 3124 | 553 | 89 | 691 | 4139 | 1 | 41 |
| fibr_pd | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 678 | 3579 | -1005 | -279 | 981 | 5723 | 1 | 41 |
| fibr_pd | false_break_native | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 666 | 3464 | -1047 | -220 | 995 | 5358 | 1 | 41 |
| fibr_pd | reject | urenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 349 | 2746 | -87 | -674 | -1595 | 3667 | 1 | 41 |
| fibr_pd | reject_native | urenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 342 | 2899 | 228 | -466 | 1300 | 2291 | 1 | 41 |
| fibr_pd | retest | kagi_28 | {"M": 6, "tol": 0.5} | plain60/60 / both | 603 | 2661 | 78 | 584 | 477 | 2260 | 1 | 41 |
| fibr_pd | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | plain60/60 / both | 686 | 3100 | 305 | 253 | 787 | 3272 | 1 | 41 |
| piv_cama | break | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 697 | 3237 | 208 | 306 | -1672 | 2963 | 1 | 41 |
| piv_cama | break_native | pnf_10 | {"n": 3, "k": 0.5} | sym15u / both | 306 | 3386 | 269 | 1492 | 959 | 3771 | 1 | 41 |
| piv_cama | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 718 | 2761 | -500 | -98 | -1350 | 3065 | 1 | 41 |
| piv_cama | false_break_native | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 832 | 3200 | -1113 | -1440 | 84 | 4151 | 1 | 41 |
| piv_cama | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 319 | 3165 | -462 | -874 | 1496 | 3297 | 1 | 41 |
| piv_cama | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 344 | 3538 | -773 | -527 | -550 | 2854 | 1 | 41 |
| piv_cama | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 787 | 2950 | -169 | -864 | 823 | 3736 | 1 | 41 |
| piv_cama | retest_native | pnf_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 751 | 4190 | -481 | -909 | -37 | 3794 | 1 | 41 |
| piv_floor | break | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 41 |
| piv_floor | break_native | pnf_5 | {"n": 1, "k": 0.0} | plain60/60 / both | 520 | 3642 | 216 | 77 | 945 | 4099 | 1 | 41 |
| piv_floor | false_break | kagi_10 | {"M": 2, "k": 0.5} | plain60/60 / both | 552 | 3654 | -727 | -863 | 251 | 3755 | 1 | 41 |
| piv_floor | false_break_native | kagi_10 | {"M": 1, "k": 0.0} | plain60/60 / both | 553 | 3592 | -577 | -783 | 419 | 3557 | 1 | 41 |
| piv_floor | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 259 | 2195 | -719 | -1237 | -497 | 3369 | 1 | 41 |
| piv_floor | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 222 | 2515 | 703 | -945 | -1135 | 3210 | 1 | 41 |
| piv_floor | retest | kagi_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 468 | 3194 | -7 | 722 | -1698 | 3884 | 1 | 41 |
| piv_floor | retest_native | mrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 257 | 2992 | 134 | -1048 | 1326 | 4059 | 1 | 41 |
| piv_wf | break | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 41 |
| piv_wf | break_native | pnf_7 | {"n": 1, "k": 0.0} | sym15u / both | 285 | 2610 | -252 | -834 | 1910 | 3247 | 1 | 41 |
| piv_wf | false_break | frenko_28 | {"M": 2, "k": 0.5} | sym15u / both | 299 | 2465 | -1481 | -1157 | 560 | 2742 | 1 | 41 |
| piv_wf | false_break_native | wrenko_20 | {"M": 3, "k": 0.5} | sym15u / both | 288 | 2691 | -648 | -1103 | 567 | 3937 | 1 | 41 |
| piv_wf | reject | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 278 | 2564 | -131 | -855 | 521 | 3098 | 1 | 41 |
| piv_wf | reject_native | kagi_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 294 | 3050 | -355 | -1518 | -2651 | 4373 | 1 | 41 |
| piv_wf | retest | kagi_10 | {"M": 3, "tol": 0.0} | sym15u / both | 265 | 3002 | -306 | -16 | -2883 | 4150 | 1 | 41 |
| piv_wf | retest_native | mrenko_14 | {"M": 6, "tol": 0.5} | sym15u / both | 246 | 4286 | -12 | 529 | -29 | 5442 | 1 | 41 |
| swcluster | break | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1027 | -344 | -315 | -623 | 734 | 1 | 41 |
| swcluster | break_native | urenko_10 | {"n": 2, "k": 0.25} | sym15u / both | 56 | 1024 | -227 | -349 | -670 | 879 | 1 | 41 |
| swcluster | false_break | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 41 |
| swcluster | false_break_native | pnf_7 | {"M": 1, "k": 0.0} | sym15u / both | 67 | 1311 | -249 | -176 | 1393 | 2015 | 1 | 41 |
| swcluster | reject | lbrk_3_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 50 | 591 | -154 | -551 | -336 | 712 | 1 | 41 |
| swcluster | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 46 | 1097 | 102 | -253 | -33 | 902 | 1 | 41 |
| swcluster | retest | dol_350 | {"M": 10, "tol": 0.5} | sym15u / both | 50 | 1005 | -370 | 289 | 169 | 1869 | 1 | 41 |
| swcluster | retest_native | kagi_20 | {"M": 6, "tol": 0.5} | sym15u / both | 52 | 973 | -319 | 31 | 1182 | 1353 | 1 | 41 |
| swsr15 | break | urenko_28 | {"n": 3, "k": 0.5} | plain60/60 / both | 607 | 2835 | -125 | 665 | 1504 | 4520 | 1 | 41 |
| swsr15 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 639 | 2579 | 273 | 977 | -86 | 2926 | 1 | 41 |
| swsr15 | false_break | kagi_56 | {"M": 2, "k": 0.5} | sym15u / both | 283 | 2324 | -223 | -60 | -629 | 1560 | 1 | 41 |
| swsr15 | false_break_native | kagi_20 | {"M": 2, "k": 0.5} | sym15u / both | 322 | 2961 | 743 | -10 | -136 | 4162 | 1 | 41 |
| swsr15 | reject | mrenko_14 | {"tol": 0.5, "conf": "body"} | sym15u / both | 177 | 2218 | 174 | -27 | -468 | 3125 | 1 | 41 |
| swsr15 | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 754 | 3070 | 146 | 508 | -2024 | 2007 | 1 | 41 |
| swsr15 | retest | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 41 |
| swsr15 | retest_native | wrenko_10 | {"M": 3, "tol": 0.0} | sym15u / both | 264 | 2630 | -1036 | -575 | -2284 | 3617 | 1 | 41 |
| swsr5 | break | kagi_56 | {"n": 1, "k": 0.0} | sym15u / both | 306 | 3427 | -11 | 1352 | -1241 | 2548 | 1 | 41 |
| swsr5 | break_native | wrenko_20 | {"n": 3, "k": 0.5} | plain60/60 / both | 789 | 3514 | 80 | 1736 | 1316 | 4658 | 1 | 41 |
| swsr5 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 369 | 2780 | 622 | 976 | 2 | 1580 | 1 | 41 |
| swsr5 | false_break_native | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 272 | 3016 | 270 | 578 | -45 | 3124 | 1 | 41 |
| swsr5 | reject | pnf_5 | {"tol": 1.0, "conf": "body"} | sym15u / both | 228 | 4159 | 82 | 315 | 42 | 4336 | 1 | 41 |
| swsr5 | reject_native | kagi_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 899 | 3040 | 121 | -370 | 48 | 3663 | 1 | 41 |
| swsr5 | retest | frenko_40 | {"M": 6, "tol": 0.5} | sym15u / both | 261 | 4292 | -147 | -323 | -3129 | 3722 | 1 | 41 |
| swsr5 | retest_native | urenko_56 | {"M": 10, "tol": 0.5} | plain60/60 / both | 592 | 3645 | -130 | 1122 | 406 | 2944 | 1 | 41 |
| swsr60 | break | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 41 |
| swsr60 | break_native | lbrk_3_20 | {"n": 1, "k": 0.0} | plain60/60 / both | 339 | 2087 | -226 | -417 | 916 | 3678 | 1 | 41 |
| swsr60 | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 41 |
| swsr60 | false_break_native | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 359 | 3080 | 63 | -144 | 856 | 5035 | 1 | 41 |
| swsr60 | reject | frenko_40 | {"tol": 1.0, "conf": "body"} | sym15u / short | 63 | 901 | 155 | -797 | 359 | 831 | 1 | 41 |
| swsr60 | reject_native | urenko_112 | {"tol": 1.0, "conf": "body"} | sym15u / both | 145 | 1613 | 196 | 417 | -574 | 1076 | 1 | 41 |
| swsr60 | retest | vrb_700 | {"M": 10, "tol": 0.5} | plain60/60 / both | 278 | 2336 | -13 | -70 | -477 | 2897 | 1 | 41 |
| swsr60 | retest_native | urenko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 254 | 2089 | 120 | -274 | -719 | 2097 | 1 | 41 |
| stack | break | wrenko_14 | {"k": 3, "cw": 1.0} | sym15u / both | 163 | 3697 | -1113 | -75 | 53 | 4771 | 1 | 211 |
| stack | break_native | frenko_28 | {"k": 2, "cw": 0.5} | sym15u / both | 268 | 4216 | 269 | 854 | 910 | 5395 | 1 | 211 |
| stack | reject | tick_300 | {"k": 2, "cw": 2.0} | asym10u/20u / both | 186 | 2906 | 61 | 648 | 73 | 1352 | 2 | 211 |
| stack | reject_native | dol_500 | {"k": 2, "cw": 0.5} | plain60/60 / short | 404 | 2492 | -100 | -1358 | -2089 | 2951 | 1 | 211 |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 791 | 86 | 772 | 1607 | 2 | 209 |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 95 | 1824 | 841 | 86 | 772 | 1607 | 2 | 209 |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 209 |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 54 | 1020 | -630 | -597 | -345 | 292 | 1 | 209 |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 151 | 1480 | -474 | -213 | -350 | 2822 | 1 | 209 |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 97 | 1443 | 732 | 638 | 74 | 699 | 1 | 209 |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 176 | 899 | -1465 | 616 | 147 | 1417 | 1 | 209 |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 156 | 821 | -381 | -305 | -21 | 226 | 1 | 209 |
| book_walls_loose | break | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 461 | 137 | 581 | 4298 | 2 | 211 |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 191 | 3527 | 411 | 137 | 581 | 4298 | 2 | 211 |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 62 | 1856 | -61 | -317 | 372 | 986 | 1 | 211 |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 62 | 1806 | 153 | -209 | 562 | 1133 | 1 | 211 |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 329 | 3303 | -618 | -483 | -2918 | 3949 | 1 | 211 |
| book_walls_loose | reject_native | tm45 | {"tol": 0.5, "conf": "body"} | sym30u / both | 209 | 3172 | 252 | -1284 | -1029 | 2939 | 2 | 211 |
| book_walls_loose | retest | tm20 | {"M": 6, "tol": 0.5} | sym15u / both | 353 | 2344 | -963 | -496 | 59 | 3790 | 1 | 211 |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 438 | 1781 | -951 | -565 | -1164 | 2912 | 1 | 211 |
| channel | break | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 41 |
| channel | break_native | kagi_14 | {"n": 1, "k": 0.0} | plain60/60 / both | 837 | 3760 | -394 | 415 | 890 | 5034 | 1 | 41 |
| channel | false_break | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 41 |
| channel | false_break_native | pnf_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 825 | 4523 | -84 | 780 | 1351 | 6011 | 1 | 41 |
| channel | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 319 | 2451 | -40 | -904 | 1980 | 74 | 1 | 41 |
| channel | reject_native | mrenko_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 690 | 2704 | -28 | 101 | 2034 | 3732 | 1 | 41 |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 488 | 3847 | -658 | -725 | -31 | 3628 | 1 | 41 |
| channel | retest_native | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 488 | 3847 | -658 | -725 | -31 | 3628 | 1 | 41 |
| fvg15 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 191 | 4507 | -198 | 255 | 2301 | 3589 | 1 | 41 |
| fvg15 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 191 | 4507 | -198 | 255 | 2301 | 3589 | 1 | 41 |
| fvg15 | false_break | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 179 | 4460 | -421 | 153 | 1819 | 3544 | 1 | 41 |
| fvg15 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 172 | 4624 | -258 | 241 | 2280 | 3548 | 1 | 41 |
| fvg15 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 172 | 2211 | -152 | 845 | -1066 | 1952 | 1 | 41 |
| fvg15 | reject_native | mrenko_14 | {"tol": 1.0, "conf": "body"} | sym15u / both | 192 | 3238 | -531 | 176 | 1230 | 3572 | 1 | 41 |
| fvg15 | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 158 | 2861 | -10 | 344 | -1206 | 2681 | 1 | 41 |
| fvg15 | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 165 | 3408 | -517 | 640 | -449 | 2985 | 1 | 41 |
| fvg5 | break | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 450 | 3449 | 423 | 609 | -1560 | 5044 | 1 | 41 |
| fvg5 | break_native | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 461 | 3420 | 327 | 253 | -1454 | 4831 | 1 | 41 |
| fvg5 | false_break | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 333 | 2970 | -57 | -288 | -1769 | 3049 | 1 | 41 |
| fvg5 | false_break_native | lbrk_3_10 | {"M": 3, "k": 0.5} | sym15u / both | 332 | 3092 | -31 | -408 | -1857 | 3270 | 1 | 41 |
| fvg5 | reject | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 326 | 5293 | -657 | -3 | -1020 | 7490 | 1 | 41 |
| fvg5 | reject_native | mrenko_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 345 | 4619 | -963 | -126 | -1590 | 6845 | 1 | 41 |
| fvg5 | retest | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3156 | -584 | -548 | -2079 | 4493 | 1 | 41 |
| fvg5 | retest_native | wrenko_10 | {"M": 6, "tol": 0.5} | sym15u / both | 270 | 3569 | -603 | -322 | -233 | 4778 | 1 | 41 |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 140 | 2941 | 712 | 954 | 90 | 2534 | 2 | 211 |
| gaps | break_native | dib_400 | {"n": 2, "k": 0.25} | sym15u / both | 181 | 3181 | 83 | 121 | -102 | 2510 | 1 | 211 |
| gaps | false_break | kagi_14 | {"M": 3, "k": 0.5} | plain60/60 / both | 435 | 3838 | -315 | -223 | 999 | 4659 | 1 | 211 |
| gaps | false_break_native | kagi_14 | {"M": 1, "k": 0.0} | plain60/60 / both | 435 | 3828 | -358 | 225 | 1018 | 4408 | 1 | 211 |
| gaps | reject | mrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 129 | 2273 | 361 | 369 | -613 | 1685 | 1 | 211 |
| gaps | reject_native | renko_20 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 89 | 2688 | -72 | -741 | 685 | 2799 | 2 | 211 |
| gaps | retest | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 150 | 2373 | -138 | 438 | 1115 | 1777 | 1 | 211 |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 151 | 2887 | -129 | 409 | 967 | 2191 | 1 | 211 |
| mmove | break | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 575 | 3266 | -125 | -274 | 199 | 3622 | 1 | 41 |
| mmove | break_native | frenko_28 | {"n": 2, "k": 0.25} | plain60/60 / both | 581 | 2913 | -307 | -72 | 462 | 3355 | 1 | 41 |
| mmove | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 322 | 4674 | -803 | 888 | 1620 | 3258 | 1 | 41 |
| mmove | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 322 | 5031 | -813 | 1377 | 2286 | 3597 | 1 | 41 |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 274 | 2229 | -215 | -135 | -986 | 3788 | 1 | 41 |
| mmove | reject_native | urenko_20 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 494 | 2494 | -127 | -205 | -307 | 3948 | 1 | 41 |
| mmove | retest | pnf_7 | {"M": 10, "tol": 0.5} | sym15u / both | 270 | 4009 | -265 | 707 | 166 | 4154 | 1 | 41 |
| mmove | retest_native | kagi_28 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 3501 | 153 | -509 | -661 | 2363 | 1 | 41 |
| ob15 | break | mrenko_20 | {"n": 2, "k": 0.25} | plain60/60 / both | 87 | 1145 | -110 | 211 | 463 | 1243 | 1 | 41 |
| ob15 | break_native | mrenko_14 | {"n": 2, "k": 0.25} | plain60/60 / both | 91 | 1395 | 9 | -204 | 659 | 1133 | 1 | 41 |
| ob15 | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / short | 35 | 733 | -85 | -25 | 420 | 701 | 1 | 41 |
| ob15 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / short | 35 | 733 | -85 | -25 | 420 | 701 | 1 | 41 |
| ob15 | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 59 | 1016 | -445 | -109 | 212 | 1364 | 1 | 41 |
| ob15 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 79 | 1546 | -161 | -222 | 273 | 1825 | 1 | 41 |
| ob15 | retest | mrenko_10 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 | 729 | 168 | 295 | -73 | 1126 | 1 | 41 |
| ob15 | retest_native | urenko_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 79 | 942 | 14 | -160 | 421 | 1025 | 1 | 41 |
| ob5 | break | kagi_10 | {"n": 2, "k": 0.25} | sym15u / both | 145 | 1926 | -810 | -333 | 600 | 2773 | 1 | 41 |
| ob5 | break_native | kagi_56 | {"n": 3, "k": 0.5} | sym15u / both | 118 | 1866 | 238 | 603 | 530 | 2260 | 1 | 41 |
| ob5 | false_break | urenko_80 | {"M": 3, "k": 0.5} | sym15u / long | 39 | 1216 | 28 | 406 | 1050 | 1397 | 1 | 41 |
| ob5 | false_break_native | urenko_40 | {"M": 3, "k": 0.5} | sym15u / both | 115 | 1109 | -143 | 486 | 1724 | 1968 | 1 | 41 |
| ob5 | reject | kagi_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 81 | 2035 | 288 | -683 | -526 | 2219 | 1 | 41 |
| ob5 | reject_native | kagi_20 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 330 | 2437 | -94 | -408 | 247 | 3278 | 1 | 41 |
| ob5 | retest | kagi_28 | {"M": 6, "tol": 0.5} | sym15u / both | 114 | 2116 | -453 | -364 | 1873 | 1885 | 1 | 41 |
| ob5 | retest_native | mrenko_14 | {"M": 3, "tol": 0.0} | sym15u / both | 53 | 1697 | 111 | -230 | 324 | 2333 | 1 | 41 |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 210 |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 53 | 1298 | 117 | 673 | 306 | 1466 | 2 | 210 |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 210 |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 70 | 1010 | 198 | 258 | 592 | 798 | 1 | 210 |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 30 | 1749 | -167 | -524 | 629 | 1343 | 1 | 210 |
| open_range | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 58 | 1841 | -107 | -871 | 61 | 1790 | 1 | 210 |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 1729 | 78 | 85 | -517 | 1653 | 1 | 210 |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 44 | 1630 | 90 | 126 | -312 | 1681 | 1 | 210 |
| opens | break | tick_800 | {"n": 1, "k": 0.5} | asym10u/20u / both | 187 | 3057 | -72 | -628 | 803 | 3795 | 2 | 212 |
| opens | break_native | renko_10 | {"n": 2, "k": 0.25} | asym20u/10u / both | 287 | 3101 | -120 | -401 | 418 | 3462 | 2 | 212 |
| opens | false_break | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 212 |
| opens | false_break_native | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2 | 212 |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 337 | 2673 | -406 | -615 | 1004 | 2486 | 1 | 212 |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 326 | 2567 | 351 | -48 | 259 | 2256 | 1 | 212 |
| opens | retest | tm10 | {"M": 3, "tol": 0.5} | sym15u / both | 435 | 3568 | -310 | -114 | -1092 | 4604 | 2 | 212 |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1 | 212 |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 212 |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 246 | 3507 | -655 | -1228 | 1030 | 4129 | 2 | 212 |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 2 | 212 |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 2 | 212 |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 212 |
| prior_day | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 196 | 2853 | 1004 | -338 | -174 | 2975 | 2 | 212 |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 2 | 212 |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 208 | 3097 | 85 | -1821 | 1481 | 3186 | 2 | 212 |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2 | 211 |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 315 | 6822 | -337 | 673 | 881 | 6105 | 2 | 211 |
| profile_nodes | false_break | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 556 | 3365 | -801 | 527 | 801 | 3841 | 2 | 211 |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 558 | 3484 | -740 | 546 | 962 | 4423 | 2 | 211 |
| profile_nodes | reject | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 217 | 3451 | -794 | -877 | -1862 | 3671 | 2 | 211 |
| profile_nodes | reject_native | renko_10 | {"tol": 1.0, "conf": "body"} | asym20u/10u / both | 369 | 4029 | 332 | -911 | -262 | 3245 | 2 | 211 |
| profile_nodes | retest | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 296 | 4628 | -315 | 325 | 906 | 5594 | 1 | 211 |
| profile_nodes | retest_native | mrenko_10 | {"M": 10, "tol": 0.5} | sym15u / both | 295 | 4808 | -512 | 139 | 1484 | 5809 | 1 | 211 |
| profile_va | break | mrenko_14 | {"n": 3, "k": 0.5} | sym15u / both | 232 | 3734 | 98 | -1260 | -135 | 2075 | 1 | 212 |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 295 | 4390 | 441 | 1089 | 434 | 4834 | 2 | 212 |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 406 | 4140 | -236 | 556 | 105 | 4352 | 1 | 212 |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 408 | 4355 | -797 | 1115 | 377 | 4710 | 1 | 212 |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 272 | 3560 | 36 | -985 | -1281 | 2925 | 1 | 212 |
| profile_va | reject_native | rng_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 523 | 3959 | 232 | -523 | -699 | 2840 | 2 | 212 |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 278 | 3166 | -186 | 347 | -497 | 3338 | 2 | 212 |
| profile_va | retest_native | swing_pct_8 | {"M": 10, "tol": 0.5} | plain60/60 / both | 528 | 2876 | -589 | -641 | 945 | 3902 | 1 | 212 |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2 | 212 |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 2 | 212 |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 510 | 5082 | 49 | 1726 | 822 | 2815 | 2 | 212 |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 512 | 4615 | 55 | 1226 | 1172 | 2100 | 2 | 212 |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 357 | 5332 | -34 | -2185 | -928 | 2256 | 2 | 212 |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 352 | 6253 | -388 | -1954 | -762 | 2373 | 2 | 212 |
| round | retest | vsess_50 | {"M": 3, "tol": 0.0} | plain60/60 / both | 480 | 4161 | -390 | -850 | -175 | 4245 | 1 | 212 |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 746 | 4186 | -64 | -517 | -1818 | 3708 | 1 | 212 |
| session_hl | break | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 210 |
| session_hl | break_native | mom_112 | {"n": 1, "k": 0.0} | sym15u / both | 70 | 1191 | 365 | -30 | -555 | 957 | 1 | 210 |
| session_hl | false_break | mom_112 | {"M": 2, "k": 0.5} | sym15u / both | 68 | 1379 | 345 | -101 | -707 | 1114 | 1 | 210 |
| session_hl | false_break_native | mom_112 | {"M": 1, "k": 0.0} | sym15u / both | 68 | 1310 | 345 | -28 | -555 | 1077 | 1 | 210 |
| session_hl | reject | swing_pct_20 | {"tol": 1.0, "conf": "body"} | sym15u / both | 31 | 966 | 156 | 215 | 82 | 717 | 1 | 210 |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 33 | 1362 | -408 | 57 | -145 | 1310 | 2 | 210 |
| session_hl | retest | swing_atr_0.9 | {"M": 10, "tol": 0.5} | sym15u / both | 42 | 930 | 394 | -159 | 104 | 1490 | 1 | 210 |
| session_hl | retest_native | mom_80 | {"M": 6, "tol": 0.5} | plain60/60 / both | 42 | 1071 | 10 | -357 | 55 | 691 | 1 | 210 |
| trendline | break | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 281 | 4047 | -334 | -565 | -398 | 3647 | 1 | 41 |
| trendline | break_native | frenko_28 | {"n": 1, "k": 0.0} | sym15u / both | 281 | 4047 | -334 | -565 | -398 | 3647 | 1 | 41 |
| trendline | false_break | urenko_56 | {"M": 2, "k": 0.5} | sym15u / both | 224 | 2652 | 5 | 374 | -456 | 3314 | 1 | 41 |
| trendline | false_break_native | wrenko_14 | {"M": 2, "k": 0.5} | sym15u / both | 290 | 2491 | 555 | -381 | 1308 | 960 | 1 | 41 |
| trendline | reject | wrenko_10 | {"tol": 0.0, "conf": "close"} | sym15u / both | 249 | 2489 | -856 | 1637 | -467 | 1528 | 1 | 41 |
| trendline | reject_native | lbrk_3_40 | {"tol": 1.0, "conf": "body"} | sym15u / both | 164 | 3233 | -304 | 1786 | -548 | 2457 | 1 | 41 |
| trendline | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / short | 107 | 2672 | -76 | -1151 | -251 | 3477 | 1 | 41 |
| trendline | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / short | 110 | 2940 | -11 | -899 | -333 | 3003 | 1 | 41 |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 248 | 3109 | 0 | 0 | -194 | 4482 | 2 | 211 |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 321 | 3370 | 0 | 0 | -211 | 3635 | 2 | 211 |
| uw_dp | false_break | lbrk_3_20 | {"M": 1, "k": 0.0} | plain60/60 / both | 287 | 2541 | 0 | 0 | 860 | 3869 | 1 | 211 |
| uw_dp | false_break_native | lbrk_3_20 | {"M": 2, "k": 0.5} | plain60/60 / both | 284 | 2570 | 0 | 0 | 860 | 3898 | 1 | 211 |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 241 | 3076 | 0 | 0 | -185 | 3668 | 2 | 211 |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 365 | 2903 | 0 | 0 | 640 | 2809 | 1 | 211 |
| uw_dp | retest | dchg_28 | {"M": 3, "tol": 0.0} | sym15u / both | 152 | 3224 | 0 | 0 | 812 | 3434 | 1 | 211 |
| uw_dp | retest_native | dchg_14 | {"M": 10, "tol": 0.5} | plain60/60 / both | 342 | 3604 | 0 | 0 | 54 | 3859 | 1 | 211 |
| uw_ndx | break | renko_14 | {"n": 2, "k": 0.5} | sym8u / both | 331 | 2910 | 0 | -114 | 269 | 2774 | 2 | 211 |
| uw_ndx | break_native | renko_28 | {"n": 1, "k": 0.0} | sym15u / both | 184 | 2821 | 0 | 832 | 1783 | 4375 | 2 | 211 |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 282 | 2880 | 0 | 798 | -20 | 2253 | 2 | 211 |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 296 | 2751 | 0 | 605 | 329 | 2931 | 2 | 211 |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 179 | 3907 | 0 | -115 | 231 | 3626 | 1 | 211 |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 263 | 3310 | 0 | -439 | -2153 | 2322 | 1 | 211 |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 186 | 3189 | 0 | 458 | -820 | 3576 | 2 | 211 |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 197 | 3129 | 0 | 455 | -1052 | 2716 | 2 | 211 |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 275 | 3874 | 0 | 230 | -203 | 2990 | 2 | 211 |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 444 | 3333 | 0 | 825 | 798 | 2619 | 2 | 211 |
| uw_qqq | false_break | cusum_112 | {"M": 1, "k": 0.0} | sym15u / both | 189 | 2553 | 0 | -215 | 1193 | 2621 | 1 | 211 |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 228 | 2553 | 0 | -518 | 1669 | 3080 | 2 | 211 |
| uw_qqq | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 211 | 4506 | 0 | -170 | -57 | 4909 | 1 | 211 |
| uw_qqq | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 585 | 4310 | 0 | 145 | -321 | 3898 | 2 | 211 |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 257 | 2889 | 0 | -916 | -406 | 2594 | 2 | 211 |
| uw_qqq | retest_native | renko_40 | {"M": 6, "tol": 0.5} | plain60/60 / both | 252 | 2711 | 0 | -192 | 815 | 3673 | 2 | 211 |
| vwap | break | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 211 |
| vwap | break_native | pasl_14 | {"n": 1, "k": 0.0} | sym15u / both | 274 | 4766 | -317 | 672 | 719 | 6551 | 1 | 211 |
| vwap | false_break | pasl_10 | {"M": 1, "k": 0.0} | sym15u / both | 272 | 3707 | 24 | -1009 | 1272 | 5049 | 1 | 211 |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2 | 211 |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 253 | 4824 | 391 | 1335 | -496 | 4063 | 2 | 211 |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 259 | 6125 | -66 | 51 | -560 | 6208 | 2 | 211 |
| vwap | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym30u / both | 244 | 3984 | 745 | -933 | 4153 | 6617 | 2 | 211 |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2 | 211 |
| vwap_bands | break | frenko_40 | {"n": 2, "k": 0.25} | plain60/60 / both | 618 | 4055 | 470 | -88 | 753 | 4340 | 1 | 210 |
| vwap_bands | break_native | time_m_2 | {"n": 2, "k": 0.25} | sym15u / both | 309 | 4019 | -106 | -2428 | -2221 | 2246 | 1 | 210 |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 286 | 3606 | -772 | 1263 | 588 | 3677 | 2 | 210 |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 282 | 3942 | 302 | -309 | -1313 | 5176 | 1 | 210 |
| vwap_bands | reject | mom_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 315 | 4433 | 431 | -493 | -3278 | 5352 | 1 | 210 |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 627 | 4896 | 115 | 120 | 784 | 5405 | 2 | 210 |
| vwap_bands | retest | dib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 483 | 3490 | -310 | -978 | -792 | 2632 | 1 | 210 |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 359 | 4296 | -30 | 774 | 891 | 2066 | 2 | 210 |
| week_month | break | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1357 | -472 | -345 | 67 | 873 | 1 | 212 |
| week_month | break_native | frenko_28 | {"n": 2, "k": 0.25} | sym15u / both | 41 | 1508 | -384 | -405 | 191 | 1025 | 1 | 212 |
| week_month | false_break | swing_atr_0.6 | {"M": 1, "k": 0.0} | sym15u / both | 59 | 1710 | 48 | 6 | 86 | 1948 | 1 | 212 |
| week_month | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 53 | 1816 | -233 | -4 | 426 | 2452 | 1 | 212 |
| week_month | reject | mom_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 34 | 1258 | 146 | -282 | -335 | 871 | 1 | 212 |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 60 | 1233 | -161 | 407 | -240 | 443 | 1 | 212 |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 212 |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 32 | 1176 | -66 | -246 | 312 | 1474 | 1 | 212 |
| zones | break | rng_40 | {"n": 1, "k": 0.5} | sym8u / both | 199 | 3211 | 33 | 78 | 580 | 2604 | 2 | 211 |
| zones | break_native | renko_10 | {"n": 1, "k": 0.5} | sym30u / both | 215 | 3602 | -167 | -1067 | -65 | 1949 | 2 | 211 |
| zones | false_break | renko_14 | {"M": 1, "k": 0.5} | sym8u / both | 294 | 3063 | -198 | 1130 | -84 | 3122 | 2 | 211 |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 177 | 2863 | -154 | 660 | -299 | 2423 | 2 | 211 |
| zones | reject | wrenko_10 | {"tol": 0.5, "conf": "body"} | sym15u / both | 196 | 3254 | -73 | -1065 | -502 | 3105 | 1 | 211 |
| zones | reject_native | renko_10 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 278 | 3157 | -1008 | -1664 | -1608 | 2818 | 2 | 211 |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 152 | 3234 | -701 | -310 | -373 | 2927 | 2 | 211 |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 161 | 2948 | -119 | -238 | 150 | 2390 | 2 | 211 |

## LEVEL triggers: FAMILY-LEVEL rolling result (pick the best level cell of the pool every 2 weeks on the trailing 26 weeks, trade the next 2 weeks; neighbour-agreed pick), own null
Null = the same procedure on the random-entry draws available for ALL level cells at pass 1 (p1rand1, p1rand2: only 2 draws per pool, so NO LABEL, <5 draws; 5+ draws exist only for candidate cells). Shifted label = pick lagged 2/3/5 weeks (mean). Year flags vs the pooled mean: AMBER 15-30% worse, RED >30% worse (standing rule). pnf = point-and-figure bars (post-reversal entries, see notice 1); "without pnf" = Renko/Kagi/etc. price bars only.
### NYAM
| pool (level sub-family | bar set) | cells | OOS pts/wk (1 lot, $4.84 incl) | persistence | last 6M pts/wk | by year | year flags | null draws | null mean | excess | shifted-label mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| SWING S/R | ALL bars | 23588 | +55.3 | 0.64 | +144.4 | {"2023": 50.4, "2024": 17.2, "2025": 49.7, "2026": 108.5} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -6.2 | +61.5 | +34.1 |
| SWING S/R | PRICE bars without pnf | 15524 | +46.4 | 0.63 | +156.0 | {"2023": 50.4, "2024": -24.6, "2025": 57.9, "2026": 115.3} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -8.8 | +55.2 | +23.0 |
| STACK | PRICE bars without pnf | 11252 | +43.3 | 0.56 | +151.1 | {"2023": -70.2, "2024": -2.5, "2025": 56.9, "2026": 117.3} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +10.1 | +33.1 | +37.1 |
| SWING S/R | PRICE bars | 20132 | +42.9 | 0.63 | +144.4 | {"2023": 50.4, "2024": 9.0, "2025": 19.3, "2026": 108.5} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +9.0 | +33.9 | +24.7 |
| PIVOT | PRICE bars without pnf | 11664 | +41.8 | 0.60 | +96.3 | {"2023": 13.6, "2024": 22.6, "2025": 78.6, "2026": 29.9} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +2.1 | +39.7 | +8.7 |
| FIB (fib/fibr) | PRICE bars | 43092 | +40.3 | 0.59 | -147.9 | {"2023": 3.4, "2024": 64.4, "2025": 99.6, "2026": -46.3} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -17.5 | +57.9 | +22.1 |
| PIVOT | PRICE bars | 15120 | +40.1 | 0.58 | +115.1 | {"2023": 10.7, "2024": 17.5, "2025": 80.4, "2026": 28.5} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -3.0 | +43.1 | +26.1 |
| SD (sd/sdx/zones) | INFORMATION bars | 14150 | +40.0 | 0.59 | +28.7 | {"2023": -13.7, "2024": 31.6, "2025": 61.4, "2026": 41.7} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -5.1 | +45.1 | +1.9 |
| FIB (fib/fibr) | INFORMATION bars | 3780 | +39.2 | 0.56 | +18.0 | {"2023": -16.8, "2024": -39.3, "2025": 134.8, "2026": 36.7} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -48.2 | +87.3 | +24.7 |
| PIVOT | ALL bars | 17712 | +39.1 | 0.60 | +115.1 | {"2023": -69.1, "2024": 17.5, "2025": 57.1, "2026": 77.9} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -4.8 | +43.9 | +35.5 |
| ALL LEVEL (structure modules above) | pnf only | 39878 | +38.1 | 0.56 | +30.6 | {"2023": 26.2, "2024": 60.8, "2025": -10.1, "2026": 72.3} | {"2023": "ok", "2024": "ok", "2025": "AMBER", "2026": "ok"} | 2 | -29.2 | +67.4 | +40.7 |
| SD (sd/sdx/zones) | PRICE bars without pnf | 62696 | +38.1 | 0.57 | -26.8 | {"2023": 20.7, "2024": 30.9, "2025": 67.1, "2026": 17.8} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -7.7 | +45.7 | +35.3 |
| SWING S/R | pnf only | 4608 | +37.3 | 0.56 | +120.0 | {"2023": -46.8, "2024": 28.1, "2025": 55.8, "2026": 53.1} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +17.0 | +20.3 | +18.4 |
| STACK | ALL bars | 27932 | +36.4 | 0.57 | +95.0 | {"2023": -70.2, "2024": -1.8, "2025": 72.8, "2026": 72.4} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -3.1 | +39.5 | +25.9 |
| STACK | PRICE bars | 11828 | +35.4 | 0.54 | +151.1 | {"2023": -70.2, "2024": -27.1, "2025": 56.9, "2026": 117.3} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +8.4 | +26.9 | +34.2 |
| STACK | INFORMATION bars | 3288 | +34.8 | 0.56 | +18.7 | {"2023": 24.9, "2024": 20.9, "2025": 73.9, "2026": 8.3} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -13.4 | +48.2 | +18.5 |
| SD (sd/sdx/zones) | ALL bars | 120964 | +31.8 | 0.57 | -26.8 | {"2023": -26.0, "2024": 43.5, "2025": 55.2, "2026": 8.6} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +18.6 | +13.1 | +40.0 |
| SD (sd/sdx/zones) | PRICE bars | 74898 | +27.9 | 0.56 | -26.8 | {"2023": -11.2, "2024": 25.8, "2025": 57.0, "2026": 8.6} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +11.0 | +17.0 | +38.2 |
| ALL LEVEL (structure modules above) | INFORMATION bars | 37058 | +26.5 | 0.57 | -35.1 | {"2023": 13.5, "2024": 5.1, "2025": 75.0, "2026": -1.4} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -22.8 | +49.2 | +21.3 |
| TREND/CHANNEL/MMOVE | pnf only | 3456 | +24.6 | 0.47 | -85.7 | {"2023": 64.1, "2024": 22.5, "2025": 61.9, "2026": -29.7} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -21.2 | +45.7 | +10.2 |
| ALL LEVEL (structure modules above) | TIME bars | 17442 | +21.6 | 0.51 | +0.4 | {"2023": -75.3, "2024": -11.0, "2025": 82.3, "2026": 19.1} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -7.0 | +28.6 | +9.9 |
| TREND/CHANNEL/MMOVE | PRICE bars | 15120 | +17.8 | 0.49 | -80.4 | {"2023": 53.0, "2024": 38.0, "2025": 51.5, "2026": -57.1} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -24.3 | +42.1 | +15.9 |
| PIVOT | pnf only | 3456 | +15.3 | 0.59 | +69.0 | {"2023": 35.7, "2024": 34.8, "2025": -12.6, "2026": 18.6} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -11.4 | +26.6 | +30.9 |
| ALL LEVEL (structure modules above) | PRICE bars | 227266 | +14.3 | 0.47 | -42.2 | {"2023": 3.7, "2024": 24.1, "2025": 50.2, "2026": -36.2} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -21.6 | +35.9 | -1.7 |

### London
| pool (level sub-family | bar set) | cells | OOS pts/wk (1 lot, $4.84 incl) | persistence | last 6M pts/wk | by year | year flags | null draws | null mean | excess | shifted-label mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL LEVEL (structure modules above) | ALL bars | 338507 | +36.1 | 0.65 | +37.4 | {"2023": 18.2, "2024": 18.0, "2025": 56.1, "2026": 39.7} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -2.2 | +38.3 | -6.3 |
| ALL LEVEL (structure modules above) | PRICE bars | 217761 | +33.5 | 0.65 | +23.8 | {"2023": 18.2, "2024": 23.6, "2025": 60.4, "2026": 18.2} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -1.8 | +35.3 | +0.2 |
| SD (sd/sdx/zones) | ALL bars | 119810 | +24.6 | 0.69 | +5.4 | {"2023": 49.7, "2024": 20.9, "2025": 24.7, "2026": 20.8} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +6.4 | +18.2 | -11.1 |
| ALL LEVEL (structure modules above) | PRICE bars without pnf | 179099 | +23.2 | 0.65 | +23.8 | {"2023": 28.9, "2024": 14.1, "2025": 19.9, "2026": 36.2} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +2.2 | +21.1 | -10.6 |
| SD (sd/sdx/zones) | PRICE bars | 74378 | +18.9 | 0.68 | -8.2 | {"2023": 49.7, "2024": 21.4, "2025": 24.7, "2026": -0.7} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +15.5 | +3.4 | -5.6 |
| SD (sd/sdx/zones) | PRICE bars without pnf | 62206 | +16.6 | 0.68 | -36.0 | {"2023": 49.7, "2024": 10.0, "2025": 29.9, "2026": -1.9} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +18.1 | -1.5 | -17.0 |
| FIB (fib/fibr) | INFORMATION bars | 2482 | +14.1 | 0.51 | +71.3 | {"2023": -2.1, "2024": 16.6, "2025": 20.7, "2026": 8.4} | {"2023": "AMBER", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +7.6 | +6.5 | -4.3 |
| STACK | ACTIVITY bars | 9576 | +13.0 | 0.49 | +24.9 | {"2023": -32.3, "2024": 5.3, "2025": -1.6, "2026": 53.6} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -0.3 | +13.3 | +5.4 |
| FIB (fib/fibr) | pnf only | 8634 | +11.3 | 0.51 | +11.8 | {"2023": -11.6, "2024": 18.9, "2025": -15.7, "2026": 41.5} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -25.6 | +36.9 | +10.4 |
| STACK | pnf only | 576 | +11.1 | 0.46 | +71.6 | {"2023": -35.4, "2024": 16.5, "2025": -14.8, "2026": 50.1} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -4.3 | +15.4 | -10.0 |
| TREND/CHANNEL/MMOVE | PRICE bars | 15120 | +10.6 | 0.52 | +23.8 | {"2023": -47.9, "2024": 20.9, "2025": -3.5, "2026": 33.6} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -10.6 | +21.2 | +15.5 |
| TREND/CHANNEL/MMOVE | PRICE bars without pnf | 11664 | +10.1 | 0.47 | +23.8 | {"2023": -28.1, "2024": 18.4, "2025": -11.2, "2026": 37.6} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -12.3 | +22.4 | +25.8 |
| TREND/CHANNEL/MMOVE | ALL bars | 17710 | +9.8 | 0.52 | +19.9 | {"2023": -47.9, "2024": 16.8, "2025": 0.1, "2026": 31.3} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -16.2 | +26.0 | +17.3 |
| ALL LEVEL (structure modules above) | INFORMATION bars | 35106 | +7.1 | 0.51 | -11.9 | {"2023": -8.3, "2024": 5.9, "2025": 8.1, "2026": 12.3} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +7.8 | -0.7 | -4.5 |
| TREND/CHANNEL/MMOVE | pnf only | 3456 | +6.9 | 0.48 | +50.1 | {"2023": 16.1, "2024": -29.8, "2025": 7.5, "2026": 46.6} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +19.0 | -12.1 | +4.9 |
| GAP/FVG/OB | pnf only | 5760 | +6.5 | 0.56 | +13.6 | {"2023": 56.6, "2024": 2.4, "2025": -11.3, "2026": 16.4} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -17.8 | +24.3 | +4.5 |
| ALL LEVEL (structure modules above) | pnf only | 38662 | +5.2 | 0.53 | -43.7 | {"2023": 13.3, "2024": 36.6, "2025": 3.4, "2026": -32.3} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -18.5 | +23.7 | +5.9 |
| SD (sd/sdx/zones) | INFORMATION bars | 13606 | +4.9 | 0.52 | +55.0 | {"2023": -9.2, "2024": 27.9, "2025": -70.0, "2026": 70.7} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -8.1 | +13.0 | +2.1 |
| TREND/CHANNEL/MMOVE | INFORMATION bars | 1294 | +4.8 | 0.47 | +24.5 | {"2023": -20.7, "2024": -34.5, "2025": 57.5, "2026": -2.8} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} | 2 | +1.4 | +3.4 | +12.2 |
| STACK | INFORMATION bars | 3248 | +2.8 | 0.56 | -19.7 | {"2023": 12.1, "2024": -15.5, "2025": 19.9, "2026": 1.3} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -5.3 | +8.1 | -20.6 |
| STACK | ALL bars | 27883 | +2.7 | 0.46 | -10.0 | {"2023": -0.1, "2024": 2.2, "2025": -1.6, "2026": 9.3} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -6.4 | +9.1 | -8.0 |
| TREND/CHANNEL/MMOVE | ACTIVITY bars | 1296 | +1.4 | 0.44 | +68.3 | {"2023": -37.7, "2024": -3.9, "2025": -12.4, "2026": 36.5} | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | +0.4 | +1.1 | +7.3 |
| SD (sd/sdx/zones) | pnf only | 12172 | -0.7 | 0.53 | +5.1 | {"2023": 29.5, "2024": 33.1, "2025": -36.0, "2026": -8.7} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} | 2 | -6.1 | +5.3 | +3.1 |
| SWING S/R | INFORMATION bars | 1716 | -1.7 | 0.52 | +9.2 | {"2023": -29.9, "2024": 22.4, "2025": -33.3, "2026": 16.1} | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -5.9 | +4.3 | -8.5 |

### NYPM
| pool (level sub-family | bar set) | cells | OOS pts/wk (1 lot, $4.84 incl) | persistence | last 6M pts/wk | by year | year flags | null draws | null mean | excess | shifted-label mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| SD (sd/sdx/zones) | INFORMATION bars | 13996 | +30.3 | 0.58 | +1.7 | {"2023": -20.0, "2024": 14.2, "2025": 42.9, "2026": 50.6} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -17.7 | +48.1 | +29.7 |
| ALL LEVEL (structure modules above) | ACTIVITY bars | 68392 | +25.6 | 0.54 | +16.4 | {"2023": 40.2, "2024": -22.6, "2025": 94.4, "2026": -3.5} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +9.0 | +16.6 | +18.7 |
| GAP/FVG/OB | PRICE bars | 46916 | +23.1 | 0.56 | -49.0 | {"2023": 19.1, "2024": 23.3, "2025": 61.3, "2026": -21.1} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | +19.9 | +3.2 | +13.3 |
| TREND/CHANNEL/MMOVE | ALL bars | 17712 | +19.7 | 0.51 | +13.1 | {"2023": -72.7, "2024": 10.5, "2025": 53.0, "2026": 20.6} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -22.3 | +42.0 | +16.1 |
| GAP/FVG/OB | INFORMATION bars | 11516 | +18.3 | 0.54 | -21.4 | {"2023": -14.5, "2024": 24.4, "2025": 44.0, "2026": -8.8} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -1.5 | +19.9 | +1.4 |
| SD (sd/sdx/zones) | ACTIVITY bars | 26290 | +17.1 | 0.47 | +39.8 | {"2023": 31.1, "2024": -27.7, "2025": 82.8, "2026": -12.1} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} | 2 | -38.2 | +55.3 | +16.5 |
| GAP/FVG/OB | ALL bars | 91444 | +17.0 | 0.54 | -49.0 | {"2023": 19.1, "2024": 14.6, "2025": 61.3, "2026": -33.2} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | +18.2 | -1.2 | +10.6 |
| ALL LEVEL (structure modules above) | pnf only | 40000 | +16.7 | 0.53 | +73.0 | {"2023": 18.0, "2024": -17.1, "2025": 37.8, "2026": 31.2} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +1.0 | +15.7 | +10.2 |
| ALL LEVEL (structure modules above) | TIME bars | 17442 | +15.6 | 0.52 | +28.1 | {"2023": 26.1, "2024": 43.3, "2025": -17.4, "2026": 18.5} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | +12.9 | +2.8 | +1.5 |
| TREND/CHANNEL/MMOVE | PRICE bars | 15120 | +15.3 | 0.48 | +13.1 | {"2023": -44.7, "2024": -10.2, "2025": 52.4, "2026": 20.6} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -16.0 | +31.3 | +15.2 |
| TREND/CHANNEL/MMOVE | pnf only | 3456 | +14.9 | 0.54 | +70.2 | {"2023": -93.4, "2024": 22.5, "2025": 8.5, "2026": 48.0} | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -9.3 | +24.3 | +22.4 |
| GAP/FVG/OB | PRICE bars without pnf | 41164 | +12.9 | 0.54 | -52.2 | {"2023": 19.1, "2024": 26.7, "2025": 61.3, "2026": -62.8} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | +13.6 | -0.7 | +11.2 |
| STACK | TIME bars | 3240 | +11.9 | 0.49 | +6.7 | {"2023": 16.4, "2024": 24.3, "2025": -1.5, "2026": 11.6} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +9.5 | +2.4 | +4.8 |
| TREND/CHANNEL/MMOVE | INFORMATION bars | 1296 | +11.4 | 0.59 | -63.6 | {"2023": 22.9, "2024": 25.8, "2025": 18.4, "2026": -17.6} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -6.5 | +17.8 | +1.3 |
| SD (sd/sdx/zones) | ALL bars | 120695 | +9.5 | 0.58 | -43.5 | {"2023": 72.5, "2024": -24.3, "2025": 34.2, "2026": 0.0} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -6.4 | +15.8 | +5.9 |
| SD (sd/sdx/zones) | PRICE bars | 74793 | +8.3 | 0.57 | -43.5 | {"2023": 72.5, "2024": 5.0, "2025": 6.0, "2026": -5.4} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -6.5 | +14.8 | -9.8 |
| TREND/CHANNEL/MMOVE | ACTIVITY bars | 1296 | +7.0 | 0.53 | -12.2 | {"2023": -20.2, "2024": -16.9, "2025": 12.1, "2026": 37.9} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -3.2 | +10.2 | -7.4 |
| FIB (fib/fibr) | INFORMATION bars | 3780 | +5.8 | 0.51 | -96.1 | {"2023": -48.9, "2024": -11.0, "2025": 83.5, "2026": -48.8} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} | 2 | +7.6 | -1.8 | +26.6 |
| FIB (fib/fibr) | ALL bars | 51656 | +2.2 | 0.51 | +31.7 | {"2023": 84.0, "2024": 3.7, "2025": 0.8, "2026": -24.0} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -10.6 | +12.8 | +9.4 |
| FIB (fib/fibr) | PRICE bars without pnf | 34016 | +1.0 | 0.52 | +31.7 | {"2023": 84.0, "2024": 3.7, "2025": -25.0, "2026": 2.1} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -19.0 | +20.0 | +1.9 |
| SD (sd/sdx/zones) | pnf only | 12074 | +0.2 | 0.53 | +31.8 | {"2023": 8.1, "2024": -16.7, "2025": -7.1, "2026": 26.2} | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | +1.4 | -1.2 | -3.0 |
| TREND/CHANNEL/MMOVE | PRICE bars without pnf | 11664 | -1.5 | 0.46 | -86.4 | {"2023": -44.7, "2024": -6.2, "2025": 46.0, "2026": -38.1} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} | 2 | -6.2 | +4.7 | +3.5 |
| SD (sd/sdx/zones) | PRICE bars without pnf | 62719 | -2.6 | 0.54 | -41.4 | {"2023": 72.5, "2024": 5.0, "2025": -31.9, "2026": -0.8} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} | 2 | -1.2 | -1.3 | -18.0 |
| PIVOT | ACTIVITY bars | 1296 | -2.9 | 0.51 | -3.0 | {"2023": 39.6, "2024": 32.8, "2025": -35.6, "2026": -20.1} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} | 2 | -11.0 | +8.0 | -3.4 |

### Asia
| pool (level sub-family | bar set) | cells | OOS pts/wk (1 lot, $4.84 incl) | persistence | last 6M pts/wk | by year | year flags | null draws | null mean | excess | shifted-label mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PIVOT | ALL bars | 17710 | +30.1 | 0.65 | +87.0 | {"2023": 15.0, "2024": 35.9, "2025": 8.1, "2026": 54.1} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -14.0 | +44.1 | +14.8 |
| PIVOT | PRICE bars without pnf | 11664 | +29.6 | 0.63 | +87.0 | {"2023": -3.8, "2024": 34.9, "2025": 8.0, "2026": 59.6} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -19.9 | +49.6 | +20.2 |
| PIVOT | PRICE bars | 15120 | +29.5 | 0.67 | +87.0 | {"2023": 16.3, "2024": 35.9, "2025": 5.7, "2026": 54.1} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -22.3 | +51.7 | +14.5 |
| SWING S/R | pnf only | 4608 | +20.8 | 0.56 | +17.0 | {"2023": 14.6, "2024": 5.6, "2025": 28.5, "2026": 31.6} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -20.6 | +41.4 | +3.3 |
| TREND/CHANNEL/MMOVE | INFORMATION bars | 1288 | +19.5 | 0.58 | +47.2 | {"2023": 1.7, "2024": 20.6, "2025": 2.1, "2026": 44.4} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | +1.8 | +17.7 | +7.7 |
| SWING S/R | INFORMATION bars | 1714 | +17.1 | 0.59 | +61.8 | {"2023": 7.1, "2024": 9.0, "2025": -1.0, "2026": 51.4} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -11.1 | +28.3 | +20.1 |
| PIVOT | pnf only | 3456 | +14.1 | 0.54 | +36.3 | {"2023": 26.3, "2024": -0.3, "2025": 16.7, "2026": 24.1} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} | 2 | -24.3 | +38.3 | -7.2 |
| SD (sd/sdx/zones) | pnf only | 11894 | +13.5 | 0.52 | +15.8 | {"2023": 14.1, "2024": 21.5, "2025": 20.4, "2026": -4.4} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | +5.0 | +8.5 | +8.0 |
| GAP/FVG/OB | ACTIVITY bars | 24426 | +12.4 | 0.52 | -21.2 | {"2023": 12.6, "2024": -7.7, "2025": 22.0, "2026": 24.8} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +17.2 | -4.7 | +17.8 |
| ALL LEVEL (structure modules above) | TIME bars | 20748 | +8.4 | 0.58 | +37.6 | {"2023": 11.6, "2024": 2.3, "2025": -3.6, "2026": 29.0} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -10.8 | +19.2 | +6.3 |
| GAP/FVG/OB | PRICE bars | 47052 | +6.5 | 0.49 | +11.1 | {"2023": 27.6, "2024": -5.1, "2025": -22.3, "2026": 47.4} | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | +1.3 | +5.2 | +26.5 |
| GAP/FVG/OB | ALL bars | 92502 | +6.0 | 0.48 | +2.4 | {"2023": 31.9, "2024": -9.7, "2025": -16.0, "2026": 42.2} | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | +6.9 | -0.9 | +22.7 |
| STACK | TIME bars | 3288 | +4.7 | 0.53 | -24.2 | {"2023": 21.6, "2024": 6.6, "2025": 26.6, "2026": -28.8} | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} | 2 | -15.8 | +20.5 | +2.4 |
| STACK | INFORMATION bars | 3186 | +4.3 | 0.51 | -1.1 | {"2023": 17.1, "2024": -14.2, "2025": 10.8, "2026": 14.4} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | +3.8 | +0.5 | -1.7 |
| TREND/CHANNEL/MMOVE | pnf only | 3456 | +4.1 | 0.47 | +32.2 | {"2023": 9.4, "2024": 3.6, "2025": -7.2, "2026": 16.2} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | +4.7 | -0.7 | +12.9 |
| GAP/FVG/OB | PRICE bars without pnf | 41292 | +3.7 | 0.48 | +11.1 | {"2023": 27.6, "2024": -20.9, "2025": -17.9, "2026": 50.8} | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | +7.9 | -4.2 | +28.8 |
| FIB (fib/fibr) | INFORMATION bars | 3778 | +3.2 | 0.51 | +7.0 | {"2023": -5.9, "2024": -16.7, "2025": -2.0, "2026": 36.0} | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | -13.7 | +17.0 | -0.5 |
| GAP/FVG/OB | INFORMATION bars | 11304 | +3.1 | 0.48 | +2.8 | {"2023": 24.7, "2024": 2.0, "2025": -30.7, "2026": 37.6} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -31.3 | +34.4 | -0.5 |
| ALL LEVEL (structure modules above) | PRICE bars | 227793 | +2.9 | 0.52 | -4.6 | {"2023": 44.4, "2024": 0.0, "2025": -9.8, "2026": 7.9} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | -13.4 | +16.3 | -12.7 |
| GAP/FVG/OB | TIME bars | 9720 | +2.7 | 0.52 | +26.7 | {"2023": 11.6, "2024": 15.5, "2025": -17.0, "2026": 8.1} | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "ok"} | 2 | +1.3 | +1.4 | -8.1 |
| GAP/FVG/OB | pnf only | 5760 | +2.6 | 0.54 | -17.7 | {"2023": -14.1, "2024": -16.0, "2025": 7.4, "2026": 24.2} | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} | 2 | -25.3 | +27.9 | +12.6 |
| SD (sd/sdx/zones) | TIME bars | 7740 | +2.2 | 0.56 | +51.8 | {"2023": -2.2, "2024": -7.6, "2025": -16.4, "2026": 37.4} | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | -13.7 | +15.9 | +10.8 |
| ALL LEVEL (structure modules above) | PRICE bars without pnf | 187963 | +0.7 | 0.54 | -19.5 | {"2023": 44.4, "2024": -3.9, "2025": -23.6, "2026": 20.9} | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} | 2 | -2.9 | +3.5 | -6.0 |
| ALL LEVEL (structure modules above) | ALL bars | 352567 | -0.1 | 0.49 | -40.7 | {"2023": 44.4, "2024": -1.4, "2025": 0.5, "2026": -13.4} | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} | 2 | -13.3 | +13.2 | -23.2 |

## LEVEL triggers on NON-reversal bars (order 1324Z): best cell per (module, variant) over time / activity / information / plain-range rows only, beside the best reversal-bar row (Kagi, P&F, Renko family, swing, dchg, trend, mom, HA)
Columns: bracket = bracket code and stop/target in points after the 10..120 clip (median over the row's L6M-era bars; wide event bars clip to 120/120). "plain 60/60" = the SAME signals (same bar row, params, side) on a fixed 60/60 bracket: L6M and 2023 / 2024 / 2025 (n/a where the cell was not run on plain 60/60 at this pass level). "Reversal-bar best" = best cell of the same (module, variant) on Kagi/P&F/Renko-type rows: row, L6M, 2023 / 2024 / 2025 (last-26-week pick, >= 30 trades). In-sample best-of-many picks.
### NYAM - supply/demand modules by definition (variant = entry type)
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd15 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 60 / 60 | 33 | -234 | 67 | -448 | -269 | -2 | -234 (67 / -448 / -269) | no reversal row has trades |
| sd15 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 60 / 60 | 33 | -234 | 67 | -448 | -269 | -2 | -234 (67 / -448 / -269) | no reversal row has trades |
| sd5 | break | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 60 / 60 | 30 | -93 | -177 | 306 | -382 | -313 | -93 (-177 / 306 / -382) | wrenko_10, -218 (-115 / 358 / -542) |
| sd5 | break_native | dol_350 | {"n": 2, "F": 2} | plain60/60 / both | 60 / 60 | 30 | -93 | -177 | 306 | -382 | -313 | -93 (-177 / 306 / -382) | wrenko_10, -218 (-115 / 358 / -542) |
| sd5 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 120 / 120 | 34 | 316 | 265 | -707 | -255 | 653 | 143 (81 / -477 / -466) | no reversal row has trades |
| sd5 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | sym15u / both | 120 / 120 | 34 | 316 | 265 | -707 | -255 | 653 | 143 (81 / -477 / -466) | no reversal row has trades |
| sdx15 | break | dol_6000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 137 | 1367 | 139 | -220 | 2842 | 1927 | 373 (-694 / -656 / 726) | kagi_20, 2399 (-85 / 715 / 2594) |
| sdx15 | lim_mid | dol_500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 120 | 2883 | -399 | -1339 | -3208 | 2381 | 1610 (-363 / -938 / -1191) | mrenko_20, 2976 (-2286 / -2403 / -427) |
| sdx15 | lim_prox | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 129 | 2822 | -660 | -1220 | -1966 | 2550 | 1573 (-598 / -1093 / -585) | kagi_56, 3815 (30 / -593 / -1777) |
| sdx15 | rej | dol_500 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 174 | 947 | -982 | -714 | -759 | 1597 | 947 (-982 / -714 / -759) | frenko_40, 2107 (-1412 / -869 / 341) |
| sdx15 | rej_flow | dol_350 | {"d": "A", "F": 0} | sym15u / long | 120 / 120 | 32 | 888 | -425 | 309 | -321 | 964 | 47 (-547 / 159 / 299) | wrenko_10, 1194 (-483 / 1191 / -1486) |
| sdx15 | rej_native | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 120 / 120 | 156 | 1431 | -765 | -281 | -1427 | 1440 | 1135 (-295 / 571 / -830) | kagi_56, 2039 (-160 / -2368 / -1749) |
| sdx15 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 120 / 120 | 156 | 1431 | -765 | -281 | -1427 | 1440 | 1135 (-295 / 571 / -830) | lbrk_3_10, 1956 (-1553 / -1374 / -943) |
| sdx15 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 50 | 711 | -351 | 1011 | 2192 | 1166 | 181 (-528 / -216 / 438) | kagi_28, 1671 (1303 / -626 / 3804) |
| sdx3 | break | dol_350 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 260 | 1287 | 1807 | 600 | 4413 | 989 | -306 (1168 / 1895 / 1657) | kagi_20, 3483 (1458 / 3578 / 5139) |
| sdx3 | lim_mid | dol_500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 344 | 1609 | -451 | -1100 | -3236 | 270 | 327 (-1311 / -3295 / -2282) | pnf_56, 3365 (26 / 2134 / 1935) |
| sdx3 | lim_prox | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / short | 60 / 60 | 368 | 1998 | -1233 | -1199 | -649 | 1330 | 1998 (-1233 / -1199 / -649) | kagi_80, 3509 (1324 / 128 / -1502) |
| sdx3 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 411 | 1831 | -910 | -1044 | -6843 | 1590 | 1707 (-593 / -4280 / -6764) | mrenko_10, 3002 (-2715 / -1978 / -5508) |
| sdx3 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / long | 120 / 120 | 149 | 2221 | 155 | -634 | -2925 | 2569 | 455 (401 / -918 / -1926) | wrenko_10, 3037 (6 / 1057 / -3441) |
| sdx3 | rej_native | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 649 | 2040 | -278 | -1856 | -3694 | 811 | 2040 (-278 / -1856 / -3694) | mrenko_20, 3139 (271 / -969 / -2462) |
| sdx3 | rej_zone | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 120 / 120 | 263 | 1695 | 2 | -371 | -2197 | 3744 | -217 (-422 / -1959 / -6179) | mrenko_20, 3139 (271 / -969 / -2462) |
| sdx3 | retest | dol_350 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 215 | 1369 | 1289 | 1891 | 5124 | 1384 | 209 (457 / 1011 / 2013) | kagi_14, 2392 (2042 / 2685 / 4969) |
| sdx30 | break | dol_6000 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 46 | 719 | 783 | 259 | 882 | 1271 | 431 (96 / 619 / -23) | pnf_56, 1933 (-372 / 1333 / 866) |
| sdx30 | lim_mid | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 120 / 120 | 36 | 1195 | -66 | -555 | -174 | 943 | 465 (-61 / -715 / -785) | wrenko_20, 1565 (12 / -897 / 111) |
| sdx30 | lim_prox | dol_500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / short | 120 / 120 | 42 | 1220 | 31 | -223 | 190 | 689 | 695 (63 / -232 / -92) | pnf_56, 2308 (-245 / -373 / 1505) |
| sdx30 | rej | vrb_70000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 52 | 1129 | 167 | -1005 | 780 | 954 | 429 (172 / -1050 / 545) | wrenko_14, 1261 (-467 / -838 / -1738) |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 120 / 120 | 146 | 1480 | -676 | -2116 | -2930 | 1823 | 180 (-424 / -1913 / -2150) | wrenko_14, 1001 (73 / -979 / -1302) |
| sdx30 | rej_native | vrb_70000 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 57 | 1100 | -154 | -1645 | -596 | 695 | 903 (-292 / -694 / -518) | kagi_56, 1748 (-1904 / -3586 / -1161) |
| sdx30 | rej_zone | vrb_40000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 102 | 1030 | -924 | -732 | -179 | 134 | 658 (-1113 / 488 / 196) | kagi_56, 1748 (-1904 / -3586 / -1161) |
| sdx30 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 31 | 196 | 190 | 438 | 263 | 344 | -217 (283 / 342 / 69) | pnf_28, 976 (-101 / -1016 / 521) |
| sdx5 | break | dol_350 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 120 / 120 | 113 | 1986 | -19 | 351 | 1701 | 2104 | 291 (-158 / 803 / 1311) | wrenko_20, 2348 (760 / 872 / 1375) |
| sdx5 | lim_mid | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 491 | 1975 | 47 | -1857 | -1722 | 1335 | 1975 (47 / -1857 / -1722) | pnf_56, 4263 (-912 / -271 / 1146) |
| sdx5 | lim_prox | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 463 | 1797 | -116 | -1432 | 256 | 2644 | -344 (-1059 / 343 / -1952) | urenko_80, 4370 (1480 / 714 / 2473) |
| sdx5 | rej | dol_500 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 252 | 1768 | -758 | -713 | -3558 | 2890 | 983 (-1446 / -698 / -1555) | urenko_14, 2627 (-830 / 131 / -3477) |
| sdx5 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / both | 120 / 120 | 258 | 1062 | -1205 | -898 | -1943 | 1771 | -723 (-1112 / -1529 / -1512) | wrenko_14, 735 (-722 / 565 / 43) |
| sdx5 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 120 / 120 | 183 | 1291 | -1412 | -1434 | 415 | 780 | -135 (-1423 / -882 / -365) | wrenko_20, 3244 (1053 / 165 / -5880) |
| sdx5 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 183 | 1291 | -1412 | -1434 | 415 | 780 | -135 (-1423 / -882 / -365) | wrenko_20, 3244 (1053 / 165 / -5880) |
| sdx5 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 165 | 2309 | 1186 | -216 | 3671 | 2698 | -531 (632 / 1193 / 1827) | pnf_56, 2164 (463 / 1190 / 1731) |
| sdx60 | break | vrb_40000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 34 | 595 | 117 | 523 | 522 | 387 | 365 (112 / 473 / -93) | kagi_40, 1464 (466 / 334 / 762) |
| sdx60 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 417 | 1570 | -1168 | -222 | -1705 | 689 | 1570 (-1168 / -222 / -1705) | wrenko_10, 1413 (-1233 / -23 / -2684) |
| sdx60 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 429 | 1099 | -814 | -1355 | -3002 | 1374 | 1099 (-814 / -1355 / -3002) | urenko_80, 1005 (76 / 77 / -422) |
| sdx60 | rej | vrb_70000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 47 | 1112 | -265 | -1498 | 539 | 922 | -73 (-406 / -621 / 220) | lbrk_3_10, 2540 (-595 / -1785 / -237) |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / long | 60 / 60 | 90 | 1309 | 89 | -465 | -399 | 884 | 1309 (89 / -465 / -399) | wrenko_14, 589 (-294 / -644 / -547) |
| sdx60 | rej_native | vrb_40000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 89 | 1212 | -1553 | -1080 | -1414 | 799 | 1080 (-1510 / -148 / -1077) | lbrk_3_10, 2102 (-330 / -834 / -199) |
| sdx60 | rej_zone | vrb_40000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 89 | 1212 | -1553 | -1080 | -1414 | 799 | 1080 (-1510 / -148 / -1077) | lbrk_3_10, 2102 (-330 / -834 / -199) |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 332 | 1695 | 334 | 1290 | 4480 | 2938 | -1409 (1087 / 1838 / 2178) | pnf_56, 2617 (-1111 / 1032 / 1543) |
| sdx_renko28 | lim_mid | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 1307 | 1677 | -1073 | -135 | -175 | 1628 | 1677 (-1073 / -135 / -175) | kagi_20, 4203 (121 / -178 / 3832) |
| sdx_renko28 | lim_prox | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 422 | 947 | -344 | -799 | 286 | 1859 | -1527 (-142 / -1546 / -1688) | pnf_56, 4526 (216 / 1871 / -67) |
| sdx_renko28 | rej | dol_350 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 916 | 1534 | -2810 | -2502 | -3115 | 1647 | 1534 (-2810 / -2502 / -3115) | mrenko_10, 2601 (-2519 / -2626 / -4344) |
| sdx_renko28 | rej_flow | vrb_70000 | {"d": "E", "F": 0} | sym15u / both | 120 / 120 | 65 | 1686 | -488 | 438 | -551 | 2434 | 342 (-389 / 28 / 89) | wrenko_10, 2765 (740 / -3083 / 894) |
| sdx_renko28 | rej_native | dol_350 | {"d": "B", "F": 0, "tol": 0.5} | plain60/60 / long | 60 / 60 | 176 | 1866 | -379 | 397 | -1618 | 2727 | 1866 (-379 / 397 / -1618) | urenko_56, 2552 (-84 / -3676 / -2682) |
| sdx_renko28 | rej_zone | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 120 / 120 | 224 | 783 | -700 | -2134 | -2967 | 2707 | -1234 (-1370 / -2099 / -3182) | urenko_56, 2552 (-84 / -3676 / -2682) |
| sdx_renko28 | retest | dol_500 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 118 | 977 | 392 | 1821 | 163 | 839 | -40 (314 / 1278 / 854) | pnf_56, 2994 (-717 / 618 / 233) |
| sdx_rng28 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 480 | 4135 | -249 | -747 | 7833 | 6261 | -2081 (-548 / 1085 / 722) | kagi_20, 4615 (1288 / 2874 / 6639) |
| sdx_rng28 | lim_mid | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / short | 60 / 60 | 665 | 1214 | -76 | -369 | -2591 | 520 | 1214 (-76 / -369 / -2591) | kagi_20, 4204 (-595 / -701 / -2) |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 502 | 1844 | -310 | 2554 | -1323 | 2668 | -3119 (611 / -387 / -7072) | wrenko_20, 5342 (520 / 1267 / -40) |
| sdx_rng28 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / long | 60 / 60 | 697 | 846 | 734 | 232 | -2558 | 1691 | 846 (734 / 232 / -2558) | mrenko_20, 2856 (-984 / -1842 / -5463) |
| sdx_rng28 | rej_flow | vrb_70000 | {"d": "E", "F": 0} | sym15u / long | 120 / 120 | 40 | 920 | 303 | -300 | -663 | 1489 | 213 (242 / -15 / 19) | wrenko_14, 2052 (2014 / -466 / -281) |
| sdx_rng28 | rej_native | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 1530 | 2621 | -75 | -1547 | -3362 | 2847 | 2621 (-75 / -1547 / -3362) | kagi_40, 3332 (1328 / -4047 / 1358) |
| sdx_rng28 | rej_zone | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 1530 | 2621 | -75 | -1547 | -3362 | 2847 | 2621 (-75 / -1547 / -3362) | frenko_40, 4594 (559 / -3692 / -3237) |
| sdx_rng28 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 445 | 3741 | 1098 | -711 | 4872 | 5506 | -4873 (202 / 720 / -2797) | kagi_10, 3491 (-1168 / 3003 / 5388) |
| sdx_vol1100 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 432 | 3924 | -781 | 1019 | 5689 | 4212 | -1383 (416 / 2458 / 1103) | lbrk_3_10, 2954 (-817 / 879 / 1581) |
| sdx_vol1100 | lim_mid | dol_350 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 497 | 3273 | 1482 | 911 | -3564 | 3362 | 1535 (941 / 747 / -2575) | mrenko_14, 5146 (-307 / -267 / -7260) |
| sdx_vol1100 | lim_prox | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 501 | 3809 | -323 | -506 | -1569 | 6111 | -3687 (1592 / 839 / -4428) | mrenko_14, 4616 (1989 / -3 / -5487) |
| sdx_vol1100 | rej | dol_500 | {"d": "B", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 344 | 1932 | 118 | -80 | -4202 | 2554 | 1932 (118 / -80 / -4202) | kagi_14, 5058 (-1453 / -1789 / -1589) |
| sdx_vol1100 | rej_flow | vrb_700 | {"d": "E", "F": 0} | sym15u / both | 120 / 120 | 321 | 2969 | -6 | 1488 | -104 | 2957 | 1114 (-1032 / -593 / -1771) | wrenko_20, 1923 (-695 / -1236 / -1274) |
| sdx_vol1100 | rej_native | dol_350 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 1324 | 2682 | 150 | -1791 | -2877 | 806 | 2682 (150 / -1791 / -2877) | kagi_20, 3771 (-172 / -664 / -3831) |
| sdx_vol1100 | rej_zone | dol_500 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 1040 | 1987 | 1290 | -3756 | -3937 | 2605 | 1987 (1290 / -3756 / -3937) | frenko_28, 4710 (-906 / -898 / -3639) |
| sdx_vol1100 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 375 | 4034 | 902 | 713 | 2371 | 3527 | -1629 (-723 / 626 / 2297) | wrenko_14, 4494 (-381 / -1960 / 2674) |
| zones | break | rng_14 | {"n": 1, "k": 0.25} | sym8u / both | 86 / 86 | 258 | 3168 | -553 | -1075 | -778 | 2957 | 1512 (-92 / -453 / -648) | dchg_80, 2303 (505 / -559 / -1394) |
| zones | break_native | cdr_100 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 149 | 2887 | -187 | -692 | -659 | 5911 | -918 (448 / -841 / 340) | swing_pct_8, 3433 (-813 / -1533 / -456) |
| zones | false_break | rng_56 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 155 | 2265 | 948 | 1669 | -1646 | 3186 | 1837 (297 / 250 / -1280) | urenko_28, 3068 (829 / 2566 / -2302) |
| zones | false_break_native | rng_14 | {"M": 3, "k": 0.5} | sym8u / both | 86 / 86 | 251 | 2582 | -614 | 345 | -1723 | 1702 | 428 (208 / 1011 / -3167) | urenko_28, 3155 (720 / 2082 / -2078) |
| zones | reject | tm60 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 94 | 1997 | 1405 | -860 | 13 | 1117 | 1138 (632 / 190 / 1105) | urenko_28, 2134 (178 / -1365 / -390) |
| zones | reject_native | dlt_150 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 243 | 2882 | -1835 | -913 | -60 | 3270 | 23 (-1474 / -756 / 157) | urenko_28, 2772 (-431 / -536 / 199) |
| zones | retest | rng_14 | {"M": 10, "tol": 0.5} | sym8u / both | 86 / 86 | 208 | 3198 | -1554 | -825 | -689 | 2586 | 2568 (-1079 / -781 / -2314) | dchg_10, 1767 (-1210 / -108 / -1623) |
| zones | retest_native | rng_14 | {"M": 6, "tol": 0.5} | sym8u / both | 86 / 86 | 217 | 2669 | -1529 | -653 | -535 | 2164 | 2208 (-999 / -277 / -2026) | mom_28, 1906 (1033 / -2115 / -61) |

### NYAM - other level modules
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fib15 | break | vrb_40000 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 171 | 1449 | 840 | -414 | 438 | 2902 | 1449 (840 / -414 / 438) | kagi_20, 3524 (552 / 2335 / 3568) |
| fib15 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 309 | 3889 | 1224 | -1144 | 3109 | 4406 | 738 (442 / -651 / 2277) | kagi_56, 3762 (75 / -500 / 6087) |
| fib15 | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 335 | 1345 | 75 | 2348 | 2958 | -113 | -2292 (-1022 / 1310 / 703) | pnf_5, 3289 (-131 / 2456 / 3878) |
| fib15 | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 309 | 1464 | 919 | 3195 | 542 | 1029 | -1410 (-96 / 1542 / -944) | kagi_28, 3291 (444 / 1910 / -2104) |
| fib15 | pullback | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 113 | 1859 | 2134 | -69 | -2374 | 3386 | 718 (1414 / 472 / -1808) | kagi_10, 2115 (1754 / 472 / -1463) |
| fib15 | pullback_native | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 618 | 2181 | 1842 | 877 | 431 | 509 | 2181 (1842 / 877 / 431) | pnf_5, 2608 (1196 / 45 / -914) |
| fib15 | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 290 | 1757 | -133 | -2396 | 1708 | -164 | -1114 (446 / -1901 / 1638) | kagi_28, 2531 (868 / -585 / 3010) |
| fib15 | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 358 | 2048 | -26 | -2743 | 2480 | 1493 | -2817 (598 / -2023 / 1836) | kagi_28, 4502 (87 / 1288 / 1778) |
| fib15 | retest | vrb_40000 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 162 | 1118 | -23 | 414 | 377 | 880 | 1118 (-23 / 414 / 377) | kagi_20, 4147 (-1385 / 2285 / 2790) |
| fib15 | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 331 | 1993 | -315 | -715 | 4791 | 420 | -1633 (-715 / 359 / 3466) | kagi_20, 3490 (-840 / 1601 / -161) |
| fib5 | break | vrb_40000 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 195 | 2261 | 1065 | 531 | -51 | 3361 | 2261 (1065 / 531 / -51) | pnf_10, 4876 (-635 / -1541 / 2534) |
| fib5 | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / long | 120 / 120 | 194 | 2372 | 157 | 1216 | 990 | 4379 | -1754 (584 / 739 / -271) | pnf_56, 3101 (1263 / -128 / 1540) |
| fib5 | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 394 | 3343 | 460 | -369 | 2484 | 1320 | -229 (461 / 429 / -2408) | kagi_20, 4940 (944 / 1313 / 3307) |
| fib5 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 400 | 2629 | -356 | -2084 | 3607 | 1757 | -2829 (-462 / -1084 / -2744) | wrenko_10, 5399 (68 / -2894 / 1385) |
| fib5 | pullback | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 319 | 1876 | 420 | 42 | 1527 | 4582 | -501 (-1105 / -1510 / 488) | lbrk_3_20, 2243 (-33 / -959 / -883) |
| fib5 | pullback_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 311 | 2409 | 129 | 147 | 363 | 4528 | 1050 (180 / 5 / 1775) | pnf_56, 2320 (692 / 1177 / -653) |
| fib5 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 193 | 1159 | 846 | -1311 | -581 | 2391 | -1755 (1432 / 929 / -3779) | pnf_14, 1877 (-184 / 434 / -161) |
| fib5 | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / long | 120 / 120 | 192 | 2023 | 555 | 847 | 175 | 3783 | -976 (1753 / 659 / -1835) | pnf_20, 2753 (-140 / 262 / 1608) |
| fib5 | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 351 | 3172 | 786 | -3051 | 2235 | 4879 | 1855 (1081 / -1478 / -2698) | kagi_28, 4340 (561 / -571 / 2129) |
| fib5 | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 351 | 3172 | 786 | -3051 | 2235 | 4879 | 1855 (1081 / -1478 / -2698) | kagi_28, 4261 (1104 / -1881 / 3422) |
| fib60 | break | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 286 | 4189 | 1780 | 567 | 1201 | 4963 | -2723 (1399 / 302 / -653) | frenko_28, 4260 (834 / -351 / -346) |
| fib60 | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 286 | 4189 | 1780 | 567 | 1201 | 4963 | -2723 (1399 / 302 / -653) | frenko_28, 4260 (834 / -351 / -346) |
| fib60 | false_break | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 288 | 4302 | 869 | 588 | 1330 | 5241 | -1840 (1337 / 522 / -425) | pnf_14, 3933 (1570 / 2104 / 2305) |
| fib60 | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 289 | 4225 | 1675 | 395 | 1376 | 4683 | -2633 (1303 / 641 / -1459) | kagi_40, 4321 (2499 / 3022 / 1035) |
| fib60 | pullback | vrb_40000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 47 | 1226 | -450 | 835 | -776 | 973 | 382 (-561 / 222 / 620) | lbrk_3_20, 1315 (-353 / 2477 / 284) |
| fib60 | pullback_native | vrb_40000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 47 | 1226 | -460 | 835 | -776 | 973 | 382 (-561 / 222 / 620) | kagi_80, 1953 (409 / 2239 / 1366) |
| fib60 | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 295 | 3352 | -569 | -2793 | 3024 | 5199 | 1327 (222 / -2505 / -944) | wrenko_10, 3853 (197 / -2307 / -1069) |
| fib60 | reject_native | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 295 | 3280 | 604 | -1398 | -1567 | 2847 | 2861 (936 / -1022 / -202) | pnf_7, 3595 (-544 / -1575 / -629) |
| fib60 | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 272 | 3054 | 642 | -128 | 1384 | 2196 | 2477 (114 / -1737 / 374) | wrenko_14, 4034 (1024 / 761 / 814) |
| fib60 | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 272 | 3054 | 642 | -128 | 1384 | 2196 | 2477 (114 / -1737 / 374) | mrenko_10, 3645 (-129 / 298 / 273) |
| fibr_dev | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 434 | 3057 | -648 | 1464 | 6940 | 4372 | -259 (-556 / 600 / -1759) | kagi_40, 3837 (4233 / 2856 / 953) |
| fibr_dev | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 434 | 3057 | -648 | 1464 | 6940 | 4372 | -259 (-556 / 600 / -1759) | kagi_40, 3837 (4233 / 2856 / 953) |
| fibr_dev | false_break | dol_350 | {"M": 3, "k": 0.5} | sym15u / long | 120 / 120 | 214 | 1761 | -615 | -467 | 610 | 4464 | -206 (-486 / -310 / -2361) | kagi_40, 3921 (2689 / 822 / 2042) |
| fibr_dev | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 210 | 1731 | -404 | -397 | 612 | 4140 | -318 (-493 / -795 / -2245) | kagi_40, 4732 (2585 / -852 / 3835) |
| fibr_dev | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 432 | 2156 | 1970 | 906 | -874 | 2038 | 519 (-641 / 2376 / -2369) | pnf_7, 3087 (936 / 1508 / -135) |
| fibr_dev | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 434 | 2547 | -217 | 354 | 6148 | 3708 | 177 (-1233 / -394 / 466) | pnf_14, 4974 (1168 / 2667 / 817) |
| fibr_dev | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 415 | 1565 | 1125 | -1799 | 615 | 2852 | -1906 (1300 / -1088 / -3762) | pnf_7, 5720 (-316 / 1766 / 2350) |
| fibr_dev | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 426 | 2150 | 1199 | 2897 | 2592 | 1371 | -296 (76 / 1818 / 1381) | pnf_7, 4867 (-1061 / -570 / 4293) |
| fibr_ib | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 314 | 2855 | -277 | 881 | 4137 | 3297 | -455 (-2596 / 58 / 939) | frenko_28, 2727 (171 / -466 / 2503) |
| fibr_ib | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 331 | 2157 | -1066 | 2087 | 3670 | 1363 | 517 (-2276 / 498 / 2920) | frenko_28, 2812 (1115 / -212 / 3599) |
| fibr_ib | false_break | dol_6000 | {"M": 2, "k": 0.5} | sym15u / long | 120 / 120 | 132 | 806 | 562 | -129 | -415 | 1203 | -957 (241 / 750 / -1588) | kagi_40, 4545 (1796 / -1944 / 2034) |
| fibr_ib | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 132 | 578 | 690 | 103 | -344 | 995 | -968 (245 / 420 / -1495) | kagi_40, 4545 (1796 / -1944 / 2034) |
| fibr_ib | reject | vrb_70000 | {"tol": 0.5, "conf": "body"} | sym15u / long | 120 / 120 | 43 | 1095 | 320 | 302 | 590 | 1457 | 557 (75 / 121 / 747) | kagi_20, 3281 (-283 / -506 / 2843) |
| fibr_ib | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 914 | 1282 | -1302 | -321 | -974 | -522 | 1282 (-1302 / -321 / -974) | kagi_56, 3225 (598 / 890 / -471) |
| fibr_ib | retest | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / short | 60 / 60 | 344 | 1170 | -1094 | 105 | 310 | -552 | 1170 (-1094 / 105 / 310) | lbrk_3_20, 2506 (180 / -429 / 3) |
| fibr_ib | retest_native | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / short | 60 / 60 | 364 | 1178 | -1081 | -181 | 59 | -339 | 1178 (-1081 / -181 / 59) | kagi_20, 2991 (863 / 1825 / 1106) |
| fibr_on | break | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 397 | 1838 | 3089 | 1850 | 2409 | -30 | -1089 (466 / 1258 / -493) | urenko_14, 3646 (879 / 2200 / 7144) |
| fibr_on | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 406 | 2191 | 1114 | -1195 | 6807 | 3136 | 668 (860 / -1714 / 1366) | kagi_20, 4795 (1610 / 372 / 7170) |
| fibr_on | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 400 | 1578 | 2073 | 2011 | 492 | 417 | -2254 (-262 / -22 / -1875) | pnf_14, 5252 (1464 / 1013 / 2918) |
| fibr_on | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 400 | 1578 | 2073 | 2011 | 492 | 417 | -2254 (-262 / -22 / -1875) | pnf_10, 5512 (761 / 1389 / 392) |
| fibr_on | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 1073 | 2934 | 854 | -766 | 249 | 1445 | 2934 (854 / -766 / 249) | wrenko_10, 2691 (1164 / -1169 / 4230) |
| fibr_on | reject_native | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 325 | 2757 | 1096 | -1554 | 649 | 1688 | -1432 (2173 / 1435 / -1948) | kagi_112, 3620 (579 / -1335 / -1835) |
| fibr_on | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 359 | 2442 | 137 | 1062 | -1504 | 2586 | -1294 (-995 / 4031 / 2900) | lbrk_3_20, 2663 (-1647 / 883 / 1488) |
| fibr_on | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 392 | 2934 | 2492 | -1326 | 4717 | 5071 | 89 (2974 / -1307 / 602) | pnf_28, 3227 (1904 / -823 / -47) |
| fibr_or | break | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 363 | 2838 | 671 | -1563 | 1724 | 581 | -2323 (-103 / -914 / 942) | kagi_40, 5520 (-1080 / -710 / -2013) |
| fibr_or | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 363 | 2838 | 671 | -1563 | 1724 | 581 | -2323 (-103 / -914 / 942) | kagi_40, 5520 (-1080 / -710 / -2013) |
| fibr_or | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 378 | 3837 | -1599 | -71 | -1975 | 1180 | -718 (-646 / 189 / 997) | urenko_28, 3867 (432 / 1403 / -216) |
| fibr_or | false_break_native | dol_500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 350 | 3729 | -1114 | -212 | -965 | 1239 | -780 (-314 / -1602 / -1167) | kagi_14, 3852 (98 / 1427 / 1769) |
| fibr_or | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 362 | 2397 | 437 | -4092 | 1703 | 2271 | 953 (-1474 / -1455 / -3339) | wrenko_14, 3996 (-233 / 328 / 4247) |
| fibr_or | reject_native | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 362 | 2397 | 437 | -4092 | 1703 | 2271 | 953 (-1474 / -1455 / -3339) | lbrk_3_10, 3288 (56 / 1396 / 513) |
| fibr_or | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 355 | 2797 | -602 | 519 | 771 | 1060 | -4295 (-327 / -738 / -385) | kagi_20, 5330 (-762 / -231 / -3898) |
| fibr_or | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 355 | 2797 | -602 | 519 | 771 | 1060 | -4295 (-327 / -738 / -385) | kagi_20, 5330 (-762 / -231 / -3898) |
| fibr_pd | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 318 | 2075 | 1721 | -1626 | 1166 | 2326 | -136 (616 / 327 / -14) | kagi_20, 6035 (-981 / 1122 / 3395) |
| fibr_pd | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 370 | 2619 | -2350 | -1210 | -1168 | 3801 | -1567 (-1244 / -1891 / -908) | kagi_20, 5426 (-679 / 158 / 2300) |
| fibr_pd | false_break | dol_6000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 319 | 923 | -385 | 2226 | 2898 | -72 | -118 (760 / 2511 / 177) | pnf_56, 3574 (-320 / 484 / 1967) |
| fibr_pd | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 301 | 1709 | -26 | 1733 | -849 | 1626 | -284 (701 / 1088 / -873) | pnf_56, 3574 (-278 / 484 / 1967) |
| fibr_pd | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 355 | 2995 | -935 | -968 | -377 | 2272 | -646 (-235 / -244 / 160) | wrenko_20, 5238 (-1748 / 1982 / 2411) |
| fibr_pd | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 381 | 4091 | -746 | -3096 | 709 | 3289 | 1571 (-1467 / -1567 / 1615) | wrenko_20, 5238 (-1748 / 1982 / 2411) |
| fibr_pd | retest | dol_6000 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 509 | 1919 | -834 | 1433 | 1208 | 503 | 1919 (-834 / 1433 / 1208) | mrenko_10, 4397 (-248 / -304 / -18) |
| fibr_pd | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 341 | 1526 | -1012 | -2220 | 2816 | 1807 | 57 (-759 / 492 / 1285) | mrenko_10, 4397 (-248 / -304 / -18) |
| piv_cama | break | vrb_40000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 155 | 1358 | 1491 | -163 | -144 | 724 | 104 (1136 / 794 / 1214) | pnf_10, 5210 (1949 / 420 / -2741) |
| piv_cama | break_native | vrb_700 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 397 | 2771 | -244 | 189 | -2907 | 2592 | -1870 (-785 / -480 / -1852) | pnf_7, 6524 (489 / 1354 / 649) |
| piv_cama | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / long | 120 / 120 | 179 | 286 | -495 | 1329 | 595 | -103 | -1813 (-360 / 344 / 103) | pnf_56, 3092 (319 / 526 / 2048) |
| piv_cama | false_break_native | dol_350 | {"M": 3, "k": 0.5} | sym15u / long | 120 / 120 | 168 | 696 | 392 | 1179 | 1990 | 129 | -1325 (320 / 913 / -211) | pnf_56, 3276 (454 / 729 / 1972) |
| piv_cama | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 381 | 3907 | -760 | 253 | 597 | 3463 | 2240 (229 / -1091 / -866) | wrenko_14, 2583 (-1426 / 1370 / 3989) |
| piv_cama | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 381 | 3907 | -760 | 253 | 597 | 3463 | 2240 (229 / -1091 / -866) | kagi_28, 4654 (-2040 / -878 / -4527) |
| piv_cama | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 361 | 1908 | 443 | 955 | 1049 | -609 | -1885 (-868 / -61 / -643) | wrenko_10, 3890 (-15 / 859 / 1334) |
| piv_cama | retest_native | dol_350 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 388 | 2869 | -602 | -54 | -1703 | 1537 | -4106 (-530 / 514 / -5842) | wrenko_10, 3890 (-15 / 859 / 1334) |
| piv_floor | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 296 | 2238 | 171 | 908 | 4315 | 4932 | -784 (410 / 2040 / 1152) | pnf_56, 3553 (-161 / 488 / 2430) |
| piv_floor | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 332 | 3466 | 1517 | 603 | -570 | 5036 | 399 (874 / 1384 / -1289) | pnf_10, 4181 (1622 / 504 / 3964) |
| piv_floor | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 359 | 673 | -702 | 2450 | 4283 | -238 | -638 (-1569 / 2229 / -993) | pnf_56, 3796 (-476 / 286 / 3151) |
| piv_floor | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 283 | 1392 | 181 | -520 | 1214 | 1966 | -1249 (-47 / 2620 / -32) | kagi_40, 4160 (1164 / 1611 / 1824) |
| piv_floor | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 351 | 2917 | 1884 | -488 | -3275 | 2870 | 604 (976 / -555 / 651) | kagi_40, 1062 (595 / 2464 / 2078) |
| piv_floor | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 351 | 2917 | 1884 | -488 | -3275 | 2870 | 604 (976 / -555 / 651) | urenko_40, 2407 (1631 / 3763 / 519) |
| piv_floor | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 217 | 1671 | 675 | 1502 | 75 | 2831 | -104 (806 / 1126 / 750) | pnf_56, 3307 (1674 / 1218 / 2007) |
| piv_floor | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 217 | 1671 | 675 | 1502 | 75 | 2831 | -104 (806 / 1126 / 750) | pnf_56, 3913 (1673 / 239 / 2389) |
| piv_wf | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 334 | 2892 | 2036 | -151 | 2031 | 2523 | 833 (921 / -188 / 1420) | pnf_56, 3685 (42 / 27 / 876) |
| piv_wf | break_native | vrb_40000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 126 | 2618 | 1347 | -1067 | 338 | 3208 | 1757 (1177 / -634 / -51) | kagi_20, 3769 (-323 / 382 / 4352) |
| piv_wf | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 172 | 1724 | 144 | 426 | 1566 | 1818 | 58 (149 / 586 / 1283) | kagi_40, 3750 (2632 / 2336 / 1588) |
| piv_wf | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 172 | 1724 | 144 | 426 | 1566 | 1818 | 58 (149 / 586 / 1283) | kagi_40, 3736 (2381 / 2146 / 1178) |
| piv_wf | reject | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 365 | 1490 | -1897 | -2327 | 163 | 2031 | -1463 (-1935 / -231 / -2135) | urenko_20, 2772 (-874 / -732 / 1160) |
| piv_wf | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 433 | 1751 | -1670 | 196 | -1417 | 1505 | -1709 (-655 / -514 / 1417) | urenko_56, 2303 (-833 / 3724 / 3038) |
| piv_wf | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 348 | 3798 | -424 | 132 | 1098 | 1071 | -764 (-920 / -1475 / 2093) | kagi_20, 4657 (320 / 3797 / -729) |
| piv_wf | retest_native | dol_500 | {"M": 10, "tol": 0.5} | sym15u / long | 120 / 120 | 180 | 2069 | 115 | 482 | -1394 | 1653 | -799 (139 / -717 / 308) | urenko_28, 4338 (1465 / 1240 / 2816) |
| swcluster | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 82 | 907 | -300 | 483 | -1305 | 496 | -533 (399 / -476 / 715) | urenko_112, 1306 (832 / -672 / 48) |
| swcluster | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 86 | 697 | -228 | 556 | 1464 | 466 | 360 (68 / 926 / 551) | kagi_80, 1203 (-745 / -84 / -805) |
| swcluster | false_break | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 86 | 817 | -734 | 1041 | 1620 | 574 | -121 (31 / 348 / 565) | pnf_40, 1551 (-519 / -769 / 385) |
| swcluster | false_break_native | vrb_700 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 88 | 927 | -46 | 716 | 2128 | 1330 | 418 (478 / 197 / 1067) | pnf_40, 1583 (-538 / -389 / -652) |
| swcluster | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / long | 120 / 120 | 42 | 776 | -849 | 351 | 106 | 735 | 40 (-689 / 137 / 568) | wrenko_20, 994 (-808 / 727 / -1417) |
| swcluster | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 93 | 941 | -293 | -671 | -1280 | 351 | -523 (-171 / -642 / -160) | kagi_112, 1254 (-69 / -238 / 607) |
| swcluster | retest | dol_350 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 84 | 959 | -600 | 707 | -1102 | 825 | 234 (-168 / 350 / -463) | kagi_80, 1317 (-512 / -727 / -288) |
| swcluster | retest_native | vrb_40000 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 34 | 428 | 302 | -762 | 125 | 78 | 428 (302 / -762 / 125) | kagi_80, 1293 (791 / -1867 / 192) |
| swsr15 | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 289 | 1723 | 799 | 799 | 759 | 1654 | -2078 (653 / 600 / 2255) | kagi_40, 3793 (2163 / 1177 / 3112) |
| swsr15 | break_native | vrb_40000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 126 | 1752 | 1288 | -881 | -434 | 1095 | 1313 (1129 / 310 / -613) | kagi_40, 3793 (2163 / 1177 / 3112) |
| swsr15 | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 351 | 2074 | 90 | -687 | 3491 | 2687 | 386 (1010 / -423 / 2239) | kagi_40, 3937 (1163 / 182 / 1458) |
| swsr15 | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 343 | 5020 | 338 | -1450 | 5190 | 5244 | 1149 (1567 / -2114 / 2240) | kagi_28, 4013 (-579 / -1717 / 3531) |
| swsr15 | reject | vrb_40000 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 179 | 1521 | 340 | -77 | 1423 | 1138 | 1521 (340 / -77 / 1423) | kagi_10, 3874 (-2044 / -176 / -1129) |
| swsr15 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 370 | 1936 | -1391 | -699 | -3168 | 3028 | -1181 (-1788 / -356 / -2478) | pnf_10, 3290 (-1693 / 687 / -2566) |
| swsr15 | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 332 | 2411 | -275 | 1737 | 5730 | 1104 | -1048 (-761 / -224 / 1224) | urenko_20, 5015 (-392 / -944 / 1428) |
| swsr15 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 304 | 1914 | 1487 | -39 | -1921 | 2713 | -321 (682 / -122 / -3259) | urenko_14, 4907 (1503 / -111 / 2647) |
| swsr5 | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 357 | 3915 | 706 | 1857 | 1071 | 3401 | -592 (206 / 1529 / 829) | kagi_28, 5683 (1075 / -778 / -1404) |
| swsr5 | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / long | 120 / 120 | 188 | 1915 | 1250 | 1089 | 1368 | 2641 | -1103 (820 / 1252 / -642) | kagi_28, 5683 (1075 / -778 / -1404) |
| swsr5 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 429 | 1639 | 304 | -385 | 720 | -206 | -92 (-16 / -1976 / 2042) | kagi_28, 5625 (880 / -288 / -1389) |
| swsr5 | false_break_native | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 440 | 2556 | -1270 | -546 | 475 | 1267 | -1333 (437 / -2466 / 1208) | kagi_28, 8188 (1948 / -2061 / 866) |
| swsr5 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 413 | 2018 | -54 | 544 | -2433 | -1185 | -1120 (-802 / -377 / 306) | wrenko_14, 3165 (-776 / 1166 / 1559) |
| swsr5 | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 445 | 2061 | 1216 | 1585 | -1034 | 2881 | 2026 (1162 / -811 / -2849) | wrenko_14, 4120 (-609 / 1554 / 3190) |
| swsr5 | retest | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 735 | 3406 | -1681 | 1460 | -718 | 3572 | 3406 (-1681 / 1460 / -718) | pnf_20, 4493 (665 / 2200 / 3212) |
| swsr5 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 735 | 3406 | -1681 | 1460 | -718 | 3572 | 3406 (-1681 / 1460 / -718) | pnf_20, 4493 (691 / 2200 / 3212) |
| swsr60 | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 264 | 3169 | -1091 | 462 | -1221 | 2411 | -843 (-519 / 1928 / -635) | pnf_5, 3965 (36 / 158 / -2380) |
| swsr60 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 260 | 2763 | -65 | 168 | 2754 | 2947 | -839 (-104 / -739 / -416) | mrenko_20, 4303 (338 / -270 / -2273) |
| swsr60 | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 272 | 2354 | 754 | -564 | 1942 | 2221 | 76 (-104 / 841 / 261) | pnf_7, 2588 (1112 / -417 / 1728) |
| swsr60 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 272 | 2354 | 754 | -564 | 1942 | 2221 | 76 (-104 / 841 / 261) | pnf_5, 2726 (385 / -291 / 3026) |
| swsr60 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 267 | 2782 | -1997 | -1028 | -1956 | 2565 | -1429 (193 / -855 / -1467) | wrenko_14, 2871 (-893 / -1110 / -691) |
| swsr60 | reject_native | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 277 | 992 | -1233 | 1016 | -2995 | -829 | 207 (-1261 / -118 / -1888) | pnf_7, 2996 (-223 / 738 / -2958) |
| swsr60 | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / long | 120 / 120 | 101 | 1043 | 236 | 846 | 388 | 2425 | 280 (-34 / 747 / -254) | kagi_14, 3367 (417 / 713 / 2105) |
| swsr60 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 249 | 1449 | -1050 | 1003 | 75 | 1874 | -1351 (107 / 1340 / 627) | urenko_28, 3947 (-295 / 1712 / 542) |
| stack | break | rng_20 | {"k": 2, "cw": 2.0} | asym20u/10u / both | 120 / 120 | 251 | 5486 | 738 | 818 | 1504 | 1968 | -35 (691 / -162 / -297) | renko_10, 4315 (1203 / 1801 / 2184) |
| stack | break_native | rng_80 | {"k": 2, "cw": 2.0} | sym8u / both | 120 / 120 | 307 | 6590 | -1020 | 397 | 79 | 3936 | 2836 (-105 / 575 / 1623) | renko_10, 4611 (2212 / 2055 / -34) |
| stack | reject | vsess_200 | {"k": 2, "cw": 2.0} | sym8u / both | 120 / 120 | 288 | 2140 | -161 | -1789 | -313 | 1945 | -989 (-847 / 220 / -553) | pnf_5, 2969 (-1754 / -1412 / -638) |
| stack | reject_native | vsess_120 | {"k": 2, "cw": 0.5} | asym20u/10u / both | 120 / 120 | 248 | 3290 | -789 | 971 | -1202 | 4802 | -80 (-1138 / 347 / -1045) | renko_10, 3240 (934 / -641 / -1625) |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym15u/30u / both | 120 / 120 | 101 | 1642 | -1133 | 498 | 721 | 2376 | 321 (-1288 / -23 / 766) | urenko_20, 978 (-170 / 1854 / 577) |
| book_walls_loose | break_native | tm60 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 65 | 1335 | -822 | 539 | 550 | 1717 | 561 (-824 / 62 / -255) | frenko_40, 841 (78 / 531 / 342) |
| book_walls_loose | false_break | tm15 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 66 | 1142 | -1301 | -222 | 612 | 2107 | 879 (-1805 / 683 / -362) | dchg_10, 1436 (-1803 / -2147 / -1329) |
| book_walls_loose | false_break_native | tm15 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 66 | 1142 | -1301 | -222 | 612 | 2107 | 879 (-1805 / 683 / -362) | dchg_10, 1436 (-1803 / -2147 / -1329) |
| book_walls_loose | reject | rng_14 | {"tol": 1.0, "conf": "close"} | sym30u / both | 120 / 120 | 93 | 1730 | 66 | 6 | 2266 | 2356 | 280 (113 / 923 / 1292) | mom_10, 1415 (-42 / -1125 / 792) |
| book_walls_loose | reject_native | dib_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 107 / 107 | 126 | 1601 | -738 | -637 | 518 | 1605 | 901 (146 / 752 / 687) | mom_10, 1234 (-158 / -428 / 506) |
| book_walls_loose | retest | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 107 / 107 | 108 | 1266 | -894 | 749 | 1751 | 1947 | 530 (354 / 1410 / 1139) | dchg_14, 1157 (-821 / 309 / 432) |
| book_walls_loose | retest_native | dib_700 | {"M": 6, "tol": 0.5} | sym15u / both | 107 / 107 | 106 | 989 | -876 | 864 | 2087 | 1765 | 194 (50 / 2045 / 1404) | dchg_14, 1406 (-798 / -684 / 1371) |
| channel | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 344 | 2328 | 2338 | 3290 | 2404 | 2951 | -502 (757 / 1922 / 3773) | wrenko_14, 4675 (-645 / 4537 / 4359) |
| channel | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 419 | 2193 | 761 | 2690 | 3451 | -508 | -2870 (-214 / 1636 / 248) | wrenko_14, 4675 (-645 / 4537 / 4359) |
| channel | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 418 | 2330 | 572 | 3241 | 3186 | -693 | -2470 (-802 / 1739 / -1084) | wrenko_14, 3460 (-132 / 4073 / 3994) |
| channel | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 418 | 2330 | 572 | 3241 | 3186 | -693 | -2470 (-802 / 1739 / -1084) | wrenko_14, 3460 (-132 / 4073 / 3994) |
| channel | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 181 | 1414 | -129 | -472 | 1009 | 2184 | -950 (346 / -436 / 787) | wrenko_20, 3917 (-208 / 972 / 4672) |
| channel | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 461 | 1818 | -1046 | -1482 | 3302 | 1439 | -3648 (55 / -1062 / -163) | wrenko_14, 4187 (146 / -2476 / 4036) |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 380 | 1080 | 351 | 1791 | 4977 | 1088 | -1210 (-3 / 1143 / 1299) | urenko_10, 5168 (1396 / -726 / 235) |
| channel | retest_native | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 380 | 1080 | 351 | 1791 | 4977 | 1088 | -1210 (-3 / 1143 / 1299) | kagi_20, 6420 (1977 / 2723 / 3726) |
| fvg15 | break | vrb_40000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 72 | 1667 | 854 | -636 | 216 | 1025 | 498 (702 / 444 / -435) | pnf_40, 2491 (330 / -695 / 1898) |
| fvg15 | break_native | vrb_40000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 61 | 1158 | 345 | 0 | 337 | 954 | 233 (578 / 263 / -22) | pnf_40, 2491 (408 / -695 / 1898) |
| fvg15 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 176 | 990 | -815 | -658 | -539 | -1636 | -615 (-743 / -324 / -1973) | pnf_56, 2026 (106 / -1123 / 207) |
| fvg15 | false_break_native | dol_6000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 132 | 1237 | 885 | 453 | -2058 | 772 | -844 (-444 / -389 / -1972) | kagi_112, 2100 (-895 / 84 / -297) |
| fvg15 | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 79 | 721 | 437 | 1383 | -700 | 234 | -363 (260 / 1178 / -1129) | wrenko_14, 1407 (-534 / 1658 / -536) |
| fvg15 | reject_native | vrb_40000 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 107 | 908 | 126 | 1053 | 721 | 1202 | 908 (126 / 1053 / 721) | kagi_14, 1253 (175 / 1053 / 1876) |
| fvg15 | retest | vrb_40000 | {"M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 33 | 403 | -342 | -418 | -426 | 395 | 164 (-87 / -434 / -16) | kagi_80, 2444 (878 / 1057 / -281) |
| fvg15 | retest_native | vrb_40000 | {"M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 46 | 873 | -313 | -878 | -343 | 905 | 381 (-323 / -640 / -316) | kagi_80, 2444 (878 / 1057 / -281) |
| fvg5 | break | dol_500 | {"n": 3, "k": 0.5} | plain60/60 / long | 60 / 60 | 213 | 887 | 269 | -704 | 5 | 662 | 887 (269 / -704 / 5) | lbrk_3_40, 2212 (932 / -1000 / -902) |
| fvg5 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 109 | 873 | 1101 | 183 | 581 | 1431 | 303 (710 / 559 / -435) | pnf_14, 2280 (649 / 1613 / 1744) |
| fvg5 | false_break | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / long | 60 / 60 | 198 | 550 | 888 | 269 | -781 | 779 | 550 (888 / 269 / -781) | pnf_20, 1913 (-47 / -1966 / 1134) |
| fvg5 | false_break_native | dol_500 | {"M": 2, "k": 0.5} | plain60/60 / long | 60 / 60 | 183 | 954 | 655 | 780 | -1319 | 1124 | 954 (655 / 780 / -1319) | pnf_20, 1676 (-1207 / -1321 / 1577) |
| fvg5 | reject | vrb_40000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 68 | 1301 | 963 | -1574 | 866 | 480 | 256 (234 / -473 / 289) | kagi_28, 1934 (248 / 21 / 1054) |
| fvg5 | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / long | 120 / 120 | 137 | 1549 | 517 | 109 | -874 | 2866 | 699 (412 / 562 / -590) | kagi_14, 1899 (677 / 400 / -1831) |
| fvg5 | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 112 | 945 | 975 | -217 | 1161 | 1497 | 167 (306 / 43 / -88) | kagi_40, 3806 (-1035 / -262 / -445) |
| fvg5 | retest_native | dol_350 | {"M": 10, "tol": 0.5} | sym15u / long | 120 / 120 | 115 | 1604 | 908 | -722 | 204 | 2365 | 554 (685 / 42 / -67) | pnf_40, 2329 (-55 / -245 / -934) |
| gaps | break | vol_350 | {"n": 3, "k": 0.25} | sym15u / both | 120 / 120 | 80 | 2491 | -83 | -863 | 1089 | 2684 | 886 (-487 / -886 / 163) | pnf_28, 2587 (104 / -1328 / 2128) |
| gaps | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 102 | 2326 | -1328 | -323 | -847 | 2501 | 1433 (-1303 / -423 / -1330) | pnf_28, 2587 (142 / -1328 / 2128) |
| gaps | false_break | rng_10 | {"M": 1, "k": 0.5} | asym15u/30u / both | 120 / 120 | 81 | 1723 | -440 | 680 | -314 | 1252 | 652 (-462 / 1039 / 622) | pnf_56, 3123 (-820 / -86 / 2898) |
| gaps | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym10u/20u / both | 108 / 120 | 77 | 2847 | -185 | -240 | -14 | 2548 | 1157 (-570 / 169 / 249) | pnf_56, 3123 (-762 / -86 / 2898) |
| gaps | reject | time_m_7 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 52 | 1582 | 423 | 187 | -717 | 1904 | 548 (-143 / -861 / -293) | wrenko_14, 2674 (-544 / 2257 / 2203) |
| gaps | reject_native | drb_25000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 74 | 1636 | 1164 | -912 | -758 | 1844 | 475 (629 / -929 / -628) | wrenko_14, 2674 (-544 / 2257 / 2203) |
| gaps | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 132 | 2127 | -230 | 992 | -804 | 2894 | 691 (-264 / 968 / -407) | kagi_28, 2981 (-132 / -126 / -354) |
| gaps | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 221 | 3004 | 496 | -2177 | 458 | 3709 | -34 (288 / -893 / -525) | kagi_28, 2211 (-1073 / 726 / -402) |
| mmove | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 329 | 2602 | 2170 | -1145 | 2721 | -1181 | -624 (2362 / 81 / 783) | kagi_14, 3567 (239 / -51 / 4187) |
| mmove | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 329 | 2655 | 435 | -1969 | 2892 | 1091 | -1882 (1020 / 653 / 307) | kagi_14, 3567 (239 / -51 / 4187) |
| mmove | false_break | dol_6000 | {"M": 3, "k": 0.5} | plain60/60 / short | 60 / 60 | 331 | 756 | -1375 | -34 | 1482 | 630 | 756 (-1375 / -34 / 1482) | pnf_56, 2201 (17 / 122 / 1471) |
| mmove | false_break_native | dol_6000 | {"M": 2, "k": 0.5} | plain60/60 / short | 60 / 60 | 292 | 803 | -1053 | 92 | 1205 | 50 | 803 (-1053 / 92 / 1205) | pnf_56, 2638 (531 / -330 / 1424) |
| mmove | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 274 | 1551 | -283 | 289 | 450 | 3334 | -1741 (-742 / 497 / -158) | mrenko_14, 2790 (1939 / 398 / 1792) |
| mmove | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 181 | 2154 | 906 | 512 | -1548 | 2111 | -219 (1694 / -782 / -2274) | kagi_20, 3372 (-70 / 595 / -1300) |
| mmove | retest | vrb_70000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 102 | 1463 | 574 | -1044 | 2704 | 1496 | -26 (372 / -211 / 1389) | kagi_56, 3092 (1424 / 140 / 3397) |
| mmove | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 306 | 2020 | 488 | 17 | 1733 | 1964 | 329 (189 / 260 / 1923) | kagi_80, 3030 (552 / -385 / 1137) |
| ob15 | break | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 128 | 2257 | -324 | -667 | -326 | 977 | 1831 (124 / -926 / -402) | mrenko_10, 2715 (-364 / 1077 / -198) |
| ob15 | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 64 | 1817 | -754 | -137 | -528 | 2908 | 1548 (-432 / 207 / 45) | mrenko_10, 2579 (-490 / 437 / 440) |
| ob15 | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 57 | 1547 | -27 | -254 | -62 | 1483 | 461 (69 / 235 / 173) | kagi_80, 1724 (1840 / 757 / 2754) |
| ob15 | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 57 | 1547 | -27 | -254 | -62 | 1483 | 461 (69 / 235 / 173) | kagi_14, 1730 (694 / -773 / 1270) |
| ob15 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 125 | 2280 | -762 | 112 | 499 | 2143 | -26 (-1008 / 54 / 1065) | mrenko_10, 1612 (-55 / -833 / 1139) |
| ob15 | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 133 | 2093 | -1313 | -1871 | 232 | 2483 | 119 (-858 / -967 / 1742) | wrenko_14, 2140 (289 / -157 / 1697) |
| ob15 | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 120 | 2146 | 356 | -1751 | -1277 | 1688 | 621 (340 / -1045 / 983) | urenko_14, 2538 (-231 / 102 / 2014) |
| ob15 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 107 | 1942 | -1299 | -1076 | -13 | 1822 | 288 (-794 / -1150 / 301) | pnf_7, 2091 (649 / -1044 / 32) |
| ob5 | break | vrb_700 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 57 | 1933 | 85 | -1077 | -828 | 2827 | 439 (16 / -1528 / -344) | kagi_10, 3190 (-50 / -560 / -1480) |
| ob5 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 70 | 1448 | -292 | -1077 | -1359 | 559 | 71 (-116 / -582 / 952) | kagi_10, 3190 (-50 / -560 / -1480) |
| ob5 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 148 | 1465 | 181 | -1185 | 385 | 121 | 8 (180 / 459 / 2475) | kagi_10, 2647 (367 / 57 / -284) |
| ob5 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 143 | 1544 | 501 | -758 | -194 | 967 | -39 (633 / -563 / 2516) | kagi_10, 2647 (367 / 57 / -284) |
| ob5 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 64 | 1403 | 301 | -625 | -1429 | 1840 | 471 (-20 / -1530 / 98) | urenko_14, 1592 (443 / -1429 / -219) |
| ob5 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 158 | 2132 | 1174 | -149 | -638 | 3965 | 190 (313 / -2216 / -176) | urenko_14, 2232 (-724 / -50 / -411) |
| ob5 | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 61 | 1953 | -60 | -303 | -1720 | 1585 | -841 (20 / -1050 / -34) | kagi_14, 2614 (-885 / -1043 / -1778) |
| ob5 | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 61 | 1943 | -194 | -492 | -888 | 2055 | 240 (205 / -1050 / 18) | pnf_5, 2537 (-637 / -296 / -515) |
| open_range | break | dib_15000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 368 | 4752 | 1257 | 1200 | -2299 | 3041 | -221 (951 / -72 / -410) | swing_atr_0.4, 4634 (1364 / -1317 / -1376) |
| open_range | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 120 / 120 | 394 | 5790 | 809 | -1370 | 684 | 4105 | 428 (116 / -641 / -1529) | pnf_10, 5029 (-69 / -3515 / -2743) |
| open_range | false_break | time_m_13 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 98 | 2075 | 728 | 1727 | -156 | 2633 | -158 (490 / 920 / -59) | renko_14, 2425 (23 / -145 / -730) |
| open_range | false_break_native | rng_14 | {"M": 1, "k": 0.5} | plain60/60 / long | 60 / 60 | 346 | 2075 | 275 | 907 | -479 | 1503 | 2075 (275 / 907 / -479) | renko_20, 2670 (231 / -183 / -1477) |
| open_range | reject | tick_800 | {"tol": 1.0, "conf": "close"} | sym15u / both | 120 / 120 | 403 | 6353 | 476 | -605 | -960 | 4974 | 2232 (-461 / -2723 / -1009) | dchg_56, 4036 (1173 / 149 / -1685) |
| open_range | reject_native | vol_1100 | {"tol": 0.5, "conf": "close"} | asym20u/10u / both | 120 / 120 | 444 | 5685 | -805 | -428 | -1655 | 7085 | 2338 (-1152 / -2972 / -1532) | renko_40, 6274 (-1585 / 1562 / -2188) |
| open_range | retest | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 120 / 120 | 298 | 4014 | 703 | 324 | -1734 | 2744 | 1389 (969 / -1827 / 129) | swing_atr_0.6, 4800 (1260 / 1255 / -2074) |
| open_range | retest_native | vol_6000 | {"M": 10, "tol": 0.0} | sym8u / both | 120 / 120 | 298 | 4014 | 703 | 324 | -1734 | 2744 | 1389 (969 / -1827 / 129) | pnf_28, 3712 (405 / 334 / -579) |
| opens | break | tib_3500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 317 | 4934 | -124 | 1732 | 1224 | 6218 | 3515 (1474 / -454 / 1576) | dchg_40, 5490 (-643 / 803 / 229) |
| opens | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 338 | 5821 | 1364 | -659 | -1602 | 6521 | 2605 (1183 / -1237 / -3533) | dchg_40, 5490 (-643 / 803 / 229) |
| opens | false_break | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 108 | 379 | 4101 | 1530 | 331 | -2505 | 4943 | -1634 (1709 / 1016 / -413) | pnf_56, 4705 (-649 / -420 / 1329) |
| opens | false_break_native | dlt_30 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 427 | 4013 | 87 | 262 | -53 | 2389 | -721 (-269 / -120 / -1393) | pnf_56, 4781 (-690 / 144 / 2901) |
| opens | reject | time_s_15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 367 | 5218 | -809 | 1237 | -891 | 2404 | 1816 (-573 / -89 / 2414) | mom_28, 3984 (60 / -2640 / -1217) |
| opens | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 315 | 4982 | -996 | -570 | 2619 | 6379 | 1223 (139 / -2865 / 1348) | swing_atr_0.25, 4022 (-260 / -1091 / -3839) |
| opens | retest | rng_14 | {"M": 6, "tol": 0.5} | asym15u/30u / both | 120 / 120 | 328 | 4390 | 832 | -2026 | 110 | 1839 | -383 (562 / -1561 / 1722) | swing_atr_0.9, 4952 (1079 / -2912 / 3174) |
| opens | retest_native | dib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 302 | 4310 | -847 | 968 | -656 | 6865 | 362 (901 / -1687 / -1007) | pnf_20, 4635 (1331 / 789 / 2801) |
| prior_day | break | rng_14 | {"n": 1, "k": 0.25} | sym15u / both | 120 / 120 | 190 | 5337 | -1099 | -260 | 2183 | 3374 | 2040 (-356 / -347 / 328) | swing_atr_0.25, 5918 (1300 / 387 / 6559) |
| prior_day | break_native | tm45 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 166 | 4824 | 372 | -1815 | 3016 | 4514 | 912 (-137 / 1768 / 804) | swing_atr_0.25, 5918 (1300 / 387 / 6559) |
| prior_day | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / both | 120 / 120 | 181 | 5625 | 1424 | 248 | 1200 | 7728 | 2057 (654 / 580 / 1102) | swing_atr_0.25, 6120 (1169 / 654 / 6266) |
| prior_day | false_break_native | tm45 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 166 | 5246 | 602 | -1614 | 2897 | 5200 | 1898 (92 / 1647 / 1378) | swing_atr_0.25, 5639 (1638 / 523 / 6789) |
| prior_day | reject | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 170 | 3323 | 195 | -118 | 844 | 3659 | 878 (106 / 109 / 58) | swing_atr_0.1, 2190 (-1483 / -2953 / -2526) |
| prior_day | reject_native | dib_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 170 | 3323 | 195 | -118 | 844 | 3659 | 878 (106 / 109 / 58) | renko_10, 3941 (-100 / 955 / 4507) |
| prior_day | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1726 (-485 / -1786 / 415) | swing_atr_0.25, 4486 (595 / -1973 / 4160) |
| prior_day | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 208 | 4776 | 180 | -1521 | -450 | 3980 | 1726 (-485 / -1786 / 415) | mom_14, 4509 (883 / 213 / 3193) |
| profile_nodes | break | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 400 (501 / 248 / 2879) | pnf_5, 3118 (1663 / 3670 / 2959) |
| profile_nodes | break_native | tib_25000 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 241 | 3760 | -105 | 2744 | 3238 | 4007 | 400 (501 / 248 / 2879) | pnf_7, 3995 (2467 / -1651 / 1370) |
| profile_nodes | false_break | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 240 | 3719 | 2 | 1783 | 3064 | 3861 | 461 (215 / 127 / 2646) | pnf_5, 3188 (1380 / 3216 / 2452) |
| profile_nodes | false_break_native | rng_40 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 226 | 3965 | -671 | 942 | 823 | 4444 | -985 (-369 / 691 / -266) | pnf_5, 3226 (1531 / 2452 / 3410) |
| profile_nodes | reject | tick_500 | {"tol": 1.0, "conf": "close"} | sym8u / both | 120 / 120 | 277 | 2389 | -1070 | -2196 | -1410 | 2285 | -2322 (-695 / -1289 / -1629) | renko_20, 3360 (110 / -1175 / 115) |
| profile_nodes | reject_native | drb_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 305 | 4170 | 488 | -242 | -812 | 3982 | -2114 (242 / -268 / -2261) | dchg_14, 2893 (-188 / -865 / -2075) |
| profile_nodes | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 242 | 4251 | -587 | -1214 | 1954 | 2715 | -238 (-951 / -277 / 699) | renko_40, 3845 (172 / 438 / 986) |
| profile_nodes | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 242 | 4251 | -587 | -1214 | 1954 | 2715 | -238 (-951 / -277 / 699) | renko_20, 3791 (679 / 1554 / 370) |
| profile_va | break | rng_14 | {"n": 2, "k": 0.25} | sym8u / both | 86 / 86 | 366 | 3975 | -235 | -2980 | 1616 | 3745 | 942 (-557 / -510 / 594) | swing_atr_0.15, 3117 (-257 / 1488 / 3789) |
| profile_va | break_native | rng_28 | {"n": 2, "k": 0.5} | sym15u / both | 120 / 120 | 217 | 4047 | 449 | 1260 | 3137 | 4304 | 408 (181 / -538 / 1432) | renko_14, 3548 (526 / -496 / 3363) |
| profile_va | false_break | vol_4000 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 198 | 3091 | 543 | 151 | 2346 | 3855 | -488 (-8 / -1022 / 884) | pnf_7, 2993 (1062 / 46 / 172) |
| profile_va | false_break_native | tm60 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 192 | 2931 | 898 | 795 | 2798 | 3179 | 167 (719 / -546 / 436) | pnf_7, 2993 (1062 / 46 / 172) |
| profile_va | reject | time_s_10 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 487 | 4134 | 580 | -764 | 1549 | 4242 | 4134 (580 / -764 / 1549) | mom_20, 3236 (-2021 / 1217 / 1231) |
| profile_va | reject_native | tm15 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 263 | 4791 | -360 | 58 | 2424 | 3455 | 496 (-319 / -751 / 638) | wrenko_10, 3266 (-1978 / 637 / 1913) |
| profile_va | retest | vol_350 | {"M": 6, "tol": 0.5} | sym30u / both | 120 / 120 | 196 | 3474 | -389 | 1100 | 3716 | 3326 | 2563 (-364 / -986 / -188) | swing_atr_0.1, 3564 (-541 / -277 / 960) |
| profile_va | retest_native | drb_400 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 222 | 3898 | 285 | -1093 | 3159 | 4441 | 1812 (364 / -189 / 1706) | swing_atr_0.1, 5646 (-87 / 79 / 1170) |
| round | break | vol_500 | {"n": 2, "k": 0.5} | asym20u/10u / both | 120 / 120 | 505 | 8284 | -852 | -683 | 2764 | 7588 | -1242 (135 / 40 / 3906) | renko_10, 4489 (-18 / -1490 / 4165) |
| round | break_native | vol_350 | {"n": 3, "k": 0.25} | sym30u / both | 120 / 120 | 480 | 8082 | 547 | 474 | 3963 | 8386 | -756 (1232 / -1131 / 3547) | renko_10, 4981 (271 / -1652 / 2517) |
| round | false_break | vol_500 | {"M": 1, "k": 0.5} | asym10u/20u / both | 120 / 120 | 531 | 6712 | -926 | -3185 | 1543 | 6684 | -4254 (-176 / -2674 / 2633) | dchg_40, 4373 (-149 / 720 / -3015) |
| round | false_break_native | vol_500 | {"M": 2, "k": 0.5} | asym10u/20u / both | 120 / 120 | 543 | 5669 | -1429 | -2821 | 263 | 7059 | -1106 (-148 / -1342 / 1254) | swing_pct_8, 4309 (-585 / -25 / 1605) |
| round | reject | vsess_120 | {"tol": 0.0, "conf": "close"} | asym20u/10u / both | 120 / 120 | 478 | 4873 | -530 | -1094 | -2797 | 4697 | 847 (232 / -900 / -1221) | renko_10, 8023 (-600 / -3119 / -4002) |
| round | reject_native | vsess_200 | {"tol": 0.5, "conf": "close"} | sym15u / both | 120 / 120 | 540 | 6009 | 257 | -1854 | -806 | 4925 | -1655 (752 / -2068 / 1921) | renko_10, 5935 (-992 / -3347 / -3174) |
| round | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 602 | 6345 | -467 | 1846 | 1394 | 5830 | 3526 (530 / 1339 / -4418) | wrenko_10, 4511 (-485 / 1242 / 4475) |
| round | retest_native | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 617 | 6587 | -614 | 2075 | 217 | 5937 | 2142 (599 / 1912 / -3127) | dchg_14, 5823 (618 / 1627 / 2861) |
| session_hl | break | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 289 | 5222 | 455 | 152 | -732 | 4801 | 577 (804 / 1980 / 1180) | dchg_28, 3699 (1993 / -379 / 1023) |
| session_hl | break_native | cdr_400 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 289 | 5222 | 391 | 152 | -732 | 4801 | 577 (754 / 1980 / 1180) | dchg_28, 3699 (1993 / -379 / 1023) |
| session_hl | false_break | dib_3500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 332 | 4746 | -391 | 493 | 3618 | 4433 | 620 (200 / 840 / 1323) | dchg_10, 4857 (1820 / -135 / 2442) |
| session_hl | false_break_native | dib_3500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 332 | 4746 | -391 | 493 | 3618 | 4433 | 620 (200 / 840 / 1323) | dchg_10, 5417 (1497 / 47 / 2767) |
| session_hl | reject | tick_5000 | {"tol": 0.0, "conf": "body"} | sym8u / both | 120 / 120 | 257 | 2738 | -362 | 1005 | -702 | 2504 | 2476 (1369 / 274 / 1587) | mrenko_20, 2389 (337 / -258 / -28) |
| session_hl | reject_native | dib_40000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 364 | 4887 | -1490 | 1571 | -1284 | 4483 | -2176 (-1585 / -298 / 720) | renko_14, 2597 (1208 / -184 / -816) |
| session_hl | retest | tm30 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 296 | 4319 | 81 | -834 | 117 | 4377 | -1894 (291 / -370 / 590) | renko_10, 5395 (-994 / -1033 / -525) |
| session_hl | retest_native | tm30 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 296 | 4319 | 81 | -834 | 117 | 4377 | -1894 (291 / -370 / 590) | renko_10, 5395 (-994 / -1033 / -525) |
| trendline | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 278 | 3276 | -1202 | 1866 | 826 | 1610 | 344 (-843 / 95 / -965) | kagi_20, 3996 (289 / 1595 / -1677) |
| trendline | break_native | dol_350 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 502 | 2195 | 370 | 797 | 1020 | 1494 | 2195 (370 / 797 / 1020) | kagi_28, 3534 (1905 / 1508 / -2673) |
| trendline | false_break | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 38 | 747 | 244 | -9 | 292 | 380 | -122 (231 / -137 / 144) | pnf_20, 4062 (1560 / 1127 / 1434) |
| trendline | false_break_native | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / long | 120 / 120 | 38 | 747 | 369 | -9 | 292 | 380 | -122 (352 / -137 / 144) | pnf_20, 4692 (42 / 1654 / 1101) |
| trendline | reject | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 264 | 1453 | -1530 | 1954 | 1091 | 3685 | 723 (-887 / 1374 / -17) | urenko_14, 2009 (-383 / -16 / 2214) |
| trendline | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 550 | 1474 | -515 | 1643 | -1940 | -2420 | 1474 (-515 / 1643 / -1940) | urenko_40, 3205 (233 / 64 / 1560) |
| trendline | retest | vrb_70000 | {"M": 10, "tol": 0.5} | sym15u / long | 120 / 120 | 58 | 1280 | 671 | -204 | 375 | 1688 | 89 (399 / -377 / 542) | wrenko_20, 3192 (-7 / -266 / -583) |
| trendline | retest_native | vrb_70000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 71 | 1040 | 315 | -1224 | 971 | 1066 | 290 (223 / -1037 / 164) | kagi_10, 3545 (204 / 994 / 2670) |
| uw_dp | break | rng_10 | {"n": 3, "k": 0.0} | asym20u/10u / both | 120 / 80 | 222 | 3431 | 0 | 0 | 374 | 2879 | 1732 (0 / 0 / -99) | swing_pct_8, 2760 (0 / 0 / 430) |
| uw_dp | break_native | tick_300 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 324 | 3901 | 0 | 0 | -440 | 3278 | 3901 (0 / 0 / -440) | renko_10, 2849 (0 / 0 / 69) |
| uw_dp | false_break | tick_1300 | {"M": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 260 | 1939 | 0 | 0 | 592 | 1789 | 1939 (0 / 0 / 592) | swing_pct_8, 2760 (0 / 0 / 430) |
| uw_dp | false_break_native | tick_1300 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 218 | 2422 | 0 | 0 | -172 | 2062 | 2422 (0 / 0 / -172) | swing_pct_8, 2760 (0 / 0 / 430) |
| uw_dp | reject | tib_1200 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 343 | 2978 | 0 | 0 | -449 | 2772 | 2978 (0 / 0 / -449) | urenko_14, 3468 (0 / 0 / 524) |
| uw_dp | reject_native | drb_25000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 132 | 3082 | 0 | 0 | -414 | 3180 | 1188 (0 / 0 / -377) | mom_14, 3130 (0 / 0 / 439) |
| uw_dp | retest | rng_10 | {"M": 10, "tol": 0.5} | asym15u/30u / both | 120 / 120 | 153 | 3839 | 0 | 0 | 1297 | 3514 | 1524 (0 / 0 / 25) | renko_14, 3397 (0 / 0 / 1119) |
| uw_dp | retest_native | rng_10 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 120 / 120 | 155 | 4448 | 0 | 0 | 599 | 5392 | 2071 (0 / 0 / 261) | renko_14, 3571 (0 / 0 / 1056) |
| uw_ndx | break | vsess_120 | {"n": 1, "k": 0.5} | asym15u/30u / both | 120 / 120 | 164 | 3136 | 0 | -374 | 1450 | 3813 | 812 (0 / -793 / 192) | pnf_56, 3128 (0 / -546 / 405) |
| uw_ndx | break_native | vol_750 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 324 | 3123 | 0 | 144 | 18 | 1482 | 3123 (0 / 144 / 18) | pnf_56, 3128 (0 / -546 / 405) |
| uw_ndx | false_break | vol_750 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 322 | 3245 | 0 | 163 | 419 | 1531 | 3245 (0 / 163 / 419) | pnf_56, 3610 (0 / -751 / 396) |
| uw_ndx | false_break_native | vol_750 | {"M": 3, "k": 0.0} | plain60/60 / both | 60 / 60 | 324 | 3243 | 0 | 273 | 298 | 1603 | 3243 (0 / 273 / 298) | pnf_56, 3723 (0 / -835 / 637) |
| uw_ndx | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | plain60/60 / short | 60 / 60 | 170 | 2315 | 0 | -661 | -1890 | 3272 | 2315 (0 / -661 / -1890) | wrenko_14, 2550 (0 / -500 / 237) |
| uw_ndx | reject_native | tm1800 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 102 | 2410 | 0 | -964 | 135 | 3727 | 765 (0 / -484 / 1125) | renko_10, 2195 (0 / 93 / -634) |
| uw_ndx | retest | vrb_700 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 308 | 2442 | 0 | 186 | -435 | 1648 | 2442 (0 / 186 / -435) | dchg_20, 3552 (0 / 364 / 3186) |
| uw_ndx | retest_native | time_s_5 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 316 | 2788 | 0 | 68 | -1542 | 922 | 2788 (0 / 68 / -1542) | dchg_20, 3552 (0 / 364 / 3186) |
| uw_qqq | break | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 120 / 120 | 197 | 4488 | 0 | -934 | 2894 | 3826 | 51 (0 / -772 / -1102) | pasl_20, 3715 (0 / -228 / 1568) |
| uw_qqq | break_native | tick_300 | {"n": 3, "k": 0.0} | asym20u/10u / both | 120 / 120 | 197 | 4488 | 0 | -934 | 2894 | 3826 | 51 (0 / -772 / -1102) | swing_atr_0.6, 3384 (0 / 197 / 3751) |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 120 / 120 | 202 | 2661 | 0 | 171 | 12 | 4090 | -549 (0 / 679 / 1145) | swing_atr_0.6, 3700 (0 / 196 / 4339) |
| uw_qqq | false_break_native | dib_700 | {"M": 2, "k": 0.5} | sym15u / both | 107 / 107 | 303 | 3135 | 0 | 284 | 1636 | 3176 | 526 (0 / 1004 / 1520) | swing_atr_0.6, 3384 (0 / 197 / 3751) |
| uw_qqq | reject | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 120 / 120 | 177 | 3843 | 0 | -504 | 1611 | 4151 | 168 (0 / -538 / -1156) | pasl_20, 2938 (0 / -522 / -1154) |
| uw_qqq | reject_native | tick_500 | {"tol": 0.0, "conf": "body"} | sym15u / both | 120 / 120 | 177 | 3843 | 0 | -504 | 1611 | 4151 | 168 (0 / -538 / -1156) | renko_14, 2627 (0 / -353 / -1602) |
| uw_qqq | retest | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 120 / 120 | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2049 (0 / -740 / -207) | renko_10, 2871 (0 / 394 / -1559) |
| uw_qqq | retest_native | tick_500 | {"M": 3, "tol": 0.0} | sym8u / both | 120 / 120 | 155 | 3864 | 0 | -483 | 3298 | 3373 | 2049 (0 / -740 / -207) | pnf_40, 2999 (0 / 266 / 904) |
| vwap | break | rng_80 | {"n": 2, "k": 0.5} | sym8u / both | 120 / 120 | 294 | 4569 | 929 | 247 | 3761 | 4575 | 1952 (688 / 2276 / -171) | swing_atr_0.1, 3907 (1270 / 640 / -510) |
| vwap | break_native | cdr_100 | {"n": 2, "k": 0.5} | sym8u / both | 120 / 120 | 395 | 5218 | 1227 | -679 | 3360 | 2889 | -2055 (2074 / 610 / 2182) | swing_pct_5, 6256 (-15 / 937 / -331) |
| vwap | false_break | drb_25000 | {"M": 3, "k": 0.5} | sym15u / short | 120 / 120 | 104 | 1896 | -266 | 1325 | -50 | 1696 | 1479 (-347 / 822 / -491) | pnf_56, 4696 (63 / -174 / 2422) |
| vwap | false_break_native | rng_28 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 298 | 3315 | 761 | 749 | 1258 | 3418 | 130 (1098 / -450 / -418) | pnf_56, 4411 (-108 / -214 / 2319) |
| vwap | reject | vol_500 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 120 / 120 | 336 | 6019 | 1125 | -146 | -239 | 7732 | -2154 (654 / 308 / 1462) | swing_atr_0.1, 5627 (-707 / -1407 / 502) |
| vwap | reject_native | tm60 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 302 | 5838 | -1468 | 1495 | -1469 | 6714 | 792 (-972 / 691 / -126) | dchg_10, 5661 (-737 / 1031 / -1179) |
| vwap | retest | tm15 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 353 | 4113 | 1019 | 662 | 1923 | 5583 | 315 (388 / 522 / 3723) | swing_pct_35, 3938 (362 / 749 / 1444) |
| vwap | retest_native | tm15 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 352 | 4260 | 459 | 1038 | 2222 | 6362 | -597 (121 / 1224 / 3284) | swing_pct_8, 4085 (-1384 / 75 / 3789) |
| vwap_bands | break | cusum_20 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 483 | 5272 | -1175 | 248 | 3588 | 4396 | -1720 (-723 / -1 / -131) | mom_20, 6544 (86 / 1981 / 5311) |
| vwap_bands | break_native | drb_400 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 545 | 5721 | -772 | -2232 | 2651 | 4494 | 924 (-1594 / -3864 / -344) | pnf_10, 5104 (611 / 739 / -2380) |
| vwap_bands | false_break | time_m_3 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 417 | 3930 | -741 | 2914 | 1634 | 5148 | 1309 (-520 / 1453 / 1274) | swing_atr_0.6, 3977 (1234 / -534 / 5712) |
| vwap_bands | false_break_native | tick_3200 | {"M": 3, "k": 0.5} | sym8u / both | 120 / 120 | 419 | 5308 | -523 | -797 | 1777 | 7540 | -2920 (-973 / -250 / -1522) | swing_pct_5, 3970 (781 / 1565 / -1673) |
| vwap_bands | reject | tick_300 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 120 / 120 | 481 | 6944 | 1737 | -351 | 2059 | 7316 | 1137 (1263 / 2243 / -2441) | renko_14, 4979 (-788 / -533 / -3753) |
| vwap_bands | reject_native | vol_500 | {"tol": 0.5, "conf": "close"} | asym10u/20u / both | 120 / 120 | 512 | 6769 | -741 | 751 | 2018 | 2515 | 734 (-79 / -1478 / -714) | dchg_14, 6479 (-1030 / 939 / 1990) |
| vwap_bands | retest | vol_500 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 475 | 5871 | -47 | -3369 | -2356 | 8027 | -62 (1738 / -1272 / -821) | mom_28, 4662 (1140 / -4 / 2687) |
| vwap_bands | retest_native | tib_15000 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 452 | 5820 | -431 | 1126 | 1466 | 4714 | -2237 (87 / -866 / 1544) | swing_pct_35, 4161 (43 / -829 / 1978) |
| week_month | break | rng_14 | {"n": 2, "k": 0.0} | asym20u/10u / both | 120 / 108 | 76 | 2603 | -154 | 112 | -620 | 2562 | 1293 (229 / -148 / 406) | renko_14, 2684 (577 / 625 / -670) |
| week_month | break_native | rng_14 | {"n": 2, "k": 0.0} | asym20u/10u / both | 120 / 108 | 76 | 2603 | -154 | 112 | -620 | 2562 | 1293 (229 / -148 / 406) | renko_14, 3092 (228 / -190 / -164) |
| week_month | false_break | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1070 (-164 / -713 / 1240) | renko_14, 2049 (-42 / -1075 / -595) |
| week_month | false_break_native | tib_1200 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 77 | 2427 | -395 | -156 | 1122 | 1884 | 1070 (-164 / -713 / 1240) | renko_14, 2049 (-42 / -1075 / -595) |
| week_month | reject | vol_1100 | {"tol": 0.5, "conf": "close"} | sym8u / both | 120 / 120 | 68 | 1536 | 868 | -885 | -2434 | 2056 | 860 (756 / 458 / -254) | wrenko_10, 1812 (674 / -92 / 992) |
| week_month | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 68 / 68 | 136 | 1501 | -154 | 308 | 1349 | 1149 | 1408 (1 / -181 / 1835) | mrenko_10, 2131 (988 / -272 / -1646) |
| week_month | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 80 | 2596 | 90 | -1765 | -1604 | 1598 | 864 (-101 / -1173 / -517) | mom_10, 2393 (223 / -4 / -3) |
| week_month | retest_native | tick_300 | {"M": 3, "tol": 0.5} | sym8u / both | 120 / 120 | 68 | 2858 | 1034 | 105 | -852 | 1578 | 431 (940 / 10 / -192) | mom_10, 2708 (-479 / 411 / -884) |

### London - supply/demand modules by definition (variant = entry type)
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | reject | vrb_700 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / long | 60 / 60 | 32 | 619 | -187 | -147 | -283 | 567 | 619 (-187 / -147 / -283) | no reversal row has trades |
| sd5 | reject_native | vrb_700 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / long | 60 / 60 | 32 | 619 | -187 | -147 | -283 | 567 | 619 (-187 / -147 / -283) | no reversal row has trades |
| sdx15 | break | dol_6000 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 86 | 1280 | 474 | -825 | -291 | 1218 | 731 (430 / -1172 / -939) | kagi_80, 2579 (645 / -535 / -454) |
| sdx15 | lim_mid | dol_6000 | {"d": "B", "F": 9, "tgt": "opp"} | sym15u / both | 120 / 120 | 43 | 726 | -465 | 113 | -1133 | 424 | 706 (-553 / 272 / -842) | kagi_80, 2214 (105 / -102 / 862) |
| sdx15 | lim_prox | dol_6000 | {"d": "B", "F": 9, "tgt": "opp"} | sym15u / both | 120 / 120 | 42 | 864 | -465 | -10 | -735 | 203 | 621 (-492 / 205 / -444) | kagi_112, 1722 (-776 / 900 / -2080) |
| sdx15 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 386 | 1867 | 1258 | 1001 | 193 | 1192 | 1867 (1258 / 1001 / 193) | kagi_10, 1336 (713 / -70 / 1061) |
| sdx15 | rej_flow | vrb_700 | {"d": "E", "F": 9} | plain60/60 / both | 60 / 60 | 200 | 1025 | 1001 | -160 | -409 | -111 | 1025 (1001 / -160 / -409) | wrenko_14, 950 (-225 / 789 / 232) |
| sdx15 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 460 | 2407 | 914 | -42 | -1257 | 1411 | 2407 (914 / -42 / -1257) | pnf_7, 1444 (-1063 / -311 / 1126) |
| sdx15 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 460 | 2407 | 914 | -42 | -1257 | 1411 | 2407 (914 / -42 / -1257) | mrenko_10, 1391 (-373 / -860 / 1022) |
| sdx15 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 31 | 642 | 135 | -390 | -419 | -34 | -321 (16 / -483 / -449) | kagi_80, 1895 (-252 / -737 / -146) |
| sdx3 | break | vrb_700 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 215 | 1893 | -190 | 394 | 77 | 3132 | 973 (-16 / -220 / 609) | kagi_80, 3088 (-168 / 318 / -923) |
| sdx3 | lim_mid | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 261 | 2179 | -232 | 794 | 1282 | 4340 | 1972 (-55 / 2352 / 178) | kagi_10, 3690 (400 / 1269 / -2651) |
| sdx3 | lim_prox | dol_500 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 254 | 2542 | -660 | 336 | 238 | 4583 | 715 (-635 / 1574 / 686) | urenko_10, 4320 (49 / 1608 / -1461) |
| sdx3 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 238 | 2142 | 2164 | 1162 | -922 | 2240 | 1000 (1569 / 409 / 723) | urenko_10, 1505 (-172 / -1100 / -778) |
| sdx3 | rej_flow | dol_500 | {"d": "B", "F": 9} | sym15u / both | 120 / 120 | 96 | 998 | 238 | -855 | 370 | 1341 | 169 (432 / -929 / 522) | wrenko_20, 1238 (-32 / -410 / -333) |
| sdx3 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 251 | 2133 | 2444 | 1667 | -962 | 911 | 720 (1728 / -292 / 1412) | kagi_10, 3620 (859 / 1354 / 441) |
| sdx3 | rej_zone | vrb_700 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 219 | 3956 | 1228 | 1976 | -779 | 5574 | 1682 (823 / 1518 / -1000) | urenko_10, 2671 (-57 / -178 / -380) |
| sdx3 | retest | vrb_700 | {"d": "B", "M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 73 | 989 | -432 | -494 | -156 | 965 | 989 (-432 / -494 / -156) | mrenko_20, 1881 (-279 / 106 / 782) |
| sdx30 | break | dol_6000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 50 | 22 | -737 | -887 | -5 | -44 | -7 (-607 / -976 / -121) | kagi_112, 1445 (411 / -743 / -552) |
| sdx30 | lim_mid | dol_6000 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 97 | 1708 | 367 | 522 | 155 | 1960 | 550 (242 / -263 / 208) | kagi_56, 1852 (-92 / 580 / -256) |
| sdx30 | lim_prox | dol_6000 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 88 | 1737 | 253 | -133 | -244 | 1808 | 1420 (248 / -393 / -135) | kagi_28, 3089 (-6 / 17 / 1634) |
| sdx30 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / short | 120 / 120 | 57 | 611 | 549 | 195 | -311 | 910 | -364 (373 / -29 / -620) | frenko_28, 712 (-95 / -341 / 622) |
| sdx30 | rej_flow | dol_350 | {"d": "A", "F": 0} | sym15u / both | 120 / 120 | 31 | 595 | 340 | 318 | -802 | 812 | 177 (231 / 192 / -846) | wrenko_14, 633 (-473 / 306 / 239) |
| sdx30 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 119 | 1080 | 969 | -556 | 331 | 1331 | -271 (681 / -960 / 199) | kagi_40, 1413 (260 / -189 / -77) |
| sdx30 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 101 | 340 | -6 | -81 | -413 | 425 | 340 (-6 / -81 / -413) | kagi_56, 1016 (-341 / 208 / 498) |
| sdx5 | break | dol_350 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 175 | 2163 | 178 | 975 | 357 | 1809 | 128 (467 / 1052 / -370) | urenko_14, 3068 (197 / 1069 / 1759) |
| sdx5 | lim_mid | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 611 | 2358 | 295 | 579 | 398 | 3264 | 2358 (295 / 579 / 398) | kagi_80, 2364 (118 / 1141 / -997) |
| sdx5 | lim_prox | dol_350 | {"d": "A", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 572 | 2492 | -318 | -767 | 467 | 2734 | 2492 (-318 / -767 / 467) | frenko_40, 2470 (-182 / -1246 / 1005) |
| sdx5 | rej | vrb_700 | {"d": "B", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 216 | 2671 | -193 | -1603 | 1240 | 2253 | 2671 (-193 / -1603 / 1240) | frenko_40, 2268 (121 / -280 / 338) |
| sdx5 | rej_flow | vrb_700 | {"d": "B", "F": 9} | plain60/60 / both | 60 / 60 | 83 | 1379 | -251 | -555 | 1072 | 759 | 1379 (-251 / -555 / 1072) | wrenko_14, 1086 (-347 / -317 / 939) |
| sdx5 | rej_native | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 180 | 1656 | -68 | 634 | -1535 | 653 | 228 (206 / -479 / -840) | frenko_40, 2126 (-203 / -436 / 139) |
| sdx5 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 180 | 1656 | -68 | 634 | -1535 | 653 | 228 (206 / -479 / -840) | kagi_56, 1959 (163 / 674 / -953) |
| sdx5 | retest | vrb_700 | {"d": "A", "M": 6, "tol": 0.5} | plain60/60 / short | 60 / 60 | 53 | 1167 | 509 | -451 | -133 | 1269 | 1167 (509 / -451 / -133) | kagi_20, 3004 (-581 / -1198 / -562) |
| sdx60 | lim_mid | dol_6000 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 44 | 1137 | -329 | -302 | -87 | 1906 | 532 (-371 / -479 / 192) | kagi_56, 2417 (-215 / 125 / -1666) |
| sdx60 | lim_prox | dol_6000 | {"d": "A", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 43 | 1665 | -258 | -544 | 57 | 2252 | 857 (-286 / -647 / 297) | pnf_14, 3080 (290 / 236 / -323) |
| sdx60 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 120 / 120 | 32 | 1124 | -130 | -222 | -19 | 853 | 111 (32 / -22 / -6) | mrenko_10, 538 (-208 / -141 / 111) |
| sdx60 | rej_flow | dol_6000 | {"d": "E", "F": 9} | sym15u / both | 120 / 120 | 33 | 411 | -239 | -225 | -389 | 457 | 102 (-163 / -62 / -512) | wrenko_10, -103 (-459 / 284 / -944) |
| sdx60 | rej_native | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / long | 120 / 120 | 66 | 759 | -78 | 608 | 699 | 817 | 225 (-65 / 200 / 568) | pnf_20, 2072 (-291 / 171 / -795) |
| sdx60 | rej_zone | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 120 / 120 | 66 | 759 | -78 | 608 | 699 | 817 | 225 (-65 / 200 / 568) | pnf_20, 2072 (-291 / 171 / -795) |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 137 | 1083 | 54 | -926 | -613 | 1506 | -513 (-43 / -752 / -461) | kagi_112, 2263 (-119 / -618 / -1891) |
| sdx_renko28 | lim_mid | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / long | 60 / 60 | 389 | 1533 | 221 | 349 | 249 | 2284 | 1533 (221 / 349 / 249) | kagi_112, 2991 (-88 / -812 / -829) |
| sdx_renko28 | lim_prox | dol_350 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / long | 120 / 120 | 138 | 1371 | -300 | 901 | -378 | 2329 | 1040 (-445 / 1817 / -432) | kagi_112, 3623 (-359 / -657 / -693) |
| sdx_renko28 | rej | vrb_700 | {"d": "B", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 99 | 1044 | -369 | -467 | 1900 | 1319 | 1044 (-369 / -467 / 1900) | mrenko_14, 1095 (778 / -472 / 371) |
| sdx_renko28 | rej_flow | dol_350 | {"d": "E", "F": 0} | plain60/60 / both | 60 / 60 | 137 | 639 | 351 | -677 | 1111 | 521 | 639 (351 / -677 / 1111) | wrenko_10, 445 (-26 / -150 / 326) |
| sdx_renko28 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 244 | 1564 | -622 | 717 | -706 | 1249 | -1657 (-248 / -515 / -819) | pnf_28, 1940 (-28 / 921 / -908) |
| sdx_renko28 | rej_zone | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / long | 120 / 120 | 115 | 626 | 366 | 955 | -462 | 995 | -460 (410 / 920 / 194) | pnf_28, 1940 (-28 / 921 / -908) |
| sdx_renko28 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 34 | 331 | -200 | 146 | 609 | 815 | 114 (-135 / 97 / 90) | pnf_5, 1772 (-155 / -1444 / -732) |
| sdx_rng28 | break | dol_500 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 237 | 1402 | 1378 | 584 | -225 | 1598 | -1610 (1105 / -899 / 1399) | lbrk_3_20, 3527 (904 / -349 / 756) |
| sdx_rng28 | lim_mid | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 798 | 2508 | 680 | -162 | -796 | 2678 | 2508 (680 / -162 / -796) | pnf_14, 3467 (-998 / 2482 / -838) |
| sdx_rng28 | lim_prox | dol_350 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 280 | 2430 | -369 | -1659 | 262 | 2681 | 1879 (-648 / -201 / -258) | wrenko_10, 2565 (-697 / 820 / 191) |
| sdx_rng28 | rej | vrb_40000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 33 | 169 | -96 | -153 | 412 | 83 | 160 (-74 / -171 / 68) | kagi_56, 1361 (603 / 353 / -205) |
| sdx_rng28 | rej_flow | vrb_700 | {"d": "E", "F": 0} | plain60/60 / both | 60 / 60 | 304 | 1173 | 22 | 186 | 46 | 1250 | 1173 (22 / 186 / 46) | wrenko_14, 1446 (811 / -32 / 1520) |
| sdx_rng28 | rej_native | dol_6000 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 191 | 843 | 79 | -84 | 1784 | -184 | 790 (42 / -833 / -759) | mrenko_10, 2075 (-573 / -292 / 1394) |
| sdx_rng28 | rej_zone | dol_500 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 520 | 594 | -203 | 1801 | -475 | 120 | 594 (-203 / 1801 / -475) | mrenko_10, 2075 (-573 / -292 / 1394) |
| sdx_rng28 | retest | vrb_40000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 39 | 1132 | 134 | -441 | -36 | 1167 | 588 (118 / -542 / -377) | pnf_7, 2538 (635 / -1058 / -796) |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 172 | 1168 | 654 | -1530 | 1775 | 1858 | -544 (525 / -652 / 183) | frenko_28, 2638 (-348 / -213 / 189) |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 209 | 3784 | 896 | 457 | 888 | 4785 | 580 (688 / 391 / 115) | kagi_56, 3366 (163 / 465 / 1569) |
| sdx_vol1100 | lim_prox | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 207 | 2676 | 938 | 558 | 851 | 3567 | 145 (893 / 617 / -74) | kagi_56, 3123 (198 / -474 / 859) |
| sdx_vol1100 | rej | dol_350 | {"d": "B", "F": 0, "tol": 0.5} | plain60/60 / short | 60 / 60 | 55 | 894 | -79 | -60 | 77 | 933 | 894 (-79 / -60 / 77) | kagi_14, 1551 (-175 / 755 / -1556) |
| sdx_vol1100 | rej_flow | dol_350 | {"d": "E", "F": 0} | sym15u / short | 120 / 120 | 67 | 1136 | -141 | -656 | 353 | 1458 | 401 (-112 / -163 / 58) | wrenko_14, 887 (-67 / -326 / 37) |
| sdx_vol1100 | rej_native | dol_350 | {"d": "B", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 114 | 1070 | -345 | -635 | -277 | 883 | 105 (-314 / -506 / -69) | kagi_56, 2477 (1072 / -510 / -2133) |
| sdx_vol1100 | rej_zone | dol_500 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 429 | 1189 | -916 | 1584 | -1594 | 1449 | 1189 (-916 / 1584 / -1594) | kagi_56, 2477 (1072 / -510 / -2133) |
| sdx_vol1100 | retest | vrb_40000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 34 | 933 | 49 | 88 | -155 | 752 | 425 (53 / 15 / -573) | kagi_10, 1778 (-246 / -234 / -609) |
| zones | break | vol_4000 | {"n": 1, "k": 0.5} | sym8u / both | 120 / 120 | 113 | 2090 | 229 | 143 | 393 | 2008 | 1164 (-119 / 197 / 1317) | pnf_10, 1878 (159 / 1524 / -251) |
| zones | break_native | rng_28 | {"n": 1, "k": 0.5} | sym15u / both | 120 / 120 | 171 | 2595 | -316 | -372 | -1349 | 3591 | -296 (-329 / -1015 / -1101) | renko_14, 2650 (-114 / -424 / -736) |
| zones | false_break | rng_10 | {"M": 1, "k": 0.5} | sym30u / both | 120 / 120 | 162 | 2098 | -451 | -622 | -1038 | 3686 | 800 (-479 / -893 / 348) | pnf_14, 1617 (187 / -421 / -1537) |
| zones | false_break_native | vol_6000 | {"M": 3, "k": 0.0} | sym8u / both | 120 / 120 | 112 | 1825 | -112 | -996 | 314 | 2093 | 521 (-504 / -592 / 965) | pnf_14, 1617 (133 / -421 / -1537) |
| zones | reject | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 75 / 120 | 201 | 3168 | 225 | -131 | -1006 | 2880 | 869 (472 / -549 / -45) | renko_10, 2290 (-249 / 654 / -723) |
| zones | reject_native | rng_10 | {"tol": 0.0, "conf": "close"} | asym10u/20u / both | 75 / 120 | 201 | 3168 | 225 | -131 | -1006 | 2880 | 869 (472 / -549 / -45) | dchg_56, 2754 (-160 / 350 / 1158) |
| zones | retest | tib_1200 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 128 | 2375 | -1292 | 285 | 258 | 2085 | 1088 (-1398 / 422 / -499) | mom_14, 1532 (-958 / 103 / 190) |
| zones | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 102 | 2223 | -765 | 332 | -877 | 1559 | 1058 (-825 / -107 / 50) | urenko_40, 1984 (-293 / -782 / -1059) |

### London - other level modules
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fib15 | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 237 | 2095 | -547 | 597 | -492 | 4406 | 1520 (-478 / -1238 / -248) | kagi_10, 3282 (-364 / -1291 / 590) |
| fib15 | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 232 | 1606 | 316 | 366 | 776 | 3291 | 447 (341 / -2042 / -247) | kagi_112, 2716 (-400 / -119 / -1799) |
| fib15 | false_break | vrb_40000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 674 | 28 | -183 | -570 | 542 | 674 (28 / -183 / -570) | kagi_56, 4142 (430 / 262 / -578) |
| fib15 | false_break_native | vrb_40000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 674 | 42 | -183 | -570 | 542 | 674 (42 / -183 / -570) | kagi_56, 3974 (399 / 289 / -884) |
| fib15 | pullback | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 194 | 1410 | -108 | -107 | -1066 | 1100 | 191 (-312 / -790 / -1468) | wrenko_20, 1233 (-351 / -828 / -503) |
| fib15 | pullback_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 202 | 1630 | 223 | 224 | -1394 | 1048 | 456 (3 / -890 / -1698) | kagi_28, 2553 (-505 / -2114 / -1143) |
| fib15 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 236 | 3372 | -149 | -168 | 1413 | 3851 | 1562 (99 / -957 / 911) | kagi_10, 3712 (-473 / -683 / 2041) |
| fib15 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 249 | 3703 | -555 | 839 | 2164 | 4988 | 1475 (-64 / -728 / 3210) | wrenko_20, 2516 (-870 / 1390 / 290) |
| fib15 | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 231 | 1999 | 142 | 1014 | -32 | 877 | -1620 (419 / -379 / -2009) | kagi_80, 3012 (-328 / 676 / -1536) |
| fib15 | retest_native | dol_350 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 241 | 1983 | -18 | 2260 | -875 | -23 | 1205 (712 / -976 / -1347) | kagi_80, 2792 (329 / 815 / -1874) |
| fib5 | break | dol_6000 | {"n": 3, "k": 0.5} | plain60/60 / long | 60 / 60 | 184 | 1137 | -137 | -579 | 500 | 947 | 1137 (-137 / -579 / 500) | kagi_56, 2478 (923 / 588 / -748) |
| fib5 | break_native | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 263 | 980 | 969 | -354 | -710 | 32 | 52 (1198 / -301 / -588) | kagi_56, 2474 (665 / -63 / 652) |
| fib5 | false_break | vrb_40000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 62 | 781 | -37 | -779 | 4 | 1035 | 772 (44 / -669 / -303) | kagi_80, 3383 (715 / 310 / -1361) |
| fib5 | false_break_native | vrb_40000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 62 | 781 | -23 | -779 | 4 | 1035 | 772 (58 / -669 / -303) | kagi_80, 3196 (963 / 251 / -520) |
| fib5 | pullback | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 211 | 1105 | -557 | 506 | 2880 | 787 | 158 (43 / 271 / 3622) | urenko_20, 1590 (1243 / 113 / 223) |
| fib5 | pullback_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 226 | 1176 | -372 | 177 | 1730 | 655 | -1652 (177 / -257 / 2957) | lbrk_3_20, 1164 (677 / -276 / 1144) |
| fib5 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 252 | 2234 | 34 | -487 | 1302 | 1444 | 698 (328 / -1030 / 105) | urenko_56, 2344 (186 / -2299 / -368) |
| fib5 | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 265 | 2146 | 246 | -1025 | 366 | 781 | 1390 (1176 / 59 / 1) | urenko_56, 2128 (-618 / 172 / -2575) |
| fib5 | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 244 | 2158 | 46 | 3215 | -368 | 1423 | -108 (12 / 3075 / -762) | urenko_28, 2243 (323 / 944 / -1709) |
| fib5 | retest_native | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 244 | 2158 | 46 | 3215 | -368 | 1423 | -108 (12 / 3075 / -762) | kagi_80, 3002 (919 / 626 / -2031) |
| fib60 | break | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 187 | 1894 | -2 | 1604 | -1096 | 1487 | 1670 (213 / 35 / -785) | lbrk_3_10, 2830 (528 / -2082 / 186) |
| fib60 | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 183 | 1539 | -1154 | -483 | -696 | -688 | -292 (-857 / -1564 / 871) | lbrk_3_10, 2648 (1046 / -1546 / -110) |
| fib60 | false_break | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 198 | 1925 | -325 | -310 | -229 | 813 | -186 (-425 / -1287 / 813) | kagi_14, 2654 (1181 / 1317 / -829) |
| fib60 | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 199 | 1742 | -741 | -208 | 264 | 99 | -227 (-570 / -1455 / 1418) | kagi_14, 2749 (1588 / 1316 / -68) |
| fib60 | pullback | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 134 | 367 | -377 | 226 | -1391 | -263 | -884 (1 / 240 / -1118) | kagi_10, 1205 (-627 / -79 / -654) |
| fib60 | pullback_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 74 | 348 | -423 | -23 | -587 | -473 | -404 (-165 / -181 / -978) | kagi_80, 1231 (-694 / 107 / -2246) |
| fib60 | reject | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 442 | 1799 | 225 | -696 | 1370 | 1643 | 1799 (225 / -696 / 1370) | kagi_56, 2314 (-527 / -402 / -2571) |
| fib60 | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 510 | 1125 | 963 | -1061 | -1064 | 498 | 1125 (963 / -1061 / -1064) | kagi_56, 2299 (-228 / -443 / -3051) |
| fib60 | retest | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 395 | 2543 | 120 | -359 | 2776 | 1391 | 2543 (120 / -359 / 2776) | kagi_80, 3143 (228 / 413 / -1867) |
| fib60 | retest_native | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 416 | 1941 | 471 | -655 | 2481 | 638 | 1941 (471 / -655 / 2481) | kagi_80, 3612 (-726 / 592 / -710) |
| fibr_dev | break | dol_350 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 638 | 1333 | -440 | -1715 | 485 | -1256 | 1333 (-440 / -1715 / 485) | lbrk_3_10, 2661 (-156 / 1064 / -57) |
| fibr_dev | break_native | dol_350 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 638 | 1333 | -440 | -1715 | 485 | -1256 | 1333 (-440 / -1715 / 485) | lbrk_3_10, 2661 (-156 / 1064 / -57) |
| fibr_dev | false_break | vrb_700 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 631 | 1103 | 7 | 938 | -1172 | -403 | 1103 (7 / 938 / -1172) | kagi_112, 1774 (127 / -330 / -1672) |
| fibr_dev | false_break_native | vrb_700 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 622 | 978 | -235 | 1002 | -423 | -1125 | 978 (-235 / 1002 / -423) | kagi_40, 2530 (-963 / -884 / -3116) |
| fibr_dev | reject | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 664 | 1364 | 497 | -2084 | -2923 | -2178 | 1364 (497 / -2084 / -2923) | kagi_10, 3197 (564 / -144 / -10) |
| fibr_dev | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 685 | 2174 | -110 | -1858 | -2517 | -951 | 2174 (-110 / -1858 / -2517) | pnf_40, 1943 (13 / 365 / -532) |
| fibr_dev | retest | vrb_700 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 596 | 2182 | 330 | 405 | -2952 | 2681 | 2182 (330 / 405 / -2952) | urenko_14, 2751 (131 / -652 / -1202) |
| fibr_dev | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 529 | 1904 | -106 | -433 | -3800 | 2933 | 1904 (-106 / -433 / -3800) | kagi_80, 2228 (-96 / -768 / -515) |
| fibr_pd | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 197 | 2609 | 794 | 306 | 1054 | 1531 | -571 (890 / -127 / -111) | urenko_14, 2784 (1325 / -554 / -802) |
| fibr_pd | break_native | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 202 | 1876 | 434 | 772 | -2073 | 2016 | 1250 (980 / -471 / -1417) | pnf_5, 3135 (51 / 239 / -950) |
| fibr_pd | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / long | 120 / 120 | 100 | 1009 | 672 | 664 | -936 | 1250 | 1 (600 / 362 / -86) | pnf_28, 1922 (-666 / -75 / -1) |
| fibr_pd | false_break_native | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 189 | 1356 | 683 | -739 | -556 | 790 | 444 (419 / 296 / 1582) | pnf_28, 1857 (-580 / 114 / -478) |
| fibr_pd | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 187 | 1845 | 992 | -838 | 174 | 2783 | 638 (804 / -531 / 1044) | urenko_20, 2146 (523 / -1414 / -889) |
| fibr_pd | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 213 | 2259 | -9 | 197 | -2770 | 3540 | -252 (33 / -986 / -1270) | kagi_56, 3803 (503 / 321 / -2364) |
| fibr_pd | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 174 | 1511 | 545 | 679 | 93 | 2070 | -369 (179 / 454 / -1148) | kagi_80, 2461 (865 / 467 / -2371) |
| fibr_pd | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 184 | 2598 | 473 | 221 | -1721 | 2726 | 60 (283 / 31 / -1378) | kagi_40, 2979 (-199 / -788 / -742) |
| piv_cama | break | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 216 | 2096 | -93 | -648 | -4345 | 2382 | -330 (-228 / -999 / 12) | kagi_112, 2487 (-355 / -657 / -3166) |
| piv_cama | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 216 | 2096 | -93 | -648 | -4345 | 2382 | -330 (-228 / -999 / 12) | kagi_112, 2487 (-439 / -657 / -3166) |
| piv_cama | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 215 | 2317 | -220 | -670 | -4345 | 2604 | -330 (-348 / -1021 / 37) | kagi_112, 2442 (-589 / -486 / -3125) |
| piv_cama | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 215 | 2317 | -220 | -670 | -4345 | 2604 | -330 (-348 / -1021 / 37) | kagi_112, 2442 (-536 / -486 / -3125) |
| piv_cama | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / long | 60 / 60 | 212 | 611 | 106 | 237 | -584 | 1040 | 611 (106 / 237 / -584) | mrenko_14, 1882 (-418 / 222 / -1471) |
| piv_cama | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 222 | 967 | -376 | -481 | -36 | 319 | -916 (-518 / -1938 / -1374) | kagi_56, 2839 (-84 / -1811 / 959) |
| piv_cama | retest | vrb_700 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 342 | 2093 | -345 | -1426 | -2230 | 2696 | 2093 (-345 / -1426 / -2230) | kagi_40, 3129 (-577 / 292 / 2082) |
| piv_cama | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 342 | 2093 | -345 | -1426 | -2230 | 2696 | 2093 (-345 / -1426 / -2230) | kagi_40, 3129 (-577 / 292 / 2082) |
| piv_floor | break | vrb_700 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 177 | 1631 | 629 | 672 | -2120 | 3367 | -320 (514 / -234 / -354) | kagi_10, 2773 (-876 / -2336 / -4004) |
| piv_floor | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 180 | 1201 | -677 | -896 | -1036 | 812 | -242 (-546 / -563 / -645) | kagi_10, 2773 (-876 / -2336 / -4004) |
| piv_floor | false_break | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 180 | 1733 | -558 | -772 | -867 | 1077 | -422 (-545 / -411 / -373) | wrenko_14, 2587 (226 / -1570 / -3011) |
| piv_floor | false_break_native | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 174 | 2284 | -569 | -927 | -520 | 1817 | -486 (-523 / -469 / 160) | wrenko_14, 2587 (226 / -1570 / -3011) |
| piv_floor | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 74 | 837 | 185 | -344 | -1186 | 783 | 762 (177 / -27 / -893) | urenko_28, 1156 (133 / 855 / 1142) |
| piv_floor | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 217 | 2321 | 417 | 1571 | -187 | 1903 | 1123 (794 / -871 / 110) | kagi_80, 2290 (720 / 70 / -1278) |
| piv_floor | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 161 | 2144 | -132 | -35 | 808 | 3016 | -333 (-47 / -592 / -95) | kagi_14, 3948 (347 / -890 / -497) |
| piv_floor | retest_native | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 169 | 2046 | -23 | -119 | -188 | 2599 | -686 (-69 / -151 / -477) | kagi_14, 3948 (347 / -890 / -497) |
| piv_wf | break | dol_6000 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 203 | 1777 | 321 | -959 | -656 | 1968 | 1777 (321 / -959 / -656) | kagi_80, 2656 (-333 / -1729 / -430) |
| piv_wf | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 214 | 1895 | -1012 | -1008 | 888 | 1164 | -20 (-556 / -1369 / 621) | urenko_40, 2880 (-608 / -890 / -364) |
| piv_wf | false_break | vrb_40000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 62 | 597 | -102 | -261 | -130 | 354 | 297 (-41 / -360 / -571) | kagi_80, 2887 (-211 / -1555 / -414) |
| piv_wf | false_break_native | vrb_40000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 55 | 771 | -227 | -93 | -303 | 524 | 506 (-163 / -206 / -434) | kagi_80, 2636 (-144 / -1563 / -448) |
| piv_wf | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 169 | 971 | -395 | -325 | -572 | 2259 | -1315 (-391 / -650 / 130) | urenko_14, 1472 (651 / 362 / -430) |
| piv_wf | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 212 | 1244 | 70 | 21 | 103 | 1481 | -1604 (124 / -1388 / -1410) | kagi_56, 3435 (-674 / 1015 / -1014) |
| piv_wf | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 86 | 1043 | -566 | -450 | -1203 | 834 | 231 (-254 / -314 / -643) | kagi_80, 2164 (-5 / -1635 / -1545) |
| piv_wf | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 86 | 1043 | -566 | -450 | -1203 | 834 | 231 (-254 / -314 / -643) | kagi_80, 3307 (-134 / -1185 / -1620) |
| swcluster | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 53 | 1499 | -295 | -392 | -37 | 1271 | 604 (-82 / -501 / -1204) | kagi_56, 1670 (-518 / -793 / -14) |
| swcluster | break_native | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 51 | 728 | 188 | -384 | -580 | 510 | 489 (264 / -551 / -867) | kagi_80, 1656 (-586 / -594 / -193) |
| swcluster | false_break | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 58 | 554 | -70 | 239 | 608 | 304 | 485 (57 / 368 / 1032) | kagi_80, 1459 (-140 / -948 / 37) |
| swcluster | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 81 | 568 | 254 | 286 | 1488 | 597 | 568 (254 / 286 / 1488) | kagi_80, 1438 (-192 / -927 / 429) |
| swcluster | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 33 | 557 | -385 | -162 | -263 | 677 | 557 (-385 / -162 / -263) | kagi_10, 1206 (-808 / 524 / -708) |
| swcluster | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 102 | 932 | -166 | -272 | -1458 | 1185 | 932 (-166 / -272 / -1458) | frenko_40, 1389 (5 / -698 / -300) |
| swcluster | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 41 | 705 | -800 | -658 | 235 | 428 | 470 (-567 / -583 / -246) | kagi_14, 1227 (-296 / 686 / 80) |
| swcluster | retest_native | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 70 | 855 | 168 | 159 | 144 | 341 | 855 (168 / 159 / 144) | kagi_40, 1228 (47 / -874 / -370) |
| swsr15 | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 230 | 2311 | 223 | -327 | -8 | 3157 | -1371 (246 / -794 / -3180) | mrenko_20, 2294 (97 / -2202 / -2829) |
| swsr15 | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 237 | 2596 | 79 | -84 | -1309 | 3896 | -1063 (573 / 495 / -1363) | kagi_10, 2675 (-145 / -1131 / -495) |
| swsr15 | false_break | vrb_40000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 61 | 975 | 77 | -503 | -167 | 1197 | 810 (90 / -323 / -451) | kagi_112, 1830 (-590 / -550 / -3102) |
| swsr15 | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / long | 120 / 120 | 117 | 1149 | 99 | 736 | 718 | 1791 | 573 (380 / 254 / 615) | urenko_80, 1864 (-177 / 269 / -551) |
| swsr15 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 241 | 2478 | 214 | -863 | -296 | 4375 | -1238 (516 / -89 / -1408) | mrenko_10, 2378 (-1258 / -508 / 212) |
| swsr15 | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 225 | 2243 | 161 | -71 | 348 | 2515 | -478 (-705 / -445 / -470) | kagi_28, 2619 (-292 / -295 / -2422) |
| swsr15 | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 215 | 3007 | -662 | -672 | -105 | 3909 | -1618 (382 / -714 / -1331) | mrenko_20, 3116 (-742 / -538 / 263) |
| swsr15 | retest_native | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 233 | 1952 | -199 | -97 | 68 | 1798 | -859 (354 / -754 / -565) | pnf_28, 2587 (-36 / 852 / 31) |
| swsr5 | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 106 | 1216 | -22 | 17 | -897 | 1705 | 1075 (-5 / -50 / 437) | kagi_80, 1969 (-49 / 176 / -191) |
| swsr5 | break_native | vrb_700 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 631 | 1132 | 755 | -1358 | -88 | 258 | 1132 (755 / -1358 / -88) | urenko_14, 2084 (-669 / -1018 / 182) |
| swsr5 | false_break | dol_500 | {"M": 2, "k": 0.5} | plain60/60 / long | 60 / 60 | 336 | 1104 | 831 | 675 | -722 | 1378 | 1104 (831 / 675 / -722) | kagi_112, 2538 (48 / 76 / -1945) |
| swsr5 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | plain60/60 / long | 60 / 60 | 326 | 941 | 545 | 1014 | 148 | 1139 | 941 (545 / 1014 / 148) | kagi_112, 2788 (236 / -264 / -2437) |
| swsr5 | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / long | 120 / 120 | 137 | 889 | 375 | 857 | 820 | 1052 | -1447 (432 / 254 / 803) | lbrk_3_40, 1638 (-293 / -1179 / -1318) |
| swsr5 | reject_native | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 256 | 528 | 47 | 1150 | -796 | 400 | -1729 (-270 / 520 / -521) | kagi_40, 3237 (265 / 1368 / 654) |
| swsr5 | retest | vrb_700 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 557 | 1409 | 659 | -300 | -488 | 1304 | 1409 (659 / -300 / -488) | mrenko_20, 2659 (-716 / -995 / -709) |
| swsr5 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / long | 120 / 120 | 113 | 1215 | 758 | 949 | 515 | 913 | 47 (433 / -101 / 228) | mrenko_10, 2360 (398 / -1263 / -1865) |
| swsr60 | break | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 164 | 1169 | 1333 | 436 | -1475 | 2204 | 482 (1307 / -10 / -474) | pnf_10, 2714 (-1019 / -989 / 1889) |
| swsr60 | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 164 | 1169 | 1333 | 436 | -1475 | 2204 | 482 (1307 / -10 / -474) | kagi_40, 2084 (-313 / -2637 / -700) |
| swsr60 | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 296 | 1532 | 1223 | -808 | 835 | 1093 | 1532 (1223 / -808 / 835) | pnf_40, 1557 (-946 / -1881 / -885) |
| swsr60 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 296 | 1532 | 1223 | -808 | 835 | 1093 | 1532 (1223 / -808 / 835) | frenko_40, 1673 (1094 / -445 / -324) |
| swsr60 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 60 / 60 | 150 | 1013 | -299 | -515 | -477 | 1036 | 1013 (-299 / -515 / -477) | wrenko_10, 2075 (-1036 / -2049 / -1412) |
| swsr60 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 192 | 914 | -362 | -882 | -317 | 602 | 914 (-362 / -882 / -317) | kagi_56, 2648 (-423 / -1524 / 1834) |
| swsr60 | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 137 | 1667 | -201 | 137 | 1485 | 3122 | 1356 (-190 / 480 / 300) | wrenko_14, 1599 (-190 / -251 / 910) |
| swsr60 | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 137 | 1667 | -201 | 137 | 1485 | 3122 | 1356 (-190 / 480 / 300) | pnf_14, 2367 (-533 / -15 / -85) |
| stack | break | dol_350 | {"k": 4, "cw": 2.0} | plain60/60 / both | 60 / 60 | 171 | 1324 | -184 | 402 | -1161 | 504 | 1324 (-184 / 402 / -1161) | kagi_20, 3437 (176 / 1393 / -17) |
| stack | break_native | dol_6000 | {"k": 2, "cw": 0.5} | sym15u / both | 120 / 120 | 166 | 2044 | 168 | -215 | -923 | 3129 | -453 (161 / -143 / -19) | frenko_28, 2805 (-674 / 49 / 2094) |
| stack | reject | vsess_120 | {"k": 2, "cw": 0.5} | sym8u / both | 120 / 120 | 94 | 2473 | 270 | -72 | -962 | 2621 | 104 (-101 / -333 / -593) | wrenko_14, 2358 (140 / -1516 / -343) |
| stack | reject_native | tm780 | {"k": 3, "cw": 1.0} | sym15u / both | 120 / 120 | 102 | 3166 | -439 | -1258 | -1762 | 1845 | 643 (-375 / -444 / -2268) | pnf_14, 3864 (-615 / -258 / -63) |
| book_walls | break | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 59 | 1238 | -272 | -1504 | -9 | 988 | 567 (586 / -1325 / 58) | urenko_10, 1020 (-371 / -66 / -270) |
| book_walls | break_native | dib_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 59 | 1238 | -272 | -1504 | -9 | 988 | 567 (586 / -1325 / 58) | mrenko_10, 874 (-752 / -8 / 293) |
| book_walls | false_break | tm20 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 51 | 490 | -513 | -1299 | -929 | -49 | 490 (-513 / -1299 / -929) | swing_atr_0.1, 809 (547 / -1665 / -90) |
| book_walls | false_break_native | tm10 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 56 | 1019 | -536 | -1198 | -714 | 848 | 1019 (-536 / -1198 / -714) | swing_atr_0.1, 809 (547 / -1665 / -90) |
| book_walls | reject | dib_240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 77 | 1348 | -552 | -1085 | 294 | 1099 | 1348 (-552 / -1085 / 294) | urenko_10, 894 (-540 / -479 / -723) |
| book_walls | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 55 | 1152 | 209 | -451 | 107 | 688 | 1152 (209 / -451 / 107) | urenko_10, 882 (518 / 67 / -1396) |
| book_walls | retest | tib_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 46 | 978 | -549 | -37 | -855 | 476 | 978 (-549 / -37 / -855) | no reversal row has trades |
| book_walls | retest_native | vsess_600 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 31 | 948 | -230 | -711 | 334 | 598 | 869 (493 / -921 / 266) | no reversal row has trades |
| book_walls_loose | break | rng_10 | {"n": 1, "k": 0.5} | asym20u/10u / both | 120 / 75 | 197 | 2357 | -978 | -1528 | -3048 | 1807 | 1196 (606 / -37 / -2108) | renko_10, 1961 (519 / 691 / -437) |
| book_walls_loose | break_native | rng_10 | {"n": 2, "k": 0.25} | sym15u / both | 112 / 112 | 176 | 2309 | -1415 | 296 | -1880 | 2748 | 588 (-1570 / 862 / -287) | urenko_10, 2161 (-1653 / -1091 / -2596) |
| book_walls_loose | false_break | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1898 (-1493 / 606 / -1053) | mom_10, 619 (741 / -58 / -1370) |
| book_walls_loose | false_break_native | time_s_5 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 252 | 1898 | -1493 | 606 | -1053 | 1595 | 1898 (-1493 / 606 / -1053) | mom_10, 754 (262 / -379 / -1718) |
| book_walls_loose | reject | dib_400 | {"tol": 0.5, "conf": "body"} | sym15u / both | 98 / 98 | 170 | 3163 | -1118 | 31 | -1206 | 3714 | 1632 (374 / -319 / -674) | urenko_10, 2763 (-456 / -342 / -3133) |
| book_walls_loose | reject_native | dib_400 | {"tol": 1.0, "conf": "body"} | sym15u / both | 98 / 98 | 208 | 3375 | -1082 | -93 | -1302 | 3631 | 1751 (432 / 138 / -1141) | urenko_10, 2310 (132 / 232 / -3365) |
| book_walls_loose | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 98 / 98 | 150 | 3516 | 15 | -764 | -863 | 4040 | 1863 (1609 / 493 / -461) | swing_atr_0.1, 1151 (-1103 / 1079 / 2225) |
| book_walls_loose | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 98 / 98 | 149 | 3365 | -152 | -1165 | 168 | 4037 | 1391 (1375 / 348 / 444) | swing_atr_0.1, 1788 (-1327 / 520 / 1049) |
| channel | break | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 246 | 2195 | -175 | 403 | -312 | 2454 | 203 (-331 / -711 / 1510) | urenko_20, 3125 (-354 / -1559 / 474) |
| channel | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 101 | 1594 | -28 | 277 | -557 | 1886 | 1464 (-57 / 505 / 727) | kagi_112, 2782 (-78 / -142 / -1977) |
| channel | false_break | vrb_40000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 69 | 545 | 67 | -575 | -108 | 778 | 543 (53 / -533 / -280) | kagi_112, 2909 (-148 / -291 / -2237) |
| channel | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 254 | 572 | -421 | 1439 | 2428 | 1278 | 240 (-112 / 538 / -8) | kagi_80, 3344 (373 / 1739 / 1102) |
| channel | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 251 | 2490 | -360 | -1496 | -597 | 469 | -645 (-761 / -1189 / 207) | kagi_56, 2681 (332 / 48 / -1806) |
| channel | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 288 | 3964 | -646 | -158 | -1582 | 1781 | 477 (-801 / -394 / 540) | kagi_56, 3978 (-529 / -363 / -2591) |
| channel | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 244 | 1596 | -440 | 502 | 538 | 951 | 501 (-258 / 54 / 481) | pnf_5, 2499 (248 / -1221 / -688) |
| channel | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 256 | 2098 | -324 | -779 | 234 | 2096 | 1082 (43 / -456 / 741) | pnf_5, 2499 (248 / -1221 / -688) |
| fvg15 | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 62 | 800 | 85 | -57 | -535 | 82 | 452 (17 / -223 / 284) | kagi_80, 1769 (-239 / 176 / 876) |
| fvg15 | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 139 | 1778 | 684 | -248 | -495 | 1587 | 1281 (479 / -28 / -1440) | wrenko_10, 2142 (699 / 1173 / -2521) |
| fvg15 | false_break | dol_500 | {"M": 2, "k": 0.5} | plain60/60 / short | 60 / 60 | 106 | 85 | 111 | 64 | -329 | 297 | 85 (111 / 64 / -329) | pnf_10, 1273 (165 / -386 / -465) |
| fvg15 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 69 | 368 | 580 | -636 | 29 | 402 | 259 (463 / -812 / -495) | pnf_10, 1094 (257 / -577 / -633) |
| fvg15 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 160 | 2306 | 36 | -377 | -1310 | 3252 | 1374 (163 / 270 / -1622) | kagi_14, 3384 (-99 / 1317 / -307) |
| fvg15 | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 174 | 3748 | 628 | -189 | -449 | 4032 | 2046 (377 / 391 / -1862) | kagi_14, 4419 (-178 / 432 / 336) |
| fvg15 | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 143 | 1417 | 1092 | 374 | -81 | 2635 | 703 (616 / -163 / 71) | pnf_14, 1682 (-181 / -793 / -565) |
| fvg15 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 158 | 2957 | 1199 | 1020 | -199 | 3816 | 1333 (514 / 642 / -328) | kagi_28, 2753 (583 / -533 / -855) |
| fvg5 | break | dol_6000 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 161 | 1221 | -60 | -797 | -314 | 2139 | 1221 (-60 / -797 / -314) | pnf_10, 3565 (411 / 793 / 1067) |
| fvg5 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 52 | 1033 | -49 | 155 | -1440 | 1457 | 645 (190 / -82 / -558) | pnf_10, 3565 (411 / 793 / 1067) |
| fvg5 | false_break | dol_6000 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 160 | 673 | -671 | -758 | -520 | 1009 | 673 (-671 / -758 / -520) | pnf_10, 2223 (925 / 729 / 320) |
| fvg5 | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 132 | 921 | -66 | -606 | -548 | 1070 | 921 (-66 / -606 / -548) | pnf_10, 2223 (925 / 729 / 320) |
| fvg5 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / long | 120 / 120 | 120 | 726 | 747 | 27 | -23 | 1174 | -391 (743 / -569 / 638) | kagi_10, 2756 (214 / -1882 / -387) |
| fvg5 | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 170 | 1490 | 226 | -1625 | 601 | 1536 | 1226 (443 / -1045 / -547) | kagi_10, 2182 (193 / -1316 / -820) |
| fvg5 | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 201 | 1526 | 1141 | 1693 | 1785 | 1898 | -1530 (1011 / 2127 / 277) | frenko_40, 2473 (-230 / -1137 / -66) |
| fvg5 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 118 | 1189 | 639 | 1437 | 988 | 1372 | -1054 (706 / 1071 / 973) | frenko_40, 3090 (-276 / -1553 / 384) |
| gaps | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 55 | 2001 | 211 | 6 | -1149 | 1959 | 564 (214 / 99 / -1845) | pnf_7, 2458 (515 / -722 / -3227) |
| gaps | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 102 | 1869 | 596 | -1342 | -2369 | 1291 | 326 (241 / -771 / -1128) | pnf_7, 2868 (-251 / -161 / -3421) |
| gaps | false_break | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 48 | 1335 | 503 | -512 | -1129 | 1673 | 482 (650 / -642 / -885) | pnf_28, 1779 (18 / -19 / 344) |
| gaps | false_break_native | tm1800 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 47 | 1309 | 379 | -508 | -1289 | 1811 | 456 (595 / -569 / -859) | pnf_28, 1843 (-87 / 76 / 307) |
| gaps | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 77 | 1787 | -503 | -1304 | -74 | 1632 | 1006 (-566 / -1174 / 150) | wrenko_14, 2035 (-730 / -1775 / 708) |
| gaps | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 120 | 1775 | -22 | -1146 | -1037 | 1614 | 514 (-135 / -1403 / -1177) | kagi_56, 2332 (-600 / 3 / -1106) |
| gaps | retest | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 53 | 1584 | -348 | -820 | -994 | 1765 | 852 (-368 / -812 / 268) | kagi_40, 1555 (-396 / -734 / -587) |
| gaps | retest_native | cusum_14 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 53 | 1584 | -348 | -820 | -994 | 1765 | 852 (-368 / -812 / 268) | kagi_40, 2963 (-29 / 441 / -1448) |
| mmove | break | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 477 | 1913 | 715 | 1230 | 235 | 3294 | 1913 (715 / 1230 / 235) | kagi_40, 2588 (-853 / -45 / -2503) |
| mmove | break_native | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 477 | 1913 | 715 | 1230 | 235 | 3294 | 1913 (715 / 1230 / 235) | kagi_40, 2486 (-450 / 418 / -1675) |
| mmove | false_break | vrb_700 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 603 | 1509 | -39 | 343 | -1122 | 1749 | 1509 (-39 / 343 / -1122) | pnf_20, 2557 (-462 / -577 / -579) |
| mmove | false_break_native | dol_500 | {"M": 3, "k": 0.5} | plain60/60 / long | 60 / 60 | 296 | 980 | 585 | -244 | -344 | 299 | 980 (585 / -244 / -344) | pnf_20, 2897 (-838 / -578 / -949) |
| mmove | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 481 | 3098 | 409 | 646 | -265 | 2767 | 3098 (409 / 646 / -265) | lbrk_3_10, 2106 (652 / 71 / 184) |
| mmove | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 211 | 1836 | 199 | -667 | -1125 | 1860 | -1363 (-350 / -1068 / -198) | urenko_56, 3153 (-70 / 1060 / -1089) |
| mmove | retest | vrb_700 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 471 | 1925 | -117 | 201 | -162 | 690 | 1925 (-117 / 201 / -162) | pnf_5, 3290 (700 / 11 / -758) |
| mmove | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 238 | 1406 | 1087 | 1442 | -478 | 1244 | 165 (1537 / 847 / -323) | pnf_5, 3290 (700 / 11 / -758) |
| ob15 | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 50 | 1052 | 44 | -972 | 350 | 894 | -266 (-53 / -713 / -248) | wrenko_20, 1091 (244 / -107 / 133) |
| ob15 | break_native | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 66 | 916 | 532 | -811 | -722 | 1406 | 815 (381 / -797 / -319) | kagi_10, 1244 (663 / -890 / -72) |
| ob15 | false_break | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 82 | 787 | -429 | -443 | -506 | 1161 | 787 (-429 / -443 / -506) | lbrk_3_10, 748 (-455 / -628 / 338) |
| ob15 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 82 | 787 | -429 | -443 | -506 | 1161 | 787 (-429 / -443 / -506) | lbrk_3_10, 748 (-455 / -628 / 338) |
| ob15 | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 64 | 781 | 283 | -160 | -1024 | 1055 | -214 (536 / -568 / -748) | wrenko_10, 1376 (323 / -1331 / 1080) |
| ob15 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 71 | 782 | 786 | -171 | 52 | 1030 | 205 (450 / -300 / 398) | pnf_7, 1184 (775 / -274 / 61) |
| ob15 | retest | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 74 | 346 | -285 | -229 | 448 | 567 | 346 (-285 / -229 / 448) | kagi_56, 1142 (267 / -325 / 553) |
| ob15 | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 63 | 583 | -221 | -663 | 417 | 670 | 390 (-197 / 161 / 63) | wrenko_20, 1197 (155 / -638 / 61) |
| ob5 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 131 | 1418 | -177 | 100 | 1544 | 148 | 1157 (-343 / 19 / -122) | kagi_10, 2331 (256 / 1088 / 649) |
| ob5 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 131 | 1418 | -177 | 100 | 1544 | 148 | 1157 (-343 / 19 / -122) | kagi_10, 2331 (256 / 1088 / 649) |
| ob5 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 130 | 1634 | -186 | 249 | 1890 | 455 | 1006 (-517 / 119 / -91) | pnf_5, 1963 (-56 / 924 / 346) |
| ob5 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 126 | 2383 | -849 | -727 | 1517 | 1531 | 1271 (-850 / 30 / 334) | kagi_20, 2094 (10 / 566 / -25) |
| ob5 | reject | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 135 | 720 | 253 | -978 | -488 | -196 | -719 (-578 / -2135 / 25) | urenko_14, 1424 (71 / -876 / -916) |
| ob5 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / long | 60 / 60 | 124 | 441 | 16 | -1100 | -677 | 22 | 441 (16 / -1100 / -677) | urenko_40, 1981 (-488 / -1059 / -729) |
| ob5 | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 48 | 648 | -188 | -487 | -570 | 1061 | -205 (-306 / -556 / -624) | mrenko_14, 2215 (-850 / -680 / 932) |
| ob5 | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 54 | 471 | -333 | -345 | -220 | 1081 | 67 (-174 / -321 / -424) | mrenko_14, 2232 (-468 / -959 / 1160) |
| opens | break | vol_750 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 176 | 2591 | 1060 | -1930 | -782 | 2008 | -321 (1317 / -1557 / -845) | renko_14, 3946 (43 / 1332 / 422) |
| opens | break_native | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 203 | 2680 | 239 | -818 | -649 | 1849 | -373 (688 / -1149 / 333) | renko_14, 4141 (36 / 1264 / 62) |
| opens | false_break | tm45 | {"M": 1, "k": 0.5} | sym15u / both | 120 / 120 | 196 | 2379 | 150 | 148 | -622 | 3248 | -301 (-462 / -684 / -802) | pasl_20, 3114 (444 / -588 / -837) |
| opens | false_break_native | rng_20 | {"M": 3, "k": 0.5} | asym20u/10u / both | 120 / 120 | 183 | 2484 | 493 | 2453 | -1738 | 3139 | 392 (680 / 1542 / -1018) | pasl_20, 3114 (444 / -588 / -837) |
| opens | reject | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 214 | 4551 | -246 | 238 | 430 | 3334 | 1643 (547 / -1660 / 2146) | mom_20, 2108 (1204 / -1149 / -277) |
| opens | reject_native | time_s_45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 214 | 4551 | -246 | 238 | 430 | 3334 | 1643 (547 / -1660 / 2146) | mom_20, 2108 (1204 / -1149 / -277) |
| opens | retest | time_s_45 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 178 | 2786 | -349 | -636 | 220 | 1949 | 1073 (85 / -1671 / -583) | pasl_28, 3307 (120 / -78 / -1413) |
| opens | retest_native | vsess_80 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 172 | 3335 | 1124 | -912 | -114 | 1454 | 1232 (1324 / -1726 / -601) | dchg_56, 2737 (427 / 275 / -1516) |
| prior_day | break | tm600 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 112 | 2773 | 102 | -1087 | -1733 | 4007 | 1132 (16 / -1402 / -2358) | swing_atr_0.1, 2061 (325 / -1139 / -831) |
| prior_day | break_native | tm1800 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 103 | 2083 | 433 | -525 | -990 | 3127 | 1404 (634 / -977 / -1295) | swing_atr_0.1, 2061 (325 / -1139 / -831) |
| prior_day | false_break | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 102 | 1926 | 97 | -571 | -1137 | 2696 | 1301 (271 / -1064 / -1375) | pasl_10, 2376 (649 / -33 / -1668) |
| prior_day | false_break_native | tm1800 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 101 | 1900 | 270 | -544 | -1219 | 2901 | 1274 (506 / -995 / -1321) | swing_atr_0.1, 2405 (621 / -246 / -702) |
| prior_day | reject | vsess_50 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 105 | 1827 | -426 | -804 | -662 | 720 | -610 (-469 / -178 / 135) | urenko_20, 1311 (325 / -23 / 487) |
| prior_day | reject_native | tm240 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 281 | 2224 | 66 | -917 | -270 | 1824 | 2224 (66 / -917 / -270) | mrenko_10, 1491 (-382 / -443 / -247) |
| prior_day | retest | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 167 | 2609 | 12 | -329 | 707 | 2514 | 2609 (12 / -329 / 707) | dchg_40, 1788 (97 / -231 / -475) |
| prior_day | retest_native | tm300 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 191 | 2712 | -110 | -383 | 424 | 2187 | 2712 (-110 / -383 / 424) | dchg_40, 1960 (212 / -209 / -386) |
| profile_nodes | break | dib_1200 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 162 | 2957 | -620 | 59 | -1689 | 2002 | 2598 (-504 / -340 / -1321) | renko_10, 2313 (-345 / -255 / -2844) |
| profile_nodes | break_native | tm20 | {"n": 1, "k": 0.5} | sym30u / both | 120 / 120 | 165 | 3227 | -565 | 323 | -1499 | 2266 | -265 (-302 / -677 / -971) | dchg_40, 2292 (-503 / -811 / -1173) |
| profile_nodes | false_break | time_m_30 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 125 | 1744 | 20 | -1664 | -1283 | 2642 | -374 (-352 / -1935 / -2566) | dchg_40, 2292 (-55 / -984 / -1066) |
| profile_nodes | false_break_native | tm420 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 135 | 1946 | 302 | -1997 | -2185 | 1519 | 135 (267 / -2504 / -1931) | renko_10, 2676 (-200 / -70 / 183) |
| profile_nodes | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 186 | 2800 | 375 | -833 | -240 | 2859 | -384 (793 / -192 / -53) | wrenko_10, 2817 (-450 / -1140 / -2494) |
| profile_nodes | reject_native | dib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 157 | 2560 | 717 | 260 | 397 | 751 | -188 (964 / 409 / -407) | renko_10, 2821 (-98 / -360 / 235) |
| profile_nodes | retest | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 2557 (-652 / -148 / -1983) | dchg_56, 2167 (-533 / -983 / -340) |
| profile_nodes | retest_native | dlt_45 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 150 | 3144 | -763 | -1162 | -2086 | 2103 | 2557 (-652 / -148 / -1983) | swing_atr_0.15, 2505 (172 / -1776 / -3194) |
| profile_va | break | tm300 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 137 | 2970 | -121 | -1950 | -524 | 1758 | -217 (518 / -1809 / -1897) | dchg_112, 2364 (-191 / -909 / -897) |
| profile_va | break_native | tick_2000 | {"n": 3, "k": 0.0} | sym8u / both | 120 / 120 | 124 | 2577 | -608 | -532 | -391 | 1887 | -451 (-377 / -870 / -871) | renko_28, 2591 (-66 / -1416 / -848) |
| profile_va | false_break | rng_10 | {"M": 1, "k": 0.0} | asym20u/10u / both | 120 / 75 | 206 | 2370 | -19 | -168 | -2032 | 2117 | 1265 (96 / -670 / -1899) | dchg_112, 2493 (-419 / -437 / -1179) |
| profile_va | false_break_native | tm30 | {"M": 2, "k": 0.5} | sym15u / both | 112 / 112 | 162 | 2584 | 299 | -691 | -241 | 3689 | 699 (-81 / -863 / -112) | dchg_112, 2493 (-365 / -437 / -1179) |
| profile_va | reject | tib_2000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 128 | 2405 | -523 | 863 | 668 | 2266 | 660 (-54 / 1023 / -736) | mom_28, 1647 (-245 / -1490 / 71) |
| profile_va | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 131 | 2493 | 295 | -1054 | 183 | 1120 | -465 (267 / -1652 / -555) | dchg_56, 1915 (-35 / -1135 / -1742) |
| profile_va | retest | dib_2000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 124 | 2902 | 997 | -1389 | -688 | 3254 | 1214 (1022 / -1585 / -1098) | mom_28, 3198 (93 / -1886 / -354) |
| profile_va | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 144 | 3224 | -311 | -329 | -209 | 2404 | 2594 (-441 / -680 / -559) | swing_pct_20, 2637 (-704 / -895 / -173) |
| round | break | vsess_450 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 270 | 2974 | 47 | -1095 | -1288 | 1742 | -1403 (287 / -820 / -129) | mom_28, 3115 (485 / -528 / -148) |
| round | break_native | vsess_450 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 270 | 2974 | 47 | -1095 | -1288 | 1742 | -1403 (287 / -820 / -129) | mom_28, 3115 (485 / -528 / -148) |
| round | false_break | rng_80 | {"M": 2, "k": 0.5} | sym8u / both | 120 / 120 | 250 | 2986 | 749 | -1352 | -1991 | 4166 | -243 (903 / -300 / -2650) | pasl_10, 3076 (-134 / 387 / -1885) |
| round | false_break_native | rng_80 | {"M": 3, "k": 0.5} | sym8u / both | 120 / 120 | 244 | 3178 | 720 | -1781 | -1274 | 4592 | -315 (949 / -825 / -2353) | dchg_112, 3286 (139 / -661 / -1168) |
| round | reject | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 82 / 82 | 405 | 3731 | -1516 | 737 | 448 | 5872 | 6 (-1205 / 597 / 277) | renko_10, 2348 (-550 / -193 / -872) |
| round | reject_native | time_s_20 | {"tol": 0.5, "conf": "body"} | sym15u / both | 82 / 82 | 390 | 3588 | -302 | 1061 | -995 | 4599 | 166 (-495 / 513 / -1179) | swing_atr_0.4, 5128 (-1178 / 438 / 2006) |
| round | retest | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 120 / 120 | 246 | 4477 | -191 | -320 | -645 | 5031 | -601 (-278 / -359 / 2450) | urenko_14, 2746 (593 / -116 / -1969) |
| round | retest_native | rng_10 | {"M": 6, "tol": 0.0} | sym30u / both | 120 / 120 | 246 | 4477 | -191 | -320 | -645 | 5031 | -601 (-278 / -359 / 2450) | pasl_56, 3731 (-467 / 869 / 533) |
| session_hl | break | vsess_30 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 119 | 1588 | -860 | -1167 | -1297 | 391 | -645 (-590 / -2070 / -1454) | pasl_56, 1771 (-1102 / -336 / -292) |
| session_hl | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 125 | 2010 | -499 | -89 | 122 | 1020 | -923 (-820 / -1601 / 497) | pasl_20, 2654 (-107 / 389 / -378) |
| session_hl | false_break | dlt_250 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 85 | 1599 | 871 | -1444 | -546 | 1761 | -456 (1060 / -1239 / -217) | renko_14, 1640 (-516 / 85 / -1030) |
| session_hl | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 100 | 114 | 2154 | 41 | 535 | 418 | 2967 | 1051 (653 / -205 / 1252) | renko_14, 1443 (-233 / 172 / -712) |
| session_hl | reject | tick_300 | {"tol": 1.0, "conf": "close"} | asym20u/10u / both | 120 / 120 | 130 | 1634 | -79 | 16 | 319 | 1221 | -628 (-353 / -1256 / 1004) | renko_10, 1098 (-1137 / 45 / -1134) |
| session_hl | reject_native | time_m_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 143 | 1774 | 300 | -1099 | -154 | 1667 | 237 (-104 / -305 / -1391) | swing_pct_5, 1805 (-162 / -987 / -1228) |
| session_hl | retest | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 95 | 2698 | 463 | -1670 | -1618 | 2468 | 1039 (562 / -2020 / -1364) | urenko_10, 1558 (212 / 18 / 482) |
| session_hl | retest_native | time_m_13 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 125 | 1751 | 351 | -1422 | -30 | 1828 | 398 (538 / -2046 / -627) | swing_pct_12, 2330 (-299 / -559 / 604) |
| trendline | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 215 | 2090 | -153 | -816 | -1450 | 3234 | 270 (8 / -1448 / 511) | mrenko_10, 2957 (-338 / -167 / -927) |
| trendline | break_native | dol_500 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 437 | 2014 | -419 | -819 | 963 | 883 | 2014 (-419 / -819 / 963) | mrenko_14, 3004 (8 / 371 / -320) |
| trendline | false_break | dol_350 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 481 | 1722 | -187 | -1129 | 1605 | 521 | 1722 (-187 / -1129 / 1605) | kagi_14, 1894 (260 / -1042 / -2133) |
| trendline | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / long | 60 / 60 | 229 | 1706 | 227 | -362 | 557 | 922 | 1706 (227 / -362 / 557) | kagi_14, 1886 (383 / -246 / -48) |
| trendline | reject | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 418 | 1737 | 425 | -377 | 418 | 2023 | 1737 (425 / -377 / 418) | wrenko_14, 3780 (-431 / -284 / 730) |
| trendline | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 497 | 3116 | -9 | 31 | 2074 | 4060 | 3116 (-9 / 31 / 2074) | wrenko_14, 3780 (-431 / -284 / 730) |
| trendline | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 199 | 1887 | 463 | -405 | 1066 | 1066 | -59 (430 / 102 / 1255) | urenko_14, 2709 (329 / -350 / 447) |
| trendline | retest_native | dol_500 | {"M": 3, "tol": 0.0} | sym15u / long | 120 / 120 | 100 | 1495 | 341 | 1054 | 826 | 1934 | 390 (355 / 629 / -40) | wrenko_14, 3008 (-48 / -1940 / 1275) |
| uw_dp | break | tm780 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 90 | 2707 | 0 | 0 | -91 | 3294 | 517 (0 / 0 / 252) | dchg_40, 2727 (0 / 0 / 546) |
| uw_dp | break_native | tm900 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 97 | 2687 | 0 | 0 | 188 | 2687 | 238 (0 / 0 / 151) | dchg_40, 2727 (0 / 0 / 546) |
| uw_dp | false_break | tm1800 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 84 | 2532 | 0 | 0 | 151 | 2362 | -480 (0 / 0 / 200) | dchg_40, 2734 (0 / 0 / 530) |
| uw_dp | false_break_native | tm1800 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 86 | 2489 | 0 | 0 | 151 | 2305 | -351 (0 / 0 / 200) | dchg_40, 2727 (0 / 0 / 546) |
| uw_dp | reject | vsess_30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 77 | 1652 | 0 | 0 | 311 | 1135 | -124 (0 / 0 / 5) | lbrk_3_10, 1964 (0 / 0 / 365) |
| uw_dp | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 122 | 2086 | 0 | 0 | -468 | 1673 | 681 (0 / 0 / -591) | dchg_80, 1914 (0 / 0 / -479) |
| uw_dp | retest | tm120 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 78 | 2365 | 0 | 0 | -220 | 2127 | 917 (0 / 0 / -401) | pasl_20, 2915 (0 / 0 / -57) |
| uw_dp | retest_native | tm120 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 78 | 2365 | 0 | 0 | -220 | 2127 | 917 (0 / 0 / -401) | dchg_40, 2424 (0 / 0 / 561) |
| uw_ndx | break | tm180 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 114 | 3365 | 0 | 362 | -1630 | 3657 | 1404 (0 / 467 / -1716) | mrenko_10, 2753 (0 / -62 / 764) |
| uw_ndx | break_native | time_m_2 | {"n": 2, "k": 0.5} | asym10u/20u / both | 120 / 120 | 112 | 3662 | 0 | -280 | -459 | 3598 | 793 (0 / -361 / -1) | mrenko_10, 2646 (0 / 126 / 762) |
| uw_ndx | false_break | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 88 | 2347 | 0 | -175 | -2312 | 2034 | 361 (0 / -429 / -1205) | renko_20, 2292 (0 / 107 / -76) |
| uw_ndx | false_break_native | time_m_30 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 88 | 2347 | 0 | -175 | -2312 | 2034 | 361 (0 / -429 / -1205) | renko_20, 2292 (0 / 107 / -76) |
| uw_ndx | reject | drb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 103 | 3115 | 0 | -345 | 406 | 1676 | -555 (0 / -43 / -524) | wrenko_10, 1943 (0 / 171 / -213) |
| uw_ndx | reject_native | vol_500 | {"tol": 0.0, "conf": "body"} | sym8u / both | 120 / 120 | 96 | 2723 | 0 | -340 | 1465 | 2885 | 1432 (0 / -234 / 808) | pasl_56, 2337 (0 / -39 / -615) |
| uw_ndx | retest | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 98 / 98 | 142 | 2949 | 0 | -109 | -693 | 2727 | 1188 (0 / 130 / -1013) | pasl_56, 2404 (0 / 497 / -2150) |
| uw_ndx | retest_native | dib_400 | {"M": 10, "tol": 0.5} | sym15u / both | 98 / 98 | 141 | 2796 | 0 | 85 | -715 | 2712 | 1461 (0 / 414 / -1137) | pasl_56, 2673 (0 / 781 / -2189) |
| uw_qqq | break | rng_28 | {"n": 2, "k": 0.0} | sym15u / both | 120 / 120 | 113 | 2607 | 0 | 547 | 2209 | 2901 | -411 (0 / 340 / -424) | renko_20, 2987 (0 / -70 / -7) |
| uw_qqq | break_native | rng_28 | {"n": 2, "k": 0.0} | sym15u / both | 120 / 120 | 113 | 2607 | 0 | 547 | 2209 | 2901 | -411 (0 / 340 / -424) | renko_20, 2846 (0 / 48 / 263) |
| uw_qqq | false_break | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 120 | 122 | 3111 | 0 | 268 | -100 | 2849 | 1287 (0 / 74 / -333) | urenko_56, 2085 (0 / -675 / -579) |
| uw_qqq | false_break_native | vsess_120 | {"M": 3, "k": 0.5} | sym8u / both | 120 / 120 | 125 | 2832 | 0 | -304 | -463 | 2243 | 1454 (0 / -649 / -668) | dchg_56, 2262 (0 / 272 / 174) |
| uw_qqq | reject | vsess_30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 106 | 2063 | 0 | -99 | -1486 | 1064 | -197 (0 / 6 / -2098) | wrenko_20, 2612 (0 / 241 / -787) |
| uw_qqq | reject_native | cdr_160 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 121 | 3084 | 0 | 263 | -571 | 3471 | 165 (0 / -16 / -1337) | dchg_56, 2541 (0 / 512 / -2277) |
| uw_qqq | retest | vsess_120 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 116 | 3298 | 0 | -430 | -1042 | 2339 | 920 (0 / -440 / -229) | pasl_56, 3332 (0 / 198 / -544) |
| uw_qqq | retest_native | tm3600 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 129 | 2682 | 0 | 72 | -1841 | 2866 | 1028 (0 / 141 / -976) | dchg_80, 2490 (0 / 115 / -550) |
| vwap | break | tm420 | {"n": 2, "k": 0.5} | sym8u / both | 120 / 120 | 204 | 4876 | -172 | -860 | -219 | 5922 | 726 (425 / -978 / 1849) | renko_14, 5484 (276 / -1123 / -2301) |
| vwap | break_native | dlt_30 | {"n": 2, "k": 0.5} | asym20u/10u / both | 120 / 115 | 286 | 5213 | -46 | -1375 | 817 | 5488 | 2541 (47 / -1870 / -936) | renko_14, 5738 (534 / -1080 / -3184) |
| vwap | false_break | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 160 | 2710 | 83 | 637 | 249 | 2886 | 1565 (-466 / 285 / 268) | dchg_56, 2837 (298 / -962 / 1185) |
| vwap | false_break_native | tm3600 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 160 | 2710 | 122 | 637 | 249 | 2886 | 1565 (-427 / 285 / 268) | dchg_56, 2671 (306 / -1210 / 1449) |
| vwap | reject | cusum_10 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 120 / 120 | 248 | 4751 | -37 | -1718 | 768 | 7179 | 1387 (1012 / -859 / -1409) | mom_28, 3029 (-849 / -1109 / 382) |
| vwap | reject_native | cdr_100 | {"tol": 0.5, "conf": "body"} | sym8u / both | 120 / 120 | 233 | 5846 | 667 | 1147 | -135 | 5737 | 1938 (524 / 418 / 608) | swing_pct_5, 5054 (-406 / 677 / -109) |
| vwap | retest | dlt_45 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 221 | 4700 | 559 | 726 | -1028 | 4660 | 2771 (160 / -646 / 299) | swing_pct_5, 3636 (1237 / 687 / 383) |
| vwap | retest_native | cdr_100 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 218 | 4634 | 959 | 362 | -947 | 5800 | 534 (577 / -470 / 312) | dchg_14, 3194 (27 / -1109 / -398) |
| vwap_bands | break | drb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 245 | 4128 | 539 | -1135 | -304 | 5386 | 525 (922 / -1329 / -2208) | dchg_80, 2911 (91 / -58 / -2319) |
| vwap_bands | break_native | cusum_14 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 292 | 3642 | 1104 | 410 | -1140 | 1707 | -143 (890 / -1798 / -2065) | renko_10, 3283 (220 / 602 / -1805) |
| vwap_bands | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 668 | 2190 | 843 | -1542 | 2621 | 1533 | 2190 (843 / -1542 / 2621) | lbrk_3_10, 2432 (689 / -2155 / 618) |
| vwap_bands | false_break_native | rng_14 | {"M": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 659 | 2315 | -458 | -1886 | -2589 | 2706 | 2315 (-458 / -1886 / -2589) | lbrk_3_10, 2432 (689 / -2155 / 618) |
| vwap_bands | reject | tm420 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 249 | 3847 | -1624 | 1607 | 609 | 3094 | -1567 (-1868 / 1303 / -863) | renko_10, 3708 (-1147 / 916 / -2052) |
| vwap_bands | reject_native | dib_1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 280 | 3027 | 61 | -795 | 419 | 5272 | -1896 (-610 / -978 / -1320) | pnf_14, 2829 (-797 / -123 / 535) |
| vwap_bands | retest | drb_240 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 684 | 3403 | 537 | -777 | -29 | 2793 | 3403 (537 / -777 / -29) | dchg_80, 3208 (-488 / 658 / -1879) |
| vwap_bands | retest_native | vsess_30 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 257 | 3675 | 581 | -1198 | -2832 | 5778 | -846 (-176 / -1725 / -144) | renko_10, 3064 (1201 / -1008 / -1051) |
| week_month | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 120 / 120 | 36 | 1253 | -81 | -73 | 48 | 2318 | 922 (-159 / -68 / -939) | pnf_7, 1567 (304 / -30 / -1454) |
| week_month | break_native | rng_20 | {"n": 2, "k": 0.25} | asym20u/10u / both | 120 / 120 | 37 | 1177 | 179 | -16 | 990 | 1587 | 811 (226 / 100 / -142) | swing_atr_0.25, 1508 (-111 / -183 / -1226) |
| week_month | false_break | cdr_100 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 54 | 747 | 3 | -908 | -295 | 875 | 747 (3 / -908 / -295) | dchg_112, 1229 (-532 / 225 / -375) |
| week_month | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 41 | 914 | -245 | -393 | -121 | 818 | 914 (-245 / -393 / -121) | dchg_112, 1229 (-532 / 225 / -375) |
| week_month | reject | dib_3500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 34 | 1552 | -278 | -260 | -1282 | 1727 | 570 (-240 / -112 / -793) | wrenko_20, 1618 (133 / -162 / -2232) |
| week_month | reject_native | vol_2600 | {"tol": 0.5, "conf": "close"} | sym8u / both | 120 / 120 | 46 | 1503 | 278 | 173 | -636 | 1684 | -91 (140 / -7 / -831) | urenko_40, 1579 (-70 / -765 / -196) |
| week_month | retest | tm60 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 33 | 1229 | 124 | -30 | -141 | 1120 | 991 (121 / 107 / -461) | wrenko_20, 1089 (-280 / -367 / -429) |
| week_month | retest_native | drb_700 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 34 | 1569 | 279 | -272 | -775 | 1609 | 667 (129 / -345 / -702) | pnf_40, 1759 (102 / -138 / -542) |

### NYPM - supply/demand modules by definition (variant = entry type)
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sdx15 | break | vrb_40000 | {"d": "A", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 31 | 44 | -880 | -1737 | -1096 | -337 | -412 (-516 / -589 / -843) | pnf_40, 745 (-750 / 713 / 55) |
| sdx15 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 221 | 3400 | 133 | -1681 | -2632 | 3458 | 3179 (1253 / -1482 / -4236) | urenko_14, 3979 (866 / -1611 / -3817) |
| sdx15 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 566 | 2874 | 449 | -1494 | -463 | 3887 | 2874 (449 / -1494 / -463) | lbrk_3_10, 3753 (213 / -649 / -2699) |
| sdx15 | rej | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 195 | 2396 | 1301 | -1445 | 263 | 2223 | 1921 (992 / -1446 / -472) | wrenko_14, 2838 (1403 / -67 / -500) |
| sdx15 | rej_flow | vrb_700 | {"d": "E", "F": 9} | sym15u / both | 120 / 120 | 133 | 1794 | -161 | -1986 | 656 | 1865 | 1201 (275 / -1916 / 155) | wrenko_14, 1888 (-308 / 1188 / 1098) |
| sdx15 | rej_native | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 344 | 2906 | 1016 | -529 | -826 | 2452 | 2906 (1016 / -529 / -826) | kagi_40, 3230 (-109 / -1094 / -602) |
| sdx15 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 344 | 2906 | 1016 | -529 | -826 | 2452 | 2906 (1016 / -529 / -826) | kagi_40, 3230 (-109 / -1094 / -602) |
| sdx3 | break | dol_6000 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 120 / 120 | 91 | 1340 | -736 | -145 | 1764 | 1884 | 210 (82 / 374 / 115) | pnf_7, 1995 (-691 / -13 / 2296) |
| sdx3 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 182 | 1931 | 980 | 199 | -3051 | 1560 | -29 (674 / -662 / -1947) | mrenko_14, 3243 (1073 / -1181 / -5173) |
| sdx3 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 341 | 2496 | -80 | 361 | -4793 | 913 | -1396 (307 / 1058 / -4060) | lbrk_3_10, 3173 (-505 / 837 / -3633) |
| sdx3 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 251 | 2478 | 724 | 613 | -327 | 1370 | 2067 (1408 / -932 / -1472) | pnf_7, 2223 (1029 / -286 / -877) |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / both | 120 / 120 | 218 | 3964 | 768 | 815 | -3268 | 3684 | 1524 (-534 / 900 / -487) | wrenko_14, 1295 (306 / 9 / -317) |
| sdx3 | rej_native | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 518 | 2303 | 1479 | -1765 | -1524 | 2486 | 2303 (1479 / -1765 / -1524) | kagi_56, 3617 (-84 / 3155 / -2428) |
| sdx3 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 145 | 1991 | 846 | 1115 | -1185 | 2435 | -344 (573 / 847 / -2327) | kagi_56, 3617 (-84 / 3155 / -2428) |
| sdx3 | retest | vrb_40000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 87 | 1155 | -583 | 61 | -809 | 1512 | -344 (-776 / 986 / -1029) | kagi_10, 1390 (118 / 65 / 1080) |
| sdx30 | lim_mid | vrb_40000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 56 | 1684 | 103 | 991 | 667 | 1019 | 282 (567 / 596 / 242) | pnf_10, 1951 (721 / -406 / -107) |
| sdx30 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 199 | 3042 | -219 | -1016 | 531 | 2612 | 453 (5 / -348 / -1517) | kagi_40, 2657 (-934 / -1031 / -26) |
| sdx30 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 82 | 618 | 373 | 32 | 1066 | 485 | 618 (373 / 32 / 1066) | urenko_14, 1091 (-267 / -1452 / -151) |
| sdx30 | rej_flow | dol_500 | {"d": "E", "F": 9} | plain60/60 / short | 60 / 60 | 62 | 592 | -282 | -737 | -409 | 420 | 592 (-282 / -737 / -409) | wrenko_20, 383 (-313 / -316 / -602) |
| sdx30 | rej_native | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 129 | 765 | 82 | -674 | -730 | 266 | 765 (82 / -674 / -730) | kagi_56, 1505 (53 / -888 / -1269) |
| sdx30 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 129 | 765 | 82 | -674 | -730 | 266 | 765 (82 / -674 / -730) | kagi_56, 1505 (53 / -888 / -1269) |
| sdx5 | break | dol_6000 | {"d": "A", "F": 9, "n": 1} | sym15u / short | 120 / 120 | 48 | 1203 | -721 | 181 | -1443 | 1268 | 668 (-559 / 94 / -1148) | pnf_14, 2323 (-533 / 988 / 255) |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 720 | 2734 | 720 | 3 | -3881 | 2478 | 2734 (720 / 3 / -3881) | wrenko_20, 2442 (357 / 891 / -1052) |
| sdx5 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 609 | 2348 | 639 | 516 | -3774 | 2502 | 2348 (639 / 516 / -3774) | mrenko_20, 2572 (-102 / -1530 / -5419) |
| sdx5 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / short | 120 / 120 | 141 | 1883 | 722 | -27 | -1763 | 1737 | 1506 (460 / 594 / 74) | kagi_28, 2330 (3481 / 902 / -3209) |
| sdx5 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 120 / 120 | 97 | 1766 | 159 | -855 | -1246 | 2358 | 594 (112 / -720 / -1433) | wrenko_14, 441 (27 / 873 / 69) |
| sdx5 | rej_native | dol_500 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / short | 120 / 120 | 106 | 1741 | 362 | -1006 | 107 | 1880 | 1193 (140 / -113 / -2163) | urenko_10, 2412 (-1189 / 369 / -649) |
| sdx5 | rej_zone | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 328 | 1500 | 211 | 283 | -205 | 1764 | 1500 (211 / 283 / -205) | mrenko_20, 2334 (-819 / -884 / -1076) |
| sdx5 | retest | vrb_700 | {"d": "A", "M": 6, "tol": 0.5} | plain60/60 / short | 60 / 60 | 31 | 424 | -598 | -563 | 120 | 460 | 424 (-598 / -563 / 120) | kagi_20, 1774 (-756 / -147 / -45) |
| sdx60 | lim_mid | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 84 | 1048 | -893 | -703 | 356 | 2009 | -23 (-766 / -163 / -476) | kagi_80, 1628 (155 / 544 / -311) |
| sdx60 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 85 | 1152 | -236 | -482 | 931 | 2020 | -401 (-307 / -554 / -334) | pnf_20, 1933 (-320 / -699 / -24) |
| sdx60 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / both | 60 / 60 | 175 | 753 | 730 | -311 | -285 | 516 | 753 (730 / -311 / -285) | urenko_10, 986 (-87 / -92 / 901) |
| sdx60 | rej_flow | dol_500 | {"d": "E", "F": 9} | plain60/60 / short | 60 / 60 | 34 | 255 | -200 | 56 | 401 | 163 | 255 (-200 / 56 / 401) | wrenko_10, 432 (-131 / 314 / 665) |
| sdx60 | rej_native | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 94 | 686 | 308 | -151 | 848 | 742 | 686 (308 / -151 / 848) | urenko_20, 1065 (125 / -191 / 644) |
| sdx60 | rej_zone | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 94 | 686 | 308 | -151 | 848 | 742 | 686 (308 / -151 / 848) | urenko_20, 1065 (125 / -191 / 644) |
| sdx_renko28 | break | vrb_70000 | {"d": "E", "F": 9, "n": 1} | sym15u / short | 120 / 120 | 37 | 1183 | -315 | -54 | 190 | 1607 | 273 (23 / -271 / 108) | pnf_14, 2292 (-1534 / 786 / -391) |
| sdx_renko28 | lim_mid | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 123 | 1772 | -278 | 334 | -454 | 1753 | 1380 (-1045 / -932 / -770) | mrenko_10, 3882 (-32 / 158 / -242) |
| sdx_renko28 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 131 | 1705 | 72 | -56 | -1831 | 1589 | 1406 (-914 / -1004 / -714) | kagi_56, 3300 (213 / 469 / 2009) |
| sdx_renko28 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 537 | 5198 | -406 | -1538 | 809 | 6421 | 5198 (-406 / -1538 / 809) | mrenko_10, 4161 (-1746 / -3181 / -2583) |
| sdx_renko28 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / short | 120 / 120 | 102 | 1940 | 787 | 26 | -743 | 1348 | 883 (-10 / -213 / 1093) | wrenko_10, 877 (513 / -550 / 377) |
| sdx_renko28 | rej_native | vrb_700 | {"d": "E", "F": 0, "tol": 0.5} | plain60/60 / both | 60 / 60 | 640 | 2904 | -615 | -269 | 1795 | 3570 | 2904 (-615 / -269 / 1795) | pnf_5, 3581 (-461 / -885 / -96) |
| sdx_renko28 | rej_zone | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 581 | 3301 | -1287 | -1511 | 1839 | 4100 | 3301 (-1287 / -1511 / 1839) | pnf_5, 3581 (-461 / -885 / -96) |
| sdx_renko28 | retest | vrb_70000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 52 | 720 | -267 | -30 | 182 | 1672 | -141 (-476 / -371 / -183) | pnf_14, 1596 (-851 / 795 / 41) |
| sdx_rng28 | break | vrb_70000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 92 | 1889 | -492 | -827 | -552 | 3167 | -60 (-156 / -1165 / 79) | frenko_40, 3408 (-2123 / 661 / -816) |
| sdx_rng28 | lim_mid | dol_6000 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / short | 120 / 120 | 115 | 2295 | 343 | 1982 | -727 | 858 | 1179 (249 / 1634 / 561) | frenko_40, 3377 (299 / -3020 / -3304) |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 1024 | 4026 | -947 | 896 | -3778 | 6473 | 4026 (-947 / 896 / -3778) | pnf_7, 3324 (-202 / 219 / -1999) |
| sdx_rng28 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 462 | 2252 | -1322 | -833 | -1038 | 2734 | 2252 (-1322 / -833 / -1038) | mrenko_14, 2249 (2358 / -2729 / 945) |
| sdx_rng28 | rej_flow | dol_500 | {"d": "E", "F": 9} | plain60/60 / short | 60 / 60 | 300 | 1148 | 101 | -933 | 1420 | 1015 | 1148 (101 / -933 / 1420) | wrenko_10, 2295 (245 / -1493 / 2758) |
| sdx_rng28 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 501 | 2495 | -1913 | -53 | -1658 | 2241 | 2495 (-1913 / -53 / -1658) | wrenko_10, 3234 (2062 / -100 / 5954) |
| sdx_rng28 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 501 | 2495 | -1913 | -53 | -1658 | 2241 | 2495 (-1913 / -53 / -1658) | wrenko_10, 3234 (2062 / -100 / 5954) |
| sdx_rng28 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 117 | 2944 | -978 | 239 | 485 | 3365 | 731 (-838 / 662 / -973) | frenko_28, 2182 (-899 / -1243 / -3435) |
| sdx_vol1100 | break | dol_6000 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 276 | 2159 | -419 | 987 | 1738 | 3340 | -244 (-22 / 1484 / -756) | pnf_5, 4031 (-1409 / -503 / 658) |
| sdx_vol1100 | lim_mid | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 126 | 2082 | 898 | 846 | -2139 | 2172 | -362 (476 / -154 / -544) | pnf_20, 6337 (-998 / 71 / 1443) |
| sdx_vol1100 | lim_prox | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 913 | 3182 | -1644 | 2479 | -5012 | 2626 | 3182 (-1644 / 2479 / -5012) | pnf_20, 5565 (-679 / -26 / -465) |
| sdx_vol1100 | rej | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 455 | 2348 | 775 | 167 | 316 | 2211 | 2348 (775 / 167 / 316) | frenko_28, 3089 (-275 / -2567 / -1719) |
| sdx_vol1100 | rej_flow | dol_500 | {"d": "E", "F": 9} | plain60/60 / short | 60 / 60 | 247 | 2104 | 408 | 217 | -1011 | 1195 | 2104 (408 / 217 / -1011) | wrenko_20, 2232 (-129 / -218 / 268) |
| sdx_vol1100 | rej_native | dol_350 | {"d": "E", "F": 9, "tol": 0.5} | plain60/60 / short | 60 / 60 | 483 | 2484 | 931 | 169 | 166 | 2324 | 2484 (931 / 169 / 166) | wrenko_20, 3970 (-570 / -433 / -756) |
| sdx_vol1100 | rej_zone | dol_500 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / short | 60 / 60 | 349 | 2506 | -1329 | -553 | 857 | 3731 | 2506 (-1329 / -553 / 857) | mrenko_14, 3444 (914 / 374 / -624) |
| sdx_vol1100 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 227 | 3437 | -1140 | -704 | 968 | 4601 | -126 (-81 / 836 / -755) | pnf_14, 2174 (-829 / 511 / -380) |
| zones | break | rng_20 | {"n": 3, "k": 0.5} | asym10u/20u / both | 120 / 120 | 65 | 1780 | -207 | 1188 | -715 | 2006 | 544 (132 / 719 / -495) | mom_14, 2369 (-404 / 426 / 270) |
| zones | break_native | rng_14 | {"n": 3, "k": 0.5} | asym20u/10u / both | 120 / 108 | 84 | 2033 | -807 | 123 | 171 | 1556 | 901 (-1002 / 381 / 668) | mom_10, 2794 (-344 / 462 / -516) |
| zones | false_break | rng_14 | {"M": 1, "k": 0.5} | asym15u/30u / short | 120 / 120 | 53 | 1806 | 238 | 747 | -44 | 1799 | 394 (237 / 398 / 21) | renko_10, 1688 (-207 / 321 / -725) |
| zones | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym30u / both | 120 / 120 | 92 | 1781 | -499 | 864 | -1928 | 1942 | 57 (264 / 699 / -518) | renko_10, 1849 (-1626 / 1128 / -516) |
| zones | reject | rng_14 | {"tol": 1.0, "conf": "body"} | sym30u / both | 120 / 120 | 133 | 3041 | 2935 | -1064 | 682 | 3212 | 1191 (1364 / -499 / -424) | renko_10, 1801 (-82 / 401 / -571) |
| zones | reject_native | rng_14 | {"tol": 0.5, "conf": "body"} | sym30u / both | 120 / 120 | 134 | 2702 | 2260 | -2018 | 250 | 3460 | 973 (949 / -637 / -983) | swing_atr_0.15, 2146 (394 / -146 / 547) |
| zones | retest | rng_14 | {"M": 3, "tol": 0.5} | asym15u/30u / both | 120 / 120 | 85 | 1789 | -304 | -1453 | -436 | 1882 | 492 (609 / -1246 / 237) | dchg_10, 1355 (-570 / 198 / 368) |
| zones | retest_native | rng_14 | {"M": 10, "tol": 0.5} | sym30u / short | 120 / 120 | 52 | 1806 | 541 | -739 | -371 | 2106 | 623 (169 / -193 / -441) | dchg_14, 1513 (-101 / -122 / -351) |

### NYPM - other level modules
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 132 | 3206 | 269 | -467 | 638 | 3248 | 1115 (42 / -584 / 2327) | urenko_10, 3386 (-215 / -1066 / -1338) |
| fib15 | break_native | vrb_700 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 140 | 3217 | 133 | -157 | -867 | 3438 | 1754 (18 / -301 / 1310) | urenko_10, 3296 (118 / -747 / -1540) |
| fib15 | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 126 | 2702 | -508 | -1080 | 334 | 3392 | 1876 (-273 / -760 / 39) | urenko_28, 3285 (-897 / -1602 / 168) |
| fib15 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 126 | 2702 | -508 | -1080 | 334 | 3392 | 1876 (-273 / -760 / 39) | urenko_28, 3285 (-897 / -1602 / 168) |
| fib15 | pullback | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 107 | 1130 | 187 | -353 | 107 | 1150 | 517 (-366 / -221 / 1076) | urenko_14, 1869 (-30 / -12 / -37) |
| fib15 | pullback_native | dol_6000 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 154 | 1645 | 437 | 765 | 111 | 830 | 1645 (437 / 765 / 111) | mrenko_20, 2154 (184 / -420 / -152) |
| fib15 | reject | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 135 | 2480 | -124 | -1121 | 204 | 2387 | 1428 (-459 / -1804 / -1361) | wrenko_14, 3784 (-345 / -1343 / 2139) |
| fib15 | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 276 | 2798 | -467 | 1465 | -486 | 1962 | 1329 (-88 / 1926 / -793) | wrenko_14, 3784 (-345 / -1343 / 2139) |
| fib15 | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 190 | 2513 | 812 | 1268 | -1696 | 1583 | 1185 (1188 / -610 / -1047) | wrenko_10, 3286 (93 / -404 / 983) |
| fib15 | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 190 | 2513 | 812 | 1268 | -1696 | 1583 | 1185 (1188 / -610 / -1047) | frenko_40, 3836 (116 / -100 / -2461) |
| fib5 | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 297 | 3578 | -210 | 1673 | -722 | 2136 | 302 (-227 / 1783 / -2813) | kagi_14, 4326 (634 / -449 / -5249) |
| fib5 | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 278 | 3324 | -704 | -1927 | 652 | 3009 | -1167 (-143 / -1203 / -1484) | mrenko_20, 3290 (-1099 / 214 / -1933) |
| fib5 | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 286 | 2289 | -770 | -561 | -1071 | 2541 | 210 (-364 / 58 / -3042) | lbrk_3_40, 3891 (-953 / -2389 / 59) |
| fib5 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 286 | 2289 | -770 | -561 | -1071 | 2541 | 210 (-364 / 58 / -3042) | lbrk_3_40, 3891 (-953 / -2389 / 59) |
| fib5 | pullback | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 169 | 1189 | 219 | 1920 | 384 | 1879 | 429 (-348 / 353 / -232) | urenko_28, 2745 (927 / 815 / -218) |
| fib5 | pullback_native | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 82 | 1180 | -543 | 760 | 1058 | 1234 | -153 (-854 / 914 / 371) | urenko_10, 1865 (-693 / 1105 / -22) |
| fib5 | reject | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 296 | 3010 | -221 | 1657 | 1062 | 2046 | 137 (-1147 / 1888 / -1614) | urenko_10, 5190 (867 / 1104 / 100) |
| fib5 | reject_native | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 296 | 3010 | -221 | 1657 | 1062 | 2046 | 137 (-1147 / 1888 / -1614) | urenko_14, 3775 (-1517 / 2905 / 1380) |
| fib5 | retest | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 123 | 1913 | -194 | 991 | 358 | 2075 | -253 (220 / 940 / -1447) | kagi_80, 2669 (-792 / 1234 / -3864) |
| fib5 | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 212 | 1890 | 403 | 508 | 555 | 3099 | 225 (255 / 904 / -1468) | kagi_56, 2959 (-1605 / -750 / -58) |
| fib60 | break | dol_350 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 72 | 1502 | 131 | -556 | -1238 | 1942 | -592 (-243 / -17 / 950) | urenko_20, 3622 (-931 / 339 / -776) |
| fib60 | break_native | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 431 | 1781 | -613 | 63 | 993 | 528 | 1781 (-613 / 63 / 993) | urenko_20, 3622 (-931 / 339 / -776) |
| fib60 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 185 | 2793 | -114 | -1593 | -370 | 2750 | -592 (-201 / -452 / -1288) | frenko_28, 2975 (-251 / -49 / -2488) |
| fib60 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 183 | 2544 | -178 | -1636 | -748 | 2587 | -1272 (66 / -741 / -787) | frenko_28, 2975 (-251 / -49 / -2488) |
| fib60 | pullback | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 112 | 1154 | -168 | 33 | 1030 | 1211 | 1154 (-168 / 33 / 1030) | urenko_10, 950 (-134 / -49 / -111) |
| fib60 | pullback_native | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 124 | 1147 | -154 | -514 | 855 | 1018 | 1147 (-154 / -514 / 855) | lbrk_3_40, 1090 (514 / -645 / 216) |
| fib60 | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 160 | 1847 | -862 | 2531 | 1525 | 2927 | 542 (-287 / 1219 / 326) | kagi_28, 1820 (-241 / -150 / -56) |
| fib60 | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 160 | 1847 | -862 | 2531 | 1525 | 2927 | 542 (-287 / 1219 / 326) | kagi_20, 2566 (-602 / -1595 / -766) |
| fib60 | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 67 | 1241 | -391 | -504 | 166 | 787 | 386 (-53 / 207 / 479) | mrenko_20, 2392 (-360 / 1609 / -959) |
| fib60 | retest_native | dol_500 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 67 | 1241 | -391 | -504 | 166 | 787 | 386 (-53 / 207 / 479) | pnf_20, 2972 (-1194 / 195 / 1413) |
| fibr_dev | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 152 | 2241 | -690 | -407 | 2955 | 3152 | 124 (-194 / -5 / 418) | kagi_28, 3270 (-463 / 160 / 151) |
| fibr_dev | break_native | vrb_700 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 337 | 2587 | 730 | -44 | 302 | 3926 | -225 (1077 / 3426 / -968) | kagi_20, 3177 (292 / 1852 / -1651) |
| fibr_dev | false_break | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 71 | 1633 | -203 | -76 | -1836 | 1453 | 716 (15 / -265 / -431) | mrenko_20, 2113 (-1084 / 533 / -722) |
| fibr_dev | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / short | 120 / 120 | 150 | 2157 | -469 | -722 | -791 | 2049 | 473 (839 / 109 / -1170) | pnf_14, 2266 (-564 / -453 / 81) |
| fibr_dev | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 159 | 2100 | -1153 | 18 | -404 | 2688 | -425 (-332 / 962 / -1297) | kagi_56, 3039 (-906 / -439 / 785) |
| fibr_dev | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 310 | 2919 | -21 | 3751 | 295 | 2947 | -190 (2061 / 1955 / -1601) | urenko_112, 2679 (-1704 / 1086 / -206) |
| fibr_dev | retest | vrb_40000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 96 | 1346 | -114 | 1356 | 693 | 563 | 230 (64 / 727 / -816) | kagi_112, 2769 (-1419 / 969 / 78) |
| fibr_dev | retest_native | vrb_40000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 104 | 1724 | -176 | 1459 | 685 | 849 | 360 (16 / 810 / -558) | kagi_112, 2734 (-611 / -1064 / -1498) |
| fibr_ib | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 235 | 3158 | -322 | 1421 | 180 | 2750 | -1361 (-385 / 916 / -1491) | pnf_5, 3612 (92 / -1032 / -493) |
| fibr_ib | break_native | vrb_40000 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 66 | 1778 | -123 | -718 | 699 | 1552 | 493 (-367 / 302 / 542) | frenko_40, 3856 (-1527 / 184 / -1787) |
| fibr_ib | false_break | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 267 | 2149 | -1781 | 308 | -921 | 4431 | -1178 (153 / 585 / -1970) | lbrk_3_40, 2998 (-1461 / -465 / -1676) |
| fibr_ib | false_break_native | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 270 | 1757 | -2305 | -109 | -16 | 4043 | -1017 (-927 / 111 / -1015) | mrenko_20, 3604 (-782 / -1742 / -1366) |
| fibr_ib | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 103 | 2850 | -295 | -373 | -692 | 2170 | 1443 (-108 / 194 / -111) | kagi_40, 2311 (-1067 / -120 / 1124) |
| fibr_ib | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 267 | 3485 | 245 | 3147 | -1000 | 2581 | -1094 (306 / 724 / -3142) | urenko_56, 2936 (-599 / 129 / -207) |
| fibr_ib | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 94 | 2795 | 219 | -460 | -2092 | 2233 | 1813 (377 / -1015 / -1312) | kagi_10, 3021 (-364 / 170 / 78) |
| fibr_ib | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 94 | 2795 | 219 | -460 | -2092 | 2233 | 1813 (377 / -1015 / -1312) | kagi_10, 3021 (-364 / 170 / 78) |
| fibr_on | break | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 235 | 2308 | -806 | 3069 | -2296 | 3200 | 714 (-1463 / 183 / -817) | urenko_28, 2288 (-1496 / 1579 / 3141) |
| fibr_on | break_native | vrb_700 | {"n": 2, "k": 0.25} | plain60/60 / long | 60 / 60 | 242 | 1931 | -489 | 69 | 634 | 1508 | 1931 (-489 / 69 / 634) | wrenko_14, 2613 (83 / 1407 / 1700) |
| fibr_on | false_break | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 53 | 763 | -456 | 1045 | -863 | 817 | 269 (342 / 432 / -1009) | pnf_14, 2221 (-828 / 1006 / -1840) |
| fibr_on | false_break_native | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 53 | 763 | -424 | 1045 | -863 | 817 | 269 (373 / 432 / -1009) | pnf_14, 2219 (-607 / 594 / -2194) |
| fibr_on | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 224 | 4457 | -1590 | -30 | -30 | 3118 | 101 (-388 / 526 / -1683) | kagi_40, 2090 (-805 / -1514 / 1626) |
| fibr_on | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 224 | 4457 | -1590 | -30 | -30 | 3118 | 101 (-388 / 526 / -1683) | kagi_40, 3277 (-279 / -634 / -938) |
| fibr_on | retest | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 184 | 1457 | -175 | 1397 | 580 | 308 | 940 (65 / 1030 / -1820) | urenko_10, 2547 (-512 / 810 / -273) |
| fibr_on | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 104 | 1685 | 11 | 802 | -156 | 1909 | 1452 (399 / 858 / -1570) | pnf_14, 2587 (-133 / 2095 / -1145) |
| fibr_or | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 131 | 2345 | -757 | -617 | -321 | 2248 | -1107 (-118 / -616 / -1231) | mrenko_20, 3722 (1679 / 177 / 2896) |
| fibr_or | break_native | dol_350 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 235 | 3359 | -844 | 380 | -352 | 3018 | -1772 (-821 / 1837 / -1032) | lbrk_3_10, 3227 (-97 / -651 / -3922) |
| fibr_or | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 95 | 1947 | -363 | -108 | 104 | 2664 | 173 (-761 / -578 / -922) | kagi_10, 3162 (-2539 / 1556 / 88) |
| fibr_or | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 101 | 1915 | -644 | 237 | 34 | 2797 | 306 (-1352 / 26 / -599) | kagi_10, 2711 (-2616 / 999 / 797) |
| fibr_or | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 114 | 2224 | -251 | -387 | 381 | 2411 | 286 (-78 / -97 / -784) | wrenko_14, 2671 (-626 / -664 / -1437) |
| fibr_or | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 118 | 1989 | -217 | -763 | 16 | 2124 | 9 (245 / -79 / -869) | wrenko_14, 2671 (-626 / -664 / -1437) |
| fibr_or | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / short | 60 / 60 | 220 | 1842 | -373 | -366 | -1444 | 1836 | 1842 (-373 / -366 / -1444) | wrenko_14, 2541 (-582 / -25 / -891) |
| fibr_or | retest_native | dol_350 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 111 | 1940 | -1340 | -367 | -1353 | 2432 | -261 (-1026 / 567 / -2624) | wrenko_14, 3433 (-1079 / 1971 / 1090) |
| fibr_pd | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 103 | 1498 | -63 | -222 | -1809 | 1540 | 1386 (-436 / 377 / -1732) | lbrk_3_40, 1967 (-914 / 42 / -1381) |
| fibr_pd | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 108 | 1920 | 149 | -343 | -2430 | 970 | 1769 (-536 / 416 / -2516) | lbrk_3_40, 1967 (-914 / 42 / -1381) |
| fibr_pd | false_break | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 206 | 1267 | 172 | -203 | -203 | 1178 | 1267 (172 / -203 / -203) | pnf_20, 1998 (-349 / 1339 / -3324) |
| fibr_pd | false_break_native | dol_350 | {"M": 2, "k": 0.5} | plain60/60 / short | 60 / 60 | 215 | 1390 | -358 | 73 | 223 | 1290 | 1390 (-358 / 73 / 223) | lbrk_3_40, 1967 (-914 / 38 / -1381) |
| fibr_pd | reject | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 102 | 1736 | 1186 | -1977 | -1571 | 1245 | 715 (32 / -218 / -1222) | wrenko_14, 3093 (14 / 1008 / -2214) |
| fibr_pd | reject_native | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 228 | 2046 | 905 | 264 | -2804 | 1248 | -876 (868 / 48 / -2156) | kagi_112, 3634 (-868 / -66 / -1162) |
| fibr_pd | retest | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / short | 60 / 60 | 171 | 1375 | -260 | -866 | -857 | 2264 | 1375 (-260 / -866 / -857) | pnf_10, 2090 (436 / -59 / -1075) |
| fibr_pd | retest_native | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / short | 60 / 60 | 171 | 1375 | -260 | -866 | -857 | 2264 | 1375 (-260 / -866 / -857) | kagi_56, 2104 (27 / 796 / -2196) |
| piv_cama | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 230 | 1619 | 1235 | 2518 | -43 | 1664 | 1205 (1713 / 1795 / -1183) | kagi_10, 2062 (1743 / 913 / -1667) |
| piv_cama | break_native | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 229 | 3002 | -798 | 88 | -642 | 3792 | -765 (-168 / 846 / -1908) | mrenko_20, 2483 (797 / 1927 / 1854) |
| piv_cama | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 205 | 1211 | -1613 | 1135 | 1006 | 996 | -1356 (-980 / 2405 / -2164) | kagi_20, 1059 (-2014 / 1462 / -4681) |
| piv_cama | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 224 | 1497 | -1854 | 1699 | -3056 | 2291 | -1113 (-676 / 1424 / -2423) | kagi_20, 1272 (-2038 / 898 / -4067) |
| piv_cama | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 98 | 2042 | -199 | 1525 | -852 | 2117 | 933 (-394 / 440 / -460) | kagi_10, 2838 (205 / -269 / -2327) |
| piv_cama | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 123 | 1527 | -404 | 586 | -1201 | 1771 | 1183 (47 / -317 / -1816) | kagi_10, 2235 (495 / -257 / -1384) |
| piv_cama | retest | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 200 | 2795 | -1905 | -399 | -658 | 1996 | -407 (-1135 / 763 / -1218) | urenko_20, 3017 (1323 / -981 / 973) |
| piv_cama | retest_native | vrb_700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 200 | 2795 | -1905 | -399 | -658 | 1996 | -407 (-1135 / 763 / -1218) | wrenko_14, 2890 (-621 / -741 / 2051) |
| piv_floor | break | vrb_700 | {"n": 2, "k": 0.25} | plain60/60 / short | 60 / 60 | 151 | 909 | -738 | 140 | -1041 | -99 | 909 (-738 / 140 / -1041) | urenko_80, 2104 (89 / 2484 / 144) |
| piv_floor | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 89 | 1151 | -140 | 1588 | -384 | -217 | 359 (294 / 2101 / -1035) | urenko_56, 2598 (440 / 2679 / 586) |
| piv_floor | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 83 | 719 | 751 | -560 | -512 | 358 | -136 (519 / -670 / 428) | kagi_56, 1091 (-1194 / 1149 / -191) |
| piv_floor | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 89 | 910 | 890 | -846 | -175 | 699 | 139 (560 / -667 / 76) | kagi_56, 1091 (-1194 / 1149 / -191) |
| piv_floor | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 105 | 1240 | 189 | 1081 | 668 | 1381 | 551 (136 / -225 / -339) | kagi_14, 2732 (312 / 945 / 1219) |
| piv_floor | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 208 | 2755 | 17 | 4960 | 367 | 516 | 823 (-146 / 4076 / -507) | kagi_28, 4162 (-247 / 2182 / -410) |
| piv_floor | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 104 | 997 | -1308 | 507 | -430 | 223 | -408 (-1085 / 324 / -1243) | mrenko_20, 2261 (-762 / -663 / -1617) |
| piv_floor | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 169 | 2081 | -855 | 2779 | -42 | 807 | -1519 (-1287 / 1451 / -1205) | lbrk_3_10, 2174 (539 / -433 / 264) |
| piv_wf | break | vrb_700 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 104 | 1785 | 1407 | 575 | 11 | 1781 | 598 (927 / 379 / -674) | kagi_56, 2012 (-1824 / 1272 / 416) |
| piv_wf | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 106 | 1319 | -902 | 836 | 38 | 325 | -23 (-951 / 536 / 117) | kagi_56, 2012 (-1824 / 1272 / 416) |
| piv_wf | false_break | vrb_700 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 100 | 1669 | -715 | 213 | -504 | 1544 | 84 (-849 / -351 / -131) | kagi_56, 2201 (-2119 / 1210 / 156) |
| piv_wf | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 183 | 1580 | -1714 | 1189 | -3484 | 1745 | -143 (-1441 / 2194 / -3949) | kagi_56, 2012 (-1842 / 1094 / 416) |
| piv_wf | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 116 | 1257 | 320 | 110 | -1973 | 1224 | 528 (689 / -647 / -1559) | mrenko_20, 1762 (-1585 / -62 / -1571) |
| piv_wf | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 253 | 2301 | 319 | -234 | -305 | 595 | -807 (1719 / -249 / -928) | kagi_40, 3055 (-151 / -947 / -2159) |
| piv_wf | retest | dol_350 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 213 | 1967 | 159 | 2615 | -2683 | 1744 | 1472 (-1050 / 2556 / -3906) | kagi_28, 2470 (-1242 / 354 / 915) |
| piv_wf | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 205 | 2085 | -2602 | 722 | -2855 | 1276 | -365 (-286 / 477 / -1247) | kagi_28, 2470 (-1242 / 354 / 915) |
| swcluster | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 40 | 882 | -980 | 384 | -628 | 1206 | 616 (-904 / 365 / -995) | pnf_5, 1434 (-579 / -308 / -267) |
| swcluster | break_native | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 52 | 1251 | -193 | 717 | 525 | 1608 | 981 (-230 / 747 / 227) | lbrk_3_20, 1484 (-898 / 212 / -2023) |
| swcluster | false_break | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 55 | 400 | -396 | 629 | -353 | 485 | 400 (-396 / 629 / -353) | lbrk_3_40, 711 (-608 / 898 / -670) |
| swcluster | false_break_native | dol_6000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 35 | 424 | -598 | 967 | 305 | 24 | 167 (85 / 618 / -176) | urenko_112, 948 (-1573 / 501 / -496) |
| swcluster | reject | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 65 | 1010 | 277 | 444 | -1021 | 1327 | 1010 (277 / 444 / -1021) | wrenko_14, 1368 (-235 / -439 / 744) |
| swcluster | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 56 | 1435 | 270 | -419 | -931 | 842 | 1255 (-197 / -737 / -562) | urenko_56, 1544 (242 / 371 / -1281) |
| swcluster | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 40 | 1102 | -97 | 1505 | 256 | 416 | 738 (146 / 953 / 513) | kagi_20, 1442 (-759 / 86 / 271) |
| swcluster | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 44 | 1618 | -3 | 1405 | 681 | 911 | 1067 (242 / 1133 / 1045) | pnf_7, 1287 (-302 / 729 / 809) |
| swsr15 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 117 | 2961 | 514 | -460 | 1073 | 3477 | 526 (535 / -752 / 842) | kagi_40, 3147 (-556 / 558 / 71) |
| swsr15 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 117 | 2961 | 514 | -460 | 1073 | 3477 | 526 (535 / -752 / 842) | kagi_40, 3147 (-556 / 558 / 71) |
| swsr15 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 112 | 2495 | -762 | -252 | 672 | 2908 | 158 (-272 / 569 / 196) | kagi_56, 2905 (-826 / 1401 / 1932) |
| swsr15 | false_break_native | vrb_700 | {"M": 3, "k": 0.5} | sym15u / short | 120 / 120 | 122 | 2688 | 446 | -20 | 858 | 2726 | 244 (157 / 162 / 343) | pnf_5, 2948 (43 / -480 / 1191) |
| swsr15 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 133 | 2792 | -184 | -34 | 1082 | 2134 | 1754 (-574 / 696 / -1246) | kagi_14, 3340 (255 / -524 / 1304) |
| swsr15 | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 134 | 3198 | -1156 | -297 | 368 | 3053 | 1012 (-1325 / -1206 / -539) | kagi_20, 4013 (690 / 61 / -2201) |
| swsr15 | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 109 | 1989 | 896 | 246 | 971 | 1977 | 986 (420 / -436 / 154) | pnf_20, 2920 (1261 / 1356 / -1090) |
| swsr15 | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 126 | 2410 | -568 | 350 | 681 | 2051 | 220 (-42 / -407 / -889) | kagi_56, 2938 (-421 / -968 / 2213) |
| swsr5 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 133 | 2791 | 566 | -124 | 942 | 2651 | 841 (41 / -282 / 344) | kagi_56, 3444 (-2207 / -1559 / 1262) |
| swsr5 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / short | 120 / 120 | 133 | 2791 | 566 | -124 | 942 | 2651 | 841 (41 / -282 / 344) | kagi_56, 3444 (-2207 / -1559 / 1262) |
| swsr5 | false_break | dol_6000 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 143 | 2710 | -1688 | -180 | 2027 | 2261 | -118 (-179 / 740 / 1789) | urenko_10, 3895 (-1112 / -1283 / 613) |
| swsr5 | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 142 | 2665 | -1758 | -91 | 2308 | 2174 | -302 (-284 / 650 / 1978) | urenko_10, 3895 (-1112 / -1283 / 613) |
| swsr5 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 154 | 2295 | 551 | 384 | 461 | 3442 | 779 (542 / -1043 / 520) | kagi_14, 2900 (435 / -192 / 1157) |
| swsr5 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 165 | 2981 | 290 | 1019 | 19 | 3754 | 1469 (402 / -269 / 621) | urenko_40, 2951 (-1432 / 2774 / -395) |
| swsr5 | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 132 | 2650 | 1673 | 36 | 1344 | 2407 | 759 (919 / -901 / 2193) | kagi_56, 4440 (-950 / -3103 / 1054) |
| swsr5 | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 157 | 2447 | -808 | -779 | -789 | 1562 | 425 (56 / -363 / -639) | kagi_56, 4019 (-261 / -2125 / 4208) |
| swsr60 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 169 | 1417 | 1297 | -797 | -1265 | 2029 | -2217 (858 / -1266 / -546) | pnf_40, 1767 (558 / -107 / 48) |
| swsr60 | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 141 | 1741 | -2842 | 849 | 857 | 2196 | 51 (-1851 / -1030 / -174) | kagi_40, 2879 (-1426 / 831 / -277) |
| swsr60 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 187 | 2016 | 888 | -971 | -1148 | 2792 | -1953 (471 / -1318 / -1571) | mrenko_20, 1784 (-2173 / -454 / -1920) |
| swsr60 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 187 | 2016 | 888 | -971 | -1148 | 2792 | -1953 (471 / -1318 / -1571) | mrenko_20, 1784 (-2173 / -454 / -1920) |
| swsr60 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 82 | 1368 | -854 | 399 | -738 | 1723 | 1249 (-370 / 1055 / -280) | kagi_40, 1934 (-1464 / 154 / -1935) |
| swsr60 | reject_native | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 151 | 1711 | -338 | 1166 | -356 | 1083 | 1711 (-338 / 1166 / -356) | kagi_40, 3196 (-733 / 1116 / -3739) |
| swsr60 | retest | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 72 | 1103 | 1059 | 111 | 26 | 1831 | 463 (559 / 203 / 112) | kagi_28, 1496 (335 / -641 / -63) |
| swsr60 | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 76 | 945 | 1077 | 133 | 1153 | 1732 | 687 (501 / 169 / 38) | kagi_80, 1967 (-1647 / 1506 / -2401) |
| stack | break | dol_350 | {"k": 3, "cw": 1.0} | sym15u / both | 120 / 120 | 106 | 2198 | -1538 | -710 | -443 | 1033 | 1519 (-536 / -423 / -265) | urenko_28, 2291 (234 / -41 / 1145) |
| stack | break_native | dib_40000 | {"k": 2, "cw": 0.5} | sym15u / both | 120 / 120 | 107 | 3072 | 144 | 769 | -10 | 2485 | 396 (-447 / 443 / -1074) | kagi_56, 2692 (-299 / -324 / 749) |
| stack | reject | rng_20 | {"k": 2, "cw": 1.0} | asym10u/20u / both | 120 / 120 | 101 | 2187 | -447 | 1473 | -506 | 1062 | 5 (-169 / 678 / 1190) | swing_atr_0.15, 1510 (-304 / -31 / 892) |
| stack | reject_native | dol_350 | {"k": 4, "cw": 2.0} | plain60/60 / short | 60 / 60 | 192 | 3062 | -384 | 254 | 556 | 2627 | 3062 (-384 / 254 / 556) | mrenko_14, 2715 (-713 / -2101 / -338) |
| book_walls | break | time_s_5 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 42 | 894 | -489 | -382 | 220 | 1042 | 894 (-489 / -382 / 220) | swing_atr_0.15, -78 (938 / -572 / 301) |
| book_walls | break_native | tm15 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 30 | 605 | -584 | -435 | -96 | 784 | 605 (-584 / -435 / -96) | swing_atr_0.15, -78 (938 / -572 / 301) |
| book_walls | reject | time_s_5 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 47 | 475 | -958 | -263 | -638 | 569 | 475 (-958 / -263 / -638) | no reversal row has trades |
| book_walls | reject_native | time_s_10 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 34 | 561 | 55 | -204 | -128 | 492 | 561 (55 / -204 / -128) | no reversal row has trades |
| book_walls | retest | time_s_5 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 47 | 499 | -402 | -181 | 44 | 592 | 499 (-402 / -181 / 44) | no reversal row has trades |
| book_walls | retest_native | time_s_10 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 34 | 627 | -374 | 538 | 3 | 600 | 627 (-374 / 538 / 3) | no reversal row has trades |
| book_walls_loose | break | cdr_100 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 96 | 1984 | 477 | -129 | -417 | 3812 | 162 (645 / -203 / -420) | renko_10, 1851 (1171 / 709 / 1332) |
| book_walls_loose | break_native | vol_4000 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 63 | 2298 | 1117 | -1651 | -239 | 2399 | 976 (718 / -1113 / -440) | renko_10, 1851 (1171 / 709 / 1332) |
| book_walls_loose | false_break | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 89 | 1908 | -489 | 1460 | -116 | 1811 | 1051 (-549 / 1157 / -368) | mom_10, 975 (-1229 / 1328 / -948) |
| book_walls_loose | false_break_native | dlt_45 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 86 | 1871 | -345 | 574 | 531 | 1850 | 1192 (-520 / 512 / -190) | mom_10, 975 (-1229 / 1328 / -948) |
| book_walls_loose | reject | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 120 / 120 | 57 | 1173 | 963 | -1384 | -1489 | 994 | 813 (584 / -958 / -514) | mom_20, 1045 (-261 / 1152 / 212) |
| book_walls_loose | reject_native | vol_4000 | {"tol": 0.5, "conf": "close"} | sym8u / both | 120 / 120 | 78 | 1240 | 1069 | -1699 | -1249 | 291 | 776 (361 / -1333 / -734) | mom_20, 851 (654 / 44 / -123) |
| book_walls_loose | retest | dib_2000 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 41 | 962 | -161 | -663 | 174 | 1475 | 536 (-137 / -571 / -124) | mrenko_10, 764 (-110 / -608 / 432) |
| book_walls_loose | retest_native | vsess_300 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 72 | 1146 | 212 | 787 | -261 | 941 | 827 (-372 / 140 / -270) | swing_atr_0.15, 682 (-920 / -303 / 706) |
| channel | break | dol_6000 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 131 | 2891 | -746 | -580 | 1666 | 2590 | -236 (-287 / -157 / -285) | pnf_20, 2734 (517 / -988 / -662) |
| channel | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 166 | 2268 | 71 | -1190 | -157 | 2076 | 675 (-331 / -1479 / -388) | mrenko_20, 3932 (-2003 / 2173 / -8) |
| channel | false_break | vrb_70000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 120 | 1836 | -1485 | 363 | -102 | 2244 | 183 (-755 / 7 / -632) | pnf_7, 3216 (-1127 / 782 / 1821) |
| channel | false_break_native | vrb_70000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 121 | 1790 | -1361 | 351 | 66 | 2198 | 122 (-740 / -54 / -518) | kagi_56, 3285 (-130 / 684 / 4085) |
| channel | reject | vrb_40000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 49 | 2136 | -146 | 628 | 138 | 2109 | 704 (-519 / 697 / -359) | frenko_40, 3044 (-754 / 780 / -1553) |
| channel | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 60 / 60 | 409 | 2271 | -842 | 579 | 152 | 1533 | 2271 (-842 / 579 / 152) | frenko_40, 3124 (-1460 / -819 / -1409) |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 121 | 1738 | -1201 | -426 | -86 | 2356 | 39 (-1285 / -511 / 348) | kagi_28, 2884 (-1066 / -819 / -1144) |
| channel | retest_native | vrb_40000 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 78 | 1813 | -960 | -567 | 760 | 1141 | 443 (-566 / 400 / 97) | kagi_40, 4816 (-153 / -1208 / 1427) |
| fvg15 | break | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 104 | 1347 | 97 | 511 | -716 | 1428 | -55 (384 / 215 / -926) | kagi_28, 1564 (-1302 / 388 / 1546) |
| fvg15 | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 104 | 1347 | 97 | 511 | -716 | 1428 | -55 (384 / 215 / -926) | kagi_28, 1564 (-1302 / 388 / 1546) |
| fvg15 | false_break | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 101 | 1146 | 718 | 563 | -1379 | 1557 | 157 (772 / -585 / -689) | pnf_28, 1383 (-786 / 196 / 311) |
| fvg15 | false_break_native | dol_350 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 101 | 1144 | 312 | 723 | -1567 | 818 | 94 (835 / -24 / -982) | pnf_28, 1383 (-786 / 196 / 311) |
| fvg15 | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 98 | 739 | 279 | -985 | -843 | 969 | -60 (155 / -486 / -899) | pnf_5, 1177 (560 / -604 / 190) |
| fvg15 | reject_native | vrb_40000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 34 | 1545 | -182 | 363 | -346 | 1563 | 365 (26 / 84 / -467) | pnf_5, 1044 (-987 / 68 / 64) |
| fvg15 | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 120 | 601 | 276 | -383 | 344 | 869 | 601 (276 / -383 / 344) | urenko_28, 1488 (-659 / 345 / -893) |
| fvg15 | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 99 | 733 | 10 | 151 | -335 | 255 | -339 (369 / 108 / -247) | pnf_7, 2069 (-451 / 295 / -1907) |
| fvg5 | break | vrb_40000 | {"n": 2, "k": 0.25} | sym15u / short | 120 / 120 | 36 | 1089 | -364 | -320 | -400 | 177 | 300 (243 / 240 / 345) | kagi_40, 2941 (-43 / 529 / 74) |
| fvg5 | break_native | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 208 | 2242 | -1096 | -547 | -2145 | 1206 | 858 (-1005 / -524 / -63) | kagi_28, 2590 (-1104 / -310 / -224) |
| fvg5 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 197 | 1213 | 802 | 1590 | 551 | 1201 | -300 (554 / 1301 / 792) | kagi_40, 1497 (237 / -1092 / -344) |
| fvg5 | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 200 | 1182 | -52 | 1740 | 697 | 518 | -1091 (-99 / 1513 / 419) | kagi_28, 1603 (-227 / -235 / -464) |
| fvg5 | reject | dol_350 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 331 | 1028 | -601 | -972 | -1599 | -289 | 1028 (-601 / -972 / -1599) | mrenko_14, 1877 (86 / 1529 / -360) |
| fvg5 | reject_native | vrb_40000 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 38 | 1132 | -829 | 508 | -816 | 413 | 494 (-237 / 527 / -906) | kagi_20, 1978 (-13 / -449 / -1512) |
| fvg5 | retest | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 311 | 2041 | -507 | -733 | 178 | 770 | 2041 (-507 / -733 / 178) | wrenko_20, 1812 (-1404 / 1937 / 357) |
| fvg5 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 271 | 1762 | 88 | -1082 | 69 | 1092 | 1762 (88 / -1082 / 69) | frenko_40, 1893 (54 / 15 / -175) |
| gaps | break | vol_500 | {"n": 1, "k": 0.25} | sym30u / both | 120 / 120 | 36 | 1482 | -209 | 1576 | 785 | 971 | 282 (-461 / 91 / -666) | kagi_28, 2351 (-1950 / -331 / -1857) |
| gaps | break_native | dol_6000 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 50 | 1902 | -425 | 476 | -875 | 1782 | 352 (-590 / 242 / -783) | wrenko_14, 1966 (-1477 / 311 / -678) |
| gaps | false_break | time_s_5 | {"M": 1, "k": 0.0} | sym30u / both | 120 / 120 | 39 | 1447 | -588 | 325 | -1319 | 918 | 180 (-1035 / 13 / -396) | renko_14, 1441 (459 / -563 / -271) |
| gaps | false_break_native | vsess_200 | {"M": 3, "k": 0.5} | sym8u / both | 120 / 120 | 34 | 1555 | -904 | 638 | -875 | 1064 | 88 (-977 / 205 / -631) | kagi_56, 1904 (-1039 / 978 / -175) |
| gaps | reject | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 189 | 1492 | 731 | -1239 | -821 | 493 | 1492 (731 / -1239 / -821) | kagi_112, 1442 (-214 / -380 / -128) |
| gaps | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 118 | 2446 | -357 | 1370 | -177 | 2150 | -174 (-458 / 308 / -836) | kagi_28, 2841 (-343 / 129 / -838) |
| gaps | retest | cusum_28 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 32 | 1736 | -1009 | 1068 | -1865 | 1624 | 190 (-667 / 387 / -1054) | kagi_56, 1919 (-539 / 412 / 1770) |
| gaps | retest_native | vol_4000 | {"M": 3, "tol": 0.5} | sym8u / both | 120 / 120 | 30 | 1273 | -630 | -3 | -721 | 744 | 243 (-801 / -243 / -71) | kagi_56, 2649 (-496 / -97 / 417) |
| mmove | break | dol_6000 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 198 | 2300 | -1038 | -194 | -330 | 2191 | -409 (-436 / 1467 / -764) | pnf_14, 3555 (-25 / -1259 / -1777) |
| mmove | break_native | dol_6000 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 198 | 2300 | -1038 | -194 | -330 | 2191 | -409 (-436 / 1467 / -764) | pnf_14, 3555 (-25 / -1259 / -1777) |
| mmove | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 285 | 3509 | -276 | 1342 | -585 | 4192 | 347 (-370 / 600 / -278) | mrenko_14, 4681 (-1015 / 591 / -1419) |
| mmove | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 285 | 3509 | -276 | 1342 | -585 | 4192 | 347 (-370 / 600 / -278) | mrenko_14, 4681 (-1015 / 591 / -1419) |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 242 | 2230 | 761 | -280 | -16 | 1468 | -1024 (-50 / -3194 / -2404) | pnf_5, 1952 (75 / -438 / 2598) |
| mmove | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 129 | 1999 | -320 | 567 | -154 | 1998 | 1637 (-403 / 211 / 29) | pnf_7, 2490 (-534 / 260 / 1315) |
| mmove | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 114 | 1591 | 1082 | 90 | -1308 | 1594 | -639 (140 / 170 / 1122) | urenko_10, 3260 (-205 / -1462 / 726) |
| mmove | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 114 | 1376 | -1318 | 749 | -581 | 246 | 48 (-522 / 407 / 2) | urenko_10, 3260 (-205 / -1462 / 726) |
| ob15 | break | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 45 | 870 | -1115 | 1921 | -1209 | 1982 | 353 (-300 / 853 / -1033) | frenko_28, 1311 (-552 / 809 / -735) |
| ob15 | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 45 | 870 | -1115 | 1921 | -1209 | 1982 | 353 (-300 / 853 / -1033) | frenko_28, 1311 (-552 / 809 / -735) |
| ob15 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 45 | 978 | -825 | 254 | -114 | 1714 | 843 (-179 / 255 / -854) | pnf_20, 1383 (-438 / 971 / 66) |
| ob15 | false_break_native | dol_6000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 39 | 1164 | -538 | 1213 | -684 | 1581 | 631 (-614 / 697 / -2215) | pnf_20, 1394 (-674 / 804 / 277) |
| ob15 | reject | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 90 | 904 | 512 | -409 | -673 | 873 | 904 (512 / -409 / -673) | wrenko_10, 925 (-325 / -377 / 1269) |
| ob15 | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 96 | 874 | 301 | 159 | -52 | 903 | 874 (301 / 159 / -52) | wrenko_10, 1100 (158 / 617 / 1076) |
| ob15 | retest | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 35 | 1080 | -107 | -198 | -526 | 894 | 476 (-96 / -323 / -54) | kagi_10, 1312 (-71 / 347 / 114) |
| ob15 | retest_native | dol_500 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 35 | 1080 | -107 | -198 | -526 | 894 | 476 (-96 / -323 / -54) | wrenko_10, 1242 (-237 / 630 / -361) |
| ob5 | break | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 72 | 1928 | -105 | 220 | 2480 | 1611 | 660 (-407 / 550 / 372) | urenko_10, 1964 (-227 / -120 / 1433) |
| ob5 | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 68 | 1342 | 393 | 635 | 2003 | 1962 | 775 (-121 / 286 / 618) | urenko_10, 2181 (-420 / 239 / 1123) |
| ob5 | false_break | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 68 | 1771 | -70 | 552 | 1555 | 2673 | 1031 (-341 / 196 / 72) | urenko_80, 1758 (-619 / 734 / 1100) |
| ob5 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 68 | 1771 | -70 | 552 | 1555 | 2673 | 1031 (-341 / 196 / 72) | urenko_80, 1758 (-619 / 734 / 1100) |
| ob5 | reject | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 112 | 930 | -169 | -394 | 268 | 1627 | 930 (-169 / -394 / 268) | lbrk_3_10, 1483 (-588 / -295 / -66) |
| ob5 | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 114 | 1128 | -604 | -630 | -299 | 1764 | 1128 (-604 / -630 / -299) | urenko_40, 1452 (-364 / -720 / -1186) |
| ob5 | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 66 | 1637 | 192 | 955 | 1323 | 2213 | 345 (32 / 934 / -40) | urenko_10, 2171 (-115 / 238 / -314) |
| ob5 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 70 | 2211 | -406 | 884 | 1917 | 2671 | 824 (-385 / 805 / 869) | urenko_10, 2276 (28 / 288 / 302) |
| open_range | break | rng_10 | {"n": 3, "k": 0.25} | asym20u/10u / both | 120 / 78 | 349 | 3873 | -1219 | -1703 | -1699 | 2102 | -802 (-500 / -275 / -6141) | swing_pct_8, 3999 (-973 / 293 / 1639) |
| open_range | break_native | rng_10 | {"n": 3, "k": 0.25} | asym20u/10u / both | 120 / 78 | 352 | 3840 | -739 | -1259 | -1616 | 2547 | -1465 (272 / -590 / -5356) | swing_pct_8, 3999 (-973 / 293 / 1639) |
| open_range | false_break | tm1200 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 194 | 3201 | -2185 | -861 | 1140 | 2118 | -137 (-122 / -702 / -1259) | swing_pct_8, 3833 (-796 / 831 / 1402) |
| open_range | false_break_native | rng_14 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 232 | 3074 | -1074 | 306 | 1907 | 2909 | -794 (46 / -236 / 1997) | swing_atr_0.6, 3862 (-340 / 1191 / 2887) |
| open_range | reject | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 813 (1091 / -1871 / -1155) | wrenko_10, 2722 (-379 / -769 / 1754) |
| open_range | reject_native | dlt_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 217 | 3154 | 1473 | 1601 | 2437 | 1934 | 813 (1091 / -1871 / -1155) | dchg_112, 3058 (-851 / -785 / -1741) |
| open_range | retest | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 116 / 116 | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 133 (-2034 / -1800 / -953) | mom_28, 2633 (-1126 / 1670 / 2926) |
| open_range | retest_native | rng_10 | {"M": 10, "tol": 0.0} | sym15u / both | 116 / 116 | 284 | 3295 | -1401 | -2410 | 1408 | 1791 | 133 (-2034 / -1800 / -953) | renko_56, 2613 (-1769 / 473 / 218) |
| opens | break | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 120 / 120 | 161 | 2766 | -1910 | -784 | -471 | 2936 | -558 (-262 / -2258 / -410) | pnf_14, 2447 (-235 / 560 / 39) |
| opens | break_native | tick_300 | {"n": 2, "k": 0.0} | asym10u/20u / both | 120 / 120 | 161 | 2766 | -1910 | -784 | -471 | 2936 | -558 (-262 / -2258 / -410) | pnf_14, 2447 (-235 / 560 / 39) |
| opens | false_break | time_m_20 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 111 | 2859 | -993 | 34 | -12 | 3095 | 325 (-176 / 542 / -2222) | dchg_14, 2521 (-572 / 2137 / -2525) |
| opens | false_break_native | tib_25000 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 125 | 2780 | -851 | -477 | -259 | 2715 | 240 (120 / -393 / 21) | dchg_56, 2454 (45 / 3344 / -160) |
| opens | reject | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 120 / 120 | 151 | 2916 | 760 | -1324 | -957 | 2033 | 1400 (-93 / -845 / 284) | renko_10, 2641 (59 / 335 / -156) |
| opens | reject_native | vol_1700 | {"tol": 0.0, "conf": "close"} | sym8u / both | 120 / 120 | 151 | 2916 | 760 | -1324 | -957 | 2033 | 1400 (-93 / -845 / 284) | renko_10, 2689 (-315 / -298 / 795) |
| opens | retest | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 610 (-725 / -1025 / -1850) | mom_40, 2914 (-628 / 509 / -1624) |
| opens | retest_native | vol_1700 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 123 | 3080 | -1283 | -330 | -2619 | 1726 | 610 (-725 / -1025 / -1850) | mom_40, 2742 (-1502 / -295 / -1024) |
| prior_day | break | vol_750 | {"n": 1, "k": 0.25} | sym15u / both | 120 / 120 | 88 | 3218 | -249 | -3166 | -1481 | 3363 | 1924 (481 / -2265 / -1486) | mom_20, 2757 (-253 / -508 / -1396) |
| prior_day | break_native | vsess_120 | {"n": 3, "k": 0.0} | sym15u / both | 120 / 120 | 91 | 2959 | -204 | -697 | -3330 | 1835 | 890 (490 / -1135 / -2029) | mom_20, 2757 (-253 / -508 / -1396) |
| prior_day | false_break | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 120 / 120 | 88 | 2868 | -302 | 511 | -1840 | 2689 | 229 (289 / -560 / -2233) | pasl_10, 2873 (-837 / 323 / -2884) |
| prior_day | false_break_native | tick_2000 | {"M": 1, "k": 0.0} | sym8u / both | 120 / 120 | 88 | 2868 | -302 | 511 | -1840 | 2689 | 229 (289 / -560 / -2233) | mom_40, 2780 (-371 / -328 / -1402) |
| prior_day | reject | cusum_28 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 78 | 1739 | 98 | -1696 | -2312 | 1518 | 712 (1003 / -804 / -1059) | renko_10, 2231 (-401 / -852 / 528) |
| prior_day | reject_native | drb_6000 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 244 | 2354 | 203 | -1048 | -421 | 3066 | 2354 (203 / -1048 / -421) | renko_28, 2665 (149 / 475 / -2001) |
| prior_day | retest | dol_350 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 88 | 2568 | -149 | -1124 | -2622 | 2472 | 195 (206 / -549 / -876) | swing_atr_0.25, 2704 (-415 / -138 / -1222) |
| prior_day | retest_native | tm120 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 87 | 2570 | 174 | -1356 | -2937 | 483 | 44 (1141 / -309 / -2095) | swing_atr_0.25, 2940 (75 / -924 / -980) |
| profile_nodes | break | dlt_100 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 137 | 2489 | -45 | -739 | -7388 | 1667 | 220 (-756 / -809 / -1543) | swing_atr_0.6, 2411 (-1188 / 1868 / -925) |
| profile_nodes | break_native | vsess_120 | {"n": 2, "k": 0.5} | sym15u / both | 120 / 120 | 150 | 2825 | -1310 | 1408 | -1251 | 1857 | 510 (-803 / -247 / -1506) | pnf_10, 2992 (-647 / 1127 / -2618) |
| profile_nodes | false_break | tib_25000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 113 | 1444 | -1783 | 1091 | -2780 | 297 | 155 (-729 / 745 / -1809) | renko_10, 2054 (-1160 / -714 / -3668) |
| profile_nodes | false_break_native | vol_1700 | {"M": 1, "k": 0.5} | sym15u / both | 120 / 120 | 104 | 1708 | -1423 | -739 | -500 | 2097 | 354 (-273 / 275 / -2957) | renko_14, 2340 (-341 / 580 / -1695) |
| profile_nodes | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym20u/10u / both | 120 / 78 | 202 | 2560 | -341 | -814 | -361 | 4081 | 546 (189 / 143 / -955) | renko_10, 2027 (626 / 221 / 1413) |
| profile_nodes | reject_native | vol_4000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 120 / 120 | 171 | 3528 | -578 | 149 | -1542 | 2655 | 2036 (-576 / 285 / -16) | urenko_80, 2697 (0 / 622 / 203) |
| profile_nodes | retest | vsess_80 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 124 | 2403 | 252 | 1644 | -3530 | 1516 | -152 (-547 / 191 / -1705) | pnf_20, 2447 (-490 / 89 / -3842) |
| profile_nodes | retest_native | vol_2600 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 125 | 2379 | -428 | 1000 | -3336 | 1008 | 761 (43 / 125 / -1640) | pnf_20, 2802 (-508 / 830 / -3084) |
| profile_va | break | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 93 | 2285 | -957 | 2055 | -845 | 2570 | 833 (-36 / 776 / 49) | dchg_14, 2027 (107 / 301 / -1242) |
| profile_va | break_native | tick_5000 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 107 | 2219 | -494 | 117 | -111 | 3321 | 651 (254 / -169 / 260) | dchg_14, 2027 (107 / 301 / -1242) |
| profile_va | false_break | tick_5000 | {"M": 1, "k": 0.0} | sym8u / both | 120 / 120 | 94 | 1901 | -1353 | 1885 | -208 | 2123 | 731 (-400 / 534 / 243) | lbrk_3_40, 1601 (-1097 / 1179 / -1955) |
| profile_va | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 113 | 1975 | -1229 | 386 | -282 | 2315 | 1447 (-695 / -495 / -493) | renko_20, 1619 (-57 / -485 / -222) |
| profile_va | reject | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 88 / 88 | 184 | 3015 | -84 | 570 | -1275 | 3231 | 924 (1217 / -629 / 578) | dchg_28, 1815 (264 / -987 / 45) |
| profile_va | reject_native | drb_240 | {"tol": 1.0, "conf": "body"} | sym15u / both | 88 / 88 | 184 | 3050 | -470 | 1055 | -505 | 3721 | 1121 (749 / -872 / 2397) | urenko_56, 2239 (805 / 1816 / -229) |
| profile_va | retest | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 116 / 116 | 138 | 2551 | 282 | 812 | -308 | 1772 | 1421 (844 / 1912 / 1146) | dchg_10, 2015 (-962 / 832 / -2293) |
| profile_va | retest_native | cusum_10 | {"M": 3, "tol": 0.0} | sym15u / both | 116 / 116 | 138 | 2551 | 282 | 812 | -308 | 1772 | 1421 (844 / 1912 / 1146) | dchg_10, 2015 (-962 / 832 / -2293) |
| round | break | vsess_600 | {"n": 2, "k": 0.25} | asym20u/10u / both | 120 / 120 | 355 | 4389 | 347 | 1851 | -354 | 3926 | 1165 (313 / -13 / -2164) | urenko_20, 4837 (-1805 / 1243 / 3655) |
| round | break_native | dib_3500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 330 | 3809 | -1044 | 1989 | -51 | 2946 | -392 (-1127 / 562 / 1542) | mrenko_20, 3869 (-1678 / -471 / -86) |
| round | false_break | vol_750 | {"M": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 940 | 4099 | -2068 | 178 | -2932 | 4587 | 4099 (-2068 / 178 / -2932) | renko_14, 4685 (-629 / -2293 / -206) |
| round | false_break_native | tick_800 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 942 | 3478 | -2371 | 3492 | -70 | 1454 | 3478 (-2371 / 3492 / -70) | urenko_20, 4358 (-1829 / -1460 / 284) |
| round | reject | tick_300 | {"tol": 1.0, "conf": "body"} | sym8u / both | 112 / 112 | 424 | 4545 | -732 | -3108 | -1559 | 3759 | 1981 (407 / -1235 / -1215) | swing_atr_0.25, 4084 (-460 / -3206 / 2375) |
| round | reject_native | dib_10000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 313 | 4704 | -419 | 268 | -1458 | 3186 | -434 (-10 / 929 / -1470) | swing_atr_0.15, 4679 (1148 / -1566 / 745) |
| round | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 314 | 3757 | -127 | -303 | -1960 | 2375 | 1543 (290 / 950 / 828) | renko_14, 4728 (-399 / 513 / -1661) |
| round | retest_native | vol_2600 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 310 | 4143 | -2272 | 319 | 2108 | 4401 | -1750 (-1234 / -2327 / -408) | renko_14, 4722 (-107 / 506 / 309) |
| session_hl | break | time_m_7 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 171 | 3430 | -820 | 2114 | -94 | 2764 | -87 (-494 / 1628 / -471) | urenko_40, 2977 (-942 / 1915 / 2268) |
| session_hl | break_native | cusum_80 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 176 | 3625 | -2152 | 404 | 326 | 3669 | 335 (-1603 / 511 / -2448) | pasl_28, 2891 (-710 / -901 / -459) |
| session_hl | false_break | time_m_20 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 142 | 2762 | -1614 | -234 | 48 | 2023 | -411 (-301 / 892 / 95) | renko_14, 2956 (1816 / 1583 / -123) |
| session_hl | false_break_native | vol_1100 | {"M": 1, "k": 0.5} | asym10u/20u / both | 120 / 120 | 173 | 3424 | -20 | -574 | 863 | 2619 | -551 (-394 / -593 / 974) | dchg_40, 3061 (-469 / -1258 / -1446) |
| session_hl | reject | tm180 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 94 | 3102 | -1056 | 1294 | 418 | 2908 | 894 (105 / 34 / -465) | dchg_28, 2145 (117 / 56 / 446) |
| session_hl | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 226 | 4081 | -1531 | 1331 | -428 | 4336 | 2759 (-1651 / -318 / -1146) | mom_80, 2925 (-1067 / 962 / 965) |
| session_hl | retest | vol_350 | {"M": 3, "tol": 0.5} | sym30u / short | 120 / 120 | 95 | 3205 | -819 | -845 | -75 | 4545 | 451 (-272 / 912 / -421) | pnf_14, 2671 (-358 / -1031 / 1147) |
| session_hl | retest_native | vol_6000 | {"M": 10, "tol": 0.5} | sym8u / both | 120 / 120 | 198 | 5238 | -2267 | 2114 | 2158 | 4134 | -939 (-1601 / 1247 / 290) | renko_10, 2985 (-972 / 416 / 1083) |
| trendline | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 229 | 2153 | 870 | 1223 | 5536 | 3245 | 1217 (1296 / 480 / 1727) | lbrk_3_10, 2404 (-1368 / -1341 / -1311) |
| trendline | break_native | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 238 | 2318 | 1154 | 1901 | 653 | 3119 | 395 (729 / 1636 / -5) | kagi_14, 3812 (1332 / 2406 / 3337) |
| trendline | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / short | 120 / 120 | 107 | 1157 | -683 | -1747 | 683 | 1917 | 667 (-425 / -1126 / 379) | kagi_40, 3067 (348 / -1809 / 440) |
| trendline | false_break_native | dol_6000 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 295 | 2022 | -421 | -655 | -453 | 2571 | 2022 (-421 / -655 / -453) | kagi_40, 2770 (640 / -2164 / 534) |
| trendline | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 424 | 1733 | 1649 | 1994 | 303 | 2132 | 1733 (1649 / 1994 / 303) | urenko_28, 1991 (1175 / -2319 / 1129) |
| trendline | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 254 | 4010 | 1369 | 1988 | 1894 | 2118 | 897 (1227 / -352 / 839) | wrenko_14, 3408 (1778 / 3021 / 2069) |
| trendline | retest | vrb_700 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 378 | 1237 | 351 | 1039 | -532 | 1297 | 1237 (351 / 1039 / -532) | urenko_20, 3496 (392 / -2357 / 725) |
| trendline | retest_native | dol_500 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 106 | 1301 | -803 | -236 | 611 | 964 | 685 (-745 / -548 / -316) | urenko_20, 3496 (392 / -2357 / 725) |
| uw_dp | break | tick_3200 | {"n": 1, "k": 0.5} | sym8u / both | 120 / 120 | 60 | 1487 | 0 | 0 | 40 | 304 | 386 (0 / 0 / -564) | swing_atr_0.4, 2095 (0 / 0 / 399) |
| uw_dp | break_native | dol_6000 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 61 | 2272 | 0 | 0 | 421 | 2655 | 170 (0 / 0 / 79) | renko_40, 1811 (0 / 0 / 665) |
| uw_dp | false_break | vsess_50 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 56 | 1430 | 0 | 0 | 210 | 1085 | 37 (0 / 0 / -14) | pasl_10, 1240 (0 / 0 / 101) |
| uw_dp | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym15u / both | 120 / 120 | 61 | 1448 | 0 | 0 | 28 | 1366 | 493 (0 / 0 / 317) | pasl_10, 1386 (0 / 0 / 133) |
| uw_dp | reject | vol_2600 | {"tol": 1.0, "conf": "body"} | sym8u / both | 120 / 120 | 58 | 1359 | 0 | 0 | -37 | 922 | 732 (0 / 0 / 361) | lbrk_3_10, 1508 (0 / 0 / -241) |
| uw_dp | reject_native | vol_6000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 120 / 120 | 92 | 2286 | 0 | 0 | -217 | 1948 | 993 (0 / 0 / -163) | lbrk_3_10, 1790 (0 / 0 / -82) |
| uw_dp | retest | vsess_120 | {"M": 6, "tol": 0.5} | sym8u / both | 120 / 120 | 53 | 1639 | 0 | 0 | -212 | 1040 | 825 (0 / 0 / 50) | urenko_10, 1926 (0 / 0 / 295) |
| uw_dp | retest_native | dib_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 52 | 1476 | 0 | 0 | 495 | 1054 | -603 (0 / 0 / 52) | swing_atr_0.25, 2346 (0 / 0 / -187) |
| uw_ndx | break | rng_40 | {"n": 3, "k": 0.25} | sym8u / both | 120 / 120 | 95 | 2347 | 0 | -1001 | -2044 | 1016 | -375 (0 / -440 / -359) | renko_10, 1795 (0 / -252 / 1611) |
| uw_ndx | break_native | tick_300 | {"n": 3, "k": 0.5} | asym20u/10u / both | 120 / 120 | 102 | 2167 | 0 | -30 | -1920 | 1473 | -585 (0 / 273 / 239) | renko_10, 1791 (0 / 212 / 1169) |
| uw_ndx | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 68 | 1566 | 0 | -844 | -617 | 1700 | -317 (0 / 95 / -209) | renko_10, 1789 (0 / -138 / 1771) |
| uw_ndx | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 68 | 1566 | 0 | -844 | -617 | 1700 | -317 (0 / 95 / -209) | renko_10, 1695 (0 / -451 / 1017) |
| uw_ndx | reject | vol_750 | {"tol": 1.0, "conf": "close"} | sym8u / both | 120 / 120 | 101 | 1925 | 0 | -40 | -1237 | 2405 | -244 (0 / 220 / 716) | renko_10, 1537 (0 / 552 / 282) |
| uw_ndx | reject_native | rng_20 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 120 / 120 | 109 | 1815 | 0 | 716 | 1230 | 815 | -850 (0 / 438 / 130) | swing_atr_0.25, 1867 (0 / -44 / -84) |
| uw_ndx | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 89 | 1835 | 0 | -348 | -933 | 690 | -135 (0 / -458 / 654) | swing_atr_0.15, 2055 (0 / 271 / -781) |
| uw_ndx | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 89 | 1835 | 0 | -348 | -933 | 690 | -135 (0 / -458 / 654) | urenko_10, 2464 (0 / -631 / 475) |
| uw_qqq | break | rng_20 | {"n": 2, "k": 0.5} | sym15u / both | 120 / 120 | 107 | 2086 | 0 | 199 | -1304 | 2295 | 1024 (0 / 468 / 91) | renko_10, 1644 (0 / -302 / -257) |
| uw_qqq | break_native | rng_20 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 107 | 1587 | 0 | 166 | -667 | 1796 | 242 (0 / 540 / 208) | renko_10, 1644 (0 / -302 / -257) |
| uw_qqq | false_break | rng_10 | {"M": 1, "k": 0.5} | sym15u / both | 116 / 116 | 129 | 1746 | 0 | 169 | -358 | 956 | 704 (0 / -392 / 178) | renko_10, 1386 (0 / -207 / -2830) |
| uw_qqq | false_break_native | vsess_300 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 103 | 2069 | 0 | 764 | -695 | 1273 | 153 (0 / -35 / 49) | renko_10, 1343 (0 / 501 / -383) |
| uw_qqq | reject | vol_750 | {"tol": 0.5, "conf": "close"} | plain60/60 / both | 60 / 60 | 239 | 1562 | 0 | 34 | -577 | 1228 | 1562 (0 / 34 / -577) | mom_20, 1323 (0 / -231 / -1028) |
| uw_qqq | reject_native | time_m_10 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 107 | 1670 | 0 | 90 | -1214 | 721 | -622 (0 / 328 / -2161) | dchg_112, 2076 (0 / 175 / -871) |
| uw_qqq | retest | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 93 | 1917 | 0 | 437 | -582 | 1450 | 1306 (0 / -213 / 700) | pasl_10, 1717 (0 / -204 / -1665) |
| uw_qqq | retest_native | vsess_450 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 93 | 1917 | 0 | 437 | -582 | 1450 | 1306 (0 / -213 / 700) | dchg_20, 1938 (0 / 452 / -985) |
| vwap | break | cusum_10 | {"n": 2, "k": 0.0} | sym30u / both | 120 / 120 | 172 | 3562 | -932 | -281 | -154 | 2583 | 2624 (1377 / -204 / 1261) | renko_40, 3681 (-1617 / 765 / 724) |
| vwap | break_native | time_m_1 | {"n": 1, "k": 0.25} | sym8u / both | 116 / 116 | 178 | 3781 | -1232 | 727 | 3089 | 3780 | 1765 (-97 / -432 / 2392) | mom_40, 3296 (-928 / 1205 / 276) |
| vwap | false_break | dlt_45 | {"M": 1, "k": 0.5} | asym10u/20u / both | 111 / 120 | 197 | 3017 | -1532 | -1590 | -11 | 392 | 2137 (-297 / -2993 / 1083) | mom_40, 3221 (-789 / 1199 / 397) |
| vwap | false_break_native | cdr_100 | {"M": 1, "k": 0.5} | asym15u/30u / both | 120 / 120 | 148 | 4046 | -392 | -617 | -202 | 3159 | 1544 (-1442 / -1340 / -657) | mom_40, 3283 (-1074 / 517 / -263) |
| vwap | reject | dlt_30 | {"tol": 0.5, "conf": "body"} | sym15u / both | 109 / 109 | 282 | 2175 | 137 | 797 | 2776 | 2233 | -175 (-130 / 2256 / 3258) | mrenko_20, 2424 (-43 / 12 / 1717) |
| vwap | reject_native | tib_240 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 406 | 2038 | 4 | 2182 | -463 | 1587 | 2038 (4 / 2182 / -463) | lbrk_3_20, 2247 (589 / -748 / -179) |
| vwap | retest | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 167 | 4103 | 315 | 215 | 2521 | 4281 | -142 (236 / -876 / 1118) | swing_atr_0.1, 2874 (-206 / 128 / -1868) |
| vwap | retest_native | cusum_14 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 171 | 4078 | 605 | -156 | 1901 | 3767 | 241 (511 / -821 / 599) | dchg_14, 3199 (-828 / 2947 / -381) |
| vwap_bands | break | tm1200 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 205 | 3749 | -2237 | -1511 | -430 | 2231 | 515 (-681 / -467 / -483) | mom_14, 4022 (-815 / -2816 / 1718) |
| vwap_bands | break_native | cusum_56 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 242 | 3923 | -2077 | -681 | 2975 | 4369 | -666 (-1051 / -1560 / -1739) | renko_40, 3501 (-759 / -685 / 1823) |
| vwap_bands | false_break | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 120 / 120 | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 848 (-1192 / 1667 / -2870) | dchg_14, 3021 (-753 / -304 / -832) |
| vwap_bands | false_break_native | tick_800 | {"M": 1, "k": 0.0} | asym20u/10u / both | 120 / 120 | 246 | 3540 | -2203 | -1122 | 548 | 5855 | 848 (-1192 / 1667 / -2870) | dchg_14, 3246 (-968 / -155 / -1524) |
| vwap_bands | reject | time_m_1 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 261 | 3187 | -333 | 734 | 1706 | 3911 | -2485 (-331 / 1749 / 1407) | wrenko_14, 3357 (-1402 / -865 / 800) |
| vwap_bands | reject_native | tm1200 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 232 | 4941 | -869 | 1336 | -856 | 4552 | 660 (141 / -119 / 89) | swing_pct_12, 4578 (858 / 3358 / -669) |
| vwap_bands | retest | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 238 | 4091 | -2704 | -152 | -2144 | 3461 | -669 (-1804 / 967 / -3009) | pnf_5, 2828 (-2562 / -1065 / 389) |
| vwap_bands | retest_native | tm120 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 255 | 3708 | -2141 | 140 | 737 | 4693 | -801 (-488 / 565 / -3141) | swing_atr_0.6, 4137 (353 / -1853 / 636) |
| week_month | break | tib_25000 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 46 | 1774 | -72 | -295 | -513 | 1502 | 1011 (-310 / 683 / -206) | swing_pct_8, 1996 (-302 / -1266 / -107) |
| week_month | break_native | vol_4000 | {"n": 3, "k": 0.25} | sym8u / both | 120 / 120 | 51 | 1935 | -323 | -717 | -1028 | 2200 | 872 (-705 / 732 / -51) | swing_pct_8, 1868 (-333 / -1138 / 420) |
| week_month | false_break | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 33 | 1414 | 387 | 43 | -551 | 1838 | 331 (-19 / 866 / -201) | renko_20, 894 (253 / 480 / 955) |
| week_month | false_break_native | time_m_20 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 33 | 1414 | 387 | 43 | -551 | 1838 | 331 (-19 / 866 / -201) | pasl_40, 1289 (-307 / -629 / 75) |
| week_month | reject | time_m_2 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 38 | 1814 | -158 | -245 | 711 | 1727 | -8 (7 / 893 / 341) | frenko_40, 1114 (-638 / 267 / 14) |
| week_month | reject_native | tick_8000 | {"tol": 1.0, "conf": "body"} | sym8u / both | 120 / 120 | 72 | 1892 | -134 | -795 | -399 | 2132 | 979 (-355 / 320 / -103) | mom_56, 1508 (-245 / -1039 / 1483) |
| week_month | retest | dib_3500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 43 | 1765 | 87 | -540 | 870 | 1874 | 691 (10 / -202 / 176) | urenko_28, 1109 (-102 / 643 / 254) |
| week_month | retest_native | tick_5000 | {"M": 6, "tol": 0.5} | sym8u / both | 120 / 120 | 38 | 1687 | -215 | -1383 | 15 | 2423 | 843 (-541 / 53 / 286) | mom_56, 1498 (-615 / -1019 / 1241) |

### Asia - supply/demand modules by definition (variant = entry type)
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| sd5 | reject | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 60 / 60 | 31 | 195 | -34 | -11 | -200 | 446 | 195 (-34 / -11 / -200) | no reversal row has trades |
| sd5 | reject_native | dol_350 | {"F": 2, "D": 15, "tol": 0.0} | plain60/60 / both | 60 / 60 | 31 | 195 | -34 | -11 | -200 | 446 | 195 (-34 / -11 / -200) | no reversal row has trades |
| sdx15 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 61 | 448 | -231 | 115 | 749 | 790 | 414 (-157 / -300 / 297) | urenko_56, 1077 (-200 / -153 / 1318) |
| sdx15 | lim_mid | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 252 | 2124 | 13 | 1265 | 158 | -185 | 804 (-258 / 574 / 682) | wrenko_20, 3630 (-249 / -670 / -1170) |
| sdx15 | lim_prox | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 318 | 4155 | 759 | 194 | -1585 | 2577 | -1262 (538 / 128 / -2512) | urenko_56, 3613 (443 / 1635 / -503) |
| sdx15 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 143 | 1639 | -197 | 375 | -1227 | 1202 | 539 (-377 / 62 / 6) | urenko_20, 2164 (235 / -369 / -1160) |
| sdx15 | rej_flow | dol_500 | {"d": "A", "F": 0} | sym15u / both | 120 / 120 | 53 | 1065 | -42 | -617 | -253 | 1086 | 424 (-53 / -286 / -220) | wrenko_20, 2275 (39 / -418 / -673) |
| sdx15 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 170 | 2342 | -359 | -990 | -1569 | 2705 | 263 (-339 / -309 / -1025) | pnf_10, 2499 (143 / -843 / -1768) |
| sdx15 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 195 | 2091 | -651 | -27 | -1140 | 2775 | 1192 (-749 / -460 / -158) | pnf_10, 2499 (143 / -843 / -1768) |
| sdx3 | break | vrb_700 | {"d": "A", "F": 9, "n": 1} | plain60/60 / both | 60 / 60 | 421 | 2280 | -55 | 514 | 2224 | 3079 | 2280 (-55 / 514 / 2224) | wrenko_20, 2989 (-298 / 492 / 507) |
| sdx3 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 357 | 2213 | 12 | 390 | -1510 | -175 | -193 (-357 / -878 / -7) | lbrk_3_10, 3840 (-653 / -1268 / -1861) |
| sdx3 | lim_prox | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 353 | 2585 | -269 | 1326 | 207 | 526 | -213 (-202 / 165 / 200) | kagi_10, 6224 (-119 / -224 / -2213) |
| sdx3 | rej | dol_500 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / short | 120 / 120 | 147 | 2159 | -420 | -1303 | -1665 | 3069 | 94 (-398 / -1105 / -1108) | kagi_10, 3708 (-457 / -454 / -1839) |
| sdx3 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 120 / 120 | 117 | 2069 | -220 | -709 | -1314 | 3044 | -57 (-59 / -322 / -1599) | wrenko_20, 1286 (-498 / 192 / -724) |
| sdx3 | rej_native | dol_500 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 315 | 2066 | -528 | -1319 | -3774 | 2543 | -1207 (-583 / -842 / -2381) | urenko_10, 4669 (123 / 34 / -3034) |
| sdx3 | rej_zone | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 203 | 1722 | 296 | -285 | 635 | 1498 | 1188 (212 / -531 / 1552) | urenko_10, 4669 (123 / 34 / -3034) |
| sdx3 | retest | dol_6000 | {"d": "A", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 151 | 1308 | 81 | 126 | 831 | 1812 | 531 (41 / -80 / 801) | lbrk_3_20, 2387 (-339 / -259 / 1887) |
| sdx30 | break | dol_6000 | {"d": "A", "F": 9, "n": 1} | plain60/60 / both | 60 / 60 | 35 | -3 | -74 | 103 | 762 | -47 | -3 (-74 / 103 / 762) | kagi_56, 796 (-102 / 249 / 541) |
| sdx30 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 192 | 1242 | -471 | -520 | -3170 | 155 | 161 (-574 / 304 / -2574) | wrenko_14, 3133 (-150 / -817 / -949) |
| sdx30 | lim_prox | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / short | 60 / 60 | 257 | 1475 | 51 | -1229 | -253 | 1375 | 1475 (51 / -1229 / -253) | urenko_20, 3270 (-189 / -1338 / -13) |
| sdx30 | rej | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 159 | 1658 | 62 | -1293 | -821 | 349 | 113 (27 / -1018 / -591) | wrenko_10, 1478 (-177 / -1037 / -308) |
| sdx30 | rej_flow | dol_350 | {"d": "E", "F": 9} | sym15u / short | 120 / 120 | 44 | 1278 | -32 | -42 | -652 | 899 | 315 (-10 / -69 / -1144) | wrenko_10, 980 (-54 / -29 / -875) |
| sdx30 | rej_native | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 186 | 1569 | 172 | -1180 | -1517 | 785 | -254 (119 / -1095 / -946) | pnf_28, 2502 (8 / 245 / -348) |
| sdx30 | rej_zone | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 186 | 1569 | 172 | -1180 | -1517 | 785 | -254 (119 / -1095 / -946) | pnf_28, 2502 (8 / 245 / -348) |
| sdx5 | break | vrb_700 | {"d": "B", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 111 | 1810 | -443 | -357 | 1017 | 857 | 841 (-456 / -222 / 447) | urenko_56, 2472 (-146 / -590 / 1239) |
| sdx5 | lim_mid | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 365 | 3515 | -611 | 1076 | -2140 | 2585 | 1535 (-502 / -123 / -1100) | lbrk_3_10, 4411 (-88 / -1705 / -1193) |
| sdx5 | lim_prox | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 555 | 2485 | -158 | 1862 | 2117 | 1843 | 2485 (-158 / 1862 / 2117) | kagi_10, 5056 (283 / 711 / -1448) |
| sdx5 | rej | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 258 | 5300 | -710 | -111 | -394 | 5406 | 1890 (-235 / 18 / -58) | kagi_10, 4568 (-952 / -1164 / -3346) |
| sdx5 | rej_flow | dol_500 | {"d": "E", "F": 9} | sym15u / short | 120 / 120 | 107 | 1466 | -172 | -632 | 515 | 2171 | 288 (-143 / -581 / -59) | wrenko_10, 2801 (412 / -179 / -668) |
| sdx5 | rej_native | vrb_700 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 284 | 4619 | -598 | -24 | -1073 | 5324 | -154 (-87 / 125 / -560) | kagi_28, 4053 (-521 / -922 / -442) |
| sdx5 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 325 | 2785 | 101 | -573 | -1444 | 850 | -768 (396 / -368 / -1632) | mrenko_14, 3304 (-209 / -1861 / 763) |
| sdx5 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 59 | 986 | 98 | 94 | 141 | 1317 | 79 (67 / 22 / 293) | kagi_40, 1465 (-6 / -476 / -174) |
| sdx60 | lim_mid | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 70 | 668 | -209 | -461 | -1611 | 676 | 370 (-163 / -270 / -1288) | urenko_40, 1330 (181 / -523 / -342) |
| sdx60 | lim_prox | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 90 | 523 | -210 | -732 | -539 | 957 | -239 (-186 / -808 / 418) | urenko_28, 1502 (-62 / -1032 / -516) |
| sdx60 | rej | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 46 | 2001 | -43 | -297 | -277 | 2024 | 640 (-27 / -344 / -254) | kagi_10, 1580 (-20 / -174 / -290) |
| sdx60 | rej_flow | vrb_700 | {"d": "E", "F": 9} | sym15u / short | 120 / 120 | 30 | 913 | 12 | -370 | -367 | 777 | 521 (-2 / -117 / -258) | wrenko_10, 352 (-29 / 149 / -99) |
| sdx60 | rej_native | dol_350 | {"d": "A", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 55 | 1865 | -30 | -186 | -356 | 1683 | 530 (-18 / -304 / -329) | wrenko_14, 2048 (-3 / -244 / -270) |
| sdx60 | rej_zone | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / short | 120 / 120 | 62 | 1004 | -203 | -171 | -112 | 822 | -129 (-97 / -66 / -20) | wrenko_10, 1710 (25 / -264 / -895) |
| sdx_renko28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | sym15u / both | 120 / 120 | 182 | 3218 | 348 | 613 | 1501 | 3608 | 2197 (181 / 788 / 740) | kagi_10, 2989 (-99 / -30 / 159) |
| sdx_renko28 | lim_mid | dol_6000 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 505 | 1531 | -22 | 1122 | 1268 | 1692 | 1531 (-22 / 1122 / 1268) | kagi_28, 3926 (-225 / -191 / -3870) |
| sdx_renko28 | lim_prox | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 337 | 1882 | -89 | 1513 | -2130 | -30 | -3713 (-260 / 1089 / -1983) | pnf_7, 3491 (102 / -741 / -4298) |
| sdx_renko28 | rej | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 289 | 2322 | -347 | -2305 | -1815 | 504 | -352 (-325 / -2542 / -2300) | wrenko_14, 2070 (-289 / -772 / -816) |
| sdx_renko28 | rej_flow | dol_500 | {"d": "E", "F": 0} | sym15u / both | 120 / 120 | 129 | 2136 | -201 | -119 | -1662 | 3211 | 1303 (-127 / -150 / -1018) | wrenko_10, 2509 (-260 / -487 / -1295) |
| sdx_renko28 | rej_native | vrb_700 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 311 | 2346 | -542 | -2719 | -1881 | 69 | -1381 (-442 / -3696 / -2745) | kagi_10, 3009 (-86 / -3096 / -4876) |
| sdx_renko28 | rej_zone | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 311 | 2346 | -542 | -2719 | -1881 | 69 | -1381 (-442 / -3696 / -2745) | kagi_10, 3009 (-86 / -3096 / -4876) |
| sdx_renko28 | retest | dol_6000 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 98 | 1122 | 294 | 1178 | -327 | 2170 | 709 (232 / 836 / -568) | kagi_56, 2189 (230 / -226 / -1251) |
| sdx_rng28 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 60 / 60 | 725 | 4190 | -141 | 1676 | 779 | 3235 | 4190 (-141 / 1676 / 779) | mrenko_20, 5407 (129 / 1213 / -529) |
| sdx_rng28 | lim_mid | dol_350 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 363 | 2474 | -659 | 794 | 276 | 3658 | -2341 (-919 / 342 / 1397) | lbrk_3_20, 3033 (349 / -535 / 1306) |
| sdx_rng28 | lim_prox | vrb_700 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 876 | 1280 | 40 | -656 | -2323 | 977 | 1280 (40 / -656 / -2323) | lbrk_3_20, 2705 (51 / -193 / -1074) |
| sdx_rng28 | rej | dol_6000 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 214 | 1907 | 205 | 847 | -2396 | 1762 | -295 (245 / 724 / -1462) | frenko_40, 4551 (663 / 859 / -858) |
| sdx_rng28 | rej_flow | dol_6000 | {"d": "E", "F": 0} | sym15u / both | 120 / 120 | 165 | 1758 | -160 | -423 | -740 | 2040 | 926 (-186 / -309 / -530) | wrenko_14, 1284 (-125 / -911 / -891) |
| sdx_rng28 | rej_native | dol_500 | {"d": "E", "F": 9, "tol": 0.5} | sym15u / both | 120 / 120 | 345 | 2502 | 360 | 1558 | -1448 | 196 | 1699 (458 / 1443 / -4261) | wrenko_20, 2929 (-775 / -407 / -1591) |
| sdx_rng28 | rej_zone | dol_500 | {"d": "E", "F": 9, "tgt": "r2"} | sym15u / both | 120 / 120 | 345 | 2502 | 360 | 1558 | -1448 | 196 | 1699 (458 / 1443 / -4261) | urenko_20, 2693 (-208 / -802 / -2507) |
| sdx_rng28 | retest | vrb_700 | {"d": "E", "M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 447 | 3522 | -103 | 677 | -611 | 2695 | 3522 (-103 / 677 / -611) | kagi_28, 2488 (202 / 1443 / 17) |
| sdx_vol1100 | break | vrb_700 | {"d": "E", "F": 9, "n": 1} | plain60/60 / both | 60 / 60 | 392 | 3031 | 130 | 198 | 714 | 2880 | 3031 (130 / 198 / 714) | kagi_14, 3019 (-303 / -758 / 428) |
| sdx_vol1100 | lim_mid | dol_350 | {"d": "E", "F": 0, "tgt": "opp"} | plain60/60 / both | 60 / 60 | 849 | 2256 | 548 | -787 | -2088 | 2083 | 2256 (548 / -787 / -2088) | wrenko_14, 3043 (-308 / 140 / -2784) |
| sdx_vol1100 | lim_prox | vrb_700 | {"d": "E", "F": 9, "tgt": "r2"} | plain60/60 / both | 60 / 60 | 881 | 2053 | 243 | 1222 | -1815 | 1673 | 2053 (243 / 1222 / -1815) | kagi_10, 4466 (-175 / -58 / -998) |
| sdx_vol1100 | rej | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 281 | 4086 | 117 | -233 | -2354 | 3347 | -335 (-13 / 30 / -342) | kagi_10, 1728 (-252 / -1315 / -1161) |
| sdx_vol1100 | rej_flow | dol_6000 | {"d": "E", "F": 9} | plain60/60 / both | 60 / 60 | 204 | 2004 | -631 | 200 | -652 | 1775 | 2004 (-631 / 200 / -652) | wrenko_14, 1360 (-676 / -750 / -806) |
| sdx_vol1100 | rej_native | dol_500 | {"d": "E", "F": 0, "tol": 0.5} | sym15u / both | 120 / 120 | 315 | 4153 | -19 | -209 | -2233 | 3638 | 200 (-37 / 219 / -1523) | kagi_10, 3389 (-344 / -1220 / -2227) |
| sdx_vol1100 | rej_zone | dol_500 | {"d": "E", "F": 0, "tgt": "opp"} | sym15u / both | 120 / 120 | 254 | 1320 | -390 | 331 | -2491 | -122 | -904 (-286 / 160 / -1529) | pnf_14, 3356 (427 / -643 / -1132) |
| sdx_vol1100 | retest | dol_350 | {"d": "E", "M": 6, "tol": 0.5} | sym15u / long | 120 / 120 | 57 | 1250 | 94 | 309 | 1050 | 1214 | 758 (69 / 318 / 876) | urenko_40, 2414 (61 / -321 / 464) |
| zones | break | rng_40 | {"n": 1, "k": 0.5} | sym8u / both | 120 / 120 | 199 | 3211 | 33 | 78 | 580 | 2604 | 835 (35 / -424 / 231) | renko_20, 2493 (-117 / -44 / -1238) |
| zones | break_native | rng_56 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 198 | 3109 | -32 | 151 | -834 | 3456 | 1237 (-26 / -158 / 805) | renko_10, 3602 (-167 / -1067 / -65) |
| zones | false_break | vsess_120 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 120 | 227 | 2849 | -378 | 266 | -1045 | 1446 | 1925 (-227 / 794 / -455) | renko_14, 3063 (-198 / 1130 / -84) |
| zones | false_break_native | rng_20 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 120 | 177 | 2863 | -154 | 660 | -299 | 2423 | 2081 (-306 / 420 / -1089) | renko_20, 2530 (-415 / 296 / -665) |
| zones | reject | tib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 86 / 86 | 333 | 3009 | 617 | -1519 | -284 | 3333 | 904 (443 / -1298 / 170) | wrenko_10, 3254 (-73 / -1065 / -502) |
| zones | reject_native | tib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 86 / 86 | 329 | 2550 | 500 | -806 | -414 | 2561 | 616 (326 / -1204 / 137) | renko_10, 3157 (-1008 / -1664 / -1608) |
| zones | retest | rng_20 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 152 | 3234 | -701 | -310 | -373 | 2927 | 1471 (-798 / -102 / -257) | urenko_10, 2609 (131 / 97 / -411) |
| zones | retest_native | rng_28 | {"M": 6, "tol": 0.5} | sym8u / both | 120 / 120 | 161 | 2948 | -119 | -238 | 150 | 2390 | 1117 (-139 / -483 / 1303) | renko_14, 2622 (-234 / 231 / -728) |

### Asia - other level modules
| module | variant (entry type) | best NON-reversal bar | params | bracket / side | stop / target pts | trades L6M | L6M pts | 2023 | 2024 | 2025 | 2026 | plain 60/60: L6M (2023 / 24 / 25) | REVERSAL-bar best: row, L6M (2023 / 24 / 25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fib15 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 664 | 4358 | 1020 | 111 | 108 | 5473 | 4358 (1020 / 111 / 108) | lbrk_3_10, 3199 (-503 / 800 / 2149) |
| fib15 | break_native | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 706 | 2534 | 752 | 195 | 810 | 3054 | 2534 (752 / 195 / 810) | lbrk_3_10, 3199 (-503 / 800 / 2149) |
| fib15 | false_break | dol_500 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 719 | 3265 | -100 | -525 | 1345 | 2488 | 3265 (-100 / -525 / 1345) | urenko_14, 3531 (-251 / 204 / 302) |
| fib15 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 724 | 2793 | 10 | -642 | 1509 | 1799 | 2793 (10 / -642 / 1509) | urenko_80, 3386 (-101 / -338 / 505) |
| fib15 | pullback | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 217 | 1496 | -455 | -1176 | -1606 | 32 | -506 (-313 / -818 / -887) | frenko_28, 2905 (-586 / 78 / -1531) |
| fib15 | pullback_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 223 | 1514 | -394 | -1003 | -1442 | -141 | 856 (-382 / -872 / -570) | frenko_28, 2602 (-56 / 387 / -221) |
| fib15 | reject | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 641 | 1780 | -63 | -389 | -1282 | 3453 | 1780 (-63 / -389 / -1282) | urenko_10, 3114 (323 / -624 / 1153) |
| fib15 | reject_native | dol_350 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 646 | 1654 | -404 | -1032 | 705 | 3215 | 1654 (-404 / -1032 / 705) | urenko_10, 3684 (770 / -1991 / 1912) |
| fib15 | retest | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 520 | 2385 | -510 | 483 | 220 | 3257 | 2385 (-510 / 483 / 220) | frenko_28, 3328 (623 / 999 / -465) |
| fib15 | retest_native | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 520 | 2385 | -510 | 483 | 220 | 3257 | 2385 (-510 / 483 / 220) | frenko_28, 3269 (420 / -791 / 495) |
| fib5 | break | vrb_700 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 344 | 2004 | -59 | 1255 | -546 | 2992 | -97 (-0 / 715 / -555) | frenko_40, 3710 (255 / 1241 / -1391) |
| fib5 | break_native | vrb_700 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 347 | 2324 | 260 | 1597 | -296 | 3047 | -1153 (-166 / 785 / 377) | urenko_80, 3121 (-59 / 232 / 1286) |
| fib5 | false_break | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 396 | 877 | -462 | -661 | -667 | 428 | 877 (-462 / -661 / -667) | pnf_14, 2831 (-211 / 899 / -3174) |
| fib5 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | plain60/60 / short | 60 / 60 | 394 | 1195 | -376 | -665 | -1006 | 854 | 1195 (-376 / -665 / -1006) | kagi_56, 3381 (57 / 598 / -2618) |
| fib5 | pullback | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 153 | 1705 | -705 | -2220 | 108 | 3172 | 1128 (-637 / -1647 / -184) | mrenko_20, 3450 (-194 / -957 / 412) |
| fib5 | pullback_native | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 153 | 1705 | -705 | -2220 | 108 | 3172 | 1128 (-637 / -1647 / -184) | kagi_28, 3577 (-99 / 252 / -1371) |
| fib5 | reject | vrb_700 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 778 | 2162 | -184 | -63 | 941 | 2515 | 2162 (-184 / -63 / 941) | urenko_40, 3634 (32 / -710 / -768) |
| fib5 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 894 | 1935 | -1118 | 154 | -704 | 3451 | 1935 (-1118 / 154 / -704) | pnf_10, 3481 (593 / -1004 / -1778) |
| fib5 | retest | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 338 | 2083 | -410 | 668 | -2513 | 2961 | 323 (-572 / -470 / -2972) | kagi_28, 5432 (117 / -762 / -4567) |
| fib5 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 138 | 1574 | -267 | 58 | -1567 | 2234 | 950 (-299 / -548 / -1645) | kagi_28, 5432 (117 / -762 / -4567) |
| fib60 | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 546 | 3316 | -354 | -596 | -431 | 3796 | 3316 (-354 / -596 / -431) | urenko_14, 4046 (-15 / -506 / 1369) |
| fib60 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 556 | 4408 | -100 | 188 | -541 | 3433 | 4408 (-100 / 188 / -541) | frenko_28, 3346 (-625 / -109 / -986) |
| fib60 | false_break | dol_500 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 559 | 1990 | 161 | -857 | -585 | 2631 | 1990 (161 / -857 / -585) | lbrk_3_40, 2589 (-24 / 1523 / -232) |
| fib60 | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 556 | 1419 | 170 | -503 | -1336 | 1695 | 1419 (170 / -503 / -1336) | lbrk_3_40, 2559 (-102 / 1257 / -523) |
| fib60 | pullback | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 78 | 1400 | 273 | -104 | -239 | 2025 | 727 (270 / 69 / -308) | urenko_10, 2500 (277 / -321 / -1857) |
| fib60 | pullback_native | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 98 | 1367 | 145 | -351 | -1248 | 1605 | 578 (274 / 117 / -212) | urenko_10, 2403 (331 / -240 / -1482) |
| fib60 | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 161 | 2645 | -40 | -503 | 537 | 2560 | 819 (-172 / 286 / 899) | kagi_10, 3600 (321 / -1524 / -787) |
| fib60 | reject_native | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 161 | 2645 | -40 | -503 | 537 | 2560 | 819 (-172 / 286 / 899) | urenko_28, 3269 (101 / -14 / 853) |
| fib60 | retest | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 471 | 1348 | 48 | -430 | 1118 | 1183 | 1348 (48 / -430 / 1118) | urenko_10, 2269 (379 / -1909 / -1529) |
| fib60 | retest_native | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 513 | 1807 | 98 | 214 | 137 | 2831 | 1807 (98 / 214 / 137) | urenko_10, 2705 (324 / -1493 / -867) |
| fibr_dev | break | dol_350 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 794 | 1200 | 194 | -791 | -3046 | 3223 | 1200 (194 / -791 / -3046) | pnf_14, 3094 (492 / 1108 / 1598) |
| fibr_dev | break_native | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / short | 60 / 60 | 413 | 1275 | 233 | -1659 | -1115 | 2026 | 1275 (233 / -1659 / -1115) | pnf_14, 3094 (515 / 1108 / 1598) |
| fibr_dev | false_break | vrb_700 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 342 | 1062 | 38 | 789 | 537 | 1853 | 436 (48 / 459 / -1595) | pnf_14, 3799 (772 / 931 / 1745) |
| fibr_dev | false_break_native | vrb_700 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 341 | 1495 | 269 | 731 | 423 | 2047 | -20 (300 / 572 / -1766) | pnf_14, 3556 (1165 / 401 / 1540) |
| fibr_dev | reject | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / short | 60 / 60 | 415 | 1665 | 231 | -2418 | -2161 | 2543 | 1665 (231 / -2418 / -2161) | frenko_40, 3144 (-189 / 873 / -2406) |
| fibr_dev | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / short | 60 / 60 | 394 | 1452 | 193 | -1466 | -1018 | 1403 | 1452 (193 / -1466 / -1018) | frenko_40, 4083 (-588 / 684 / -1434) |
| fibr_dev | retest | dol_350 | {"M": 10, "tol": 0.5} | plain60/60 / short | 60 / 60 | 357 | 2048 | -233 | -1156 | -2303 | 2490 | 2048 (-233 / -1156 / -2303) | urenko_14, 3210 (14 / -1791 / 2306) |
| fibr_dev | retest_native | dol_350 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 128 | 1739 | -139 | -1122 | -1673 | 1873 | 783 (-133 / -1145 / -1806) | urenko_14, 3210 (14 / -1791 / 2306) |
| fibr_ib | break | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 777 | 13 | 583 | 213 | 617 | 777 (13 / 583 / 213) | urenko_80, 973 (-5 / 119 / 967) |
| fibr_ib | break_native | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 777 | 13 | 583 | 213 | 617 | 777 (13 / 583 / 213) | urenko_80, 973 (-5 / 119 / 967) |
| fibr_ib | false_break | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 777 | 13 | 583 | 213 | 617 | 777 (13 / 583 / 213) | urenko_80, 987 (109 / 245 / 994) |
| fibr_ib | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 777 | 13 | 583 | 213 | 617 | 777 (13 / 583 / 213) | urenko_80, 973 (-5 / 218 / 954) |
| fibr_ib | reject | dol_6000 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 46 | 583 | -124 | -72 | 163 | 553 | 424 (-44 / 186 / -66) | pnf_28, 624 (386 / 146 / -104) |
| fibr_ib | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 67 | 746 | 217 | 496 | -491 | 704 | 618 (248 / 762 / -286) | pnf_28, 1206 (460 / -101 / 173) |
| fibr_ib | retest | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 45 | 950 | -154 | -86 | -373 | 1468 | 426 (-67 / -42 / -314) | urenko_80, 1139 (116 / -501 / 309) |
| fibr_ib | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 49 | 1035 | -57 | -384 | -713 | 1267 | 424 (20 / -195 / -571) | urenko_80, 1416 (2 / -1461 / -161) |
| fibr_on | break | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 1079 | 118 | 617 | 30 | 742 | 1079 (118 / 617 / 30) | wrenko_14, 1099 (45 / 789 / 149) |
| fibr_on | break_native | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 1079 | 118 | 617 | 30 | 742 | 1079 (118 / 617 / 30) | wrenko_14, 1099 (45 / 789 / 149) |
| fibr_on | false_break | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 1079 | 118 | 617 | 30 | 742 | 1079 (118 / 617 / 30) | wrenko_14, 1342 (57 / 761 / 588) |
| fibr_on | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 62 | 1079 | 118 | 617 | 30 | 742 | 1079 (118 / 617 / 30) | pnf_7, 1558 (176 / 575 / 928) |
| fibr_on | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 40 | 171 | 34 | -182 | -10 | 174 | -224 (-1 / -23 / 211) | kagi_112, 769 (6 / 260 / 62) |
| fibr_on | reject_native | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 40 | 171 | 34 | -182 | -10 | 174 | -224 (-1 / -23 / 211) | pnf_56, 1587 (-6 / 47 / -1673) |
| fibr_on | retest | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 39 | 1028 | 379 | 451 | -273 | 920 | 765 (354 / 378 / -37) | urenko_80, 1166 (-61 / -3 / 830) |
| fibr_on | retest_native | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 44 | 688 | 226 | 428 | -341 | 718 | 461 (201 / 325 / -102) | urenko_80, 1220 (-2 / 140 / 639) |
| fibr_or | break | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 1018 | 235 | 522 | -164 | 814 | 1018 (235 / 522 / -164) | urenko_80, 1194 (169 / -60 / 437) |
| fibr_or | break_native | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 1018 | 235 | 522 | -164 | 814 | 1018 (235 / 522 / -164) | urenko_80, 1194 (169 / -60 / 437) |
| fibr_or | false_break | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 1018 | 258 | 522 | -164 | 814 | 1018 (258 / 522 / -164) | urenko_80, 1075 (184 / 90 / 361) |
| fibr_or | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 65 | 1018 | 258 | 522 | -164 | 814 | 1018 (258 / 522 / -164) | urenko_80, 1075 (184 / 90 / 361) |
| fibr_or | reject | dol_500 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 33 | 489 | 144 | -523 | -654 | 44 | 45 (93 / -428 / -567) | pnf_40, 319 (180 / -2 / -170) |
| fibr_or | reject_native | vrb_40000 | {"tol": 1.0, "conf": "body"} | plain60/60 / short | 60 / 60 | 36 | 501 | 36 | 26 | -146 | 506 | 501 (36 / 26 / -146) | kagi_80, 808 (243 / -645 / -131) |
| fibr_or | retest | vrb_40000 | {"M": 10, "tol": 0.5} | plain60/60 / short | 60 / 60 | 37 | 690 | 19 | -52 | -9 | 869 | 690 (19 / -52 / -9) | urenko_80, 1143 (260 / -956 / -170) |
| fibr_or | retest_native | vrb_40000 | {"M": 10, "tol": 0.5} | plain60/60 / short | 60 / 60 | 37 | 581 | 19 | 17 | -77 | 760 | 581 (19 / 17 / -77) | urenko_80, 1342 (216 / -1025 / -198) |
| fibr_pd | break | dol_6000 | {"n": 3, "k": 0.5} | sym15u / short | 120 / 120 | 89 | 1850 | 270 | -8 | 467 | 2527 | 1701 (185 / 137 / 470) | kagi_10, 3124 (553 / 89 / 691) |
| fibr_pd | break_native | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 630 | 2165 | -103 | 1588 | -427 | 2239 | 2165 (-103 / 1588 / -427) | kagi_10, 3124 (553 / 89 / 691) |
| fibr_pd | false_break | dol_6000 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 436 | 1980 | -440 | 795 | 1346 | 1956 | 1980 (-440 / 795 / 1346) | kagi_10, 3579 (-1005 / -279 / 981) |
| fibr_pd | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 442 | 1752 | -480 | 793 | 1383 | 1789 | 1752 (-480 / 793 / 1383) | kagi_10, 3464 (-1047 / -220 / 995) |
| fibr_pd | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 135 | 1712 | -120 | -1420 | -455 | 1332 | 1621 (-40 / -726 / -599) | urenko_10, 2746 (-87 / -674 / -1595) |
| fibr_pd | reject_native | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 273 | 1884 | 97 | -1703 | -206 | 3908 | 402 (11 / -335 / -602) | urenko_10, 2899 (228 / -466 / 1300) |
| fibr_pd | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 60 | 1340 | 16 | -545 | 357 | 1825 | 550 (39 / 23 / 504) | kagi_28, 2661 (78 / 584 / 477) |
| fibr_pd | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / short | 120 / 120 | 60 | 1340 | 16 | -545 | 357 | 1825 | 550 (39 / 23 / 504) | kagi_28, 3100 (305 / 253 / 787) |
| piv_cama | break | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 697 | 3237 | 208 | 306 | -1672 | 2963 | 3237 (208 / 306 / -1672) | mrenko_20, 2847 (-237 / -199 / -769) |
| piv_cama | break_native | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 697 | 3237 | 208 | 306 | -1672 | 2963 | 3237 (208 / 306 / -1672) | pnf_10, 3386 (269 / 1492 / 959) |
| piv_cama | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 718 | 2761 | -500 | -98 | -1350 | 3065 | 2761 (-500 / -98 / -1350) | kagi_14, 2755 (-1113 / -1285 / 50) |
| piv_cama | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 718 | 2761 | -500 | -98 | -1350 | 3065 | 2761 (-500 / -98 / -1350) | kagi_14, 3200 (-1113 / -1440 / 84) |
| piv_cama | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 319 | 3165 | -462 | -874 | 1496 | 3297 | 3065 (-835 / -485 / 1325) | kagi_14, 3116 (-104 / -1966 / -1113) |
| piv_cama | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 344 | 3538 | -773 | -527 | -550 | 2854 | 1457 (-969 / -59 / 1038) | kagi_10, 3432 (-1039 / -1266 / 885) |
| piv_cama | retest | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 558 | 2113 | -244 | 387 | -22 | 2224 | 2113 (-244 / 387 / -22) | kagi_14, 2950 (-169 / -864 / 823) |
| piv_cama | retest_native | dol_350 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 558 | 2113 | -244 | 387 | -22 | 2224 | 2113 (-244 / 387 / -22) | pnf_5, 4190 (-481 / -909 / -37) |
| piv_floor | break | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 233 | 2914 | -212 | -232 | 2261 | 3511 | 455 (-427 / -13 / -20) | pnf_5, 3642 (216 / 77 / 945) |
| piv_floor | break_native | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 237 | 2024 | 222 | 946 | 2662 | 3800 | 1960 (-32 / 533 / 1768) | pnf_5, 3642 (216 / 77 / 945) |
| piv_floor | false_break | dol_350 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 502 | 1430 | -941 | -1648 | -325 | 3482 | 1430 (-941 / -1648 / -325) | kagi_10, 3654 (-727 / -863 / 251) |
| piv_floor | false_break_native | dol_350 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 502 | 1430 | -941 | -1648 | -325 | 3482 | 1430 (-941 / -1648 / -325) | kagi_10, 3592 (-577 / -783 / 419) |
| piv_floor | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 170 | 1120 | -396 | -306 | 201 | 553 | -269 (-316 / -337 / -512) | mrenko_10, 2195 (-719 / -1237 / -497) |
| piv_floor | reject_native | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 170 | 1120 | -396 | -306 | 201 | 553 | -269 (-316 / -337 / -512) | urenko_20, 2515 (703 / -945 / -1135) |
| piv_floor | retest | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 114 | 2135 | 63 | 578 | -449 | 3815 | 1180 (-44 / 369 / 29) | kagi_14, 3194 (-7 / 722 / -1698) |
| piv_floor | retest_native | dol_6000 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 114 | 2135 | 63 | 578 | -449 | 3815 | 1180 (-44 / 369 / 29) | mrenko_10, 2992 (134 / -1048 / 1326) |
| piv_wf | break | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 584 | 2182 | -723 | -256 | 505 | 2299 | 2182 (-723 / -256 / 505) | pnf_7, 2610 (-252 / -834 / 1910) |
| piv_wf | break_native | dol_350 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 273 | 2079 | -217 | 1120 | 2282 | 2352 | 1015 (-532 / 547 / 1608) | pnf_7, 2610 (-252 / -834 / 1910) |
| piv_wf | false_break | dol_6000 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 430 | 2083 | -705 | 242 | 1750 | 2389 | 2083 (-705 / 242 / 1750) | frenko_28, 2465 (-1481 / -1157 / 560) |
| piv_wf | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 295 | 2342 | -937 | -1501 | 271 | 3266 | 434 (-1041 / -1311 / -182) | wrenko_20, 2691 (-648 / -1103 / 567) |
| piv_wf | reject | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 278 | 2564 | -131 | -855 | 521 | 3098 | -327 (156 / -1546 / 39) | wrenko_14, 2409 (-138 / -114 / -2979) |
| piv_wf | reject_native | vrb_700 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 278 | 2564 | -131 | -855 | 521 | 3098 | -327 (156 / -1546 / 39) | kagi_10, 3050 (-355 / -1518 / -2651) |
| piv_wf | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 344 | 1917 | 105 | -1315 | -27 | 1775 | 1917 (105 / -1315 / -27) | kagi_10, 3002 (-306 / -16 / -2883) |
| piv_wf | retest_native | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 344 | 1917 | 105 | -1315 | -27 | 1775 | 1917 (105 / -1315 / -27) | mrenko_14, 4286 (-12 / 529 / -29) |
| swcluster | break | dol_500 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 54 | 655 | 192 | -634 | 282 | 1471 | 237 (127 / -487 / 139) | urenko_10, 1027 (-344 / -315 / -623) |
| swcluster | break_native | dol_500 | {"n": 3, "k": 0.5} | sym15u / both | 120 / 120 | 59 | 575 | 193 | -262 | 233 | 1225 | -572 (246 / -107 / -164) | urenko_10, 1024 (-227 / -349 / -670) |
| swcluster | false_break | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 61 | 545 | -117 | -169 | 1397 | 1679 | 377 (-69 / 261 / 411) | pnf_7, 1311 (-249 / -176 / 1393) |
| swcluster | false_break_native | dol_350 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 82 | 735 | -68 | 258 | 847 | 1109 | 735 (-68 / 258 / 847) | pnf_7, 1311 (-249 / -176 / 1393) |
| swcluster | reject | dol_6000 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 35 | 576 | -2 | 29 | -595 | 402 | -769 (-2 / -174 / -630) | lbrk_3_10, 591 (-154 / -551 / -336) |
| swcluster | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 34 | 654 | 57 | -580 | 147 | 916 | 74 (72 / -677 / -166) | urenko_112, 1097 (102 / -253 / -33) |
| swcluster | retest | dol_350 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 50 | 1005 | -370 | 289 | 169 | 1869 | 8 (-304 / 239 / -290) | wrenko_10, 972 (-130 / 69 / 114) |
| swcluster | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 50 | 939 | 1 | -497 | 339 | 1531 | 339 (-43 / -468 / -446) | kagi_20, 973 (-319 / 31 / 1182) |
| swsr15 | break | vrb_700 | {"n": 3, "k": 0.5} | plain60/60 / short | 60 / 60 | 299 | 2419 | 255 | -341 | -1079 | 2017 | 2419 (255 / -341 / -1079) | urenko_28, 2835 (-125 / 665 / 1504) |
| swsr15 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 639 | 2579 | 273 | 977 | -86 | 2926 | 2579 (273 / 977 / -86) | frenko_40, 2391 (-295 / 324 / -1522) |
| swsr15 | false_break | dol_500 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 129 | 1506 | 374 | -1395 | -98 | 1724 | 734 (302 / -1259 / -1471) | kagi_56, 2324 (-223 / -60 / -629) |
| swsr15 | false_break_native | dol_500 | {"M": 2, "k": 0.5} | sym15u / short | 120 / 120 | 131 | 1725 | 454 | -1379 | -623 | 1955 | 603 (364 / -1237 / -1756) | kagi_20, 2961 (743 / -10 / -136) |
| swsr15 | reject | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 274 | 1892 | 157 | 467 | 495 | 2489 | -571 (57 / 283 / -1225) | mrenko_14, 2218 (174 / -27 / -468) |
| swsr15 | reject_native | dol_500 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 754 | 3070 | 146 | 508 | -2024 | 2007 | 3070 (146 / 508 / -2024) | urenko_40, 2650 (-1013 / 464 / -381) |
| swsr15 | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 124 | 1482 | 245 | -410 | -333 | 1854 | 669 (152 / -1112 / -1109) | wrenko_10, 2630 (-1036 / -575 / -2284) |
| swsr15 | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 336 | 1427 | -257 | 1129 | 490 | 1077 | 1427 (-257 / 1129 / 490) | wrenko_10, 2630 (-1036 / -575 / -2284) |
| swsr5 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 371 | 3336 | 971 | 788 | -175 | 3367 | 1776 (700 / 945 / -1144) | kagi_56, 3427 (-11 / 1352 / -1241) |
| swsr5 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 371 | 3336 | 1004 | 788 | -175 | 3367 | 1776 (733 / 945 / -1144) | wrenko_20, 3514 (80 / 1736 / 1316) |
| swsr5 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 369 | 2780 | 622 | 976 | 2 | 1580 | -347 (453 / 366 / -2374) | kagi_56, 2683 (222 / 1358 / 730) |
| swsr5 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 369 | 2780 | 585 | 976 | 2 | 1580 | -347 (416 / 366 / -2374) | urenko_56, 3016 (270 / 578 / -45) |
| swsr5 | reject | dol_6000 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 363 | 1847 | -71 | 543 | 1275 | 2955 | 1847 (-71 / 543 / 1275) | pnf_5, 4159 (82 / 315 / 42) |
| swsr5 | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 483 | 2078 | 76 | 472 | 591 | 2175 | 2078 (76 / 472 / 591) | kagi_28, 3040 (121 / -370 / 48) |
| swsr5 | retest | dol_500 | {"M": 6, "tol": 0.5} | plain60/60 / short | 60 / 60 | 327 | 2394 | -338 | -1284 | -1751 | 2578 | 2394 (-338 / -1284 / -1751) | frenko_40, 4292 (-147 / -323 / -3129) |
| swsr5 | retest_native | dol_500 | {"M": 6, "tol": 0.5} | plain60/60 / short | 60 / 60 | 368 | 1701 | -359 | -1506 | -1538 | 1552 | 1701 (-359 / -1506 / -1538) | urenko_56, 3645 (-130 / 1122 / 406) |
| swsr60 | break | dol_350 | {"n": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 165 | 1249 | 164 | -622 | 254 | 1932 | 1249 (164 / -622 / 254) | lbrk_3_20, 2087 (-226 / -417 / 916) |
| swsr60 | break_native | dol_350 | {"n": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 165 | 1249 | 164 | -622 | 254 | 1932 | 1249 (164 / -622 / 254) | lbrk_3_20, 2087 (-226 / -417 / 916) |
| swsr60 | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 218 | 2051 | 406 | 749 | 1518 | 3117 | 1180 (480 / 66 / 1754) | lbrk_3_20, 3080 (63 / -144 / 856) |
| swsr60 | false_break_native | dol_350 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 363 | 2242 | 332 | -109 | 1535 | 3722 | 2242 (332 / -109 / 1535) | lbrk_3_20, 3080 (63 / -144 / 856) |
| swsr60 | reject | dol_500 | {"tol": 0.5, "conf": "body"} | sym15u / short | 120 / 120 | 96 | 896 | -71 | -830 | -537 | 397 | -222 (-26 / -586 / -208) | frenko_40, 901 (155 / -797 / 359) |
| swsr60 | reject_native | dol_6000 | {"tol": 1.0, "conf": "body"} | sym15u / short | 120 / 120 | 104 | 1463 | 116 | -794 | -885 | 2315 | 635 (139 / -751 / -388) | urenko_112, 1613 (196 / 417 / -574) |
| swsr60 | retest | vrb_700 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 278 | 2336 | -13 | -70 | -477 | 2897 | 2336 (-13 / -70 / -477) | urenko_40, 2036 (-8 / -105 / -593) |
| swsr60 | retest_native | vrb_700 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 315 | 1978 | 193 | 83 | 237 | 2192 | 1978 (193 / 83 / 237) | urenko_40, 2089 (120 / -274 / -719) |
| stack | break | rng_10 | {"k": 2, "cw": 1.0} | sym30u / both | 120 / 120 | 148 | 2776 | -782 | -209 | 540 | 2035 | 1119 (-667 / -114 / -922) | wrenko_14, 3697 (-1113 / -75 / 53) |
| stack | break_native | vol_1100 | {"k": 2, "cw": 2.0} | sym8u / both | 120 / 120 | 259 | 4020 | -769 | 291 | 1001 | 4305 | 2050 (-885 / 354 / 570) | frenko_28, 4216 (269 / 854 / 910) |
| stack | reject | tick_300 | {"k": 2, "cw": 2.0} | asym10u/20u / both | 120 / 120 | 186 | 2906 | 61 | 648 | 73 | 1352 | 339 (-146 / -65 / -8) | renko_10, 2437 (123 / 1362 / -980) |
| stack | reject_native | dol_500 | {"k": 2, "cw": 0.5} | plain60/60 / short | 60 / 60 | 404 | 2492 | -100 | -1358 | -2089 | 2951 | 2492 (-100 / -1358 / -2089) | renko_14, 2380 (-436 / -47 / -1891) |
| book_walls | break | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 120 / 120 | 95 | 1824 | 791 | 86 | 772 | 1607 | 894 (509 / -188 / -131) | dchg_14, 1054 (-86 / -1176 / -1450) |
| book_walls | break_native | time_m_1 | {"n": 1, "k": 0.0} | sym30u / both | 120 / 120 | 95 | 1824 | 841 | 86 | 772 | 1607 | 894 (559 / -188 / -131) | dchg_14, 1054 (-86 / -1176 / -1450) |
| book_walls | false_break | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 54 | 1020 | -630 | -597 | -345 | 292 | 771 (-346 / -451 / -513) | swing_atr_0.15, 500 (-250 / 867 / -330) |
| book_walls | false_break_native | dib_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 54 | 1020 | -630 | -597 | -345 | 292 | 771 (-346 / -451 / -513) | swing_atr_0.15, 500 (-250 / 867 / -330) |
| book_walls | reject | time_s_45 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 151 | 1480 | -474 | -213 | -350 | 2822 | -21 (668 / -1320 / -732) | mom_14, 534 (-356 / 693 / -176) |
| book_walls | reject_native | vsess_450 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 97 | 1443 | 732 | 638 | 74 | 699 | 556 (453 / -183 / 1330) | frenko_28, 812 (50 / -182 / -1110) |
| book_walls | retest | time_s_20 | {"M": 6, "tol": 0.5} | sym15u / both | 86 / 86 | 176 | 899 | -1465 | 616 | 147 | 1417 | 48 (81 / -334 / 830) | swing_atr_0.1, 417 (-67 / 295 / -235) |
| book_walls | retest_native | time_s_20 | {"M": 10, "tol": 0.5} | sym15u / both | 86 / 86 | 156 | 821 | -381 | -305 | -21 | 226 | 341 (756 / -653 / -409) | swing_atr_0.1, 301 (2 / 487 / -265) |
| book_walls_loose | break | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 120 / 120 | 191 | 3527 | 461 | 137 | 581 | 4298 | -590 (651 / 756 / -92) | renko_10, 2628 (-178 / 151 / -318) |
| book_walls_loose | break_native | tm45 | {"n": 1, "k": 0.0} | sym30u / both | 120 / 120 | 191 | 3527 | 411 | 137 | 581 | 4298 | -590 (601 / 756 / -92) | renko_10, 2628 (-178 / 151 / -318) |
| book_walls_loose | false_break | dib_2000 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 62 | 1856 | -61 | -317 | 372 | 986 | 390 (145 / 127 / -205) | kagi_10, 1370 (-1813 / -315 / -1735) |
| book_walls_loose | false_break_native | dib_2000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 62 | 1806 | 153 | -209 | 562 | 1133 | 660 (119 / 322 / -309) | swing_atr_0.1, 1691 (-1210 / 550 / 70) |
| book_walls_loose | reject | tm30 | {"tol": 1.0, "conf": "body"} | sym15u / both | 109 / 109 | 329 | 3303 | -618 | -483 | -2918 | 3949 | -878 (-585 / -924 / -321) | mom_10, 2124 (320 / 1489 / 964) |
| book_walls_loose | reject_native | tm45 | {"tol": 0.5, "conf": "body"} | sym30u / both | 120 / 120 | 209 | 3172 | 252 | -1284 | -1029 | 2939 | -489 (332 / -1361 / 198) | mom_10, 1965 (478 / -863 / 563) |
| book_walls_loose | retest | tm20 | {"M": 6, "tol": 0.5} | sym15u / both | 86 / 86 | 353 | 2344 | -963 | -496 | 59 | 3790 | 1014 (224 / -770 / 320) | swing_atr_0.15, 1237 (98 / 207 / 1167) |
| book_walls_loose | retest_native | time_s_15 | {"M": 6, "tol": 0.5} | sym15u / both | 73 / 73 | 438 | 1781 | -951 | -565 | -1164 | 2912 | 1706 (482 / -43 / -1036) | swing_atr_0.15, 1237 (98 / 207 / 1167) |
| channel | break | dol_500 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 681 | 3651 | -768 | 948 | 2734 | 5375 | 3651 (-768 / 948 / 2734) | kagi_14, 3760 (-394 / 415 / 890) |
| channel | break_native | dol_350 | {"n": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 731 | 3717 | -414 | 129 | 1845 | 3898 | 3717 (-414 / 129 / 1845) | kagi_14, 3760 (-394 / 415 / 890) |
| channel | false_break | dol_500 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 695 | 3253 | -687 | 480 | 1888 | 4822 | 3253 (-687 / 480 / 1888) | pnf_5, 4523 (-84 / 780 / 1351) |
| channel | false_break_native | dol_500 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 705 | 3193 | -741 | 141 | 1981 | 4742 | 3193 (-741 / 141 / 1981) | pnf_5, 4523 (-84 / 780 / 1351) |
| channel | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 319 | 2451 | -40 | -904 | 1980 | 74 | 197 (-342 / -151 / 523) | frenko_40, 2239 (-137 / -627 / -253) |
| channel | reject_native | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 319 | 2451 | -40 | -904 | 1980 | 74 | 197 (-342 / -151 / 523) | mrenko_20, 2704 (-28 / 101 / 2034) |
| channel | retest | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 488 | 3847 | -658 | -725 | -31 | 3628 | 3847 (-658 / -725 / -31) | kagi_56, 3220 (669 / -520 / 191) |
| channel | retest_native | dol_500 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 488 | 3847 | -658 | -725 | -31 | 3628 | 3847 (-658 / -725 / -31) | kagi_56, 3220 (669 / -520 / 191) |
| fvg15 | break | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 191 | 4507 | -198 | 255 | 2301 | 3589 | 2454 (-321 / 622 / 114) | mrenko_10, 3843 (-251 / 495 / 933) |
| fvg15 | break_native | vrb_700 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 191 | 4507 | -198 | 255 | 2301 | 3589 | 2454 (-321 / 622 / 114) | mrenko_10, 3696 (-362 / 650 / 1002) |
| fvg15 | false_break | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 179 | 4460 | -421 | 153 | 1819 | 3544 | 1665 (-466 / 479 / -115) | urenko_40, 3689 (-171 / -177 / 1864) |
| fvg15 | false_break_native | dol_500 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 172 | 4624 | -258 | 241 | 2280 | 3548 | 2101 (-380 / 590 / 446) | mrenko_20, 3960 (34 / 246 / 1170) |
| fvg15 | reject | vrb_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 172 | 2211 | -152 | 845 | -1066 | 1952 | 562 (-177 / 203 / -511) | mrenko_14, 1390 (-795 / -80 / 724) |
| fvg15 | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 197 | 1748 | -922 | -425 | 1122 | 1414 | 1047 (-809 / -24 / 1299) | mrenko_14, 3238 (-531 / 176 / 1230) |
| fvg15 | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 158 | 2861 | -10 | 344 | -1206 | 2681 | -73 (-130 / -104 / -1648) | wrenko_20, 2561 (-576 / 357 / 459) |
| fvg15 | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 165 | 3408 | -517 | 640 | -449 | 2985 | 228 (-423 / 263 / -590) | wrenko_10, 3378 (-38 / 97 / -280) |
| fvg5 | break | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 445 | 2122 | -166 | 849 | -30 | 2808 | 2122 (-166 / 849 / -30) | frenko_28, 3449 (423 / 609 / -1560) |
| fvg5 | break_native | dol_500 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 457 | 1869 | -386 | 607 | 53 | 2487 | 1869 (-386 / 607 / 53) | frenko_28, 3420 (327 / 253 / -1454) |
| fvg5 | false_break | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 112 | 1455 | -414 | 627 | 837 | 3129 | 1085 (-256 / 258 / 498) | lbrk_3_10, 2970 (-57 / -288 / -1769) |
| fvg5 | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 112 | 1455 | -414 | 627 | 837 | 3129 | 1085 (-256 / 258 / 498) | lbrk_3_10, 3092 (-31 / -408 / -1857) |
| fvg5 | reject | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 447 | 1478 | -77 | 39 | 809 | 2201 | 1478 (-77 / 39 / 809) | mrenko_10, 5293 (-657 / -3 / -1020) |
| fvg5 | reject_native | dol_500 | {"tol": 0.0, "conf": "close"} | plain60/60 / both | 60 / 60 | 447 | 1478 | -77 | 39 | 809 | 2201 | 1478 (-77 / 39 / 809) | mrenko_10, 4619 (-963 / -126 / -1590) |
| fvg5 | retest | dol_6000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 134 | 1600 | -15 | 297 | 1739 | 690 | 209 (-63 / 465 / 683) | wrenko_10, 3156 (-584 / -548 / -2079) |
| fvg5 | retest_native | vrb_700 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 112 | 1469 | 71 | -1267 | 524 | 2178 | 298 (277 / -1023 / -742) | wrenko_10, 3569 (-603 / -322 / -233) |
| gaps | break | rng_14 | {"n": 2, "k": 0.5} | sym30u / both | 120 / 120 | 140 | 2941 | 712 | 954 | 90 | 2534 | 1383 (567 / 705 / -186) | kagi_14, 2800 (-117 / -270 / 904) |
| gaps | break_native | dib_400 | {"n": 2, "k": 0.25} | sym15u / both | 96 / 96 | 181 | 3181 | 83 | 121 | -102 | 2510 | 662 (217 / 430 / 4) | kagi_14, 2800 (-117 / -270 / 904) |
| gaps | false_break | time_s_20 | {"M": 1, "k": 0.5} | asym10u/20u / both | 58 / 115 | 217 | 2043 | 148 | 16 | -25 | 2757 | -267 (454 / -232 / 120) | kagi_14, 3838 (-315 / -223 / 999) |
| gaps | false_break_native | time_s_20 | {"M": 1, "k": 0.5} | asym10u/20u / both | 58 / 115 | 233 | 1914 | -36 | -145 | 456 | 2280 | 177 (288 / -5 / 915) | kagi_14, 3828 (-358 / 225 / 1018) |
| gaps | reject | rng_10 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 75 / 120 | 173 | 2089 | 572 | -1514 | -1141 | 2058 | 962 (760 / -1259 / -1853) | mrenko_10, 2273 (361 / 369 / -613) |
| gaps | reject_native | time_s_20 | {"tol": 0.5, "conf": "body"} | asym10u/20u / both | 58 / 115 | 196 | 2257 | 282 | -855 | -20 | 2079 | 1652 (-319 / -1241 / 237) | renko_20, 2688 (-72 / -741 / 685) |
| gaps | retest | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 105 / 105 | 150 | 2373 | -138 | 438 | 1115 | 1777 | 1238 (-290 / 53 / 1209) | kagi_14, 2199 (392 / -438 / 502) |
| gaps | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 105 / 105 | 151 | 2887 | -129 | 409 | 967 | 2191 | 1016 (-340 / 447 / 1197) | kagi_14, 2867 (373 / -484 / 328) |
| mmove | break | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 355 | 1761 | -8 | 736 | 1461 | 1837 | 1761 (-8 / 736 / 1461) | frenko_28, 3266 (-125 / -274 / 199) |
| mmove | break_native | dol_6000 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 355 | 1761 | 3 | 736 | 1461 | 1837 | 1761 (3 / 736 / 1461) | frenko_28, 2913 (-307 / -72 / 462) |
| mmove | false_break | dol_350 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 322 | 4674 | -803 | 888 | 1620 | 3258 | -78 (-700 / -337 / -509) | kagi_56, 3727 (-662 / -437 / 695) |
| mmove | false_break_native | dol_350 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 322 | 5031 | -813 | 1377 | 2286 | 3597 | -545 (-746 / 269 / 1085) | kagi_56, 3727 (-665 / -437 / 695) |
| mmove | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 274 | 2229 | -215 | -135 | -986 | 3788 | 657 (-181 / 385 / -1100) | urenko_56, 2172 (-113 / 1317 / 220) |
| mmove | reject_native | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 296 | 1626 | -163 | 113 | -1948 | 2244 | 1350 (-70 / 68 / -1717) | urenko_20, 2494 (-127 / -205 / -307) |
| mmove | retest | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 266 | 3166 | -617 | 1628 | -199 | 3495 | 1735 (-682 / 152 / 162) | pnf_7, 4009 (-265 / 707 / 166) |
| mmove | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / both | 120 / 120 | 279 | 2802 | -598 | 1925 | -304 | 3173 | -258 (-637 / 264 / -386) | kagi_28, 3501 (153 / -509 / -661) |
| ob15 | break | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 89 | 710 | 405 | 447 | 384 | 914 | 710 (405 / 447 / 384) | mrenko_20, 1145 (-110 / 211 / 463) |
| ob15 | break_native | vrb_700 | {"n": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 89 | 710 | 405 | 447 | 384 | 914 | 710 (405 / 447 / 384) | mrenko_14, 1395 (9 / -204 / 659) |
| ob15 | false_break | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 35 | 733 | -85 | -25 | 420 | 701 | 733 (-85 / -25 / 420) | mrenko_10, 527 (393 / 352 / 362) |
| ob15 | false_break_native | vrb_700 | {"M": 1, "k": 0.0} | plain60/60 / short | 60 / 60 | 35 | 733 | -85 | -25 | 420 | 701 | 733 (-85 / -25 / 420) | mrenko_10, 527 (409 / 357 / 362) |
| ob15 | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 59 | 1016 | -445 | -109 | 212 | 1364 | -284 (-394 / -275 / 293) | urenko_10, 791 (-118 / 315 / -442) |
| ob15 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 79 | 1546 | -161 | -222 | 273 | 1825 | -159 (-196 / -469 / 146) | lbrk_3_10, 1375 (108 / 245 / -15) |
| ob15 | retest | dol_350 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 46 | 601 | -41 | -56 | 771 | 988 | -10 (-30 / -50 / 587) | mrenko_10, 729 (168 / 295 / -73) |
| ob15 | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 43 | 702 | 134 | 200 | -0 | 871 | 702 (134 / 200 / -0) | urenko_14, 942 (14 / -160 / 421) |
| ob5 | break | dol_350 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 60 | 1272 | -347 | 24 | 1246 | 1557 | 1012 (-276 / 348 / 73) | kagi_10, 1926 (-810 / -333 / 600) |
| ob5 | break_native | dol_350 | {"n": 3, "k": 0.5} | sym15u / long | 120 / 120 | 59 | 1571 | -502 | -31 | 1049 | 1663 | 1175 (-428 / 324 / 394) | kagi_56, 1866 (238 / 603 / 530) |
| ob5 | false_break | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 94 | 765 | 148 | 94 | 403 | 1194 | 765 (148 / 94 / 403) | urenko_80, 1216 (28 / 406 / 1050) |
| ob5 | false_break_native | dol_6000 | {"M": 2, "k": 0.5} | sym15u / long | 120 / 120 | 33 | 818 | 43 | 313 | 741 | 1423 | 480 (44 / 288 / 118) | urenko_40, 1109 (-143 / 486 / 1724) |
| ob5 | reject | dol_350 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 198 | 976 | -212 | 157 | -57 | 1407 | 976 (-212 / 157 / -57) | kagi_20, 2035 (288 / -683 / -526) |
| ob5 | reject_native | dol_350 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 284 | 1297 | -525 | -136 | 67 | 1508 | 1297 (-525 / -136 / 67) | kagi_20, 2437 (-94 / -408 / 247) |
| ob5 | retest | dol_350 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 173 | 800 | -69 | 38 | 1089 | 1019 | 800 (-69 / 38 / 1089) | kagi_28, 2116 (-453 / -364 / 1873) |
| ob5 | retest_native | dol_6000 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 38 | 1077 | 36 | -74 | 468 | 938 | 605 (58 / -129 / 218) | mrenko_14, 1697 (111 / -230 / 324) |
| open_range | break | dlt_600 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 70 | 1010 | 198 | 258 | 592 | 798 | 648 (141 / 353 / 590) | renko_80, 852 (167 / 281 / 958) |
| open_range | break_native | rng_80 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 53 | 1298 | 117 | 673 | 306 | 1466 | 1191 (136 / 619 / -245) | renko_112, 956 (277 / 240 / -326) |
| open_range | false_break | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 70 | 1010 | 198 | 258 | 592 | 798 | 648 (141 / 353 / 590) | renko_28, 873 (6 / 63 / 881) |
| open_range | false_break_native | dlt_600 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 70 | 1010 | 198 | 258 | 592 | 798 | 648 (141 / 353 / 590) | renko_28, 873 (6 / 63 / 881) |
| open_range | reject | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 30 | 1749 | -167 | -524 | 629 | 1343 | 709 (-196 / -252 / -51) | mom_112, 1071 (-0 / 126 / -100) |
| open_range | reject_native | cusum_80 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 58 | 1841 | -107 | -871 | 61 | 1790 | 760 (-168 / -600 / -326) | renko_56, 1445 (142 / -59 / -279) |
| open_range | retest | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 42 | 1729 | 78 | 85 | -517 | 1653 | 319 (11 / 304 / -848) | swing_atr_0.9, 1277 (267 / -0 / 229) |
| open_range | retest_native | tib_40000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 44 | 1630 | 90 | 126 | -312 | 1681 | 367 (23 / 377 / -647) | urenko_56, 1250 (300 / 583 / 167) |
| opens | break | tick_800 | {"n": 1, "k": 0.5} | asym10u/20u / both | 120 / 120 | 187 | 3057 | -72 | -628 | 803 | 3795 | 386 (-96 / 432 / 716) | renko_10, 2827 (-43 / -60 / 625) |
| opens | break_native | tick_800 | {"n": 1, "k": 0.0} | asym10u/20u / both | 120 / 120 | 181 | 2862 | 119 | -1050 | 634 | 2949 | 1123 (73 / 481 / 841) | renko_10, 3101 (-120 / -401 / 418) |
| opens | false_break | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 120 / 105 | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2618 (-279 / 1844 / -194) | mom_14, 2801 (-695 / 1748 / -1439) |
| opens | false_break_native | rng_14 | {"M": 2, "k": 0.0} | asym20u/10u / both | 120 / 105 | 230 | 3507 | -265 | 1161 | 1124 | 4942 | 2618 (-279 / 1844 / -194) | mom_14, 2709 (-924 / 1765 / -1224) |
| opens | reject | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 79 / 79 | 337 | 2673 | -406 | -615 | 1004 | 2486 | 758 (192 / 88 / 340) | lbrk_3_20, 2180 (-423 / 947 / -228) |
| opens | reject_native | dib_240 | {"tol": 0.5, "conf": "body"} | sym15u / both | 79 / 79 | 326 | 2567 | 351 | -48 | 259 | 2256 | 251 (693 / 405 / -576) | mrenko_14, 1750 (812 / 178 / 18) |
| opens | retest | tm10 | {"M": 3, "tol": 0.5} | sym15u / both | 54 / 54 | 435 | 3568 | -310 | -114 | -1092 | 4604 | 1833 (215 / -398 / -93) | lbrk_3_10, 2398 (48 / -421 / -849) |
| opens | retest_native | tib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 105 / 105 | 258 | 3460 | -259 | 680 | -1474 | 3879 | 1619 (-72 / 916 / -578) | lbrk_3_10, 1931 (-150 / -631 / -898) |
| prior_day | break | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 120 / 120 | 246 | 3507 | -655 | -1228 | 1030 | 4129 | -793 (-626 / -371 / 110) | mom_28, 2910 (-559 / 933 / 883) |
| prior_day | break_native | vsess_200 | {"n": 2, "k": 0.0} | asym20u/10u / both | 120 / 120 | 246 | 3507 | -655 | -1228 | 1030 | 4129 | -793 (-626 / -371 / 110) | mom_28, 2910 (-559 / 933 / 883) |
| prior_day | false_break | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 323 | 3765 | -768 | -1292 | -1567 | 2464 | 111 (-1117 / -1565 / -1855) | swing_atr_0.15, 3183 (-1040 / -1330 / 1769) |
| prior_day | false_break_native | vsess_200 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 313 | 3726 | -632 | -1514 | -2518 | 2479 | 607 (-1172 / -1525 / -2867) | swing_atr_0.15, 3183 (-1040 / -1330 / 1769) |
| prior_day | reject | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 120 / 120 | 196 | 2853 | 1004 | -338 | -174 | 2975 | -222 (985 / -587 / -1340) | frenko_40, 1929 (481 / 200 / 196) |
| prior_day | reject_native | rng_10 | {"tol": 0.0, "conf": "body"} | sym30u / both | 120 / 120 | 196 | 2853 | 1004 | -338 | -174 | 2975 | -222 (985 / -587 / -1340) | renko_20, 2328 (128 / -159 / 551) |
| prior_day | retest | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 196 | 2678 | 41 | -1271 | 1686 | 2766 | 185 (233 / -1045 / 964) | swing_atr_0.15, 2470 (-206 / 649 / 531) |
| prior_day | retest_native | vsess_200 | {"M": 6, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 208 | 3097 | 85 | -1821 | 1481 | 3186 | -956 (275 / -1186 / 634) | swing_atr_0.15, 2470 (-206 / 649 / 531) |
| profile_nodes | break | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 120 / 120 | 312 | 5604 | -351 | 1074 | -89 | 5675 | 2116 (187 / 982 / 462) | mom_20, 5235 (-220 / 450 / -323) |
| profile_nodes | break_native | vol_350 | {"n": 2, "k": 0.25} | sym8u / both | 120 / 120 | 315 | 6822 | -337 | 673 | 881 | 6105 | 1706 (17 / 840 / 1500) | renko_20, 4641 (-136 / 226 / 1661) |
| profile_nodes | false_break | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 556 | 3365 | -801 | 527 | 801 | 3841 | 3365 (-801 / 527 / 801) | renko_20, 3111 (-881 / 806 / 2172) |
| profile_nodes | false_break_native | rng_28 | {"M": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 558 | 3484 | -740 | 546 | 962 | 4423 | 3484 (-740 / 546 / 962) | renko_20, 3111 (-881 / 806 / 2172) |
| profile_nodes | reject | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 120 / 120 | 217 | 3451 | -794 | -877 | -1862 | 3671 | -12 (-860 / -880 / -1273) | mrenko_10, 2836 (-174 / 346 / -222) |
| profile_nodes | reject_native | tick_1300 | {"tol": 0.0, "conf": "close"} | sym8u / both | 120 / 120 | 217 | 3451 | -794 | -877 | -1862 | 3671 | -12 (-860 / -880 / -1273) | renko_10, 4029 (332 / -911 / -262) |
| profile_nodes | retest | tib_1200 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 235 | 3969 | 307 | 287 | 173 | 4860 | 1164 (274 / 116 / 936) | mrenko_10, 4628 (-315 / 325 / 906) |
| profile_nodes | retest_native | tib_400 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 565 | 4390 | -1341 | 74 | 1546 | 5242 | 4390 (-1341 / 74 / 1546) | mrenko_10, 4808 (-512 / 139 / 1484) |
| profile_va | break | vol_1700 | {"n": 2, "k": 0.5} | plain60/60 / both | 60 / 60 | 390 | 3386 | -189 | -192 | 528 | 2426 | 3386 (-189 / -192 / 528) | mrenko_14, 3734 (98 / -1260 / -135) |
| profile_va | break_native | rng_10 | {"n": 1, "k": 0.5} | sym15u / both | 112 / 112 | 295 | 4390 | 441 | 1089 | 434 | 4834 | 1223 (103 / 281 / 182) | mom_20, 3492 (315 / -685 / 532) |
| profile_va | false_break | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 86 / 86 | 406 | 4140 | -236 | 556 | 105 | 4352 | 1578 (-787 / -174 / -132) | dchg_10, 3049 (-1003 / 11 / 1020) |
| profile_va | false_break_native | time_s_20 | {"M": 2, "k": 0.5} | sym15u / both | 86 / 86 | 408 | 4355 | -797 | 1115 | 377 | 4710 | 1427 (-1006 / 202 / 396) | dchg_10, 3049 (-1003 / 11 / 1020) |
| profile_va | reject | tm45 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 272 | 3560 | 36 | -985 | -1281 | 2925 | -561 (-262 / -395 / -497) | mom_10, 2410 (406 / -1785 / -410) |
| profile_va | reject_native | rng_40 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 523 | 3959 | 232 | -523 | -699 | 2840 | 3959 (232 / -523 / -699) | swing_atr_0.15, 3423 (-318 / -705 / -1077) |
| profile_va | retest | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 112 / 112 | 278 | 3166 | -186 | 347 | -497 | 3338 | 1872 (-3 / -220 / 248) | mom_14, 2529 (-160 / -604 / 379) |
| profile_va | retest_native | rng_10 | {"M": 6, "tol": 0.5} | sym15u / both | 112 / 112 | 281 | 2708 | -4 | 174 | -601 | 3117 | 1152 (94 / -247 / 257) | swing_pct_8, 2876 (-589 / -641 / 945) |
| round | break | rng_10 | {"n": 1, "k": 0.5} | asym10u/20u / both | 75 / 120 | 504 | 4724 | -349 | -1442 | -58 | 2797 | 2476 (-657 / -1193 / 916) | renko_10, 3806 (-201 / -1642 / 1258) |
| round | break_native | rng_10 | {"n": 2, "k": 0.25} | sym30u / both | 120 / 120 | 344 | 5251 | -266 | 1464 | 1128 | 2860 | 3622 (-225 / 169 / 287) | dchg_40, 3283 (346 / 1266 / -1561) |
| round | false_break | vsess_600 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 510 | 5082 | 49 | 1726 | 822 | 2815 | -3457 (-448 / 1142 / 492) | swing_atr_0.15, 3583 (-154 / -691 / -151) |
| round | false_break_native | vsess_600 | {"M": 2, "k": 0.0} | sym15u / both | 120 / 120 | 512 | 4615 | 55 | 1226 | 1172 | 2100 | -4576 (-394 / 169 / 155) | swing_atr_0.15, 4209 (-127 / -226 / 152) |
| round | reject | rng_14 | {"tol": 1.0, "conf": "close"} | asym15u/30u / both | 120 / 120 | 357 | 5332 | -34 | -2185 | -928 | 2256 | 492 (-281 / -1459 / -2758) | renko_10, 3620 (-227 / -2528 / -500) |
| round | reject_native | rng_14 | {"tol": 0.5, "conf": "close"} | asym15u/30u / both | 120 / 120 | 352 | 6253 | -388 | -1954 | -762 | 2373 | 482 (-663 / -2112 / -829) | renko_14, 4086 (-235 / -2369 / -3944) |
| round | retest | vsess_50 | {"M": 3, "tol": 0.0} | plain60/60 / both | 60 / 60 | 480 | 4161 | -390 | -850 | -175 | 4245 | 4161 (-390 / -850 / -175) | renko_14, 3094 (23 / 168 / -82) |
| round | retest_native | tib_2000 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 746 | 4186 | -64 | -517 | -1818 | 3708 | 4186 (-64 / -517 / -1818) | urenko_10, 3568 (-118 / -1598 / 219) |
| session_hl | break | vol_6000 | {"n": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 50 | 1089 | 437 | 579 | -672 | 923 | 1089 (437 / 579 / -672) | mom_112, 1191 (365 / -30 / -555) |
| session_hl | break_native | vol_6000 | {"n": 1, "k": 0.25} | sym8u / both | 120 / 120 | 49 | 1120 | 317 | 376 | 508 | 682 | 1083 (303 / 262 / -365) | mom_112, 1191 (365 / -30 / -555) |
| session_hl | false_break | tib_3500 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 31 | 1085 | 293 | 74 | 850 | 728 | 254 (221 / 98 / 131) | mom_112, 1379 (345 / -101 / -707) |
| session_hl | false_break_native | dol_6000 | {"M": 1, "k": 0.0} | plain60/60 / both | 60 / 60 | 49 | 1024 | 230 | 591 | -381 | 686 | 1024 (230 / 591 / -381) | mom_112, 1310 (345 / -28 / -555) |
| session_hl | reject | tick_3200 | {"tol": 0.5, "conf": "close"} | sym8u / both | 120 / 120 | 30 | 943 | -354 | -388 | 424 | 693 | 196 (-313 / -484 / 281) | swing_pct_20, 966 (156 / 215 / 82) |
| session_hl | reject_native | tick_1300 | {"tol": 1.0, "conf": "close"} | sym8u / both | 120 / 120 | 33 | 1362 | -408 | 57 | -145 | 1310 | 588 (-280 / -90 / -133) | swing_pct_20, 885 (53 / 51 / -222) |
| session_hl | retest | drb_25000 | {"M": 10, "tol": 0.5} | sym15u / both | 120 / 120 | 55 | 757 | 0 | 84 | 33 | 1081 | -122 (0 / 24 / -70) | swing_atr_0.9, 930 (394 / -159 / 104) |
| session_hl | retest_native | cusum_80 | {"M": 10, "tol": 0.5} | plain60/60 / both | 60 / 60 | 38 | 995 | 142 | 57 | -11 | 297 | 995 (142 / 57 / -11) | mom_80, 1071 (10 / -357 / 55) |
| trendline | break | dol_500 | {"n": 1, "k": 0.0} | sym15u / both | 120 / 120 | 277 | 2434 | 340 | -559 | -497 | 3214 | 902 (239 / -1433 / 160) | frenko_28, 4047 (-334 / -565 / -398) |
| trendline | break_native | vrb_700 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 278 | 2631 | 56 | 1082 | -90 | 3650 | 762 (124 / 2165 / 1312) | frenko_28, 4047 (-334 / -565 / -398) |
| trendline | false_break | vrb_700 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 316 | 2330 | 226 | -444 | -677 | 1665 | 100 (144 / -302 / -181) | urenko_56, 2652 (5 / 374 / -456) |
| trendline | false_break_native | vrb_700 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 310 | 2405 | 621 | -712 | -1608 | 1349 | -872 (501 / -700 / -1375) | wrenko_14, 2491 (555 / -381 / 1308) |
| trendline | reject | dol_350 | {"tol": 0.0, "conf": "close"} | sym15u / short | 120 / 120 | 140 | 1908 | -389 | -337 | -229 | 2503 | 1614 (-412 / -44 / -955) | wrenko_10, 2489 (-856 / 1637 / -467) |
| trendline | reject_native | dol_6000 | {"tol": 0.5, "conf": "body"} | plain60/60 / both | 60 / 60 | 319 | 1927 | -360 | 665 | -452 | 1619 | 1927 (-360 / 665 / -452) | lbrk_3_40, 3233 (-304 / 1786 / -548) |
| trendline | retest | dol_500 | {"M": 10, "tol": 0.5} | sym15u / short | 120 / 120 | 107 | 2672 | -76 | -1151 | -251 | 3477 | 901 (-38 / -848 / -642) | kagi_20, 2659 (77 / -1818 / -579) |
| trendline | retest_native | dol_500 | {"M": 6, "tol": 0.5} | sym15u / short | 120 / 120 | 110 | 2940 | -11 | -899 | -333 | 3003 | 1498 (-71 / -280 / -214) | kagi_20, 2648 (-109 / -215 / 1694) |
| uw_dp | break | rng_10 | {"n": 2, "k": 0.5} | asym10u/20u / both | 75 / 120 | 248 | 3109 | 0 | 0 | -194 | 4482 | 2279 (0 / 0 / -572) | renko_14, 2950 (0 / 0 / -19) |
| uw_dp | break_native | rng_10 | {"n": 2, "k": 0.25} | plain60/60 / both | 60 / 60 | 321 | 3370 | 0 | 0 | -211 | 3635 | 3370 (0 / 0 / -211) | renko_14, 2950 (0 / 0 / -19) |
| uw_dp | false_break | vsess_120 | {"M": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 296 | 2541 | 0 | 0 | 145 | 2793 | 2541 (0 / 0 / 145) | lbrk_3_20, 2541 (0 / 0 / 860) |
| uw_dp | false_break_native | tick_300 | {"M": 3, "k": 0.5} | plain60/60 / both | 60 / 60 | 288 | 2400 | 0 | 0 | 474 | 2831 | 2400 (0 / 0 / 474) | lbrk_3_20, 2570 (0 / 0 / 860) |
| uw_dp | reject | rng_10 | {"tol": 1.0, "conf": "body"} | asym10u/20u / both | 75 / 120 | 241 | 3076 | 0 | 0 | -185 | 3668 | 2547 (0 / 0 / -109) | lbrk_3_10, 2098 (0 / 0 / -160) |
| uw_dp | reject_native | cdr_160 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 365 | 2903 | 0 | 0 | 640 | 2809 | 2903 (0 / 0 / 640) | pasl_40, 2321 (0 / 0 / 98) |
| uw_dp | retest | rng_10 | {"M": 3, "tol": 0.5} | asym10u/20u / both | 75 / 120 | 215 | 2671 | 0 | 0 | -118 | 3049 | 765 (0 / 0 / 106) | dchg_28, 3224 (0 / 0 / 812) |
| uw_dp | retest_native | tick_800 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 102 | 2288 | 0 | 0 | 180 | 2988 | 1211 (0 / 0 / 321) | dchg_14, 3604 (0 / 0 / 54) |
| uw_ndx | break | rng_80 | {"n": 1, "k": 0.25} | plain60/60 / both | 60 / 60 | 344 | 2496 | 0 | -120 | -300 | 2253 | 2496 (0 / -120 / -300) | renko_14, 2910 (0 / -114 / 269) |
| uw_ndx | break_native | rng_28 | {"n": 2, "k": 0.0} | sym8u / both | 120 / 120 | 189 | 2368 | 0 | -67 | 948 | 2850 | 1524 (0 / -223 / 24) | renko_28, 2821 (0 / 832 / 1783) |
| uw_ndx | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym8u / both | 120 / 120 | 282 | 2880 | 0 | 798 | -20 | 2253 | 2193 (0 / 258 / 1047) | lbrk_3_10, 2515 (0 / -439 / 311) |
| uw_ndx | false_break_native | rng_14 | {"M": 1, "k": 0.5} | sym8u / both | 84 / 84 | 296 | 2751 | 0 | 605 | 329 | 2931 | 1700 (0 / 627 / 1352) | lbrk_3_10, 2515 (0 / -439 / 311) |
| uw_ndx | reject | cusum_28 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 179 | 3907 | 0 | -115 | 231 | 3626 | 28 (0 / -577 / 301) | dchg_28, 2433 (0 / -851 / 1825) |
| uw_ndx | reject_native | dib_700 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 263 | 3310 | 0 | -439 | -2153 | 2322 | 191 (0 / -447 / -2019) | urenko_14, 2841 (0 / -205 / -680) |
| uw_ndx | retest | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 186 | 3189 | 0 | 458 | -820 | 3576 | 992 (0 / -36 / -1315) | urenko_80, 2395 (0 / -185 / 374) |
| uw_ndx | retest_native | vol_350 | {"M": 10, "tol": 0.5} | asym20u/10u / both | 120 / 120 | 197 | 3129 | 0 | 455 | -1052 | 2716 | 595 (0 / -6 / -1271) | urenko_80, 2602 (0 / -349 / 88) |
| uw_qqq | break | rng_14 | {"n": 2, "k": 0.5} | asym20u/10u / both | 120 / 105 | 275 | 3874 | 0 | 230 | -203 | 2990 | 1072 (0 / 262 / 215) | urenko_10, 3261 (0 / 123 / 1667) |
| uw_qqq | break_native | rng_80 | {"n": 1, "k": 0.5} | plain60/60 / both | 60 / 60 | 444 | 3333 | 0 | 825 | 798 | 2619 | 3333 (0 / 825 / 798) | urenko_10, 2953 (0 / 45 / 1343) |
| uw_qqq | false_break | cusum_112 | {"M": 1, "k": 0.0} | sym15u / both | 120 / 120 | 189 | 2553 | 0 | -215 | 1193 | 2621 | 386 (0 / -464 / -1185) | dchg_14, 2207 (0 / -642 / 1222) |
| uw_qqq | false_break_native | tick_500 | {"M": 2, "k": 0.5} | sym8u / both | 120 / 120 | 228 | 2553 | 0 | -518 | 1669 | 3080 | 1738 (0 / -565 / 1373) | dchg_14, 2342 (0 / -803 / 1038) |
| uw_qqq | reject | dol_350 | {"tol": 0.5, "conf": "body"} | sym15u / both | 120 / 120 | 211 | 4506 | 0 | -170 | -57 | 4909 | 1596 (0 / 9 / 725) | mom_40, 2471 (0 / -529 / -1012) |
| uw_qqq | reject_native | rng_28 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 585 | 4310 | 0 | 145 | -321 | 3898 | 4310 (0 / 145 / -321) | swing_pct_8, 3647 (0 / 19 / -946) |
| uw_qqq | retest | rng_14 | {"M": 3, "tol": 0.5} | asym20u/10u / both | 120 / 105 | 257 | 2889 | 0 | -916 | -406 | 2594 | 968 (0 / -722 / -184) | urenko_14, 2427 (0 / -836 / -170) |
| uw_qqq | retest_native | dlt_100 | {"M": 6, "tol": 0.5} | plain60/60 / both | 60 / 60 | 383 | 2224 | 0 | -263 | 721 | 2591 | 2224 (0 / -263 / 721) | renko_40, 2711 (0 / -192 / 815) |
| vwap | break | tick_500 | {"n": 1, "k": 0.5} | asym20u/10u / both | 120 / 120 | 243 | 4589 | 446 | 139 | -180 | 5086 | 2709 (369 / 40 / 345) | pasl_14, 4766 (-317 / 672 / 719) |
| vwap | break_native | cusum_14 | {"n": 2, "k": 0.0} | sym30u / both | 120 / 120 | 251 | 4117 | -608 | -1072 | 1694 | 4468 | 1943 (-441 / -1526 / 940) | pasl_14, 4766 (-317 / 672 / 719) |
| vwap | false_break | vsess_120 | {"M": 1, "k": 0.5} | asym10u/20u / both | 120 / 120 | 295 | 3625 | -599 | -915 | -95 | 4567 | 979 (-879 / -958 / -900) | pasl_10, 3707 (24 / -1009 / 1272) |
| vwap | false_break_native | rng_14 | {"M": 1, "k": 0.5} | asym20u/10u / both | 120 / 105 | 279 | 4303 | -276 | -1895 | 2871 | 4541 | 2216 (-456 / -742 / 570) | pasl_10, 3707 (24 / -1009 / 1272) |
| vwap | reject | cusum_14 | {"tol": 1.0, "conf": "body"} | asym15u/30u / both | 120 / 120 | 253 | 4824 | 391 | 1335 | -496 | 4063 | 341 (341 / 1095 / -848) | mom_10, 2505 (680 / 890 / -208) |
| vwap | reject_native | cusum_14 | {"tol": 0.5, "conf": "body"} | asym15u/30u / both | 120 / 120 | 259 | 6125 | -66 | 51 | -560 | 6208 | 1130 (11 / 218 / -408) | dchg_10, 3609 (-403 / -242 / 293) |
| vwap | retest | cusum_10 | {"M": 10, "tol": 0.5} | sym30u / both | 120 / 120 | 244 | 3984 | 745 | -933 | 4153 | 6617 | 1138 (263 / -1230 / 1755) | mom_14, 3440 (561 / -1618 / 3431) |
| vwap | retest_native | dlt_30 | {"M": 10, "tol": 0.0} | asym20u/10u / both | 120 / 116 | 288 | 3976 | 560 | -1057 | 1590 | 3989 | 2092 (-102 / -1741 / 1467) | mrenko_14, 3782 (-49 / 172 / 1188) |
| vwap_bands | break | dlt_30 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 342 | 4036 | -365 | -1198 | -1134 | 3306 | -982 (-311 / -223 / -463) | frenko_40, 4055 (470 / -88 / 753) |
| vwap_bands | break_native | time_m_2 | {"n": 2, "k": 0.25} | sym15u / both | 120 / 120 | 309 | 4019 | -106 | -2428 | -2221 | 2246 | 2104 (-425 / -1763 / 588) | renko_14, 3476 (-585 / 630 / -335) |
| vwap_bands | false_break | vsess_120 | {"M": 1, "k": 0.5} | sym30u / both | 120 / 120 | 286 | 3606 | -772 | 1263 | 588 | 3677 | 1207 (-525 / 836 / 686) | mom_80, 3133 (-94 / 562 / 806) |
| vwap_bands | false_break_native | time_m_15 | {"M": 3, "k": 0.5} | sym15u / both | 120 / 120 | 282 | 3942 | 302 | -309 | -1313 | 5176 | 571 (-110 / -525 / -481) | mom_80, 3133 (-95 / 562 / 806) |
| vwap_bands | reject | cdr_100 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 286 | 4404 | 318 | -901 | 1201 | 4016 | 1843 (284 / -518 / -527) | mom_10, 4433 (431 / -493 / -3278) |
| vwap_bands | reject_native | rng_80 | {"tol": 1.0, "conf": "body"} | plain60/60 / both | 60 / 60 | 627 | 4896 | 115 | 120 | 784 | 5405 | 4896 (115 / 120 / 784) | mom_10, 4872 (598 / -246 / -2166) |
| vwap_bands | retest | dib_400 | {"M": 6, "tol": 0.5} | sym15u / both | 96 / 96 | 483 | 3490 | -310 | -978 | -792 | 2632 | 1404 (-611 / 100 / -999) | mom_10, 3469 (309 / -358 / -560) |
| vwap_bands | retest_native | vol_350 | {"M": 6, "tol": 0.5} | sym8u / both | 120 / 120 | 359 | 4296 | -30 | 774 | 891 | 2066 | 1136 (215 / -220 / -210) | mom_10, 3469 (309 / -358 / -560) |
| week_month | break | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 120 / 120 | 44 | 1289 | -193 | -513 | -213 | 813 | 833 (-261 / -525 / -797) | frenko_28, 1357 (-472 / -345 / 67) |
| week_month | break_native | vsess_200 | {"n": 3, "k": 0.0} | asym20u/10u / both | 120 / 120 | 44 | 1289 | -193 | -513 | -213 | 813 | 833 (-261 / -525 / -797) | frenko_28, 1508 (-384 / -405 / 191) |
| week_month | false_break | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 53 | 1580 | -263 | -94 | 516 | 2291 | 1037 (-341 / -427 / -191) | swing_atr_0.6, 1710 (48 / 6 / 86) |
| week_month | false_break_native | vsess_80 | {"M": 2, "k": 0.5} | sym15u / both | 120 / 120 | 53 | 1816 | -233 | -4 | 426 | 2452 | 1098 (-281 / -186 / -344) | swing_atr_0.6, 1710 (48 / 6 / 86) |
| week_month | reject | vsess_50 | {"tol": 0.0, "conf": "close"} | sym15u / both | 120 / 120 | 33 | 1117 | 51 | 628 | -684 | 1334 | -86 (53 / -55 / -614) | mom_20, 1258 (146 / -282 / -335) |
| week_month | reject_native | tm780 | {"tol": 1.0, "conf": "body"} | sym15u / both | 120 / 120 | 60 | 1233 | -161 | 407 | -240 | 443 | 720 (-86 / -48 / -939) | renko_28, 1190 (-84 / 207 / -64) |
| week_month | retest | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 32 | 1176 | -66 | -246 | 312 | 1474 | 34 (-97 / -373 / -345) | mom_10, 902 (-331 / -243 / -451) |
| week_month | retest_native | cusum_20 | {"M": 3, "tol": 0.0} | sym15u / both | 120 / 120 | 32 | 1176 | -66 | -246 | 312 | 1474 | 34 (-97 / -373 / -345) | mom_28, 1160 (-99 / 167 / -411) |

## DATA-QUALITY NOTICE: the load-dependent "SLOW" acceptance check silently dropped 30 modules from the job lists (found 05:00Z, fixed 05:40Z)
Affected modules (pass-1 cells missing for them while rejected): bands_donchian, bands_envelope, bands_keltner, momentum_cci, momentum_mvote, momentum_willr, trend_heikin, trend_hma_turn, trend_supertrend, xmarket_commod, xmarket_es, xmarket_nkd, xmarket_rates, xmarket_rty, xmarket_tick, xmarket_leaders, levels_sd5, levels_sd15, levels_sd60, levels_fib5, levels_fib15, levels_fib60, levels_sdx3, levels_sdx5, levels_sdx15, levels_sdx30, levels_sdx60, levels_sdx_rng28, levels_sdx_vol1100, levels_sdx_renko28. All 146 modules are accepted again; their missing (row, module) pass-1 jobs are re-queued (stage b for level modules on time/volume/range rows, stage d for the rest). Missing pairs now: 12170 of 14280 (modules x 476 bar rows); pass-1 result files written in the last hour: 262 (all modules); ETA for these at that rate if they were alone: 46.5 h, real ETA depends on stage order (b before d).
Their pass-1 tables above are therefore PARTIAL for those modules (bands: Keltner/Donchian/envelope; momentum: CCI/mvote/Williams %R; trend: Supertrend/HMA turn/Heikin-Ashi; xmarket: ES/RTY/NKD/rates/commodities/tick/leaders; levels: supply-demand sd5/15/60, sdx3/5/15/30/60 + rng/vol/renko variants, Fibonacci 5/15/60).

