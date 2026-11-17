# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas rand1,rand2,rand3,rand4,rand5): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-17 21:53Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-17 21:53Z)
Result files per tag: {"rand1": 901, "rand2": 882, "rand3": 856, "rand4": 810, "rand5": 722, "real": 1063}. 
Cells scored per session: {"London": 796131, "NYAM": 887964, "NYPM": 891681, "Asia": 891681}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 2.8 | 0.018 | 343.3 | 0.56 | -31.4 | -82.5 | 172.6 | 189.9 | -169.8 | 0.00 | -22.0 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| agreed | 0.5 | 0.013 | 345.2 | 0.53 | -29.4 | -82.5 | 172.6 | 189.9 | -172.1 | 0.00 | -21.7 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -17.2 [-179.4; 0.00] |
| bands (native) | -19.7 [-170.2; 0.00] |
| barnative | -26.8 [-161.1; 0.00] |
| confluence | -4.6 [-131.5; 0.00] |
| levels | -24.4 [-75.5; 0.00] |
| levels (native) | -22.6 [-110.2; 0.00] |
| live | 6.4 [-186.3; 0.00] |
| manual | -31.5 [-148.1; 0.00] |
| manual (native) | -26.0 [-22.3; 0.00] |
| momentum | -9.2 [-150.8; 0.00] |
| momentum (native) | -9.2 [-158.2; 0.00] |
| pullback | 13.8 [-156.2; 0.00] |
| pullback (native) | -35.5 [-212.2; 0.00] |
| structure | -6.7 [-157.0; 0.00] |
| structure (native) | -4.5 [-129.3; 0.00] |
| tape | -34.1 [-182.3; 0.00] |
| tape (native) | -35.4 [-125.7; 0.00] |
| trend | -5.3 [-128.5; 0.00] |
| trend (native) | -12.7 [-104.8; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 5109 | 2777 | 271 | 0.60 | {"2023": -338.0, "2024": -1054.0, "2025": -1804.0, "2026": 4824.0} |
| 2 | time_m_5 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym10u/20u | both | 4789 | 2432 | 218 | 0.50 | {"2023": -448.0, "2024": -213.0, "2025": -885.0, "2026": 3730.0} |
| 3 | tm60 | momentum.momentum_squeeze.fire_slope_native | {"len": 20, "wd": 1.5} | sym15u | both | 4739 | 2256 | 241 | 1.00 | {"2023": -25.0, "2024": 77.0, "2025": -3029.0, "2026": 5113.0} |
| 4 | tm60 | momentum.momentum_squeeze.fire_slope | {"len": 20, "wd": 1.5} | sym15u | both | 4739 | 2256 | 241 | 1.00 | {"2023": -25.0, "2024": 77.0, "2025": -3029.0, "2026": 5113.0} |
| 5 | time_m_5 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | sym30u | both | 4734 | 2423 | 218 | 0.50 | {"2023": 182.0, "2024": -264.0, "2025": 368.0, "2026": 3577.0} |
| 6 | time_m_5 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | sym15u | both | 4734 | 2423 | 218 | 0.50 | {"2023": -7.0, "2024": -397.0, "2025": 691.0, "2026": 3619.0} |
| 7 | time_m_5 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym15u/30u | both | 4734 | 2423 | 218 | 0.50 | {"2023": 203.0, "2024": -505.0, "2025": 153.0, "2026": 3580.0} |
| 8 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | asym15u/30u | both | 4606 | 1637 | 208 | 1.00 | {"2023": -426.0, "2024": -1275.0, "2025": -309.0, "2026": 4377.0} |
| 9 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | sym30u | both | 4606 | 1637 | 208 | 1.00 | {"2023": -419.0, "2024": -967.0, "2025": 177.0, "2026": 4267.0} |
| 10 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | sym15u | both | 4606 | 1637 | 208 | 1.00 | {"2023": -508.0, "2024": -1068.0, "2025": -329.0, "2026": 4340.0} |
| 11 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | asym10u/20u | both | 4603 | 1634 | 208 | 1.00 | {"2023": -751.0, "2024": -1254.0, "2025": -276.0, "2026": 4604.0} |
| 12 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | asym20u/10u | both | 4578 | 1612 | 208 | 1.00 | {"2023": -352.0, "2024": -1260.0, "2025": 623.0, "2026": 4342.0} |
| 13 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym15u | both | 4560 | 2385 | 262 | 0.80 | {"2023": -396.0, "2024": -1110.0, "2025": -2691.0, "2026": 4718.0} |
| 14 | tm300 | levels.levels_vwap.break | {"n": 3, "k": 0.25} | sym8u | both | 4524 | 1630 | 213 | 1.00 | {"2023": -1760.0, "2024": -2092.0, "2025": -187.0, "2026": 4661.0} |
| 15 | tm180 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym8u | both | 4490 | 1631 | 240 | 0.75 | {"2023": -989.0, "2024": -1388.0, "2025": -727.0, "2026": 5090.0} |
| 16 | time_m_5 | levels.levels_vwap.break_native | {"n": 1, "k": 0.5} | asym20u/10u | both | 4457 | 2153 | 218 | 0.50 | {"2023": -265.0, "2024": -869.0, "2025": 1756.0, "2026": 3343.0} |
| 17 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4436 | 1366 | 530 | 1.00 | {"2023": -709.0, "2024": -651.0, "2025": 1201.0, "2026": 3773.0} |
| 18 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym15u/30u | both | 4418 | 2391 | 262 | 0.80 | {"2023": -545.0, "2024": -702.0, "2025": -3036.0, "2026": 4079.0} |
| 19 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym30u | both | 4418 | 2391 | 262 | 0.80 | {"2023": -789.0, "2024": 471.0, "2025": -2414.0, "2026": 4037.0} |
| 20 | tm60 | momentum.momentum_squeeze.fire_slope_native | {"len": 20, "wd": 1.5} | asym15u/30u | both | 4397 | 2111 | 232 | 1.00 | {"2023": 343.0, "2024": -1167.0, "2025": -4281.0, "2026": 5076.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -3.0 | 0.012 | 1036.7 | 0.46 | 44.1 | 124.3 | 367.7 | 398.6 | -370.7 | 0.00 | 39.0 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -11.8 | 0.001 | 1057.6 | 0.43 | -11.1 | -80.1 | 367.7 | 398.6 | -379.6 | 0.00 | 27.5 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 20.0 [-244.7; 0.00] |
| bands (native) | 15.3 [-256.8; 0.00] |
| barnative | -29.8 [-274.6; 0.00] |
| confluence | 63.1 [-100.0; 0.00] |
| levels | -24.7 [-173.0; 0.00] |
| levels (native) | -7.6 [-165.7; 0.00] |
| live | -18.7 [-344.6; 0.00] |
| manual | 1.8 [-165.4; 0.00] |
| manual (native) | -35.6 [-48.8; 0.00] |
| momentum | 27.0 [-189.7; 0.00] |
| momentum (native) | 27.0 [-168.4; 0.00] |
| pullback | -35.2 [-380.1; 0.00] |
| pullback (native) | 23.4 [-333.4; 0.00] |
| structure | 9.6 [-219.6; 0.00] |
| structure (native) | -2.9 [-233.1; 0.00] |
| tape | 21.1 [-210.6; 0.00] |
| tape (native) | -9.9 [-255.1; 0.00] |
| trend | -42.0 [-233.5; 0.00] |
| trend (native) | -23.7 [-115.4; 0.00] |
| xmarket | -26.1 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | sym15u | both | 7209 | 1055 | 498 | 1.00 | {"2023": 138.0, "2024": -1461.0, "2025": -774.0, "2026": 7274.0} |
| 2 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym15u | both | 7078 | 1303 | 505 | 1.00 | {"2023": 213.0, "2024": -421.0, "2025": 4075.0, "2026": 5878.0} |
| 3 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | sym30u | both | 6745 | 438 | 495 | 1.00 | {"2023": -1361.0, "2024": -1132.0, "2025": -1397.0, "2026": 6640.0} |
| 4 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym30u | both | 6720 | 1021 | 501 | 1.00 | {"2023": -493.0, "2024": -878.0, "2025": 4115.0, "2026": 5311.0} |
| 5 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym20u/10u | both | 6549 | 1906 | 526 | 0.75 | {"2023": 136.0, "2024": -551.0, "2025": -39.0, "2026": 4795.0} |
| 6 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | asym15u/30u | both | 6545 | 547 | 496 | 1.00 | {"2023": -24.0, "2024": -1420.0, "2025": -735.0, "2026": 6609.0} |
| 7 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym15u/30u | both | 6526 | 905 | 502 | 0.75 | {"2023": 798.0, "2024": 419.0, "2025": 4575.0, "2026": 5333.0} |
| 8 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "body"} | asym10u/20u | both | 6347 | 2866 | 507 | 1.00 | {"2023": 256.0, "2024": 1530.0, "2025": 321.0, "2026": 5007.0} |
| 9 | tm60 | levels.levels_vwap_bands.reject | {"tol": 1.0, "conf": "close"} | asym20u/10u | both | 6310 | 870 | 521 | 1.00 | {"2023": 274.0, "2024": -1741.0, "2025": -3957.0, "2026": 6951.0} |
| 10 | time_s_15 | trend.trend_ma_hma.cross | {"len": 13, "width": 3, "hyst": 0.0} | asym20u/10u | both | 6221 | 2504 | 578 | 0.50 | {"2023": -1167.0, "2024": -2783.0, "2025": 2848.0, "2026": 4676.0} |
| 11 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 6151 | 2822 | 348 | 0.50 | {"2023": 520.0, "2024": -1188.0, "2025": 336.0, "2026": 4836.0} |
| 12 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 58.0, "2024": -1481.0, "2025": -181.0, "2026": 4722.0} |
| 13 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 311.0, "2024": -1331.0, "2025": -406.0, "2026": 4722.0} |
| 14 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 614.0, "2024": -1423.0, "2025": -422.0, "2026": 4722.0} |
| 15 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 6138 | 2822 | 348 | 0.50 | {"2023": -959.0, "2024": -1653.0, "2025": -153.0, "2026": 5234.0} |
| 16 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym10u/20u | both | 6077 | 1376 | 517 | 0.75 | {"2023": -895.0, "2024": -568.0, "2025": 2689.0, "2026": 4085.0} |
| 17 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | plain60/60 | both | 6062 | 3184 | 1446 | 1.00 | {"2023": -545.0, "2024": -1661.0, "2025": -1603.0, "2026": 5644.0} |
| 18 | tm60 | levels.levels_vwap_bands.break_native | {"n": 1, "k": 0.5} | asym20u/10u | both | 5990 | 1743 | 499 | 1.00 | {"2023": -59.0, "2024": -263.0, "2025": 1483.0, "2026": 6262.0} |
| 19 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 5976 | 797 | 539 | 1.00 | {"2023": -2316.0, "2024": -537.0, "2025": -1936.0, "2026": 5304.0} |
| 20 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5939 | 2672 | 349 | 0.50 | {"2023": -1064.0, "2024": -1551.0, "2025": 841.0, "2026": 5025.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -13.0 | -0.004 | 913.8 | 0.49 | -19.8 | 26.9 | 219.5 | 238.2 | -232.4 | 0.00 | -13.0 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -19.2 | -0.005 | 773.8 | 0.48 | -91.0 | -127.3 | 219.5 | 238.2 | -238.7 | 0.00 | -8.3 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -29.4 [-238.5; 0.00] |
| bands (native) | -45.5 [-249.5; 0.00] |
| barnative | 2.6 [-193.3; 0.00] |
| confluence | -11.2 [-171.4; 0.00] |
| levels | -20.0 [-113.1; 0.00] |
| levels (native) | -59.7 [-156.1; 0.00] |
| live | -30.2 [-255.0; 0.00] |
| manual | -2.2 [-130.9; 0.00] |
| manual (native) | 22.1 [3.0; 0.60] |
| momentum | -7.9 [-175.4; 0.00] |
| momentum (native) | -7.9 [-157.1; 0.00] |
| pullback | -3.6 [-224.1; 0.00] |
| pullback (native) | -50.1 [-270.4; 0.00] |
| structure | -17.4 [-203.3; 0.00] |
| structure (native) | -28.1 [-231.4; 0.00] |
| tape | -41.1 [-205.3; 0.00] |
| tape (native) | -54.9 [-235.0; 0.00] |
| trend | 2.2 [-130.8; 0.00] |
| trend (native) | -16.2 [-77.9; 0.00] |
| xmarket | -3.4 [-78.1; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_s_15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | both | 5418 | 2146 | 927 | 1.00 | {"2023": -2269.0, "2024": -2257.0, "2025": 207.0, "2026": 4647.0} |
| 2 | time_s_15 | momentum.momentum_squeeze.hist_turn | {"len": 14, "wd": 3} | plain60/60 | both | 5249 | 2959 | 976 | 1.00 | {"2023": 571.0, "2024": -898.0, "2025": -327.0, "2026": 6081.0} |
| 3 | time_s_15 | momentum.momentum_squeeze.hist_turn_native | {"len": 14, "wd": 3} | plain60/60 | both | 5249 | 2959 | 976 | 1.00 | {"2023": 571.0, "2024": -898.0, "2025": -327.0, "2026": 6081.0} |
| 4 | time_s_15 | trend.trend_macd.hist_turn | {"len": 26, "width": 0.01} | sym8u | both | 5184 | 2653 | 957 | 1.00 | {"2023": -2549.0, "2024": -580.0, "2025": -510.0, "2026": 5491.0} |
| 5 | time_s_15 | trend.trend_macd.hist_turn_native | {"len": 26, "width": 0.01} | sym8u | both | 5184 | 2653 | 957 | 1.00 | {"2023": -2549.0, "2024": -580.0, "2025": -510.0, "2026": 5491.0} |
| 6 | time_s_15 | trend.trend_adx_di.adx_cross | {"len": 7, "width": 25} | sym15u | both | 5136 | 2018 | 403 | 1.00 | {"2023": 984.0, "2024": 21.0, "2025": 266.0, "2026": 5157.0} |
| 7 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym10u/20u | short | 4985 | 1727 | 203 | 1.00 | {"2023": 136.0, "2024": -457.0, "2025": 823.0, "2026": 5375.0} |
| 8 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym15u/30u | short | 4985 | 1727 | 203 | 1.00 | {"2023": 94.0, "2024": -471.0, "2025": 823.0, "2026": 5375.0} |
| 9 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym15u | short | 4985 | 1727 | 203 | 1.00 | {"2023": 94.0, "2024": -471.0, "2025": 823.0, "2026": 5375.0} |
| 10 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym30u | short | 4985 | 1727 | 203 | 1.00 | {"2023": 92.0, "2024": -471.0, "2025": 823.0, "2026": 5375.0} |
| 11 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | asym20u/10u | short | 4985 | 1727 | 203 | 1.00 | {"2023": 99.0, "2024": -477.0, "2025": 823.0, "2026": 5375.0} |
| 12 | tm600 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "close"} | sym8u | short | 4981 | 1727 | 203 | 1.00 | {"2023": 142.0, "2024": -557.0, "2025": 821.0, "2026": 5371.0} |
| 13 | time_s_15 | trend.trend_ma_hma.price_native | {"len": 25, "width": 1.0} | asym20u/10u | both | 4969 | 3179 | 501 | 0.67 | {"2023": -737.0, "2024": 231.0, "2025": 1147.0, "2026": 3634.0} |
| 14 | time_s_15 | trend.trend_adx_di.adx_cross | {"len": 7, "width": 25} | asym10u/20u | both | 4797 | 1900 | 452 | 1.00 | {"2023": 204.0, "2024": -1133.0, "2025": -1794.0, "2026": 3747.0} |
| 15 | time_s_15 | trend.trend_adx_di.adx_cross | {"len": 7, "width": 25} | asym15u/30u | both | 4741 | 2448 | 355 | 1.00 | {"2023": -408.0, "2024": 706.0, "2025": 1499.0, "2026": 5358.0} |
| 16 | tm60 | momentum.momentum_rsi.mom_native | {"len": 21, "lvl": 55} | sym15u | both | 4723 | 1337 | 257 | 0.75 | {"2023": -904.0, "2024": 597.0, "2025": -265.0, "2026": 5642.0} |
| 17 | tm60 | momentum.momentum_rsi.mom | {"len": 21, "lvl": 55} | sym15u | both | 4723 | 1337 | 257 | 0.75 | {"2023": -904.0, "2024": 597.0, "2025": -265.0, "2026": 5642.0} |
| 18 | tm60 | momentum.momentum_rsi.mom_native | {"len": 21, "lvl": 55} | sym30u | both | 4721 | 1336 | 257 | 0.75 | {"2023": -733.0, "2024": 714.0, "2025": -102.0, "2026": 5611.0} |
| 19 | tm60 | momentum.momentum_rsi.mom_native | {"len": 21, "lvl": 55} | asym15u/30u | both | 4721 | 1336 | 257 | 0.75 | {"2023": -667.0, "2024": 733.0, "2025": -225.0, "2026": 5637.0} |
| 20 | tm60 | momentum.momentum_rsi.mom | {"len": 21, "lvl": 55} | sym30u | both | 4721 | 1336 | 257 | 0.75 | {"2023": -733.0, "2024": 714.0, "2025": -102.0, "2026": 5611.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 10.1 | -0.008 | 339.9 | 0.54 | -30.5 | -109.7 | 198.7 | 209.9 | -188.6 | 0.00 | 17.2 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 8.8 | -0.007 | 361.8 | 0.54 | -30.5 | -109.7 | 198.7 | 209.9 | -189.9 | 0.00 | 18.1 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 15.3 [-151.1; 0.00] |
| bands (native) | 10.7 [-148.8; 0.00] |
| barnative | -8.5 [-164.3; 0.00] |
| confluence | 5.6 [-111.4; 0.00] |
| levels | 6.4 [-67.3; 0.00] |
| levels (native) | -12.9 [-111.1; 0.00] |
| live | -5.0 [-214.9; 0.00] |
| manual | -2.2 [-142.1; 0.00] |
| manual (native) | -2.2 [-6.9; 0.40] |
| momentum | -0.0 [-146.5; 0.00] |
| momentum (native) | 0.0 [-141.7; 0.00] |
| pullback | -2.5 [-201.7; 0.00] |
| pullback (native) | 3.5 [-195.2; 0.00] |
| structure | 0.3 [-165.0; 0.00] |
| structure (native) | 12.0 [-106.5; 0.00] |
| tape | -10.1 [-164.7; 0.00] |
| tape (native) | 23.9 [-88.4; 0.00] |
| trend | -7.8 [-136.4; 0.00] |
| trend (native) | -3.6 [-85.2; 0.00] |
| xmarket | -21.3 [-102.8; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | sym30u | both | 7068 | 2287 | 282 | 1.00 | {"2023": -240.0, "2024": 569.0, "2025": 250.0, "2026": 5190.0} |
| 2 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | asym15u/30u | both | 6437 | 1832 | 309 | 1.00 | {"2023": -566.0, "2024": 879.0, "2025": 380.0, "2026": 4283.0} |
| 3 | tm60 | trend.trend_adx_di.di_cross | {"len": 10, "width": 25} | sym15u | both | 6113 | 2058 | 333 | 1.00 | {"2023": -709.0, "2024": 986.0, "2025": -693.0, "2026": 4091.0} |
| 4 | time_s_15 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.0} | sym30u | both | 6019 | 1477 | 515 | 0.67 | {"2023": -164.0, "2024": -901.0, "2025": -3766.0, "2026": 5196.0} |
| 5 | time_s_15 | trend.trend_macd.hist_turn_native | {"len": 12, "width": 0.0} | sym30u | both | 6019 | 1477 | 515 | 0.67 | {"2023": -164.0, "2024": -901.0, "2025": -3766.0, "2026": 5196.0} |
| 6 | time_s_15 | trend.trend_macd.hist_turn_native | {"len": 12, "width": 0.0} | asym15u/30u | both | 5732 | 2286 | 696 | 0.67 | {"2023": -417.0, "2024": 1194.0, "2025": -1589.0, "2026": 5576.0} |
| 7 | time_s_15 | trend.trend_macd.hist_turn | {"len": 12, "width": 0.0} | asym15u/30u | both | 5732 | 2286 | 696 | 0.67 | {"2023": -417.0, "2024": 1194.0, "2025": -1589.0, "2026": 5576.0} |
| 8 | tm60 | momentum.momentum_willr.revert_native | {"len": 7, "lvl": 10} | sym30u | both | 5719 | 3601 | 363 | 0.67 | {"2023": -241.0, "2024": -974.0, "2025": -1078.0, "2026": 4861.0} |
| 9 | tm60 | momentum.momentum_willr.revert | {"len": 7, "lvl": 10} | sym30u | both | 5719 | 3601 | 363 | 0.67 | {"2023": -241.0, "2024": -974.0, "2025": -1078.0, "2026": 4861.0} |
| 10 | tm60 | momentum.momentum_stoch.revert | {"len": 5, "lvl": 15} | sym30u | both | 5625 | 4078 | 371 | 0.67 | {"2023": -352.0, "2024": -358.0, "2025": -1686.0, "2026": 5159.0} |
| 11 | tm60 | momentum.momentum_stoch.revert_native | {"len": 5, "lvl": 15} | sym30u | both | 5625 | 4078 | 371 | 0.67 | {"2023": -352.0, "2024": -358.0, "2025": -1686.0, "2026": 5159.0} |
| 12 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 10, "k": 1.0} | sym8u | both | 5480 | 2797 | 304 | 0.75 | {"2023": -941.0, "2024": -2057.0, "2025": -423.0, "2026": 4005.0} |
| 13 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 5, "k": 1.0} | sym8u | both | 5480 | 2797 | 304 | 0.67 | {"2023": -941.0, "2024": -2057.0, "2025": -423.0, "2026": 4005.0} |
| 14 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 1.5} | asym10u/20u | both | 5475 | 2410 | 481 | 1.00 | {"2023": 576.0, "2024": -1904.0, "2025": -3365.0, "2026": 2611.0} |
| 15 | time_s_15 | trend.trend_adx_di.adx_cross | {"len": 28, "width": 15} | asym15u/30u | both | 5417 | 2148 | 596 | 1.00 | {"2023": -817.0, "2024": -1674.0, "2025": -46.0, "2026": 5027.0} |
| 16 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 10, "k": 1.0} | asym10u/20u | both | 5406 | 2673 | 301 | 0.75 | {"2023": -1024.0, "2024": -1940.0, "2025": -397.0, "2026": 4161.0} |
| 17 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 5, "k": 1.0} | asym10u/20u | both | 5406 | 2673 | 301 | 0.67 | {"2023": -1024.0, "2024": -1940.0, "2025": -397.0, "2026": 4161.0} |
| 18 | tm60 | trend.trend_adx_di.di_cross | {"len": 7, "width": 15} | sym30u | both | 5404 | 2251 | 347 | 1.00 | {"2023": -888.0, "2024": -1373.0, "2025": -601.0, "2026": 4642.0} |
| 19 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 5, "k": 1.0} | asym20u/10u | both | 5403 | 2670 | 301 | 0.67 | {"2023": -967.0, "2024": -2076.0, "2025": -324.0, "2026": 4306.0} |
| 20 | tm300 | bands.bands_envelope.fade_sma_native | {"clk": 10, "k": 1.0} | sym15u | both | 5403 | 2670 | 301 | 0.75 | {"2023": -1060.0, "2024": -1988.0, "2025": -232.0, "2026": 4356.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.03 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.99 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.05 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.28 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.08 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.06 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.88 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.88 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.02 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.70 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.23 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.01 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.84 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.84 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.18 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 0.99 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 1.00 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.96 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.93 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.71 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.67 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.20 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.71 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.67 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.85 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.13 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.12 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.88 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.83 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.03 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.10 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.15 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.02 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.85 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.30 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.02 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.06 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.05 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.32 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.28 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.28 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.41 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.79 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.31 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.05 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.01 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.02 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.02 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.06 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.92 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.93 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.84 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.93 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.72 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.23 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.07 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.11 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.86 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.82 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.85 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.79 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.85 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.25 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.22 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.17 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.04 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.86 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.13 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.06 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.12 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.17 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.21 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.83 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.13 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.70 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.24 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.75 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.19 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.24 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.12 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.06 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.09 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.17 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.11 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.19 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.19 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.36 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.21 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.70 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.13 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.12 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.09 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.22 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.68 |  |
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
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.93 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.31 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.92 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.10 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.20 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.98 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.95 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 0.99 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.37 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.12 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.89 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.90 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.91 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.95 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.96 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.74 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.34 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.26 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.87 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.93 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell time_m_3 bands.bands_bollinger.break_native asym20u/10u L6M 196.5 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell tm60 levels.levels_vwap_bands.reject sym15u L6M 277.3 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell time_s_15 trend.trend_ma_hma.cross plain60/60 L6M 208.4 pts/wk vs weak baselines K7 -22.5
