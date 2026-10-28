# DS3_SESSION2_B_PULLBACK - T-PULLBACK2/3 (PB2 28 + PB2B 24 + PB3 141 = 193 cells)

Written 2026-10-28T21:15Z (D3SB2, T-SESSION-2 item B). Research only; no live/execution/chart change; label days after 2026-02-06 never read. Prereg l2vast/ds3/prereg/SB2_pb_prereg.md sha256 64edfdccaad33c915820c3bb26b3d2b300412e1054e7aff914b966de2be4bdbb (DECISIONS.md); PREHOLD autopilot/DS3_SB2_PB_PREHOLD.md sha256 de7d2875dc10839916db9b9680fe39378be805eabf86b4ab477a1d281c7dac3c (written before the single HOLD and X looks; looks logged in out/sb2/looks.jsonl). Code l2vast/ds3/code/sb2/, outputs l2vast/ds3/out/sb2/pb/.

## 1. Regeneration and reproduction
All 193 cells (PB2 28, PB2B 24, PB3A-D 84, PB3E 27, PB3F 30) were regenerated with the original generating code (pb2_lib/pb2_lad ladders and pb3_core/pb3_core2 events + bracket sim + the exact lock engine): the daily $ series of the re-run equals the stored daily series (atol 1e-6) in 100.0% of cells (193/193); the stored trade tables (tin, side, net) of PB2/PB2B equal the re-run in 100.0%. Basis MAPPED (1-s path bracket sim + corrected-P9 mapping), as the source; the 21 direct-replayed PB3 finalists are not re-run (their direct rows stay in out/SERIES). pnl = lock-engine net $ at the cell's lot sizing; PB2B rungs are separate trades (netraw).


## 2. Multiplicity
Cells 193; F = cells x 7 sessions (6 + NY) = **1351**; overlap clusters (Jaccard>=0.5 on PRE entry minute+side) **53**, F_eff = **371**. PRE tests with n>=100: 1029 cell-sessions; PRE-selected (CI>0): 27 cell-sessions in 14 clusters (chance expectation at 2.5% one-sided: about 26 cell-sessions, fewer independent). Best-of-F label: BOF_F clear 0, BOF_Feff clear 0 (labels, not gates).

## 3. Number alive per session (stored/mapped basis; HOLD looked once)
| session | cells_n100 | pre_selected | candidate | passed | dead_in_hold | alive_clusters | best_t |
|---|---|---|---|---|---|---|---|
| ASIA | 189 | 8 | 4 | 0 | 4 | 2 | 3.22 |
| LONDON | 189 | 8 | 4 | 0 | 4 | 2 | 3.08 |
| PREOPEN | 93 | 9 | 1 | 0 | 8 | 1 | 2.85 |
| NY-AM | 189 | 1 | 0 | 0 | 1 | 0 | 2.21 |
| NY-PM | 180 | 0 | 0 | 0 | 0 | 0 | 1.61 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | nan |
| NY | 189 | 1 | 0 | 0 | 1 | 0 | 2.02 |


Tiers: SESSION-PASS 0, SESSION-CANDIDATE 9, DEAD-IN-HOLD 18. New session books found (alive on stored basis): 9 cell-sessions, 7 cells; alive with MEASURED-analytic mean > 0 on PRE and HOLD: 6.

## 4. Top 30 session-restricted cell-sessions by PRE t (n>=100), regardless of verdict
mean/MDE = per trade $ (the family unit: see conventions); hold_*/x_mean only where PRE-selected (one look). failed_gate = first failing gate (PRE gates for non-selected, HOLD gates for selected). meas_pre/meas_hold = MEASURED-analytic mean.

