# DS3_SESSION2_B_BRACKET - T-BRACKET grids (re-runnable part: T4A 392 + T4G1 420 tier-4 trade-health cells; SESSION 300 / BA2 286 / T4G2 420 already have rows in the ss2 ledger; G1/G2/G3 = T-HOLD)

Written 2026-10-28T21:21Z (D3SB2, T-SESSION-2 item B). Research only; no live/execution/chart change; label days after 2026-02-06 never read. Prereg l2vast/ds3/prereg/SB2_bracket_prereg.md sha256 835042c0f9615852bc54cd020c790b8e1f53dd78ed1bacfa7779b819ab7e6d90 (DECISIONS.md); PREHOLD autopilot/DS3_SB2_BRACKET_PREHOLD.md sha256 1dfdf0499016b7f4d8cb10e23a66d3a3f42f1da184c2c3dc34080fa53e23c144 (written before the single HOLD and X looks; looks logged in out/sb2/looks.jsonl). Code l2vast/ds3/code/sb2/, outputs l2vast/ds3/out/sb2/bracket/.

## 1. Regeneration and reproduction
T4A: 392 cells (14 tier-4 entries x 28 bracket shapes) regenerated with the original code (t4_lib.gen_ev on the entry events + the 1-s sim + A.price calibrated mapping + lock engine). The row tables (entry bars, side, bracket points) equal the stored rows pkl in 100.0% of cells. The WEEKLY dollar results do NOT reproduce (0.0% within tolerance; median absolute WF weekly-mean difference 1,056 $/wk): out/ba/calib_coef.pkl (the D3BA exit-type calibration used for the T4A pricing, labelled 'interim' in the source) was refit on 2026-10-28 00:38Z, after the T4A run (2026-10-27 06:04Z). The re-run therefore uses the CURRENT calibration; trade entries, brackets and exit classes are the stored ones. T4G1: 14 entry tags x 30 cells = 420 cell-entries, d1/d2/cutj/kind arrays of the re-run identical to the stored screen in 100% of entries (zero maximum difference). SESSION (300), BA2/stage-1 (286) and T4G2 (420) brackets already have trade rows in the ss2 ledger (ba/rows3, ba/rows2, ba/rows, out/t4/G2) and are scored there (DS3_SESSION_2_LEDGER.md); T4D (420 pyramids) belongs to B4; G1/G2/G3 tier 1 (5,088) are T-HOLD (identical cell sets under both names), scored once in DS3_SESSION2_B_HOLD.md.


## 2. Multiplicity
Cells 812; F = cells x 7 sessions (6 + NY) = **5684**; overlap clusters (Jaccard>=0.5 on PRE entry minute+side) **43**, F_eff = **301**. PRE tests with n>=100: 4067 cell-sessions; PRE-selected (CI>0): 129 cell-sessions in 19 clusters (chance expectation at 2.5% one-sided: about 102 cell-sessions, fewer independent). Best-of-F label: BOF_F clear 0, BOF_Feff clear 2 (labels, not gates).

## 3. Number alive per session (stored/mapped basis; HOLD looked once)
| session | cells_n100 | pre_selected | candidate | passed | dead_in_hold | alive_clusters | best_t |
|---|---|---|---|---|---|---|---|
| ASIA | 809 | 61 | 44 | 0 | 17 | 12 | 3.07 |
| LONDON | 751 | 23 | 4 | 0 | 19 | 1 | 4.42 |
| PREOPEN | 430 | 14 | 1 | 0 | 13 | 1 | 2.85 |
| NY-AM | 687 | 16 | 10 | 0 | 6 | 3 | 3.20 |
| NY-PM | 640 | 3 | 0 | 0 | 3 | 0 | 2.15 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | nan |
| NY | 750 | 12 | 9 | 0 | 3 | 4 | 3.96 |


Tiers: SESSION-PASS 0, SESSION-CANDIDATE 68, DEAD-IN-HOLD 61. New session books found (alive on stored basis): 68 cell-sessions, 53 cells; alive with MEASURED-analytic mean > 0 on PRE and HOLD: 57.

## 4. Top 30 session-restricted cell-sessions by PRE t (n>=100), regardless of verdict
mean/MDE = per trade $ (the family unit: see conventions); hold_*/x_mean only where PRE-selected (one look). failed_gate = first failing gate (PRE gates for non-selected, HOLD gates for selected). meas_pre/meas_hold = MEASURED-analytic mean.

