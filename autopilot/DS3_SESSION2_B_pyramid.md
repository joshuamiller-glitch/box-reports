# DS3_SESSION2_B_pyramid - T-PYRAMID entry-clock re-run and session scoring

Written 2026-10-28T21:16:48Z. Research only; no live/execution-server/chart change; label days after 2026-02-06 never read. Code l2vast/ds3/code/sb3/, outputs l2vast/ds3/out/sb3/pyramid/. Prereg l2vast/ds3/prereg/SB3_pyramid_prereg.md sha256 70b6b539d1047bc568c5ac711191b905b8fd84ac87bb5d8ab8aed4a631bbe085; PREHOLD autopilot/DS3_SESSION2_B_pyramid_PREHOLD.md sha256 58a6f9a09270e40fb456bdb38bf492e5df1f7b5938275a91bce25d5e9a033dee (written before HOLD/X; one HOLD look + one X look logged in out/sb3/looks.jsonl).

## 1. Re-run, reproduction and basis
Re-run of the original 1-s path sequential simulation (py_lib.simulate_seq/build_seq with the original cells py_cells.CELLS+CELLS_B; tier-4 through t4_pycore with its stop/target/lots), one position per trade: pnl = sum over legs of 200*u*(pe-0.5) - 48.4*u (u in 10-lot units, tier-4 native lots), unlocked, i.e. the tradenet of the original paired test; entry time = main-leg et_in (ET, bar end stamp as in the ledger convention). Basis: main leg DIRECT P9 / T-ENTRY S10x1+XJ3 where available else mapped; adds and changed exits MAPPED; 'cons' = no join bonus on modified stops (the verdict basis of the source), 'plain' = year x exit haircut (upper bound, stated by the source as not registered). Adds are not a plain entry+bracket: pyramid survivors cannot go to the fixed-bracket replay queue as is (listed separately).

Reproduction (lock-engine weekly PRE and HOLD mean and trade count vs the stored out/py/<entry>_res[_c].pkl and out/t4/D/<entry>_res.pkl): tier-1 cons+plain 430/430, tier-4 420/420 (100%, all cells; both weekly means and cell trade counts). out/sb3/pyramid/repro_*.csv.

## 2. Multiplicity and counts
- Cells 850; F = cells x 7 sessions = **5950**; overlap clusters (Jaccard >= 0.5, PRE entries) **19**, F_eff = **133**. Independent (cluster x session) PRE tests with n >= 100: 106; PRE-selected cell-sessions 396 = 28 independent (chance at 2.5% one-sided = about 3).
- Tiers after the one HOLD look: SESSION-PASS 7, SESSION-CANDIDATE 267, DEAD-IN-HOLD 122; alive cells 138, alive clusters 8. HOLD sign persistence of the selected list: 81%.
- $ per trade: pnl as stored in the regenerated tables (see section 1). Session = ENTRY time ET; 16:54-18:00 = OFF (pooled only). CI/MDE week-clustered; MDE = 2.8 x SE ($ per trade; mde_wk = x trades/week).

## 3. Number alive per session
| session | window | cells_n100 | pre_sig | pre_sig_clusters | cand | passed | alive_clusters | best | best_mean | best_mde |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | 18:00-02:00 | 850 | 126 | 10 | 100 | 0 | 8 | PY_plain_KB_D2_N15_f50_m2_s15_G1 | 745 | 460 |
| LONDON | 02:00-08:30 | 820 | 14 | 3 | 13 | 0 | 3 | PY_plain_KB_D2_PB_f50_m1_s30_G1 | 753 | 625 |
| PREOPEN | 08:30-09:30 | 575 | 6 | 1 | 0 | 0 | 0 | - |  |  |
| NY-AM | 09:30-12:00 | 793 | 145 | 8 | 85 | 0 | 6 | PY_plain_KB_D2_N15_f50_m2_s15_G1 | 847 | 522 |
| NY-PM | 12:00-15:00 | 791 | 19 | 2 | 12 | 0 | 2 | PY_plain_ST10_D2_N15_f50_m2_s15_G1 | 785 | 592 |
| CLOSE | 15:00-16:54 | 0 | 0 | 0 | 0 | 0 | 0 | - |  |  |
| NY | 09:30-15:00 | 820 | 86 | 4 | 57 | 7 | 4 | PY_plain_ST10_D2_N30_f50_m1_s30_G3 | 1114 | 536 |


