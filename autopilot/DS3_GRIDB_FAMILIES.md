# DS3_GRIDB_FAMILIES - W-GRIDB trigger families on every bar row (naked bracket grid; harness W-GRIDA procedure restricted to my modules)
Five-line summary: (1) tried: pullback / structure / bar-native / manual-set / library-extras / confluence entry triggers recomputed on each bar row, 7 bracket sets, tape fills, 4.84 RT; (2) what holds: see the heat table (OOS mean pts/wk over rolling 2-week picks, excess over the best-pick null); (3) what does not: cells with excess <= 0 or RED years; (4) needs in DS7: DATA_NEED per trigger in REGISTRY_B.csv; (5) next: stage-2 confluence from families that beat the null, then layers + exact engine for the top cells.
Header: pick window end 2026-11-14 (trailing 26 weeks, 13 weeks beside), refit date 2026-11-22 (every 2 weeks), data end 2026-11-14 (last full week start 2026-11-08), prior-year check amber 15-30 / red >30 vs doing nothing; trials = param sets x rows x sessions x brackets x modes counted per pool (cells column); FIRST PASS, naked, NOT engine; nulls = harness random-clock tags (rand1, rand2, rand3, rand4, rand5); best-pick fit corrected only by the null excess column.
updated 2026-11-17T21:24:41Z; COVERAGE real-tag result files 300 of 8019 (4%: my 27 modules x 297 bar rows); result files by tag {"rand1": 234, "rand2": 204, "rand3": 198, "rand4": 198, "rand5": 198, "real": 300}

