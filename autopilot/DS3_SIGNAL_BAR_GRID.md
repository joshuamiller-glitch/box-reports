# DS3_SIGNAL_BAR_GRID - whole trigger library x every bar row x session (W-GRIDA), FIRST PASS, NAKED SCREEN
VERDICT (data ends 2026-11-12; naked screen with bar-scaled brackets, no layers, NOT an engine verdict; first heat table on built bars; nulls: random-entry replicas NOT FINISHED): see the headline table - a trigger x bar counts only by EXCESS over the null distribution of the BEST pick; nothing here is a pass until the engine row with layers exists.

Header: pick window end = newest data week (2026-11-12); refit date = every 2 weeks, this table refreshed 2026-11-17 20:23Z; trials counted = number of cells (below); correction = best-pick null (random-entry replicas, shifted labels 2/3/5 weeks), no White/SPA at screen level; PBO not computed here; selection = walk-forward rolling (trailing 26 weeks pick, next 2 weeks scored), all numbers out of sample; prior-year flags AMBER 15-30% / RED >30% worse than doing nothing; data end 2026-11-12. Spec: autopilot/PREREG_SIGNAL_BAR_GRID.md.

## Five-line summary
1. Tried: every trigger module (bands, trend flips, momentum; W-GRIDB/C/D families join as their modules pass the contract check) on every built bar row, long/short/both, 7 brackets, tape fills + measured slippage + $4.84, flat at session end.
2. Judged: rolling pick on the trailing 26 weeks, scored on the next 2 weeks; neighbour-agreed pick beside the free pick; excess over random-entry null of the best pick.
3. Holds / does not: see the heat tables below (only cells with positive excess AND percentile >= 0.9 deserve attention).
4. Needs in D7: trigger modules are bar-indicator only (no new feed) except book/tape families flagged in TRIGGER_REGISTRY.md; non-time bars need a custom BarsType (BAR_REGISTRY.md).
5. Next: top cells -> live layers (fast replay) -> exact JL3 engine with controls (identity first); then Asia.

## Progress (2026-11-17 20:23Z)
Result files per tag: {"real": 54}. 
Cells scored per session: {"London": 48489, "NYAM": 50001, "NYPM": 51135, "Asia": 51135}

