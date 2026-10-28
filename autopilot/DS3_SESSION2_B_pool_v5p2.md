# DS3_SESSION2_B_pool_v5p2 - Pool family V5P2 entry-clock re-run and session scoring

Written 2026-10-28T21:14:25Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/pool_v5p2/. Prereg l2vast/ds3/prereg/SB3_pool_v5p2_prereg.md sha256 2f2c72e1ee2405c856b8487f53c9c43b76bf27c8ecf4989962e0c7c32660aa84; PREHOLD autopilot/DS3_SESSION2_B_pool_v5p2_PREHOLD.md sha256 0b20bbc42e6af69a5de1a03af1f4b1f3e05a51bdf701fbe250c53d6c552d1e09 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original core (run_cell -> trade records: exit bar, net $, entry bar index) for every grid cell of the pool family; entry time = ET minute of the entry bar (HM) on the label-day calendar (label day minus one calendar day for minutes >= 18:00), pnl = net $ per trade as in the pool series (instrument costs, NT8sim fills: MAPPED, not direct), lots = contracts. Side is not carried by the trade record (stored as 0), so the overlap-cluster Jaccard uses entry minute only (clusters are a conservative merge). Cell label column shows the original pool name and pool tier (F-* = failed pooled, T1/T2 = passed pooled). Entries are bar-level market entries; exits opp/trail/time are dynamic, brk is a fixed stop=target bracket (par x BS points).

Reproduction: the daily $ series of every cell equals the stored series (real_*.pkl X) for all days up to 2026-10-13 (rtol 1e-4) and, for C5/C7/C10, the stored 2013-2022 trade count; the stored pickles predate the 2026-10-19 end-of-day fix and the series extension, so the re-run uses ENDI_LEGACY and is compared only up to 2026-10-13 (the window used here ends 2026-02-06). All cells checked, rates in out/sb3/pool_<mod>/repro_*.json.

