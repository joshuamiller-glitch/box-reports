# DS3_SDISC_2A_T-ENTRY - session-native re-search of the T-ENTRY family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **235** (T-ENTRY pb4 (TB4), T-ENTRY e1); fixed 60/60 bracket (analytic MEASURED available): **216**; dynamic/other exits (stored basis only): 19. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 220 | 17 | 10 | 1 | 1 | 1 | 7 |
| LONDON | 222 | 3 | 4 | 1 | 0 | 0 | 3 |
| PREOPEN | 185 | 4 | 4 | 1 | 0 | 0 | 3 |
| NY-AM | 234 | 3 | 4 | 4 | 0 | 0 | 0 |
| NY-PM | 230 | 3 | 4 | 1 | 0 | 0 | 3 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| NY | 234 | 3 | 3 | 0 | 0 | 0 | 3 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 220)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1A_RENKOC5_A3_r48 | dyn | 424 | 5.7 | 2,341 | 1,141 | 3.89 | 1,686 |  | 2,321 |  |  | +11.86 | 1,658 | 4,151 | -13 | 294/2,450/2,022/4,151 | STORED-CANDIDATE(MEASURED n/a) | - | - | reread |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | 60/60 | 450 | 6.0 | 1,842 | 749 | 3.36 | 1,537 | 1,722 | -1,060 | -1,202 | -1,432 | -5.75 | -1,414 | -235 | -93 | 14/1,479/464/-235 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | 60/60 | 800 | 10.7 | 1,237 | 467 | 3.20 | 1,083 | 1,112 | 494 | 363 | 126 | +2.08 | -93 | 1,757 | -246 | -469/1,177/471/1,757 | MEASURED-FAIL | H25<=0 | - | reread |
| TB4W_06_time_30s_ST3_E20_1_T2_ntime14 | 60/60 | 780 | 10.4 | 1,084 | 297 | 2.75 | 1,105 | 958 | 500 | 369 | 132 | +2.11 | -151 | 2,067 | -336 | -552/886/502/2,067 | DEAD-IN-HOLD | H25<=0 | - | reread |
| E1A_RENKOC5_A3_r80 | dyn | 161 | 2.1 | 4,978 | 1,238 | 2.65 | 5,256 |  | -666 |  |  | -3.07 | -2,196 | 2,289 | -2,743 | -3,277/7,437/1,500/2,289 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TB4A_time_03_time_30s_ST3_SW38_T2 | 60/60 | 690 | 9.2 | 1,062 | 245 | 2.59 | 1,149 | 936 | -296 | -431 | -664 | -1.90 | -1,021 | 1,749 | -174 | -321/763/145/1,749 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TB4E_renko_24_renko_40_ST3_SW38_T1 | 60/60 | 549 | 7.3 | 1,172 | 226 | 2.47 | 1,329 | 1,047 | -1,572 | -1,717 | -1,944 | -8.33 | -2,374 | 694 | -977 | -2,096/887/-64/694 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TB4W_12_volume_1000_ST10_E20_1_T1_nvolume00 | 60/60 | 542 | 7.2 | 1,427 | 275 | 2.47 | 1,619 | 1,303 | 1,142 | 1,016 | 775 | +5.34 | 1,481 | -433 | 1,093 | 981/1,291/1,318/-433 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4C_range_24_range_80_ST5_SW38_T1 | 60/60 | 595 | 7.9 | 1,268 | 233 | 2.44 | 1,453 | 1,143 | 728 | 599 | 361 | +3.25 | 194 | 2,018 | -54 | -778/1,932/432/2,018 | SESSION-CANDIDATE | - | - | reread |
| TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 60/60 | 663 | 8.8 | 897 | 93 | 2.22 | 1,130 | 769 | -164 | -300 | -533 | -1.24 | -771 | 1,075 | -980 | -858/480/352/1,075 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |

### LONDON (N screened 222)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB4A_time_29_time_30s_ST60_VWAP_T3 | 60/60 | 226 | 3.0 | 1,956 | 440 | 2.57 | 2,130 | 1,837 | 1,006 | 880 | 641 | +4.66 | 1,190 | -235 | -1,927 | -1,248/1,702/1,618/-235 | DEAD-IN-HOLD | H26<=0 | - | reread |
| E1C_KEL_unirenko_40_60 | 60/60 | 450 | 6.0 | 1,101 | 137 | 2.28 | 1,354 | 975 | 627 | 498 | 263 | +2.75 | 544 | 369 | -402 | -584/808/973/369 | SESSION-CANDIDATE | - | - | reread |
| TB4E_renko_24_renko_40_ST3_SW38_T1 | 60/60 | 418 | 5.6 | 1,075 | 10 | 2.01 | 1,497 | 949 | 546 | 417 | 181 | +2.34 | 1,479 | -2,652 | -389 | -126/676/1,110/-2,652 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | 60/60 | 397 | 5.3 | 972 | -66 | 1.87 | 1,460 | 846 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_23_renko_20_PSD3_E20_5_T3 | 60/60 | 444 | 5.9 | 1,000 | -107 | 1.80 | 1,556 | 874 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_25_tick_500_PSD5_SW50_T1 | 60/60 | 470 | 6.3 | 708 | -276 | 1.43 | 1,383 | 579 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_22_renko_20_PSD15_VWAP_T3 | 60/60 | 234 | 3.1 | 1,040 | -615 | 1.25 | 2,325 | 913 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_29_tick_250_ST3_VWAP_T3 | 60/60 | 355 | 4.7 | 689 | -479 | 1.17 | 1,642 | 560 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_14_tick_1000_PSD30_E20_1_T2 | 60/60 | 290 | 3.9 | 758 | -571 | 1.14 | 1,869 | 630 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4D_volume_24_volume_1000_PSD5_SW38_T1 | 60/60 | 441 | 5.9 | 552 | -438 | 1.11 | 1,391 | 422 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 185)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB4C_range_03_range_20_PSD10_SW38_T2 | 60/60 | 135 | 1.8 | 2,166 | 271 | 2.28 | 2,662 | 2,048 | 883 | 755 | 515 | +4.04 | 950 | -235 | -1,962 | -1,630/1,338/1,663/-235 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4A_time_24_time_15s_PSD15_SW38_T1 | 60/60 | 141 | 1.9 | 2,121 | 172 | 2.17 | 2,740 | 2,002 | 471 | 340 | 102 | +1.96 | 1,215 | -3,024 | -53 | -235/1,996/1,650/-3,024 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4B_tick_17_tick_1000_ST60_SW38_T3 | 60/60 | 118 | 1.6 | 2,341 | 186 | 2.16 | 3,028 | 2,223 | 2,497 | 2,382 | 2,140 | +12.17 | 1,153 | 6,479 | -463 | 212/1,533/2,287/6,479 | SESSION-CANDIDATE | - | - | reread |
| TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 60/60 | 190 | 2.5 | 1,795 | 11 | 2.00 | 2,506 | 1,673 | 74 | -60 | -296 | -0.04 | -1,098 | 4,413 | -2,054 | -1,209/189/1,540/4,413 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TB4B_tick_24_tick_500_PSD10_SW38_T1 | 60/60 | 136 | 1.8 | 1,691 | -120 | 1.86 | 2,545 | 1,570 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_18_renko_40_ST15_SW50_T1 | 60/60 | 125 | 1.7 | 1,985 | -218 | 1.80 | 3,095 | 1,865 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_05_tick_250_PSD15_SW62_T3 | 60/60 | 158 | 2.1 | 1,200 | -349 | 1.54 | 2,177 | 1,075 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| E1B_EMA_unirenko_20_30 | 60/60 | 245 | 3.3 | 928 | -324 | 1.48 | 1,760 | 801 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4A_time_26_time_30s_EMA20030_SW62_T2 | 60/60 | 119 | 1.6 | 1,614 | -564 | 1.48 | 3,060 | 1,491 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4D_volume_16_volume_500_ST10_E20_5_T3 | 60/60 | 138 | 1.8 | 1,387 | -522 | 1.45 | 2,682 | 1,263 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 234)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1C_KEL_range_40 | 60/60 | 1364 | 18.2 | 871 | 269 | 2.88 | 846 | 745 | 355 | 224 | -8 | +1.38 | 154 | 435 | 749 | -90/905/427/435 | SESSION-CANDIDATE | - | - | reread |
| TB4D_volume_07_volume_500_ST15_E20_1_T1 | 60/60 | 1111 | 14.8 | 675 | 73 | 2.24 | 846 | 547 | 704 | 577 | 346 | +3.14 | 85 | 2,129 | -18 | -163/940/14/2,129 | SESSION-CANDIDATE | - | - | reread |
| TB4C_range_00_range_40_ST3_E20_1_T1 | 60/60 | 1133 | 15.1 | 678 | 16 | 2.04 | 930 | 550 | 814 | 689 | 457 | +3.70 | 593 | 987 | 441 | 306/948/242/987 | SESSION-CANDIDATE | - | - | reread |
| TB4C_range_21_range_80_HMA555_E20_1_T2 | 60/60 | 844 | 11.3 | 712 | -6 | 1.98 | 1,008 | 582 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4W_06_time_30s_ST3_E20_1_T2_ntime14 | 60/60 | 899 | 12.0 | 841 | -14 | 1.96 | 1,201 | 712 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_27_tick_2000_ST3_FLIP_T2 | 60/60 | 509 | 6.8 | 929 | -57 | 1.88 | 1,385 | 802 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_07_renko_20_HMA555_E20_1_T1 | 60/60 | 1097 | 14.6 | 620 | -67 | 1.80 | 965 | 492 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_01_tick_500_ST3_VWAP_T1 | 60/60 | 438 | 5.8 | 999 | -140 | 1.75 | 1,601 | 871 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 60/60 | 1043 | 13.9 | 643 | -105 | 1.71 | 1,051 | 516 | 841 | 716 | 485 | +3.84 | 847 | 314 | 808 | 745/777/357/314 | SESSION-CANDIDATE | - | - |  |
| TB4D_volume_22_volume_2000_PSD3_VWAP_T3 | 60/60 | 342 | 4.6 | 910 | -210 | 1.62 | 1,573 | 782 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 230)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB4B_tick_28_tick_2000_ST10_E20_1_T3 | 60/60 | 449 | 6.0 | 1,163 | 253 | 2.55 | 1,279 | 1,048 | 1,556 | 1,445 | 1,236 | +7.49 | 1,618 | 778 | -200 | -541/865/1,599/778 | SESSION-CANDIDATE | - | - | reread |
| TB4B_tick_20_tick_1000_ST15_FLIP_T2 | 60/60 | 179 | 2.4 | 1,746 | 266 | 2.35 | 2,079 | 1,639 | 1,870 | 1,764 | 1,562 | +9.08 | 2,440 | -169 | -1,083 | -161/473/2,278/-169 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4W_24_renko_40_ST10_E20_1_T3_nrenko28 | 60/60 | 533 | 7.1 | 859 | 35 | 2.08 | 1,158 | 738 | 437 | 316 | 106 | +1.84 | 899 | -2,138 | -13 | -278/842/772/-2,138 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TB4W_25_renko_40_ST15_E20_1_T3_nrenko28 | 60/60 | 520 | 6.9 | 811 | -30 | 1.92 | 1,182 | 690 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| E1B_EMA_unirenko_10_15 | 60/60 | 1199 | 16.0 | 477 | -68 | 1.74 | 767 | 353 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_10_renko_40_EMA2003_SW38_T3 | 60/60 | 446 | 5.9 | 688 | -341 | 1.33 | 1,446 | 565 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_08_renko_20_HMA5515_VWAP_T2 | 60/60 | 169 | 2.3 | 1,173 | -595 | 1.32 | 2,485 | 1,058 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4A_time_20_time_30s_HMA5515_FLIP_T2 | 60/60 | 223 | 3.0 | 949 | -523 | 1.28 | 2,068 | 831 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| E1B_EMA_renko_10 | 60/60 | 1144 | 15.3 | 420 | -260 | 1.23 | 955 | 294 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_27_tick_2000_ST3_FLIP_T2 | 60/60 | 291 | 3.9 | 805 | -578 | 1.16 | 1,944 | 688 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### CLOSE: no cell with PRE n >= 100