| cid | session | n | tpw | pre_mean | mde | t | hold_n | hold_mean | x_mean | meas_pre | meas_hold | tier | failed_gate | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB3E_C_R3_P2_40_1.5R | ASIA | 579 | 7.72 | 1,765 | 1,533 | 3.22 | 252 | -182 | -800 | 1,373 | -611 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3C_R60_P1 | LONDON | 349 | 4.65 | 1,679 | 1,528 | 3.08 | 157 | 57.49 | -532 | 1,483 | -164 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3F_C_R3_P2_atr1_2R_bracket | ASIA | 806 | 10.75 | 1,072 | 1,027 | 2.92 | 359 | 1,198 | -842 | 475 | 597 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB2B_B1_SC2_T30_i62 | PREOPEN | 121 | 1.61 | 1,551 | 1,523 | 2.85 | 38.00 | -622 | 792 | 1,380 | -860 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3E_B_R60_P2_pl5_1R | PREOPEN | 168 | 2.24 | 1,851 | 1,828 | 2.84 | 71.00 | 1,105 | -852 | 1,467 | 725 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3D_R3_P1 | ASIA | 485 | 6.47 | 1,460 | 1,456 | 2.81 | 209 | 313 | -412 | 1,263 | 98.72 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3F_C_R3_P2_pl5_2R_bracket | ASIA | 800 | 10.67 | 1,004 | 1,024 | 2.74 | 358 | 850 | -881 | 403 | 241 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3E_D_R3_P2_40_swing | PREOPEN | 124 | 1.65 | 2,028 | 2,096 | 2.71 | 49.00 | -3,080 | -1,780 | 1,796 | -3,472 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3C_R60_P3 | LONDON | 349 | 4.65 | 1,414 | 1,485 | 2.67 | 155 | 932 | -1,207 | 1,214 | 724 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3C_R3_P1 | LONDON | 348 | 4.64 | 1,402 | 1,617 | 2.43 | 163 | 953 | 92.10 | 1,202 | 747 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB2B_B4_SC2_T30_i62 | PREOPEN | 117 | 1.56 | 1,269 | 1,485 | 2.39 | 38.00 | -620 | 993 | 1,088 | -858 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3C_R15_P2 | PREOPEN | 100 | 1.33 | 2,450 | 2,989 | 2.30 | 28.00 | -1,949 | -1,242 | 2,264 | -2,206 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3E_D_R3_P2_40_1.5R | ASIA | 528 | 7.04 | 1,295 | 1,624 | 2.23 | 231 | -26.33 | 751 | 895 | -450 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3F_B_R60_P2_60_1R_tstop120 | NY-AM | 414 | 5.52 | 1,132 | 1,433 | 2.21 | 182 | 293 | 506 | 926 | 78.22 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3C_R60_P5 | LONDON | 335 | 4.47 | 1,135 | 1,441 | 2.21 | 156 | 686 | -1,688 | 931 | 473 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB2B_B1_LAD_T30_i62 | PREOPEN | 180 | 2.40 | 813 | 1,047 | 2.17 | 72.00 | -22.96 | 945 | 629 | -243 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared |
| PB2B_B2_LAD_T30_i62 | LONDON | 367 | 4.89 | 561 | 728 | 2.16 | 153 | 25.15 | 200 | 367 | -191 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3C_R15_P3 | PREOPEN | 102 | 1.36 | 2,440 | 3,178 | 2.15 | 26.00 | -848 | -2,918 | 2,257 | -1,081 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3B_R5_P1 | ASIA | 678 | 9.04 | 924 | 1,204 | 2.15 | 311 | 1,076 | -715 | 718 | 871 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3E_C_R3_P2_40_1R | ASIA | 651 | 8.68 | 899 | 1,200 | 2.10 | 288 | 593 | -503 | 561 | 248 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3E_C_R3_P2_60_1.5R | LONDON | 241 | 3.21 | 1,693 | 2,264 | 2.09 | 117 | 1,228 | -836 | 1,449 | 986 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3F_C_R3_P2_pl5_2R_bracket | LONDON | 641 | 8.55 | 856 | 1,157 | 2.07 | 303 | 337 | -388 | 250 | -289 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB2B_B4_LAD_T30_i62 | PREOPEN | 175 | 2.33 | 810 | 1,117 | 2.03 | 69.00 | 248 | 644 | 626 | 40.22 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3A_R15_P1 | NY | 772 | 10.29 | 818 | 1,134 | 2.02 | 357 | 310 | 166 | 605 | 87.26 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3F_C_R3_P2_atr1_2R_bracket | LONDON | 640 | 8.53 | 840 | 1,173 | 2.01 | 299 | 526 | -532 | 235 | -99.17 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| PB3B_R3_P2 | ASIA | 653 | 8.71 | 949 | 1,327 | 2.00 | 288 | 476 | -630 | 744 | 263 | DEAD-IN-HOLD | HOLD 2025H2<=0 or none | BOF:not cleared |
| PB3F_D_R3_P2_atr1_1.5R_bracket | PREOPEN | 121 | 1.61 | 1,840 | 2,572 | 2.00 | 49.00 | 55.46 | -1,475 | 1,373 | -482 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| PB3B_R3_P1 | ASIA | 686 | 9.15 | 929 | 1,319 | 1.97 | nan | nan | nan | nan | nan | NOT-SELECTED | PRE CI includes 0 (lo -10; needs >0) | nan |
| PB3D_R3_P2 | ASIA | 475 | 6.33 | 1,140 | 1,629 | 1.96 | nan | nan | nan | nan | nan | NOT-SELECTED | PRE CI includes 0 (lo -19; needs >0) | nan |
| PB3E_D_R3_P2_60_1R | ASIA | 475 | 6.33 | 1,140 | 1,629 | 1.96 | nan | nan | nan | nan | nan | NOT-SELECTED | PRE CI includes 0 (lo -19; needs >0) | nan |