## 2. Multiplicity and counts
- Cells 2016; F = cells x 7 sessions = **14112**; overlap clusters (Jaccard >= 0.5, PRE entries) **1346**, F_eff = **9422**. Independent (cluster x session) PRE tests with n >= 100: 4556; PRE-selected cell-sessions 122 = 116 independent (chance at 2.5% one-sided = about 114).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 49, DEAD-IN-HOLD 73; alive cells 43, alive clusters 42. HOLD sign persistence of the selected list: 77%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 1271 | 21 | 20 | 13 | 0 | 12 | V5P2_NQ_1652 | 2336 | 2476 |
| LONDON | 02:00-08:30 | 1324 | 11 | 10 | 0 | 0 | 0 | - |  |  |
| PREOPEN | 08:30-09:30 | 218 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 1223 | 53 | 50 | 25 | 0 | 25 | V5P2_NQ_627 | 1825 | 1558 |
| NY-PM | 12:00-15:00 | 1056 | 7 | 7 | 0 | 0 | 0 | - |  |  |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 1327 | 30 | 29 | 11 | 0 | 11 | V5P2_NQ_393 | 2357 | 2273 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V5P2_NQ_1446 | NY-AM | 244 | 3.25 | 1553 | 1318 | 3.30 | 0.59 | 102 | 1668 | 2198 | -1666 | 589 | 574 | 1208 | 2191 | -1666 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1040 | 334 |
| V5P2_NQ_627 | NY-AM | 267 | 3.56 | 1825 | 1558 | 3.28 | 0.60 | 116 | 1483 | 1432 | 1829 | 525 | 494 | 1375 | 2035 | 1829 | SESSION-CANDIDATE |  | BOF:not cleared | 1115 | 1049 |
| V5P2_NQ_511 | NY | 173 | 2.31 | 3531 | 3094 | 3.20 | 0.62 | 75.0 | -518 | -466 | -792 | 1079 | 2096 | 1557 | 2569 | -792 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 202 | 961 |
| V5P2_NQ_1570 | NY | 721 | 9.61 | 1106 | 1024 | 3.02 | 0.53 | 302 | 471 | 820 | -1577 | -144 | -304 | 827 | 1258 | -1577 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1106 | 421 |
| V5P2_NQ_1570 | NY-AM | 360 | 4.80 | 2085 | 1936 | 3.02 | 0.55 | 147 | 981 | 2002 | -5894 | -804 | -931 | 1525 | 2496 | -5894 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1106 | 421 |
| V5P2_NQ_393 | NY | 344 | 4.59 | 2357 | 2273 | 2.90 | 0.56 | 144 | 939 | 708 | 2097 | -888 | -821 | 2073 | 1520 | 2097 | SESSION-CANDIDATE |  | BOF:not cleared | 2357 | 864 |
| V5P2_NQ_30 | LONDON | 361 | 4.81 | 2710 | 2635 | 2.88 | 0.51 | 160 | 508 | 1464 | -3811 | 155 | 407 | 1368 | 2998 | -3811 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 597 | 792 |
| V5P2_NQ_1615 | NY-AM | 260 | 3.47 | 1495 | 1454 | 2.88 | 0.58 | 121 | 906 | 487 | 4715 | 330 | 433 | 1109 | 1139 | 4715 | SESSION-CANDIDATE |  | BOF:not cleared | 430 | 457 |
| V5P2_NQ_490 | LONDON | 507 | 6.76 | 1861 | 1826 | 2.85 | 0.53 | 214 | -939 | -1752 | 3218 | -366 | -443 | 1512 | 230 | 3218 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 417 | 946 |
| V5P2_NQ_489 | LONDON | 507 | 6.76 | 1861 | 1826 | 2.85 | 0.53 | 214 | -939 | -1752 | 3218 | -366 | -443 | 1512 | 230 | 3218 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -25.2 | 946 |
| V5P2_NQ_1174 | NY | 311 | 4.15 | 1272 | 1271 | 2.80 | 0.57 | 116 | -95.6 | 1.48 | -661 | 272 | 204 | 1033 | 881 | -661 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 1272 | 123 |
| V5P2_NQ_981 | LONDON | 578 | 7.71 | 925 | 938 | 2.76 | 0.55 | 250 | -177 | -402 | 569 | 606 | 844 | 612 | 527 | 569 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 253 | 1328 |
| V5P2_NQ_612 | NY-AM | 234 | 3.12 | 2505 | 2571 | 2.73 | 0.58 | 88.0 | 3501 | 3185 | 5502 | -494 | -714 | 2305 | 2973 | 5502 | SESSION-CANDIDATE |  | BOF:not cleared | 99.3 | 1040 |
| V5P2_NQ_1446 | NY | 398 | 5.31 | 1040 | 1096 | 2.66 | 0.56 | 153 | 1140 | 1357 | -227 | 4.23 | 41.7 | 727 | 1410 | -227 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1040 | 334 |
| V5P2_NQ_1583 | NY-AM | 381 | 5.08 | 1197 | 1261 | 2.66 | 0.57 | 155 | -228 | 62.8 | -1813 | -12.8 | -145 | 911 | 926 | -1813 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 500 | 433 |
| V5P2_NQ_1964 | NY-AM | 158 | 2.11 | 2106 | 2225 | 2.65 | 0.62 | 62.0 | -613 | -519 | -1164 | 52.9 | -373 | 2531 | 533 | -1164 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 962 | 573 |
| V5P2_NQ_627 | NY | 434 | 5.79 | 1115 | 1181 | 2.64 | 0.56 | 171 | 855 | 552 | 2710 | 70.5 | 39.5 | 903 | 1001 | 2710 | SESSION-CANDIDATE |  | BOF:not cleared | 1115 | 1049 |
| V5P2_NQ_1652 | ASIA | 200 | 2.67 | 2336 | 2476 | 2.64 | 0.59 | 104 | 567 | 577 | 532 | 1479 | 1230 | 1638 | 2117 | 532 | SESSION-CANDIDATE |  | BOF:not cleared | 563 | 477 |
| V5P2_NQ_797 | NY-AM | 229 | 3.05 | 1535 | 1634 | 2.63 | 0.59 | 107 | 136 | -33.1 | 974 | -644 | -754 | 1522 | 644 | 974 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 379 | 1188 |
| V5P2_NQ_587 | NY-AM | 325 | 4.33 | 1984 | 2125 | 2.61 | 0.57 | 149 | -348 | -1210 | 3549 | -688 | -361 | 1156 | 771 | 3549 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 849 | 1018 |
| V5P2_NQ_945 | NY-AM | 157 | 2.09 | 2393 | 2573 | 2.60 | 0.58 | 64.0 | 586 | 569 | 700 | 199 | 408 | 2200 | 1486 | 700 | SESSION-CANDIDATE |  | BOF:not cleared | 161 | 1299 |
| V5P2_NQ_777 | ASIA | 291 | 3.88 | 2227 | 2397 | 2.60 | 0.55 | 128 | 1191 | 905 | 2651 | 521 | 106 | 2515 | 1429 | 2651 | SESSION-CANDIDATE |  | BOF:not cleared | 1200 | 1176 |
| V5P2_NQ_266 | NY-AM | 261 | 3.48 | 2219 | 2392 | 2.60 | 0.58 | 112 | 940 | 568 | 3178 | 138 | -135 | 1851 | 1790 | 3178 | SESSION-CANDIDATE |  | BOF:not cleared | 1569 | 768 |
| V5P2_NQ_797 | NY | 464 | 6.19 | 1178 | 1277 | 2.58 | 0.57 | 180 | 682 | 225 | 2964 | 357 | 95.0 | 1041 | 984 | 2964 | SESSION-CANDIDATE |  | BOF:not cleared | 379 | 1188 |
| V5P2_NQ_1239 | NY-AM | 281 | 3.75 | 1145 | 1243 | 2.58 | 0.44 | 129 | 226 | 711 | -2418 | -510 | -380 | 1243 | 541 | -2418 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 475 | 174 |
| V5P2_NQ_622 | NY-AM | 299 | 3.99 | 2521 | 2752 | 2.57 | 0.43 | 129 | 988 | 1062 | 422 | -579 | -835 | 2246 | 1997 | 422 | SESSION-CANDIDATE |  | BOF:not cleared | 919 | 1046 |
| V5P2_NQ_403 | ASIA | 702 | 9.36 | 763 | 844 | 2.53 | 0.40 | 321 | 164 | 282 | -525 | -79.8 | -57.9 | 324 | 835 | -525 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 117 | 871 |
| V5P2_NQ_743 | LONDON | 222 | 2.96 | 2693 | 2982 | 2.53 | 0.60 | 116 | -651 | -1484 | 1965 | 768 | 3075 | 2059 | 677 | 1965 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 321 | 1147 |
| V5P2_NQ_1651 | ASIA | 236 | 3.15 | 1768 | 1974 | 2.51 | 0.44 | 125 | 988 | 940 | 1190 | -2.49 | -89.7 | 665 | 2247 | 1190 | SESSION-CANDIDATE |  | BOF:not cleared | 199 | 477 |
| V5P2_NQ_1169 | NY-AM | 280 | 3.73 | 1357 | 1545 | 2.46 | 0.58 | 117 | 1130 | 1027 | 1829 | 370 | 270 | 1550 | 1038 | 1829 | SESSION-CANDIDATE |  | BOF:not cleared | 870 | 119 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V5P2_NQ_1446 | NY-AM | 244 | 3.25 | 1553 | 1318 | 3.30 | 0.59 | 102 | 1668 | 2198 | -1666 | 589 | 574 | 1208 | 2191 | -1666 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1040 | 334 |
| V5P2_NQ_627 | NY-AM | 267 | 3.56 | 1825 | 1558 | 3.28 | 0.60 | 116 | 1483 | 1432 | 1829 | 525 | 494 | 1375 | 2035 | 1829 | SESSION-CANDIDATE |  | BOF:not cleared | 1115 | 1049 |
| V5P2_NQ_511 | NY | 173 | 2.31 | 3531 | 3094 | 3.20 | 0.62 | 75.0 | -518 | -466 | -792 | 1079 | 2096 | 1557 | 2569 | -792 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 202 | 961 |
| V5P2_NQ_1570 | NY | 721 | 9.61 | 1106 | 1024 | 3.02 | 0.53 | 302 | 471 | 820 | -1577 | -144 | -304 | 827 | 1258 | -1577 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 1106 | 421 |
| V5P2_NQ_393 | NY | 344 | 4.59 | 2357 | 2273 | 2.90 | 0.56 | 144 | 939 | 708 | 2097 | -888 | -821 | 2073 | 1520 | 2097 | SESSION-CANDIDATE |  | BOF:not cleared | 2357 | 864 |
| V5P2_NQ_30 | LONDON | 361 | 4.81 | 2710 | 2635 | 2.88 | 0.51 | 160 | 508 | 1464 | -3811 | 155 | 407 | 1368 | 2998 | -3811 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 597 | 792 |
| V5P2_NQ_1615 | NY-AM | 260 | 3.47 | 1495 | 1454 | 2.88 | 0.58 | 121 | 906 | 487 | 4715 | 330 | 433 | 1109 | 1139 | 4715 | SESSION-CANDIDATE |  | BOF:not cleared | 430 | 457 |
| V5P2_NQ_490 | LONDON | 507 | 6.76 | 1861 | 1826 | 2.85 | 0.53 | 214 | -939 | -1752 | 3218 | -366 | -443 | 1512 | 230 | 3218 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 417 | 946 |
| V5P2_NQ_1174 | NY | 311 | 4.15 | 1272 | 1271 | 2.80 | 0.57 | 116 | -95.6 | 1.48 | -661 | 272 | 204 | 1033 | 881 | -661 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 1272 | 123 |
| V5P2_NQ_981 | LONDON | 578 | 7.71 | 925 | 938 | 2.76 | 0.55 | 250 | -177 | -402 | 569 | 606 | 844 | 612 | 527 | 569 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 253 | 1328 |
| V5P2_NQ_612 | NY-AM | 234 | 3.12 | 2505 | 2571 | 2.73 | 0.58 | 88.0 | 3501 | 3185 | 5502 | -494 | -714 | 2305 | 2973 | 5502 | SESSION-CANDIDATE |  | BOF:not cleared | 99.3 | 1040 |
| V5P2_NQ_1583 | NY-AM | 381 | 5.08 | 1197 | 1261 | 2.66 | 0.57 | 155 | -228 | 62.8 | -1813 | -12.8 | -145 | 911 | 926 | -1813 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared | 500 | 433 |
| V5P2_NQ_1964 | NY-AM | 158 | 2.11 | 2106 | 2225 | 2.65 | 0.62 | 62.0 | -613 | -519 | -1164 | 52.9 | -373 | 2531 | 533 | -1164 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 962 | 573 |
| V5P2_NQ_1652 | ASIA | 200 | 2.67 | 2336 | 2476 | 2.64 | 0.59 | 104 | 567 | 577 | 532 | 1479 | 1230 | 1638 | 2117 | 532 | SESSION-CANDIDATE |  | BOF:not cleared | 563 | 477 |
| V5P2_NQ_797 | NY-AM | 229 | 3.05 | 1535 | 1634 | 2.63 | 0.59 | 107 | 136 | -33.1 | 974 | -644 | -754 | 1522 | 644 | 974 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 379 | 1188 |
| V5P2_NQ_587 | NY-AM | 325 | 4.33 | 1984 | 2125 | 2.61 | 0.57 | 149 | -348 | -1210 | 3549 | -688 | -361 | 1156 | 771 | 3549 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 849 | 1018 |
| V5P2_NQ_945 | NY-AM | 157 | 2.09 | 2393 | 2573 | 2.60 | 0.58 | 64.0 | 586 | 569 | 700 | 199 | 408 | 2200 | 1486 | 700 | SESSION-CANDIDATE |  | BOF:not cleared | 161 | 1299 |
| V5P2_NQ_777 | ASIA | 291 | 3.88 | 2227 | 2397 | 2.60 | 0.55 | 128 | 1191 | 905 | 2651 | 521 | 106 | 2515 | 1429 | 2651 | SESSION-CANDIDATE |  | BOF:not cleared | 1200 | 1176 |
| V5P2_NQ_266 | NY-AM | 261 | 3.48 | 2219 | 2392 | 2.60 | 0.58 | 112 | 940 | 568 | 3178 | 138 | -135 | 1851 | 1790 | 3178 | SESSION-CANDIDATE |  | BOF:not cleared | 1569 | 768 |
| V5P2_NQ_1239 | NY-AM | 281 | 3.75 | 1145 | 1243 | 2.58 | 0.44 | 129 | 226 | 711 | -2418 | -510 | -380 | 1243 | 541 | -2418 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 475 | 174 |
| V5P2_NQ_622 | NY-AM | 299 | 3.99 | 2521 | 2752 | 2.57 | 0.43 | 129 | 988 | 1062 | 422 | -579 | -835 | 2246 | 1997 | 422 | SESSION-CANDIDATE |  | BOF:not cleared | 919 | 1046 |
| V5P2_NQ_403 | ASIA | 702 | 9.36 | 763 | 844 | 2.53 | 0.40 | 321 | 164 | 282 | -525 | -79.8 | -57.9 | 324 | 835 | -525 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 117 | 871 |
| V5P2_NQ_743 | LONDON | 222 | 2.96 | 2693 | 2982 | 2.53 | 0.60 | 116 | -651 | -1484 | 1965 | 768 | 3075 | 2059 | 677 | 1965 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 321 | 1147 |
| V5P2_NQ_1169 | NY-AM | 280 | 3.73 | 1357 | 1545 | 2.46 | 0.58 | 117 | 1130 | 1027 | 1829 | 370 | 270 | 1550 | 1038 | 1829 | SESSION-CANDIDATE |  | BOF:not cleared | 870 | 119 |
| V5P2_NQ_763 | ASIA | 725 | 9.67 | 981 | 1129 | 2.43 | 0.40 | 350 | 687 | 717 | 495 | -245 | -293 | 683 | 1048 | 495 | SESSION-CANDIDATE |  | BOF:not cleared | 194 | 1168 |
| V5P2_NQ_701 | ASIA | 858 | 11.4 | 867 | 1001 | 2.42 | 0.38 | 443 | 485 | 331 | 1333 | -268 | -218 | 323 | 936 | 1333 | SESSION-CANDIDATE |  | BOF:not cleared | -63.6 | 1111 |
| V5P2_NQ_47 | NY | 684 | 9.12 | 1141 | 1317 | 2.42 | 0.52 | 294 | 97.6 | -583 | 3588 | -180 | -212 | 846 | 466 | 3588 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 1141 | 926 |
| V5P2_NQ_1938 | NY-AM | 255 | 3.40 | 1282 | 1490 | 2.41 | 0.57 | 108 | 923 | 1315 | -2212 | 538 | 390 | 1346 | 1310 | -2212 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 518 | 681 |
| V5P2_NQ_53 | NY | 195 | 2.60 | 2221 | 2628 | 2.37 | 0.57 | 87.0 | 1354 | 261 | 6203 | 596 | 899 | 1945 | 1361 | 6203 | SESSION-CANDIDATE |  | BOF:not cleared | 175 | 974 |
| V5P2_NQ_770 | NY | 639 | 8.52 | 872 | 1032 | 2.37 | 0.55 | 256 | 354 | 2.68 | 2093 | 717 | 402 | 1033 | 477 | 2093 | SESSION-CANDIDATE |  | BOF:not cleared | 872 | 1170 |


## 5. Dead pooled, alive in a session
2 cell-sessions (2 cells, 2 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V5P2_NQ_701 | ASIA | 858 | 11.4 | 867 | 1001 | 2.42 | 443 | 485 | 331 | 1333 | -268 | -218 | 323 | 936 | 1333 | SESSION-CANDIDATE | BOF:not cleared |  | -63.6 | 1111 |
| V5P2_NQ_1100 | ASIA | 268 | 3.57 | 983 | 1317 | 2.09 | 136 | 629 | 556 | 986 | -368 | -385 | 485 | 1152 | 986 | SESSION-CANDIDATE | BOF:not cleared |  | -95.0 | 74 |


## 6. Notes
- Pooled labels are not attached (pool names V5P2/cNNNN are not mapped to the 2,016 sampled cells by index; the dead-pooled table therefore uses only the pooled PRE mean <= 0 test).
