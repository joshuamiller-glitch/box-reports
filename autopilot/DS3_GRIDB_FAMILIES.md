# DS3_GRIDB_FAMILIES - W-GRIDB trigger families on every bar row (naked bracket grid; harness W-GRIDA procedure restricted to my modules)
Five-line summary: (1) tried: pullback / structure / bar-native / manual-set / library-extras / confluence entry triggers recomputed on each bar row, 7 bracket sets, tape fills, 4.84 RT; (2) what holds: see the heat table (OOS mean pts/wk over rolling 2-week picks, excess over the best-pick null); (3) what does not: cells with excess <= 0 or RED years; (4) needs in DS7: DATA_NEED per trigger in REGISTRY_B.csv; (5) next: stage-2 confluence from families that beat the null, then layers + exact engine for the top cells.
Header: pick window end 2026-11-14 (trailing 26 weeks, 13 weeks beside), refit date 2026-11-22 (every 2 weeks), data end 2026-11-14 (last full week start 2026-11-08), prior-year check amber 15-30 / red >30 vs doing nothing; trials = param sets x rows x sessions x brackets x modes counted per pool (cells column); FIRST PASS, naked, NOT engine; nulls = harness random-clock tags (rand1, rand2, rand3, rand4, rand5); best-pick fit corrected only by the null excess column.
updated 2026-11-17T22:34:06Z; COVERAGE real-tag result files 560 of 12852 (4%: my 27 modules x 476 bar rows); result files by tag {"rand1": 532, "rand2": 523, "rand3": 326, "rand4": 326, "rand5": 325, "real": 560}

