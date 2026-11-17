# DS3_GRIDB_FAMILIES - W-GRIDB trigger families on every bar row (naked bracket grid; harness W-GRIDA procedure restricted to my modules)
Five-line summary: (1) tried: pullback / structure / bar-native / manual-set / library-extras / confluence entry triggers recomputed on each bar row, 7 bracket sets, tape fills, 4.84 RT; (2) what holds: see the heat table (OOS mean pts/wk over rolling 2-week picks, excess over the best-pick null); (3) what does not: cells with excess <= 0 or RED years; (4) needs in DS7: DATA_NEED per trigger in REGISTRY_B.csv; (5) next: stage-2 confluence from families that beat the null, then layers + exact engine for the top cells.
Header: pick window end 2026-11-14 (trailing 26 weeks, 13 weeks beside), refit date 2026-11-22 (every 2 weeks), data end 2026-11-14 (last full week start 2026-11-08), prior-year check amber 15-30 / red >30 vs doing nothing; trials = param sets x rows x sessions x brackets x modes counted per pool (cells column); FIRST PASS, naked, NOT engine; nulls = harness random-clock tags (); best-pick fit corrected only by the null excess column.
updated 2026-11-17T20:18:21Z; COVERAGE real-tag result files 13 of 8019 (0%: my 27 modules x 297 bar rows); result files by tag {"real": 13}

## Heat table London (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|TIME | 4998 | 81 | 3.2 | 0.008 | 509 | 54% | 2.3 | -46.2 | nan | nan | nan | nan | {"2023": "RED", "2024": "ok", "2025": "ok", "2026": "AMBER"} |

## Heat table NYAM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|TIME | 4998 | 81 | 4.0 | 0.007 | 759 | 44% | -29.8 | -52.2 | nan | nan | nan | nan | {"2023": "RED", "2024": "ok", "2025": "RED", "2026": "RED"} |

## Heat table NYPM (agreed pick; pool = trigger family | bar family)
| pool | cells | rolls | OOS pts/wk | R/trade | ulcer pts | persistence | L6M | L3M | null mean | null max | excess | pctile | year flags |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| barnative|TIME | 4998 | 81 | -26.8 | -0.028 | 1332 | 48% | -64.8 | 41.4 | nan | nan | nan | nan | {"2023": "ok", "2024": "ok", "2025": "RED", "2026": "RED"} |

