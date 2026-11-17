# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas NOT FINISHED): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-17 22:57Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**Every number on this page comes from: FULL-GRID RESULTS FROM THE FIRST SWEEP (all parameter sets, 7 brackets) - partial coverage.**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-17 22:57Z)
Result files per tag: {"p1rand1": 405, "p1rand2": 390, "p1real": 433, "prof": 3, "real": 1654, "vfyA": 6, "vfyB": 6, "vfyC": 1, "vfyD": 1}. 
Cells scored per session: {"London": 1471197, "NYAM": 1471197, "NYPM": 1471197, "Asia": 1471197}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -21.1 | -0.028 | 956.9 | 0.48 | -42.8 | -14.1 | 167.4 | 173.6 | -188.5 | 0.00 | -31.2 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| agreed | -32.5 | -0.038 | 1549.0 | 0.44 | -42.8 | -14.1 | 167.4 | 173.6 | -199.9 | 0.00 | -31.7 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -13.4 [-166.0; 0.00] |
| bands (native) | -5.5 [-174.1; 0.00] |
| barnative | -50.2 [-190.6; 0.00] |
| confluence | 11.1 [-101.0; 0.00] |
| levels | -14.6 [-94.4; 0.00] |
| levels (native) | -17.4 [-100.7; 0.00] |
| live | 6.4 [-192.2; 0.00] |
| manual | -17.3 [-117.1; 0.00] |
| manual (native) | -15.6 [-30.4; 0.00] |
| momentum | -20.3 [-172.8; 0.00] |
| momentum (native) | -20.3 [-160.1; 0.00] |
| pullback | -21.3 [-182.5; 0.00] |
| pullback (native) | -23.3 [-203.6; 0.00] |
| structure | -35.8 [-178.4; 0.00] |
| structure (native) | 1.1 [-121.9; 0.00] |
| tape | -0.8 [-141.7; 0.00] |
| tape (native) | -17.3 [-126.6; 0.00] |
| trend | -28.3 [-155.5; 0.00] |
| trend (native) | -31.5 [-121.6; 0.00] |
| xmarket | 2.4 [-70.2; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | asym10u/20u | both | 5379 | 1373 | 214 | 1.00 | {"2023": -343.0, "2024": -1307.0, "2025": 598.0, "2026": 6278.0} |
| 2 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | asym10u/20u | both | 5379 | 1373 | 214 | 1.00 | {"2023": -343.0, "2024": -1307.0, "2025": 598.0, "2026": 6278.0} |
| 3 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym8u | both | 5308 | 1670 | 224 | 1.00 | {"2023": -430.0, "2024": -2727.0, "2025": -390.0, "2026": 5912.0} |
| 4 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym8u | both | 5308 | 1670 | 224 | 1.00 | {"2023": -430.0, "2024": -2727.0, "2025": -390.0, "2026": 5912.0} |
| 5 | time_m_2 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym15u/30u | both | 5303 | 2680 | 225 | 0.75 | {"2023": -17.0, "2024": -1574.0, "2025": 176.0, "2026": 4068.0} |
| 6 | time_s_45 | tape.tape_speed.fade | {"f": 3.0, "L": 200} | sym8u | both | 5296 | 2020 | 688 | 0.67 | {"2023": -1383.0, "2024": -46.0, "2025": 668.0, "2026": 6159.0} |
| 7 | time_m_2 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | sym15u | both | 5289 | 2646 | 225 | 0.75 | {"2023": 484.0, "2024": -1796.0, "2025": 1286.0, "2026": 4222.0} |
| 8 | time_m_2 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | sym30u | both | 5257 | 2646 | 225 | 0.75 | {"2023": 43.0, "2024": -844.0, "2025": 403.0, "2026": 3825.0} |
| 9 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | asym15u/30u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 706.0, "2024": -1450.0, "2025": 716.0, "2026": 5567.0} |
| 10 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | asym15u/30u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 706.0, "2024": -1450.0, "2025": 716.0, "2026": 5567.0} |
| 11 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym15u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 381.0, "2024": -914.0, "2025": 447.0, "2026": 5551.0} |
| 12 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | sym30u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 670.0, "2024": -1399.0, "2025": 1224.0, "2026": 5494.0} |
| 13 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym15u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 381.0, "2024": -914.0, "2025": 447.0, "2026": 5551.0} |
| 14 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | sym30u | both | 5249 | 1296 | 212 | 1.00 | {"2023": 670.0, "2024": -1399.0, "2025": 1224.0, "2026": 5494.0} |
| 15 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 5109 | 2777 | 271 | 0.60 | {"2023": -338.0, "2024": -1054.0, "2025": -1804.0, "2026": 4824.0} |
| 16 | time_m_2 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym10u/20u | both | 5103 | 2832 | 236 | 0.75 | {"2023": -492.0, "2024": -1849.0, "2025": -140.0, "2026": 3965.0} |
| 17 | time_m_4 | levels.levels_vwap.break_native | {"n": 3, "k": 0.0} | asym20u/10u | both | 5102 | 1208 | 212 | 1.00 | {"2023": 912.0, "2024": -1256.0, "2025": 521.0, "2026": 5782.0} |
| 18 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.0} | asym20u/10u | both | 5102 | 1208 | 212 | 1.00 | {"2023": 912.0, "2024": -1256.0, "2025": 521.0, "2026": 5782.0} |
| 19 | time_m_2 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym20u/10u | both | 5045 | 2578 | 234 | 0.75 | {"2023": 306.0, "2024": -2665.0, "2025": 997.0, "2026": 4264.0} |
| 20 | time_m_4 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | sym8u | both | 4977 | 1554 | 232 | 1.00 | {"2023": -138.0, "2024": -2125.0, "2025": 299.0, "2026": 5586.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 17.0 | 0.018 | 511.7 | 0.53 | 74.1 | 119.9 |  |  |  |  | 0.4 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 22.4 | 0.025 | 517.8 | 0.53 | 113.2 | 119.9 |  |  |  |  | 1.0 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 17.9 [; ] |
| bands (native) | 50.0 [; ] |
| barnative | -10.6 [; ] |
| confluence | 42.5 [; ] |
| levels | -14.2 [; ] |
| levels (native) | -7.4 [; ] |
| live | -18.7 [; ] |
| manual | 0.6 [; ] |
| manual (native) | 14.3 [; ] |
| momentum | 49.0 [; ] |
| momentum (native) | 49.0 [; ] |
| pullback | -13.0 [; ] |
| pullback (native) | 1.9 [; ] |
| structure | -19.8 [; ] |
| structure (native) | 8.9 [; ] |
| tape | 8.7 [; ] |
| tape (native) | 16.3 [; ] |
| trend | 6.9 [; ] |
| trend (native) | 6.9 [; ] |
| xmarket | -26.1 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 7209 | 1055 | 498 | 1.00 | {"2023": 138.0, "2024": -1461.0, "2025": -774.0, "2026": 7274.0} |
| 2 | tm10 | bands.bands_regchan.break_stderr | {"n": 40, "k": 2.5} | sym8u | both | 7168 | 4001 | 866 | 1.00 | {"2023": 422.0, "2024": 630.0, "2025": 1668.0, "2026": 2987.0} |
| 3 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym15u | both | 7078 | 1303 | 505 | 1.00 | {"2023": 213.0, "2024": -421.0, "2025": 4075.0, "2026": 5878.0} |
| 4 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym8u | both | 6921 | 2747 | 391 | 1.00 | {"2023": 231.0, "2024": 57.0, "2025": -1815.0, "2026": 9448.0} |
| 5 | time_m_4 | tape.tape_delta.fade_sm | {"L": 200, "z": 1.0, "sm": 3} | sym8u | both | 6815 | 2643 | 395 | 1.00 | {"2023": 948.0, "2024": 3089.0, "2025": 1815.0, "2026": 9270.0} |
| 6 | time_m_4 | tape.tape_delta.fade | {"L": 200, "z": 1.0} | sym8u | both | 6785 | 2965 | 434 | 1.00 | {"2023": -440.0, "2024": 231.0, "2025": 2951.0, "2026": 9340.0} |
| 7 | time_s_15 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | sym30u | both | 6760 | 635 | 479 | 1.00 | {"2023": 1330.0, "2024": -1354.0, "2025": -3112.0, "2026": 4179.0} |
| 8 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | sym30u | both | 6745 | 438 | 495 | 1.00 | {"2023": -1361.0, "2024": -1132.0, "2025": -1397.0, "2026": 6640.0} |
| 9 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | asym10u/20u | both | 6733 | 2241 | 390 | 1.00 | {"2023": -564.0, "2024": 173.0, "2025": -3180.0, "2026": 9360.0} |
| 10 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym15u | both | 6733 | 2241 | 390 | 1.00 | {"2023": 483.0, "2024": 206.0, "2025": -2823.0, "2026": 9680.0} |
| 11 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | asym20u/10u | both | 6733 | 2241 | 390 | 1.00 | {"2023": 156.0, "2024": -878.0, "2025": -2282.0, "2026": 9457.0} |
| 12 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | asym15u/30u | both | 6733 | 2241 | 390 | 1.00 | {"2023": 403.0, "2024": 92.0, "2025": -2810.0, "2026": 9680.0} |
| 13 | time_m_4 | tape.tape_delta.fade | {"L": 100, "z": 1.5} | sym30u | both | 6733 | 2241 | 390 | 1.00 | {"2023": 567.0, "2024": -297.0, "2025": -2982.0, "2026": 9680.0} |
| 14 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym30u | both | 6720 | 1021 | 501 | 1.00 | {"2023": -493.0, "2024": -878.0, "2025": 4115.0, "2026": 5311.0} |
| 15 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym20u/10u | both | 6549 | 1906 | 526 | 0.75 | {"2023": 136.0, "2024": -551.0, "2025": -39.0, "2026": 4795.0} |
| 16 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | asym15u/30u | both | 6545 | 547 | 496 | 1.00 | {"2023": -24.0, "2024": -1420.0, "2025": -735.0, "2026": 6609.0} |
| 17 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym15u/30u | both | 6526 | 905 | 502 | 0.75 | {"2023": 798.0, "2024": 419.0, "2025": 4575.0, "2026": 5333.0} |
| 18 | time_s_15 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | asym15u/30u | both | 6438 | 1129 | 528 | 1.00 | {"2023": -220.0, "2024": -1566.0, "2025": -3077.0, "2026": 4770.0} |
| 19 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 6347 | 2866 | 507 | 1.00 | {"2023": 256.0, "2024": 1530.0, "2025": 321.0, "2026": 5007.0} |
| 20 | time_m_4 | tape.tape_delta.fade | {"L": 50, "z": 1.0} | sym8u | both | 6342 | 3516 | 403 | 1.00 | {"2023": 201.0, "2024": -1924.0, "2025": 982.0, "2026": 9751.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 11.0 | 0.014 | 607.6 | 0.51 | -24.0 | 75.2 |  |  |  |  | -13.2 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| agreed | 10.0 | 0.012 | 613.8 | 0.49 | -30.2 | 61.8 |  |  |  |  | -11.4 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -2.5 [; ] |
| bands (native) | -15.2 [; ] |
| barnative | 29.0 [; ] |
| confluence | -57.8 [; ] |
| levels | -15.1 [; ] |
| levels (native) | -39.4 [; ] |
| live | -30.2 [; ] |
| manual | 2.6 [; ] |
| manual (native) | -17.8 [; ] |
| momentum | -9.2 [; ] |
| momentum (native) | -9.2 [; ] |
| pullback | -38.7 [; ] |
| pullback (native) | -20.2 [; ] |
| structure | 12.2 [; ] |
| structure (native) | 23.1 [; ] |
| tape | -15.7 [; ] |
| tape (native) | -30.4 [; ] |
| trend | 26.8 [; ] |
| trend (native) | 25.2 [; ] |
| xmarket | -3.4 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm10 | trend.trend_ma_hma.cross | {"len": 21, "width": 4, "hyst": 0.0} | plain60/60 | both | 6076 | 1146 | 908 | 1.00 | {"2023": -1233.0, "2024": -756.0, "2025": 2796.0, "2026": 6659.0} |
| 2 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.08} | plain60/60 | both | 5867 | 1722 | 855 | 1.00 | {"2023": -61.0, "2024": -81.0, "2025": -154.0, "2026": 5010.0} |
| 3 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.12} | plain60/60 | both | 5838 | 2593 | 867 | 0.75 | {"2023": 500.0, "2024": 1370.0, "2025": 392.0, "2026": 4266.0} |
| 4 | tm10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.05} | plain60/60 | both | 5699 | 1614 | 855 | 0.75 | {"2023": -52.0, "2024": -38.0, "2025": 410.0, "2026": 4841.0} |
| 5 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym20u/10u | both | 5651 | 1260 | 278 | 1.00 | {"2023": -448.0, "2024": 3799.0, "2025": 1764.0, "2026": 5365.0} |
| 6 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym15u/30u | both | 5547 | 1156 | 276 | 1.00 | {"2023": -554.0, "2024": 3950.0, "2025": 1587.0, "2026": 5256.0} |
| 7 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym30u | both | 5547 | 1156 | 276 | 1.00 | {"2023": -571.0, "2024": 3918.0, "2025": 1587.0, "2026": 5256.0} |
| 8 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym15u | both | 5547 | 1156 | 276 | 1.00 | {"2023": -299.0, "2024": 3950.0, "2025": 1587.0, "2026": 5256.0} |
| 9 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym10u/20u | both | 5547 | 1156 | 276 | 1.00 | {"2023": -380.0, "2024": 3758.0, "2025": 1738.0, "2026": 5306.0} |
| 10 | time_m_2 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym8u | both | 5453 | 1177 | 278 | 1.00 | {"2023": -640.0, "2024": 3766.0, "2025": 1918.0, "2026": 5030.0} |
| 11 | time_s_15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | both | 5418 | 2146 | 927 | 1.00 | {"2023": -2269.0, "2024": -2257.0, "2025": 207.0, "2026": 4647.0} |
| 12 | tm10 | trend.trend_ma_sma.cross_native | {"len": 5, "width": 0.25, "ratio": 3} | plain60/60 | both | 5405 | 2892 | 882 | 1.00 | {"2023": -576.0, "2024": 932.0, "2025": 1778.0, "2026": 4975.0} |
| 13 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym20u/10u | both | 5372 | 1078 | 277 | 1.00 | {"2023": 289.0, "2024": 2792.0, "2025": 1372.0, "2026": 5024.0} |
| 14 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym10u/20u | both | 5316 | 974 | 275 | 1.00 | {"2023": 290.0, "2024": 2766.0, "2025": 1163.0, "2026": 5035.0} |
| 15 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym15u | both | 5280 | 974 | 275 | 1.00 | {"2023": 172.0, "2024": 2975.0, "2025": 886.0, "2026": 4931.0} |
| 16 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | asym15u/30u | both | 5280 | 974 | 275 | 1.00 | {"2023": 105.0, "2024": 3020.0, "2025": 886.0, "2026": 4931.0} |
| 17 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym30u | both | 5268 | 974 | 275 | 1.00 | {"2023": 88.0, "2024": 2940.0, "2025": 886.0, "2026": 4920.0} |
| 18 | time_s_15 | momentum.momentum_squeeze.hist_turn | {"len": 14, "wd": 3} | plain60/60 | both | 5249 | 2959 | 976 | 1.00 | {"2023": 571.0, "2024": -898.0, "2025": -327.0, "2026": 6081.0} |
| 19 | time_s_15 | momentum.momentum_squeeze.hist_turn_native | {"len": 14, "wd": 3} | plain60/60 | both | 5249 | 2959 | 976 | 1.00 | {"2023": 571.0, "2024": -898.0, "2025": -327.0, "2026": 6081.0} |
| 20 | tm120 | bands.bands_regchan.break_stderr_native | {"clk": 20, "k": 2.0} | sym8u | both | 5236 | 995 | 277 | 1.00 | {"2023": -130.0, "2024": 2840.0, "2025": 1562.0, "2026": 4840.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 23.9 | -0.001 | 317.8 | 0.56 | -0.4 | -44.4 |  |  |  |  | 9.9 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 18.9 | -0.006 | 317.4 | 0.54 | -59.5 | -172.5 |  |  |  |  | 9.7 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 34.7 [; ] |
| bands (native) | 12.8 [; ] |
| barnative | -28.4 [; ] |
| confluence | -4.9 [; ] |
| levels | 8.5 [; ] |
| levels (native) | -9.9 [; ] |
| live | -5.0 [; ] |
| manual | -18.7 [; ] |
| manual (native) | 1.8 [; ] |
| momentum | -11.1 [; ] |
| momentum (native) | -11.5 [; ] |
| pullback | -2.3 [; ] |
| pullback (native) | 0.3 [; ] |
| structure | 4.1 [; ] |
| structure (native) | -2.2 [; ] |
| tape | 14.5 [; ] |
| tape (native) | 17.5 [; ] |
| trend | 12.2 [; ] |
| trend (native) | 7.8 [; ] |
| xmarket | -21.3 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | sym30u | both | 7068 | 2287 | 282 | 1.00 | {"2023": -240.0, "2024": 569.0, "2025": 250.0, "2026": 5190.0} |
| 2 | time_m_1 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | sym30u | both | 6542 | 2067 | 279 | 0.75 | {"2023": -299.0, "2024": 2.0, "2025": 681.0, "2026": 4538.0} |
| 3 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | asym15u/30u | both | 6437 | 1832 | 309 | 0.80 | {"2023": -566.0, "2024": 879.0, "2025": 380.0, "2026": 4283.0} |
| 4 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | sym15u | both | 6113 | 2058 | 333 | 0.80 | {"2023": -709.0, "2024": 986.0, "2025": -693.0, "2026": 4091.0} |
| 5 | time_m_1 | momentum.momentum_willr.revert_native | {"len": 7, "lvl": 10} | sym30u | both | 6024 | 3548 | 362 | 1.00 | {"2023": -354.0, "2024": -923.0, "2025": -965.0, "2026": 5279.0} |
| 6 | time_m_1 | momentum.momentum_willr.revert | {"len": 7, "lvl": 10} | sym30u | both | 6024 | 3548 | 362 | 1.00 | {"2023": -354.0, "2024": -923.0, "2025": -965.0, "2026": 5279.0} |
| 7 | time_s_15 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.0} | sym30u | both | 6019 | 1477 | 515 | 0.50 | {"2023": -164.0, "2024": -901.0, "2025": -3766.0, "2026": 5196.0} |
| 8 | time_s_15 | trend.trend_macd.hist_turn_native | {"len": 12, "width": 0.0} | sym30u | both | 6019 | 1477 | 515 | 0.50 | {"2023": -164.0, "2024": -901.0, "2025": -3766.0, "2026": 5196.0} |
| 9 | time_s_45 | trend.trend_adx_di.adx_cross | {"len": 10, "width": 20} | sym30u | both | 5818 | 1919 | 348 | 0.80 | {"2023": -89.0, "2024": -532.0, "2025": -571.0, "2026": 5018.0} |
| 10 | time_s_15 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.0} | asym15u/30u | both | 5732 | 2286 | 696 | 0.50 | {"2023": -417.0, "2024": 1194.0, "2025": -1589.0, "2026": 5576.0} |
| 11 | time_s_15 | trend.trend_macd.hist_turn_native | {"len": 12, "width": 0.0} | asym15u/30u | both | 5732 | 2286 | 696 | 0.50 | {"2023": -417.0, "2024": 1194.0, "2025": -1589.0, "2026": 5576.0} |
| 12 | tm60 | momentum.momentum_willr.revert_native | {"len": 7, "lvl": 10} | sym30u | both | 5719 | 3601 | 363 | 0.50 | {"2023": -241.0, "2024": -974.0, "2025": -1078.0, "2026": 4861.0} |
| 13 | tm60 | momentum.momentum_willr.revert | {"len": 7, "lvl": 10} | sym30u | both | 5719 | 3601 | 363 | 0.50 | {"2023": -241.0, "2024": -974.0, "2025": -1078.0, "2026": 4861.0} |
| 14 | tm60 | momentum.momentum_stoch.revert | {"len": 5, "lvl": 15} | sym30u | both | 5625 | 4078 | 371 | 0.50 | {"2023": -352.0, "2024": -358.0, "2025": -1686.0, "2026": 5159.0} |
| 15 | tm60 | momentum.momentum_stoch.revert_native | {"len": 5, "lvl": 15} | sym30u | both | 5625 | 4078 | 371 | 0.50 | {"2023": -352.0, "2024": -358.0, "2025": -1686.0, "2026": 5159.0} |
| 16 | time_m_1 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | asym15u/30u | both | 5620 | 1552 | 309 | 0.75 | {"2023": -502.0, "2024": 301.0, "2025": 739.0, "2026": 3336.0} |
| 17 | time_m_1 | momentum.momentum_stoch.revert | {"len": 5, "lvl": 15} | sym30u | both | 5558 | 3969 | 372 | 1.00 | {"2023": -447.0, "2024": -241.0, "2025": -1538.0, "2026": 4926.0} |
| 18 | time_m_1 | momentum.momentum_stoch.revert_native | {"len": 5, "lvl": 15} | sym30u | both | 5558 | 3969 | 372 | 1.00 | {"2023": -447.0, "2024": -241.0, "2025": -1538.0, "2026": 4926.0} |
| 19 | time_s_45 | tape.tape_delta.cvd_follow | {"N": 5, "L": 100, "z": 1.5} | plain60/60 | both | 5501 | 3095 | 797 | 0.75 | {"2023": -904.0, "2024": 276.0, "2025": -1824.0, "2026": 4474.0} |
| 20 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 5, "k": 1.0} | sym8u | both | 5480 | 2797 | 304 | 0.67 | {"2023": -941.0, "2024": -2057.0, "2025": -423.0, "2026": 4005.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.05 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.98 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.07 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.32 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.10 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.09 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.87 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.87 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.03 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.67 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.27 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.02 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.82 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.82 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.22 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 0.99 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.96 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.92 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.68 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.64 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.24 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.69 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.64 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.83 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.16 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.15 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.86 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.81 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.03 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.11 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.16 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.03 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.83 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.32 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.03 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.06 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.06 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.33 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.30 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.29 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.44 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.76 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.33 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.06 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.01 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.02 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.02 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.06 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.91 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.92 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.82 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.92 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.68 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.24 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.07 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.12 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.84 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.80 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.83 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.76 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.83 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.26 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.23 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.19 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.04 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.86 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.14 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.07 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.12 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.18 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.22 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.82 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.14 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.68 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.26 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.73 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.21 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.26 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.13 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.07 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.10 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.18 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.12 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.20 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.20 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.40 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.22 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.67 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.14 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.12 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.09 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.24 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.66 |  |
| Asia | K7 | tm180 | LIVE | 72.1 | 61.6 | 11.3 | 978.2 | 0.56 | 683 | 0.99 |  |
| Asia | K7 | tm60 | neighbour | 82.2 | -34.7 | 23.8 | 585.9 | 0.57 | 896 | 0.99 |  |
| Asia | K7 | tm120 | neighbour | 98.9 | 36.5 | 26.2 | 556.4 | 0.56 | 759 | 1.00 |  |
| Asia | K7 | tm240 | neighbour | 115.3 | 117.7 | 38.9 | 543.2 | 0.65 | 635 | 1.00 |  |
| Asia | K7 | tm300 | neighbour | 97.3 | 106.9 | 35.3 | 360.3 | 0.60 | 570 | 1.00 |  |
| Asia | M7 | tm60 | LIVE | 80.8 | 126.3 | 38.6 | 423.4 | 0.63 | 593 | 0.99 |  |
| Asia | M7 | tm30 | neighbour | 90.3 | 89.8 | 35.0 | 444.9 | 0.65 | 795 | 0.99 |  |
| Asia | M7 | tm45 | neighbour | 49.4 | 102.7 | 29.0 | 480.3 | 0.65 | 697 | 0.96 |  |
| Asia | M7 | tm120 | neighbour | 130.5 | 160.7 | 34.4 | 344.2 | 0.59 | 438 | 1.00 |  |
| Asia | M7 | tm180 | neighbour | 50.4 | 113.2 | 25.0 | 304.0 | 0.59 | 339 | 0.96 |  |
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.92 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.34 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.91 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.11 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.22 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.98 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.94 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.41 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.13 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.88 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.89 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.90 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.94 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.96 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.72 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.37 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.29 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.86 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.92 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell time_m_4 levels.levels_vwap.break_native asym10u/20u L6M 206.9 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell tm60 levels.levels_vwap_bands.reject sym15u L6M 277.3 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell tm10 trend.trend_ma_hma.cross plain60/60 L6M 233.7 pts/wk vs weak baselines K7 -22.5