### NY (N screened 234)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TB4B_tick_27_tick_2000_ST3_FLIP_T2 | 60/60 | 800 | 10.7 | 884 | 197 | 2.57 | 965 | 760 | 200 | 72 | -149 | +0.62 | 236 | -614 | -359 | -607/628/619/-614 | DEAD-IN-HOLD | H26<=0 | - |  |
| TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 60/60 | 1762 | 23.5 | 475 | 16 | 2.06 | 646 | 348 | 490 | 366 | 149 | +2.09 | 516 | -134 | 547 | 311/575/262/-134 | DEAD-IN-HOLD | H26<=0 | - |  |
| E1C_KEL_range_40 | 60/60 | 2195 | 29.3 | 449 | 5 | 2.02 | 624 | 320 | 16 | -115 | -340 | -0.32 | -88 | -206 | 393 | -141/521/58/-206 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| TB4B_tick_28_tick_2000_ST10_E20_1_T3 | 60/60 | 1203 | 16.0 | 514 | -54 | 1.80 | 799 | 389 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4D_volume_07_volume_500_ST15_E20_1_T1 | 60/60 | 1894 | 25.3 | 401 | -54 | 1.75 | 640 | 274 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_11_tick_2000_ST10_SW50_T3 | 60/60 | 1006 | 13.4 | 612 | -121 | 1.66 | 1,030 | 489 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4C_range_21_range_80_HMA555_E20_1_T2 | 60/60 | 1378 | 18.4 | 360 | -113 | 1.52 | 664 | 231 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4D_volume_00_volume_1000_ST15_E20_1_T1 | 60/60 | 1769 | 23.6 | 410 | -136 | 1.50 | 768 | 284 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4E_renko_28_renko_20_ST15_E20_1_T3 | 60/60 | 1919 | 25.6 | 341 | -187 | 1.29 | 742 | 213 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TB4B_tick_20_tick_1000_ST15_FLIP_T2 | 60/60 | 566 | 7.5 | 648 | -371 | 1.27 | 1,431 | 525 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