## 4. Top 30 session-restricted cell-sessions by PRE t (n >= 100), regardless of verdict
failed_gate empty = passes the PRE and HOLD gates. HOLD columns are blank for cells that were not PRE-selected (never looked at).
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PY_plain_ST10_D2_N30_f50_m1_s30_G3 | NY | 1974 | 26.3 | 1114 | 536 | 5.82 | 0.67 | 939 | 1637 | 1431 | 2518 | -464 | -428 | 924 | 1323 | 2518 | SESSION-PASS |  | BOF_F:clear | 869 | 4 |
| PY_plain_ST10_D3_N30_f50_m1_s30_G3 | NY | 1946 | 25.9 | 1112 | 555 | 5.61 | 0.53 | 924 | 1470 | 1296 | 2201 | -431 | -401 | 951 | 1239 | 2201 | SESSION-PASS |  | BOF_F:clear | 925 | 4 |
| PY_plain_ST10_D1_N30_f50_m1_s30_G3 | NY | 1946 | 25.9 | 1112 | 555 | 5.61 | 0.53 | 924 | 1470 | 1296 | 2201 | -431 | -401 | 951 | 1239 | 2201 | SESSION-PASS |  | BOF_F:clear | 925 | 4 |
| PY_plain_ST10_D4_N30_f0_m1_s30_G3 | NY | 1946 | 25.9 | 974 | 491 | 5.55 | 0.67 | 924 | 1393 | 1230 | 2082 | -329 | -294 | 823 | 1137 | 2082 | SESSION-PASS |  | BOF_F:clear | 827 | 4 |
| PY_plain_ST10_D1_N30_f50_m2_s15_G3 | NY | 1946 | 25.9 | 1148 | 581 | 5.53 | 0.53 | 924 | 1543 | 1360 | 2314 | -451 | -420 | 994 | 1281 | 2314 | SESSION-PASS |  | BOF_F:clear | 960 | 4 |
| PY_plain_ST10_D1_N30_f100_m1_s30_G3 | NY | 1946 | 25.9 | 1213 | 642 | 5.29 | 0.45 | 924 | 1509 | 1326 | 2280 | -566 | -542 | 1042 | 1305 | 2280 | SESSION-PASS |  | BOF_F:clear | 986 | 4 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY | 2768 | 36.9 | 663 | 362 | 5.14 | 0.78 | 1192 | 546 | 395 | 1290 | -290 | -323 | 486 | 644 | 1290 | SESSION-PASS |  | BOF_F:clear | 638 | 2 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY-AM | 1480 | 19.7 | 847 | 522 | 4.54 | 0.78 | 692 | 661 | 557 | 1167 | -385 | -397 | 578 | 867 | 1167 | SESSION-CANDIDATE |  | BOF_Feff:clear | 638 | 2 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | ASIA | 1553 | 20.7 | 745 | 460 | 4.53 | 0.80 | 746 | 1111 | 1030 | 1383 | -115 | -118 | 632 | 914 | 1383 | SESSION-CANDIDATE |  | BOF_Feff:clear | 638 | 2 |
| PY_plain_ST10_D4_N15_f0_m1_s30_G3 | NY | 2438 | 32.5 | 600 | 378 | 4.45 | 0.52 | 1127 | 1284 | 1180 | 1728 | -238 | -204 | 377 | 1008 | 1728 | SESSION-CANDIDATE |  | BOF_Feff:clear | 567 | 4 |
| PY_plain_KB_D2_N20_f50_m1_s30_G1 | NY | 2439 | 32.5 | 644 | 409 | 4.41 | 0.74 | 1067 | 418 | 294 | 999 | -40.3 | -29.6 | 542 | 520 | 999 | SESSION-CANDIDATE |  | BOF_Feff:clear | 584 | 2 |
| PY_plain_ST10_D1_PB_f50_m1_s30_G3 | NY | 2198 | 29.3 | 833 | 529 | 4.41 | 0.48 | 1030 | 1553 | 1417 | 2125 | -197 | -119 | 690 | 1140 | 2125 | SESSION-CANDIDATE |  | BOF_Feff:clear | 761 | 4 |
| PY_plain_KB_D1_PB_f50_m1_s30_G3 | NY | 2208 | 29.4 | 904 | 593 | 4.27 | 0.46 | 941 | 793 | 885 | 385 | 74.5 | 99.5 | 946 | 799 | 385 | SESSION-CANDIDATE |  | BOF_Feff:clear | 680 | 2 |
| PY_plain_ST10_D3_N30_f50_m1_s30_G3 | NY-AM | 1231 | 16.4 | 1291 | 870 | 4.15 | 0.53 | 615 | 2298 | 2185 | 2724 | -298 | -225 | 1080 | 1785 | 2724 | SESSION-CANDIDATE |  | BOF_Feff:clear | 925 | 4 |
| PY_plain_ST10_D1_N30_f50_m1_s30_G3 | NY-AM | 1231 | 16.4 | 1291 | 870 | 4.15 | 0.53 | 615 | 2298 | 2185 | 2724 | -298 | -225 | 1080 | 1785 | 2724 | SESSION-CANDIDATE |  | BOF_Feff:clear | 925 | 4 |
| PY_plain_ST10_D1_N15_f50_m1_s30_G3 | NY | 2438 | 32.5 | 706 | 476 | 4.15 | 0.44 | 1127 | 1507 | 1409 | 1929 | -374 | -346 | 448 | 1193 | 1929 | SESSION-CANDIDATE |  | BOF_Feff:clear | 695 | 4 |
| PY_plain_ST10_D4_N30_f0_m1_s30_G3 | NY-AM | 1231 | 16.4 | 1119 | 760 | 4.12 | 0.68 | 615 | 2085 | 1954 | 2580 | -247 | -153 | 894 | 1596 | 2580 | SESSION-CANDIDATE |  | BOF_Feff:clear | 827 | 4 |
| PY_plain_KB_D3_N30_f50_m1_s30_G3 | NY | 1976 | 26.3 | 936 | 637 | 4.12 | 0.53 | 856 | 506 | 467 | 680 | 307 | 235 | 982 | 687 | 680 | SESSION-CANDIDATE |  | BOF_Feff:clear | 866 | 2 |
| PY_plain_KB_D1_N30_f50_m1_s30_G3 | NY | 1976 | 26.3 | 936 | 637 | 4.12 | 0.53 | 856 | 506 | 467 | 680 | 307 | 235 | 982 | 687 | 680 | SESSION-CANDIDATE |  | BOF_Feff:clear | 866 | 2 |
| PY_plain_KB_D2_N20_f50_m1_s30_G1 | NY-AM | 1328 | 17.7 | 910 | 622 | 4.10 | 0.75 | 638 | 369 | 204 | 1135 | -215 | -190 | 670 | 680 | 1135 | SESSION-CANDIDATE |  | BOF_Feff:clear | 584 | 2 |
| PY_plain_ST10_D2_N20_f50_m1_s30_G1 | NY | 2284 | 30.5 | 630 | 431 | 4.09 | 0.74 | 1064 | 1406 | 1266 | 2012 | -287 | -265 | 419 | 1052 | 2012 | SESSION-CANDIDATE |  | BOF_Feff:clear | 578 | 4 |
| PY_plain_KB_D2_N30_f50_m1_s30_G3 | NY | 2030 | 27.1 | 964 | 663 | 4.07 | 0.66 | 879 | 813 | 700 | 1317 | 256 | 220 | 1030 | 769 | 1317 | SESSION-CANDIDATE |  | BOF_Feff:clear | 903 | 2 |
| PY_plain_ST10_D2_N30_f50_m2_s15_G1 | NY | 1978 | 26.4 | 733 | 506 | 4.06 | 0.67 | 940 | 1085 | 924 | 1772 | -341 | -280 | 668 | 797 | 1772 | SESSION-CANDIDATE |  | BOF_Feff:clear | 516 | 4 |
| PY_plain_ST10_D2_N30_f50_m1_s30_G1 | NY | 1978 | 26.4 | 733 | 506 | 4.06 | 0.67 | 940 | 1085 | 924 | 1772 | -341 | -280 | 668 | 797 | 1772 | SESSION-CANDIDATE |  | BOF_Feff:clear | 516 | 4 |
| PY_plain_HM10_D2_N30_f100_m1_s30_G1 | NY-AM | 653 | 8.71 | 1223 | 844 | 4.06 | 0.69 | 299 | 925 | 399 | 3486 | -59.9 | 145 | 925 | 862 | 3486 | SESSION-CANDIDATE |  | BOF_Feff:clear | 571 | 1 |
| PY_plain_ST10_D1_N30_f50_m2_s15_G3 | NY-AM | 1231 | 16.4 | 1351 | 935 | 4.04 | 0.53 | 615 | 2417 | 2299 | 2859 | -317 | -258 | 1179 | 1844 | 2859 | SESSION-CANDIDATE |  | BOF_Feff:clear | 960 | 4 |
| PY_plain_ST10_D2_N30_f50_m1_s30_G3 | NY-AM | 1246 | 16.6 | 1184 | 823 | 4.03 | 0.68 | 624 | 2304 | 2138 | 2932 | -418 | -295 | 837 | 1794 | 2932 | SESSION-CANDIDATE |  | BOF_Feff:clear | 869 | 4 |
| PY_plain_KB_D4_N30_f0_m1_s30_G3 | NY | 1976 | 26.3 | 826 | 577 | 4.01 | 0.66 | 856 | 337 | 277 | 603 | 343 | 280 | 882 | 537 | 603 | SESSION-CANDIDATE |  | BOF_Feff:clear | 752 | 2 |
| PY_plain_KB_D2_PB_f50_m1_s30_G1 | NY | 2455 | 32.7 | 613 | 429 | 4.00 | 0.74 | 1054 | 488 | 332 | 1190 | 19.8 | -65.1 | 533 | 556 | 1190 | SESSION-CANDIDATE |  | BOF_Feff:clear | 605 | 2 |
| PY_plain_ST10_D1_N30_f100_m1_s30_G3 | NY-AM | 1231 | 16.4 | 1426 | 1006 | 3.97 | 0.45 | 615 | 2472 | 2378 | 2828 | -384 | -332 | 1228 | 1937 | 2828 | SESSION-CANDIDATE |  | BOF_Feff:clear | 986 | 4 |


