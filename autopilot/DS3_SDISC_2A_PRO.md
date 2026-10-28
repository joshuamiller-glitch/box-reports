# DS3_SDISC_2A_PRO - session-native re-search of the PRO family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **264** (T-PRO1, T-PRO2, T-PRO3); fixed 60/60 bracket (analytic MEASURED available): **264**; dynamic/other exits (stored basis only): 0. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 223 | 3 | 4 | 0 | 0 | 1 | 3 |
| LONDON | 208 | 3 | 4 | 0 | 0 | 0 | 4 |
| PREOPEN | 59 | 0 | 1 | 0 | 0 | 0 | 1 |
| NY-AM | 203 | 2 | 2 | 1 | 0 | 0 | 1 |
| NY-PM | 186 | 10 | 11 | 2 | 0 | 0 | 9 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| NY | 214 | 2 | 3 | 1 | 0 | 0 | 2 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 223)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_Z120_t1.5 | 60/60 | 567 | 7.6 | 1,060 | 99 | 2.20 | 1,351 | 700 | 190 | -353 | -587 | -1.51 | -196 | -991 | -546 | -859/1,307/-75/-991 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO_Z60_t1.5 | 60/60 | 666 | 8.9 | 918 | 80 | 2.18 | 1,178 | 571 | 2 | -540 | -770 | -2.44 | -520 | -606 | 383 | -464/700/247/-606 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO3A_A1 | 60/60 | 194 | 2.6 | 1,677 | 145 | 2.18 | 2,152 | 1,360 | 131 | -421 | -655 | -1.85 | 746 | -4,535 | -485 | -559/1,098/1,296/-4,535 | DEAD-IN-HOLD | HOLD mean<=0;H26<=0 | - | reread |
| PRO3B_OPEN1800_EMA1_T1 | 60/60 | 183 | 2.4 | 1,589 | -11 | 1.98 | 2,249 | 1,273 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3A_A1X25 | 60/60 | 152 | 2.0 | 1,588 | -99 | 1.88 | 2,371 | 1,259 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z20_t1.0 | 60/60 | 769 | 10.3 | 733 | -66 | 1.83 | 1,124 | 369 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_KAL_s0.5_k0.25 | 60/60 | 781 | 10.4 | 752 | -72 | 1.82 | 1,157 | 383 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_ABS_V15_ST10_EMA5 | 60/60 | 537 | 7.2 | 825 | -91 | 1.79 | 1,287 | 487 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_ABS_R10_EMA200_VWAP | 60/60 | 359 | 4.8 | 1,055 | -169 | 1.72 | 1,720 | 738 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z120_t1.0 | 60/60 | 586 | 7.8 | 750 | -145 | 1.67 | 1,258 | 388 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### LONDON (N screened 208)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO1_AGG_RL5_ST10_VWAP | 60/60 | 156 | 2.1 | 2,345 | 814 | 3.05 | 2,152 | 2,016 | -3,065 | -3,734 | -3,939 | -18.41 | -4,311 | -1,424 | -128 | -499/3,844/-1,902/-1,424 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO_ER4_EMA5 | 60/60 | 137 | 1.8 | 2,277 | 258 | 2.25 | 2,836 | 1,981 | 1,113 | 620 | 385 | +3.36 | 2,626 | -5,021 | 661 | 1,031/2,320/1,591/-5,021 | DEAD-IN-HOLD | H26<=0 | - | reread |
| PRO3A_A1P3 | 60/60 | 220 | 2.9 | 1,702 | 86 | 2.10 | 2,272 | 1,368 | -850 | -1,444 | -1,668 | -6.96 | -362 | -5,451 | 479 | 397/1,955/-254/-5,451 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO_Z120_t2.0 | 60/60 | 408 | 5.4 | 1,057 | -41 | 1.92 | 1,544 | 689 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_AGG_RL5_EMA200_VWAP | 60/60 | 127 | 1.7 | 1,827 | -121 | 1.87 | 2,738 | 1,506 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_LPC_Z16_EMA200_SWZ | 60/60 | 164 | 2.2 | 1,590 | -117 | 1.86 | 2,399 | 1,281 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_IMB_K3_EMA200_EMA5 | 60/60 | 391 | 5.2 | 925 | -90 | 1.82 | 1,427 | 584 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3A_VOL | 60/60 | 283 | 3.8 | 1,209 | -186 | 1.73 | 1,960 | 882 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_AGG_RL3_EMA200_SWZ | 60/60 | 370 | 4.9 | 845 | -286 | 1.49 | 1,590 | 503 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3A_R60 | 60/60 | 309 | 4.1 | 938 | -322 | 1.48 | 1,771 | 592 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 59)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_KAL_s0.5_k0.25 | 60/60 | 127 | 1.7 | 1,698 | -112 | 1.87 | 2,543 | 1,411 | 106 | -379 | -598 | -1.64 | -1,380 | 2,695 | -1,623 | -862/924/-155/2,695 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| PRO1_LPC_C50_ST10_SWZ | 60/60 | 118 | 1.6 | 1,698 | -121 | 1.86 | 2,555 | 1,396 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z20_t1.5 | 60/60 | 121 | 1.6 | 1,745 | -163 | 1.82 | 2,680 | 1,444 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_LPC_C50_EMA200_SWZ | 60/60 | 121 | 1.6 | 1,461 | -286 | 1.67 | 2,456 | 1,144 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z20_t1.0 | 60/60 | 138 | 1.8 | 760 | -608 | 1.11 | 1,922 | 447 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_IMB_K3_ST10_EMA5 | 60/60 | 105 | 1.4 | 1,141 | -1,020 | 1.05 | 3,037 | 821 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_KAL_s0.5_k0.5 | 60/60 | 133 | 1.8 | 974 | -952 | 1.01 | 2,706 | 640 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_KAL_k0.0 | 60/60 | 126 | 1.7 | 732 | -752 | 0.98 | 2,085 | 444 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z60_t1.5_ST10 | 60/60 | 122 | 1.6 | 1,050 | -1,119 | 0.96 | 3,048 | 769 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_AGG_CD2_ST10_EMA5 | 60/60 | 104 | 1.4 | 1,171 | -1,386 | 0.91 | 3,593 | 884 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 203)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO3B_OPEN0930_DRV38_T1 | 60/60 | 219 | 2.9 | 1,926 | 203 | 2.23 | 2,421 | 1,638 | 1,991 | 1,529 | 1,287 | +7.90 | 988 | 4,167 | -692 | -749/1,479/1,454/4,167 | SESSION-CANDIDATE | - | - | reread |
| PRO1_LPC_C100_EMA200_EMA5 | 60/60 | 480 | 6.4 | 1,020 | 25 | 2.04 | 1,399 | 687 | -707 | -1,265 | -1,485 | -6.06 | -1,582 | -174 | -865 | -379/949/-791/-174 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO3A_A1P3 | 60/60 | 122 | 1.6 | 2,014 | -17 | 1.98 | 2,855 | 1,708 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3B_OPEN0930_EMA1_T2 | 60/60 | 215 | 2.9 | 1,371 | -60 | 1.91 | 2,011 | 1,076 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_ST10_AVWAP_sw_T1 | 60/60 | 412 | 5.5 | 953 | -65 | 1.86 | 1,431 | 638 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_IMB_K3_EMA200_SWZ | 60/60 | 360 | 4.8 | 948 | -87 | 1.82 | 1,454 | 634 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z60_t2.0_ST10 | 60/60 | 417 | 5.6 | 980 | -91 | 1.82 | 1,505 | 674 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_ST10_CONF2_T2 | 60/60 | 401 | 5.3 | 946 | -112 | 1.78 | 1,487 | 637 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_KAL_k0.0 | 60/60 | 529 | 7.1 | 881 | -123 | 1.75 | 1,411 | 591 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_LPC_Z13_EMA200_EMA5 | 60/60 | 111 | 1.5 | 1,399 | -303 | 1.64 | 2,392 | 1,134 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 186)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO1_AGG_CD3_EMA200_VWAP | 60/60 | 125 | 1.7 | 2,435 | 529 | 2.55 | 2,678 | 2,216 | 259 | -154 | -336 | -0.51 | -2,092 | 5,384 | -44 | -154/1,044/909/5,384 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| PRO1_IMB_K3_EMA200_VWAP | 60/60 | 121 | 1.6 | 2,343 | 496 | 2.53 | 2,595 | 2,061 | 39 | -425 | -621 | -1.87 | -1,000 | 1,092 | -801 | -812/3,116/-750/1,092 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| PRO1_AGG_RL3_EMA200_VWAP | 60/60 | 134 | 1.8 | 2,073 | 337 | 2.38 | 2,439 | 1,782 | 1,221 | 856 | 668 | +4.54 | 97 | 3,274 | -2,216 | -1,620/1,612/831/3,274 | SESSION-CANDIDATE | - | - | reread |
| PRO1_LPC_C100_EMA200_VWAP | 60/60 | 100 | 1.3 | 2,504 | 385 | 2.35 | 2,977 | 2,251 | -877 | -1,366 | -1,543 | -6.57 | -1,783 | 602 | -1,821 | -1,933/904/572/602 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| PRO_ST10_AVWAP_flip_T1 | 60/60 | 169 | 2.3 | 1,972 | 275 | 2.31 | 2,386 | 1,720 | 2,121 | 1,754 | 1,548 | +9.03 | 2,500 | -1,079 | 172 | 54/795/3,185/-1,079 | DEAD-IN-HOLD | H26<=0 | - | reread |
| PRO1_SWR_M10_N60_EMA200_EMA5 | 60/60 | 237 | 3.2 | 1,282 | 154 | 2.27 | 1,585 | 1,010 | -102 | -503 | -676 | -2.26 | -357 | -1,240 | -952 | -848/1,143/-62/-1,240 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| PRO_ST10_AVWAP_flip_T2 | 60/60 | 165 | 2.2 | 1,655 | 191 | 2.25 | 2,057 | 1,417 | 1,538 | 1,149 | 949 | +6.00 | 1,239 | 643 | -300 | -432/693/1,936/643 | SESSION-CANDIDATE | - | - | reread |
| PRO1_IMB_K3_ST10_VWAP | 60/60 | 124 | 1.7 | 1,955 | 174 | 2.19 | 2,503 | 1,643 | 1,071 | 710 | 513 | +3.81 | -720 | 7,144 | -3,445 | -1,834/2,502/-776/7,144 | DEAD-IN-HOLD | H25<=0 | - | reread |
| PRO1_LPC_C100_ST10_VWAP | 60/60 | 119 | 1.6 | 1,900 | 73 | 2.07 | 2,567 | 1,612 | -972 | -1,492 | -1,687 | -7.20 | -3,197 | 5,516 | -897 | -756/1,358/-942/5,516 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| PRO_Z60_t1.0_ST10 | 60/60 | 263 | 3.5 | 966 | 14 | 2.02 | 1,339 | 680 | -564 | -968 | -1,134 | -4.58 | -1,029 | -479 | 391 | -538/758/248/-479 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |

### CLOSE: no cell with PRE n >= 100

### NY (N screened 214)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO3B_OPEN0930_DRV38_T1 | 60/60 | 219 | 2.9 | 1,926 | 203 | 2.23 | 2,421 | 1,638 | 1,991 | 1,529 | 1,287 | +7.90 | 988 | 4,167 | -692 | -749/1,479/1,454/4,167 | SESSION-CANDIDATE | - | - |  |
| PRO3B_XA_pull_EMA1 | 60/60 | 608 | 8.1 | 978 | 103 | 2.23 | 1,229 | 680 | 1,168 | 765 | 559 | +4.08 | 1,166 | -888 | 831 | 692/1,132/336/-888 | DEAD-IN-HOLD | H26<=0 | - |  |
| PRO1_LPC_C100_EMA200_EMA5 | 60/60 | 726 | 9.7 | 831 | -4 | 1.98 | 1,172 | 512 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3B_OPEN0930_EMA1_T2 | 60/60 | 215 | 2.9 | 1,371 | -60 | 1.91 | 2,011 | 1,076 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_ABS_R10_EMA200_EMA5 | 60/60 | 327 | 4.4 | 1,141 | -55 | 1.90 | 1,682 | 841 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_KAL_k0.0 | 60/60 | 741 | 9.9 | 746 | -69 | 1.82 | 1,145 | 466 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO3A_VOL | 60/60 | 360 | 4.8 | 913 | -123 | 1.76 | 1,456 | 633 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_ST10_IMP62_T1 | 60/60 | 546 | 7.3 | 804 | -123 | 1.73 | 1,302 | 496 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO1_AGG_RL5_EMA200_EMA5 | 60/60 | 486 | 6.5 | 780 | -150 | 1.67 | 1,307 | 457 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| PRO_Z60_t1.0 | 60/60 | 789 | 10.5 | 561 | -169 | 1.53 | 1,026 | 252 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