| cid | session | n | tpw | pre_mean | mde | t | hold_n | hold_mean | x_mean | meas_pre | meas_hold | tier | failed_gate | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_sst | LONDON | 823 | 10.97 | 636 | 403 | 4.42 | 375 | 677 | 601 | 404 | 443 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF_Feff:clear |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY | 842 | 11.23 | 732 | 518 | 3.96 | 405 | 698 | 258 | 549 | 514 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF_Feff:clear |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | LONDON | 432 | 5.76 | 1,251 | 1,049 | 3.34 | 207 | 286 | -582 | 1,060 | 75.49 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY-AM | 469 | 6.25 | 818 | 714 | 3.20 | 241 | 757 | 360 | 638 | 575 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PRO_KAL_k0.0_t60_s50 | NY | 788 | 10.51 | 1,091 | 958 | 3.19 | 374 | 218 | 447 | 873 | -15.00 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | ASIA | 537 | 7.16 | 1,117 | 1,019 | 3.07 | 234 | 356 | 733 | 880 | 103 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| G1_0028__T4_PRO_ER4_EMA5 | LONDON | 137 | 1.83 | 2,363 | 2,161 | 3.06 | 61 | 673 | 2,315 | 2,140 | 434 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3B_R60_P2_t30_s50 | NY-AM | 701 | 9.35 | 695 | 665 | 2.93 | 307 | -280 | -70.67 | 531 | -468 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3B_R5_P1_t45_s40 | ASIA | 973 | 12.97 | 622 | 599 | 2.91 | 452 | 823 | -517 | 406 | 609 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | ASIA | 539 | 7.19 | 1,050 | 1,016 | 2.89 | 235 | 805 | 624 | 855 | 605 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3B_R60_P2_t30_s40 | NY-AM | 770 | 10.27 | 560 | 547 | 2.87 | 353 | -278 | -54.76 | 378 | -485 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | PREOPEN | 125 | 1.67 | 1,725 | 1,694 | 2.85 | 40 | -1,489 | 27.45 | 1,585 | -1,709 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY-AM | 433 | 5.77 | 814 | 800 | 2.85 | 215 | 830 | 263 | 652 | 669 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| G1_0039__T4_PRO_ER4_EMA5 | LONDON | 137 | 1.83 | 2,194 | 2,163 | 2.84 | 61 | 363 | 2,384 | 1,943 | 90.59 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| G1_0045__T4_PRO_ER4_EMA5 | LONDON | 137 | 1.83 | 2,082 | 2,062 | 2.83 | 61 | 818 | 2,494 | 1,843 | 573 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | ASIA | 580 | 7.73 | 812 | 810 | 2.81 | 253 | 690 | 1,032 | 594 | 468 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | ASIA | 514 | 6.85 | 1,200 | 1,201 | 2.80 | 227 | 676 | 682 | 1,022 | 488 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | PREOPEN | 146 | 1.95 | 1,313 | 1,324 | 2.78 | 49 | -1,136 | -286 | 1,147 | -1,373 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY | 779 | 10.39 | 548 | 566 | 2.71 | 363 | 895 | 237 | 377 | 735 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY | 703 | 9.37 | 713 | 737 | 2.71 | 342 | 1,093 | 290 | 493 | 882 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | NY-AM | 359 | 4.79 | 1,099 | 1,145 | 2.69 | 176 | 1,515 | -243 | 904 | 1,330 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3D_R3_P2_t30_s40 | PREOPEN | 142 | 1.89 | 1,320 | 1,377 | 2.68 | 49 | -1,483 | -567 | 1,158 | -1,720 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF:not cleared |
| G1_0017__T4_PB3B_R5_P1 | ASIA | 753 | 10.04 | 865 | 907 | 2.67 | 361 | 536 | -894 | 629 | 293 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s90 | ASIA | 484 | 6.45 | 1,407 | 1,477 | 2.67 | 210 | 294 | 279 | 1,259 | 132 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| G1_TH_LIVE_ST__T4_PRO_ER4_EMA5 | LONDON | 137 | 1.83 | 1,924 | 2,020 | 2.67 | 61 | 504 | 2,106 | 1,673 | 237 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3B_R5_P1_t60_s40 | ASIA | 827 | 11.03 | 807 | 852 | 2.65 | 370 | 1,049 | -878 | 569 | 814 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| G1_0036__T4_PRO_ER4_EMA5 | LONDON | 137 | 1.83 | 1,946 | 2,058 | 2.65 | 61 | 572 | 2,389 | 1,690 | 299 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | ASIA | 588 | 7.84 | 763 | 810 | 2.63 | 275 | 556 | 430 | 599 | 387 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF:not cleared |
| T4A_PB3D_R3_P2_t45_s50 | LONDON | 432 | 5.76 | 1,009 | 1,085 | 2.61 | 207 | 45.69 | -898 | 818 | -165 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF:not cleared |
| T4A_PRO_KAL_k0.0_t60_s50 | NY-AM | 561 | 7.48 | 1,070 | 1,152 | 2.60 | 283 | -91.68 | 380 | 850 | -330 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none | BOF:not cleared |


