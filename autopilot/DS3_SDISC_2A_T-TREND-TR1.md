# DS3_SDISC_2A_T-TREND-TR1 - session-native re-search of the T-TREND-TR1 family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **133** (T-TREND TR1); fixed 60/60 bracket (analytic MEASURED available): **132**; dynamic/other exits (stored basis only): 1. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 128 | 9 | 9 | 1 | 0 | 1 | 7 |
| LONDON | 127 | 2 | 3 | 1 | 0 | 0 | 2 |
| PREOPEN | 48 | 0 | 2 | 1 | 0 | 0 | 1 |
| NY-AM | 124 | 5 | 5 | 0 | 0 | 2 | 3 |
| NY-PM | 119 | 0 | 2 | 0 | 0 | 0 | 2 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| NY | 130 | 2 | 3 | 1 | 0 | 0 | 2 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 128)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1E_bos_15m_c2 | 60/60 | 251 | 3.3 | 1,835 | 382 | 2.52 | 2,041 | 1,508 | 246 | -298 | -533 | -1.23 | -576 | 1,027 | 166 | -603/1,939/251/1,027 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1E_bos_1m_c3 | 60/60 | 643 | 8.6 | 1,051 | 200 | 2.46 | 1,196 | 700 | -113 | -663 | -894 | -3.06 | -1,037 | 552 | -1,383 | -1,268/437/5/552 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1E_bos_1m_c2 | 60/60 | 670 | 8.9 | 874 | 125 | 2.32 | 1,053 | 520 | 973 | 463 | 225 | +2.57 | 213 | 1,153 | -1,366 | -1,223/-54/818/1,153 | SESSION-CANDIDATE | - | - | reread |
| TR1B_reg1m_n60_t2_r0.5 | 60/60 | 633 | 8.4 | 999 | 135 | 2.30 | 1,214 | 637 | -819 | -1,407 | -1,634 | -6.77 | -2,153 | 1,396 | -729 | -698/853/-901/1,396 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1B_reg1m_n60_t3_r0.5 | 60/60 | 633 | 8.4 | 999 | 135 | 2.30 | 1,214 | 637 | -819 | -1,407 | -1,634 | -6.77 | -2,153 | 1,396 | -729 | -698/853/-901/1,396 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1A_ens_s1.0_k3 | 60/60 | 607 | 8.1 | 1,029 | 112 | 2.24 | 1,287 | 688 | 541 | 20 | -215 | +0.36 | -129 | 553 | -159 | -665/317/637/553 | MEASURED-FAIL | H25<=0 | - | reread |
| TR1A_ens_s0.5_k4 | 60/60 | 640 | 8.5 | 928 | 82 | 2.19 | 1,188 | 585 | -320 | -874 | -1,102 | -4.11 | -987 | -507 | -312 | -365/296/123/-507 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| TR1E_bos_15m_c3 | 60/60 | 187 | 2.5 | 1,737 | 90 | 2.10 | 2,315 | 1,419 | -114 | -675 | -908 | -3.12 | -1,121 | 1,202 | -237 | -367/1,232/306/1,202 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1A_vnr_120m_s0.5 | 60/60 | 535 | 7.1 | 935 | 47 | 2.10 | 1,247 | 570 | -453 | -1,032 | -1,263 | -4.90 | -1,365 | 374 | 177 | -191/1,153/-788/374 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1A_ens_s1.5_k3 | 60/60 | 467 | 6.2 | 1,004 | -87 | 1.83 | 1,534 | 668 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### LONDON (N screened 127)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1C_HP_5m_flip | 60/60 | 448 | 6.0 | 1,474 | 458 | 2.89 | 1,428 | 1,162 | -232 | -770 | -995 | -3.59 | -1,259 | 1,082 | -117 | 255/365/526/1,082 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - | reread |
| TR1D_KALMAN_1m_slope | 60/60 | 436 | 5.8 | 1,141 | 143 | 2.28 | 1,403 | 790 | -1,632 | -2,248 | -2,467 | -10.98 | -2,679 | -794 | -1,281 | -815/294/-449/-794 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| TR1B_reg1m_n60_t2_r0.5 | 60/60 | 403 | 5.4 | 994 | -65 | 1.87 | 1,489 | 651 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1B_reg1m_n60_t3_r0.5 | 60/60 | 403 | 5.4 | 994 | -65 | 1.87 | 1,489 | 651 | 1,703 | 1,257 | 1,023 | +6.54 | 783 | 2,541 | 490 | 686/844/412/2,541 | SESSION-CANDIDATE | - | - |  |
| TR1C_KALMAN_5m_flip | 60/60 | 424 | 5.7 | 904 | -93 | 1.81 | 1,400 | 584 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_30m_s0.5 | 60/60 | 413 | 5.5 | 1,064 | -158 | 1.73 | 1,718 | 731 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_60m_s0.5 | 60/60 | 394 | 5.3 | 917 | -143 | 1.72 | 1,489 | 554 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_JURIK_3m_flip | 60/60 | 431 | 5.7 | 841 | -244 | 1.54 | 1,525 | 490 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_KALMAN_1m_flip | 60/60 | 512 | 6.8 | 719 | -217 | 1.53 | 1,315 | 366 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_120m_s0.5 | 60/60 | 333 | 4.4 | 800 | -303 | 1.44 | 1,550 | 418 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 48)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1A_vnr_30m_s0.5 | 60/60 | 122 | 1.6 | 1,842 | -271 | 1.74 | 2,970 | 1,548 | 1,494 | 1,023 | 783 | +5.37 | 937 | 1,694 | 4,772 | 2,938/2,001/1,082/1,694 | SESSION-CANDIDATE | - | - |  |
| TR1C_MAMA_1m_flip | 60/60 | 128 | 1.7 | 1,466 | -292 | 1.66 | 2,471 | 1,142 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_MAMA_3m_slope | 60/60 | 137 | 1.8 | 1,262 | -413 | 1.50 | 2,353 | 938 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_HP_1m_slope | 60/60 | 134 | 1.8 | 1,316 | -466 | 1.47 | 2,505 | 1,001 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_KALMAN_1m_slope | 60/60 | 133 | 1.8 | 995 | -978 | 1.00 | 2,771 | 649 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_HP_3m_flip | 60/60 | 149 | 2.0 | 737 | -828 | 0.94 | 2,199 | 406 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_60m_s0.5 | 60/60 | 106 | 1.4 | 600 | -1,567 | 0.55 | 3,044 | 250 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_15m_s1.0 | 60/60 | 138 | 1.8 | 418 | -1,460 | 0.44 | 2,639 | 71 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_JURIK_1m_slope | 60/60 | 142 | 1.9 | 441 | -1,562 | 0.44 | 2,814 | 107 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1E_choch_1m_c3 | 60/60 | 107 | 1.4 | 434 | -1,595 | 0.43 | 2,851 | 86 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 124)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1D_HP_10m_slope | 60/60 | 210 | 2.8 | 1,946 | 578 | 2.84 | 1,922 | 1,663 | 1,150 | 665 | 437 | +3.59 | 1,583 | -4,411 | -147 | 285/1,333/1,476/-4,411 | DEAD-IN-HOLD | H26<=0 | - | reread |
| TR1A_ens_s0.5_k4 | 60/60 | 522 | 7.0 | 1,383 | 381 | 2.75 | 1,408 | 1,078 | 393 | -85 | -301 | -0.17 | -328 | 980 | -1,659 | -1,542/1,223/-72/980 | MEASURED-FAIL | HOLD mean<=0;H25<=0 | - | reread |
| TR1B_reg5m_n20_t3_r0.5 | 60/60 | 292 | 3.9 | 1,426 | 382 | 2.72 | 1,466 | 1,090 |  |  |  |  |  |  |  |  | not selected | cluster/top10 cap | - |  |
| TR1B_reg5m_n20_t2_r0.5 | 60/60 | 292 | 3.9 | 1,426 | 382 | 2.72 | 1,466 | 1,090 | 167 | -310 | -521 | -1.29 | -348 | -66 | 914 | 762/1,557/-15/-66 | MEASURED-FAIL | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| TR1B_reg5m_n20_t3_r0.0 | 60/60 | 266 | 3.5 | 1,405 | 71 | 2.10 | 1,876 | 1,112 | 307 | -188 | -408 | -0.68 | 76 | -2,369 | -520 | -770/448/825/-2,369 | DEAD-IN-HOLD | HOLD mean<=0;H26<=0 | - | reread |
| TR1A_ens_s1.5_k4 | 60/60 | 214 | 2.9 | 1,426 | -40 | 1.94 | 2,060 | 1,107 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_HP_5m_slope | 60/60 | 279 | 3.7 | 1,111 | -94 | 1.84 | 1,693 | 799 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1E_choch_15m_c3 | 60/60 | 107 | 1.4 | 1,995 | -220 | 1.79 | 3,113 | 1,732 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_MAMA_1m_flip | 60/60 | 481 | 6.4 | 830 | -105 | 1.77 | 1,314 | 526 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1B_reg5m_n20_t2_r0.7 | 60/60 | 253 | 3.4 | 1,135 | -169 | 1.73 | 1,833 | 822 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 119)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1D_MAMA_10m_slope | 60/60 | 220 | 2.9 | 1,123 | -368 | 1.50 | 2,095 | 860 | -1,071 | -1,537 | -1,696 | -7.43 | -1,670 | -631 | -843 | -690/-238/39/-631 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| TR1A_ens_s1.5_k3 | 60/60 | 215 | 2.9 | 847 | -629 | 1.14 | 2,074 | 576 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_240m_s1.0 | 60/60 | 127 | 1.7 | 1,031 | -841 | 1.10 | 2,631 | 745 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_MAMA_5m_flip | 60/60 | 204 | 2.7 | 898 | -767 | 1.07 | 2,340 | 612 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_60m_s0.5 | 60/60 | 257 | 3.4 | 723 | -654 | 1.05 | 1,935 | 456 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_ens_s1.0_k3 | 60/60 | 254 | 3.4 | 543 | -607 | 0.94 | 1,616 | 236 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1F_vote_ST_k3 | 60/60 | 134 | 1.8 | 858 | -1,001 | 0.92 | 2,613 | 530 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_JURIK_3m_slope | 60/60 | 276 | 3.7 | 479 | -588 | 0.89 | 1,499 | 193 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1A_vnr_60m_s1.0 | 60/60 | 262 | 3.5 | 601 | -739 | 0.89 | 1,883 | 325 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1E_choch_3m_c3 | 60/60 | 206 | 2.7 | 666 | -862 | 0.87 | 2,147 | 364 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### CLOSE: no cell with PRE n >= 100