## Heat table London (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|TIME | 7938 | 81 | -3.3 | -0.024 | 713 | 49% | 68.9 | 83.9 | 126.7 | 152.4 | -130.0 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "ok"} |
| pullback|TIME | 12348 | 81 | -4.2 | -0.026 | 473 | 48% | 9.3 | -68.4 | 170.0 | 192.8 | -174.1 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| structure (native)|TIME | 6048 | 81 | -13.1 | -0.026 | 740 | 51% | 19.9 | -39.9 | 131.2 | 142.2 | -144.4 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| structure|TIME | 43155 | 81 | -14.6 | -0.009 | 659 | 49% | -33.5 | -25.2 | 150.3 | 187.2 | -164.9 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| barnative|TIME | 36204 | 81 | -22.8 | -0.031 | 821 | 46% | -113.7 | -23.7 | 136.9 | 157.5 | -159.7 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| manual|TIME | 11298 | 81 | -24.7 | -0.021 | 975 | 47% | -98.9 | -63.4 | 116.2 | 140.1 | -140.9 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| manual (native)|TIME | 4410 | 81 | -26.0 | -0.013 | 1404 | 46% | -70.0 | -77.6 | -3.7 | 6.0 | -22.3 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| momentum|TIME | 2100 | 81 | -27.0 | -0.042 | 1162 | 42% | -12.8 | -55.5 | nan | nan | nan | nan | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| trend|TIME | 4788 | 81 | -28.5 | -0.040 | 1349 | 42% | -14.9 | -72.4 | 125.2 | 142.8 | -153.7 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "RED"} |
| pullback (native)|TIME | 6048 | 81 | -31.3 | -0.046 | 1060 | 44% | -101.9 | -149.5 | 176.6 | 196.1 | -207.9 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| tape|TIME | 4095 | 81 | -35.3 | -0.046 | 1263 | 41% | -75.0 | -82.7 | 27.6 | 40.6 | -62.8 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Heat table NYAM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| confluence|TIME | 7938 | 81 | 63.1 | 0.040 | 261 | 57% | 1.9 | -79.4 | 164.9 | 183.3 | -101.9 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| pullback (native)|TIME | 6048 | 81 | 23.4 | 0.026 | 579 | 59% | -12.4 | 20.1 | 346.7 | 415.7 | -323.3 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "AMBER"} |
| structure|TIME | 43155 | 81 | 9.6 | 0.004 | 1066 | 47% | 18.0 | 76.1 | 232.6 | 250.8 | -223.0 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "ok"} |
| manual|TIME | 11298 | 81 | 1.8 | 0.008 | 694 | 56% | -13.4 | 36.3 | 164.4 | 194.2 | -162.6 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| structure (native)|TIME | 6048 | 81 | -2.9 | 0.004 | 728 | 53% | 25.2 | 139.6 | 220.2 | 246.3 | -223.1 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| momentum|TIME | 2100 | 81 | -7.7 | -0.009 | 815 | 46% | -23.9 | -31.2 | nan | nan | nan | nan | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| trend|TIME | 4788 | 81 | -17.8 | -0.012 | 995 | 46% | -76.7 | -37.4 | 201.9 | 222.4 | -219.6 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "ok", "2026": "RED"} |
| tape|TIME | 4095 | 81 | -23.8 | -0.026 | 1412 | 44% | -63.4 | 81.0 | 13.8 | 42.3 | -37.6 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |
| barnative|TIME | 36204 | 81 | -29.8 | -0.006 | 1546 | 43% | 3.1 | -34.4 | 228.1 | 246.5 | -257.8 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| pullback|TIME | 12348 | 81 | -35.2 | -0.019 | 1434 | 44% | -188.7 | -92.6 | 349.4 | 380.2 | -384.6 | 0.00 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "RED"} |
| manual (native)|TIME | 4410 | 81 | -35.6 | -0.032 | 1397 | 41% | -47.8 | -24.9 | 13.2 | 34.1 | -48.8 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Heat table NYPM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| manual (native)|TIME | 4410 | 81 | 22.1 | 0.025 | 261 | 56% | 6.8 | 37.9 | 17.6 | 37.1 | 4.6 | 0.60 | {"2023": "ok", "2024": "ok", "2025": "ok", "2026": "ok"} |
| momentum|TIME | 2100 | 81 | 3.3 | -0.004 | 352 | 52% | 5.9 | 20.8 | nan | nan | nan | nan | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| barnative|TIME | 36204 | 81 | 2.6 | 0.005 | 644 | 52% | 3.7 | -95.0 | 184.4 | 209.8 | -181.8 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| manual|TIME | 11298 | 81 | -2.2 | 0.010 | 1095 | 51% | 80.8 | 109.8 | 138.2 | 150.7 | -140.5 | 0.00 | {"2023": "ok", "2024": "RED", "2025": "RED", "2026": "ok"} |
| pullback|TIME | 12348 | 81 | -3.6 | -0.015 | 725 | 47% | 45.2 | 30.5 | 219.7 | 230.2 | -223.3 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "ok"} |
| confluence|TIME | 7938 | 81 | -11.2 | -0.007 | 739 | 49% | -20.2 | -158.0 | 162.7 | 175.9 | -173.9 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "ok", "2026": "RED"} |
| trend|TIME | 4788 | 81 | -11.7 | 0.001 | 1553 | 40% | 63.0 | 75.4 | 143.9 | 156.4 | -155.6 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "ok"} |
| structure|TIME | 43155 | 81 | -17.4 | -0.028 | 1460 | 51% | 10.1 | 39.6 | 189.4 | 205.0 | -206.8 | 0.00 | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |
| tape|TIME | 4095 | 81 | -22.3 | -0.016 | 1547 | 48% | -15.2 | 122.8 | 36.9 | 43.3 | -59.2 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| structure (native)|TIME | 6048 | 81 | -28.1 | -0.025 | 1902 | 40% | 31.5 | 55.0 | 185.3 | 232.0 | -213.4 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |
| pullback (native)|TIME | 6048 | 81 | -50.1 | -0.050 | 2264 | 38% | -70.3 | -50.0 | 223.4 | 241.4 | -273.5 | 0.00 | {"2023": "RED", "2024": "RED", "2025": "RED", "2026": "RED"} |

