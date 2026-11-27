# FLATTEN quick screen, Asia (W-PLAN-AS, order 0914Z S1-S4; bare, all events one-position, 1-s NQ, no Trade Health; REF = flatten at the bell; hard flat 16:55 ET of the bell date). Raw output of code/th_planas/flatten_study.py AS on server C
AS events 19203 hard<=bell (no carry room): 1
### AS: variants vs REF = flatten at the bell, bare, all events one-position; wk/DD in $, income ratio vs REF; year incomes in $k
REF flatten                n  6373 car    0 | inc 1.00 ( 2564852) DD  -173163 (1.00) wk -139123 | L6 1134853/ -64656 L3  439633/ -64656 |  0  0  0 ---- | {2023: 193, 2024: 414, 2025: 635, 2026: 1456}
S1a carry all              n  6373 car 2138 | inc 0.90 ( 2319932) DD  -184967 (1.07) wk -106123 | L6 1281523/ -62160 L3  469993/ -62160 |  3  2  5 ---- | {2023: 147, 2024: 148, 2025: 461, 2026: 1657}
S1b carry if >=0           n  6373 car 1277 | inc 0.98 ( 2509352) DD  -154672 (0.89) wk  -99793 | L6 1253173/ -60126 L3  426973/ -60126 |  3  3  5 ---- | {2023: 221, 2024: 293, 2025: 455, 2026: 1628}
S1c carry if >=.25R        n  6373 car  807 | inc 1.03 ( 2651672) DD  -149540 (0.86) wk -122353 | L6 1157503/ -60126 L3  399193/ -60126 |  2  4  5 ---- | {2023: 274, 2024: 353, 2025: 565, 2026: 1558}
S1d carry all +BE          n  6373 car 2138 | inc 1.04 ( 2656922) DD  -160989 (0.93) wk -133513 | L6 1195513/ -60126 L3  442183/ -60126 |  5  3  5 ---- | {2023: 256, 2024: 349, 2025: 659, 2026: 1514}
S1e carry all +half stop   n  6373 car 2138 | inc 1.02 ( 2616662) DD  -177309 (1.02) wk -140773 | L6 1269493/ -57480 L3  525103/ -57480 |  3  2  6 ---- | {2023: 268, 2024: 336, 2025: 511, 2026: 1598}
S1f carry all max30        n  6373 car 2138 | inc 1.06 ( 2722772) DD  -173583 (1.00) wk -138493 | L6 1207573/ -56466 L3  467113/ -56466 |  6  6 10 PASS | {2023: 198, 2024: 415, 2025: 664, 2026: 1570}
S1f carry all max60        n  6373 car 2138 | inc 1.12 ( 2880512) DD  -160610 (0.93) wk -129463 | L6 1217083/ -63688 L3  465193/ -63688 |  8  5 10 PASS | {2023: 211, 2024: 457, 2025: 727, 2026: 1612}
S1f carry all max120       n  6373 car 2138 | inc 1.15 ( 2939072) DD  -150530 (0.87) wk -119383 | L6 1243543/ -57538 L3  470623/ -57538 |  6  6  9 PASS | {2023: 224, 2024: 482, 2025: 712, 2026: 1613}
S1b+BE carry>=0 +BE        n  6373 car 1277 | inc 1.04 ( 2654822) DD  -161739 (0.93) wk -134113 | L6 1193743/ -60126 L3  442243/ -60126 |  5  2  5 ---- | {2023: 257, 2024: 348, 2025: 656, 2026: 1513}
S1c+BE carry>=.25R +BE     n  6373 car  807 | inc 1.04 ( 2674082) DD  -165039 (0.95) wk -137413 | L6 1192873/ -60126 L3  438973/ -60126 |  4  3  6 ---- | {2023: 267, 2024: 361, 2025: 649, 2026: 1514}
carry>=.25R max90 [my label, not W-DYNH c90 cut rule] n  6373 car  807 | inc 1.07 ( 2747102) DD  -158000 (0.91) wk -130813 | L6 1167943/ -60126 L3  424813/ -60126 |  8  8  6 ---- | {2023: 173, 2024: 484, 2025: 622, 2026: 1570}
S3 mgmt T15                n  6560 car    0 | inc 0.96 ( 2468394) DD  -180501 (1.04) wk -139213 | L6 1065843/ -71274 L3  379280/ -71274 |  5  3  7 ---- | {2023: 171, 2024: 406, 2025: 661, 2026: 1362}
S3 mgmt T30                n  6839 car    0 | inc 0.89 ( 2285834) DD  -171800 (0.99) wk -118303 | L6  985716/ -70554 L3  331478/ -70554 |  6  5  2 ---- | {2023: 164, 2024: 337, 2025: 581, 2026: 1296}
S3 mgmt T60                n  7335 car    0 | inc 0.77 ( 1968988) DD  -176626 (1.02) wk -136061 | L6  966219/ -79805 L3  292479/ -79805 |  8  6  3 ---- | {2023: 118, 2024: 307, 2025: 411, 2026: 1190}
S4 bell +30 min            n  6373 car    0 | inc 1.06 ( 2722772) DD  -173583 (1.00) wk -138493 | L6 1207573/ -56466 L3  467113/ -56466 |  6  6 10 PASS | {2023: 198, 2024: 415, 2025: 664, 2026: 1570}
S4 bell +60 min            n  6373 car    0 | inc 1.12 ( 2880512) DD  -160610 (0.93) wk -129463 | L6 1217083/ -63688 L3  465193/ -63688 |  8  5 10 PASS | {2023: 211, 2024: 457, 2025: 727, 2026: 1612}
S4 bell +90 min            n  6373 car    0 | inc 1.11 ( 2851112) DD  -155450 (0.90) wk -124303 | L6 1214173/ -57538 L3  455773/ -57538 |  8  4  9 PASS | {2023: 199, 2024: 521, 2025: 641, 2026: 1585}
S2 skip late (median-p50)  n  5775 car    0 | inc 0.93 ( 2372808) DD  -165087 (0.95) wk -136134 | L6 1060608/ -64567 L3  401437/ -64567 |  7  5  3 ---- | {2023: 182, 2024: 408, 2025: 550, 2026: 1350}
S2 late at half size p50   n  6373 car    0 | inc 0.96 ( 2468830) DD  -167751 (0.97) wk -137628 | L6 1097730/ -64611 L3  420535/ -64611 |  8  6  3 ---- | {2023: 187, 2024: 411, 2025: 592, 2026: 1403}
S2 skip late (median-p75)  n  5137 car    0 | inc 0.79 ( 2016268) DD  -182020 (1.05) wk -141064 | L6  955054/ -63519 L3  336803/ -63519 | 10  7  4 ---- | {2023: 165, 2024: 435, 2025: 390, 2026: 1119}
S2 late at half size p75   n  6373 car    0 | inc 0.89 ( 2290560) DD  -176218 (1.02) wk -140094 | L6 1044953/ -64087 L3  388218/ -64087 | 11  8  4 ---- | {2023: 179, 2024: 424, 2025: 513, 2026: 1288}
### pessimistic label (stop slip by lots), reference also stressed
S1a carry all STRESS       n  6373 car 2138 | inc 0.94 ( 1938940) DD  -217599 (1.19) wk -112301 | L6 1188146/ -64774 L3  426393/ -64774 |  3  2  5 ---- | {2023: 103, 2024: 64, 2025: 337, 2026: 1515}
S1b carry if >=0 STRESS    n  6373 car 1277 | inc 1.02 ( 2099016) DD  -178788 (0.97) wk -106090 | L6 1156945/ -62383 L3  381591/ -62383 |  4  2  6 ---- | {2023: 168, 2024: 201, 2025: 323, 2026: 1481}
S1c carry if >=.25R STRESS n  6373 car  807 | inc 1.07 ( 2215794) DD  -158094 (0.86) wk -129006 | L6 1057592/ -62383 L3  352386/ -62383 |  3  4  5 ---- | {2023: 214, 2024: 254, 2025: 427, 2026: 1406}
S1d carry all +BE STRESS   n  6373 car 2138 | inc 1.07 ( 2205125) DD  -172750 (0.94) wk -140285 | L6 1094533/ -62383 L3  394782/ -62383 |  5  3  5 ---- | {2023: 192, 2024: 244, 2025: 517, 2026: 1359}
S1f carry all max60 STRESS n  6373 car 2138 | inc 1.17 ( 2415528) DD  -169045 (0.92) wk -136116 | L6 1118122/ -66658 L3  419336/ -66658 |  8  5 10 PASS | {2023: 139, 2024: 346, 2025: 583, 2026: 1459}
carry>=.25R max90 [my label, not W-DYNH c90 cut rule] STRESS n  6373 car  807 | inc 1.10 ( 2282237) DD  -166673 (0.91) wk -137585 | L6 1066250/ -62383 L3  377412/ -62383 |  8  7  6 ---- | {2023: 103, 2024: 374, 2025: 477, 2026: 1415}
S3 mgmt T30 STRESS         n  6839 car    0 | inc 0.83 ( 1721652) DD  -186056 (1.01) wk -125431 | L6  866560/ -74118 L3  274572/ -74118 |  5  5  2 ---- | {2023: 73, 2024: 203, 2025: 407, 2026: 1114}
S4 +30 STRESS              n  6373 car    0 | inc 1.09 ( 2244839) DD  -183562 (1.00) wk -145265 | L6 1105642/ -58604 L3  419593/ -58604 |  6  6 10 PASS | {2023: 125, 2024: 301, 2025: 515, 2026: 1413}
S4 +60 STRESS              n  6373 car    0 | inc 1.17 ( 2415528) DD  -169045 (0.92) wk -136116 | L6 1118122/ -66658 L3  419336/ -66658 |  8  5 10 PASS | {2023: 139, 2024: 346, 2025: 583, 2026: 1459}
S4 +90 STRESS              n  6373 car    0 | inc 1.17 ( 2407275) DD  -163766 (0.89) wk -130837 | L6 1116638/ -60271 L3  410391/ -60271 |  7  6  9 PASS | {2023: 133, 2024: 418, 2025: 502, 2026: 1436}
### random-carry null (same number carried, random among the trades open at the bell under REF flatten), 40 draws
S1b carry if >=0             carried 1277 of 2139 open at bell | plan inc 2509352 DD -154672 wk -99793 | null mean inc 2460763 DD -158863 wk -119964 | plan beats null: inc 0.53 DD 0.60 wk 1.00
S1c carry if >=.25R          carried 807 of 2139 open at bell | plan inc 2651672 DD -149540 wk -122353 | null mean inc 2485298 DD -158863 wk -125194 | plan beats null: inc 0.95 DD 0.78 wk 0.55
carry>=.25R max90 [my label, not W-DYNH c90 cut rule]   carried 807 of 2139 open at bell | plan inc 2747102 DD -158000 wk -130813 | null mean inc 2666252 DD -167150 wk -134079 | plan beats null: inc 0.80 DD 0.90 wk 0.65
S1a carry all                carried 2138 of 2139 open at bell | plan inc 2319932 DD -184967 wk -106123 | null mean inc 2318327 DD -185392 wk -106123 | plan beats null: inc 0.57 DD 0.20 wk 0.00
### per book (income/DD/worst wk vs REF)
  S1a carry all          MF1 inc 0.78 DD 1.90 wk 0.89
  S1a carry all          MF2 inc 0.80 DD 1.78 wk 1.39
  S1a carry all          MF3 inc 1.13 DD 1.29 wk 0.84
  S1a carry all          MF4 inc 0.92 DD 2.53 wk 1.61
  S1b carry if >=0       MF1 inc 0.94 DD 1.54 wk 0.89
  S1b carry if >=0       MF2 inc 0.90 DD 1.47 wk 1.14
  S1b carry if >=0       MF3 inc 1.09 DD 1.11 wk 0.84
  S1b carry if >=0       MF4 inc 0.96 DD 1.38 wk 1.45
  S1c carry if >=.25R    MF1 inc 1.08 DD 1.18 wk 0.89
  S1c carry if >=.25R    MF2 inc 0.96 DD 1.09 wk 1.07
  S1c carry if >=.25R    MF3 inc 1.04 DD 0.95 wk 0.93
  S1c carry if >=.25R    MF4 inc 1.00 DD 1.64 wk 1.45
### REF P&L by exit kind and year ($k): 1 stop 2 target 3 bell flatten
kind       1       2      3
tx                         
2023  -407.0   380.0  220.0
2024 -1735.0  1734.0  414.0
2025 -3664.0  3918.0  382.0
2026 -5301.0  6415.0  342.0
bell-flatten trades: n 2139 net $1358083 ; open R at bell median 0.09 p25 -0.19 p75 0.45 (in points 3.8)
