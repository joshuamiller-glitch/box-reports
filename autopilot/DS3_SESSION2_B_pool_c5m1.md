# DS3_SESSION2_B_pool_c5m1 - Pool family C5M1 entry-clock re-run and session scoring

Written 2026-10-28T21:08:11Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/pool_c5m1/. Prereg l2vast/ds3/prereg/SB3_pool_c5m1_prereg.md sha256 690a3a6461a6eaf882ff0927b89093272d7c7793559d8eb37a238903bf33c3a6; PREHOLD autopilot/DS3_SESSION2_B_pool_c5m1_PREHOLD.md sha256 34614a03e59f519b4891fcc83ce2305f229f1331c9d9241399c25a02ee967e66 (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original core (run_cell -> trade records: exit bar, net $, entry bar index) for every grid cell of the pool family; entry time = ET minute of the entry bar (HM) on the label-day calendar (label day minus one calendar day for minutes >= 18:00), pnl = net $ per trade as in the pool series (instrument costs, NT8sim fills: MAPPED, not direct), lots = contracts. Side is not carried by the trade record (stored as 0), so the overlap-cluster Jaccard uses entry minute only (clusters are a conservative merge). Cell label column shows the original pool name and pool tier (F-* = failed pooled, T1/T2 = passed pooled). Entries are bar-level market entries; exits opp/trail/time are dynamic, brk is a fixed stop=target bracket (par x BS points).

Reproduction: the daily $ series of every cell equals the stored series (real_*.pkl X) for all days up to 2026-10-13 (rtol 1e-4) and, for C5/C7/C10, the stored 2013-2022 trade count; the stored pickles predate the 2026-10-19 end-of-day fix and the series extension, so the re-run uses ENDI_LEGACY and is compared only up to 2026-10-13 (the window used here ends 2026-02-06). All cells checked, rates in out/sb3/pool_<mod>/repro_*.json.

## 2. Multiplicity and counts
- Cells 2928; F = cells x 7 sessions = **20496**; overlap clusters (Jaccard >= 0.5, PRE entries) **250**, F_eff = **1750**. Independent (cluster x session) PRE tests with n >= 100: 867; PRE-selected cell-sessions 97 = 63 independent (chance at 2.5% one-sided = about 22).
- Tiers after the one HOLD look: SESSION-PASS 0, SESSION-CANDIDATE 26, DEAD-IN-HOLD 71; alive cells 23, alive clusters 17. HOLD sign persistence of the selected list: 70%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 1374 | 6 | 3 | 2 | 0 | 1 | C5M1_NQ_306 | 628 | 770 |
| LONDON | 02:00-08:30 | 1604 | 10 | 5 | 4 | 0 | 2 | C5M1_ES_330 | 1190 | 1412 |
| PREOPEN | 08:30-09:30 | 46 | 2 | 1 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 1349 | 38 | 23 | 11 | 0 | 10 | C5M1_NQ_188 | 1478 | 1626 |
| NY-PM | 12:00-15:00 | 946 | 11 | 10 | 2 | 0 | 2 | C5M1_NQ_894 | 2306 | 2821 |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 1736 | 30 | 21 | 7 | 0 | 7 | C5M1_NQ_258 | 1173 | 1272 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C5M1_ES_540 | PREOPEN | 157 | 2.09 | 1044 | 942 | 3.10 | 0.69 | 58.0 | -1283 | -563 | -4043 | -93.5 | -273 | 529 | 903 | -4043 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | -96.9 | 76 |
| C5M1_ES_544 | PREOPEN | 157 | 2.09 | 1044 | 942 | 3.10 | 0.69 | 58.0 | -1283 | -563 | -4043 | -93.5 | -273 | 529 | 903 | -4043 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | -52.8 | 76 |
| C5M1_NQ_849 | NY-AM | 156 | 2.08 | 2258 | 2134 | 2.96 | 0.63 | 62.0 | -613 | -519 | -1164 | 53.3 | -373 | 2531 | 738 | -1164 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1013 | 243 |
| C5M1_NQ_847 | NY-AM | 107 | 1.43 | 2435 | 2349 | 2.90 | 0.64 | 43.0 | -1588 | -2146 | 1279 | 584 | 85.9 | 3043 | -325 | 1279 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 231 | 242 |
| C5M1_ES_48 | NY | 188 | 2.51 | 1804 | 1749 | 2.89 | 0.57 | 67.0 | -503 | -1042 | 1215 | -769 | -981 | 1447 | 964 | 1215 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 585 | 62 |
| C5M1_ES_301 | NY | 129 | 1.72 | 1892 | 1854 | 2.86 | 0.62 | 50.0 | 408 | -43.6 | 2215 | -864 | -892 | 1107 | 1458 | 2215 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 279 | 58 |
| C5M1_ES_654 | LONDON | 180 | 2.40 | 1298 | 1276 | 2.85 | 0.59 | 77.0 | 431 | -14.2 | 1791 | -229 | -265 | 673 | 1056 | 1791 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | -111 | 105 |
| C5M1_ES_658 | LONDON | 180 | 2.40 | 1298 | 1276 | 2.85 | 0.59 | 77.0 | 431 | -14.2 | 1791 | -229 | -265 | 673 | 1056 | 1791 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 205 | 105 |
| C5M1_NQ_29 | LONDON | 445 | 5.93 | 1043 | 1099 | 2.66 | 0.55 | 194 | 211 | 352 | -501 | 7.46 | -39.9 | 607 | 1058 | -501 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 145 | 126 |
| C5M1_NQ_25 | LONDON | 445 | 5.93 | 1043 | 1099 | 2.66 | 0.55 | 194 | 211 | 352 | -501 | 7.46 | -39.9 | 607 | 1058 | -501 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 457 | 126 |
| C5M1_NQ_462 | LONDON | 423 | 5.64 | 2373 | 2517 | 2.64 | 0.52 | 188 | -1837 | -1088 | -4997 | 45.8 | 35.1 | 1253 | 1561 | -4997 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 509 | 195 |
| C5M1_NQ_466 | LONDON | 423 | 5.64 | 2373 | 2517 | 2.64 | 0.52 | 188 | -1837 | -1088 | -4997 | 45.8 | 35.1 | 1253 | 1561 | -4997 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 441 | 195 |
| C5M1_NQ_80 | NY-AM | 225 | 3.00 | 1475 | 1582 | 2.61 | 0.58 | 98.0 | 1338 | 1618 | -94.9 | -45.2 | -35.8 | 1562 | 1364 | -94.9 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 696 | 132 |
| C5M1_NQ_258 | NY | 466 | 6.21 | 1173 | 1272 | 2.58 | 0.57 | 180 | 682 | 226 | 2964 | 357 | 95.0 | 1068 | 950 | 2964 | SESSION-CANDIDATE |  | BOF:not cleared | 409 | 180 |
| C5M1_ES_966 | NY | 396 | 5.28 | 913 | 990 | 2.58 | 0.52 | 161 | -753 | -827 | -387 | 105 | 145 | 490 | 383 | -387 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 248 | 124 |
| C5M1_ES_295 | NY | 178 | 2.37 | 1282 | 1401 | 2.56 | 0.61 | 75.0 | 376 | 611 | -994 | -838 | -670 | 1151 | 851 | -994 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 303 | 58 |
| C5M1_ES_948 | NY | 434 | 5.79 | 1369 | 1500 | 2.55 | 0.46 | 193 | -293 | -99.3 | -1348 | -13.9 | 133 | 1111 | 609 | -1348 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 509 | 124 |
| C5M1_NQ_188 | NY-AM | 265 | 3.53 | 1478 | 1626 | 2.55 | 0.58 | 117 | 503 | 496 | 546 | 155 | 38.0 | 1392 | 1058 | 546 | SESSION-CANDIDATE |  | BOF:not cleared | 798 | 175 |
| C5M1_NQ_258 | NY-AM | 230 | 3.07 | 1486 | 1643 | 2.53 | 0.58 | 107 | 136 | -33.1 | 974 | -643 | -754 | 1522 | 583 | 974 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 409 | 180 |
| C5M1_ES_44 | NY-AM | 262 | 3.49 | 1140 | 1272 | 2.51 | 0.59 | 117 | 725 | 833 | -312 | 512 | 932 | 688 | 1091 | -312 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 941 | 65 |
| C5M1_NQ_152 | NY-AM | 335 | 4.47 | 1277 | 1428 | 2.50 | 0.57 | 153 | 848 | 1023 | -94.9 | -787 | -779 | 937 | 1371 | -94.9 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 536 | 173 |
| C5M1_NQ_819 | NY | 151 | 2.01 | 2447 | 2752 | 2.49 | 0.59 | 65.0 | 1317 | 792 | 5050 | 25.4 | 551 | 1033 | 2427 | 5050 | SESSION-CANDIDATE |  | BOF:not cleared | 2447 | 241 |
| C5M1_NQ_12 | NY-AM | 171 | 2.28 | 2339 | 2646 | 2.48 | 0.57 | 77.0 | 10.8 | -1.98 | 63.8 | -622 | -649 | 1548 | 1764 | 63.8 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 204 | 126 |
| C5M1_ES_44 | NY | 414 | 5.52 | 941 | 1068 | 2.47 | 0.57 | 174 | 273 | 388 | -383 | 240 | 531 | 390 | 926 | -383 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 941 | 65 |
| C5M1_NQ_848 | NY-AM | 233 | 3.11 | 1543 | 1754 | 2.46 | 0.59 | 93.0 | 796 | 1165 | -1698 | -326 | -413 | 1849 | 1024 | -1698 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 768 | 243 |
| C5M1_NQ_303 | NY | 317 | 4.23 | 2042 | 2322 | 2.46 | 0.58 | 118 | 711 | 109 | 3849 | 959 | 811 | 2085 | 1099 | 3849 | SESSION-CANDIDATE |  | BOF:not cleared | 2042 | 183 |
| C5M1_NQ_259 | NY | 279 | 3.72 | 1156 | 1323 | 2.45 | 0.57 | 106 | 748 | -63.3 | 5310 | 101 | -134 | 894 | 915 | 5310 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 255 | 180 |
| C5M1_NQ_44 | NY-AM | 304 | 4.05 | 1402 | 1605 | 2.45 | 0.58 | 127 | 365 | 513 | -736 | -304 | -374 | 1121 | 1178 | -736 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 801 | 189 |
| C5M1_ES_48 | NY-PM | 103 | 1.37 | 2062 | 2380 | 2.43 | 0.57 | 40.0 | -866 | -1646 | 583 | -2102 | -1877 | 359 | 1607 | 583 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 585 | 62 |
| C5M1_NQ_242 | NY | 659 | 8.79 | 1383 | 1599 | 2.42 | 0.50 | 275 | -1181 | -1850 | 2331 | 157 | -68.3 | 1037 | 174 | 2331 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1383 | 177 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C5M1_ES_540 | PREOPEN | 157 | 2.09 | 1044 | 942 | 3.10 | 0.69 | 58.0 | -1283 | -563 | -4043 | -93.5 | -273 | 529 | 903 | -4043 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | -96.9 | 76 |
| C5M1_NQ_849 | NY-AM | 156 | 2.08 | 2258 | 2134 | 2.96 | 0.63 | 62.0 | -613 | -519 | -1164 | 53.3 | -373 | 2531 | 738 | -1164 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 1013 | 243 |
| C5M1_NQ_847 | NY-AM | 107 | 1.43 | 2435 | 2349 | 2.90 | 0.64 | 43.0 | -1588 | -2146 | 1279 | 584 | 85.9 | 3043 | -325 | 1279 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 231 | 242 |
| C5M1_ES_48 | NY | 188 | 2.51 | 1804 | 1749 | 2.89 | 0.57 | 67.0 | -503 | -1042 | 1215 | -769 | -981 | 1447 | 964 | 1215 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 585 | 62 |
| C5M1_ES_301 | NY | 129 | 1.72 | 1892 | 1854 | 2.86 | 0.62 | 50.0 | 408 | -43.6 | 2215 | -864 | -892 | 1107 | 1458 | 2215 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 279 | 58 |
| C5M1_ES_654 | LONDON | 180 | 2.40 | 1298 | 1276 | 2.85 | 0.59 | 77.0 | 431 | -14.2 | 1791 | -229 | -265 | 673 | 1056 | 1791 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | -111 | 105 |
| C5M1_NQ_29 | LONDON | 445 | 5.93 | 1043 | 1099 | 2.66 | 0.55 | 194 | 211 | 352 | -501 | 7.46 | -39.9 | 607 | 1058 | -501 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 145 | 126 |
| C5M1_NQ_462 | LONDON | 423 | 5.64 | 2373 | 2517 | 2.64 | 0.52 | 188 | -1837 | -1088 | -4997 | 45.8 | 35.1 | 1253 | 1561 | -4997 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 509 | 195 |
| C5M1_NQ_80 | NY-AM | 225 | 3.00 | 1475 | 1582 | 2.61 | 0.58 | 98.0 | 1338 | 1618 | -94.9 | -45.2 | -35.8 | 1562 | 1364 | -94.9 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 696 | 132 |
| C5M1_NQ_258 | NY | 466 | 6.21 | 1173 | 1272 | 2.58 | 0.57 | 180 | 682 | 226 | 2964 | 357 | 95.0 | 1068 | 950 | 2964 | SESSION-CANDIDATE |  | BOF:not cleared | 409 | 180 |
| C5M1_ES_966 | NY | 396 | 5.28 | 913 | 990 | 2.58 | 0.52 | 161 | -753 | -827 | -387 | 105 | 145 | 490 | 383 | -387 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 248 | 124 |
| C5M1_NQ_188 | NY-AM | 265 | 3.53 | 1478 | 1626 | 2.55 | 0.58 | 117 | 503 | 496 | 546 | 155 | 38.0 | 1392 | 1058 | 546 | SESSION-CANDIDATE |  | BOF:not cleared | 798 | 175 |
| C5M1_ES_44 | NY-AM | 262 | 3.49 | 1140 | 1272 | 2.51 | 0.59 | 117 | 725 | 833 | -312 | 512 | 932 | 688 | 1091 | -312 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 941 | 65 |
| C5M1_NQ_152 | NY-AM | 335 | 4.47 | 1277 | 1428 | 2.50 | 0.57 | 153 | 848 | 1023 | -94.9 | -787 | -779 | 937 | 1371 | -94.9 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 536 | 173 |
| C5M1_NQ_819 | NY | 151 | 2.01 | 2447 | 2752 | 2.49 | 0.59 | 65.0 | 1317 | 792 | 5050 | 25.4 | 551 | 1033 | 2427 | 5050 | SESSION-CANDIDATE |  | BOF:not cleared | 2447 | 241 |
| C5M1_NQ_303 | NY | 317 | 4.23 | 2042 | 2322 | 2.46 | 0.58 | 118 | 711 | 109 | 3849 | 959 | 811 | 2085 | 1099 | 3849 | SESSION-CANDIDATE |  | BOF:not cleared | 2042 | 183 |
| C5M1_NQ_44 | NY-AM | 304 | 4.05 | 1402 | 1605 | 2.45 | 0.58 | 127 | 365 | 513 | -736 | -304 | -374 | 1121 | 1178 | -736 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 801 | 189 |
| C5M1_NQ_242 | NY | 659 | 8.79 | 1383 | 1599 | 2.42 | 0.50 | 275 | -1181 | -1850 | 2331 | 157 | -68.3 | 1037 | 174 | 2331 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1383 | 177 |
| C5M1_NQ_1178 | NY-AM | 186 | 2.48 | 2103 | 2461 | 2.39 | 0.58 | 82.0 | 2435 | 2796 | -910 | 1227 | 1462 | 1233 | 3072 | -910 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 631 | 142 |
| C5M1_ES_334 | LONDON | 179 | 2.39 | 1190 | 1412 | 2.36 | 0.59 | 87.0 | 942 | 1202 | 122 | -644 | -842 | 1892 | 844 | 122 | SESSION-CANDIDATE |  | BOF:not cleared | 413 | 60 |
| C5M1_ES_20 | NY | 686 | 9.15 | 477 | 567 | 2.36 | 0.53 | 274 | 286 | 189 | 795 | -9.94 | 37.8 | 142 | 601 | 795 | SESSION-CANDIDATE |  | BOF:not cleared | 477 | 42 |
| C5M1_NQ_100 | ASIA | 318 | 4.24 | 695 | 829 | 2.35 | 0.56 | 162 | -352 | -724 | 1424 | -233 | -299 | 589 | -11.8 | 1424 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | -225 | 127 |
| C5M1_NQ_992 | NY-AM | 256 | 3.41 | 1239 | 1507 | 2.30 | 0.57 | 108 | 923 | 1315 | -2212 | 736 | 601 | 1286 | 1310 | -2212 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 494 | 129 |
| C5M1_NQ_894 | NY-PM | 107 | 1.43 | 2306 | 2821 | 2.29 | 0.55 | 38.0 | 1026 | 41.5 | 7525 | -465 | 82.3 | 1035 | 1899 | 7525 | SESSION-CANDIDATE |  | BOF:not cleared | 307 | 244 |
| C5M1_NQ_896 | NY-PM | 107 | 1.43 | 2306 | 2821 | 2.29 | 0.55 | 38.0 | 1026 | 41.5 | 7525 | -465 | 82.3 | 1035 | 1899 | 7525 | SESSION-CANDIDATE |  | BOF:not cleared | 1182 | 245 |
| C5M1_NQ_54 | NY-AM | 184 | 2.45 | 2388 | 2926 | 2.28 | 0.57 | 76.0 | 3563 | 3318 | 5177 | 662 | 549 | 2550 | 2667 | 5177 | SESSION-CANDIDATE |  | BOF:not cleared | 263 | 186 |
| C5M1_NQ_162 | NY-AM | 215 | 2.87 | 2349 | 2879 | 2.28 | 0.57 | 85.0 | 2274 | 1940 | 4305 | 155 | 4.43 | 2521 | 1888 | 4305 | SESSION-CANDIDATE |  | BOF:not cleared | 101 | 171 |
| C5M1_NQ_310 | ASIA | 292 | 3.89 | 628 | 770 | 2.28 | 0.55 | 149 | 245 | 116 | 827 | -209 | -253 | 141 | 753 | 827 | SESSION-CANDIDATE |  | BOF:not cleared | 177 | 182 |
| C5M1_NQ_8 | NY | 694 | 9.25 | 691 | 848 | 2.28 | 0.54 | 306 | 502 | 7.64 | 2917 | 227 | 179 | 676 | 372 | 2917 | SESSION-CANDIDATE |  | BOF:not cleared | 691 | 166 |
| C5M1_NQ_513 | NY-AM | 159 | 2.12 | 1509 | 1910 | 2.21 | 0.57 | 62.0 | -956 | -1200 | 1829 | -1129 | -1204 | 611 | 924 | 1829 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 1165 | 199 |


## 5. Dead pooled, alive in a session
15 cell-sessions (14 cells, 15 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C5M1_NQ_258 | NY | 466 | 6.21 | 1173 | 1272 | 2.58 | 180 | 682 | 226 | 2964 | 357 | 95.0 | 1068 | 950 | 2964 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_st_14_3_brk_60_all_0|F-X (2023-04..2024-01 <=0) | 409 | 180 |
| C5M1_NQ_188 | NY-AM | 265 | 3.53 | 1478 | 1626 | 2.55 | 117 | 503 | 496 | 546 | 155 | 38.0 | 1392 | 1058 | 546 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_macd_19_39_brk_60_rth_0|F-X (2023-04..2024-01 <=0) | 798 | 175 |
| C5M1_NQ_819 | NY | 151 | 2.01 | 2447 | 2752 | 2.49 | 65.0 | 1317 | 792 | 5050 | 25.4 | 551 | 1033 | 2427 | 5050 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_ema_20_60_brk_90_rth_1|F-HOLD (holdout <=0) | 2447 | 241 |
| C5M1_NQ_303 | NY | 317 | 4.23 | 2042 | 2322 | 2.46 | 118 | 711 | 109 | 3849 | 959 | 811 | 2085 | 1099 | 3849 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_st_21_4_brk_90_rth_1|F-HOLD (holdout <=0) | 2042 | 183 |
| C5M1_ES_20 | NY | 686 | 9.15 | 477 | 567 | 2.36 | 274 | 286 | 189 | 795 | -9.94 | 37.8 | 142 | 601 | 795 | SESSION-CANDIDATE | BOF:not cleared | C5M1_ES/5_ema_9_21_time_60_rth_0|F-HOLD (holdout <=0) | 477 | 42 |
| C5M1_NQ_896 | NY-PM | 107 | 1.43 | 2306 | 2821 | 2.29 | 38.0 | 1026 | 41.5 | 7525 | -465 | 82.3 | 1035 | 1899 | 7525 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_macd_12_26_time_60_rth_0|F-X (2023-04..2024-01 <=0) | 1182 | 245 |
| C5M1_NQ_894 | NY-PM | 107 | 1.43 | 2306 | 2821 | 2.29 | 38.0 | 1026 | 41.5 | 7525 | -465 | 82.3 | 1035 | 1899 | 7525 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_macd_12_26_time_60_all_0|F-HOLD (holdout <=0) | 307 | 244 |
| C5M1_NQ_54 | NY-AM | 184 | 2.45 | 2388 | 2926 | 2.28 | 76.0 | 3563 | 3318 | 5177 | 662 | 549 | 2550 | 2667 | 5177 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_ema_13_40_time_60_all_0|F-HOLD (holdout <=0) | 263 | 186 |
| C5M1_NQ_162 | NY-AM | 215 | 2.87 | 2349 | 2879 | 2.28 | 85.0 | 2274 | 1940 | 4305 | 155 | 4.43 | 2521 | 1888 | 4305 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_macd_12_26_time_60_all_0|F-HOLD (holdout <=0) | 101 | 171 |
| C5M1_NQ_310 | ASIA | 292 | 3.89 | 628 | 770 | 2.28 | 149 | 245 | 116 | 827 | -209 | -253 | 141 | 753 | 827 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_st_21_4_time_60_glx_0|F-HOLD (holdout <=0) | 177 | 182 |
| C5M1_NQ_818 | NY-AM | 123 | 1.64 | 2500 | 3274 | 2.14 | 61.0 | 1682 | 1718 | 1445 | -289 | 779 | 890 | 2650 | 1445 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_ema_20_60_brk_90_rth_0|F-HOLD (holdout <=0) | 1688 | 241 |
| C5M1_NQ_14 | NY-AM | 335 | 4.47 | 1609 | 2117 | 2.13 | 155 | 1309 | 969 | 2787 | -561 | -334 | 1199 | 1369 | 2787 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/5_ema_9_21_brk_90_rth_0|F-HOLD (holdout <=0) | 955 | 166 |
| C5M1_ES_62 | NY | 411 | 5.48 | 795 | 1061 | 2.10 | 173 | 726 | 409 | 2300 | -181 | -13.6 | 762 | 393 | 2300 | SESSION-CANDIDATE | BOF:not cleared | C5M1_ES/5_ema_13_40_time_120_rth_0|F-X (2023-04..2024-01 <=0) | 795 | 65 |
| C5M1_NQ_894 | NY | 253 | 3.37 | 1382 | 1859 | 2.08 | 94.0 | 1948 | 988 | 7928 | 289 | 620 | 1072 | 1201 | 7928 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_macd_12_26_time_60_all_0|F-HOLD (holdout <=0) | 307 | 244 |
| C5M1_NQ_740 | NY-AM | 210 | 2.80 | 1267 | 1722 | 2.06 | 89.0 | 880 | 1001 | 171 | 16.2 | -64.5 | 1233 | 1151 | 171 | SESSION-CANDIDATE | BOF:not cleared | C5M1_NQ/15_ema_9_21_brk_60_rth_0|F-HOLD (holdout <=0) | 795 | 237 |

