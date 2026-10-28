# DS3_SDISC_2A_Footprint - session-native re-search of the Footprint family (D3SD2A, T-SESSION-DISCOVER item 2)

Written 2026-10-28 20:59Z. Research only; no live, execution-server or chart change; UNTOUCHED (after 2026-02-06) never read; no account ids. Prereg l2vast/ds3/prereg/SDISC_2A_prereg.md sha256 a6f9dc264a01670083a663b938d7abcdcb1c8e434e64684ff49d9499b3d655d5; PREHOLD autopilot/DS3_SDISC_2A_PREHOLD.md sha256 a714f336948e9a545b6ca6d20a4feacf1f262e309298a998982d7d203e3c1eb9 (hashed before HOLD/X were read; one HOLD and one X look per cell-session logged in out/sd2a/looks.jsonl; first run's MEASURED recipe had a stop-classification bug, fixed, same list, see DECISIONS.md). Code l2vast/ds3/code/sd2a/, outputs l2vast/ds3/out/sd2a/.

## 1. Grid, rows, regeneration
- Cells with trade rows: **169** (Footprint FP); fixed 60/60 bracket (analytic MEASURED available): **103**; dynamic/other exits (stored basis only): 66. Rows: out/ss2/trades_all.parquet (cid), index out/ss2/ledger_index.parquet.
- **Grid used: the STORED grid, rows reused. No regeneration with an extended parameter grid** (the family engines are mapped bar/tick-bar simulations; a re-run is neither cheap nor verified bit-identical in this program, and a per-session extended grid on top of an unverified engine would put an unvalidated basis next to the stored one). The per-session choice is made among the stored cells, which already vary every parameter axis the family has (see the token table in section 5).

## 2. Screen and selection (PRE 2024-02..2025-06, stored basis; week-cluster CI)

| session | screened N (PRE n>=100) | stored-selected (mean>0, CI lo>0) | in PREHOLD list | SESSION-CAND/PASS (MEASURED) | STORED-CAND (MEASURED n/a) | MEASURED-FAIL | DEAD-IN-HOLD |
|---|---|---|---|---|---|---|---|
| ASIA | 119 | 0 | 2 | 0 | 0 | 1 | 1 |
| LONDON | 128 | 0 | 1 | 0 | 0 | 0 | 1 |
| PREOPEN | 69 | 0 | 1 | 0 | 0 | 0 | 1 |
| NY-AM | 133 | 0 | 2 | 0 | 0 | 0 | 2 |
| NY-PM | 119 | 3 | 4 | 0 | 0 | 0 | 4 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| NY | 145 | 0 | 2 | 0 | 0 | 0 | 2 |

## 3. Top 10 per session by PRE t, regardless of verdict (stored / MEASURED / CONSERVATIVE; $ = stored 10-lot unit; MEASURED pts net of 0.242 shown for HOLD)

Cells outside the PREHOLD list (PRE CI not > 0 and not a winner) have no HOLD read by design: HOLD columns blank, failed gate = not selected. MDE = 2.8 x week-cluster SE per trade ($). X = 2023-04..2024-01 span. Year columns are MEASURED where fixed else stored.

### ASIA (N screened 119)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_CDnop_t500_N_K60 | 60/60 | 473 | 6.3 | 646 | -326 | 1.32 | 1,366 | 493 | 948 | 804 | 565 | +4.28 | 1,039 | -8 | -1,373 | -1,960/683/616/-8 | MEASURED-FAIL | H26<=0 | - |  |
| FP_CDall_t500_N_KS | dyn | 703 | 9.4 | 301 | -280 | 1.03 | 816 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI44_1m_T_K60 | 60/60 | 413 | 5.5 | 571 | -544 | 1.02 | 1,567 | 408 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAfade_t500_N_K60 | 60/60 | 146 | 1.9 | 914 | -990 | 0.96 | 2,676 | 765 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_5m_TS_K60 | 60/60 | 110 | 1.5 | 1,050 | -1,329 | 0.88 | 3,342 | 903 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDwithp_1m_N_K60 | 60/60 | 645 | 8.6 | 319 | -586 | 0.70 | 1,271 | 167 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t500_TZ_KS | dyn | 155 | 2.1 | 225 | -467 | 0.65 | 973 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_DDdvx60_cd_3m_N_K60 | 60/60 | 361 | 4.8 | 419 | -945 | 0.61 | 1,916 | 265 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDall_1m_N_K60 | 60/60 | 703 | 9.4 | 261 | -605 | 0.60 | 1,216 | 102 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDall_t1000_N_KS | dyn | 306 | 4.1 | 301 | -730 | 0.58 | 1,449 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### LONDON (N screened 128)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_UAfade_5m_Z_K60 | 60/60 | 113 | 1.5 | 1,677 | -435 | 1.58 | 2,968 | 1,537 | -2,910 | -3,094 | -3,315 | -15.21 | -4,283 | 3,251 | -2,114 | -2,297/1,433/-910/3,251 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| FP_CDpbos_3m_N_K60 | 60/60 | 381 | 5.1 | 1,060 | -287 | 1.57 | 1,892 | 905 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDwithp_t500_N_K60 | 60/60 | 278 | 3.7 | 814 | -319 | 1.43 | 1,593 | 667 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_ABloose_3m_N_K60 | 60/60 | 163 | 2.2 | 1,172 | -871 | 1.14 | 2,871 | 1,028 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_3m_TS_KS | dyn | 171 | 2.3 | 430 | -530 | 0.89 | 1,348 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_ABloose_3m_N_KS | dyn | 192 | 2.6 | 305 | -454 | 0.80 | 1,068 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t500_TS_KS | dyn | 186 | 2.5 | 335 | -593 | 0.72 | 1,305 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t1000_T_KS | dyn | 676 | 9.0 | 206 | -387 | 0.69 | 833 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDnop_t1000_N_K60 | 60/60 | 419 | 5.6 | 405 | -785 | 0.68 | 1,671 | 251 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDnop_5m_N_K60 | 60/60 | 343 | 4.6 | 406 | -848 | 0.65 | 1,762 | 249 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### PREOPEN (N screened 69)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_CDpbos_t500_N_K60 | 60/60 | 132 | 1.8 | 1,891 | -111 | 1.88 | 2,813 | 1,752 | -583 | -734 | -955 | -3.41 | -864 | -322 | -159 | 7/2,244/-422/-322 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| FP_CDnop_t500_N_K60 | 60/60 | 150 | 2.0 | 1,506 | -112 | 1.85 | 2,273 | 1,365 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t500_T_K60 | 60/60 | 119 | 1.6 | 1,571 | -459 | 1.54 | 2,852 | 1,393 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t500_TS_KS | dyn | 150 | 2.0 | 827 | -278 | 1.49 | 1,553 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_DDdvx60_bar_1m_N_K60 | 60/60 | 102 | 1.4 | 1,536 | -641 | 1.41 | 3,060 | 1,374 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDnop_1m_N_K60 | dyn | 106 | 1.4 | 1,578 | -728 | 1.36 | 3,240 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDnop_t1000_N_K60 | 60/60 | 151 | 2.0 | 1,052 | -606 | 1.26 | 2,331 | 895 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t1000_T_K60 | 60/60 | 143 | 1.9 | 872 | -835 | 1.02 | 2,399 | 718 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDall_1m_N_K60 | 60/60 | 121 | 1.6 | 1,008 | -1,103 | 0.95 | 2,966 | 873 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDall_t500_N_K60 | 60/60 | 134 | 1.8 | 1,000 | -1,146 | 0.93 | 3,017 | 863 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-AM (N screened 133)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_CDpbos_1m_N_K60 | 60/60 | 454 | 6.1 | 871 | -120 | 1.75 | 1,393 | 738 | -673 | -824 | -1,029 | -3.86 | -766 | -1,113 | -2,318 | -2,215/1,099/-571/-1,113 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| FP_UAcont_3m_N_KS | dyn | 213 | 2.8 | 1,114 | -262 | 1.61 | 1,934 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAcont_5m_N_K60 | dyn | 172 | 2.3 | 1,523 | -401 | 1.58 | 2,704 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_DDdvs_bar_3m_N_KS | dyn | 586 | 7.8 | 427 | -135 | 1.51 | 790 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_1m_N_K60 | 60/60 | 450 | 6.0 | 687 | -303 | 1.38 | 1,391 | 538 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDall_3m_N_KS | dyn | 612 | 8.2 | 468 | -226 | 1.34 | 975 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAcont_5m_T_K60 | dyn | 143 | 1.9 | 1,317 | -681 | 1.31 | 2,808 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAcont_3m_N_K60 | dyn | 228 | 3.0 | 959 | -620 | 1.21 | 2,219 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDwithp_t1000_N_K60 | 60/60 | 599 | 8.0 | 526 | -365 | 1.18 | 1,251 | 372 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDnop_5m_N_K60 | 60/60 | 292 | 3.9 | 869 | -609 | 1.17 | 2,077 | 705 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### NY-PM (N screened 119)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_DDdvx60_cd_5m_N_K60 | 60/60 | 137 | 1.8 | 2,161 | 436 | 2.50 | 2,425 | 2,011 | -1,627 | -1,762 | -1,934 | -8.55 | -1,516 | -2,848 | 128 | 1,469/1,202/175/-2,848 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| FP_SI33_1m_T_K60 | 60/60 | 141 | 1.9 | 1,788 | 109 | 2.12 | 2,358 | 1,683 | -333 | -479 | -641 | -2.14 | -209 | -4,535 | -672 | -33/1,250/474/-4,535 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| FP_SI33_t500_T_K60 | 60/60 | 119 | 1.6 | 1,974 | 118 | 2.12 | 2,608 | 1,870 | -968 | -1,089 | -1,245 | -5.19 | -4 | -8,505 | -1,298 | -1,183/2,074/-231/-8,505 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - | reread |
| FP_DDdvs_cd_t1000_N_K60 | 60/60 | 230 | 3.1 | 802 | -570 | 1.16 | 1,928 | 642 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAcont_1m_N_KS | dyn | 624 | 8.3 | 306 | -237 | 1.12 | 763 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_5m_T_K60 | 60/60 | 150 | 2.0 | 797 | -630 | 1.11 | 2,006 | 666 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_1m_N_KS | dyn | 775 | 10.3 | 222 | -188 | 1.08 | 576 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_3m_T_K60 | 60/60 | 140 | 1.9 | 974 | -851 | 1.06 | 2,564 | 838 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_t500_T_KS | dyn | 1179 | 15.7 | 134 | -122 | 1.04 | 361 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_DDdvs_cd_1m_N_K60 | 60/60 | 177 | 2.4 | 776 | -784 | 0.99 | 2,192 | 635 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

### CLOSE: no cell with PRE n >= 100

### NY (N screened 145)

| cell | brk | PRE n | tpw | PRE $ stored | CI lo | t | MDE $ | PRE $ MEAS | HOLD $ stored | HOLD $ MEAS | HOLD $ CONS | HOLD MEAS pts | H25 $ | H26 $ | X (2023) $ | 2023/24/25/26 $ | tier | failed gate | BOF | look |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FP_SI33_1m_N_K60 | 60/60 | 602 | 8.0 | 714 | -120 | 1.70 | 1,172 | 569 | -1,402 | -1,549 | -1,743 | -7.48 | -1,647 | -699 | 401 | 13/735/-971/-699 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0;H26<=0 | - |  |
| FP_DDdvs_bar_3m_N_KS | dyn | 1200 | 16.0 | 302 | -65 | 1.64 | 516 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_5m_T_K60 | 60/60 | 504 | 6.7 | 637 | -276 | 1.39 | 1,282 | 487 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_SI33_1m_N_KS | dyn | 2182 | 29.1 | 170 | -86 | 1.32 | 360 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAcont_1m_N_KS | dyn | 1392 | 18.6 | 230 | -121 | 1.31 | 492 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_IRini_1m_N_KS | dyn | 154 | 2.1 | 654 | -585 | 1.05 | 1,741 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_UAfade_5m_Z_K60 | 60/60 | 132 | 1.8 | 968 | -871 | 1.05 | 2,585 | 828 | -1,243 | -1,438 | -1,624 | -6.93 | -3,139 | 11,037 | 646 | 362/390/-1,137/11,037 | DEAD-IN-HOLD | HOLD mean<=0;H25<=0 | - |  |
| FP_ABloose_1m_N_KS | dyn | 175 | 2.3 | 489 | -441 | 1.05 | 1,307 |  |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_CDpbos_t1000_N_K60 | 60/60 | 722 | 9.6 | 402 | -511 | 0.88 | 1,282 | 264 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |
| FP_IRini_t500_N_K60 | 60/60 | 156 | 2.1 | 773 | -1,064 | 0.84 | 2,580 | 626 |  |  |  |  |  |  |  |  | not selected | PRE CI lo<=0 | - |  |

## 4. Alive cell-sessions (tier on MEASURED; stored-only where MEASURED n/a)

None.

Calibration note: the analytic MEASURED was checked against the replay on PB7_PB5_depth_atr0.5_W15_s+0 ASIA (ssa pass 2): analytic HOLD +2.22 pts vs replay MEASURED +1.42 pts (stored +4.78): the analytic is about 0.8 pt/trade optimistic, so a cell whose analytic HOLD is below ~+0.8 pts (~$160 at 10 lots) should be read as not distinguishable from zero until the replay returns. The replay (survivors_for_A.parquet) supersedes it.

## 5. Is the optimum session-specific? (the per-session parameter question)

- Spearman rank correlation of PRE stored cell means across sessions (cells with n>=100 in both): median -0.08 over 10 session pairs; ASIA vs NY-AM [0.02], ASIA vs LONDON [-0.18], NY-AM vs NY-PM [-0.24]. Near zero = the cell that is best in one session carries no information about the others: the optimum is session-specific.

- Session-tuned PRE winner vs the family's one pooled PRE winner, on the session's trades, HOLD, paired by week (weekly $ difference of the session's P&L, week-cluster 95% CI, MDE = 2.8 SE; stored s / MEASURED m):

| session | basis | session winner | pooled winner | n winner | n pooled | weekly diff $ | 95% CI | MDE | note |
|---|---|---|---|---|---|---|---|---|---|
| ASIA | s | FP_CDnop_t500_N_K60 | FP_UAfade_5m_Z_K60 | 231 | 33 | 7,456 | [-3,518, 18,431] | 15,066 |  |
| ASIA | m | FP_CDnop_t500_N_K60 | FP_UAfade_5m_Z_K60 | 231 | 33 | 6,579 | [-4,499, 17,657] | 15,209 |  |
| LONDON | s | FP_UAfade_5m_Z_K60 | FP_UAfade_5m_Z_K60 | 38 | 38 | 0 | [0, 0] | 0 | same cell |
| LONDON | m | FP_UAfade_5m_Z_K60 | FP_UAfade_5m_Z_K60 | 38 | 38 | 0 | [0, 0] | 0 | same cell |
| NY-AM | s | FP_CDpbos_1m_N_K60 | FP_UAfade_5m_Z_K60 | 174 | 31 | -2,073 | [-13,345, 9,199] | 15,475 |  |
| NY-AM | m | FP_CDpbos_1m_N_K60 | FP_UAfade_5m_Z_K60 | 174 | 31 | -2,743 | [-14,108, 8,622] | 15,603 |  |
| NY-PM | s | FP_DDdvx60_cd_5m_N_K60 | FP_UAfade_5m_Z_K60 | 65 | 19 | -2,947 | [-8,570, 2,677] | 7,720 |  |
| NY-PM | m | FP_DDdvx60_cd_5m_N_K60 | FP_UAfade_5m_Z_K60 | 65 | 19 | -3,069 | [-8,721, 2,583] | 7,759 |  |
| NY | s | FP_SI33_1m_N_K60 | FP_UAfade_5m_Z_K60 | 231 | 50 | -8,176 | [-20,392, 4,039] | 16,771 |  |
| NY | m | FP_SI33_1m_N_K60 | FP_UAfade_5m_Z_K60 | 231 | 50 | -8,933 | [-21,294, 3,428] | 16,970 |  |


- Token preference (cell-name tokens in >= 5 cells; PRE stored mean of cells with the token minus those without; descriptive): top 3 / bottom 3 per session:

  - ASIA: best CDall (10 cells, +284), T (16 cells, +267), TS (7 cells, +242); worst UAfinfade (5, -636), DDdvs (12, -394), bar (15, -345)
  - LONDON: best CDpbos (5 cells, +258), DDdvx60 (13 cells, +225), UAfade (12 cells, +219); worst TZ (7, -322), UAcont (12, -315), T (16, -265)
  - PREOPEN: best K60 (35 cells, +457), DDdvx60 (11 cells, +342), CDall (9 cells, +234); worst DDdvs (9, -540), KS (34, -457), T (12, -58)
  - NY-AM: best UAcont (11 cells, +849), CDpbos (5 cells, +766), CDwithp (5 cells, +579); worst TS (16, -920), TZ (7, -774), UAfinfade (5, -419)
  - NY-PM: best SI33 (26 cells, +616), cd (10 cells, +542), T (16 cells, +513); worst CDwithp (5, -879), CDnop (5, -667), UAfinfade (5, -599)
  - NY: best CDpbos (5 cells, +439), ABloose (6 cells, +354), N (98 cells, +354); worst TZ (11, -734), SI43 (5, -734), TS (18, -597)

## 6. Survivors for the replay
- out/sd2a/survivors_for_A.parquet (all families): this family contributes 1 cell-sessions, 912 trade rows. Columns as out/ssa/entries.parquet (t_ent UTC ns, side, st/tt ticks = 240/240, t_fl, lc, lots100, uid, ym) plus cell, session, cid, tier, prereg_member, ld, stored_pts, exit_model. MEASURED-FAIL cells are included as calibration (prereg_member False). Entry convention: F1-type tables (tin) = END stamp of the entry 1-min bar, market at its open (t_ent = tin - 60 s, as ssa_prep2 for PB7); TB4/E1 tables = t_sig_ns exactly. Flat 16:55 ET.