## 5. Alive cell-sessions (SESSION-CANDIDATE / SESSION-PASS), by-year, 2023 span, MDE

| cid | session | tier | n | pre_mean | mde | hold_n | hold_mean | hold_mde | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | pre_meas_mean | hold_meas_mean | meas_ok | med_stop | bof_label | verdict_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_sst | LONDON | SESSION-CANDIDATE | 823 | 636 | 403 | 375 | 677 | 517 | 554 | 1,180 | 601 | 560 | 601 | 642 | 1,180 | 404 | 443 | True | nan | BOF_Feff:clear | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY | SESSION-CANDIDATE | 842 | 732 | 518 | 405 | 698 | 678 | 710 | 640 | 258 | 247 | 524 | 874 | 640 | 549 | 514 | True | nan | BOF_Feff:clear | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | LONDON | SESSION-CANDIDATE | 432 | 1,251 | 1,049 | 207 | 286 | 1,462 | 322 | 142 | -582 | -482 | 875 | 975 | 142 | 1,060 | 75.49 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY-AM | SESSION-CANDIDATE | 469 | 818 | 714 | 241 | 757 | 908 | 699 | 984 | 360 | 360 | 472 | 1,009 | 984 | 638 | 575 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_KAL_k0.0_t60_s50 | NY | SESSION-CANDIDATE | 788 | 1,091 | 958 | 374 | 218 | 1,503 | 86.06 | 1,015 | 447 | 373 | 1,135 | 472 | 1,015 | 873 | -15.00 | False | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | ASIA | SESSION-CANDIDATE | 537 | 1,117 | 1,019 | 234 | 356 | 1,411 | 83.01 | 1,682 | 733 | 724 | 925 | 776 | 1,682 | 880 | 103 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t45_s40 | ASIA | SESSION-CANDIDATE | 973 | 622 | 599 | 452 | 823 | 1,051 | 660 | 1,346 | -517 | -725 | 490 | 746 | 1,346 | 406 | 609 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | ASIA | SESSION-CANDIDATE | 539 | 1,050 | 1,016 | 235 | 805 | 1,440 | 577 | 1,919 | 624 | 759 | 794 | 942 | 1,919 | 855 | 605 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY-AM | SESSION-CANDIDATE | 433 | 814 | 800 | 215 | 830 | 1,036 | 744 | 1,170 | 263 | 236 | 425 | 1,067 | 1,170 | 652 | 669 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | ASIA | SESSION-CANDIDATE | 580 | 812 | 810 | 253 | 690 | 1,288 | 426 | 1,982 | 1,032 | 1,071 | 882 | 570 | 1,982 | 594 | 468 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | ASIA | SESSION-CANDIDATE | 514 | 1,200 | 1,201 | 227 | 676 | 1,514 | 445 | 1,824 | 682 | 843 | 1,069 | 838 | 1,824 | 1,022 | 488 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY | SESSION-CANDIDATE | 779 | 548 | 566 | 363 | 895 | 765 | 896 | 892 | 237 | 216 | 328 | 889 | 892 | 377 | 735 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY | SESSION-CANDIDATE | 703 | 713 | 737 | 342 | 1,093 | 1,007 | 1,205 | 547 | 290 | 269 | 647 | 1,007 | 547 | 493 | 882 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | NY-AM | SESSION-CANDIDATE | 359 | 1,099 | 1,145 | 176 | 1,515 | 1,447 | 1,298 | 2,423 | -243 | -300 | 591 | 1,532 | 2,423 | 904 | 1,330 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s90 | ASIA | SESSION-CANDIDATE | 484 | 1,407 | 1,477 | 210 | 294 | 2,162 | 190 | 794 | 279 | 496 | 1,050 | 945 | 794 | 1,259 | 132 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t60_s40 | ASIA | SESSION-CANDIDATE | 827 | 807 | 852 | 370 | 1,049 | 1,289 | 1,039 | 1,088 | -878 | -944 | 497 | 1,065 | 1,088 | 569 | 814 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | ASIA | SESSION-CANDIDATE | 588 | 763 | 810 | 275 | 556 | 968 | 434 | 1,119 | 430 | 534 | 556 | 693 | 1,119 | 599 | 387 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s50 | ASIA | SESSION-CANDIDATE | 500 | 1,202 | 1,309 | 213 | 394 | 1,373 | 122 | 1,732 | 24.44 | 110 | 668 | 1,026 | 1,732 | 984 | 161 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t30_sst | ASIA | SESSION-CANDIDATE | 1,596 | 329 | 359 | 797 | 384 | 424 | 284 | 751 | -36.97 | -142 | 536 | 199 | 751 | 95.28 | 149 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s75 | ASIA | SESSION-CANDIDATE | 497 | 1,260 | 1,388 | 217 | 240 | 1,750 | 269 | 94.87 | 512 | 630 | 1,270 | 676 | 94.87 | 1,099 | 62.77 | True | nan | BOF:not cleared | PENDING_DIRECT |
| G1_0021__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 852 | 952 | 379 | 985 | 1,337 | 1,018 | 883 | 1,073 | 766 | 1,077 | 881 | 883 | 618 | 754 | True | nan | BOF:not cleared | UNLABELLED |
| T4A_PRO_Z20_t1.0_t45_s50 | ASIA | SESSION-CANDIDATE | 963 | 708 | 812 | 487 | 842 | 1,014 | 594 | 1,599 | 423 | 301 | 485 | 827 | 1,599 | 510 | 646 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s60 | ASIA | SESSION-CANDIDATE | 475 | 1,354 | 1,555 | 203 | 336 | 1,657 | 36.70 | 1,879 | -113 | 81.79 | 836 | 972 | 1,879 | 1,152 | 117 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s90 | ASIA | SESSION-CANDIDATE | 446 | 1,639 | 1,895 | 191 | 653 | 2,478 | 681 | 509 | -836 | -570 | 804 | 1,578 | 509 | 1,469 | 471 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | LONDON | SESSION-CANDIDATE | 395 | 1,074 | 1,245 | 188 | 364 | 1,896 | 429 | 90.49 | 419 | 636 | 887 | 810 | 90.49 | 893 | 169 | True | nan | BOF:not cleared | DEAD |
| G1_0039__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 694 | 807 | 379 | 116 | 1,162 | 123 | 94.27 | 849 | 634 | 734 | 513 | 94.27 | 427 | -166 | False | nan | BOF:not cleared | UNLABELLED |
| G1_0041__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 678 | 793 | 379 | 135 | 1,036 | 100 | 240 | 816 | 656 | 852 | 390 | 240 | 403 | -151 | False | nan | BOF:not cleared | UNLABELLED |
| T4A_PB3D_R3_P2_t45_s90 | ASIA | SESSION-CANDIDATE | 484 | 1,300 | 1,532 | 210 | 149 | 2,243 | 41.56 | 670 | 122 | 346 | 928 | 824 | 670 | 1,152 | -12.32 | False | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t60_s50 | ASIA | SESSION-CANDIDATE | 739 | 891 | 1,051 | 323 | 1,201 | 1,513 | 1,245 | 1,048 | -824 | -880 | 564 | 1,206 | 1,048 | 671 | 984 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_Z20_t1.0_t60_s40 | ASIA | SESSION-CANDIDATE | 971 | 688 | 812 | 468 | 464 | 1,038 | 391 | 698 | 617 | 329 | 679 | 649 | 698 | 448 | 218 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY-AM | SESSION-CANDIDATE | 396 | 857 | 1,012 | 205 | 1,016 | 1,428 | 979 | 1,172 | 282 | 237 | 370 | 1,288 | 1,172 | 640 | 802 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t45_s60 | ASIA | SESSION-CANDIDATE | 803 | 713 | 853 | 373 | 959 | 1,404 | 925 | 1,067 | -356 | -487 | 575 | 894 | 1,067 | 529 | 778 | True | nan | BOF:not cleared | DEAD |
| G1_0003__T4_PB3B_R60_P2 | ASIA | SESSION-CANDIDATE | 664 | 751 | 903 | 296 | 1,001 | 1,402 | 1,159 | 473 | 171 | 143 | 1,163 | 613 | 473 | 478 | 733 | True | nan | BOF:not cleared | UNLABELLED |
| G1_0027__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 595 | 716 | 379 | 156 | 895 | 129 | 235 | 633 | 393 | 879 | 303 | 235 | 306 | -141 | False | nan | BOF:not cleared | UNLABELLED |
| G1_0031__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 655 | 800 | 379 | 204 | 1,174 | 240 | 99.01 | 799 | 830 | 931 | 308 | 99.01 | 383 | -76.05 | False | nan | BOF:not cleared | UNLABELLED |
| T4A_PB3D_R3_P2_t30_s50 | NY-AM | SESSION-CANDIDATE | 431 | 688 | 842 | 211 | 728 | 1,124 | 589 | 1,287 | 75.20 | 45.40 | 266 | 955 | 1,287 | 526 | 569 | True | nan | BOF:not cleared | DEAD |
| G1_0021__T4_PB3B_R5_P3 | ASIA | SESSION-CANDIDATE | 614 | 893 | 1,098 | 274 | 529 | 1,759 | 555 | 435 | -96.66 | -263 | 463 | 1,080 | 435 | 661 | 293 | True | nan | BOF:not cleared | UNLABELLED |
| G1_0042__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 704 | 872 | 379 | 268 | 1,088 | 259 | 294 | 513 | 307 | 949 | 426 | 294 | 436 | -10.83 | False | nan | BOF:not cleared | UNLABELLED |
| T4A_PB3D_R3_P2_t45_s60 | ASIA | SESSION-CANDIDATE | 514 | 1,010 | 1,259 | 227 | 462 | 1,588 | 220 | 1,667 | 464 | 633 | 872 | 631 | 1,667 | 832 | 274 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R60_P2_t60_s90 | NY-AM | SESSION-CANDIDATE | 307 | 1,600 | 2,008 | 131 | 374 | 2,819 | 20.02 | 3,107 | 139 | 474 | 1,167 | 846 | 3,107 | 1,425 | 181 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_sst | ASIA | SESSION-CANDIDATE | 752 | 344 | 432 | 349 | 700 | 586 | 508 | 1,665 | 313 | 312 | 329 | 433 | 1,665 | 97.86 | 463 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3D_R3_P2_t30_s40 | NY | SESSION-CANDIDATE | 811 | 445 | 564 | 392 | 489 | 742 | 538 | 253 | 9.50 | -3.27 | 133 | 730 | 253 | 259 | 305 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s60 | ASIA | SESSION-CANDIDATE | 564 | 707 | 908 | 268 | 348 | 1,053 | 208 | 1,002 | 443 | 571 | 596 | 474 | 1,002 | 555 | 189 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_Z20_t1.0_t30_sst | ASIA | SESSION-CANDIDATE | 2,161 | 193 | 248 | 1067 | 203 | 319 | 153 | 379 | 348 | 338 | 311 | 111 | 379 | -49.93 | -41.33 | False | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY-AM | SESSION-CANDIDATE | 346 | 1,087 | 1,401 | 176 | 1,111 | 1,634 | 942 | 1,765 | -61.83 | 156 | 442 | 1,334 | 1,765 | 851 | 869 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s90 | ASIA | SESSION-CANDIDATE | 467 | 1,646 | 2,126 | 195 | 331 | 3,230 | 271 | 611 | 146 | 481 | 1,019 | 1,264 | 611 | 1,391 | 58.03 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t90_sst | NY-AM | SESSION-CANDIDATE | 448 | 1,146 | 1,481 | 185 | 409 | 2,186 | 319 | 891 | -557 | -526 | 1,021 | 630 | 891 | 869 | 127 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3D_R3_P2_t45_s50 | ASIA | SESSION-CANDIDATE | 539 | 815 | 1,070 | 235 | 557 | 1,519 | 316 | 1,732 | 366 | 509 | 546 | 702 | 1,732 | 620 | 357 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s60 | ASIA | SESSION-CANDIDATE | 507 | 1,391 | 1,835 | 227 | 666 | 2,359 | 444 | 1,770 | 637 | 886 | 1,163 | 950 | 1,770 | 1,093 | 350 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3D_R3_P2_t60_s90 | ASIA | SESSION-CANDIDATE | 446 | 1,477 | 1,957 | 191 | 457 | 2,560 | 486 | 311 | -1,093 | -820 | 610 | 1,417 | 311 | 1,308 | 276 | True | nan | BOF:not cleared | DEAD |
| G1_0049__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 700 | 929 | 379 | 385 | 1,295 | 371 | 428 | 771 | 596 | 999 | 434 | 428 | 444 | 113 | True | nan | BOF:not cleared | UNLABELLED |
| T4A_PRO_KAL_k0.0_t60_s40 | NY | SESSION-CANDIDATE | 1,034 | 577 | 765 | 512 | 80.57 | 1,082 | 48.76 | 320 | 62.79 | -50.81 | 572 | 295 | 320 | 334 | -173 | False | nan | BOF:not cleared | DEAD |
| G1_0017__T4_PB3B_R5_P3 | ASIA | SESSION-CANDIDATE | 614 | 738 | 983 | 274 | 155 | 1,657 | 151 | 167 | -541 | -737 | 514 | 665 | 167 | 499 | -93.64 | False | nan | BOF:not cleared | UNLABELLED |
| T4A_PRO_Z20_t1.0_t60_s50 | ASIA | SESSION-CANDIDATE | 843 | 808 | 1,076 | 390 | 828 | 1,388 | 798 | 941 | 38.08 | -149 | 506 | 1,038 | 941 | 587 | 606 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | LONDON | SESSION-CANDIDATE | 475 | 678 | 906 | 237 | 208 | 1,004 | 224 | 137 | 87.64 | 246 | 368 | 591 | 137 | 457 | -25.07 | False | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_sst | NY-AM | SESSION-CANDIDATE | 379 | 1,038 | 1,390 | 182 | 715 | 1,953 | 484 | 1,884 | -346 | -283 | 460 | 1,123 | 1,884 | 799 | 463 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R60_P2_t60_s90 | NY | SESSION-CANDIDATE | 479 | 1,063 | 1,425 | 207 | 371 | 2,278 | 270 | 1,044 | 414 | 333 | 1,182 | 488 | 1,044 | 876 | 177 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P3_t60_s40 | ASIA | SESSION-CANDIDATE | 702 | 661 | 889 | 314 | 477 | 1,441 | 420 | 703 | -335 | -496 | 529 | 667 | 703 | 420 | 232 | True | nan | BOF:not cleared | DEAD |
| G1_0021__T4_PRO_Z60_t1.0 | ASIA | SESSION-CANDIDATE | 717 | 834 | 1,123 | 320 | 927 | 1,778 | 639 | 1,836 | 1,013 | 583 | 745 | 983 | 1,836 | 600 | 692 | True | nan | BOF:not cleared | UNLABELLED |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY | SESSION-CANDIDATE | 618 | 661 | 895 | 286 | 1,213 | 1,064 | 1,291 | 859 | -274 | -145 | 374 | 1,072 | 859 | 416 | 980 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s50 | ASIA | SESSION-CANDIDATE | 530 | 1,170 | 1,591 | 234 | 732 | 2,293 | 489 | 1,908 | 488 | 696 | 790 | 1,013 | 1,908 | 846 | 394 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s50 | NY-AM | SESSION-CANDIDATE | 289 | 1,164 | 1,587 | 148 | 901 | 1,845 | 343 | 3,291 | -448 | -268 | 733 | 892 | 3,291 | 944 | 676 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_Z20_t1.0_t30_s60 | ASIA | SESSION-CANDIDATE | 1,199 | 421 | 576 | 569 | 714 | 840 | 660 | 889 | 1,039 | 1,090 | 403 | 544 | 889 | 266 | 564 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_Z60_t1.0_t30_s50 | ASIA | SESSION-CANDIDATE | 1,056 | 460 | 630 | 518 | 553 | 797 | 342 | 1,171 | 635 | 421 | 256 | 622 | 1,171 | 294 | 388 | True | nan | BOF:not cleared | DEAD |
| T4A_PRO_RIB1m_q30_t30_s50 | ASIA | SESSION-CANDIDATE | 771 | 494 | 678 | 349 | 835 | 959 | 704 | 1,404 | -26.56 | -55.74 | 266 | 731 | 1,404 | 328 | 676 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | PREOPEN | SESSION-CANDIDATE | 103 | 1,730 | 2,384 | 32 | 509 | 2,800 | 407 | 771 | 1,183 | 1,473 | 1,834 | 920 | 771 | 1,548 | 300 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3B_R5_P1_t30_s40 | ASIA | SESSION-CANDIDATE | 1,217 | 334 | 460 | 585 | 611 | 717 | 564 | 768 | 108 | -6.56 | 339 | 456 | 768 | 146 | 430 | True | nan | BOF:not cleared | DEAD |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s75 | NY | SESSION-CANDIDATE | 303 | 1,635 | 2,283 | 152 | 654 | 3,315 | 351 | 2,905 | -1,235 | -1,142 | 1,030 | 1,229 | 2,905 | 1,336 | 340 | True | nan | BOF:not cleared | DEAD |


