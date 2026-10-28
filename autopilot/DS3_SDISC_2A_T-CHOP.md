# DS3_SDISC_2A_T-CHOP - session-native re-search of the T-CHOP family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **267** (T-CHOP cells (B*)); fixed 60/60 bracket (analytic MEASURED available): **0**; dynamic/other exits (stored basis only): 267. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 52 | 0 | 1 | 0 | 0 | 0 | 1 |
| LONDON | 76 | 0 | 1 | 0 | 0 | 0 | 1 |
| PREOPEN | 38 | 0 | 1 | 0 | 1 | 0 | 0 |
| NY-AM | 90 | 0 | 1 | 0 | 0 | 0 | 1 |
| NY-PM | 52 | 0 | 1 | 0 | 0 | 0 | 1 |
| CLOSE | 46 | 0 | 1 | 0 | 1 | 0 | 0 |
| NY | 97 | 0 | 1 | 0 | 0 | 0 | 1 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 52)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B2C_X13_IG1 | dyn | 746 | 9.9 | 33 | -288 | 0.21 | 451 |  | 34 |  |  | +0.43 | 249 | -959 | -321 | -284/-174/253/-959 | DEAD-IN-HOLD | H26<=0 | - |  |
| B2C_X13_IG2 | dyn | 406 | 5.4 | -9 | -441 | -0.04 | 606 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X13_IG3 | dyn | 1007 | 13.4 | -65 | -349 | -0.45 | 399 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X22_IG2 | dyn | 137 | 1.8 | -475 | -1,757 | -0.74 | 1,802 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B7_boll_time_15m | dyn | 299 | 4.0 | -237 | -785 | -0.86 | 770 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X22_IG3 | dyn | 302 | 4.0 | -281 | -906 | -0.89 | 879 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X13 | dyn | 1359 | 18.1 | -138 | -399 | -1.05 | 367 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X22_IG1 | dyn | 269 | 3.6 | -471 | -1,332 | -1.09 | 1,210 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X13_L2_S0 | dyn | 1180 | 15.7 | -165 | -465 | -1.10 | 422 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X13_L1_S0 | dyn | 1244 | 16.6 | -187 | -476 | -1.29 | 406 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### LONDON (N screened 76)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X26 | dyn | 216 | 2.9 | 228 | -471 | 0.65 | 982 |  | -1,056 |  |  | -5.02 | -1,321 | -218 | -144 | -53/-114/-266/-218 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| B8_asia_time_15m_IG1 | dyn | 176 | 2.3 | 389 | -981 | 0.57 | 1,925 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B8_vwap3_time_15m_IG5 | dyn | 264 | 3.5 | 173 | -465 | 0.54 | 897 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B7_boll_time_15m | dyn | 642 | 8.6 | 81 | -325 | 0.40 | 570 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X16_L2_S0 | dyn | 1550 | 20.7 | 54 | -331 | 0.28 | 541 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X16 | dyn | 1694 | 22.6 | 49 | -308 | 0.27 | 502 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B8_boll_time_15m_IG1 | dyn | 320 | 4.3 | 55 | -449 | 0.22 | 707 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X20_IG1 | dyn | 189 | 2.5 | 144 | -1,226 | 0.21 | 1,925 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X16_L1_S0 | dyn | 1599 | 21.3 | 15 | -362 | 0.08 | 531 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B9_DS | dyn | 199 | 2.7 | 39 | -1,652 | 0.05 | 2,377 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 38)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B5_T3_A | dyn | 276 | 3.7 | -52 | -1,571 | -0.07 | 2,134 |  | 2,198 |  |  | +11.25 | 2,253 | 1,791 | -617 | -811/-360/1,469/1,791 | STORED-CANDIDATE(MEASURED n/a) | - | - |  |
| X14 | dyn | 211 | 2.8 | -33 | -785 | -0.09 | 1,056 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B7_vwap3_volume_2500 | dyn | 130 | 1.7 | -92 | -2,145 | -0.09 | 2,885 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B5_T3_B | dyn | 372 | 5.0 | -65 | -1,151 | -0.12 | 1,526 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B5_T9_A | dyn | 132 | 1.8 | -422 | -2,757 | -0.36 | 3,281 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X13 | dyn | 305 | 4.1 | -145 | -943 | -0.36 | 1,122 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X28 | dyn | 233 | 3.1 | -187 | -1,122 | -0.40 | 1,314 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B5_T6_A | dyn | 568 | 7.6 | -237 | -1,319 | -0.44 | 1,521 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X13_L1_S0 | dyn | 297 | 4.0 | -171 | -937 | -0.44 | 1,078 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X28_L2_S0 | dyn | 218 | 2.9 | -225 | -1,225 | -0.45 | 1,405 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 90)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B5_T4_A | dyn | 318 | 4.2 | 701 | -956 | 0.84 | 2,329 |  | -2,046 |  |  | -9.97 | -1,307 | -4,387 | -1,152 | -1,104/1,237/-871/-4,387 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| B9_SL | dyn | 212 | 2.8 | 784 | -1,194 | 0.79 | 2,779 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L1_S0 | dyn | 145 | 1.9 | 652 | -1,122 | 0.73 | 2,494 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B9_S_IG1 | dyn | 114 | 1.5 | 657 | -1,210 | 0.70 | 2,624 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L2_S0 | dyn | 146 | 1.9 | 613 | -1,161 | 0.69 | 2,492 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X24 | dyn | 148 | 2.0 | 518 | -1,222 | 0.59 | 2,444 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L1_S20 | dyn | 145 | 1.9 | 631 | -1,577 | 0.57 | 3,104 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L2_S20 | dyn | 146 | 1.9 | 605 | -1,595 | 0.55 | 3,091 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X28_IG4 | dyn | 276 | 3.7 | 289 | -929 | 0.47 | 1,711 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B11_pdhl_range_40_LM0_S0 | dyn | 195 | 2.6 | 672 | -2,782 | 0.39 | 4,854 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 52)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B2C_X13_IG2 | dyn | 167 | 2.2 | 860 | -149 | 1.70 | 1,418 |  | 70 |  |  | +0.61 | -282 | 1,577 | -141 | -538/411/612/1,577 | DEAD-IN-HOLD | H25<=0 | - |  |
| B6_X16_L2_S0 | dyn | 732 | 9.8 | 664 | -177 | 1.57 | 1,183 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X16_IG1 | dyn | 430 | 5.7 | 766 | -358 | 1.36 | 1,581 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X16_L1_S0 | dyn | 743 | 9.9 | 548 | -271 | 1.33 | 1,151 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B8_vwap3_time_15m_IG1 | dyn | 292 | 3.9 | 665 | -332 | 1.33 | 1,400 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X16 | dyn | 755 | 10.1 | 469 | -337 | 1.16 | 1,133 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X16_IG2 | dyn | 130 | 1.7 | 1,024 | -947 | 1.03 | 2,769 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X16_L2_S20 | dyn | 732 | 9.8 | 402 | -672 | 0.75 | 1,510 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B5_T4_A | dyn | 145 | 1.9 | 631 | -1,070 | 0.74 | 2,390 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B7_vwap3_time_15m | dyn | 451 | 6.0 | 280 | -558 | 0.67 | 1,177 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### CLOSE (N screened 46)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_F01 | dyn | 291 | 3.9 | 694 | -326 | 1.36 | 1,433 |  | 1,510 |  |  | +7.81 | 978 | 3,657 | -61 | -132/434/1,233/3,657 | STORED-CANDIDATE(MEASURED n/a) | - | - |  |
| B4_F19_K5 | dyn | 191 | 2.5 | 603 | -310 | 1.32 | 1,283 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B4_F19_K3 | dyn | 213 | 2.8 | 549 | -309 | 1.27 | 1,206 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B3_F02 | dyn | 386 | 5.1 | 459 | -360 | 1.12 | 1,150 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B3_F04 | dyn | 210 | 2.8 | 534 | -448 | 1.08 | 1,381 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B4_F19_K8 | dyn | 238 | 3.2 | 82 | -72 | 1.06 | 217 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B4_F08_K5 | dyn | 254 | 3.4 | 419 | -477 | 0.93 | 1,258 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B3_F07 | dyn | 206 | 2.7 | 453 | -589 | 0.87 | 1,464 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B4_F20_K3 | dyn | 258 | 3.4 | 318 | -444 | 0.83 | 1,072 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B4_F20_K5 | dyn | 226 | 3.0 | 305 | -529 | 0.73 | 1,172 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY (N screened 97)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B2C_X13_IG2 | dyn | 266 | 3.5 | 609 | -123 | 1.66 | 1,028 |  | 138 |  |  | +0.95 | -148 | 1,258 | -227 | -260/60/613/1,258 | DEAD-IN-HOLD | H25<=0 | - |  |
| B9_SL | dyn | 308 | 4.1 | 908 | -532 | 1.26 | 2,024 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B5_T4_A | dyn | 463 | 6.2 | 679 | -526 | 1.12 | 1,693 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B9_S_IG1 | dyn | 168 | 2.2 | 689 | -792 | 0.93 | 2,081 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L1_S0 | dyn | 145 | 1.9 | 652 | -1,122 | 0.73 | 2,494 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L2_S0 | dyn | 146 | 1.9 | 613 | -1,161 | 0.69 | 2,492 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| X24 | dyn | 148 | 2.0 | 518 | -1,222 | 0.59 | 2,444 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L1_S20 | dyn | 145 | 1.9 | 631 | -1,577 | 0.57 | 3,104 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B2C_X28_IG4 | dyn | 295 | 3.9 | 336 | -855 | 0.56 | 1,673 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| B6_X24_L2_S20 | dyn | 146 | 1.9 | 605 | -1,595 | 0.55 | 3,091 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