## Top 20 cells at the newest pick window (by session; trigger.module.variant, exact params, bar row, bracket, side mode)
| session | rank | row | trigger | params | bracket | mode | L6M pts | L3M pts | trades | nb agree | by year pts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| London | 1 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4436 | 1366 | 530 | 1.00 | {"2023": -709.0, "2024": -651.0, "2025": 1201.0, "2026": 3773.0} |
| London | 2 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4067 | 1379 | 527 | 1.00 | {"2023": -533.0, "2024": -483.0, "2025": 638.0, "2026": 2933.0} |
| London | 3 | time_s_15 | structure.structure_breakout.fail2 | {"n": 20, "buf": 0.0} | asym10u/20u | both | 3840 | 2418 | 760 | 1.00 | {"2023": -1387.0, "2024": 528.0, "2025": -818.0, "2026": 2220.0} |
| London | 4 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | sym8u | both | 3824 | 1182 | 420 | 1.00 | {"2023": -1046.0, "2024": -14.0, "2025": -321.0, "2026": 2199.0} |
| London | 5 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.25} | sym8u | both | 3733 | 732 | 305 | 1.00 | {"2023": -176.0, "2024": 1019.0, "2025": 279.0, "2026": 2683.0} |
| London | 6 | tm60 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 3692 | 959 | 531 | 0.67 | {"2023": -773.0, "2024": -1418.0, "2025": -2762.0, "2026": 2065.0} |
| London | 7 | time_s_15 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.25} | sym15u | both | 3625 | 2376 | 602 | 0.75 | {"2023": -404.0, "2024": -728.0, "2025": -974.0, "2026": 2966.0} |
| London | 8 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | sym8u | both | 3620 | 1297 | 409 | 1.00 | {"2023": -259.0, "2024": 390.0, "2025": -541.0, "2026": 1970.0} |
| London | 9 | time_s_15 | structure.structure_breakout.fail2 | {"n": 10, "buf": 0.0} | asym10u/20u | both | 3606 | 1734 | 778 | 0.50 | {"2023": -1674.0, "2024": -1506.0, "2025": -130.0, "2026": 2913.0} |
| London | 10 | time_s_15 | tape.tape_libvol.adline | {"len": 20} | asym20u/10u | both | 3438 | 1646 | 835 | 1.00 | {"2023": -1496.0, "2024": -918.0, "2025": -746.0, "2026": 2966.0} |
| London | 11 | tm60 | structure.structure_libpattern.pin | {"k": 3.0, "filt": 0} | sym15u | both | 3430 | 771 | 285 | 0.67 | {"2023": -1917.0, "2024": -775.0, "2025": 432.0, "2026": 1786.0} |
| London | 12 | time_m_1 | manual.manual_cci.go | {"len": 34, "lvl": 100} | asym10u/20u | both | 3346 | 1278 | 304 | 1.00 | {"2023": -530.0, "2024": -1126.0, "2025": 553.0, "2026": 2522.0} |
| London | 13 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | asym20u/10u | both | 3342 | 821 | 284 | 1.00 | {"2023": -535.0, "2024": -711.0, "2025": 284.0, "2026": 2784.0} |
| London | 14 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 3329 | 324 | 538 | 0.67 | {"2023": -468.0, "2024": -1458.0, "2025": -1775.0, "2026": 1816.0} |
| London | 15 | time_s_15 | structure.structure_breakout.fail | {"n": 10, "buf": 0.0} | asym20u/10u | both | 3329 | 1244 | 912 | 0.50 | {"2023": -1323.0, "2024": -1117.0, "2025": -1819.0, "2026": 3650.0} |
| London | 16 | tm60 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.25} | sym8u | both | 3327 | 780 | 308 | 0.80 | {"2023": -61.0, "2024": 1027.0, "2025": 1609.0, "2026": 3297.0} |
| London | 17 | time_s_15 | barnative.barnative_delta.run | {"n": 5, "thr": 0.0} | plain60/60 | both | 3298 | 1038 | 738 | 1.00 | {"2023": -659.0, "2024": -201.0, "2025": -3204.0, "2026": 1394.0} |
| London | 18 | time_s_15 | structure.structure_level.round_break | {"grid": 50, "buf": 0.0} | sym30u | both | 3270 | 2580 | 320 | 1.00 | {"2023": 410.0, "2024": -1655.0, "2025": -859.0, "2026": 1670.0} |
| London | 19 | tm60 | structure.structure_libpattern.pin | {"k": 3.0, "filt": 0} | asym15u/30u | both | 3226 | 820 | 270 | 0.67 | {"2023": -2034.0, "2024": -1615.0, "2025": -89.0, "2026": 1691.0} |
| London | 20 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym30u | both | 3216 | 1264 | 288 | 0.67 | {"2023": -732.0, "2024": 872.0, "2025": -321.0, "2026": 2421.0} |
| NYAM | 1 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 6151 | 2822 | 348 | 0.50 | {"2023": 520.0, "2024": -1188.0, "2025": 336.0, "2026": 4836.0} |
| NYAM | 2 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 311.0, "2024": -1331.0, "2025": -406.0, "2026": 4722.0} |
| NYAM | 3 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 58.0, "2024": -1481.0, "2025": -181.0, "2026": 4722.0} |
| NYAM | 4 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 6143 | 2822 | 348 | 0.50 | {"2023": 614.0, "2024": -1423.0, "2025": -422.0, "2026": 4722.0} |
| NYAM | 5 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 6138 | 2822 | 348 | 0.50 | {"2023": -959.0, "2024": -1653.0, "2025": -153.0, "2026": 5234.0} |
| NYAM | 6 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | plain60/60 | both | 6062 | 3184 | 1446 | 1.00 | {"2023": -545.0, "2024": -1661.0, "2025": -1603.0, "2026": 5644.0} |
| NYAM | 7 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 5976 | 797 | 539 | 1.00 | {"2023": -2316.0, "2024": -537.0, "2025": -1936.0, "2026": 5304.0} |
| NYAM | 8 | tm180 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5939 | 2672 | 349 | 0.50 | {"2023": -1064.0, "2024": -1551.0, "2025": 841.0, "2026": 5025.0} |
| NYAM | 9 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | plain60/60 | both | 5606 | 3180 | 1466 | 1.00 | {"2023": -299.0, "2024": -2765.0, "2025": -1751.0, "2026": 3161.0} |
| NYAM | 10 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 5420 | 2692 | 339 | 0.50 | {"2023": -280.0, "2024": -2124.0, "2025": 730.0, "2026": 4008.0} |
| NYAM | 11 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -520.0, "2024": -2856.0, "2025": 398.0, "2026": 3887.0} |
| NYAM | 12 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -344.0, "2024": -2920.0, "2025": 35.0, "2026": 3887.0} |
| NYAM | 13 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 5412 | 2692 | 339 | 0.50 | {"2023": -278.0, "2024": -2903.0, "2025": 13.0, "2026": 3887.0} |
| NYAM | 14 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 5407 | 2692 | 339 | 0.50 | {"2023": -1276.0, "2024": -3174.0, "2025": 222.0, "2026": 4405.0} |
| NYAM | 15 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5381 | 2947 | 342 | 0.50 | {"2023": -783.0, "2024": -2840.0, "2025": 1106.0, "2026": 4355.0} |
| NYAM | 16 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 3.0} | asym15u/30u | both | 5120 | 1597 | 462 | 1.00 | {"2023": 360.0, "2024": -816.0, "2025": -782.0, "2026": 6796.0} |
| NYAM | 17 | time_s_15 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 3.0} | sym30u | both | 5099 | 1729 | 440 | 1.00 | {"2023": -717.0, "2024": -1409.0, "2025": -2281.0, "2026": 4694.0} |
| NYAM | 18 | time_s_15 | structure.structure_libpattern.engulf | {"filt": 0} | sym30u | both | 5002 | 506 | 484 | 1.00 | {"2023": -1410.0, "2024": 2292.0, "2025": 473.0, "2026": 6159.0} |
| NYAM | 19 | time_s_15 | structure.structure_breakout.fail2 | {"n": 10, "buf": 0.0} | plain60/60 | both | 4563 | 2592 | 1212 | 1.00 | {"2023": 1275.0, "2024": -331.0, "2025": -377.0, "2026": 3409.0} |
| NYAM | 20 | tm60 | structure.structure_libpattern.rangeexp | {"k": 1.5} | asym15u/30u | both | 4544 | 2089 | 450 | 1.00 | {"2023": 497.0, "2024": -394.0, "2025": 761.0, "2026": 4863.0} |
| NYPM | 1 | time_s_15 | trend.trend_libstack.ema_hold | {"len": 21, "hold": 5} | sym30u | both | 4698 | 226 | 326 | 0.67 | {"2023": -1184.0, "2024": -3588.0, "2025": -914.0, "2026": 5254.0} |
| NYPM | 2 | time_s_15 | manual.manual_cci.zero | {"len": 14} | plain60/60 | both | 4583 | 1565 | 868 | 1.00 | {"2023": 543.0, "2024": 520.0, "2025": 2156.0, "2026": 4755.0} |
| NYPM | 3 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | sym30u | both | 4483 | 1808 | 332 | 1.00 | {"2023": 299.0, "2024": -118.0, "2025": -344.0, "2026": 4547.0} |
| NYPM | 4 | time_m_1 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | plain60/60 | both | 4471 | 1879 | 831 | 1.00 | {"2023": 1297.0, "2024": -612.0, "2025": -1533.0, "2026": 4923.0} |
| NYPM | 5 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | asym15u/30u | both | 4460 | 1665 | 362 | 1.00 | {"2023": 945.0, "2024": -263.0, "2025": -2194.0, "2026": 4270.0} |
| NYPM | 6 | tm60 | manual.manual_macd.histturn | {"f": 12, "s": 26, "g": 9} | plain60/60 | both | 4441 | 1780 | 829 | 1.00 | {"2023": 778.0, "2024": 43.0, "2025": -222.0, "2026": 5554.0} |
| NYPM | 7 | time_s_15 | trend.trend_libstack.trendcolor | {"len": 13} | plain60/60 | both | 4307 | 2091 | 903 | 1.00 | {"2023": 696.0, "2024": 314.0, "2025": 2346.0, "2026": 3333.0} |
| NYPM | 8 | time_s_15 | trend.trend_libstack.wave_agree | {"set": "slow"} | sym15u | both | 4258 | 1232 | 404 | 1.00 | {"2023": 346.0, "2024": -688.0, "2025": -860.0, "2026": 3192.0} |
| NYPM | 9 | time_s_15 | manual.manual_cci.rev | {"len": 50, "lvl": 100} | sym30u | short | 4226 | 1938 | 289 | 1.00 | {"2023": -567.0, "2024": -292.0, "2025": 608.0, "2026": 4173.0} |
| NYPM | 10 | tm60 | manual.manual_macd.histturn | {"f": 8, "s": 17, "g": 9} | plain60/60 | both | 4141 | 1753 | 854 | 1.00 | {"2023": 295.0, "2024": -737.0, "2025": 604.0, "2026": 6355.0} |
| NYPM | 11 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | asym15u/30u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1845.0, "2024": -983.0, "2025": -341.0, "2026": 5134.0} |
| NYPM | 12 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | asym10u/20u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1841.0, "2024": -1000.0, "2025": -341.0, "2026": 5134.0} |
| NYPM | 13 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | asym20u/10u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1864.0, "2024": -1035.0, "2025": -341.0, "2026": 5134.0} |
| NYPM | 14 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | sym15u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1845.0, "2024": -983.0, "2025": -341.0, "2026": 5134.0} |
| NYPM | 15 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | sym30u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1845.0, "2024": -983.0, "2025": -341.0, "2026": 5134.0} |
| NYPM | 16 | tm600 | momentum.momentum_libosc.aroon | {"len": 10} | sym8u | both | 4087 | 2527 | 164 | 1.00 | {"2023": -1734.0, "2024": -1104.0, "2025": -339.0, "2026": 5134.0} |
| NYPM | 17 | time_s_15 | structure.structure_level.round_break | {"grid": 50, "buf": 0.5} | sym30u | short | 4036 | 1928 | 314 | 1.00 | {"2023": -360.0, "2024": 237.0, "2025": -341.0, "2026": 3495.0} |
| NYPM | 18 | time_s_15 | structure.structure_level.round_break | {"grid": 50, "buf": 0.25} | sym30u | both | 4025 | 951 | 324 | 1.00 | {"2023": -1385.0, "2024": 2041.0, "2025": -935.0, "2026": 4422.0} |
| NYPM | 19 | tm60 | manual.manual_macd.histturn_native | {"f": 5, "s": 13, "g": 4} | plain60/60 | both | 4021 | 2027 | 845 | 1.00 | {"2023": 421.0, "2024": 295.0, "2025": -772.0, "2026": 5179.0} |
| NYPM | 20 | time_s_15 | manual.manual_cci.rev | {"len": 50, "lvl": 150} | asym20u/10u | both | 4008 | 2537 | 502 | 0.50 | {"2023": -179.0, "2024": -1268.0, "2025": 169.0, "2026": 3618.0} |