## 5. Alive cell-sessions (SESSION-CANDIDATE / SESSION-PASS), by-year, 2023 span, MDE

| cid | session | tier | n | pre_mean | mde | hold_n | hold_mean | hold_mde | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | pre_meas_mean | hold_meas_mean | meas_ok | med_stop | bof_label | verdict_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB3F_C_R3_P2_atr1_2R_bracket | ASIA | SESSION-CANDIDATE | 806 | 1,072 | 1,027 | 359 | 1,198 | 1,629 | 879 | 2,823 | -842 | -990 | 1,317 | 787 | 2,823 | 475 | 597 | True | nan | BOF:not cleared | DEAD |
| PB3E_B_R60_P2_pl5_1R | PREOPEN | SESSION-CANDIDATE | 168 | 1,851 | 1,828 | 71 | 1,105 | 2,672 | 860 | 3,028 | -852 | -778 | 2,130 | 801 | 3,028 | 1,467 | 725 | True | nan | BOF:not cleared | DEAD |
| PB3F_C_R3_P2_pl5_2R_bracket | ASIA | SESSION-CANDIDATE | 800 | 1,004 | 1,024 | 358 | 850 | 1,513 | 531 | 2,535 | -881 | -1,031 | 1,240 | 594 | 2,535 | 403 | 241 | True | nan | BOF:not cleared | DEAD |
| PB2B_B2_LAD_T30_i62 | LONDON | SESSION-CANDIDATE | 367 | 561 | 728 | 153 | 25.15 | 1,526 | 9.88 | 61.81 | 200 | 333 | 845 | 127 | 61.81 | 367 | -191 | False | nan | BOF:not cleared | DEAD |
| PB3B_R5_P1 | ASIA | SESSION-CANDIDATE | 678 | 924 | 1,204 | 311 | 1,076 | 1,626 | 1,196 | 660 | -715 | -852 | 709 | 1,165 | 660 | 718 | 871 | True | nan | BOF:not cleared | CANDIDATE |
| PB3E_C_R3_P2_40_1R | ASIA | SESSION-CANDIDATE | 651 | 899 | 1,200 | 288 | 593 | 1,832 | 580 | 650 | -503 | -391 | 1,128 | 453 | 650 | 561 | 248 | True | nan | BOF:not cleared | DEAD |
| PB3E_C_R3_P2_60_1.5R | LONDON | SESSION-CANDIDATE | 241 | 1,693 | 2,264 | 117 | 1,228 | 3,772 | 1,144 | 1,442 | -836 | -287 | 1,032 | 1,656 | 1,442 | 1,449 | 986 | True | nan | BOF:not cleared | DEAD |
| PB3F_C_R3_P2_pl5_2R_bracket | LONDON | SESSION-CANDIDATE | 641 | 856 | 1,157 | 303 | 337 | 1,236 | 420 | 1.40 | -388 | -303 | 751 | 608 | 1.40 | 250 | -289 | False | nan | BOF:not cleared | DEAD |
| PB3F_C_R3_P2_atr1_2R_bracket | LONDON | SESSION-CANDIDATE | 640 | 840 | 1,173 | 299 | 526 | 1,343 | 601 | 236 | -532 | -463 | 831 | 616 | 236 | 235 | -99.17 | False | nan | BOF:not cleared | DEAD |


