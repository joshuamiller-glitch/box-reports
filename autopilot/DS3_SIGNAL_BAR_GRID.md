# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas NOT FINISHED): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-17 23:45Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

**Every number on this page comes from: PASS 1 (coarse grid: 2-3 settings per variant spanning the range; brackets plain 60/60 + sym15u; real + rand1/rand2 nulls; long/short = side split).**

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-17 23:45Z)
Result files per tag: {"p1rand1": 2324, "p1rand2": 2315, "p1real": 2339, "real": 1654}. 
Cells scored per session: {"London": 176799, "NYAM": 190785, "NYPM": 197904, "Asia": 202440}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 4.0 | 0.003 | 556.3 | 0.51 | 98.1 | 3.2 | -0.0 | 2.9 | 4.0 | 1.00 | 4.3 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | 9.8 | 0.014 | 361.6 | 0.53 | 98.1 | 3.2 | -13.9 | -7.5 | 23.7 | 1.00 | -2.4 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 9.1 [6.0; 0.50] |
| bands (native) | -26.5 [-21.8; 0.00] |
| barnative | -23.6 [-11.8; 0.50] |
| confluence | -15.4 [1.1; 0.50] |
| levels | -4.8 [4.4; 1.00] |
| levels (native) | -9.7 [11.2; 0.50] |
| live | 6.3 [5.1; 0.50] |
| manual | -14.4 [-15.2; 0.00] |
| manual (native) | -4.6 [-0.7; 0.50] |
| momentum | 12.3 [28.0; 1.00] |
| momentum (native) | 4.0 [33.4; 1.00] |
| pullback | 2.4 [14.9; 1.00] |
| pullback (native) | -34.2 [-19.6; 0.00] |
| structure | 13.3 [16.8; 1.00] |
| structure (native) | -2.2 [18.7; 1.00] |
| tape | -37.4 [-15.5; 0.50] |
| tape (native) | -19.6 [-19.4; 0.00] |
| trend | -1.1 [-5.2; 0.50] |
| trend (native) | -21.2 [-23.2; 0.00] |
| xmarket | 9.2 [30.6; 1.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_s_15 | structure.structure_inside.outside | {"cf": 0.6, "filt": 0} | sym15u | both | 4880 | 940 | 719 | 0.67 | {"2023": -199.0, "2024": -3558.0, "2025": -2877.0, "2026": 4789.0} |
| 2 | tm300 | levels.levels_vwap.break_native | {"n": 2, "k": 0.25} | sym15u | both | 4347 | 1470 | 213 | 1.00 | {"2023": 79.0, "2024": 371.0, "2025": -657.0, "2026": 4035.0} |
| 3 | tm600 | levels.levels_vwap.reject_native | {"tol": 0.0, "conf": "close"} | sym15u | both | 4252 | 530 | 203 | 1.00 | {"2023": -123.0, "2024": -1172.0, "2025": -217.0, "2026": 2801.0} |
| 4 | tm600 | levels.levels_vwap.reject | {"tol": 0.0, "conf": "close"} | sym15u | both | 4252 | 530 | 203 | 1.00 | {"2023": -123.0, "2024": -1172.0, "2025": -217.0, "2026": 2801.0} |
| 5 | tm60 | xmarket.xmarket_fx.with_6J | {"w": 1, "thr": 1.0} | plain60/60 | both | 4129 | 1753 | 731 | 0.50 | {"2023": 34.0, "2024": -298.0, "2025": 1340.0, "2026": 3855.0} |
| 6 | time_s_20 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | sym15u | both | 4114 | 1811 | 553 | 1.00 | {"2023": 41.0, "2024": 1275.0, "2025": -61.0, "2026": 3450.0} |
| 7 | tm600 | levels.levels_vwap.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 4001 | 2420 | 210 | 1.00 | {"2023": 247.0, "2024": 1065.0, "2025": 179.0, "2026": 4775.0} |
| 8 | time_s_15 | xmarket.xmarket_fx.with_6J | {"w": 1, "thr": 1.0} | plain60/60 | both | 3950 | 1562 | 723 | 1.00 | {"2023": 90.0, "2024": -255.0, "2025": 125.0, "2026": 3708.0} |
| 9 | time_s_20 | xmarket.xmarket_fx.with_6J | {"w": 1, "thr": 1.0} | plain60/60 | both | 3928 | 1511 | 719 | 1.00 | {"2023": 29.0, "2024": -281.0, "2025": -97.0, "2026": 3641.0} |
| 10 | time_s_10 | xmarket.xmarket_fx.with_6J | {"w": 1, "thr": 1.0} | plain60/60 | both | 3912 | 1523 | 721 | 1.00 | {"2023": 51.0, "2024": -135.0, "2025": 140.0, "2026": 3757.0} |
| 11 | tm180 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym15u | both | 3900 | 2172 | 264 | 0.67 | {"2023": -560.0, "2024": -1364.0, "2025": -2704.0, "2026": 3778.0} |
| 12 | tm180 | levels.levels_vwap.break | {"n": 3, "k": 0.5} | sym15u | both | 3854 | 1228 | 221 | 1.00 | {"2023": 11.0, "2024": -781.0, "2025": 513.0, "2026": 3902.0} |
| 13 | tm600 | levels.levels_vwap.reject_native | {"tol": 0.0, "conf": "close"} | plain60/60 | both | 3789 | 541 | 411 | 1.00 | {"2023": 75.0, "2024": -2794.0, "2025": -1859.0, "2026": 3285.0} |
| 14 | tm600 | levels.levels_vwap.reject | {"tol": 0.0, "conf": "close"} | plain60/60 | both | 3789 | 541 | 411 | 1.00 | {"2023": 75.0, "2024": -2794.0, "2025": -1859.0, "2026": 3285.0} |
| 15 | time_s_20 | trend.trend_ma_hma.cross_native | {"len": 21, "width": 0.25, "ratio": 3} | sym15u | both | 3747 | 1781 | 541 | 0.50 | {"2023": -1581.0, "2024": 2746.0, "2025": -855.0, "2026": 4810.0} |
| 16 | tm180 | levels.levels_vwap.break_native | {"n": 3, "k": 0.5} | sym15u | both | 3746 | 1378 | 215 | 1.00 | {"2023": 310.0, "2024": -752.0, "2025": 1201.0, "2026": 3708.0} |
| 17 | time_s_20 | levels.levels_round.reject | {"tol": 0.5, "conf": "body"} | sym15u | both | 3731 | 560 | 405 | 1.00 | {"2023": -1516.0, "2024": 737.0, "2025": 448.0, "2026": 5872.0} |
| 18 | tm60 | tape.tape_stoprun.follow_native | {"N": 600, "k": 0.0} | plain60/60 | both | 3727 | 1157 | 768 | 1.00 | {"2023": -736.0, "2024": 112.0, "2025": 415.0, "2026": 935.0} |
| 19 | time_s_20 | trend.trend_ma_t3.cross | {"len": 9, "width": 2, "hyst": 0.0} | sym15u | both | 3644 | 1427 | 513 | 1.00 | {"2023": -532.0, "2024": 1052.0, "2025": -248.0, "2026": 1424.0} |
| 20 | time_s_20 | levels.levels_round.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 3588 | 771 | 390 | 0.50 | {"2023": -302.0, "2024": 1061.0, "2025": -995.0, "2026": 4599.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -10.5 | -0.001 | 1063.4 | 0.48 | -19.2 | 124.3 | -9.4 | 29.4 | -1.1 | 0.50 | 11.9 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -20.8 | -0.010 | 1163.7 | 0.48 | -113.2 | -79.4 | -6.3 | 10.1 | -14.5 | 0.50 | 4.3 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 17.9 [2.2; 0.50] |
| bands (native) | -27.3 [-35.9; 0.00] |
| barnative | 21.5 [56.5; 1.00] |
| confluence | -15.9 [-8.9; 0.50] |
| levels | -24.6 [-8.4; 0.00] |
| levels (native) | -6.7 [14.4; 0.50] |
| live | -10.3 [11.9; 1.00] |
| manual | 12.1 [6.9; 0.50] |
| manual (native) | 6.8 [-3.9; 0.50] |
| momentum | 0.8 [2.0; 0.50] |
| momentum (native) | 7.3 [22.1; 1.00] |
| pullback | 4.6 [18.2; 1.00] |
| pullback (native) | -4.8 [28.3; 0.50] |
| structure | 43.4 [22.1; 0.50] |
| structure (native) | -26.1 [-39.3; 0.00] |
| tape | 16.7 [37.6; 1.00] |
| tape (native) | -40.5 [-29.9; 0.00] |
| trend | -14.6 [8.1; 0.50] |
| trend (native) | -32.7 [-40.0; 0.00] |
| xmarket | -54.3 [-21.2; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_s_30 | tape.tape_delta.fade_native | {"L": 1800, "z": 1.5} | sym15u | both | 6386 | 1875 | 537 | 1.00 | {"2023": -553.0, "2024": -845.0, "2025": 273.0, "2026": 6909.0} |
| 2 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 58.0, "2024": -1481.0, "2025": -181.0, "2026": 4722.0} |
| 3 | time_s_15 | xmarket.xmarket_ym.diverge | {"w": 30} | sym15u | both | 6125 | 2754 | 460 | 1.00 | {"2023": -2158.0, "2024": -1757.0, "2025": -2342.0, "2026": 4032.0} |
| 4 | time_s_10 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 1.5} | plain60/60 | both | 6076 | 2547 | 1671 | 1.00 | {"2023": -418.0, "2024": -2535.0, "2025": -2246.0, "2026": 3245.0} |
| 5 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | plain60/60 | both | 6062 | 3184 | 1446 | 1.00 | {"2023": -545.0, "2024": -1661.0, "2025": -1603.0, "2026": 5644.0} |
| 6 | tm60 | levels.levels_vwap_bands.reject_native | {"tol": 0.5, "conf": "body"} | sym15u | both | 5877 | 2273 | 480 | 1.00 | {"2023": 1819.0, "2024": 122.0, "2025": 2742.0, "2026": 3662.0} |
| 7 | tm60 | levels.levels_vwap.reject | {"tol": 0.0, "conf": "close"} | sym15u | both | 5838 | 419 | 302 | 1.00 | {"2023": -1468.0, "2024": 1495.0, "2025": -1469.0, "2026": 6714.0} |
| 8 | tm60 | levels.levels_vwap.reject_native | {"tol": 0.0, "conf": "close"} | sym15u | both | 5838 | 419 | 302 | 1.00 | {"2023": -1468.0, "2024": 1495.0, "2025": -1469.0, "2026": 6714.0} |
| 9 | time_s_20 | xmarket.xmarket_ym.diverge | {"w": 30} | sym15u | both | 5816 | 2125 | 454 | 1.00 | {"2023": -2086.0, "2024": -1672.0, "2025": -1884.0, "2026": 4768.0} |
| 10 | time_s_15 | tape.tape_delta.fade_native | {"L": 900, "z": 1.0} | plain60/60 | both | 5643 | 1327 | 1661 | 1.00 | {"2023": 1275.0, "2024": 695.0, "2025": -3449.0, "2026": 2950.0} |
| 11 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | plain60/60 | both | 5606 | 3180 | 1466 | 1.00 | {"2023": -299.0, "2024": -2765.0, "2025": -1751.0, "2026": 3161.0} |
| 12 | time_s_10 | tape.tape_vpin.fade | {"N": 25, "thr": 0.08} | sym15u | both | 5582 | 2293 | 528 | 1.00 | {"2023": -1863.0, "2024": 1040.0, "2025": -532.0, "2026": 4155.0} |
| 13 | tm60 | xmarket.xmarket_ym.diverge | {"w": 30} | sym15u | both | 5550 | 1609 | 426 | 1.00 | {"2023": -2494.0, "2024": 713.0, "2025": -4507.0, "2026": 3772.0} |
| 14 | time_s_20 | tape.tape_delta.fade_sm | {"L": 50, "z": 1.0, "sm": 3} | sym15u | both | 5536 | 2431 | 577 | 1.00 | {"2023": -1121.0, "2024": 568.0, "2025": -1108.0, "2026": 7854.0} |
| 15 | time_s_15 | levels.levels_opens.reject | {"tol": 1.0, "conf": "body"} | sym15u | both | 5218 | 2986 | 367 | 0.67 | {"2023": -809.0, "2024": 1237.0, "2025": -891.0, "2026": 2404.0} |
| 16 | time_s_15 | tape.tape_delta.fade_sm | {"L": 50, "z": 1.0, "sm": 3} | plain60/60 | both | 5212 | 2532 | 1606 | 1.00 | {"2023": 1027.0, "2024": -4325.0, "2025": -2588.0, "2026": 5834.0} |
| 17 | time_s_10 | tape.tape_exhaust.follow | {"k": 1.5, "L": 50} | sym15u | both | 5095 | 2022 | 546 | 1.00 | {"2023": -893.0, "2024": -1915.0, "2025": -13.0, "2026": 2970.0} |
| 18 | time_s_10 | xmarket.xmarket_ym.diverge | {"w": 30} | sym15u | both | 4986 | 2381 | 466 | 1.00 | {"2023": -1488.0, "2024": -1945.0, "2025": -4006.0, "2026": 3471.0} |
| 19 | tm60 | xmarket.xmarket_etf.follow_DIA | {"w": 1, "thr": 1.5} | plain60/60 | both | 4928 | 2638 | 749 | 0.50 | {"2023": 0.0, "2024": 790.0, "2025": -2196.0, "2026": 5482.0} |
| 20 | time_s_20 | tape.tape_delta.fade_native | {"L": 1800, "z": 1.5} | sym15u | both | 4919 | 1187 | 573 | 1.00 | {"2023": -752.0, "2024": -1188.0, "2025": -623.0, "2026": 6265.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 1.1 | 0.002 | 1010.4 | 0.51 | -26.9 | 12.4 | 0.4 | 20.8 | 0.7 | 0.50 | -20.0 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -1.3 | -0.002 | 1016.3 | 0.51 | -26.9 | 12.4 | 4.6 | 46.5 | -5.9 | 0.50 | -15.8 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -14.0 [-23.1; 0.00] |
| bands (native) | -50.0 [-46.3; 0.00] |
| barnative | -53.1 [-50.6; 0.00] |
| confluence | -5.7 [3.2; 0.50] |
| levels | -20.7 [2.0; 0.50] |
| levels (native) | -45.4 [-39.0; 0.00] |
| live | -16.8 [-29.1; 0.00] |
| manual | 12.5 [28.9; 1.00] |
| manual (native) | -14.5 [9.9; 0.50] |
| momentum | 10.8 [12.7; 1.00] |
| momentum (native) | -12.5 [13.2; 1.00] |
| pullback | -3.1 [34.9; 1.00] |
| pullback (native) | -22.3 [-16.0; 0.50] |
| structure | 2.0 [26.7; 1.00] |
| structure (native) | -7.5 [4.7; 0.50] |
| tape | -8.1 [-4.7; 0.50] |
| tape (native) | -10.9 [24.4; 1.00] |
| trend | 11.3 [27.0; 1.00] |
| trend (native) | -9.7 [-32.9; 0.00] |
| xmarket | -22.2 [-15.4; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_s_15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | both | 5418 | 2146 | 927 | 1.00 | {"2023": -2269.0, "2024": -2257.0, "2025": 207.0, "2026": 4647.0} |
| 2 | time_s_10 | trend.trend_ma_sma.cross_native | {"len": 5, "width": 0.25, "ratio": 3} | plain60/60 | both | 5080 | 3107 | 878 | 1.00 | {"2023": -385.0, "2024": 1339.0, "2025": 1957.0, "2026": 4788.0} |
| 3 | time_s_10 | tape.tape_vpin.follow | {"N": 25, "thr": 0.08} | plain60/60 | both | 4933 | 1543 | 856 | 1.00 | {"2023": 667.0, "2024": 234.0, "2025": 711.0, "2026": 3087.0} |
| 4 | time_s_20 | confluence.confluence_user.u3a | {"k": 2, "w": 1} | plain60/60 | both | 4762 | 2297 | 587 | 0.67 | {"2023": 1067.0, "2024": 2367.0, "2025": 69.0, "2026": 3648.0} |
| 5 | time_s_10 | tape.tape_libvol.vwmacd | {"f": 19, "s": 39} | plain60/60 | both | 4716 | 2862 | 939 | 1.00 | {"2023": 867.0, "2024": -506.0, "2025": 4320.0, "2026": 6099.0} |
| 6 | time_s_10 | momentum.momentum_libosc.cmo | {"len": 14} | plain60/60 | both | 4641 | 1696 | 905 | 1.00 | {"2023": 157.0, "2024": -344.0, "2025": 2642.0, "2026": 4531.0} |
| 7 | time_s_10 | momentum.momentum_stoch.cross_zone_native | {"len": 14, "lvl": 20} | sym15u | both | 4638 | 3094 | 565 | 1.00 | {"2023": -1119.0, "2024": -550.0, "2025": -597.0, "2026": 3678.0} |
| 8 | time_s_10 | momentum.momentum_stoch.cross_zone | {"len": 14, "lvl": 20} | sym15u | both | 4638 | 3094 | 565 | 1.00 | {"2023": -1119.0, "2024": -550.0, "2025": -597.0, "2026": 3678.0} |
| 9 | time_s_30 | tape.tape_delta.fade | {"L": 50, "z": 1.0} | plain60/60 | both | 4609 | 4134 | 980 | 1.00 | {"2023": 490.0, "2024": -913.0, "2025": -1898.0, "2026": 5264.0} |
| 10 | time_s_15 | manual.manual_cci.zero | {"len": 14} | plain60/60 | both | 4583 | 1565 | 868 | 0.67 | {"2023": 543.0, "2024": 520.0, "2025": 2156.0, "2026": 4755.0} |
| 11 | time_s_20 | bands.bands_atrchan.break_ext | {"n": 10, "atr": 14, "k": 2.0} | sym15u | both | 4578 | 1231 | 364 | 0.50 | {"2023": 1171.0, "2024": -851.0, "2025": -168.0, "2026": 4453.0} |
| 12 | time_s_30 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | plain60/60 | both | 4524 | 3119 | 982 | 1.00 | {"2023": -10.0, "2024": 356.0, "2025": 201.0, "2026": 4514.0} |
| 13 | time_s_30 | bands.bands_atrchan.break_ext | {"n": 40, "atr": 14, "k": 4.0} | sym15u | both | 4453 | 1990 | 289 | 1.00 | {"2023": -324.0, "2024": 1453.0, "2025": -2982.0, "2026": 3890.0} |
| 14 | time_s_20 | manual.manual_macd.histturn | {"f": 24, "s": 52, "g": 18} | plain60/60 | both | 4448 | 2342 | 925 | 1.00 | {"2023": 46.0, "2024": -36.0, "2025": 713.0, "2026": 5370.0} |
| 15 | tm60 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | plain60/60 | both | 4441 | 1780 | 829 | 1.00 | {"2023": 778.0, "2024": 43.0, "2025": -222.0, "2026": 5554.0} |
| 16 | time_s_15 | trend.trend_macd.signal | {"len": 12, "width": 0.05} | plain60/60 | both | 4399 | 771 | 884 | 1.00 | {"2023": -811.0, "2024": 311.0, "2025": 2458.0, "2026": 3286.0} |
| 17 | time_s_15 | trend.trend_macd.signal_native | {"len": 12, "width": 0.05} | plain60/60 | both | 4399 | 771 | 884 | 1.00 | {"2023": -811.0, "2024": 311.0, "2025": 2458.0, "2026": 3286.0} |
| 18 | time_s_15 | trend.trend_ma_hma.cross | {"len": 21, "width": 2, "hyst": 0.0} | plain60/60 | short | 4387 | 1930 | 463 | 1.00 | {"2023": -1469.0, "2024": -1043.0, "2025": 247.0, "2026": 3991.0} |
| 19 | time_s_30 | trend.trend_ma_hma.cross | {"len": 8, "width": 2, "hyst": 0.0} | plain60/60 | both | 4327 | 2129 | 934 | 0.50 | {"2023": -1575.0, "2024": -403.0, "2025": 3064.0, "2026": 4221.0} |
| 20 | time_s_15 | trend.trend_libstack.trendcolor | {"len": 13} | plain60/60 | both | 4307 | 2091 | 903 | 1.00 | {"2023": 696.0, "2024": 314.0, "2025": 2346.0, "2026": 3333.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -7.5 | -0.034 | 926.5 | 0.57 | -9.2 | -27.1 | -11.2 | 5.2 | 3.7 | 0.50 | 1.4 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -5.6 | -0.031 | 1031.7 | 0.51 | 41.3 | -27.1 | -3.9 | -1.8 | -1.8 | 0.50 | 5.9 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -9.2 [-1.4; 0.50] |
| bands (native) | -20.7 [-14.7; 0.00] |
| barnative | -8.4 [-7.5; 0.00] |
| confluence | -13.7 [-0.3; 0.50] |
| levels | 8.9 [27.2; 1.00] |
| levels (native) | 7.3 [33.0; 1.00] |
| live | 11.7 [18.3; 1.00] |
| manual | -19.7 [-5.9; 0.00] |
| manual (native) | 0.7 [7.0; 1.00] |
| momentum | -12.5 [6.0; 1.00] |
| momentum (native) | -13.8 [0.7; 0.50] |
| pullback | -17.4 [-16.2; 0.00] |
| pullback (native) | -5.2 [9.4; 0.50] |
| structure | -7.6 [-0.1; 0.50] |
| structure (native) | 15.2 [21.1; 1.00] |
| tape | -2.6 [25.9; 1.00] |
| tape (native) | -2.8 [3.2; 1.00] |
| trend | 16.6 [21.8; 1.00] |
| trend (native) | -0.3 [7.1; 0.50] |
| xmarket | -35.8 [-40.5; 0.00] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | tm180 | trend.trend_libstack.wave_agree | {"set": "fast"} | sym15u | both | 4789 | 270 | 324 | 0.67 | {"2023": -870.0, "2024": -846.0, "2025": 292.0, "2026": 3573.0} |
| 2 | tm300 | bands.bands_regchan.fade_stderr_native | {"clk": 10, "k": 2.0} | sym15u | both | 4771 | 3635 | 322 | 1.00 | {"2023": -1365.0, "2024": -1969.0, "2025": 543.0, "2026": 3524.0} |
| 3 | tm300 | barnative.barnative_run.rev | {"n": 4} | sym15u | both | 4712 | 1227 | 270 | 1.00 | {"2023": -564.0, "2024": -2762.0, "2025": -1416.0, "2026": 3377.0} |
| 4 | time_s_20 | confluence.confluence_xfam.trendpb | {"k": 2, "w": 1} | sym15u | both | 4507 | 1440 | 563 | 0.67 | {"2023": -217.0, "2024": 159.0, "2025": -125.0, "2026": 5008.0} |
| 5 | time_s_20 | confluence.confluence_xfam.trendpb | {"k": 2, "w": 1} | plain60/60 | both | 4384 | 1571 | 679 | 0.67 | {"2023": -872.0, "2024": -358.0, "2025": -165.0, "2026": 3046.0} |
| 6 | time_s_20 | levels.levels_profile_va.false_break_native | {"M": 2, "k": 0.5} | sym15u | both | 4355 | 2471 | 408 | 1.00 | {"2023": -797.0, "2024": 1115.0, "2025": 377.0, "2026": 4710.0} |
| 7 | time_s_20 | levels.levels_profile_va.false_break | {"M": 2, "k": 0.5} | sym15u | both | 4140 | 2153 | 406 | 0.67 | {"2023": -236.0, "2024": 556.0, "2025": 105.0, "2026": 4352.0} |
| 8 | time_s_10 | trend.trend_ma_kama.cross_native | {"len": 25, "width": 1.0, "ratio": 3} | sym15u | both | 4057 | 1102 | 867 | 1.00 | {"2023": -1313.0, "2024": -1777.0, "2025": -508.0, "2026": 2408.0} |
| 9 | tm60 | levels.levels_profile_nodes.break | {"n": 1, "k": 0.0} | sym15u | both | 4046 | 2221 | 305 | 1.00 | {"2023": -56.0, "2024": 937.0, "2025": -516.0, "2026": 5481.0} |
| 10 | tm60 | levels.levels_profile_nodes.break_native | {"n": 1, "k": 0.0} | sym15u | both | 4046 | 2221 | 305 | 1.00 | {"2023": -56.0, "2024": 937.0, "2025": -516.0, "2026": 5481.0} |
| 11 | tm600 | levels.levels_round.false_break | {"M": 3, "k": 0.5} | plain60/60 | both | 4021 | 1859 | 758 | 0.50 | {"2023": -174.0, "2024": -384.0, "2025": 1144.0, "2026": 3078.0} |
| 12 | time_s_20 | levels.levels_profile_va.false_break_native | {"M": 3, "k": 0.5} | sym15u | both | 3930 | 2151 | 413 | 0.67 | {"2023": -921.0, "2024": 1198.0, "2025": 523.0, "2026": 4446.0} |
| 13 | tm180 | manual.manual_macd.zero_native | {"f": 2, "s": 5, "g": 2} | sym15u | both | 3864 | 1713 | 333 | 1.00 | {"2023": -586.0, "2024": -210.0, "2025": 131.0, "2026": 3711.0} |
| 14 | tm600 | levels.levels_round.false_break | {"M": 2, "k": 0.5} | plain60/60 | both | 3841 | 1738 | 757 | 0.50 | {"2023": -204.0, "2024": -323.0, "2025": 1125.0, "2026": 2645.0} |
| 15 | time_s_10 | tape.tape_exhaust.fade_native | {"k": 2.0, "L": 3600} | sym15u | both | 3795 | 1136 | 1223 | 1.00 | {"2023": -2051.0, "2024": -1490.0, "2025": -1305.0, "2026": 4627.0} |
| 16 | tm300 | manual.manual_macd.zero_native | {"f": 2, "s": 5, "g": 2} | sym15u | both | 3758 | 977 | 330 | 1.00 | {"2023": -232.0, "2024": 339.0, "2025": -413.0, "2026": 2151.0} |
| 17 | tm300 | levels.levels_vwap_bands.break | {"n": 2, "k": 0.25} | plain60/60 | both | 3727 | 1987 | 657 | 0.50 | {"2023": 169.0, "2024": -451.0, "2025": 1511.0, "2026": 3125.0} |
| 18 | tm300 | momentum.momentum_stoch.zone_break | {"len": 5, "lvl": 70} | plain60/60 | both | 3718 | 1032 | 725 | 1.00 | {"2023": -955.0, "2024": 768.0, "2025": -622.0, "2026": 4310.0} |
| 19 | tm300 | momentum.momentum_stoch.zone_break_native | {"len": 5, "lvl": 70} | plain60/60 | both | 3718 | 1032 | 725 | 1.00 | {"2023": -955.0, "2024": 768.0, "2025": -622.0, "2026": 4310.0} |
| 20 | tm60 | trend.trend_adx_di.adx_cross | {"len": 7, "width": 15} | sym15u | both | 3661 | 964 | 414 | 1.00 | {"2023": -940.0, "2024": -1381.0, "2025": -3365.0, "2026": 2057.0} |

## Baseline: the seven live triggers on their live bars (same screen: plain 60/60 bracket, tape fills, measured slippage, $4.84, flat at session end, 1 lot; pts per week)
Live bar per book used here: EXACT live bars: K7 tm180 (3-min), M7 tm60 (1-min), U7 tm600 (10-min), P7 / H7 / A7 / O7 tm60 (engine 1-min bars per W-SWB fidelity); the two time rows either side of each live row are shown as neighbour; weak cells flagged. This is a TRIGGER baseline: no layers, no confluence/conditions.
| session | book | row | kind | L6M pts/wk | L3M pts/wk | since 2023-10 pts/wk | ulcer (wk pts) | persistence | trades L6M | rank (share of all session cells with lower L6M) | weak cell |
|---|---|---|---|---|---|---|---|---|---|---|
| London | K7 | tm180 | LIVE | -52.7 | -45.8 | -11.6 | 962.7 | 0.46 | 583 | 0.02 | WEAK |
| London | K7 | tm60 | neighbour | 54.5 | 141.0 | -0.1 | 1758.2 | 0.48 | 719 | 0.99 | WEAK |
| London | K7 | tm120 | neighbour | -44.5 | -49.4 | -26.0 | 2358.0 | 0.43 | 635 | 0.03 | WEAK |
| London | K7 | tm240 | neighbour | -6.1 | -63.6 | 10.4 | 616.5 | 0.47 | 542 | 0.12 | WEAK |
| London | K7 | tm300 | neighbour | -35.6 | -49.3 | -3.1 | 724.9 | 0.47 | 490 | 0.04 | WEAK |
| London | M7 | tm60 | LIVE | -39.6 | -40.6 | -27.5 | 3018.7 | 0.35 | 527 | 0.04 | WEAK |
| London | M7 | tm30 | neighbour | 19.0 | 1.2 | -14.1 | 2314.0 | 0.37 | 622 | 0.96 | WEAK |
| London | M7 | tm45 | neighbour | 19.1 | -4.2 | -11.7 | 2066.1 | 0.41 | 565 | 0.96 | WEAK |
| London | M7 | tm120 | neighbour | -62.6 | -22.3 | -29.8 | 2972.8 | 0.42 | 388 | 0.01 | WEAK |
| London | M7 | tm180 | neighbour | 2.4 | -15.6 | -18.7 | 2143.6 | 0.41 | 316 | 0.90 | WEAK |
| London | U7 | tm600 | LIVE | -10.7 | -43.5 | -5.5 | 798.5 | 0.44 | 131 | 0.11 | WEAK |
| London | U7 | tm300 | neighbour | -68.4 | -111.4 | -14.2 | 1004.3 | 0.41 | 233 | 0.01 | WEAK |
| London | U7 | tm420 | neighbour | 13.8 | -18.8 | -3.0 | 756.1 | 0.52 | 178 | 0.94 | WEAK |
| London | U7 | tm780 | neighbour | 13.4 | 9.9 | -1.3 | 643.7 | 0.53 | 96 | 0.94 | WEAK |
| London | U7 | tm900 | neighbour | -16.3 | -16.5 | -8.7 | 943.2 | 0.47 | 86 | 0.09 | WEAK |
| London | P7 | tm60 | LIVE | 65.6 | 48.7 | -7.1 | 2273.6 | 0.40 | 545 | 1.00 | WEAK |
| London | P7 | tm30 | neighbour | 74.2 | 118.0 | -6.1 | 2442.4 | 0.40 | 673 | 1.00 | WEAK |
| London | P7 | tm45 | neighbour | 78.7 | 89.4 | 0.4 | 1932.2 | 0.48 | 608 | 1.00 | WEAK |
| London | P7 | tm120 | neighbour | 37.9 | 1.4 | 6.5 | 873.0 | 0.52 | 445 | 0.99 | WEAK |
| London | P7 | tm180 | neighbour | 26.7 | 28.5 | 3.7 | 897.9 | 0.47 | 378 | 0.97 | WEAK |
| London | H7 | tm60 | LIVE | 2.9 | 23.9 | 2.8 | 372.3 | 0.53 | 121 | 0.91 |  |
| London | H7 | tm30 | neighbour | 0.6 | 23.9 | 2.5 | 357.5 | 0.52 | 122 | 0.90 |  |
| London | H7 | tm45 | neighbour | -14.1 | 8.4 | 3.1 | 362.4 | 0.52 | 130 | 0.09 |  |
| London | H7 | tm120 | neighbour | 3.2 | 25.6 | 4.9 | 378.8 | 0.49 | 128 | 0.91 |  |
| London | H7 | tm180 | neighbour | 0.7 | 28.9 | -0.9 | 584.4 | 0.53 | 81 | 0.90 |  |
| London | A7 | tm60 | LIVE | 14.3 | 18.2 | -6.1 | 830.6 | 0.43 | 326 | 0.95 |  |
| London | A7 | tm30 | neighbour | -23.7 | -11.2 | -4.8 | 641.2 | 0.46 | 394 | 0.07 |  |
| London | A7 | tm45 | neighbour | -26.3 | -19.0 | -8.6 | 786.3 | 0.46 | 362 | 0.06 |  |
| London | A7 | tm120 | neighbour | 18.1 | 25.1 | 5.9 | 324.1 | 0.54 | 190 | 0.96 |  |
| London | A7 | tm180 | neighbour | 12.1 | -7.9 | 6.2 | 280.0 | 0.52 | 185 | 0.94 |  |
| NYAM | K7 | tm180 | LIVE | -75.5 | -76.7 | -13.6 | 2327.5 | 0.49 | 509 | 0.02 | WEAK |
| NYAM | K7 | tm60 | neighbour | -40.6 | -106.5 | -10.8 | 1575.2 | 0.44 | 915 | 0.05 | WEAK |
| NYAM | K7 | tm120 | neighbour | -30.0 | -123.0 | -10.5 | 1468.1 | 0.49 | 643 | 0.07 | WEAK |
| NYAM | K7 | tm240 | neighbour | -79.8 | -92.5 | -9.8 | 1102.8 | 0.47 | 407 | 0.02 | WEAK |
| NYAM | K7 | tm300 | neighbour | 15.3 | 65.7 | 15.3 | 614.4 | 0.56 | 353 | 0.94 | WEAK |
| NYAM | M7 | tm60 | LIVE | -8.9 | -62.9 | 8.8 | 799.6 | 0.49 | 469 | 0.13 | WEAK |
| NYAM | M7 | tm30 | neighbour | -80.7 | -67.0 | -11.3 | 1320.0 | 0.48 | 691 | 0.02 | WEAK |
| NYAM | M7 | tm45 | neighbour | -56.7 | -96.2 | 4.9 | 873.5 | 0.57 | 550 | 0.03 | WEAK |
| NYAM | M7 | tm120 | neighbour | -59.2 | -52.4 | -4.9 | 928.0 | 0.48 | 350 | 0.03 | WEAK |
| NYAM | M7 | tm180 | neighbour | -7.9 | 23.6 | 3.6 | 686.7 | 0.46 | 295 | 0.13 | WEAK |
| NYAM | U7 | tm600 | LIVE | -11.4 | 7.0 | 9.9 | 250.3 | 0.52 | 80 | 0.12 |  |
| NYAM | U7 | tm300 | neighbour | -11.9 | -0.8 | 17.6 | 278.5 | 0.52 | 146 | 0.12 |  |
| NYAM | U7 | tm420 | neighbour | -0.2 | 29.1 | 12.1 | 359.1 | 0.58 | 117 | 0.16 |  |
| NYAM | U7 | tm780 | neighbour | 7.6 | -23.3 | 4.7 | 450.9 | 0.48 | 83 | 0.91 |  |
| NYAM | U7 | tm900 | neighbour | -8.3 | -13.3 | 6.2 | 425.8 | 0.51 | 72 | 0.13 |  |
| NYAM | P7 | tm60 | LIVE | -60.7 | -138.1 | -12.1 | 1779.0 | 0.52 | 524 | 0.03 | WEAK |
| NYAM | P7 | tm30 | neighbour | -114.1 | -109.0 | 6.3 | 1239.6 | 0.56 | 735 | 0.01 | WEAK |
| NYAM | P7 | tm45 | neighbour | -84.3 | -131.4 | -3.6 | 1258.5 | 0.52 | 602 | 0.01 | WEAK |
| NYAM | P7 | tm120 | neighbour | -83.3 | -108.9 | -8.8 | 1172.0 | 0.47 | 360 | 0.01 | WEAK |
| NYAM | P7 | tm180 | neighbour | -58.3 | -110.6 | -12.9 | 1064.8 | 0.51 | 297 | 0.03 | WEAK |
| NYAM | H7 | tm60 | LIVE | 28.8 | 20.1 | 6.1 | 506.0 | 0.48 | 86 | 0.96 | WEAK |
| NYAM | H7 | tm30 | neighbour | 31.1 | 29.4 | 6.0 | 514.6 | 0.49 | 87 | 0.97 | WEAK |
| NYAM | H7 | tm45 | neighbour | 13.9 | 13.9 | -3.7 | 932.6 | 0.51 | 87 | 0.93 | WEAK |
| NYAM | H7 | tm120 | neighbour | 32.4 | 23.7 | 9.9 | 457.8 | 0.51 | 80 | 0.97 | WEAK |
| NYAM | H7 | tm180 | neighbour | 1.7 | 43.8 | 3.6 | 360.5 | 0.49 | 76 | 0.89 | WEAK |
| NYAM | A7 | tm60 | LIVE | -17.2 | 3.9 | -1.6 | 946.9 | 0.46 | 241 | 0.10 |  |
| NYAM | A7 | tm30 | neighbour | -52.8 | -39.6 | -10.3 | 971.6 | 0.49 | 382 | 0.04 |  |
| NYAM | A7 | tm45 | neighbour | -39.4 | -34.4 | -12.0 | 1445.4 | 0.49 | 299 | 0.05 |  |
| NYAM | A7 | tm120 | neighbour | 16.1 | 37.4 | 2.8 | 451.4 | 0.38 | 116 | 0.94 |  |
| NYAM | A7 | tm180 | neighbour | 11.4 | 8.0 | -0.0 | 509.3 | 0.47 | 85 | 0.93 |  |
| NYAM | O7 | tm60 | LIVE | 15.1 | 12.8 | 16.7 | 224.3 | 0.52 | 61 | 0.94 |  |
| NYAM | O7 | tm30 | neighbour | 8.0 | 17.4 | 16.2 | 173.8 | 0.51 | 64 | 0.92 |  |
| NYAM | O7 | tm45 | neighbour | 15.0 | 8.2 | 17.0 | 147.8 | 0.53 | 63 | 0.94 |  |
| NYAM | O7 | tm120 | neighbour | -14.7 | -19.3 | 9.2 | 236.5 | 0.47 | 44 | 0.11 |  |
| NYAM | O7 | tm180 | neighbour | -19.1 | -0.4 | -2.2 | 446.7 | 0.36 | 30 | 0.10 |  |
| NYPM | K7 | tm180 | LIVE | -22.5 | -53.2 | -4.6 | 1319.7 | 0.49 | 476 | 0.08 | WEAK |
| NYPM | K7 | tm60 | neighbour | -75.2 | -104.7 | -30.9 | 2334.8 | 0.44 | 710 | 0.01 | WEAK |
| NYPM | K7 | tm120 | neighbour | 30.2 | -57.2 | 10.2 | 977.1 | 0.59 | 545 | 0.95 | WEAK |
| NYPM | K7 | tm240 | neighbour | -31.7 | -33.9 | -20.3 | 2013.8 | 0.52 | 404 | 0.06 | WEAK |
| NYPM | K7 | tm300 | neighbour | -59.0 | -94.6 | -28.9 | 2031.6 | 0.42 | 345 | 0.02 | WEAK |
| NYPM | M7 | tm60 | LIVE | -36.8 | -112.7 | -1.0 | 758.8 | 0.54 | 410 | 0.05 |  |
| NYPM | M7 | tm30 | neighbour | -24.1 | -0.2 | -18.6 | 1872.2 | 0.41 | 561 | 0.07 |  |
| NYPM | M7 | tm45 | neighbour | -16.4 | -50.4 | -16.0 | 2237.2 | 0.46 | 485 | 0.09 |  |
| NYPM | M7 | tm120 | neighbour | 22.5 | 16.8 | -2.3 | 871.2 | 0.52 | 254 | 0.94 |  |
| NYPM | M7 | tm180 | neighbour | -32.0 | -25.8 | -9.6 | 889.0 | 0.48 | 195 | 0.06 |  |
| NYPM | U7 | tm600 | LIVE | 4.8 | 17.0 | 0.1 | 545.2 | 0.46 | 39 | 0.89 |  |
| NYPM | U7 | tm300 | neighbour | -12.4 | -31.6 | -0.9 | 607.1 | 0.44 | 116 | 0.10 |  |
| NYPM | U7 | tm420 | neighbour | 10.4 | 17.1 | -2.2 | 833.3 | 0.48 | 67 | 0.91 |  |
| NYPM | U7 | tm780 | neighbour | -19.1 | -8.4 | -0.7 | 469.3 | 0.46 | 33 | 0.08 |  |
| NYPM | U7 | tm900 | neighbour | -12.1 | -14.3 | -6.2 | 692.8 | 0.33 | 26 | 0.10 |  |
| NYPM | P7 | tm60 | LIVE | -35.9 | -97.6 | -18.4 | 3000.2 | 0.56 | 449 | 0.05 |  |
| NYPM | P7 | tm30 | neighbour | -58.7 | -112.1 | -20.5 | 1985.4 | 0.48 | 579 | 0.02 |  |
| NYPM | P7 | tm45 | neighbour | -44.7 | -54.7 | -3.1 | 902.4 | 0.59 | 514 | 0.04 |  |
| NYPM | P7 | tm120 | neighbour | -23.9 | -61.9 | -4.2 | 1017.5 | 0.48 | 334 | 0.07 |  |
| NYPM | P7 | tm180 | neighbour | -38.7 | -76.0 | -17.9 | 1375.5 | 0.49 | 251 | 0.04 |  |
| NYPM | H7 | tm60 | LIVE | -20.1 | -38.4 | -5.7 | 682.5 | 0.47 | 86 | 0.08 |  |
| NYPM | H7 | tm30 | neighbour | -20.1 | -38.4 | -6.4 | 719.8 | 0.47 | 86 | 0.08 |  |
| NYPM | H7 | tm45 | neighbour | -0.5 | -7.8 | -4.5 | 734.8 | 0.44 | 86 | 0.15 |  |
| NYPM | H7 | tm120 | neighbour | -16.8 | -8.0 | -7.7 | 849.5 | 0.46 | 85 | 0.09 |  |
| NYPM | H7 | tm180 | neighbour | 4.4 | -0.1 | -7.5 | 1241.3 | 0.48 | 54 | 0.89 |  |
| NYPM | A7 | tm60 | LIVE | -32.5 | -34.7 | -22.7 | 2732.8 | 0.46 | 199 | 0.05 |  |
| NYPM | A7 | tm30 | neighbour | -37.0 | -44.4 | -15.0 | 1771.1 | 0.48 | 238 | 0.05 |  |
| NYPM | A7 | tm45 | neighbour | -47.2 | -63.9 | -17.9 | 1674.2 | 0.47 | 225 | 0.03 |  |
| NYPM | A7 | tm120 | neighbour | -14.8 | -5.5 | -13.2 | 1971.7 | 0.49 | 133 | 0.09 |  |
| NYPM | A7 | tm180 | neighbour | 3.2 | 34.3 | -3.2 | 962.2 | 0.51 | 118 | 0.88 |  |
| Asia | K7 | tm180 | LIVE | 72.1 | 61.6 | 11.3 | 978.2 | 0.56 | 683 | 0.99 |  |
| Asia | K7 | tm60 | neighbour | 82.2 | -34.7 | 23.8 | 585.9 | 0.57 | 896 | 1.00 |  |
| Asia | K7 | tm120 | neighbour | 98.9 | 36.5 | 26.2 | 556.4 | 0.56 | 759 | 1.00 |  |
| Asia | K7 | tm240 | neighbour | 115.3 | 117.7 | 38.9 | 543.2 | 0.65 | 635 | 1.00 |  |
| Asia | K7 | tm300 | neighbour | 97.3 | 106.9 | 35.3 | 360.3 | 0.60 | 570 | 1.00 |  |
| Asia | M7 | tm60 | LIVE | 80.8 | 126.3 | 38.6 | 423.4 | 0.63 | 593 | 1.00 |  |
| Asia | M7 | tm30 | neighbour | 90.3 | 89.8 | 35.0 | 444.9 | 0.65 | 795 | 1.00 |  |
| Asia | M7 | tm45 | neighbour | 49.4 | 102.7 | 29.0 | 480.3 | 0.65 | 697 | 0.99 |  |
| Asia | M7 | tm120 | neighbour | 130.5 | 160.7 | 34.4 | 344.2 | 0.59 | 438 | 1.00 |  |
| Asia | M7 | tm180 | neighbour | 50.4 | 113.2 | 25.0 | 304.0 | 0.59 | 339 | 0.99 |  |
| Asia | U7 | tm600 | LIVE | 35.4 | 16.8 | 13.8 | 169.9 | 0.64 | 153 | 0.97 |  |
| Asia | U7 | tm300 | neighbour | -6.4 | -26.1 | 8.6 | 258.9 | 0.56 | 274 | 0.12 |  |
| Asia | U7 | tm420 | neighbour | 32.2 | 35.3 | 11.1 | 206.8 | 0.59 | 216 | 0.97 |  |
| Asia | U7 | tm780 | neighbour | -39.7 | -29.7 | 2.1 | 400.0 | 0.52 | 119 | 0.04 |  |
| Asia | U7 | tm900 | neighbour | -19.1 | 18.1 | 4.1 | 252.7 | 0.56 | 100 | 0.08 |  |
| Asia | P7 | tm60 | LIVE | 66.1 | 109.3 | 25.7 | 292.4 | 0.60 | 658 | 0.99 |  |
| Asia | P7 | tm30 | neighbour | 41.5 | 67.2 | 13.3 | 602.1 | 0.54 | 799 | 0.98 |  |
| Asia | P7 | tm45 | neighbour | 79.5 | 72.1 | 12.5 | 826.8 | 0.53 | 705 | 1.00 |  |
| Asia | P7 | tm120 | neighbour | -2.0 | -8.2 | 10.6 | 430.0 | 0.54 | 521 | 0.13 |  |
| Asia | P7 | tm180 | neighbour | -33.3 | 45.4 | 1.8 | 573.7 | 0.48 | 418 | 0.05 |  |
| Asia | H7 | tm60 | LIVE | 25.1 | 1.9 | 3.5 | 502.0 | 0.49 | 134 | 0.96 |  |
| Asia | H7 | tm30 | neighbour | 27.4 | -3.2 | 2.9 | 543.2 | 0.51 | 135 | 0.96 |  |
| Asia | H7 | tm45 | neighbour | 29.5 | 7.8 | 5.4 | 398.5 | 0.51 | 141 | 0.96 |  |
| Asia | H7 | tm120 | neighbour | 42.1 | 24.9 | 7.7 | 427.8 | 0.54 | 145 | 0.98 |  |
| Asia | H7 | tm180 | neighbour | 50.4 | 58.7 | 10.4 | 291.2 | 0.57 | 104 | 0.99 |  |
| Asia | A7 | tm60 | LIVE | 6.5 | -18.2 | 26.0 | 229.9 | 0.62 | 358 | 0.91 |  |
| Asia | A7 | tm30 | neighbour | -4.3 | -2.8 | 24.3 | 313.1 | 0.57 | 415 | 0.12 |  |
| Asia | A7 | tm45 | neighbour | -11.4 | -0.1 | 22.8 | 221.2 | 0.56 | 386 | 0.10 |  |
| Asia | A7 | tm120 | neighbour | 22.5 | 40.1 | 21.0 | 201.4 | 0.62 | 256 | 0.95 |  |
| Asia | A7 | tm180 | neighbour | 34.3 | 58.3 | 24.7 | 134.5 | 0.67 | 238 | 0.97 |  |

## Which weak cell each session top cell would replace (naked screen: top cell trailing-26w pts/wk vs the weak book baseline; replace only if better AND neighbour-agreed AND excess over null; verdict = engine row)
- London: top cell time_s_15 structure.structure_inside.outside sym15u L6M 187.7 pts/wk vs weak baselines K7 -52.7; M7 -39.6; U7 -10.7; P7 65.6
- NYAM: top cell time_s_30 tape.tape_delta.fade_native sym15u L6M 245.6 pts/wk vs weak baselines K7 -75.5; M7 -8.9; P7 -60.7; H7 28.8
- NYPM: top cell time_s_15 trend.trend_ma_hma.cross plain60/60 L6M 208.4 pts/wk vs weak baselines K7 -22.5