## London
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 2.6 | -0.000 | 495.0 | 0.49 | 40.3 | 87.6 |  |  |  |  | -9.3 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| agreed | 6.9 | 0.008 | 489.4 | 0.51 | 25.4 | 87.6 |  |  |  |  | -10.6 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 1.0 [; ] |
| bands (native) | 1.9 [; ] |
| barnative | 1.6 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 5109 | 2777 | 271 | 0.50 | {"2023": -338.0, "2024": -1054.0, "2025": -1804.0, "2026": 4824.0} |
| 2 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym15u | both | 4560 | 2385 | 262 | 0.75 | {"2023": -396.0, "2024": -1110.0, "2025": -2691.0, "2026": 4718.0} |
| 3 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym15u/30u | both | 4418 | 2391 | 262 | 0.75 | {"2023": -545.0, "2024": -702.0, "2025": -3036.0, "2026": 4079.0} |
| 4 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | sym30u | both | 4418 | 2391 | 262 | 0.75 | {"2023": -789.0, "2024": 471.0, "2025": -2414.0, "2026": 4037.0} |
| 5 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | asym20u/10u | both | 4211 | 986 | 257 | 0.75 | {"2023": -332.0, "2024": -1464.0, "2025": -516.0, "2026": 3779.0} |
| 6 | time_m_3 | bands.bands_bollinger.break_native | {"clk": 20, "k": 1.5} | asym10u/20u | both | 4113 | 2173 | 268 | 0.75 | {"2023": -846.0, "2024": 157.0, "2025": -1586.0, "2026": 4186.0} |
| 7 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4067 | 1379 | 527 | 1.00 | {"2023": -533.0, "2024": -483.0, "2025": 638.0, "2026": 2933.0} |
| 8 | time_m_1 | bands.bands_regchan.fade_linreg | {"n": 20, "k": 2.5} | sym15u | both | 4055 | 1833 | 265 | 1.00 | {"2023": 191.0, "2024": 1213.0, "2025": -1059.0, "2026": 4673.0} |
| 9 | time_m_1 | bands.bands_regchan.fade_linreg_native | {"clk": 20, "k": 2.5} | sym15u | both | 4055 | 1833 | 265 | 0.67 | {"2023": 135.0, "2024": 1213.0, "2025": -1059.0, "2026": 4673.0} |
| 10 | time_m_1 | bands.bands_regchan.fade_linreg | {"n": 20, "k": 2.5} | asym15u/30u | both | 3933 | 1800 | 256 | 1.00 | {"2023": -127.0, "2024": 2141.0, "2025": -2489.0, "2026": 4974.0} |
| 11 | time_m_1 | bands.bands_regchan.fade_linreg_native | {"clk": 20, "k": 2.5} | asym15u/30u | both | 3933 | 1800 | 256 | 0.67 | {"2023": -285.0, "2024": 2141.0, "2025": -2489.0, "2026": 4974.0} |
| 12 | time_m_3 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 2.0} | asym20u/10u | both | 3924 | 2541 | 208 | 0.75 | {"2023": 859.0, "2024": 564.0, "2025": 1698.0, "2026": 3356.0} |
| 13 | time_m_1 | bands.bands_regchan.fade_linreg | {"n": 20, "k": 2.5} | sym30u | both | 3902 | 2073 | 248 | 1.00 | {"2023": 99.0, "2024": 1405.0, "2025": -1892.0, "2026": 4138.0} |
| 14 | time_m_1 | bands.bands_regchan.fade_linreg_native | {"clk": 20, "k": 2.5} | sym30u | both | 3902 | 2073 | 248 | 0.67 | {"2023": -19.0, "2024": 1405.0, "2025": -1892.0, "2026": 4138.0} |
| 15 | time_m_3 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 2.0} | asym10u/20u | both | 3790 | 2538 | 204 | 0.75 | {"2023": 679.0, "2024": -226.0, "2025": 1139.0, "2026": 3707.0} |
| 16 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.25} | sym8u | both | 3733 | 732 | 305 | 1.00 | {"2023": -176.0, "2024": 1019.0, "2025": 279.0, "2026": 2683.0} |
| 17 | time_m_1 | bands.bands_vwap.break | {"minbars": 20, "k": 1.0} | sym30u | both | 3730 | 754 | 217 | 0.75 | {"2023": 42.0, "2024": -313.0, "2025": -268.0, "2026": 3366.0} |
| 18 | time_m_3 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 2.0} | sym30u | both | 3679 | 2490 | 203 | 0.75 | {"2023": 155.0, "2024": 19.0, "2025": 1828.0, "2026": 3487.0} |
| 19 | time_m_3 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 2.0} | asym15u/30u | both | 3679 | 2490 | 203 | 0.75 | {"2023": 248.0, "2024": -295.0, "2025": 1833.0, "2026": 3501.0} |
| 20 | time_m_3 | bands.bands_regchan.fade_linreg | {"n": 10, "k": 2.0} | sym15u | both | 3666 | 2490 | 203 | 0.75 | {"2023": 148.0, "2024": 195.0, "2025": 1809.0, "2026": 3534.0} |