## 6. Dead pooled, alive in a session
Selection: pooled all-hours PRE mean <= 0 OR the source label contains DEAD, and tier SESSION-CANDIDATE/PASS. 8 cell-sessions.

| cid | session | tier | n | pre_mean | pool_pre_mean | hold_mean | x_mean | hold_meas_mean | verdict_label | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|
| PB3F_C_R3_P2_atr1_2R_bracket | ASIA | SESSION-CANDIDATE | 806 | 1,072 | 674 | 1,198 | -842 | 597 | DEAD | BOF:not cleared |
| PB3E_B_R60_P2_pl5_1R | PREOPEN | SESSION-CANDIDATE | 168 | 1,851 | -107 | 1,105 | -852 | 725 | DEAD | BOF:not cleared |
| PB3F_C_R3_P2_pl5_2R_bracket | ASIA | SESSION-CANDIDATE | 800 | 1,004 | 537 | 850 | -881 | 241 | DEAD | BOF:not cleared |
| PB2B_B2_LAD_T30_i62 | LONDON | SESSION-CANDIDATE | 367 | 561 | 155 | 25.15 | 200 | -191 | DEAD | BOF:not cleared |
| PB3E_C_R3_P2_40_1R | ASIA | SESSION-CANDIDATE | 651 | 899 | 399 | 593 | -503 | 248 | DEAD | BOF:not cleared |
| PB3E_C_R3_P2_60_1.5R | LONDON | SESSION-CANDIDATE | 241 | 1,693 | 748 | 1,228 | -836 | 986 | DEAD | BOF:not cleared |
| PB3F_C_R3_P2_pl5_2R_bracket | LONDON | SESSION-CANDIDATE | 641 | 856 | 537 | 337 | -388 | -289 | DEAD | BOF:not cleared |
| PB3F_C_R3_P2_atr1_2R_bracket | LONDON | SESSION-CANDIDATE | 640 | 840 | 674 | 526 | -532 | -99.17 | DEAD | BOF:not cleared |


## 7. Replay queue (survivors_for_A)
Replayable static-OCO survivors: 3 cells / 2833 entries written to out/sb2/pb/survivors_for_A.parquet (columns of out/ssa/entries.parquet: t_ent, side, st, tt, t_fl, lc, lots100 + cell, session, family, stop_pts; t_ent = stored instant, t_fl = 16:55 ET of the label day). Not replayable (6 alive cell-sessions): path-dependent or non-market-entry rules, reasons in out/sb2/pb/not_replayable.json. Cells with a stop < 15 pt are not MEASURED-reliable on the stored basis and are flagged by med_stop.

Reasons: variable stop (pullback extreme/ATR), swing/structure target, or time-stop exit x5; resting-limit ladder/scale-in entries x1


## 8. Conventions and limits
$ per trade: PBX = ptsE x 200 (10-lot-equivalent net pts of the mapped conservative basis, costs and sweep surcharge inside); PB2/PB3/T4A = the lock-engine net $ at the cell's lot sizing (R = $12,000); T-HOLD/T4G1 = pts x 200 at 10 lots (base bracket net of exit costs and $4.84 commission, cut legs at the live cut cost 0.995/1.01 pt). MEASURED-analytic = pnl - 200 x lots/10 x (0.25 entry tick + stop slippage(lots, DS3_DN_STOPFILL: 1.44 pt at 10 lots, x1.18 recent drift) on losing trades); it does not remove mapped stop credit that a family may carry and is an estimate, not the replay. Placebo: weekly sign-flip, 200 draws. 2023 span (X) and by-year are printed, never a gate. Week-cluster SE across all label weeks of the window.