## Top 20 cells at the newest pick window (by session; trigger.module.variant, exact params, bar row, bracket, side mode)
| session | rank | row | trigger | params | bracket | mode | L6M pts | L3M pts | trades | nb agree | by year pts |
|---|---|---|---|---|---|---|---|---|---|---|---|
| London | 1 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | plain60/60 | both | 4067 | 1379 | 527 | 1.00 | {"2023": -533.0, "2024": -483.0, "2025": 638.0, "2026": 2933.0} |
| London | 2 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.25} | sym8u | both | 3733 | 732 | 305 | 1.00 | {"2023": -176.0, "2024": 1019.0, "2025": 279.0, "2026": 2683.0} |
| London | 3 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | sym8u | both | 3620 | 1297 | 409 | 1.00 | {"2023": -259.0, "2024": 390.0, "2025": -541.0, "2026": 1970.0} |
| London | 4 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 3329 | 324 | 538 | 0.67 | {"2023": -468.0, "2024": -1458.0, "2025": -1775.0, "2026": 1816.0} |
| London | 5 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym30u | both | 3216 | 1264 | 288 | 0.67 | {"2023": -732.0, "2024": 872.0, "2025": -321.0, "2026": 2421.0} |
| London | 6 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.5} | asym20u/10u | both | 3074 | 841 | 291 | 1.00 | {"2023": -151.0, "2024": 40.0, "2025": 702.0, "2026": 220.0} |
| London | 7 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym8u | both | 3006 | 573 | 536 | 0.67 | {"2023": -520.0, "2024": -1573.0, "2025": -2427.0, "2026": 2572.0} |
| London | 8 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | asym20u/10u | both | 2904 | 363 | 282 | 1.00 | {"2023": -286.0, "2024": -45.0, "2025": -256.0, "2026": 1603.0} |
| London | 9 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 2843 | 1919 | 557 | 1.00 | {"2023": 103.0, "2024": -2560.0, "2025": 261.0, "2026": 1481.0} |
| London | 10 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | plain60/60 | both | 2784 | 433 | 670 | 1.00 | {"2023": 115.0, "2024": 118.0, "2025": 1158.0, "2026": 809.0} |
| London | 11 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym15u/30u | both | 2734 | 972 | 297 | 0.67 | {"2023": -764.0, "2024": 825.0, "2025": -507.0, "2026": 1822.0} |
| London | 12 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | plain60/60 | both | 2714 | 1266 | 638 | 1.00 | {"2023": 11.0, "2024": -944.0, "2025": 1967.0, "2026": 1364.0} |
| London | 13 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.5} | sym30u | both | 2690 | 1173 | 255 | 1.00 | {"2023": -581.0, "2024": 441.0, "2025": 199.0, "2026": 1115.0} |
| London | 14 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.5} | asym15u/30u | both | 2685 | 1196 | 260 | 1.00 | {"2023": -951.0, "2024": 982.0, "2025": -306.0, "2026": 1445.0} |
| London | 15 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.5} | sym8u | both | 2617 | 728 | 410 | 1.00 | {"2023": -314.0, "2024": 1195.0, "2025": -989.0, "2026": 1052.0} |
| London | 16 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 2.0, "prog": 0.5} | sym15u | both | 2617 | 1244 | 267 | 1.00 | {"2023": -283.0, "2024": 1375.0, "2025": 880.0, "2026": 1008.0} |
| London | 17 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 2.0, "prog": 0.5} | asym15u/30u | both | 2576 | 484 | 246 | 1.00 | {"2023": -819.0, "2024": 211.0, "2025": -891.0, "2026": 1843.0} |
| London | 18 | time_m_1 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 2.0} | sym8u | both | 2558 | 291 | 499 | 0.50 | {"2023": -794.0, "2024": -606.0, "2025": -731.0, "2026": 2303.0} |
| London | 19 | time_m_3 | barnative.barnative_run.cont | {"n": 4} | asym20u/10u | both | 2542 | 1695 | 232 | 0.67 | {"2023": 862.0, "2024": -365.0, "2025": 2167.0, "2026": 2650.0} |
| London | 20 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | sym8u | both | 2531 | 815 | 252 | 1.00 | {"2023": -233.0, "2024": -182.0, "2025": -2159.0, "2026": 3932.0} |
| NYAM | 1 | time_m_1 | barnative.barnative_run.fade | {"n": 2} | sym8u | both | 5976 | 797 | 539 | 1.00 | {"2023": -2316.0, "2024": -537.0, "2025": -1936.0, "2026": 5304.0} |
| NYAM | 2 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym10u/20u | both | 5420 | 2692 | 339 | 0.67 | {"2023": -280.0, "2024": -2124.0, "2025": 730.0, "2026": 4008.0} |
| NYAM | 3 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym15u/30u | both | 5412 | 2692 | 339 | 0.67 | {"2023": -344.0, "2024": -2920.0, "2025": 35.0, "2026": 3887.0} |
| NYAM | 4 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym30u | both | 5412 | 2692 | 339 | 0.67 | {"2023": -278.0, "2024": -2903.0, "2025": 13.0, "2026": 3887.0} |
| NYAM | 5 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym15u | both | 5412 | 2692 | 339 | 0.67 | {"2023": -520.0, "2024": -2856.0, "2025": 398.0, "2026": 3887.0} |
| NYAM | 6 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | asym20u/10u | both | 5407 | 2692 | 339 | 0.67 | {"2023": -1276.0, "2024": -3174.0, "2025": 222.0, "2026": 4405.0} |
| NYAM | 7 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 1.5} | sym8u | both | 5381 | 2947 | 342 | 0.67 | {"2023": -783.0, "2024": -2840.0, "2025": 1106.0, "2026": 4355.0} |
| NYAM | 8 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym8u | both | 4240 | 2948 | 324 | 0.67 | {"2023": -406.0, "2024": -1521.0, "2025": 875.0, "2026": 4112.0} |
| NYAM | 9 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym10u/20u | both | 3979 | 2602 | 321 | 0.67 | {"2023": -199.0, "2024": -757.0, "2025": 249.0, "2026": 3365.0} |
| NYAM | 10 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym30u | both | 3972 | 2602 | 321 | 0.67 | {"2023": -208.0, "2024": -1762.0, "2025": -392.0, "2026": 3258.0} |
| NYAM | 11 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym15u/30u | both | 3972 | 2602 | 321 | 0.67 | {"2023": -326.0, "2024": -1918.0, "2025": -352.0, "2026": 3258.0} |
| NYAM | 12 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | sym15u | both | 3972 | 2602 | 321 | 0.67 | {"2023": -540.0, "2024": -1788.0, "2025": 10.0, "2026": 3258.0} |
| NYAM | 13 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 20, "dz": 1.5} | asym20u/10u | both | 3967 | 2602 | 321 | 0.67 | {"2023": -981.0, "2024": -1970.0, "2025": 0.0, "2026": 3797.0} |
| NYAM | 14 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 2.0} | sym8u | both | 3412 | 1962 | 301 | 0.75 | {"2023": -656.0, "2024": -1986.0, "2025": 1581.0, "2026": 3389.0} |
| NYAM | 15 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | asym10u/20u | both | 3197 | 2241 | 396 | 0.50 | {"2023": -1383.0, "2024": -2397.0, "2025": -1130.0, "2026": 2828.0} |
| NYAM | 16 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | sym15u | both | 3189 | 2241 | 396 | 0.50 | {"2023": -1746.0, "2024": -2655.0, "2025": -839.0, "2026": 2901.0} |
| NYAM | 17 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | asym15u/30u | both | 3189 | 2241 | 396 | 0.50 | {"2023": -1508.0, "2024": -3021.0, "2025": -1003.0, "2026": 2901.0} |
| NYAM | 18 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | sym30u | both | 3189 | 2241 | 396 | 0.50 | {"2023": -1368.0, "2024": -2969.0, "2025": -996.0, "2026": 2901.0} |
| NYAM | 19 | time_m_3 | barnative.barnative_run.rev | {"n": 2} | asym20u/10u | both | 3184 | 2241 | 396 | 0.50 | {"2023": -1289.0, "2024": -3097.0, "2025": -1277.0, "2026": 3095.0} |
| NYAM | 20 | time_m_3 | barnative.barnative_absorb.exhaust | {"len": 50, "dz": 2.0} | asym10u/20u | both | 3173 | 1638 | 298 | 0.75 | {"2023": -395.0, "2024": -1118.0, "2025": 679.0, "2026": 2377.0} |
| NYPM | 1 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | sym8u | both | 3316 | 2150 | 319 | 1.00 | {"2023": -1393.0, "2024": 1833.0, "2025": -1000.0, "2026": 4480.0} |
| NYPM | 2 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | sym15u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -689.0, "2024": -671.0, "2025": 256.0, "2026": 3311.0} |
| NYPM | 3 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | asym10u/20u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -641.0, "2024": -671.0, "2025": 214.0, "2026": 3311.0} |
| NYPM | 4 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | asym20u/10u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -734.0, "2024": -591.0, "2025": 240.0, "2026": 3311.0} |
| NYPM | 5 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | sym8u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -933.0, "2024": -522.0, "2025": 276.0, "2026": 3311.0} |
| NYPM | 6 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | sym30u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -689.0, "2024": -671.0, "2025": 256.0, "2026": 3311.0} |
| NYPM | 7 | time_m_3 | barnative.barnative_absorb.absorb | {"len": 50, "dz": 1.5, "prog": 0.5} | asym15u/30u | short | 3144 | 1521 | 131 | 1.00 | {"2023": -689.0, "2024": -671.0, "2025": 256.0, "2026": 3311.0} |
| NYPM | 8 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | asym10u/20u | both | 3068 | 2110 | 279 | 1.00 | {"2023": -517.0, "2024": 2124.0, "2025": -2438.0, "2026": 4577.0} |
| NYPM | 9 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | asym15u/30u | both | 3022 | 2081 | 277 | 1.00 | {"2023": -510.0, "2024": 2577.0, "2025": -1682.0, "2026": 4830.0} |
| NYPM | 10 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | sym30u | both | 3003 | 2063 | 277 | 1.00 | {"2023": -760.0, "2024": 2550.0, "2025": -1773.0, "2026": 4804.0} |
| NYPM | 11 | time_m_1 | barnative.barnative_absorb.absorb | {"len": 20, "dz": 1.5, "prog": 0.5} | sym15u | both | 3003 | 2062 | 277 | 1.00 | {"2023": -375.0, "2024": 2186.0, "2025": -1814.0, "2026": 4738.0} |
| NYPM | 12 | time_m_1 | barnative.barnative_avwap.cross | {"anchor": "ny", "k": 0.0} | sym30u | both | 2955 | 1131 | 106 | 0.67 | {"2023": -357.0, "2024": 1573.0, "2025": 354.0, "2026": 2533.0} |
| NYPM | 13 | time_m_1 | barnative.barnative_avwap.cross | {"anchor": "ny", "k": 0.0} | asym15u/30u | both | 2903 | 1079 | 106 | 0.67 | {"2023": -557.0, "2024": 1496.0, "2025": 338.0, "2026": 2481.0} |
| NYPM | 14 | time_m_1 | barnative.barnative_avwap.cross | {"anchor": "ny", "k": 0.0} | sym15u | both | 2885 | 1061 | 106 | 0.67 | {"2023": -702.0, "2024": 1433.0, "2025": 214.0, "2026": 2428.0} |
| NYPM | 15 | time_m_1 | barnative.barnative_avwap.cross | {"anchor": "ny", "k": 0.0} | asym20u/10u | both | 2871 | 1047 | 106 | 0.67 | {"2023": -1061.0, "2024": 1576.0, "2025": 124.0, "2026": 2568.0} |
| NYPM | 16 | time_m_1 | barnative.barnative_avwap.cross | {"anchor": "ny", "k": 0.0} | asym10u/20u | both | 2867 | 1028 | 108 | 0.67 | {"2023": -405.0, "2024": 1478.0, "2025": 611.0, "2026": 2466.0} |
| NYPM | 17 | time_m_1 | barnative.barnative_run.rev | {"n": 2} | sym8u | short | 2841 | 1581 | 345 | 1.00 | {"2023": -633.0, "2024": 278.0, "2025": -1900.0, "2026": 2318.0} |
| NYPM | 18 | time_m_1 | barnative.barnative_run.rev | {"n": 2} | sym15u | short | 2823 | 1504 | 314 | 1.00 | {"2023": -413.0, "2024": 245.0, "2025": -984.0, "2026": 1901.0} |
| NYPM | 19 | time_m_1 | barnative.barnative_run.rev | {"n": 2} | asym15u/30u | short | 2823 | 1504 | 314 | 1.00 | {"2023": -441.0, "2024": 177.0, "2025": -1034.0, "2026": 1864.0} |
| NYPM | 20 | time_m_1 | barnative.barnative_run.rev | {"n": 2} | sym30u | short | 2820 | 1500 | 313 | 1.00 | {"2023": -456.0, "2024": 169.0, "2025": -970.0, "2026": 1863.0} |