### One per overlap cluster (top 30 clusters)
| cid | session | n | tpw | mean | mde | t | win | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | failed_gate | bof_label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PY_plain_ST10_D2_N30_f50_m1_s30_G3 | NY | 1974 | 26.3 | 1114 | 536 | 5.82 | 0.67 | 939 | 1637 | 1431 | 2518 | -464 | -428 | 924 | 1323 | 2518 | SESSION-PASS |  | BOF_F:clear | 869 | 4 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY | 2768 | 36.9 | 663 | 362 | 5.14 | 0.78 | 1192 | 546 | 395 | 1290 | -290 | -323 | 486 | 644 | 1290 | SESSION-PASS |  | BOF_F:clear | 638 | 2 |
| PY_plain_HM10_D2_N30_f100_m1_s30_G1 | NY-AM | 653 | 8.71 | 1223 | 844 | 4.06 | 0.69 | 299 | 925 | 399 | 3486 | -59.9 | 145 | 925 | 862 | 3486 | SESSION-CANDIDATE |  | BOF_Feff:clear | 571 | 1 |
| T4PY_PB3E_D_R3_P2_40_1.5R_D4_SG_f50_m1_s30_G1 | PREOPEN | 102 | 1.36 | 3075 | 2948 | 2.92 | 0.53 | 34.0 | 578 | 978 | -381 | 1594 | 2882 | 2345 | 2275 | -381 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared | 635 | 10 |
| PY_plain_EM_D4_N45_f0_m1_s30_G3 | ASIA | 255 | 3.40 | 2151 | 2285 | 2.63 | 0.62 | 130 | 1530 | 480 | 5938 | -600 | -623 | 1874 | 1360 | 5938 | SESSION-CANDIDATE |  | BOF:not cleared | 1254 | 0 |
| T4PY_PRO_Z20_t1.0_D2_N30_f50_m1_s30_G3 | NY-AM | 1573 | 21.0 | 676 | 725 | 2.61 | 0.66 | 735 | -259 | -219 | -415 | 243 | 270 | 351 | 476 | -415 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared | 94.5 | 16 |
| PY_plain_SM_D1_N30_f50_m3_s15_G1 | ASIA | 244 | 3.25 | 2053 | 2379 | 2.42 | 0.54 | 113 | 1559 | 1537 | 1643 | 1304 | 1432 | 1592 | 2102 | 1643 | SESSION-CANDIDATE |  | BOF:not cleared | 796 | 3 |
| T4PY_PB3B_R5_P1_D2_N30_f50_m1_s30_G3 | ASIA | 929 | 12.4 | 854 | 990 | 2.41 | 0.68 | 473 | 462 | 296 | 1047 | -839 | -1029 | 864 | 600 | 1047 | SESSION-CANDIDATE |  | BOF:not cleared | 271 | 6 |
| T4PY_PB3B_R5_P3_D1_N30_f50_m1_s30_G3 | ASIA | 713 | 9.51 | 1006 | 1254 | 2.25 | 0.49 | 327 | 835 | 802 | 951 | -309 | -476 | 1022 | 912 | 951 | SESSION-CANDIDATE |  | BOF:not cleared | 357 | 5 |
| T4PY_PRO_Z60_t1.0_D3_N30_f50_m1_s30_G3 | ASIA | 849 | 11.3 | 976 | 1254 | 2.18 | 0.49 | 402 | 481 | -8.81 | 2088 | -58.0 | -268 | 1119 | 494 | 2088 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared | 162 | 18 |
| T4PY_PB3B_R60_P2_D2_PB_f50_m1_s30_G1 | NY-AM | 933 | 12.4 | 487 | 670 | 2.03 | 0.76 | 427 | -255 | -432 | 527 | -79.7 | -33.3 | 161 | 252 | 527 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared | 18.0 | 8 |
| T4PY_PRO_KAL_k0.0_D1_N30_f50_m1_s30_G2 | PREOPEN | 227 | 3.03 | 1807 | 2599 | 1.95 | 0.48 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -13.1 | 13 |
| T4PY_PRO_ER4_EMA5_D4_PB_f50_m1_s30_G1 | LONDON | 137 | 1.83 | 2508 | 3904 | 1.80 | 0.60 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 786 | 11 |
| T4PY_PRO_ER5_EMA5_D3_PB_f50_m1_s30_G1 | ASIA | 104 | 1.39 | 1654 | 3092 | 1.50 | 0.41 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 1269 | 12 |
| T4PY_PB3B_R60_P3_D4_SG_f50_m1_s30_G1 | LONDON | 428 | 5.71 | 1078 | 2026 | 1.49 | 0.54 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 115 | 9 |
| T4PY_PRO_RIB1m_q30_D2_PB_f50_m1_s30_G1 | NY-AM | 771 | 10.3 | 385 | 766 | 1.41 | 0.73 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | 50.9 | 15 |
| T4PY_PRO_Z20_t1.0_D2_SG_f50_m1_s30_G1 | NY-AM | 1509 | 20.1 | 274 | 689 | 1.11 | 0.63 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -68.9 | 17 |
| T4PY_PB3B_R5_P1_D2_SG_f50_m1_s30_G1 | ASIA | 2091 | 27.9 | 105 | 333 | 0.88 | 0.70 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE CI includes 0 | nan | -138 | 7 |
| T4PY_PRO_KAL_k0.0_D2_SG_f50_m1_s30_G1 | PREOPEN | 578 | 7.71 | -139 | 755 | -0.52 | 0.70 |  |  |  |  |  |  |  |  |  | NOT-SELECTED | PRE mean<=0 | nan | -246 | 14 |


