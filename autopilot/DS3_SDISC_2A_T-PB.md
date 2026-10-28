# DS3_SDISC_2A_T-PB - session-native re-search of the T-PB family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **158** (T-PB (pullback/PBX TP), T-PB (pullback base)); fixed 60/60 bracket (analytic MEASURED available): **158**; dynamic/other exits (stored basis only): 0. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 158 | 24 | 12 | 2 | 0 | 6 | 4 |
| LONDON | 158 | 1 | 2 | 0 | 0 | 1 | 1 |
| PREOPEN | 52 | 0 | 2 | 0 | 0 | 0 | 2 |
| NY-AM | 158 | 7 | 6 | 1 | 0 | 2 | 3 |
| NY-PM | 158 | 4 | 5 | 1 | 0 | 1 | 3 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| NY | 158 | 6 | 4 | 1 | 0 | 0 | 3 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 158)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_PB_HMA55_EMA1_T1_W60_s+3 | 60/60 | 690 | 9.2 | 1,384 | 685 | 3.95 | 981 | 1,042 | 112 | -430 | -661 | -1.89 | -389 | -571 | -574 | -898/1,082/343/-571 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PB_HMA55_EMA1_T1 | 60/60 | 695 | 9.3 | 1,425 | 658 | 3.70 | 1,077 | 1,082 | 414 | -115 | -347 | -0.31 | 192 | -1,093 | -1,340 | -1,816/861/814/-1,093 | DEAD-IN-HOLD | HOLD mean<=0;H26<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T1_W15_s+0 | 60/60 | 696 | 9.3 | 1,461 | 674 | 3.70 | 1,106 | 1,116 | 730 | 213 | -21 | +1.33 | 506 | -721 | -1,429 | -2,002/1,081/877/-721 | DEAD-IN-HOLD | H26<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T1_W30_s+3 | 60/60 | 691 | 9.2 | 1,335 | 614 | 3.69 | 1,012 | 990 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB5_depth_atr0.5_W15_s+0 | 60/60 | 342 | 4.6 | 2,372 | 934 | 3.29 | 2,020 | 2,069 | 905 | 393 | 158 | +2.22 | 598 | -175 | 640 | -120/2,108/1,376/-175 | MEASURED-FAIL | H26<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T1_W60_s+0 | 60/60 | 695 | 9.3 | 1,256 | 481 | 3.23 | 1,089 | 910 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB5_depth_atr0.5_W15_s-3 | 60/60 | 387 | 5.2 | 1,851 | 707 | 3.23 | 1,607 | 1,542 | 1,570 | 1,089 | 848 | +5.70 | 1,633 | -533 | 763 | -188/1,381/1,801/-533 | MEASURED-FAIL | H26<=0 | - | reread |
| PB7_PB5_depth_atr0.5_W60_s-3 | 60/60 | 393 | 5.2 | 1,834 | 699 | 3.22 | 1,595 | 1,527 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB5_depth_atr0.5_W30_s-3 | 60/60 | 390 | 5.2 | 1,804 | 686 | 3.22 | 1,571 | 1,496 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB5_depth_atr0.5 | 60/60 | 342 | 4.6 | 2,303 | 835 | 3.13 | 2,062 | 1,999 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |

### LONDON (N screened 158)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB_PRIORDIR_SWZ_T3 | 60/60 | 393 | 5.2 | 1,037 | 96 | 2.19 | 1,322 | 671 | 24 | -492 | -714 | -2.20 | -522 | -372 | -797 | -950/1,173/-80/-372 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PB_PRIORDIR_SWZ_T1 | 60/60 | 365 | 4.9 | 1,105 | -51 | 1.90 | 1,624 | 748 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB6_ST60m_EMA20_5m_T1 | 60/60 | 328 | 4.4 | 935 | -223 | 1.61 | 1,627 | 581 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_ST10_FLIP_T1 | 60/60 | 308 | 4.1 | 918 | -228 | 1.60 | 1,611 | 565 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_HMA55_SWZ_T2 | 60/60 | 391 | 5.2 | 861 | -386 | 1.38 | 1,752 | 504 | 1,255 | 782 | 549 | +4.17 | 1,251 | -491 | 528 | 582/744/779/-491 | MEASURED-FAIL | H26<=0 | - |  |
| PB_HMA55_FLIP_T1 | 60/60 | 297 | 4.0 | 801 | -419 | 1.31 | 1,714 | 447 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_HMA55_VWAP_T1 | 60/60 | 174 | 2.3 | 937 | -633 | 1.19 | 2,206 | 588 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_EMA200_KELT_T3 | 60/60 | 404 | 5.4 | 690 | -482 | 1.17 | 1,647 | 328 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_PRIORDIR_EMA5_T3 | 60/60 | 379 | 5.1 | 599 | -478 | 1.11 | 1,513 | 225 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_HMA55_VWAP_T2 | 60/60 | 164 | 2.2 | 1,019 | -909 | 1.05 | 2,709 | 661 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 52)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB_ST10_EMA1_T3 | 60/60 | 126 | 1.7 | 1,610 | -262 | 1.71 | 2,630 | 1,329 | 377 | -98 | -318 | -0.23 | -600 | 3,251 | 761 | 843/78/1,474/3,251 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| PB_PRIORDIR_EMA1_T3 | 60/60 | 115 | 1.5 | 1,785 | -507 | 1.55 | 3,221 | 1,496 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB6_ST10m_EMA20_2m_T1 | 60/60 | 101 | 1.3 | 1,397 | -749 | 1.30 | 3,016 | 1,083 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB6_ST5m_EMA20_2m_T1 | 60/60 | 106 | 1.4 | 1,382 | -888 | 1.21 | 3,190 | 1,083 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_ST10_SWZ_T3 | 60/60 | 112 | 1.5 | 1,075 | -868 | 1.10 | 2,730 | 742 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_HMA55_EMA1_T3 | 60/60 | 130 | 1.7 | 1,069 | -902 | 1.08 | 2,770 | 769 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_PRIORDIR_EMA1_T1 | 60/60 | 130 | 1.7 | 1,118 | -1,021 | 1.04 | 3,006 | 802 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W15_s-3 | 60/60 | 108 | 1.4 | 996 | -1,365 | 0.84 | 3,317 | 668 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W30_s-3 | 60/60 | 111 | 1.5 | 1,030 | -1,547 | 0.80 | 3,622 | 717 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB6_ST3m_EMA20_2m_T1 | 60/60 | 103 | 1.4 | 875 | -1,381 | 0.77 | 3,171 | 555 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 158)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_PB_HMA55_EMA1_T2_W60_s-3 | 60/60 | 432 | 5.8 | 1,462 | 493 | 3.01 | 1,362 | 1,192 | 653 | 185 | -28 | +1.18 | -17 | 991 | 494 | 442/1,382/195/991 | MEASURED-FAIL | H25<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T2_W30_s-3 | 60/60 | 451 | 6.0 | 1,263 | 284 | 2.57 | 1,375 | 979 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB_HMA55_EMA1_T2_W15_s+0 | 60/60 | 460 | 6.1 | 1,136 | 134 | 2.26 | 1,409 | 828 | 427 | -38 | -248 | +0.07 | -108 | 356 | 362 | -239/1,584/-158/356 | MEASURED-FAIL | HOLD mean<=0;H25<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T2_W15_s-3 | 60/60 | 439 | 5.9 | 1,098 | 127 | 2.25 | 1,365 | 813 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB_HMA55_EMA1_T1_W15_s-3 | 60/60 | 512 | 6.8 | 1,128 | 107 | 2.20 | 1,435 | 827 | 983 | 534 | 318 | +2.93 | 302 | 1,466 | 234 | 177/608/553/1,466 | SESSION-CANDIDATE | - | - | reread |
| PB7_PB5_depth_atr0.5_W15_s-3 | 60/60 | 415 | 5.5 | 1,098 | 95 | 2.18 | 1,409 | 793 | 409 | -71 | -284 | -0.10 | 111 | -930 | 750 | 176/1,006/-3/-930 | DEAD-IN-HOLD | HOLD mean<=0;H26<=0 | - | reread |
| PB_EMA200_FLIP_T2 | 60/60 | 277 | 3.7 | 1,241 | 61 | 2.09 | 1,659 | 908 | 18 | -515 | -738 | -2.32 | -592 | -207 | -962 | -541/1,163/22/-207 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T1_W30_s-3 | 60/60 | 514 | 6.9 | 1,005 | -10 | 1.97 | 1,427 | 695 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB5_depth_atr0.5_W30_s+3 | 60/60 | 334 | 4.5 | 1,160 | -13 | 1.97 | 1,648 | 837 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB5_depth_atr0.5 | 60/60 | 370 | 4.9 | 1,131 | -47 | 1.91 | 1,656 | 813 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 158)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB5_fade_PRIORDIR_VWAP | 60/60 | 124 | 1.7 | 1,972 | 186 | 2.20 | 2,510 | 1,702 | -1,110 | -1,608 | -1,799 | -7.78 | 352 | -9,642 | -2,844 | -2,616/1,325/1,119/-9,642 | DEAD-IN-HOLD | HOLD mean<=0;H26<=0 | - | reread |
| PB_EMA200_VWAP_T3 | 60/60 | 128 | 1.7 | 1,894 | 61 | 2.06 | 2,576 | 1,613 | 364 | -98 | -302 | -0.23 | -86 | -132 | -1,272 | 56/1,312/360/-132 | MEASURED-FAIL | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PB7_PB_HMA55_EMA1_T2_W60_s+3 | 60/60 | 297 | 4.0 | 1,309 | 4 | 2.00 | 1,835 | 1,026 | 259 | -137 | -319 | -0.43 | -1,062 | 4,206 | -172 | -905/950/452/4,206 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| PB_ST10_FLIP_T1 | 60/60 | 143 | 1.9 | 1,437 | 1 | 1.99 | 2,017 | 1,170 | 1,982 | 1,632 | 1,436 | +8.42 | 1,894 | -980 | -1,875 | -332/418/1,911/-980 | DEAD-IN-HOLD | H26<=0 | - | reread |
| PB_ST10_SWZ_T3 | 60/60 | 263 | 3.5 | 750 | -222 | 1.54 | 1,365 | 463 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W60_s+0 | 60/60 | 276 | 3.7 | 821 | -562 | 1.18 | 1,944 | 509 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_ST10_VWAP_T3 | 60/60 | 124 | 1.7 | 1,111 | -952 | 1.07 | 2,898 | 824 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB_ST10_SWZ_T1 | 60/60 | 253 | 3.4 | 632 | -576 | 1.04 | 1,698 | 367 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB5_depth_atr0.5 | 60/60 | 249 | 3.3 | 491 | -500 | 0.99 | 1,393 | 210 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_ST10_SWZ_T1_W15_s+0 | 60/60 | 253 | 3.4 | 577 | -603 | 0.97 | 1,658 | 307 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### CLOSE: no cell with PRE n >= 100