| session | cell | brk | PRE n | PRE $ stored | PRE $ MEAS | HOLD $ (MEAS if fixed) | HOLD pts | HOLD MDE $ | H25 $ | H26 $ | X 2023 $ | HOLD CONS $ | tier | pooled PRE $ | index verdict | HOLD look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PREOPEN | B5_T3_A | dyn | 276 | -52 |  | 2,198 | +11.25 | 3,449 | 2,253 | 1,791 | -617 |  | STORED-CANDIDATE(MEASURED n/a) | -532 | UNLABELLED | first |
| CLOSE | B3_F01 | dyn | 291 | 694 |  | 1,510 | +7.81 | 1,997 | 978 | 3,657 | -61 |  | STORED-CANDIDATE(MEASURED n/a) | 694 | UNLABELLED | first |

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median +0.16 over 10 session pairs; ASIA vs NY-AM [0.05], ASIA vs LONDON [0.45], NY-AM vs NY-PM [0.15]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| CLOSE | s | B3_F01 | B3_F01 | 136 | 136 | 0 | [0, 0] | 0 | same cell |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best X13 (9 cells, +553), B2C (15 cells, +368), X16 (9 cells, +306); worst B5 (8, -960), X28 (9, -236), S20 (6, -70)
  - LONDON: best 15m (10 cells, +396), B8 (7 cells, +359), X20 (6 cells, +343); worst A (5, -701), IG2 (5, -473), B5 (10, -432)
  - PREOPEN: best X13 (6 cells, +478), B5 (7 cells, +414), S0 (6 cells, +337); worst X16 (6, -599), boll (6, -449), S20 (6, -424)
  - NY-AM: best X24 (6 cells, +1034), B11 (8 cells, +1017), S0 (12 cells, +648); worst vwap3 (8, -627), B8 (6, -600), X16 (8, -569)
  - NY-PM: best X16 (7 cells, +932), B2C (7 cells, +563), time (5 cells, +388); worst B7 (12, -550), vwap3 (7, -415), boll (6, -318)
  - CLOSE: best K5 (5 cells, +107), F19 (8 cells, +98), B3 (17 cells, +95); worst F05 (8, -139), F20 (8, -130), B4 (27, -103)
  - NY: best B11 (8 cells, +972), X24 (6 cells, +916), S0 (12 cells, +674); worst B8 (7, -537), B7 (17, -503), vwap3 (9, -481)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 0 cell-sessions, 0 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