## 6. Dead pooled, alive in a session
Selection: pooled all-hours PRE mean <= 0 OR the source label contains DEAD, and tier SESSION-CANDIDATE/PASS. 59 cell-sessions.

| cid | session | tier | n | pre_mean | pool_pre_mean | hold_mean | x_mean | hold_meas_mean | verdict_label | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_sst | LONDON | SESSION-CANDIDATE | 823 | 636 | 488 | 677 | 601 | 443 | DEAD | BOF_Feff:clear |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY | SESSION-CANDIDATE | 842 | 732 | 565 | 698 | 258 | 514 | DEAD | BOF_Feff:clear |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | LONDON | SESSION-CANDIDATE | 432 | 1,251 | 931 | 286 | -582 | 75.49 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s40 | NY-AM | SESSION-CANDIDATE | 469 | 818 | 565 | 757 | 360 | 575 | DEAD | BOF:not cleared |
| T4A_PRO_KAL_k0.0_t60_s50 | NY | SESSION-CANDIDATE | 788 | 1,091 | 216 | 218 | 447 | -15.00 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | ASIA | SESSION-CANDIDATE | 537 | 1,117 | 851 | 356 | 733 | 103 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t45_s40 | ASIA | SESSION-CANDIDATE | 973 | 622 | 195 | 823 | -517 | 609 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | ASIA | SESSION-CANDIDATE | 539 | 1,050 | 931 | 805 | 624 | 605 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY-AM | SESSION-CANDIDATE | 433 | 814 | 661 | 830 | 263 | 669 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | ASIA | SESSION-CANDIDATE | 580 | 812 | 782 | 690 | 1,032 | 468 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | ASIA | SESSION-CANDIDATE | 514 | 1,200 | 833 | 676 | 682 | 488 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | NY | SESSION-CANDIDATE | 779 | 548 | 661 | 895 | 237 | 735 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY | SESSION-CANDIDATE | 703 | 713 | 782 | 1,093 | 290 | 882 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | NY-AM | SESSION-CANDIDATE | 359 | 1,099 | 931 | 1,515 | -243 | 1,330 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s90 | ASIA | SESSION-CANDIDATE | 484 | 1,407 | 1,026 | 294 | 279 | 132 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t60_s40 | ASIA | SESSION-CANDIDATE | 827 | 807 | 282 | 1,049 | -878 | 814 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s50 | ASIA | SESSION-CANDIDATE | 588 | 763 | 661 | 556 | 430 | 387 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s50 | ASIA | SESSION-CANDIDATE | 500 | 1,202 | 883 | 394 | 24.44 | 161 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t30_sst | ASIA | SESSION-CANDIDATE | 1,596 | 329 | 136 | 384 | -36.97 | 149 | DEAD | BOF:not cleared |
| T4A_PRO_Z20_t1.0_t45_s50 | ASIA | SESSION-CANDIDATE | 963 | 708 | 384 | 842 | 423 | 646 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s60 | ASIA | SESSION-CANDIDATE | 475 | 1,354 | 899 | 336 | -113 | 117 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s90 | ASIA | SESSION-CANDIDATE | 446 | 1,639 | 940 | 653 | -836 | 471 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s60 | LONDON | SESSION-CANDIDATE | 395 | 1,074 | 833 | 364 | 419 | 169 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t45_s90 | ASIA | SESSION-CANDIDATE | 484 | 1,300 | 893 | 149 | 122 | -12.32 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t60_s50 | ASIA | SESSION-CANDIDATE | 739 | 891 | 391 | 1,201 | -824 | 984 | DEAD | BOF:not cleared |
| T4A_PRO_Z20_t1.0_t60_s40 | ASIA | SESSION-CANDIDATE | 971 | 688 | 367 | 464 | 617 | 218 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | NY-AM | SESSION-CANDIDATE | 396 | 857 | 782 | 1,016 | 282 | 802 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t45_s60 | ASIA | SESSION-CANDIDATE | 803 | 713 | 225 | 959 | -356 | 778 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t30_s50 | NY-AM | SESSION-CANDIDATE | 431 | 688 | 507 | 728 | 75.20 | 569 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t45_s60 | ASIA | SESSION-CANDIDATE | 514 | 1,010 | 659 | 462 | 464 | 274 | DEAD | BOF:not cleared |
| T4A_PB3B_R60_P2_t60_s90 | NY-AM | SESSION-CANDIDATE | 307 | 1,600 | 547 | 374 | 139 | 181 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_sst | ASIA | SESSION-CANDIDATE | 752 | 344 | 488 | 700 | 313 | 463 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t30_s40 | NY | SESSION-CANDIDATE | 811 | 445 | 310 | 489 | 9.50 | 305 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t30_s60 | ASIA | SESSION-CANDIDATE | 564 | 707 | 503 | 348 | 443 | 189 | DEAD | BOF:not cleared |
| T4A_PRO_Z20_t1.0_t30_sst | ASIA | SESSION-CANDIDATE | 2,161 | 193 | 142 | 203 | 348 | -41.33 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY-AM | SESSION-CANDIDATE | 346 | 1,087 | 851 | 1,111 | -61.83 | 869 | DEAD | BOF:not cleared |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s90 | ASIA | SESSION-CANDIDATE | 467 | 1,646 | 1,279 | 331 | 146 | 58.03 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t90_sst | NY-AM | SESSION-CANDIDATE | 448 | 1,146 | -208 | 409 | -557 | 127 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t45_s50 | ASIA | SESSION-CANDIDATE | 539 | 815 | 687 | 557 | 366 | 357 | DEAD | BOF:not cleared |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s60 | ASIA | SESSION-CANDIDATE | 507 | 1,391 | 1,079 | 666 | 637 | 350 | DEAD | BOF:not cleared |
| T4A_PB3D_R3_P2_t60_s90 | ASIA | SESSION-CANDIDATE | 446 | 1,477 | 770 | 457 | -1,093 | 276 | DEAD | BOF:not cleared |
| G1_0049__T4_PRO_Z20_t1.0 | ASIA | SESSION-CANDIDATE | 843 | 700 | -15.89 | 385 | 771 | 113 | UNLABELLED | BOF:not cleared |
| T4A_PRO_KAL_k0.0_t60_s40 | NY | SESSION-CANDIDATE | 1,034 | 577 | 191 | 80.57 | 62.79 | -173 | DEAD | BOF:not cleared |
| G1_0017__T4_PB3B_R5_P3 | ASIA | SESSION-CANDIDATE | 614 | 738 | -35.69 | 155 | -541 | -93.64 | UNLABELLED | BOF:not cleared |
| T4A_PRO_Z20_t1.0_t60_s50 | ASIA | SESSION-CANDIDATE | 843 | 808 | 344 | 828 | 38.08 | 606 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s40 | LONDON | SESSION-CANDIDATE | 475 | 678 | 782 | 208 | 87.64 | -25.07 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_sst | NY-AM | SESSION-CANDIDATE | 379 | 1,038 | 474 | 715 | -346 | 463 | DEAD | BOF:not cleared |
| T4A_PB3B_R60_P2_t60_s90 | NY | SESSION-CANDIDATE | 479 | 1,063 | 547 | 371 | 414 | 177 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P3_t60_s40 | ASIA | SESSION-CANDIDATE | 702 | 661 | 219 | 477 | -335 | 232 | DEAD | BOF:not cleared |
| G1_0021__T4_PRO_Z60_t1.0 | ASIA | SESSION-CANDIDATE | 717 | 834 | -60.95 | 927 | 1,013 | 692 | UNLABELLED | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s40 | NY | SESSION-CANDIDATE | 618 | 661 | 851 | 1,213 | -274 | 980 | DEAD | BOF:not cleared |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s50 | ASIA | SESSION-CANDIDATE | 530 | 1,170 | 1,077 | 732 | 488 | 394 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t60_s50 | NY-AM | SESSION-CANDIDATE | 289 | 1,164 | 883 | 901 | -448 | 676 | DEAD | BOF:not cleared |
| T4A_PRO_Z20_t1.0_t30_s60 | ASIA | SESSION-CANDIDATE | 1,199 | 421 | 149 | 714 | 1,039 | 564 | DEAD | BOF:not cleared |
| T4A_PRO_Z60_t1.0_t30_s50 | ASIA | SESSION-CANDIDATE | 1,056 | 460 | 208 | 553 | 635 | 388 | DEAD | BOF:not cleared |
| T4A_PRO_RIB1m_q30_t30_s50 | ASIA | SESSION-CANDIDATE | 771 | 494 | 159 | 835 | -26.56 | 676 | DEAD | BOF:not cleared |
| T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s50 | PREOPEN | SESSION-CANDIDATE | 103 | 1,730 | 931 | 509 | 1,183 | 300 | DEAD | BOF:not cleared |
| T4A_PB3B_R5_P1_t30_s40 | ASIA | SESSION-CANDIDATE | 1,217 | 334 | 225 | 611 | 108 | 430 | DEAD | BOF:not cleared |
| T4A_PB3E_D_R3_P2_40_1.5R_t45_s75 | NY | SESSION-CANDIDATE | 303 | 1,635 | 1,379 | 654 | -1,235 | 340 | DEAD | BOF:not cleared |


