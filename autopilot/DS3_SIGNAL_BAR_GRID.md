# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas NOT FINISHED): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-17 20:16Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-17 20:16Z)
Result files per tag: {"real": 27}. 
Cells scored per session: {"London": 26628, "NYAM": 26628, "NYPM": 26628}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -4.4 | 0.004 | 796.6 | 0.48 | 50.4 | 87.6 |  |  |  |  | -13.3 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| agreed | -2.5 | 0.003 | 647.0 | 0.48 | 50.4 | 87.6 |  |  |  |  | -11.4 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 2.8 [; ] |
| bands (native) | -31.2 [; ] |
| barnative | -11.2 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 5109 | 2777 | 271 | 0.67 | {"2023": -338.0, "2024": -1054.0, "2025": -1804.0, "2026": 4824.0} |
| 2 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym15u | both | 4560 | 2385 | 262 | 0.67 | {"2023": -396.0, "2024": -1110.0, "2025": -2691.0, "2026": 4718.0} |
| 3 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym15u/30u | both | 4418 | 2391 | 262 | 0.67 | {"2023": -545.0, "2024": -702.0, "2025": -3036.0, "2026": 4079.0} |
| 4 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym30u | both | 4418 | 2391 | 262 | 0.67 | {"2023": -789.0, "2024": 471.0, "2025": -2414.0, "2026": 4037.0} |
| 5 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | asym20u/10u | both | 4211 | 986 | 257 | 0.75 | {"2023": -332.0, "2024": -1464.0, "2025": -516.0, "2026": 3779.0} |
| 6 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym10u/20u | both | 4113 | 2173 | 268 | 0.67 | {"2023": -846.0, "2024": 157.0, "2025": -1586.0, "2026": 4186.0} |
| 7 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | sym30u | both | 3730 | 754 | 217 | 0.75 | {"2023": 42.0, "2024": -313.0, "2025": -268.0, "2026": 3366.0} |
| 8 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | asym15u/30u | both | 3500 | 818 | 224 | 0.75 | {"2023": 192.0, "2024": -295.0, "2025": -800.0, "2026": 4323.0} |
| 9 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | sym15u | both | 3390 | 584 | 232 | 0.75 | {"2023": -373.0, "2024": -658.0, "2025": -941.0, "2026": 4040.0} |
| 10 | time_m_1 | bands.bands_vwap.walk | {"minbars": 20, "k": 1.0, "N": 2} | asym20u/10u | both | 3326 | 243 | 250 | 1.00 | {"2023": -269.0, "2024": 194.0, "2025": 308.0, "2026": 3316.0} |
| 11 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | asym10u/20u | both | 3244 | 1018 | 252 | 0.75 | {"2023": -169.0, "2024": -719.0, "2025": -850.0, "2026": 5290.0} |
| 12 | time_m_3 | bands.bands_bollinger.break | {"n": 20, "k": 1.5} | asym20u/10u | both | 3098 | 1596 | 245 | 1.00 | {"2023": 604.0, "2024": 108.0, "2025": 750.0, "2026": 2273.0} |
| 13 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym8u | both | 3084 | 1121 | 298 | 0.67 | {"2023": -276.0, "2024": -395.0, "2025": -953.0, "2026": 3133.0} |
| 14 | time_m_3 | bands.bands_bollinger.break | {"n": 20, "k": 1.5} | sym8u | both | 3055 | 1842 | 268 | 1.00 | {"2023": -65.0, "2024": 262.0, "2025": 1131.0, "2026": 3219.0} |
| 15 | time_m_3 | bands.bands_bollinger.break | {"n": 30, "k": 2.0} | sym8u | both | 3048 | 1299 | 234 | 1.00 | {"2023": 72.0, "2024": -605.0, "2025": 89.0, "2026": 4963.0} |
| 16 | time_m_1 | bands.bands_vwap.walk | {"minbars": 20, "k": 1.0, "N": 2} | sym30u | both | 2981 | 46 | 216 | 0.80 | {"2023": 474.0, "2024": 576.0, "2025": 813.0, "2026": 2190.0} |
| 17 | time_m_1 | bands.bands_vwap.walk | {"minbars": 20, "k": 1.0, "N": 2} | sym15u | both | 2854 | 97 | 228 | 0.80 | {"2023": 365.0, "2024": 149.0, "2025": 76.0, "2026": 3558.0} |
| 18 | time_m_1 | bands.bands_vwap.walk | {"minbars": 20, "k": 1.0, "N": 2} | asym15u/30u | both | 2835 | 127 | 222 | 0.80 | {"2023": 580.0, "2024": 167.0, "2025": -157.0, "2026": 3606.0} |
| 19 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.5} | asym15u/30u | both | 2819 | 249 | 226 | 0.80 | {"2023": -93.0, "2024": 80.0, "2025": 366.0, "2026": 2335.0} |
| 20 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.5} | sym15u | both | 2815 | 203 | 235 | 0.80 | {"2023": -623.0, "2024": -595.0, "2025": 144.0, "2026": 2291.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 0.4 | 0.007 | 547.3 | 0.53 | -69.0 | -112.1 |  |  |  |  | -14.9 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | 1.4 | 0.008 | 560.0 | 0.52 | -76.9 | -112.1 |  |  |  |  | -15.4 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -14.8 [; ] |
| bands (native) | -6.6 [; ] |
| barnative | -28.7 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 1.0} | asym20u/10u | both | 3405 | 542 | 478 | 1.00 | {"2023": -1601.0, "2024": -1944.0, "2025": 1960.0, "2026": 3087.0} |
| 2 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 1.0} | sym15u | both | 3132 | 1091 | 461 | 1.00 | {"2023": -1063.0, "2024": -2951.0, "2025": 3686.0, "2026": 2573.0} |
| 3 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 1.0} | asym15u/30u | both | 3112 | 1247 | 457 | 1.00 | {"2023": -489.0, "2024": -2153.0, "2025": 2483.0, "2026": 2479.0} |
| 4 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 1.0} | sym30u | both | 3065 | 1208 | 457 | 1.00 | {"2023": -544.0, "2024": -2706.0, "2025": 2524.0, "2026": 2067.0} |
| 5 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | sym8u | both | 2933 | 2172 | 331 | 0.50 | {"2023": 253.0, "2024": 1019.0, "2025": 1203.0, "2026": 2799.0} |
| 6 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 2.0} | asym20u/10u | both | 2814 | 924 | 446 | 1.00 | {"2023": -461.0, "2024": -3422.0, "2025": 121.0, "2026": 368.0} |
| 7 | time_m_1 | bands.bands_atrchan.fade_ext_native | {"clk": 5, "k": 1.0} | asym10u/20u | both | 2751 | 772 | 476 | 1.00 | {"2023": -358.0, "2024": -1580.0, "2025": 1217.0, "2026": 1861.0} |
| 8 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | asym10u/20u | both | 2749 | 1895 | 327 | 0.50 | {"2023": -36.0, "2024": 1113.0, "2025": 1079.0, "2026": 2507.0} |
| 9 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | sym30u | both | 2740 | 1895 | 327 | 0.50 | {"2023": -23.0, "2024": 872.0, "2025": 1816.0, "2026": 2541.0} |
| 10 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | sym15u | both | 2740 | 1895 | 327 | 0.50 | {"2023": -246.0, "2024": 775.0, "2025": 1528.0, "2026": 2541.0} |
| 11 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | asym15u/30u | both | 2740 | 1895 | 327 | 0.50 | {"2023": -183.0, "2024": 859.0, "2025": 1724.0, "2026": 2541.0} |
| 12 | time_m_3 | barnative.barnative_delta.run | {"n": 3, "thr": 0.0} | asym20u/10u | both | 2740 | 1895 | 327 | 0.50 | {"2023": 316.0, "2024": 174.0, "2025": 1897.0, "2026": 2524.0} |
| 13 | time_m_1 | bands.bands_vwap.fade | {"minbars": 10, "k": 2.0} | asym15u/30u | both | 2677 | 1804 | 244 | 0.75 | {"2023": -868.0, "2024": 656.0, "2025": -923.0, "2026": 3345.0} |
| 14 | time_m_1 | bands.bands_vwap.fade | {"minbars": 10, "k": 2.0} | sym30u | both | 2664 | 1790 | 244 | 0.75 | {"2023": -1056.0, "2024": 696.0, "2025": -643.0, "2026": 3327.0} |
| 15 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 3, "k": 1.0} | asym10u/20u | both | 2538 | 2741 | 260 | 0.67 | {"2023": -484.0, "2024": -2182.0, "2025": 1869.0, "2026": -494.0} |
| 16 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 6, "k": 1.0} | asym20u/10u | both | 2538 | 2741 | 260 | 1.00 | {"2023": -640.0, "2024": -2857.0, "2025": 2404.0, "2026": -38.0} |
| 17 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 6, "k": 1.0} | asym10u/20u | both | 2538 | 2741 | 260 | 0.75 | {"2023": -484.0, "2024": -2182.0, "2025": 1869.0, "2026": -494.0} |
| 18 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 3, "k": 1.0} | asym20u/10u | both | 2538 | 2741 | 260 | 1.00 | {"2023": -640.0, "2024": -2857.0, "2025": 2404.0, "2026": -38.0} |
| 19 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 3, "k": 1.0} | asym15u/30u | both | 2538 | 2741 | 260 | 0.67 | {"2023": -356.0, "2024": -2185.0, "2025": 1916.0, "2026": -368.0} |
| 20 | time_m_3 | bands.bands_avwap0930.fade_0930_native | {"clk": 12, "k": 1.0} | asym20u/10u | both | 2538 | 2741 | 260 | 0.75 | {"2023": -640.0, "2024": -2857.0, "2025": 2404.0, "2026": -38.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -9.0 | -0.005 | 703.7 | 0.43 | -34.8 | -6.7 |  |  |  |  | -34.2 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | 5.5 | 0.010 | 406.4 | 0.48 | -31.2 | 1.1 |  |  |  |  | -30.0 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 9.5 [; ] |
| bands (native) | -33.5 [; ] |
| barnative | -9.3 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 2.0} | sym15u | both | 3323 | 836 | 228 | 0.67 | {"2023": -122.0, "2024": 5.0, "2025": -1832.0, "2026": 1653.0} |
| 2 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 2.0} | sym15u | both | 3323 | 836 | 228 | 0.75 | {"2023": -122.0, "2024": 5.0, "2025": -1832.0, "2026": 1653.0} |
| 3 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 1.0} | sym8u | both | 3311 | 1663 | 268 | 1.00 | {"2023": -94.0, "2024": 308.0, "2025": -3582.0, "2026": 960.0} |
| 4 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 1.0} | sym8u | both | 3311 | 1663 | 268 | 1.00 | {"2023": -94.0, "2024": 308.0, "2025": -3582.0, "2026": 960.0} |
| 5 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 2.0} | asym15u/30u | both | 3305 | 818 | 228 | 0.75 | {"2023": -28.0, "2024": 92.0, "2025": -1861.0, "2026": 1633.0} |
| 6 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 2.0} | sym30u | both | 3305 | 818 | 228 | 0.75 | {"2023": 126.0, "2024": -203.0, "2025": -1423.0, "2026": 1616.0} |
| 7 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 2.0} | sym30u | both | 3305 | 818 | 228 | 0.67 | {"2023": 126.0, "2024": -203.0, "2025": -1423.0, "2026": 1616.0} |
| 8 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 2.0} | asym15u/30u | both | 3305 | 818 | 228 | 0.67 | {"2023": -28.0, "2024": 92.0, "2025": -1861.0, "2026": 1633.0} |
| 9 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 1.0} | asym10u/20u | both | 3294 | 1791 | 250 | 1.00 | {"2023": 290.0, "2024": 900.0, "2025": -2256.0, "2026": 1062.0} |
| 10 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 1.0} | asym10u/20u | both | 3294 | 1791 | 250 | 1.00 | {"2023": 290.0, "2024": 900.0, "2025": -2256.0, "2026": 1062.0} |
| 11 | time_m_1 | bands.bands_atrchan.break_ema | {"n": 40, "atr": 14, "k": 1.5} | asym10u/20u | both | 3278 | 1166 | 275 | 1.00 | {"2023": -704.0, "2024": 1416.0, "2025": 267.0, "2026": 3527.0} |
| 12 | time_m_1 | bands.bands_vwap.break | {"minbars": 30, "k": 1.0} | sym30u | both | 3260 | 1702 | 224 | 1.00 | {"2023": -1036.0, "2024": -941.0, "2025": -2724.0, "2026": 1724.0} |
| 13 | time_m_1 | bands.bands_vwap.break | {"minbars": 30, "k": 1.0} | asym15u/30u | both | 3260 | 1702 | 224 | 1.00 | {"2023": -706.0, "2024": -733.0, "2025": -2751.0, "2026": 1773.0} |
| 14 | time_m_1 | bands.bands_vwap.break | {"minbars": 30, "k": 1.0} | sym15u | both | 3260 | 1702 | 224 | 1.00 | {"2023": -748.0, "2024": -878.0, "2025": -2609.0, "2026": 1773.0} |
| 15 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 1.0} | sym30u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 814.0, "2024": 657.0, "2025": -1517.0, "2026": 1101.0} |
| 16 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 1.0} | asym15u/30u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 793.0, "2024": 852.0, "2025": -1334.0, "2026": 1116.0} |
| 17 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 1.0} | sym30u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 814.0, "2024": 657.0, "2025": -1517.0, "2026": 1101.0} |
| 18 | time_m_1 | bands.bands_vwap.break_native | {"clk": 6, "k": 1.0} | sym15u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 717.0, "2024": 1047.0, "2025": -1607.0, "2026": 1067.0} |
| 19 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 1.0} | sym15u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 717.0, "2024": 1047.0, "2025": -1607.0, "2026": 1067.0} |
| 20 | time_m_1 | bands.bands_vwap.break_native | {"clk": 3, "k": 1.0} | asym15u/30u | both | 3227 | 1807 | 249 | 1.00 | {"2023": 793.0, "2024": 852.0, "2025": -1334.0, "2026": 1116.0} |

## Seven live triggers on their live bars (honest baseline)
NOT FINISHED: to be joined from W-SWA / W-SWB pages (DS3_BAR_SWAP_A/B) once the grid pools exist; 1-min / 3-min time-bar rows they beat to follow.
