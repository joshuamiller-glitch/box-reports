# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 01:05Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 01:05Z):** result files per tag {"p1rand1": 11059, "p1rand2": 11054, "p1real": 11086, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"London": 2}; live-seven baseline: IN (30 rows). Sessions published: London (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 01:05Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1rand1": 11059, "p1rand2": 11054, "p1real": 11086, "rand1": 0, "real": 1654}; loop status: 2026-11-18T00:40Z rows=322 mods=116 todo=76376 running=0. 
Cells scored per session: {"London": 711856}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -35.3 | -0.034 | 1485.8 | 0.43 | -108.3 | -106.3 | -43.9 | -41.1 | 8.6 | 1.00 | -12.8 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -21.9 | -0.017 | 933.6 | 0.44 | -105.2 | -42.4 | -21.5 | -17.0 | -0.4 | 0.50 | -15.6 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -25.2 [0.0; 1.00] | -5.7 [3.6; 1.00] | -18.9 [0.0; 1.00] | -8.3 [-6.0; 0.00] |
| bands (native) | -3.1 [0.0; 1.00] | -41.6 [-1.9; 0.00] | -1.0 [0.0; 1.00] | -36.1 [-12.7; 0.50] |
| barnative | -18.1 [0.0; 1.00] | 3.5 [0.0; 1.00] | -24.1 [0.0; 1.00] | -28.6 [-4.9; 0.00] |
| confluence | -17.7 [0.0; 1.00] | -30.6 [-5.8; 0.00] | -13.6 [0.0; 1.00] | -2.7 [21.1; 1.00] |
| levels | -20.2 [0.0; 1.00] | -34.5 [3.7; 1.00] | 9.0 [0.0; 1.00] | -27.0 [-10.9; 0.50] |
| levels (native) | -8.5 [0.0; 1.00] | -1.3 [9.6; 1.00] | 9.4 [0.0; 1.00] | -18.5 [-15.2; 0.00] |
| live | -1.4 [0.0; 1.00] | -11.1 [2.0; 1.00] | 10.2 [0.0; 1.00] | 6.3 [5.1; 0.50] |
| manual | -34.8 [0.0; 1.00] | -10.3 [0.0; 1.00] | -51.7 [0.0; 1.00] | -29.4 [-17.3; 0.00] |
| manual (native) | 13.4 [0.0; 1.00] | -15.0 [0.0; 1.00] | -15.7 [0.0; 1.00] | 5.6 [11.7; 1.00] |
| momentum | -16.1 [0.0; 1.00] | 42.0 [3.1; 1.00] | 6.9 [0.0; 1.00] | 19.0 [27.4; 1.00] |
| momentum (native) | -31.2 [0.0; 1.00] | -30.2 [-3.3; 0.00] | -6.6 [0.0; 1.00] | 14.9 [21.9; 1.00] |
| pullback | -8.3 [0.0; 1.00] | 5.1 [2.3; 1.00] | -10.2 [0.0; 1.00] | -16.1 [-3.7; 0.50] |
| pullback (native) | -19.8 [0.0; 1.00] | -10.2 [-1.4; 0.00] | -19.5 [0.0; 1.00] | -37.8 [-3.8; 0.00] |
| structure | 5.2 [0.0; 1.00] | -32.0 [-10.3; 0.00] | -18.2 [0.0; 1.00] | -6.9 [8.5; 1.00] |
| structure (native) | -5.4 [0.0; 1.00] | -15.7 [-2.3; 0.00] | -4.2 [0.0; 1.00] | -11.6 [16.6; 0.50] |
| tape | -11.7 [0.0; 1.00] | 15.9 [2.2; 1.00] | 7.1 [0.0; 1.00] | -32.4 [-15.3; 0.50] |
| tape (native) | 12.7 [0.0; 1.00] | 16.6 [3.7; 1.00] | 12.4 [0.0; 1.00] | -27.0 [-10.5; 0.00] |
| trend | -31.0 [0.0; 1.00] | -25.9 [0.0; 1.00] | -47.0 [0.0; 1.00] | -10.5 [-6.8; 0.50] |
| trend (native) | -14.2 [0.0; 1.00] | -3.1 [1.6; 1.00] | -24.3 [0.0; 1.00] | -16.9 [-12.6; 0.00] |
| xmarket | 2.3 [0.0; 1.00] | 11.5 [5.0; 1.00] | -38.4 [0.0; 1.00] | -2.3 [11.6; 1.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | renko_14 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5738 | 2473 | 227 | 1.00 | None /  /  /  | {"2023": 534.0, "2024": -1080.0, "2025": -3184.0, "2026": 7299.0} |
| 2 | tm20 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 5614 | 2080 | 613 | 0.50 | None /  /  /  | {"2023": -1695.0, "2024": -839.0, "2025": -981.0, "2026": 7113.0} |
| 3 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5529 | 2203 | 230 | 1.00 | None /  /  /  | {"2023": 877.0, "2024": 1413.0, "2025": 8.0, "2026": 5170.0} |
| 4 | renko_14 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 5484 | 2321 | 230 | 1.00 | None /  /  /  | {"2023": 276.0, "2024": -1123.0, "2025": -2301.0, "2026": 6752.0} |
| 5 | tm780 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5463 | 2464 | 237 | 1.00 | None /  /  /  | {"2023": 821.0, "2024": -731.0, "2025": -822.0, "2026": 5499.0} |
| 6 | cdr_100 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5312 | 1946 | 232 | 1.00 | None /  /  /  | {"2023": 700.0, "2024": 1874.0, "2025": 1442.0, "2026": 5164.0} |
| 7 | time_s_5 | tape.tape_libvol.adline | {"len": 20} | plain60/60 | both | 5303 | 2868 | 836 | 0.67 | None /  /  /  | {"2023": 371.0, "2024": 263.0, "2025": 552.0, "2026": 6708.0} |
| 8 | tm15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 5261 | 1540 | 719 | 1.00 | None /  /  /  | {"2023": 266.0, "2024": -2665.0, "2025": -2838.0, "2026": 5771.0} |
| 9 | dchg_10 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 5243 | 1638 | 244 | 1.00 | None /  /  /  | {"2023": 196.0, "2024": -2911.0, "2025": 102.0, "2026": 6078.0} |
| 10 | tm420 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5217 | 2405 | 222 | 1.00 | None /  /  /  | {"2023": -371.0, "2024": -149.0, "2025": -9.0, "2026": 6896.0} |
| 11 | vsess_50 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5120 | 2049 | 223 | 1.00 | None /  /  /  | {"2023": -517.0, "2024": 795.0, "2025": -1956.0, "2026": 5273.0} |
| 12 | time_s_15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 4880 | 940 | 719 | 0.67 | None /  /  /  | {"2023": -199.0, "2024": -3558.0, "2025": -2877.0, "2026": 4789.0} |
| 13 | tm30 | bands.bands_regchan.break_stderr | {"n": 10, "k": 1.5} | sym15u | both | 4756 | 1586 | 428 | 1.00 | None /  /  /  | {"2023": -341.0, "2024": 434.0, "2025": -1516.0, "2026": 5654.0} |
| 14 | tm30 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym15u | both | 4756 | 1586 | 428 | 1.00 | None /  /  /  | {"2023": -270.0, "2024": 434.0, "2025": -1516.0, "2026": 5654.0} |
| 15 | tick_500 | trend.trend_macd.hist_turn | {"len": 6, "width": 0.0} | sym15u | both | 4728 | 2029 | 291 | 1.00 | None /  /  /  | {"2023": -379.0, "2024": 456.0, "2025": -406.0, "2026": 4423.0} |
| 16 | vsess_300 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 4725 | 1408 | 232 | 1.00 | None /  /  /  | {"2023": 827.0, "2024": -1965.0, "2025": -1079.0, "2026": 2092.0} |
| 17 | dchg_20 | levels.levels_vwap.break_native | {"n": 2, "k": 0.25} | sym15u | both | 4712 | 2238 | 229 | 1.00 | None /  /  /  | {"2023": -222.0, "2024": -760.0, "2025": -1838.0, "2026": 4187.0} |
| 18 | vol_1100 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 4691 | 2658 | 223 | 1.00 | None /  /  /  | {"2023": -300.0, "2024": 670.0, "2025": -2562.0, "2026": 5107.0} |
| 19 | tm900 | levels.levels_vwap.break_native | {"n": 1, "k": 0.0} | sym15u | both | 4682 | 2782 | 192 | 1.00 | None /  /  /  | {"2023": 154.0, "2024": 219.0, "2025": -854.0, "2026": 4271.0} |
| 20 | tm900 | levels.levels_vwap.break | {"n": 1, "k": 0.0} | sym15u | both | 4682 | 2782 | 192 | 1.00 | None /  /  /  | {"2023": 154.0, "2024": 219.0, "2025": -854.0, "2026": 4271.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.40 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.10 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.09 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.85 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.86 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.62 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.33 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.80 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.80 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.26 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.95 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.91 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.63 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.58 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.28 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.64 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.58 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.81 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.18 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.16 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.85 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.78 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell renko_14 levels.levels_vwap.break_native sym15u L6M 220.7 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