## NYAM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -6.3 | -0.008 | 725.6 | 0.49 | -27.3 | -92.3 |  |  |  |  | -4.1 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| agreed | -1.0 | -0.003 | 657.6 | 0.49 | -25.0 | -92.3 |  |  |  |  | -1.3 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | -8.7 [; ] |
| bands (native) | -1.7 [; ] |
| barnative | -1.2 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 5976 | 797 | 539 | 1.00 | {"2023": -2316.0, "2024": -537.0, "2025": -1936.0, "2026": 5304.0} |
| 2 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 5420 | 2692 | 339 | 0.50 | {"2023": -280.0, "2024": -2124.0, "2025": 730.0, "2026": 4008.0} |
| 3 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -520.0, "2024": -2856.0, "2025": 398.0, "2026": 3887.0} |
| 4 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -344.0, "2024": -2920.0, "2025": 35.0, "2026": 3887.0} |
| 5 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -278.0, "2024": -2903.0, "2025": 13.0, "2026": 3887.0} |
| 6 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 5407 | 2692 | 339 | 0.50 | {"2023": -1276.0, "2024": -3174.0, "2025": 222.0, "2026": 4405.0} |
| 7 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5381 | 2947 | 342 | 0.50 | {"2023": -783.0, "2024": -2840.0, "2025": 1106.0, "2026": 4355.0} |
| 8 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | sym8u | both | 4395 | 1440 | 404 | 0.67 | {"2023": -2372.0, "2024": -5041.0, "2025": -2333.0, "2026": 4678.0} |
| 9 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym8u | both | 4240 | 2948 | 324 | 0.50 | {"2023": -406.0, "2024": -1521.0, "2025": 875.0, "2026": 4112.0} |
| 10 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | asym10u/20u | both | 4223 | 1219 | 400 | 0.67 | {"2023": -1119.0, "2024": -3681.0, "2025": -1205.0, "2026": 3533.0} |
| 11 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | asym20u/10u | both | 4221 | 1219 | 401 | 0.67 | {"2023": -1534.0, "2024": -4919.0, "2025": -1089.0, "2026": 3726.0} |
| 12 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | sym15u | both | 4219 | 1219 | 400 | 0.67 | {"2023": -1968.0, "2024": -4218.0, "2025": -1260.0, "2026": 3499.0} |
| 13 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | sym30u | both | 4219 | 1219 | 400 | 0.67 | {"2023": -1671.0, "2024": -4301.0, "2025": -1193.0, "2026": 3499.0} |
| 14 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 1.5} | asym15u/30u | both | 4219 | 1219 | 400 | 0.67 | {"2023": -1803.0, "2024": -4311.0, "2025": -1178.0, "2026": 3499.0} |
| 15 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym10u/20u | both | 3979 | 2602 | 321 | 0.50 | {"2023": -199.0, "2024": -757.0, "2025": 249.0, "2026": 3365.0} |
| 16 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym15u | both | 3972 | 2602 | 321 | 0.50 | {"2023": -540.0, "2024": -1788.0, "2025": 10.0, "2026": 3258.0} |
| 17 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym15u/30u | both | 3972 | 2602 | 321 | 0.50 | {"2023": -326.0, "2024": -1918.0, "2025": -352.0, "2026": 3258.0} |
| 18 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym30u | both | 3972 | 2602 | 321 | 0.50 | {"2023": -208.0, "2024": -1762.0, "2025": -392.0, "2026": 3258.0} |
| 19 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym20u/10u | both | 3967 | 2602 | 321 | 0.50 | {"2023": -981.0, "2024": -1970.0, "2025": 0.0, "2026": 3797.0} |
| 20 | time_m_1 | bands.bands_envelope.break_sma_native | {"clk": 5, "k": 1.0} | asym10u/20u | both | 3668 | 1966 | 388 | 0.50 | {"2023": 850.0, "2024": 684.0, "2025": -371.0, "2026": 4046.0} |