### NY (N screened 130)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1A_ens_s0.5_k4 | 60/60 | 811 | 10.8 | 796 | 36 | 2.09 | 1,067 | 486 | 202 | -246 | -448 | -0.97 | -510 | 885 | -771 | -857/956/-571/885 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| TR1A_ens_s1.5_k4 | 60/60 | 365 | 4.9 | 1,130 | 45 | 2.08 | 1,524 | 822 | 1,185 | 755 | 541 | +4.03 | 858 | 368 | 571 | 668/894/661/368 | SESSION-CANDIDATE | - | - |  |
| TR1D_MAMA_10m_slope | 60/60 | 569 | 7.6 | 798 | -33 | 1.91 | 1,169 | 497 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_HP_10m_slope | 60/60 | 395 | 5.3 | 877 | -183 | 1.65 | 1,488 | 575 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_HP_5m_slope | 60/60 | 533 | 7.1 | 621 | -188 | 1.53 | 1,137 | 310 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_KALMAN_5m_slope | 60/60 | 509 | 6.8 | 681 | -215 | 1.51 | 1,259 | 357 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1E_retest_5m_c2 | 60/60 | 258 | 3.4 | 892 | -321 | 1.47 | 1,704 | 600 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_MAMA_5m_flip | 60/60 | 476 | 6.3 | 770 | -279 | 1.46 | 1,474 | 478 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1D_JURIK_3m_slope | 60/60 | 743 | 9.9 | 607 | -231 | 1.44 | 1,177 | 299 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| TR1C_MAMA_1m_flip | 60/60 | 746 | 9.9 | 533 | -229 | 1.39 | 1,070 | 226 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