| session | cell | brk | PRE n | PRE $ stored | PRE $ MEAS | HOLD $ (MEAS if fixed) | HOLD pts | HOLD MDE $ | H25 $ | H26 $ | X 2023 $ | HOLD CONS $ | tier | pooled PRE $ | index verdict | HOLD look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | TB4C_range_24_range_80_ST5_SW38_T1 | 60/60 | 595 | 1,268 | 1,143 | 599 | +3.25 | 2,182 | 194 | 2,018 | -54 | 361 | SESSION-CANDIDATE | 310 | CANDIDATE | reread |
| ASIA | E1A_RENKOC5_A3_r48 | dyn | 424 | 2,341 |  | 2,321 | +11.86 | 2,850 | 1,658 | 4,151 | -13 |  | STORED-CANDIDATE(MEASURED n/a) | 117 | UNLABELLED | reread |
| LONDON | E1C_KEL_unirenko_40_60 | 60/60 | 450 | 1,101 | 975 | 498 | +2.75 | 2,940 | 544 | 369 | -402 | 263 | SESSION-CANDIDATE | -86 | UNLABELLED | reread |
| PREOPEN | TB4B_tick_17_tick_1000_ST60_SW38_T3 | 60/60 | 118 | 2,341 | 2,223 | 2,382 | +12.17 | 4,845 | 1,153 | 6,479 | -463 | 2,140 | SESSION-CANDIDATE | -6 | DEAD | reread |
| NY-AM | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 60/60 | 1043 | 643 | 516 | 716 | +3.84 | 1,567 | 847 | 314 | 808 | 485 | SESSION-CANDIDATE | 592 | CANDIDATE | first |
| NY-AM | TB4C_range_00_range_40_ST3_E20_1_T1 | 60/60 | 1133 | 678 | 550 | 689 | +3.70 | 1,207 | 593 | 987 | 441 | 457 | SESSION-CANDIDATE | 339 | CANDIDATE | reread |
| NY-AM | TB4D_volume_07_volume_500_ST15_E20_1_T1 | 60/60 | 1111 | 675 | 547 | 577 | +3.14 | 1,572 | 85 | 2,129 | -18 | 346 | SESSION-CANDIDATE | 296 | PASS | reread |
| NY-AM | E1C_KEL_range_40 | 60/60 | 1364 | 871 | 745 | 224 | +1.38 | 1,325 | 154 | 435 | 749 | -8 | SESSION-CANDIDATE | 381 | UNLABELLED | reread |
| NY-PM | TB4B_tick_28_tick_2000_ST10_E20_1_T3 | 60/60 | 449 | 1,163 | 1,048 | 1,445 | +7.49 | 2,415 | 1,618 | 778 | -200 | 1,236 | SESSION-CANDIDATE | 282 | DEAD | reread |

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median -0.00 over 10 session pairs; ASIA vs NY-AM [0.36], ASIA vs LONDON [-0.12], NY-AM vs NY-PM [-0.01]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| ASIA | s | E1A_RENKOC5_A3_r48 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 188 | 325 | 15,304 | [-1,297, 31,904] | 22,791 |  |
| LONDON | s | TB4A_time_29_time_30s_ST60_VWAP_T3 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 92 | 254 | -3,126 | [-14,155, 7,903] | 15,142 |  |
| LONDON | m | TB4A_time_29_time_30s_ST60_VWAP_T3 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 92 | 254 | -2,469 | [-13,587, 8,649] | 15,264 |  |
| PREOPEN | s | TB4C_range_03_range_20_PSD10_SW38_T2 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 61 | 69 | 1,525 | [-4,943, 7,993] | 8,880 |  |
| PREOPEN | m | TB4C_range_03_range_20_PSD10_SW38_T2 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 61 | 69 | 1,569 | [-4,932, 8,070] | 8,925 |  |
| NY-AM | s | E1C_KEL_range_40 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 613 | 459 | -5,271 | [-31,617, 21,075] | 36,170 |  |
| NY-AM | m | E1C_KEL_range_40 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 613 | 459 | -5,968 | [-32,479, 20,542] | 36,396 |  |
| NY-PM | s | TB4B_tick_28_tick_2000_ST10_E20_1_T3 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 170 | 274 | 9,105 | [-6,773, 24,983] | 21,799 |  |
| NY-PM | m | TB4B_tick_28_tick_2000_ST10_E20_1_T3 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 170 | 274 | 9,554 | [-6,442, 25,551] | 21,961 |  |
| NY | s | TB4B_tick_27_tick_2000_ST3_FLIP_T2 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 347 | 733 | -9,056 | [-34,096, 15,983] | 34,376 |  |
| NY | m | TB4B_tick_27_tick_2000_ST3_FLIP_T2 | TB4E_renko_14_renko_20_HMA555_E20_1_T2 | 347 | 733 | -7,608 | [-32,879, 17,662] | 34,694 |  |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best ST3 (18 cells, +624), HMA555 (7 cells, +614), nvolume21 (5 cells, +534); worst PSD3 (5, -1362), 29 (5, -709), PSD10 (5, -638)
  - LONDON: best 29 (5 cells, +813), PSD3 (5 cells, +640), 250 (9 cells, +507); worst nrenko28 (5, -667), ST30 (16, -559), 13 (5, -513)
  - PREOPEN: best ST60 (9 cells, +910), PSD10 (5 cells, +887), EMA20030 (6 cells, +883); worst nrenko28 (5, -879), RENKOC2 (6, -811), E1A (16, -758)
  - NY-AM: best 14 (6 cells, +477), ST3 (19 cells, +471), nvolume21 (5 cells, +436); worst ST30 (17, -558), 29 (5, -465), 15 (10, -368)
  - NY-PM: best nrenko28 (5 cells, +675), HMA5515 (10 cells, +557), ST15 (11 cells, +492); worst PSD15 (5, -621), PSD3 (5, -609), PSD10 (5, -464)
  - NY: best ST3 (19 cells, +289), 00 (6 cells, +282), 1 (46 cells, +270); worst PSD15 (6, -425), PSD10 (6, -390), ST30 (17, -331)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 9 cell-sessions, 12230 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
