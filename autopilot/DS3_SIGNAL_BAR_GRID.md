# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-18 01:23Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**STATUS (PARTIAL until pass 1 completes; refreshed 2026-11-18 01:23Z):** result files per tag {"p1rand1": 12726, "p1rand2": 12721, "p1real": 12760, "rand1": 0, "real": 1654}; bar families present as columns: ACTIVITY, INFORMATION, PRICE, TIME; null draws per cell (random-entry replicas in the scored sessions): {"London": 2, "NYAM": 2, "NYPM": 2, "Asia": 2}; live-seven baseline: IN (125 rows). Sessions published: London, NYAM, NYPM, Asia (a session whose scoring failed is simply absent). Next refresh within 30 min (gcycle).

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-18 01:23Z)
COVERAGE (this table is PARTIAL while pass 1 runs): result files per tag {"p1rand1": 12726, "p1rand2": 12721, "p1real": 12760, "rand1": 0, "real": 1654}; loop status: 2026-11-18T01:10Z rows=322 mods=116 todo=70607 running=0. 
Cells scored per session: {"London": 711856, "NYAM": 803164, "NYPM": 822285, "Asia": 822028}

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

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 14.5 | 0.014 | 532.9 | 0.56 | -11.4 | 46.3 | 5.2 | 17.2 | 9.3 | 0.50 | 4.6 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| agreed | 10.7 | 0.009 | 553.2 | 0.53 | -32.0 | 1.6 | 22.4 | 23.4 | -11.7 | 0.00 | 2.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | -2.1 [0.0; 1.00] | 34.2 [0.2; 1.00] | -20.8 [0.0; 1.00] | 3.4 [19.8; 1.00] |
| bands (native) | -21.8 [0.0; 1.00] | 19.1 [-11.6; 0.00] | 14.6 [0.0; 1.00] | -31.5 [-25.7; 0.00] |
| barnative | -7.0 [0.0; 1.00] | -1.9 [-9.8; 0.00] | 32.5 [0.0; 1.00] | -8.0 [15.4; 1.00] |
| confluence | 13.5 [0.0; 1.00] | -25.0 [-3.7; 0.00] | 13.6 [0.0; 1.00] | 12.5 [-7.9; 0.00] |
| levels | 42.0 [0.0; 1.00] | -26.4 [0.0; 1.00] | 12.9 [0.0; 1.00] | 7.5 [5.0; 0.50] |
| levels (native) | 16.4 [0.0; 1.00] | -1.6 [0.0; 1.00] | 25.3 [0.0; 1.00] | -3.4 [-5.1; 0.50] |
| live | 17.8 [0.0; 1.00] | -13.7 [0.0; 1.00] | 7.2 [0.0; 1.00] | -10.3 [11.9; 1.00] |
| manual | -3.7 [0.0; 1.00] | 27.9 [-0.8; 0.50] | 8.7 [0.0; 1.00] | 27.1 [7.3; 0.50] |
| manual (native) | -61.0 [0.0; 1.00] | -53.5 [0.0; 1.00] | -18.7 [0.0; 1.00] | 8.7 [15.2; 1.00] |
| momentum | 9.4 [0.0; 1.00] | 9.4 [4.1; 1.00] | 0.7 [0.0; 1.00] | -31.8 [-51.9; 0.00] |
| momentum (native) | 7.6 [0.0; 1.00] | 5.0 [3.3; 1.00] | -24.2 [0.0; 1.00] | -23.0 [-36.4; 0.00] |
| pullback | 20.3 [0.0; 1.00] | 41.1 [2.7; 1.00] | 41.1 [0.0; 1.00] | 16.4 [-7.6; 0.50] |
| pullback (native) | 32.7 [0.0; 1.00] | -4.9 [0.0; 1.00] | 16.4 [0.0; 1.00] | -21.4 [-28.7; 0.00] |
| structure | 32.8 [0.0; 1.00] | 31.8 [6.5; 1.00] | 80.7 [0.0; 1.00] | -4.1 [15.2; 1.00] |
| structure (native) | 34.7 [0.0; 1.00] | 27.0 [2.0; 1.00] | 17.3 [0.0; 1.00] | -6.5 [3.1; 0.50] |
| tape | 5.8 [0.0; 1.00] | -32.3 [0.0; 1.00] | -20.8 [0.0; 1.00] | 20.8 [10.6; 0.50] |
| tape (native) | 37.5 [0.0; 1.00] | 14.0 [0.0; 1.00] | 17.6 [0.0; 1.00] | -4.3 [-0.8; 0.00] |
| trend | -23.4 [0.0; 1.00] | -62.0 [0.0; 1.00] | -35.1 [0.0; 1.00] | -2.5 [-2.0; 0.50] |
| trend (native) | -20.9 [0.0; 1.00] | 1.4 [0.0; 1.00] | -2.3 [0.0; 1.00] | 13.7 [9.6; 0.50] |
| xmarket | 5.3 [0.0; 1.00] | -24.9 [0.0; 1.00] | -32.1 [0.0; 1.00] | -66.5 [-10.6; 0.50] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | renko_10 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | plain60/60 | both | 7125 | 2270 | 1721 | 1.00 | None /  /  /  | {"2023": 1069.0, "2024": 1029.0, "2025": -6564.0, "2026": 6771.0} |
| 2 | vol_350 | levels.levels_round.break_native | {"n": 2, "k": 0.25} | sym15u | both | 7094 | 3963 | 495 | 1.00 | None /  /  /  | {"2023": -581.0, "2024": 2932.0, "2025": 5800.0, "2026": 6840.0} |
| 3 | cdr_400 | xmarket.xmarket_etf.follow_IWM | {"w": 5, "thr": 1.5} | sym15u | both | 7083 | 1912 | 230 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": -297.0, "2025": 17.0, "2026": 7384.0} |
| 4 | dib_240 | momentum.momentum_libosc.mfi | {"len": 7, "lvl": 15} | plain60/60 | both | 7012 | 3214 | 1869 | 1.00 | None /  /  /  | {"2023": -1213.0, "2024": -3373.0, "2025": -4932.0, "2026": 7671.0} |
| 5 | cdr_250 | xmarket.xmarket_mega.revert | {"w": 1, "thr": 1.0} | sym15u | both | 6993 | 3548 | 440 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": -1272.0, "2025": -1217.0, "2026": 7229.0} |
| 6 | vol_500 | levels.levels_round.break | {"n": 2, "k": 0.25} | sym15u | both | 6988 | 2980 | 501 | 1.00 | None /  /  /  | {"2023": -467.0, "2024": 3516.0, "2025": 6085.0, "2026": 5453.0} |
| 7 | tick_300 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "body"} | sym15u | both | 6921 | 2452 | 481 | 1.00 | None /  /  /  | {"2023": 265.0, "2024": -1109.0, "2025": 2152.0, "2026": 7293.0} |
| 8 | renko_56 | xmarket.xmarket_optflow.revert_nd_SPY | {"w": 5, "thr": 1.5} | sym15u | both | 6800 | 3271 | 332 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": 322.0, "2025": 127.0, "2026": 8530.0} |
| 9 | vsess_600 | structure.structure_inside.outside | {"cf": 0.75, "filt": 0} | sym15u | both | 6761 | 2752 | 612 | 0.50 | None /  /  /  | {"2023": -1701.0, "2024": -2802.0, "2025": 3461.0, "2026": 9458.0} |
| 10 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym15u | both | 6733 | 2241 | 390 | 1.00 | None /  /  /  | {"2023": 483.0, "2024": 206.0, "2025": -2823.0, "2026": 9680.0} |
| 11 | tick_800 | tape.tape_delta.fade_sm | {"L": 50, "z": 1.0, "sm": 3} | sym15u | both | 6696 | 4255 | 514 | 0.50 | None /  /  /  | {"2023": -792.0, "2024": 995.0, "2025": 50.0, "2026": 7310.0} |
| 12 | vol_2600 | tape.tape_vpin.fade_native | {"N": 600, "thr": 0.05} | sym15u | both | 6683 | 2970 | 468 | 1.00 | None /  /  /  | {"2023": 1412.0, "2024": -2204.0, "2025": -3162.0, "2026": 6430.0} |
| 13 | vsess_600 | bands.bands_regchan.fade_linreg_native | {"clk": 20, "k": 2.5} | sym15u | both | 6678 | 3326 | 567 | 1.00 | None /  /  /  | {"2023": 1064.0, "2024": 2942.0, "2025": 282.0, "2026": 6912.0} |
| 14 | tick_500 | tape.tape_delta.fade_native | {"L": 900, "z": 1.0} | plain60/60 | both | 6575 | 2980 | 1642 | 1.00 | None /  /  /  | {"2023": -1286.0, "2024": -4768.0, "2025": -3824.0, "2026": 6035.0} |
| 15 | cusum_56 | xmarket.xmarket_mega.revert | {"w": 1, "thr": 1.0} | sym15u | both | 6543 | 1735 | 420 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": -1051.0, "2025": -53.0, "2026": 6010.0} |
| 16 | rng_56 | xmarket.xmarket_mega.revert | {"w": 1, "thr": 1.0} | sym15u | both | 6516 | 2385 | 422 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": -1122.0, "2025": -608.0, "2026": 6079.0} |
| 17 | dchg_14 | levels.levels_vwap_bands.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 6479 | 2407 | 512 | 1.00 | None /  /  /  | {"2023": -1030.0, "2024": 939.0, "2025": 1990.0, "2026": 7581.0} |
| 18 | vol_750 | xmarket.xmarket_ym.diverge | {"w": 30} | sym15u | both | 6423 | 2777 | 424 | 1.00 | None /  /  /  | {"2023": -1391.0, "2024": -1257.0, "2025": -4348.0, "2026": 4304.0} |
| 19 | tick_300 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 6417 | 1634 | 493 | 1.00 | None /  /  /  | {"2023": 1308.0, "2024": -1700.0, "2025": -1308.0, "2026": 7480.0} |
| 20 | tick_500 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | plain60/60 | both | 6408 | 2437 | 1375 | 1.00 | None /  /  /  | {"2023": -650.0, "2024": -713.0, "2025": -2142.0, "2026": 7649.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -13.1 | -0.015 | 1238.0 | 0.47 | 48.5 | 99.6 | -3.0 | -1.6 | -10.2 | 0.00 | 24.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | -14.8 | -0.016 | 1283.8 | 0.47 | 48.5 | 99.6 | -21.0 | -14.9 | 6.2 | 1.00 | 15.5 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 32.6 [0.0; 1.00] | 5.2 [3.4; 1.00] | -47.1 [0.0; 1.00] | 20.3 [25.8; 1.00] |
| bands (native) | -20.6 [0.0; 1.00] | 14.6 [2.2; 1.00] | -49.3 [0.0; 1.00] | -12.3 [9.9; 1.00] |
| barnative | -47.3 [0.0; 1.00] | -1.1 [-2.6; 0.50] | -13.6 [0.0; 1.00] | -31.7 [-41.4; 0.00] |
| confluence | 1.5 [0.0; 1.00] | -33.2 [7.1; 1.00] | -23.7 [0.0; 1.00] | -16.6 [15.0; 1.00] |
| levels | -8.7 [0.0; 1.00] | -19.9 [1.8; 1.00] | -12.7 [0.0; 1.00] | 5.6 [13.2; 1.00] |
| levels (native) | 18.2 [0.0; 1.00] | -21.2 [1.2; 1.00] | -40.7 [0.0; 1.00] | -30.5 [-19.8; 0.50] |
| live | -31.3 [0.0; 1.00] | -37.6 [-2.0; 0.00] | -13.6 [0.0; 1.00] | -16.8 [-29.1; 0.00] |
| manual | -26.0 [0.0; 1.00] | -12.4 [0.0; 1.00] | 19.8 [0.0; 1.00] | 27.3 [27.2; 1.00] |
| manual (native) | -16.0 [0.0; 1.00] | 0.9 [4.5; 1.00] | 10.8 [0.0; 1.00] | -14.2 [-7.6; 0.50] |
| momentum | 10.6 [0.0; 1.00] | -8.9 [-8.7; 0.00] | -31.9 [0.0; 1.00] | 10.9 [25.5; 1.00] |
| momentum (native) | 15.1 [0.0; 1.00] | -43.7 [2.0; 1.00] | 2.2 [0.0; 1.00] | -4.5 [8.7; 1.00] |
| pullback | -37.6 [0.0; 1.00] | -15.8 [3.8; 1.00] | -14.9 [0.0; 1.00] | -30.0 [15.8; 1.00] |
| pullback (native) | -18.4 [0.0; 1.00] | -25.4 [8.5; 1.00] | 7.5 [0.0; 1.00] | -26.6 [-11.8; 0.50] |
| structure | 38.0 [0.0; 1.00] | -13.7 [2.6; 1.00] | -16.3 [0.0; 1.00] | 29.6 [1.8; 0.50] |
| structure (native) | -27.3 [0.0; 1.00] | -8.4 [-5.7; 0.00] | 12.7 [0.0; 1.00] | 21.9 [22.2; 1.00] |
| tape | -22.1 [0.0; 1.00] | 4.8 [5.5; 1.00] | -18.7 [0.0; 1.00] | -71.0 [-41.2; 0.00] |
| tape (native) | -11.1 [0.0; 1.00] | -10.6 [-4.7; 0.00] | 9.5 [0.0; 1.00] | 4.5 [16.3; 1.00] |
| trend | -18.8 [0.0; 1.00] | 39.9 [4.6; 1.00] | -6.1 [0.0; 1.00] | -7.5 [16.7; 1.00] |
| trend (native) | 23.9 [0.0; 1.00] | -23.5 [1.3; 1.00] | -12.6 [0.0; 1.00] | 6.2 [3.4; 1.00] |
| xmarket | -16.7 [0.0; 1.00] | -25.8 [-5.4; 0.00] | 0.3 [0.0; 1.00] | -21.9 [6.4; 1.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_2000 | barnative.barnative_speed.burst_fade | {"len": 100, "r": 0.6} | plain60/60 | both | 6993 | 1620 | 1029 | 0.50 | None /  /  /  | {"2023": 627.0, "2024": 603.0, "2025": -1983.0, "2026": 6898.0} |
| 2 | vol_2600 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 6729 | 2188 | 270 | 1.00 | None /  /  /  | {"2023": -1244.0, "2024": -1502.0, "2025": 3102.0, "2026": 7745.0} |
| 3 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.08} | plain60/60 | both | 5867 | 1722 | 855 | 1.00 | None /  /  /  | {"2023": -61.0, "2024": -81.0, "2025": -154.0, "2026": 5010.0} |
| 4 | renko_20 | structure.structure_level.round_break | {"grid": 100, "buf": 0.25} | sym15u | both | 5790 | 1514 | 285 | 1.00 | None /  /  /  | {"2023": -1814.0, "2024": 1098.0, "2025": -3217.0, "2026": 7515.0} |
| 5 | vol_2600 | trend.trend_macd.hist_turn | {"len": 6, "width": 0.0} | sym15u | both | 5696 | 2761 | 331 | 1.00 | None /  /  /  | {"2023": -1592.0, "2024": 1832.0, "2025": 1475.0, "2026": 5233.0} |
| 6 | tick_1300 | momentum.momentum_roc.break_native | {"len": 5, "wd": 0.5} | sym15u | both | 5667 | 2136 | 329 | 1.00 | None /  /  /  | {"2023": 31.0, "2024": -1701.0, "2025": 174.0, "2026": 6932.0} |
| 7 | vsess_300 | manual.manual_cci.go | {"len": 14, "lvl": 100} | sym15u | both | 5566 | 695 | 338 | 0.50 | None /  /  /  | {"2023": -1509.0, "2024": -1137.0, "2025": -1791.0, "2026": 5512.0} |
| 8 | time_s_5 | structure.structure_libpattern.pin | {"k": 2.0, "filt": 0} | plain60/60 | both | 5554 | 2258 | 1029 | 1.00 | None /  /  /  | {"2023": 814.0, "2024": -1934.0, "2025": 3639.0, "2026": 5009.0} |
| 9 | cusum_28 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym15u | both | 5483 | 1350 | 333 | 1.00 | None /  /  /  | {"2023": -372.0, "2024": 983.0, "2025": 1248.0, "2026": 7307.0} |
| 10 | vol_350 | trend.trend_psar.flip | {"af0": 0.03, "step": 0.02, "max": 0.2} | plain60/60 | both | 5451 | 1706 | 984 | 1.00 | None /  /  /  | {"2023": 1140.0, "2024": 1596.0, "2025": 3398.0, "2026": 4270.0} |
| 11 | time_s_15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | both | 5418 | 2146 | 927 | 1.00 | None /  /  /  | {"2023": -2269.0, "2024": -2257.0, "2025": 207.0, "2026": 4647.0} |
| 12 | tm10 | trend.trend_ma_sma.cross_native | {"len": 5, "width": 0.25, "ratio": 3} | plain60/60 | both | 5405 | 2892 | 882 | 1.00 | None /  /  /  | {"2023": -576.0, "2024": 932.0, "2025": 1778.0, "2026": 4975.0} |
| 13 | dib_2000 | tape.tape_speed.fade_native | {"f": 1.5, "L": 900} | plain60/60 | both | 5384 | 1075 | 1012 | 1.00 | None /  /  /  | {"2023": 1179.0, "2024": -137.0, "2025": 2370.0, "2026": 3618.0} |
| 14 | cusum_10 | confluence.confluence_user.user5 | {"k": 2, "w": 1} | sym15u | both | 5366 | 2158 | 441 | 1.00 | None /  /  /  | {"2023": -1553.0, "2024": 1451.0, "2025": -1278.0, "2026": 3684.0} |
| 15 | vol_2600 | structure.structure_libpattern.nr | {"n": 7} | sym15u | both | 5293 | 1388 | 294 | 1.00 | None /  /  /  | {"2023": -1232.0, "2024": -1548.0, "2025": 2246.0, "2026": 5979.0} |
| 16 | tm15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | both | 5262 | 1994 | 926 | 1.00 | None /  /  /  | {"2023": -1247.0, "2024": -1701.0, "2025": 783.0, "2026": 4751.0} |
| 17 | vsess_80 | structure.structure_libpattern.nr | {"n": 10} | sym15u | both | 5241 | 1007 | 273 | 0.67 | None /  /  /  | {"2023": -1754.0, "2024": 222.0, "2025": 2642.0, "2026": 3765.0} |
| 18 | vol_6000 | levels.levels_session_hl.retest_native | {"M": 10, "tol": 0.5} | sym15u | both | 5238 | 1619 | 198 | 1.00 | None /  /  /  | {"2023": -2261.0, "2024": 2114.0, "2025": 2158.0, "2026": 4134.0} |
| 19 | dchg_28 | xmarket.xmarket_optflow.revert_nd_QQQ | {"w": 5, "thr": 1.5} | sym15u | both | 5205 | 1792 | 300 | 1.00 | None /  /  /  | {"2023": 0.0, "2024": -443.0, "2025": -4171.0, "2026": 6264.0} |
| 20 | vsess_80 | structure.structure_libpattern.nr | {"n": 7} | sym15u | both | 5179 | 1481 | 288 | 0.75 | None /  /  /  | {"2023": -2246.0, "2024": 1700.0, "2025": 631.0, "2026": 2796.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -11.1 | -0.022 | 520.2 | 0.47 | -95.0 | -191.8 | -7.3 | -5.0 | -3.8 | 0.00 | 15.0 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | -1.1 | -0.010 | 326.6 | 0.49 | -95.0 | -191.8 | 1.4 | 2.7 | -2.6 | 0.00 | 13.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | ACTIVITY | INFORMATION | PRICE | TIME |
|---|---|---|---|---|
| bands | 15.1 [0.0; 1.00] | 13.1 [-9.2; 0.00] | 18.3 [0.0; 1.00] | -28.8 [-39.5; 0.00] |
| bands (native) | -8.3 [0.0; 1.00] | 15.1 [-1.5; 0.00] | 16.5 [0.0; 1.00] | -1.5 [0.8; 0.50] |
| barnative | 6.1 [0.0; 1.00] | 2.0 [0.0; 1.00] | 0.5 [0.0; 1.00] | -18.6 [9.9; 1.00] |
| confluence | 9.0 [0.0; 1.00] | -11.2 [-3.5; 0.00] | -14.3 [0.0; 1.00] | -23.8 [-0.4; 0.50] |
| levels | 24.7 [0.0; 1.00] | -25.7 [-0.5; 0.00] | 40.7 [0.0; 1.00] | 4.7 [8.8; 1.00] |
| levels (native) | 28.4 [0.0; 1.00] | 9.2 [-4.1; 0.00] | 47.5 [0.0; 1.00] | 14.9 [7.3; 1.00] |
| live | 17.0 [0.0; 1.00] | 1.2 [0.7; 1.00] | 9.4 [0.0; 1.00] | 11.7 [18.3; 1.00] |
| manual | 10.2 [0.0; 1.00] | 3.0 [-0.5; 0.00] | 16.5 [0.0; 1.00] | 4.3 [1.0; 0.50] |
| manual (native) | 12.5 [0.0; 1.00] | -18.3 [-0.9; 0.00] | -1.3 [0.0; 1.00] | -5.7 [-9.2; 0.00] |
| momentum | 12.7 [0.0; 1.00] | -2.0 [0.8; 1.00] | 24.2 [0.0; 1.00] | 7.6 [0.9; 0.50] |
| momentum (native) | -9.2 [0.0; 1.00] | 2.7 [-8.4; 0.00] | 26.2 [0.0; 1.00] | -0.9 [-7.4; 0.00] |
| pullback | 23.0 [0.0; 1.00] | 35.6 [1.0; 1.00] | 4.7 [0.0; 1.00] | -6.3 [14.0; 1.00] |
| pullback (native) | 21.5 [0.0; 1.00] | -1.0 [1.9; 1.00] | -4.8 [0.0; 1.00] | -8.8 [5.1; 1.00] |
| structure | 7.5 [0.0; 1.00] | 6.9 [0.0; 1.00] | 27.6 [0.0; 1.00] | -3.8 [2.3; 0.50] |
| structure (native) | 1.6 [0.0; 1.00] | 1.2 [0.0; 1.00] | 15.4 [0.0; 1.00] | 3.0 [16.4; 1.00] |
| tape | -12.9 [0.0; 1.00] | -0.3 [-0.2; 0.00] | -17.9 [0.0; 1.00] | 17.6 [-4.9; 0.00] |
| tape (native) | -14.0 [0.0; 1.00] | 16.8 [0.0; 1.00] | -35.9 [0.0; 1.00] | 1.0 [-2.5; 0.00] |
| trend | 16.3 [0.0; 1.00] | 42.9 [3.4; 1.00] | 3.2 [0.0; 1.00] | 25.6 [25.1; 1.00] |
| trend (native) | -4.2 [0.0; 1.00] | 22.8 [0.9; 1.00] | -2.2 [0.0; 1.00] | 18.3 [-7.6; 0.00] |
| xmarket | -6.1 [0.0; 1.00] | -3.4 [2.4; 1.00] | -46.7 [0.0; 1.00] | -14.1 [-9.3; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | cell null draws / mean / max L6M pts / pctile | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | dib_1200 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | plain60/60 | both | 6002 | 2374 | 888 | 1.00 | None /  /  /  | {"2023": -602.0, "2024": 1979.0, "2025": 1051.0, "2026": 7294.0} |
| 2 | cusum_28 | tape.tape_libvol.cmf | {"len": 20} | sym15u | both | 5982 | 1769 | 272 | 0.50 | None /  /  /  | {"2023": -120.0, "2024": -2395.0, "2025": 2657.0, "2026": 5184.0} |
| 3 | time_m_1 | tape.tape_delta.cvd_follow | {"N": 5, "L": 100, "z": 1.0} | plain60/60 | both | 5956 | 1226 | 852 | 1.00 | None /  /  /  | {"2023": -796.0, "2024": -290.0, "2025": -494.0, "2026": 5824.0} |
| 4 | dib_2000 | tape.tape_speed.follow | {"f": 3.0, "L": 200} | sym15u | both | 5833 | 2608 | 339 | 1.00 | None /  /  /  | {"2023": -2.0, "2024": 863.0, "2025": -1813.0, "2026": 5362.0} |
| 5 | dib_700 | trend.trend_ma_hma.price | {"len": 25, "width": 0.0} | sym15u | both | 5667 | 2294 | 509 | 1.00 | None /  /  /  | {"2023": -142.0, "2024": -2173.0, "2025": -1421.0, "2026": 3380.0} |
| 6 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5664 | 2189 | 259 | 1.00 | None /  /  /  | {"2023": 67.0, "2024": 4.0, "2025": -885.0, "2026": 4943.0} |
| 7 | dib_700 | trend.trend_ma_hma.price | {"len": 9, "width": 0.0} | sym15u | both | 5559 | 2206 | 524 | 1.00 | None /  /  /  | {"2023": -188.0, "2024": -434.0, "2025": 455.0, "2026": 2505.0} |
| 8 | vsess_600 | trend.trend_ma_hma.cross_native | {"len": 21, "width": 0.25, "ratio": 3} | sym15u | both | 5549 | 1933 | 385 | 1.00 | None /  /  /  | {"2023": -472.0, "2024": -2419.0, "2025": -726.0, "2026": 5219.0} |
| 9 | vol_350 | tape.tape_speed.follow_native | {"f": 1.5, "L": 900} | sym15u | both | 5460 | 871 | 357 | 1.00 | None /  /  /  | {"2023": -107.0, "2024": 2600.0, "2025": 1886.0, "2026": 4406.0} |
| 10 | cusum_40 | xmarket.xmarket_ym.follow | {"w": 1, "thr": 1.0} | sym15u | both | 5396 | 1872 | 313 | 1.00 | None /  /  /  | {"2023": -565.0, "2024": -544.0, "2025": 2542.0, "2026": 3380.0} |
| 11 | cusum_14 | levels.levels_vwap.reject_native | {"tol": 1.0, "conf": "body"} | sym15u | both | 5299 | 2326 | 269 | 1.00 | None /  /  /  | {"2023": 337.0, "2024": 407.0, "2025": -381.0, "2026": 3705.0} |
| 12 | vsess_80 | trend.trend_libstack.wave_agree | {"set": "slow"} | plain60/60 | both | 5213 | 2187 | 563 | 1.00 | None /  /  /  | {"2023": -76.0, "2024": 999.0, "2025": -605.0, "2026": 6335.0} |
| 13 | vsess_120 | trend.trend_ma_t3.cross | {"len": 4, "width": 2, "hyst": 0.0} | sym15u | both | 5199 | 2335 | 360 | 0.50 | None /  /  /  | {"2023": -534.0, "2024": -2396.0, "2025": -801.0, "2026": 4052.0} |
| 14 | cdr_100 | structure.structure_breakout.fail2 | {"n": 10, "buf": 0.0} | sym15u | both | 5176 | 1963 | 332 | 1.00 | None /  /  /  | {"2023": -643.0, "2024": -1710.0, "2025": -550.0, "2026": 2946.0} |
| 15 | vsess_600 | levels.levels_round.false_break | {"M": 3, "k": 0.5} | sym15u | both | 5082 | 2234 | 510 | 1.00 | None /  /  /  | {"2023": 49.0, "2024": 1726.0, "2025": 822.0, "2026": 2815.0} |
| 16 | vsess_450 | trend.trend_ma_sma.cross | {"len": 20, "width": 2, "hyst": 0.0} | sym15u | both | 5062 | 2598 | 372 | 1.00 | None /  /  /  | {"2023": -329.0, "2024": -3512.0, "2025": 244.0, "2026": 4607.0} |
| 17 | time_m_7 | trend.trend_linreg.thresh | {"len": 10, "width": 1.0} | sym15u | both | 5058 | 1399 | 261 | 0.50 | None /  /  /  | {"2023": 510.0, "2024": 1774.0, "2025": -1940.0, "2026": 5986.0} |
| 18 | time_m_7 | trend.trend_linreg.thresh_native | {"len": 10, "width": 1.0} | sym15u | both | 5058 | 1399 | 261 | 0.50 | None /  /  /  | {"2023": 510.0, "2024": 1774.0, "2025": -1940.0, "2026": 5986.0} |
| 19 | dib_10000 | manual.manual_macd.sigcross_native | {"f": 5, "s": 13, "g": 4} | sym15u | both | 5053 | 3014 | 321 | 1.00 | None /  /  /  | {"2023": -248.0, "2024": -1067.0, "2025": 506.0, "2026": 5514.0} |
| 20 | dib_700 | xmarket.xmarket_ym.follow | {"w": 1, "thr": 1.0} | sym15u | both | 5044 | 2174 | 486 | 1.00 | None /  /  /  | {"2023": -607.0, "2024": 84.0, "2025": 754.0, "2026": 2102.0} |

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
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.06 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.17 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.24 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.05 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.79 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.44 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.05 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.11 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.10 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.45 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.41 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.40 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.57 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.71 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.45 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.09 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.02 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.04 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.05 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.10 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.88 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.89 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.78 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.90 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.63 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.35 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.12 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.18 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.80 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.76 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.79 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.72 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.79 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.37 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.33 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.23 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.03 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.86 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.17 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.06 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.14 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.22 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.29 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.81 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.17 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.63 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.33 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.71 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.26 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.33 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.15 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.06 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.10 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.22 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.13 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.25 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.25 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.51 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.28 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.62 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.16 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.14 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.09 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.30 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.60 |  |
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
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.37 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.89 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.10 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.22 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.98 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.92 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.45 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.13 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.84 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.86 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.87 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.93 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.95 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.65 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.41 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.30 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.83 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.90 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell renko_14 levels.levels_vwap.break_native sym15u L6M 220.7 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell renko_10 manual.manual_macd.histturn plain60/60 L6M 274.0 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell dib_2000 barnative.barnative_speed.burst_fade plain60/60 L6M 269.0 pts/wk vs weak baselines K7 -22.5