### NY (N screened 158)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_PB_HMA55_EMA1_T2_W60_s-3 | 60/60 | 675 | 9.0 | 934 | 187 | 2.49 | 1,049 | 655 | 907 | 483 | 283 | +2.67 | 245 | 1,575 | 110 | 39/1,342/-264/1,575 | SESSION-CANDIDATE | - | - |  |
| PB5_depth_atr0.5 | 60/60 | 619 | 8.3 | 874 | 172 | 2.48 | 987 | 571 | -89 | -589 | -795 | -2.69 | -402 | -1,377 | 119 | 23/836/-278/-1,377 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| PB7_PB5_depth_atr0.5_W60_s+0 | 60/60 | 624 | 8.3 | 794 | 116 | 2.33 | 954 | 490 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB5_depth_atr0.5_W15_s+0 | 60/60 | 591 | 7.9 | 839 | 106 | 2.28 | 1,031 | 539 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB_HMA55_EMA1_T2_W30_s-3 | 60/60 | 695 | 9.3 | 792 | 84 | 2.23 | 995 | 496 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| PB7_PB_HMA55_EMA1_T2_W60_s+3 | 60/60 | 750 | 10.0 | 834 | 31 | 2.07 | 1,128 | 536 | -167 | -642 | -844 | -2.95 | -954 | 649 | -282 | -692/552/-142/649 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W15_s+0 | 60/60 | 725 | 9.7 | 665 | -54 | 1.84 | 1,011 | 352 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T1_W15_s-3 | 60/60 | 737 | 9.8 | 719 | -68 | 1.82 | 1,107 | 413 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W15_s+3 | 60/60 | 709 | 9.5 | 665 | -79 | 1.78 | 1,045 | 368 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PB7_PB_HMA55_EMA1_T2_W15_s-3 | 60/60 | 672 | 9.0 | 622 | -88 | 1.75 | 998 | 321 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