| session | cell | brk | PRE n | PRE $ stored | PRE $ MEAS | HOLD $ (MEAS if fixed) | HOLD pts | HOLD MDE $ | H25 $ | H26 $ | X 2023 $ | HOLD CONS $ | tier | pooled PRE $ | index verdict | HOLD look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ASIA | TR1E_bos_1m_c2 | 60/60 | 670 | 874 | 520 | 463 | +2.57 | 1,505 | 213 | 1,153 | -1,366 | 225 | SESSION-CANDIDATE | 284 | DEAD | reread |
| LONDON | TR1B_reg1m_n60_t3_r0.5 | 60/60 | 403 | 994 | 651 | 1,257 | +6.54 | 2,216 | 783 | 2,541 | 490 | 1,023 | SESSION-CANDIDATE | 716 | CANDIDATE | first |
| PREOPEN | TR1A_vnr_30m_s0.5 | 60/60 | 122 | 1,842 | 1,548 | 1,023 | +5.37 | 5,002 | 937 | 1,694 | 4,772 | 783 | SESSION-CANDIDATE | 55 | DEAD | first |
| NY | TR1A_ens_s1.5_k4 | 60/60 | 365 | 1,130 | 822 | 755 | +4.03 | 2,105 | 858 | 368 | 571 | 541 | SESSION-CANDIDATE | 345 | DEAD | first |

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median +0.10 over 10 session pairs; ASIA vs NY-AM [0.27], ASIA vs LONDON [-0.1], NY-AM vs NY-PM [0.07]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| ASIA | s | TR1E_bos_15m_c2 | TR1B_reg1m_n60_t3_r0.5 | 121 | 309 | 8,840 | [-3,682, 21,363] | 17,192 |  |
| ASIA | m | TR1E_bos_15m_c2 | TR1B_reg1m_n60_t3_r0.5 | 121 | 309 | 12,455 | [-774, 25,684] | 18,162 |  |
| LONDON | s | TR1C_HP_5m_flip | TR1B_reg1m_n60_t3_r0.5 | 201 | 167 | -10,342 | [-21,867, 1,183] | 15,823 |  |
| LONDON | m | TR1C_HP_5m_flip | TR1B_reg1m_n60_t3_r0.5 | 201 | 167 | -11,392 | [-23,315, 531] | 16,369 |  |
| PREOPEN | s | TR1A_vnr_30m_s0.5 | TR1B_reg1m_n60_t3_r0.5 | 44 | 37 | 2,221 | [-4,093, 8,535] | 8,668 |  |
| PREOPEN | m | TR1A_vnr_30m_s0.5 | TR1B_reg1m_n60_t3_r0.5 | 44 | 37 | 2,179 | [-4,380, 8,739] | 9,006 |  |
| NY-AM | s | TR1D_HP_10m_slope | TR1B_reg1m_n60_t3_r0.5 | 98 | 175 | 5,761 | [-3,762, 15,284] | 13,074 |  |
| NY-AM | m | TR1D_HP_10m_slope | TR1B_reg1m_n60_t3_r0.5 | 98 | 175 | 6,955 | [-2,805, 16,715] | 13,399 |  |
| NY-PM | s | TR1D_MAMA_10m_slope | TR1B_reg1m_n60_t3_r0.5 | 109 | 103 | 474 | [-9,431, 10,378] | 13,598 |  |
| NY-PM | m | TR1D_MAMA_10m_slope | TR1B_reg1m_n60_t3_r0.5 | 109 | 103 | 431 | [-9,856, 10,719] | 14,124 |  |
| NY | s | TR1A_ens_s0.5_k4 | TR1B_reg1m_n60_t3_r0.5 | 311 | 278 | 8,327 | [-8,112, 24,767] | 22,569 |  |
| NY | m | TR1A_ens_s0.5_k4 | TR1B_reg1m_n60_t3_r0.5 | 311 | 278 | 8,196 | [-8,984, 25,376] | 23,586 |  |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best ens (6 cells, +845), k3 (7 cells, +757), bos (8 cells, +707); worst JURIK (8, -762), FRAMA (8, -667), 3m (18, -652)
  - LONDON: best s0.5 (7 cells, +448), HP (8 cells, +393), KALMAN (8 cells, +385); worst s1.5 (7, -795), r0.7 (6, -649), reg5m (18, -590)
  - PREOPEN: best HP (5 cells, +572), s0.5 (5 cells, +536), vnr (6 cells, +437); worst KAMA (6, -1196), FRAMA (7, -998), 5m (7, -461)
  - NY-AM: best r0.5 (6 cells, +835), n20 (6 cells, +816), t3 (8 cells, +545); worst FRAMA (8, -537), KAMA (8, -480), s1.0 (8, -446)
  - NY-PM: best ens (6 cells, +634), k3 (7 cells, +593), s1.0 (8 cells, +556); worst 1m (18, -425), bos (7, -363), FRAMA (8, -349)
  - NY: best r0.7 (6 cells, +390), ens (6 cells, +355), n20 (6 cells, +353); worst FRAMA (8, -433), KAMA (8, -377), 1m (18, -312)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 7 cell-sessions, 5427 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