## 5. Dead pooled, alive in a session
131 cell-sessions (86 cells, 20 independent). Top 30:
| cid | session | n | tpw | mean | mde | t | hold_n | hold_mean | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | tier | bof_label | label | pool_pre_mean | cluster50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY | 2768 | 36.9 | 663 | 362 | 5.14 | 1192 | 546 | 395 | 1290 | -290 | -323 | 486 | 644 | 1290 | SESSION-PASS | BOF_F:clear | DEAD | 638 | 2 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY-AM | 1480 | 19.7 | 847 | 522 | 4.54 | 692 | 661 | 557 | 1167 | -385 | -397 | 578 | 867 | 1167 | SESSION-CANDIDATE | BOF_Feff:clear | DEAD | 638 | 2 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | ASIA | 1553 | 20.7 | 745 | 460 | 4.53 | 746 | 1111 | 1030 | 1383 | -115 | -118 | 632 | 914 | 1383 | SESSION-CANDIDATE | BOF_Feff:clear | DEAD | 638 | 2 |
| PY_plain_ST10_D2_N30_f50_m2_s15_G1 | NY | 1978 | 26.4 | 733 | 506 | 4.06 | 940 | 1085 | 924 | 1772 | -341 | -280 | 668 | 797 | 1772 | SESSION-CANDIDATE | BOF_Feff:clear | DEAD | 516 | 4 |
| PY_plain_HM10_D2_N30_f100_m1_s30_G1 | NY-AM | 653 | 8.71 | 1223 | 844 | 4.06 | 299 | 925 | 399 | 3486 | -59.9 | 145 | 925 | 862 | 3486 | SESSION-CANDIDATE | BOF_Feff:clear | DEAD | 571 | 1 |
| PY_plain_HM10_D2_N30_f100_m1_s30_G1 | NY | 1280 | 17.1 | 765 | 646 | 3.32 | 552 | 579 | 297 | 1974 | -394 | -414 | 774 | 461 | 1974 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 571 | 1 |
| PY_plain_HM10_D1_N30_f50_m1_s30_G3 | ASIA | 732 | 9.76 | 1400 | 1208 | 3.24 | 340 | 1580 | 1212 | 3079 | -797 | -1141 | 1521 | 1274 | 3079 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 850 | 1 |
| PY_plain_ST10_D2_N30_f50_m2_s15_G1 | NY-AM | 1249 | 16.7 | 800 | 736 | 3.04 | 622 | 1651 | 1510 | 2193 | -355 | -171 | 550 | 1204 | 2193 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 516 | 4 |
| PY_plain_EM_D1_N45_f50_m1_s30_G3 | ASIA | 255 | 3.40 | 2481 | 2705 | 2.57 | 130 | 1867 | 676 | 6871 | -781 | -865 | 2215 | 1623 | 6871 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 1432 | 0 |
| PY_plain_ST10_D3_N30_f50_m1_s30_G1 | ASIA | 813 | 10.8 | 884 | 985 | 2.51 | 384 | 624 | 291 | 1730 | 484 | 379 | 903 | 635 | 1730 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 358 | 4 |
| PY_plain_SM_D1_N30_f50_m1_s30_G1 | ASIA | 244 | 3.25 | 2053 | 2379 | 2.42 | 113 | 1559 | 1537 | 1643 | 1304 | 1432 | 1592 | 2102 | 1643 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 796 | 3 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | NY-PM | 1288 | 17.2 | 453 | 525 | 2.42 | 500 | 386 | 171 | 1465 | -176 | -233 | 374 | 384 | 1465 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 638 | 2 |
| T4PY_PB3B_R5_P1_D2_N30_f50_m1_s30_G3 | ASIA | 929 | 12.4 | 854 | 990 | 2.41 | 473 | 462 | 296 | 1047 | -839 | -1029 | 864 | 600 | 1047 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 271 | 6 |
| PY_plain_KB_D2_N15_f50_m2_s15_G1 | LONDON | 1462 | 19.5 | 518 | 601 | 2.41 | 635 | 675 | 844 | 60.1 | 7.14 | -65.5 | -123 | 1085 | 60.1 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 638 | 2 |
| PY_plain_SM_D1_PB_f50_m1_s30_G1 | NY-AM | 233 | 3.11 | 1931 | 2346 | 2.30 | 103 | 1975 | 2049 | 1459 | -94.9 | -285 | 2450 | 1450 | 1459 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 479 | 3 |
| T4PY_PB3B_R5_P3_D3_N30_f50_m1_s30_G3 | ASIA | 713 | 9.51 | 1006 | 1254 | 2.25 | 327 | 835 | 802 | 951 | -309 | -476 | 1022 | 912 | 951 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 357 | 5 |
| PY_plain_SM_D1_PB_f50_m1_s30_G1 | NY | 342 | 4.56 | 1424 | 1811 | 2.20 | 135 | 1363 | 908 | 3830 | -976 | -1277 | 1636 | 940 | 3830 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 479 | 3 |
| T4PY_PRO_Z20_t1.0_D1_SG_f50_m1_s30_G1 | ASIA | 929 | 12.4 | 912 | 1209 | 2.11 | 441 | 969 | 317 | 3137 | 728 | 277 | 1262 | 574 | 3137 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 323 | 16 |
| T4PY_PB3B_R5_P1_D2_N30_f50_m1_s30_G3 | NY-AM | 1157 | 15.4 | 631 | 850 | 2.08 | 517 | 179 | 114 | 428 | 661 | 874 | 711 | 230 | 428 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 271 | 6 |
| PY_plain_EM_D1_SG_f50_m1_s30_G3 | NY-AM | 190 | 2.53 | 1559 | 2113 | 2.07 | 80.0 | 982 | 981 | 986 | 22.8 | 15.5 | 1899 | 887 | 986 | SESSION-CANDIDATE | BOF:not cleared | DEAD | 466 | 0 |