| session | cell | brk | PRE n | PRE $ stored | PRE $ MEAS | HOLD $ (MEAS if fixed) | HOLD pts | HOLD MDE $ | H25 $ | H26 $ | X 2023 $ | HOLD CONS $ | tier | pooled PRE $ | index verdict | HOLD look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | PB_HMA55_EMA1_T2 | 60/60 | 608 | 1,147 | 790 | 218 | +1.35 | 1,902 | 40 | 871 | 97 | -17 | SESSION-CANDIDATE | 504 | PASS | reread |
| ASIA | PB_HMA55_EMA1_T3 | 60/60 | 661 | 1,050 | 698 | 201 | +1.26 | 1,880 | 86 | 553 | -1,818 | -35 | SESSION-CANDIDATE | 77 | DEAD | reread |
| NY-AM | PB7_PB_HMA55_EMA1_T1_W15_s-3 | 60/60 | 512 | 1,128 | 827 | 534 | +2.93 | 2,054 | 302 | 1,466 | 234 | 318 | SESSION-CANDIDATE | 287 | CANDIDATE | reread |
| NY-PM | PB_HMA55_SWZ_T2 | 60/60 | 243 | 554 | 290 | 399 | +2.25 | 2,497 | 308 | 1,064 | -996 | 221 | SESSION-CANDIDATE | 711 | CANDIDATE | first |
| NY | PB7_PB_HMA55_EMA1_T2_W60_s-3 | 60/60 | 675 | 934 | 655 | 483 | +2.67 | 1,775 | 245 | 1,575 | 110 | 283 | SESSION-CANDIDATE | 618 | PASS | first |

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median -0.15 over 10 session pairs; ASIA vs NY-AM [0.44], ASIA vs LONDON [-0.21], NY-AM vs NY-PM [-0.02]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| ASIA | s | PB7_PB_HMA55_EMA1_T1_W60_s+3 | PB_HMA55_SWZ_T2 | 313 | 245 | -2,476 | [-13,292, 8,340] | 14,849 |  |
| ASIA | m | PB7_PB_HMA55_EMA1_T1_W60_s+3 | PB_HMA55_SWZ_T2 | 313 | 245 | -3,677 | [-14,956, 7,602] | 15,485 |  |
| LONDON | s | PB_PRIORDIR_SWZ_T3 | PB_HMA55_SWZ_T2 | 175 | 171 | -6,576 | [-19,003, 5,851] | 17,061 |  |
| LONDON | m | PB_PRIORDIR_SWZ_T3 | PB_HMA55_SWZ_T2 | 175 | 171 | -6,868 | [-19,874, 6,138] | 17,856 |  |
| PREOPEN | s | PB_ST10_EMA1_T3 | PB_HMA55_SWZ_T2 | 46 | 43 | 3,305 | [-2,960, 9,569] | 8,600 |  |
| PREOPEN | m | PB_ST10_EMA1_T3 | PB_HMA55_SWZ_T2 | 46 | 43 | 3,331 | [-3,238, 9,900] | 9,018 |  |
| NY-AM | s | PB7_PB_HMA55_EMA1_T2_W60_s-3 | PB_HMA55_SWZ_T2 | 204 | 159 | 5,938 | [-5,237, 17,113] | 15,342 |  |
| NY-AM | m | PB7_PB_HMA55_EMA1_T2_W60_s-3 | PB_HMA55_SWZ_T2 | 204 | 159 | 5,445 | [-6,205, 17,096] | 15,995 |  |
| NY-PM | s | PB5_fade_PRIORDIR_VWAP | PB_HMA55_SWZ_T2 | 51 | 92 | -4,016 | [-12,815, 4,783] | 12,080 |  |
| NY-PM | m | PB5_fade_PRIORDIR_VWAP | PB_HMA55_SWZ_T2 | 51 | 92 | -3,709 | [-12,885, 5,467] | 12,597 |  |
| NY | s | PB7_PB_HMA55_EMA1_T2_W60_s-3 | PB_HMA55_SWZ_T2 | 313 | 251 | 8,395 | [-6,160, 22,950] | 19,982 |  |
| NY | m | PB7_PB_HMA55_EMA1_T2_W60_s-3 | PB_HMA55_SWZ_T2 | 313 | 251 | 7,837 | [-7,352, 23,027] | 20,854 |  |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best atr0.5 (9 cells, +1559), depth (14 cells, +1048), s+0 (10 cells, +765); worst fade (8, -1027), PRIORDIR (20, -767), EMA5 (17, -459)
  - LONDON: best ST60m (12 cells, +405), SWZ (20 cells, +391), T3 (24 cells, +321); worst 1m (5, -568), failed (6, -504), fade (8, -336)
  - PREOPEN: best T3 (7 cells, +883), s-3 (9 cells, +584), ST10 (7 cells, +521); worst s+0 (6, -885), 1m (5, -723), s+3 (9, -675)
  - NY-AM: best atr0.5 (9 cells, +952), s-3 (15 cells, +698), depth (14 cells, +670); worst time (5, -528), T3 (24, -413), VWAP (16, -364)
  - NY-PM: best 2m (6 cells, +486), fade (8 cells, +468), ST10 (32 cells, +435); worst PRIORDIR (20, -527), 3m (13, -515), KELT (12, -427)
  - NY: best atr0.5 (9 cells, +613), EMA1 (28 cells, +448), depth (14 cells, +430); worst PRIORDIR (20, -407), KELT (12, -404), time (5, -370)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 15 cell-sessions, 13521 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