## Heat table London (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|TIME | 31878 | 81 | 16.5 | 0.008 | 342 | 52% | 104.0 | 94.2 | 124.4 | 146.3 | -108.0 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| structure (native)|TIME | 10584 | 81 | 1.1 | -0.002 | 468 | 52% | -5.1 | -39.9 | 115.2 | 126.0 | -114.1 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| manual|TIME | 32067 | 81 | -13.6 | -0.013 | 755 | 44% | -14.9 | 52.2 | 112.5 | 138.4 | -126.1 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| manual (native)|TIME | 6930 | 81 | -20.7 | -0.020 | 750 | 43% | -66.0 | -76.9 | 2.6 | 27.2 | -23.3 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| pullback|TIME | 21420 | 81 | -21.3 | -0.046 | 1373 | 43% | 27.3 | -29.4 | 161.1 | 177.8 | -182.3 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| pullback (native)|TIME | 10584 | 81 | -23.3 | -0.043 | 858 | 48% | -37.2 | -32.6 | 180.2 | 199.7 | -203.6 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| momentum|TIME | 2100 | 81 | -27.0 | -0.042 | 1162 | 42% | -12.8 | -55.5 | 53.9 | 63.2 | -80.9 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| trend|TIME | 8379 | 81 | -30.5 | -0.026 | 1213 | 43% | -49.9 | -73.9 | 121.7 | 141.5 | -152.1 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| structure|TIME | 75033 | 81 | -35.8 | -0.045 | 1760 | 44% | -50.8 | 9.4 | 145.0 | 166.2 | -180.8 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| tape|TIME | 6930 | 81 | -46.6 | -0.035 | 2140 | 36% | -74.7 | -93.1 | 26.2 | 36.7 | -72.9 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| barnative|TIME | 57225 | 81 | -46.8 | -0.045 | 1640 | 47% | -163.6 | -122.7 | 140.5 | 155.6 | -187.3 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Heat table NYAM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|TIME | 31878 | 81 | 42.5 | 0.026 | 369 | 57% | 0.5 | 11.6 | 163.5 | 179.5 | -121.1 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 10584 | 81 | 8.9 | 0.006 | 885 | 52% | 18.5 | 139.6 | 248.7 | 265.3 | -239.9 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| manual (native)|TIME | 6930 | 81 | 8.5 | 0.008 | 973 | 46% | 155.1 | 124.3 | 29.1 | 62.6 | -20.6 | 0.20 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| trend|TIME | 8379 | 81 | 3.9 | -0.008 | 606 | 48% | -33.6 | -8.0 | 185.8 | 208.9 | -181.9 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| pullback (native)|TIME | 10584 | 81 | 1.9 | 0.007 | 599 | 52% | -33.5 | -25.6 | 356.8 | 388.6 | -354.9 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual|TIME | 32067 | 81 | 0.6 | 0.005 | 730 | 51% | -60.2 | 31.2 | 161.2 | 194.0 | -160.6 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| momentum|TIME | 2100 | 81 | -7.7 | -0.009 | 815 | 46% | -23.9 | -31.2 | 55.0 | 92.7 | -62.7 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| pullback|TIME | 21420 | 81 | -13.0 | -0.002 | 1011 | 48% | -30.2 | -41.5 | 358.5 | 388.6 | -371.6 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| structure|TIME | 75033 | 81 | -19.8 | -0.010 | 811 | 46% | -85.0 | -135.3 | 238.7 | 260.6 | -258.5 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| barnative|TIME | 57225 | 81 | -21.9 | -0.010 | 1163 | 42% | -54.5 | -98.5 | 252.9 | 286.2 | -274.8 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| tape|TIME | 6930 | 81 | -46.6 | -0.040 | 1950 | 38% | -92.0 | -94.8 | 7.1 | 41.7 | -53.7 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Heat table NYPM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|TIME | 57225 | 81 | 29.0 | 0.023 | 402 | 58% | 84.5 | 51.0 | 194.8 | 230.1 | -165.8 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 10584 | 81 | 23.1 | 0.024 | 279 | 56% | 11.2 | 49.2 | 210.8 | 220.3 | -187.7 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| structure|TIME | 75033 | 81 | 12.2 | 0.001 | 425 | 53% | -75.7 | -118.4 | 204.7 | 230.2 | -192.5 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "RED"} |
| trend|TIME | 8379 | 81 | 8.7 | 0.010 | 1031 | 49% | 73.1 | -33.9 | 138.7 | 157.6 | -130.0 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "ok"} |
| manual|TIME | 32067 | 81 | 6.4 | 0.013 | 630 | 54% | 74.5 | 109.8 | 142.2 | 160.9 | -135.9 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 2100 | 81 | 3.3 | -0.004 | 352 | 52% | 5.9 | 20.8 | 55.9 | 95.3 | -52.5 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual (native)|TIME | 6930 | 81 | -10.4 | -0.009 | 682 | 49% | -27.7 | 20.8 | 15.8 | 39.6 | -26.2 | 0.20 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| pullback (native)|TIME | 10584 | 81 | -20.2 | -0.022 | 1780 | 51% | 20.4 | -1.9 | 219.9 | 244.2 | -240.0 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| tape|TIME | 6930 | 81 | -23.1 | -0.012 | 1194 | 47% | -60.6 | 80.2 | 31.7 | 62.4 | -54.7 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| pullback|TIME | 21420 | 81 | -38.7 | -0.041 | 2041 | 37% | -47.7 | -126.8 | 218.2 | 237.1 | -256.9 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| confluence|TIME | 31878 | 81 | -56.3 | -0.047 | 2945 | 36% | -39.3 | -114.5 | 160.9 | 179.8 | -217.2 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Top 20 cells at the newest pick window (by session; trigger.module.variant, exact params, bar row, bracket, side mode)
| session | rank | row | trigger | params | bracket | mode | L6M pts | L3M pts | trades | nb agree | by year pts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| London | 1 | tm10 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | plain60/60 | both | 4507 | 1936 | 803 | 1.00 | {"2023": -769.0, "2024": -1761.0, "2025": -1397.0, "2026": 3066.0} |
| London | 2 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4436 | 1366 | 530 | 1.00 | {"2023": -709.0, "2024": -651.0, "2025": 1201.0, "2026": 3773.0} |
| London | 3 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 4096 | 2540 | 332 | 0.75 | {"2023": 1185.0, "2024": 938.0, "2025": -268.0, "2026": 5097.0} |
| London | 4 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4067 | 1379 | 527 | 1.00 | {"2023": -533.0, "2024": -483.0, "2025": 638.0, "2026": 2933.0} |
| London | 5 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 4058 | 1568 | 274 | 0.75 | {"2023": -811.0, "2024": 2047.0, "2025": -2.0, "2026": 3783.0} |
| London | 6 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym10u/20u | both | 3980 | 1634 | 273 | 0.75 | {"2023": -665.0, "2024": 1408.0, "2025": 299.0, "2026": 3494.0} |
| London | 7 | time_s_15 | manual.manual_macd.sigcross_native | {"f": 3, "s": 8, "g": 3} | sym15u | both | 3973 | 1382 | 638 | 1.00 | {"2023": -170.0, "2024": 851.0, "2025": -1729.0, "2026": 2311.0} |
| London | 8 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 3959 | 1569 | 259 | 0.75 | {"2023": -526.0, "2024": 1736.0, "2025": 462.0, "2026": 3450.0} |
| London | 9 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym8u | both | 3888 | 1788 | 331 | 0.75 | {"2023": 1120.0, "2024": 993.0, "2025": 498.0, "2026": 4359.0} |
| London | 10 | time_s_45 | manual.manual_macd.histturn | {"f": 5, "s": 13, "g": 5} | asym15u/30u | both | 3883 | 989 | 320 | 1.00 | {"2023": -876.0, "2024": 81.0, "2025": -137.0, "2026": 4896.0} |
| London | 11 | time_s_45 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | asym20u/10u | both | 3858 | 2052 | 393 | 1.00 | {"2023": -285.0, "2024": 601.0, "2025": -1467.0, "2026": 4182.0} |
| London | 12 | time_s_15 | structure.structure_breakout.fail2 | {"n": 20, "buf": 0.0} | asym10u/20u | both | 3840 | 2418 | 760 | 0.75 | {"2023": -1387.0, "2024": 528.0, "2025": -818.0, "2026": 2220.0} |
| London | 13 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | sym8u | both | 3824 | 1182 | 420 | 0.83 | {"2023": -1046.0, "2024": -14.0, "2025": -321.0, "2026": 2199.0} |
| London | 14 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym20u/10u | both | 3808 | 1864 | 274 | 0.75 | {"2023": 938.0, "2024": 1006.0, "2025": 349.0, "2026": 3307.0} |
| London | 15 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 3762 | 1368 | 260 | 0.75 | {"2023": -643.0, "2024": 1744.0, "2025": 28.0, "2026": 3041.0} |
| London | 16 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.25} | sym8u | both | 3733 | 732 | 305 | 1.00 | {"2023": -176.0, "2024": 1019.0, "2025": 279.0, "2026": 2683.0} |
| London | 17 | time_m_2 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 3721 | 1366 | 261 | 0.75 | {"2023": 355.0, "2024": 716.0, "2025": 605.0, "2026": 3091.0} |
| London | 18 | tm60 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 3692 | 959 | 531 | 0.50 | {"2023": -773.0, "2024": -1418.0, "2025": -2762.0, "2026": 2065.0} |
| London | 19 | time_s_45 | structure.structure_breakout.fail | {"n": 10, "buf": 0.0} | asym20u/10u | both | 3665 | 1313 | 389 | 1.00 | {"2023": -701.0, "2024": 571.0, "2025": 503.0, "2026": 3669.0} |
| London | 20 | time_s_15 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.25} | sym15u | both | 3625 | 2376 | 602 | 0.83 | {"2023": -404.0, "2024": -728.0, "2025": -974.0, "2026": 2966.0} |
| NYAM | 1 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 6151 | 2822 | 348 | 0.50 | {"2023": 520.0, "2024": -1188.0, "2025": 336.0, "2026": 4836.0} |
| NYAM | 2 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 58.0, "2024": -1481.0, "2025": -181.0, "2026": 4722.0} |
| NYAM | 3 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 614.0, "2024": -1423.0, "2025": -422.0, "2026": 4722.0} |
| NYAM | 4 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 311.0, "2024": -1331.0, "2025": -406.0, "2026": 4722.0} |
| NYAM | 5 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 6138 | 2822 | 348 | 0.50 | {"2023": -959.0, "2024": -1653.0, "2025": -153.0, "2026": 5234.0} |
| NYAM | 6 | time_m_1 | manual.manual_macd.histturn_native | {"f": 2, "s": 5, "g": 2} | plain60/60 | both | 6105 | 258 | 1358 | 1.00 | {"2023": -422.0, "2024": 291.0, "2025": -1849.0, "2026": 6700.0} |
| NYAM | 7 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | plain60/60 | both | 6062 | 3184 | 1446 | 0.75 | {"2023": -545.0, "2024": -1661.0, "2025": -1603.0, "2026": 5644.0} |
| NYAM | 8 | tm60 | manual.manual_macd.histturn_native | {"f": 2, "s": 5, "g": 2} | plain60/60 | both | 5990 | 552 | 1385 | 0.50 | {"2023": -289.0, "2024": -639.0, "2025": -2536.0, "2026": 7350.0} |
| NYAM | 9 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 5976 | 797 | 539 | 1.00 | {"2023": -2316.0, "2024": -537.0, "2025": -1936.0, "2026": 5304.0} |
| NYAM | 10 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5939 | 2672 | 349 | 0.50 | {"2023": -1064.0, "2024": -1551.0, "2025": 841.0, "2026": 5025.0} |
| NYAM | 11 | tm10 | structure.structure_libpattern.pin | {"k": 2.0, "filt": 0} | asym20u/10u | both | 5677 | 2166 | 620 | 0.67 | {"2023": -1145.0, "2024": 400.0, "2025": -1208.0, "2026": 8544.0} |
| NYAM | 12 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | plain60/60 | both | 5606 | 3180 | 1466 | 1.00 | {"2023": -299.0, "2024": -2765.0, "2025": -1751.0, "2026": 3161.0} |
| NYAM | 13 | tm10 | barnative.barnative_run.cont | {"n": 5} | asym10u/20u | both | 5534 | 2704 | 524 | 0.67 | {"2023": 1006.0, "2024": -462.0, "2025": 787.0, "2026": 4627.0} |
| NYAM | 14 | tm10 | barnative.barnative_run.cont | {"n": 5} | asym15u/30u | both | 5526 | 2928 | 478 | 1.00 | {"2023": 18.0, "2024": 159.0, "2025": -277.0, "2026": 5114.0} |
| NYAM | 15 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 5420 | 2692 | 339 | 1.00 | {"2023": -280.0, "2024": -2124.0, "2025": 730.0, "2026": 4008.0} |
| NYAM | 16 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 5412 | 2692 | 339 | 1.00 | {"2023": -520.0, "2024": -2856.0, "2025": 398.0, "2026": 3887.0} |
| NYAM | 17 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 5412 | 2692 | 339 | 1.00 | {"2023": -344.0, "2024": -2920.0, "2025": 35.0, "2026": 3887.0} |
| NYAM | 18 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 5412 | 2692 | 339 | 1.00 | {"2023": -278.0, "2024": -2903.0, "2025": 13.0, "2026": 3887.0} |
| NYAM | 19 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 5407 | 2692 | 339 | 1.00 | {"2023": -1276.0, "2024": -3174.0, "2025": 222.0, "2026": 4405.0} |
| NYAM | 20 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5381 | 2947 | 342 | 1.00 | {"2023": -783.0, "2024": -2840.0, "2025": 1106.0, "2026": 4355.0} |
| NYPM | 1 | time_s_10 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 2.0} | asym10u/20u | both | 4956 | 1005 | 594 | 1.00 | {"2023": -1974.0, "2024": -498.0, "2025": 767.0, "2026": 6289.0} |
| NYPM | 2 | time_s_15 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | asym15u/30u | both | 4835 | 402 | 360 | 0.50 | {"2023": -424.0, "2024": -2243.0, "2025": -1093.0, "2026": 5698.0} |
| NYPM | 3 | tm10 | tape.tape_libvol.vwmacd | {"f": 19, "s": 39} | plain60/60 | both | 4805 | 2401 | 929 | 1.00 | {"2023": -140.0, "2024": -647.0, "2025": 4222.0, "2026": 5631.0} |
| NYPM | 4 | time_s_10 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 2.0} | asym20u/10u | both | 4760 | 2263 | 626 | 1.00 | {"2023": -532.0, "2024": -1119.0, "2025": -393.0, "2026": 5689.0} |
| NYPM | 5 | time_s_15 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | sym30u | both | 4698 | 226 | 326 | 0.75 | {"2023": -1184.0, "2024": -3588.0, "2025": -914.0, "2026": 5254.0} |
| NYPM | 6 | time_s_15 | manual.manual_cci.zero | {"len": 14} | plain60/60 | both | 4583 | 1565 | 868 | 1.00 | {"2023": 543.0, "2024": 520.0, "2025": 2156.0, "2026": 4755.0} |
| NYPM | 7 | time_s_10 | barnative.barnative_run.cont | {"n": 4} | sym30u | both | 4516 | 1937 | 357 | 0.67 | {"2023": 984.0, "2024": -458.0, "2025": 4359.0, "2026": 5065.0} |
| NYPM | 8 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | sym30u | both | 4483 | 1808 | 332 | 0.67 | {"2023": 299.0, "2024": -118.0, "2025": -344.0, "2026": 4547.0} |
| NYPM | 9 | time_m_1 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | plain60/60 | both | 4471 | 1879 | 831 | 1.00 | {"2023": 1297.0, "2024": -612.0, "2025": -1533.0, "2026": 4923.0} |
| NYPM | 10 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | asym15u/30u | both | 4460 | 1665 | 362 | 0.67 | {"2023": 945.0, "2024": -263.0, "2025": -2194.0, "2026": 4270.0} |
| NYPM | 11 | tm60 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | plain60/60 | both | 4441 | 1780 | 829 | 1.00 | {"2023": 778.0, "2024": 43.0, "2025": -222.0, "2026": 5554.0} |
| NYPM | 12 | tm10 | trend.trend_libstack.vwma_px | {"len": 21} | asym10u/20u | both | 4357 | 2278 | 596 | 0.67 | {"2023": -1051.0, "2024": -705.0, "2025": 2939.0, "2026": 2832.0} |
| NYPM | 13 | time_s_10 | barnative.barnative_avwap.break | {"anchor": "sess", "k": 1.0} | asym10u/20u | both | 4335 | 906 | 435 | 0.67 | {"2023": -697.0, "2024": -1097.0, "2025": -371.0, "2026": 3790.0} |
| NYPM | 14 | time_s_10 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 2.0} | asym10u/20u | both | 4334 | 1646 | 591 | 1.00 | {"2023": -744.0, "2024": -12.0, "2025": 30.0, "2026": 5573.0} |
| NYPM | 15 | time_s_15 | trend.trend_libstack.trendcolor | {"len": 13} | plain60/60 | both | 4307 | 2091 | 903 | 0.50 | {"2023": 696.0, "2024": 314.0, "2025": 2346.0, "2026": 3333.0} |
| NYPM | 16 | time_s_15 | structure.structure_libpattern.nr | {"n": 4} | asym10u/20u | both | 4276 | 2065 | 477 | 0.50 | {"2023": -1251.0, "2024": -224.0, "2025": -2770.0, "2026": 3208.0} |
| NYPM | 17 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | sym15u | both | 4258 | 1232 | 404 | 0.67 | {"2023": 346.0, "2024": -688.0, "2025": -860.0, "2026": 3192.0} |
| NYPM | 18 | tm10 | trend.trend_libstack.ema_hold | {"len": 13, "hold": 5} | sym30u | both | 4231 | 656 | 344 | 0.67 | {"2023": -134.0, "2024": 929.0, "2025": -2421.0, "2026": 6943.0} |
| NYPM | 19 | time_s_15 | manual.manual_cci.rev | {"len": 50, "lvl": 100} | sym30u | short | 4226 | 1938 | 289 | 1.00 | {"2023": -567.0, "2024": -292.0, "2025": 608.0, "2026": 4173.0} |
| NYPM | 20 | time_s_45 | manual.manual_cci.rev | {"len": 20, "lvl": 150} | asym20u/10u | short | 4221 | 2217 | 256 | 1.00 | {"2023": -456.0, "2024": -856.0, "2025": -1124.0, "2026": 4201.0} |