## NYPM
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | -33.5 | -0.029 | 1392.4 | 0.44 | -80.8 | -92.4 |  |  |  |  | -33.0 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| agreed | -35.0 | -0.030 | 1424.6 | 0.48 | -83.1 | -84.8 |  |  |  |  | -35.3 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 4.6 [; ] |
| bands (native) | -14.8 [; ] |
| barnative | -25.8 [; ] |
| levels | -13.7 [; ] |
| levels (native) | -4.3 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | sym8u | both | 4399 | 978 | 270 | 0.67 | {"2023": 718.0, "2024": 3304.0, "2025": -806.0, "2026": 3758.0} |
| 2 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | asym10u/20u | both | 4302 | 524 | 249 | 0.67 | {"2023": -535.0, "2024": 2924.0, "2025": -349.0, "2026": 3811.0} |
| 3 | time_m_1 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | asym15u/30u | both | 4163 | 952 | 333 | 1.00 | {"2023": 799.0, "2024": -454.0, "2025": 1042.0, "2026": 3101.0} |
| 4 | time_m_1 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym30u | both | 4163 | 952 | 333 | 1.00 | {"2023": 1030.0, "2024": -353.0, "2025": 997.0, "2026": 3101.0} |
| 5 | time_m_1 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | sym15u | both | 4162 | 951 | 334 | 1.00 | {"2023": 696.0, "2024": -241.0, "2025": 870.0, "2026": 3162.0} |
| 6 | time_m_1 | bands.bands_bollinger.fade_native | {"clk": 10, "k": 1.5} | sym8u | short | 4111 | 2453 | 315 | 0.75 | {"2023": -650.0, "2024": -540.0, "2025": -89.0, "2026": 4399.0} |
| 7 | time_m_1 | bands.bands_bollinger.fade | {"n": 10, "k": 1.5} | sym8u | short | 4111 | 2453 | 315 | 1.00 | {"2023": -744.0, "2024": -540.0, "2025": -89.0, "2026": 4399.0} |
| 8 | time_m_1 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | asym20u/10u | both | 4038 | 579 | 337 | 1.00 | {"2023": 1571.0, "2024": -1047.0, "2025": 1325.0, "2026": 3158.0} |
| 9 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | asym15u/30u | both | 4031 | 227 | 246 | 0.67 | {"2023": -476.0, "2024": 2961.0, "2025": -1065.0, "2026": 3723.0} |
| 10 | time_m_1 | bands.bands_regchan.break_stderr_native | {"clk": 5, "k": 1.5} | asym10u/20u | both | 4016 | 747 | 337 | 1.00 | {"2023": 5.0, "2024": 43.0, "2025": 277.0, "2026": 2628.0} |
| 11 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | sym30u | both | 4010 | 206 | 246 | 0.67 | {"2023": -701.0, "2024": 2878.0, "2025": -834.0, "2026": 3722.0} |
| 12 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | sym15u | both | 4006 | 202 | 247 | 0.67 | {"2023": -650.0, "2024": 3123.0, "2025": -1047.0, "2026": 3697.0} |
| 13 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 2.0} | sym8u | short | 3882 | 2564 | 292 | 1.00 | {"2023": -394.0, "2024": -943.0, "2025": -194.0, "2026": 3917.0} |
| 14 | time_m_1 | bands.bands_regchan.fade_stderr | {"n": 20, "k": 2.0} | sym8u | short | 3882 | 2564 | 292 | 1.00 | {"2023": -474.0, "2024": -943.0, "2025": -194.0, "2026": 3917.0} |
| 15 | time_m_1 | bands.bands_bollinger.fade | {"n": 14, "k": 1.5} | sym8u | short | 3864 | 2130 | 296 | 1.00 | {"2023": -705.0, "2024": -267.0, "2025": -790.0, "2026": 4141.0} |
| 16 | time_m_1 | bands.bands_envelope.break_sma | {"n": 40, "pct": 0.1} | asym20u/10u | both | 3828 | 91 | 251 | 0.67 | {"2023": -421.0, "2024": 3341.0, "2025": -1041.0, "2026": 3429.0} |
| 17 | time_m_1 | bands.bands_bollinger.break_native | {"clk": 40, "k": 1.5} | asym10u/20u | both | 3819 | 1798 | 278 | 1.00 | {"2023": -2024.0, "2024": -1250.0, "2025": 1156.0, "2026": 3318.0} |
| 18 | time_m_1 | bands.bands_bollinger.fade | {"n": 10, "k": 1.5} | asym20u/10u | short | 3801 | 2220 | 293 | 1.00 | {"2023": -559.0, "2024": -703.0, "2025": 418.0, "2026": 4145.0} |
| 19 | time_m_1 | bands.bands_bollinger.fade_native | {"clk": 10, "k": 1.5} | asym20u/10u | short | 3801 | 2220 | 293 | 0.75 | {"2023": -473.0, "2024": -703.0, "2025": 418.0, "2026": 4145.0} |
| 20 | time_m_1 | bands.bands_bollinger.fade | {"n": 10, "k": 1.5} | asym10u/20u | short | 3786 | 2231 | 295 | 1.00 | {"2023": -835.0, "2024": -738.0, "2025": 182.0, "2026": 4037.0} |