| session | cell | brk | PRE n | PRE $ stored | PRE $ MEAS | HOLD $ (MEAS if fixed) | HOLD pts | HOLD MDE $ | H25 $ | H26 $ | X 2023 $ | HOLD CONS $ | tier | pooled PRE $ | index verdict | HOLD look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NY-AM | PRO3B_OPEN0930_DRV38_T1 | 60/60 | 219 | 1,926 | 1,638 | 1,529 | +7.90 | 3,537 | 988 | 4,167 | -692 | 1,287 | SESSION-CANDIDATE | 1,926 | DEAD | reread |
| NY-PM | PRO_ST10_AVWAP_flip_T2 | 60/60 | 165 | 1,655 | 1,417 | 1,149 | +6.00 | 3,700 | 1,239 | 643 | -300 | 949 | SESSION-CANDIDATE | 178 | DEAD | reread |
| NY-PM | PRO1_AGG_RL3_EMA200_VWAP | 60/60 | 134 | 2,073 | 1,782 | 856 | +4.54 | 4,077 | 97 | 3,274 | -2,216 | 668 | SESSION-CANDIDATE | 180 | DEAD | reread |
| NY | PRO3B_OPEN0930_DRV38_T1 | 60/60 | 219 | 1,926 | 1,638 | 1,529 | +7.90 | 3,537 | 988 | 4,167 | -692 | 1,287 | SESSION-CANDIDATE | 1,926 | DEAD | first |

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median -0.06 over 10 session pairs; ASIA vs NY-AM [-0.03], ASIA vs LONDON [-0.04], NY-AM vs NY-PM [-0.29]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| ASIA | s | PRO_Z120_t1.5 | PRO_ER4_n40_EMA5 | 263 | 43 | -2,189 | [-12,530, 8,153] | 14,198 |  |
| ASIA | m | PRO_Z120_t1.5 | PRO_ER4_n40_EMA5 | 263 | 43 | -6,068 | [-16,984, 4,848] | 14,987 |  |
| LONDON | s | PRO1_AGG_RL5_ST10_VWAP | PRO_ER4_n40_EMA5 | 55 | 19 | -4,352 | [-10,466, 1,762] | 8,394 |  |
| LONDON | m | PRO1_AGG_RL5_ST10_VWAP | PRO_ER4_n40_EMA5 | 55 | 19 | -5,146 | [-11,527, 1,235] | 8,760 |  |
| NY-PM | s | PRO1_AGG_CD3_EMA200_VWAP | PRO_ER4_n40_EMA5 | 54 | 21 | -1,549 | [-7,477, 4,378] | 8,138 |  |
| NY-PM | m | PRO1_AGG_CD3_EMA200_VWAP | PRO_ER4_n40_EMA5 | 54 | 21 | -2,050 | [-8,175, 4,075] | 8,409 |  |
| NY | s | PRO3B_OPEN0930_DRV38_T1 | PRO_ER4_n40_EMA5 | 100 | 33 | 5,528 | [-2,983, 14,039] | 11,684 |  |
| NY | m | PRO3B_OPEN0930_DRV38_T1 | PRO_ER4_n40_EMA5 | 100 | 33 | 4,525 | [-4,390, 13,441] | 12,240 |  |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best R12 (6 cells, +549), ABS (24 cells, +394), R10 (6 cells, +388); worst Z16 (6, -554), LPC (18, -438), C50 (6, -346)
  - LONDON: best RL5 (6 cells, +885), PRO3A (19 cells, +703), SWZ (34 cells, +417); worst KAL (13, -720), dPOC (5, -652), PRO3B (6, -601)
  - PREOPEN: best EMA5 (6 cells, +660), PRO1 (16 cells, +507), ST10 (19 cells, +496); worst RIB1m (5, -1249), t1.0 (6, -493), PRO (42, -420)
  - NY-AM: best PRO3B (7 cells, +751), T2 (5 cells, +565), KAL (13 cells, +444); worst N60 (6, -771), SWR (12, -761), N120 (6, -704)
  - NY-PM: best VWAP (23 cells, +1073), flip (6 cells, +917), C100 (6 cells, +837); worst KAL (13, -605), PRO3A (17, -585), dPOC (5, -428)
  - NY: best PRO3B (10 cells, +473), Z13 (6 cells, +391), C100 (6 cells, +364); worst N120 (6, -423), SWR (12, -413), N60 (6, -380)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 5 cell-sessions, 1653 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