## 7. Replay queue (survivors_for_A)
Replayable static-OCO survivors: 37 cells / 58616 entries written to out/sb2/bracket/survivors_for_A.parquet (columns of out/ssa/entries.parquet: t_ent, side, st, tt, t_fl, lc, lots100 + cell, session, family, stop_pts; t_ent = stored instant, t_fl = 16:55 ET of the label day). Not replayable (17 alive cell-sessions): path-dependent or non-market-entry rules, reasons in out/sb2/bracket/not_replayable.json. Cells with a stop < 15 pt are not MEASURED-reliable on the stored basis and are flagged by med_stop.

Reasons: trade-health modifier (path-dependent cut), or structure stop x17


## 8. Conventions and limits
$ per trade: PBX = ptsE x 200 (10-lot-equivalent net pts of the mapped conservative basis, costs and sweep surcharge inside); PB2/PB3/T4A = the lock-engine net $ at the cell's lot sizing (R = $12,000); T-HOLD/T4G1 = pts x 200 at 10 lots (base bracket net of exit costs and $4.84 commission, cut legs at the live cut cost 0.995/1.01 pt). MEASURED-analytic = pnl - 200 x lots/10 x (0.25 entry tick + stop slippage(lots, DS3_DN_STOPFILL: 1.44 pt at 10 lots, x1.18 recent drift) on losing trades); it does not remove mapped stop credit that a family may carry and is an estimate, not the replay. Placebo: weekly sign-flip, 200 draws. 2023 span (X) and by-year are printed, never a gate. Week-cluster SE across all label weeks of the window.