## Asia
### Headline: best pick over the whole grid (OOS mean pts/week at 1 lot, 4.84 incl)
| pick | OOS pts/wk | R/trade | ulcer (wk pts) | persistence | L6M pts/wk | L3M pts/wk | null mean | null max | excess | pctile | shifted-label mean | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| free | 18.3 | -0.007 | 491.6 | 0.54 | -41.2 | -77.6 |  |  |  |  | -2.8 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| agreed | 20.7 | -0.005 | 520.0 | 0.56 | -11.7 | -13.8 |  |  |  |  | -5.0 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
### Heat table (neighbour-agreed pick): trigger family x bar family; cell = OOS pts/wk [excess over null best-pick; percentile among null draws]; ulcer/persistence in the csv
| trigger family | TIME |
|---|---|
| bands | 31.3 [; ] |
| bands (native) | 16.6 [; ] |
| barnative | -13.6 [; ] |
| levels | 8.0 [; ] |
| levels (native) | 9.5 [; ] |
### Top 20 cells (pick window = trailing 26 weeks to the newest data day; agreed by neighbours; naked)
| # | bar row | trigger.variant | params | bracket | side | L6M pts | L3M pts | trades | nb agree | pts by year |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 1.5} | asym10u/20u | both | 5475 | 2410 | 481 | 1.00 | {"2023": 576.0, "2024": -1904.0, "2025": -3365.0, "2026": 2611.0} |
| 2 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 1.5} | sym30u | both | 4837 | 3109 | 377 | 1.00 | {"2023": 467.0, "2024": -1322.0, "2025": -3832.0, "2026": 3220.0} |
| 3 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 1.5} | asym15u/30u | both | 4156 | 2931 | 420 | 0.67 | {"2023": 461.0, "2024": -1092.0, "2025": -2873.0, "2026": 1886.0} |
| 4 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | asym10u/20u | both | 4097 | 2700 | 363 | 0.50 | {"2023": 343.0, "2024": -1111.0, "2025": 2028.0, "2026": 2821.0} |
| 5 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | sym15u | both | 3902 | 2611 | 361 | 0.75 | {"2023": 301.0, "2024": -1441.0, "2025": 1453.0, "2026": 2412.0} |
| 6 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | sym30u | both | 3897 | 2607 | 360 | 0.50 | {"2023": 352.0, "2024": -1253.0, "2025": 1117.0, "2026": 2663.0} |
| 7 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | asym15u/30u | both | 3897 | 2607 | 360 | 0.50 | {"2023": 341.0, "2024": -1390.0, "2025": 1163.0, "2026": 2660.0} |
| 8 | time_m_1 | bands.bands_atrchan.fade_ext | {"n": 20, "atr": 14, "k": 3.0} | sym30u | both | 3712 | 2021 | 347 | 0.80 | {"2023": -301.0, "2024": -1662.0, "2025": -291.0, "2026": 2501.0} |
| 9 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | sym8u | both | 3630 | 2497 | 391 | 0.50 | {"2023": 102.0, "2024": -934.0, "2025": 1418.0, "2026": 1986.0} |
| 10 | time_m_3 | bands.bands_bollinger.break | {"n": 30, "k": 1.5} | plain60/60 | both | 3559 | 1711 | 595 | 0.67 | {"2023": 993.0, "2024": -157.0, "2025": -1269.0, "2026": 3856.0} |
| 11 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 2.5} | sym30u | both | 3558 | 2850 | 295 | 0.67 | {"2023": -757.0, "2024": 168.0, "2025": -2302.0, "2026": 4097.0} |
| 12 | time_m_1 | bands.bands_bollinger.walk_native | {"clk": 20, "k": 2.0, "N": 3} | sym8u | both | 3547 | 686 | 464 | 0.50 | {"2023": -472.0, "2024": 801.0, "2025": -299.0, "2026": 5684.0} |
| 13 | time_m_1 | bands.bands_bollinger.walk | {"n": 20, "k": 2.0, "N": 3} | sym8u | both | 3547 | 686 | 464 | 0.80 | {"2023": -447.0, "2024": 801.0, "2025": -299.0, "2026": 5684.0} |
| 14 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 2.5} | asym15u/30u | both | 3530 | 2821 | 296 | 0.67 | {"2023": -769.0, "2024": 192.0, "2025": -2282.0, "2026": 4109.0} |
| 15 | time_m_3 | bands.bands_regchan.fade_stderr_native | {"clk": 20, "k": 2.5} | asym10u/20u | both | 3507 | 2783 | 300 | 0.67 | {"2023": -814.0, "2024": 317.0, "2025": -1986.0, "2026": 4263.0} |
| 16 | time_m_1 | bands.bands_regchan.fade_stderr_native | {"clk": 5, "k": 2.5} | asym10u/20u | both | 3499 | 508 | 440 | 0.67 | {"2023": -318.0, "2024": -2758.0, "2025": -949.0, "2026": 913.0} |
| 17 | time_m_3 | bands.bands_atrchan.break_ext_native | {"clk": 10, "k": 1.0} | asym20u/10u | both | 3473 | 2223 | 366 | 0.50 | {"2023": 265.0, "2024": -1473.0, "2025": 873.0, "2026": 1829.0} |
| 18 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | asym20u/10u | both | 3462 | 1567 | 350 | 0.50 | {"2023": -105.0, "2024": -636.0, "2025": -895.0, "2026": 3228.0} |
| 19 | time_m_1 | bands.bands_bollinger.walk | {"n": 20, "k": 2.0, "N": 3} | sym15u | both | 3451 | 1128 | 333 | 0.80 | {"2023": -555.0, "2024": 1468.0, "2025": -692.0, "2026": 3923.0} |
| 20 | time_m_1 | bands.bands_bollinger.walk_native | {"clk": 20, "k": 2.0, "N": 3} | sym15u | both | 3451 | 1128 | 333 | 0.50 | {"2023": -595.0, "2024": 1468.0, "2025": -692.0, "2026": 3923.0} |

## Seven live triggers on their live bars (honest baseline)
NOT FINISHED: to be joined from W-SWA / W-SWB pages (DS3_BAR_SWAP_A/B) once the grid pools exist; 1-min / 3-min time-bar rows they beat to follow.
