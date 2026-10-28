# DS3_SESSION2_B_HOLD - T-HOLD (G1 4,800 + G2 150 + G3 130 re-runnable of 138 = trade-health modifiers on ST/HM/KB/SM/EM; identical to TBRACKET_G1/G2/G3)

Written 2026-10-28T21:21Z (D3SB2, T-SESSION-2 item B). Research only; no live/execution/chart change; label days after 2026-02-06 never read. Prereg l2vast/ds3/prereg/SB2_hold_prereg.md sha256 3ea4241f01f98ce30f8aa051606b4a45b7ed0444f65b838c5117fd35fa8ba7c4 (DECISIONS.md); PREHOLD autopilot/DS3_SB2_HOLD_PREHOLD.md sha256 1097955eb30ce4da15c09c023291a174c81ff1be4bd6e0ed1ab890174cbc0858 (written before the single HOLD and X looks; looks logged in out/sb2/looks.jsonl). Code l2vast/ds3/code/sb2/, outputs l2vast/ds3/out/sb2/hold/.

## 1. Regeneration and reproduction
G1 (loss-side TH, 960 cells x 5 entries = 4,800): the original kernel (g1_screen.run: per-second condition bits, numba scan over cells, time-only and MAE-only cells) was re-run on all five entries from the stored 1-s path arrays; the d1/d2 delta matrices, cut-second matrices and fill-kind matrices are bit-identical to the stored screen (maximum absolute difference 0.0) for 4,800/4,800 cell-entries. G2 (profit-side, 30 cells x 5 = 150): the original phaseA kernel was re-run for all 150 cell-entries; the per-trade net-pts tables equal the stored tr.parquet in 150/150 (100%). G3 (new mechanisms): run_s1 re-run for all cells; the per-trade diff arrays equal the stored stage_final diffs in 130/130 stored files; 8 further OPP/A-family arrays that the source did not save were produced by the same re-run, giving 138 cell-entries (130 cells of the report's 138 + the 8 OPP rows; the 2 sequence-level re-entry cells of G3 produce extra entries rather than per-trade deltas and are listed as not re-runnable here). Basis: MAPPED screen of the source (1-s path kernel; live exit costs 0.995 market / 1.01 stop-join / 0 target applied as in the source), 10 lots; cell pnl per trade = base bracket pts minus base exit cost minus $4.84 commission (0.242 pt), with the cut legs replaced where the rule fires, x $200/pt. Entry time = the base trade's entry bar (a TH rule changes the exit, not the entry); trades that a cut frees the book for (n_new_entries in G2) are included in the G2 tables and absent from G1/G3 per-trade deltas (the source's paired mean also excludes them).


## 2. Multiplicity
Cells 5088; F = cells x 7 sessions (6 + NY) = **35616**; overlap clusters (Jaccard>=0.5 on PRE entry minute+side) **5**, F_eff = **35**. PRE tests with n>=100: 28493 cell-sessions; PRE-selected (CI>0): 1469 cell-sessions in 5 clusters (chance expectation at 2.5% one-sided: about 712 cell-sessions, fewer independent). Best-of-F label: BOF_F clear 0, BOF_Feff clear 33 (labels, not gates).

## 3. Number alive per session (stored/mapped basis; HOLD looked once)
| session | cells_n100 | pre_selected | candidate | passed | dead_in_hold | alive_clusters | best_t |
|---|---|---|---|---|---|---|---|
| ASIA | 5088 | 636 | 257 | 0 | 379 | 4 | 3.26 |
| LONDON | 5088 | 0 | 0 | 0 | 0 | 0 | 1.78 |
| PREOPEN | 3053 | 0 | 0 | 0 | 0 | 0 | 1.90 |
| NY-AM | 5088 | 563 | 132 | 0 | 431 | 3 | 3.63 |
| NY-PM | 5088 | 0 | 0 | 0 | 0 | 0 | 1.88 |
| CLOSE | 0 | 0 | 0 | 0 | 0 | 0 | nan |
| NY | 5088 | 270 | 16 | 0 | 254 | 2 | 3.80 |


Tiers: SESSION-PASS 0, SESSION-CANDIDATE 405, DEAD-IN-HOLD 1064. New session books found (alive on stored basis): 405 cell-sessions, 387 cells; alive with MEASURED-analytic mean > 0 on PRE and HOLD: 326.

## 4. Top 30 session-restricted cell-sessions by PRE t (n>=100), regardless of verdict
mean/MDE = per trade $ (the family unit: see conventions); hold_*/x_mean only where PRE-selected (one look). failed_gate = first failing gate (PRE gates for non-selected, HOLD gates for selected). meas_pre/meas_hold = MEASURED-analytic mean.

| cid | session | n | tpw | pre_mean | mde | t | hold_n | hold_mean | x_mean | meas_pre | meas_hold | tier | failed_gate | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1_0005__KB | NY | 1,547 | 20.63 | 864 | 636 | 3.80 | 686 | -394 | 10.20 | 633 | -639 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0390__KB | NY-AM | 885 | 11.80 | 1,137 | 878 | 3.63 | 430 | -308 | 443 | 912 | -551 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0476__KB | NY-AM | 885 | 11.80 | 1,098 | 871 | 3.53 | 430 | -470 | 92.78 | 855 | -736 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0009__KB | NY | 1,547 | 20.63 | 767 | 617 | 3.48 | 686 | -472 | 55.35 | 539 | -715 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0390__KB | NY | 1,547 | 20.63 | 850 | 691 | 3.44 | 686 | -84.59 | 75.94 | 623 | -323 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0013__KB | NY | 1,547 | 20.63 | 732 | 604 | 3.39 | 686 | -438 | 6.13 | 509 | -675 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0788__KB | NY-AM | 885 | 11.80 | 1,068 | 888 | 3.37 | 430 | -352 | 256 | 820 | -619 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0474__KB | NY-AM | 885 | 11.80 | 1,022 | 856 | 3.34 | 430 | -283 | 296 | 777 | -544 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0476__KB | NY | 1,547 | 20.63 | 765 | 643 | 3.33 | 686 | -139 | 3.35 | 513 | -403 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G3_OPP_EM__HM | ASIA | 622 | 8.29 | 1,048 | 901 | 3.26 | 289 | 1,623 | -103 | 814 | 1,401 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF_Feff:clear |
| G1_0133__KB | NY-AM | 885 | 11.80 | 994 | 855 | 3.26 | 430 | -968 | 67.07 | 756 | -1,233 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0180__KB | NY | 1,547 | 20.63 | 691 | 595 | 3.25 | 686 | 60.82 | -148 | 429 | -209 | DEAD-IN-HOLD | HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0775__KB | NY-AM | 885 | 11.80 | 1,027 | 884 | 3.25 | 430 | -877 | -11.19 | 791 | -1,138 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0410__KB | NY-AM | 885 | 11.80 | 1,041 | 897 | 3.25 | 430 | -644 | 207 | 801 | -906 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0563__KB | NY-AM | 885 | 11.80 | 1,033 | 895 | 3.23 | 430 | -456 | 484 | 798 | -713 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0451__KB | NY | 1,547 | 20.63 | 723 | 631 | 3.21 | 686 | -464 | -120 | 493 | -709 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0883__KB | NY | 1,547 | 20.63 | 742 | 650 | 3.20 | 686 | -285 | 63.92 | 497 | -543 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0887__KB | NY-AM | 885 | 11.80 | 969 | 849 | 3.20 | 430 | -494 | 175 | 727 | -757 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0579__KB | NY | 1,547 | 20.63 | 724 | 635 | 3.19 | 686 | -244 | 126 | 482 | -497 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0506__HM | NY-AM | 554 | 7.39 | 749 | 657 | 3.19 | 249 | 987 | -479 | 478 | 722 | SESSION-CANDIDATE | none (PRE+HOLD gates passed) | BOF_Feff:clear |
| G1_0180__KB | NY-AM | 885 | 11.80 | 908 | 799 | 3.18 | 430 | -271 | 220 | 654 | -545 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0793__KB | NY | 1,547 | 20.63 | 645 | 575 | 3.14 | 686 | -169 | 139 | 389 | -436 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0508__KB | NY | 1,547 | 20.63 | 754 | 674 | 3.13 | 686 | -304 | 131 | 529 | -543 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0775__KB | NY | 1,547 | 20.63 | 741 | 663 | 3.13 | 686 | -364 | 113 | 499 | -618 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0822__KB | NY-AM | 885 | 11.80 | 1,022 | 915 | 3.13 | 430 | -829 | 490 | 793 | -1,083 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0579__KB | NY-AM | 885 | 11.80 | 1,017 | 914 | 3.11 | 430 | -493 | 491 | 780 | -749 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0700__KB | NY | 1,547 | 20.63 | 716 | 644 | 3.11 | 686 | -367 | -201 | 479 | -617 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0447__KB | NY-AM | 885 | 11.80 | 935 | 841 | 3.11 | 430 | -558 | 269 | 689 | -826 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0793__KB | NY-AM | 885 | 11.80 | 904 | 814 | 3.11 | 430 | -627 | 235 | 654 | -900 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2025H2<=0 or none;HOLD 2026 stub<=0 or none | BOF_Feff:clear |
| G1_0444__KB | NY-AM | 885 | 11.80 | 928 | 836 | 3.11 | 430 | -136 | 52.36 | 669 | -412 | DEAD-IN-HOLD | HOLD mean<=0;HOLD 2026 stub<=0 or none | BOF_Feff:clear |


## 5. Alive cell-sessions (SESSION-CANDIDATE / SESSION-PASS), by-year, 2023 span, MDE

| cid | session | tier | n | pre_mean | mde | hold_n | hold_mean | hold_mde | h25_mean | h26_mean | x_mean | y2023_mean | y2024_mean | y2025_mean | y2026_mean | pre_meas_mean | hold_meas_mean | meas_ok | med_stop | bof_label | verdict_label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G3_OPP_EM__HM | ASIA | SESSION-CANDIDATE | 622 | 1,048 | 901 | 289 | 1,623 | 1,538 | 1,112 | 3,616 | -103 | -388 | 873 | 1,271 | 3,616 | 814 | 1,401 | True | nan | BOF_Feff:clear | DEAD |
| G1_0506__HM | NY-AM | SESSION-CANDIDATE | 554 | 749 | 657 | 249 | 987 | 1,735 | 950 | 1,148 | -479 | -584 | 821 | 757 | 1,148 | 478 | 722 | True | nan | BOF_Feff:clear | DEAD |
| G2_m40_r3_t8_s1__HM | ASIA | SESSION-CANDIDATE | 736 | 981 | 908 | 348 | 658 | 1,185 | 348 | 1,808 | -269 | -345 | 974 | 661 | 1,808 | 816 | 489 | True | nan | BOF:not cleared | DEAD |
| G1_0180__HM | NY-AM | SESSION-CANDIDATE | 554 | 845 | 797 | 249 | 465 | 1,907 | 143 | 1,849 | 125 | 146 | 980 | 322 | 1,849 | 589 | 202 | True | nan | BOF:not cleared | DEAD |
| G3_OPP_SM__HM | ASIA | SESSION-CANDIDATE | 622 | 987 | 933 | 289 | 1,608 | 1,598 | 1,014 | 3,926 | -201 | -579 | 829 | 1,218 | 3,926 | 761 | 1,392 | True | nan | BOF:not cleared | DEAD |
| G2_m40_r2_t8_s1__HM | ASIA | SESSION-CANDIDATE | 737 | 959 | 926 | 348 | 643 | 1,188 | 346 | 1,744 | -333 | -419 | 938 | 660 | 1,744 | 794 | 474 | True | nan | BOF:not cleared | DEAD |
| G1_0031__HM | NY-AM | SESSION-CANDIDATE | 554 | 798 | 786 | 249 | 287 | 1,800 | 38.72 | 1,356 | 8.00 | 50.01 | 872 | 287 | 1,356 | 530 | 13.57 | True | nan | BOF:not cleared | DEAD |
| G2_TRAILONLY_m40_t8__HM | ASIA | SESSION-CANDIDATE | 737 | 906 | 893 | 348 | 656 | 1,175 | 333 | 1,855 | -333 | -419 | 922 | 600 | 1,855 | 740 | 487 | True | nan | BOF:not cleared | DEAD |
| G1_0069__HM | NY-AM | SESSION-CANDIDATE | 554 | 957 | 950 | 249 | 880 | 2,051 | 145 | 4,039 | -261 | 23.54 | 812 | 460 | 4,039 | 724 | 646 | True | nan | BOF:not cleared | DEAD |
| G1_0030__HM | NY-AM | SESSION-CANDIDATE | 554 | 760 | 764 | 249 | 394 | 1,754 | 118 | 1,579 | -324 | -360 | 791 | 366 | 1,579 | 488 | 119 | True | nan | BOF:not cleared | DEAD |
| G1_0029__HM | NY-AM | SESSION-CANDIDATE | 554 | 760 | 767 | 249 | 340 | 1,648 | 126 | 1,259 | -277 | -334 | 822 | 357 | 1,259 | 487 | 61.73 | True | nan | BOF:not cleared | DEAD |
| G1_0569__HM | NY-AM | SESSION-CANDIDATE | 554 | 1,017 | 1,073 | 249 | 874 | 2,015 | 381 | 2,994 | -82.36 | 193 | 803 | 680 | 2,994 | 798 | 654 | True | nan | BOF:not cleared | DEAD |
| G1_0548__HM | NY-AM | SESSION-CANDIDATE | 554 | 628 | 663 | 249 | 867 | 1,626 | 648 | 1,809 | -361 | -462 | 756 | 512 | 1,809 | 354 | 597 | True | nan | BOF:not cleared | DEAD |
| G1_0876__SM | ASIA | SESSION-CANDIDATE | 242 | 1,283 | 1,359 | 113 | 274 | 1,580 | 24.01 | 1,252 | 622 | 524 | 1,250 | 692 | 1,252 | 1,010 | -19.60 | False | nan | BOF:not cleared | DEAD |
| G2_m40_r4_t8_s1__HM | ASIA | SESSION-CANDIDATE | 677 | 1,001 | 1,065 | 318 | 1,011 | 1,474 | 814 | 1,748 | -455 | -643 | 835 | 1,040 | 1,748 | 819 | 826 | True | nan | BOF:not cleared | DEAD |
| G1_0273__HM | NY-AM | SESSION-CANDIDATE | 554 | 814 | 866 | 249 | 662 | 1,893 | 255 | 2,413 | -290 | -325 | 996 | 324 | 2,413 | 554 | 402 | True | nan | BOF:not cleared | DEAD |
| G1_0359__HM | NY-AM | SESSION-CANDIDATE | 554 | 904 | 964 | 249 | 1,318 | 2,149 | 723 | 3,876 | 231 | 466 | 802 | 739 | 3,876 | 678 | 1,099 | True | nan | BOF:not cleared | DEAD |
| G1_0832__HM | NY-AM | SESSION-CANDIDATE | 554 | 732 | 782 | 249 | 545 | 1,816 | 116 | 2,389 | 95.93 | 140 | 923 | 195 | 2,389 | 472 | 283 | True | nan | BOF:not cleared | DEAD |
| G1_0292__SM | ASIA | SESSION-CANDIDATE | 242 | 1,259 | 1,347 | 113 | 317 | 1,557 | 71.79 | 1,276 | 616 | 517 | 1,213 | 718 | 1,276 | 985 | 23.33 | True | nan | BOF:not cleared | DEAD |
| G1_0579__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,923 | 2,060 | 80 | 437 | 3,070 | 235 | 1,478 | 64.08 | 252 | 2,074 | 745 | 1,478 | 1,698 | 196 | True | nan | BOF:not cleared | DEAD |
| G1_0956__HM | ASIA | SESSION-CANDIDATE | 622 | 938 | 1,010 | 289 | 1,488 | 1,592 | 1,296 | 2,237 | 7.69 | -344 | 816 | 1,297 | 2,237 | 696 | 1,257 | True | nan | BOF:not cleared | DEAD |
| G1_0155__EM | ASIA | SESSION-CANDIDATE | 249 | 1,404 | 1,525 | 128 | 622 | 2,086 | 214 | 2,394 | -71.06 | -316 | 1,388 | 872 | 2,394 | 1,167 | 371 | True | nan | BOF:not cleared | DEAD |
| G1_0705__HM | NY-AM | SESSION-CANDIDATE | 554 | 833 | 908 | 249 | 941 | 2,026 | 287 | 3,751 | 446 | 436 | 1,025 | 373 | 3,751 | 586 | 698 | True | nan | BOF:not cleared | DEAD |
| G1_0715__EM | ASIA | SESSION-CANDIDATE | 249 | 1,467 | 1,609 | 128 | 514 | 2,618 | 14.76 | 2,679 | 200 | 229 | 962 | 1,034 | 2,679 | 1,234 | 263 | True | nan | BOF:not cleared | DEAD |
| G1_0293__EM | ASIA | SESSION-CANDIDATE | 249 | 1,324 | 1,456 | 128 | 657 | 2,050 | 254 | 2,404 | -74.98 | -319 | 1,234 | 924 | 2,404 | 1,084 | 405 | True | nan | BOF:not cleared | DEAD |
| G1_0254__SM | ASIA | SESSION-CANDIDATE | 242 | 1,227 | 1,352 | 113 | 335 | 1,539 | 81.79 | 1,324 | 616 | 519 | 1,198 | 692 | 1,324 | 954 | 44.03 | True | nan | BOF:not cleared | DEAD |
| G1_0127__HM | NY-AM | SESSION-CANDIDATE | 554 | 904 | 999 | 249 | 1,072 | 1,846 | 532 | 3,391 | 600 | 794 | 1,012 | 503 | 3,391 | 661 | 839 | True | nan | BOF:not cleared | DEAD |
| G1_0947__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 897 | 249 | 1,074 | 1,993 | 395 | 3,990 | -266 | -99.42 | 674 | 573 | 3,990 | 570 | 840 | True | nan | BOF:not cleared | DEAD |
| G1_0101__SM | ASIA | SESSION-CANDIDATE | 242 | 1,224 | 1,361 | 113 | 278 | 1,559 | 27.90 | 1,259 | 606 | 493 | 1,203 | 664 | 1,259 | 949 | -15.17 | False | nan | BOF:not cleared | DEAD |
| G1_0709__HM | ASIA | SESSION-CANDIDATE | 622 | 931 | 1,040 | 289 | 1,404 | 1,513 | 1,400 | 1,417 | 146 | -186 | 876 | 1,289 | 1,417 | 685 | 1,170 | True | nan | BOF:not cleared | DEAD |
| G1_0589__HM | NY-AM | SESSION-CANDIDATE | 554 | 749 | 839 | 249 | 809 | 1,806 | 254 | 3,191 | -309 | -372 | 1,026 | 223 | 3,191 | 484 | 547 | True | nan | BOF:not cleared | DEAD |
| G1_0649__HM | NY-AM | SESSION-CANDIDATE | 554 | 753 | 843 | 249 | 744 | 1,755 | 411 | 2,174 | -494 | -544 | 817 | 474 | 2,174 | 489 | 484 | True | nan | BOF:not cleared | DEAD |
| G1_0249__HM | ASIA | SESSION-CANDIDATE | 622 | 921 | 1,033 | 289 | 1,513 | 1,614 | 1,177 | 2,824 | -558 | -870 | 697 | 1,263 | 2,824 | 693 | 1,294 | True | nan | BOF:not cleared | DEAD |
| G1_0005__HM | NY-AM | SESSION-CANDIDATE | 554 | 938 | 1,053 | 249 | 1,002 | 2,094 | 340 | 3,845 | 238 | 436 | 737 | 675 | 3,845 | 714 | 778 | True | nan | BOF:not cleared | DEAD |
| G1_0807__SM | ASIA | SESSION-CANDIDATE | 242 | 1,983 | 2,230 | 113 | 308 | 3,193 | 212 | 682 | 1,177 | 1,103 | 1,793 | 1,254 | 682 | 1,775 | 77.45 | True | nan | BOF:not cleared | DEAD |
| G1_0700__HM | NY-AM | SESSION-CANDIDATE | 554 | 898 | 1,010 | 249 | 840 | 2,264 | 173 | 3,711 | 186 | 339 | 1,014 | 312 | 3,711 | 667 | 610 | True | nan | BOF:not cleared | DEAD |
| G1_0895__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 800 | 249 | 500 | 1,443 | 225 | 1,681 | -57.87 | -105 | 909 | 269 | 1,681 | 435 | 222 | True | nan | BOF:not cleared | DEAD |
| G1_0246__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,451 | 1,636 | 100 | 1,924 | 3,250 | 2,028 | 1,164 | 761 | 751 | 1,822 | 1,371 | 1,164 | 1,223 | 1,701 | True | nan | BOF:not cleared | DEAD |
| G1_0696__HM | NY-AM | SESSION-CANDIDATE | 554 | 831 | 938 | 249 | 819 | 2,020 | 142 | 3,727 | -232 | -179 | 1,020 | 227 | 3,727 | 585 | 575 | True | nan | BOF:not cleared | DEAD |
| G1_0652__SM | ASIA | SESSION-CANDIDATE | 242 | 1,212 | 1,368 | 113 | 275 | 1,572 | 5.68 | 1,328 | 634 | 526 | 1,170 | 666 | 1,328 | 937 | -18.71 | False | nan | BOF:not cleared | DEAD |
| G1_0394__SM | ASIA | SESSION-CANDIDATE | 242 | 1,118 | 1,264 | 113 | 409 | 1,432 | 2.39 | 1,998 | 717 | 549 | 1,120 | 624 | 1,998 | 827 | 99.92 | True | nan | BOF:not cleared | DEAD |
| G1_0066__SM | ASIA | SESSION-CANDIDATE | 242 | 1,210 | 1,367 | 113 | 255 | 1,587 | 4.01 | 1,237 | 608 | 515 | 1,169 | 653 | 1,237 | 935 | -38.62 | False | nan | BOF:not cleared | DEAD |
| G1_0633__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,689 | 1,910 | 80 | 641 | 2,788 | 748 | 90.22 | 312 | 489 | 1,413 | 1,292 | 90.22 | 1,442 | 379 | True | nan | BOF:not cleared | DEAD |
| G1_0096__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 919 | 249 | 707 | 1,999 | 233 | 2,743 | 192 | 412 | 793 | 390 | 2,743 | 565 | 455 | True | nan | BOF:not cleared | DEAD |
| G1_0328__HM | NY-AM | SESSION-CANDIDATE | 554 | 716 | 810 | 249 | 606 | 1,934 | 37.41 | 3,048 | 794 | 881 | 958 | 126 | 3,048 | 453 | 351 | True | nan | BOF:not cleared | DEAD |
| G1_0069__HM | ASIA | SESSION-CANDIDATE | 622 | 994 | 1,128 | 289 | 1,376 | 1,593 | 1,249 | 1,870 | -140 | -391 | 773 | 1,327 | 1,870 | 774 | 1,164 | True | nan | BOF:not cleared | DEAD |
| G1_0592__HM | ASIA | SESSION-CANDIDATE | 622 | 864 | 981 | 289 | 890 | 1,365 | 879 | 930 | -363 | -755 | 1,139 | 767 | 930 | 614 | 642 | True | nan | BOF:not cleared | DEAD |
| G1_0235__SM | ASIA | SESSION-CANDIDATE | 242 | 1,214 | 1,380 | 113 | 257 | 1,591 | 14.57 | 1,204 | 653 | 557 | 1,240 | 601 | 1,204 | 942 | -36.85 | False | nan | BOF:not cleared | DEAD |
| G1_0940__HM | ASIA | SESSION-CANDIDATE | 622 | 926 | 1,054 | 289 | 1,415 | 1,633 | 1,239 | 2,100 | -4.89 | -280 | 809 | 1,227 | 2,100 | 687 | 1,190 | True | nan | BOF:not cleared | DEAD |
| G1_0004__HM | NY-AM | SESSION-CANDIDATE | 554 | 876 | 998 | 249 | 856 | 1,970 | 350 | 3,033 | 59.64 | 124 | 836 | 567 | 3,033 | 640 | 625 | True | nan | BOF:not cleared | DEAD |
| G1_0760__SM | ASIA | SESSION-CANDIDATE | 242 | 1,141 | 1,301 | 113 | 440 | 1,532 | 4.02 | 2,144 | 720 | 536 | 1,192 | 598 | 2,144 | 852 | 137 | True | nan | BOF:not cleared | DEAD |
| G1_0837__HM | ASIA | SESSION-CANDIDATE | 622 | 926 | 1,056 | 289 | 1,552 | 1,504 | 1,396 | 2,160 | 187 | -157 | 685 | 1,433 | 2,160 | 687 | 1,329 | True | nan | BOF:not cleared | DEAD |
| G1_0586__SM | ASIA | SESSION-CANDIDATE | 242 | 1,113 | 1,269 | 113 | 417 | 1,443 | 0.72 | 2,044 | 728 | 561 | 1,113 | 622 | 2,044 | 821 | 108 | True | nan | BOF:not cleared | DEAD |
| G1_0148__HM | NY-AM | SESSION-CANDIDATE | 554 | 824 | 941 | 249 | 653 | 1,954 | 9.72 | 3,417 | -65.57 | 72.41 | 1,098 | 49.24 | 3,417 | 576 | 404 | True | nan | BOF:not cleared | DEAD |
| G1_0478__SM | ASIA | SESSION-CANDIDATE | 242 | 1,197 | 1,368 | 113 | 270 | 1,559 | 15.12 | 1,270 | 627 | 517 | 1,172 | 649 | 1,270 | 923 | -23.13 | False | nan | BOF:not cleared | DEAD |
| G1_0616__HM | NY-AM | SESSION-CANDIDATE | 554 | 672 | 768 | 249 | 420 | 1,579 | 143 | 1,608 | 73.95 | 139 | 762 | 259 | 1,608 | 391 | 135 | True | nan | BOF:not cleared | DEAD |
| G1_0623__SM | ASIA | SESSION-CANDIDATE | 242 | 1,108 | 1,270 | 113 | 420 | 1,444 | 7.39 | 2,033 | 732 | 567 | 1,106 | 625 | 2,033 | 816 | 111 | True | nan | BOF:not cleared | DEAD |
| G1_0911__HM | NY-AM | SESSION-CANDIDATE | 554 | 890 | 1,021 | 249 | 1,044 | 2,267 | 412 | 3,761 | 7.22 | 115 | 974 | 466 | 3,761 | 662 | 821 | True | nan | BOF:not cleared | DEAD |
| G1_0784__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,615 | 1,856 | 80 | 363 | 2,742 | 116 | 1,636 | -89.32 | 15.79 | 1,449 | 875 | 1,636 | 1,353 | 79.63 | True | nan | BOF:not cleared | DEAD |
| G1_0879__SM | ASIA | SESSION-CANDIDATE | 242 | 1,928 | 2,216 | 113 | 559 | 3,250 | 618 | 326 | 856 | 688 | 1,614 | 1,589 | 326 | 1,722 | 334 | True | nan | BOF:not cleared | DEAD |
| G1_0017__HM | NY-AM | SESSION-CANDIDATE | 554 | 791 | 911 | 249 | 1,058 | 2,027 | 623 | 2,925 | 53.18 | 248 | 876 | 482 | 2,925 | 555 | 825 | True | nan | BOF:not cleared | DEAD |
| G1_0687__SM | ASIA | SESSION-CANDIDATE | 242 | 1,116 | 1,284 | 113 | 418 | 1,454 | 24.06 | 1,959 | 709 | 524 | 1,130 | 631 | 1,959 | 827 | 112 | True | nan | BOF:not cleared | DEAD |
| G1_0707__HM | NY-AM | SESSION-CANDIDATE | 554 | 793 | 915 | 249 | 557 | 1,733 | 145 | 2,329 | -224 | -159 | 1,108 | 92.10 | 2,329 | 532 | 293 | True | nan | BOF:not cleared | DEAD |
| G1_0665__SM | ASIA | SESSION-CANDIDATE | 242 | 1,186 | 1,374 | 113 | 330 | 1,554 | 96.79 | 1,244 | 620 | 526 | 1,179 | 659 | 1,244 | 913 | 39.61 | True | nan | BOF:not cleared | DEAD |
| G1_0456__HM | NY-AM | SESSION-CANDIDATE | 554 | 763 | 884 | 249 | 600 | 1,918 | 194 | 2,349 | -340 | -375 | 1,029 | 192 | 2,349 | 502 | 342 | True | nan | BOF:not cleared | DEAD |
| G1_0008__HM | NY-AM | SESSION-CANDIDATE | 554 | 779 | 904 | 249 | 714 | 1,945 | 174 | 3,033 | -98.82 | 2.74 | 616 | 518 | 3,033 | 544 | 484 | True | nan | BOF:not cleared | DEAD |
| G1_0206__HM | NY-AM | SESSION-CANDIDATE | 554 | 772 | 897 | 249 | 1,040 | 1,998 | 347 | 4,017 | -217 | -56.76 | 613 | 557 | 4,017 | 530 | 804 | True | nan | BOF:not cleared | DEAD |
| G1_0203__SM | ASIA | SESSION-CANDIDATE | 242 | 1,193 | 1,386 | 113 | 267 | 1,581 | 10.12 | 1,274 | 564 | 449 | 1,188 | 625 | 1,274 | 920 | -26.23 | False | nan | BOF:not cleared | DEAD |
| G1_0031__HM | ASIA | SESSION-CANDIDATE | 622 | 746 | 872 | 289 | 661 | 1,436 | 595 | 917 | -85.47 | -418 | 770 | 758 | 917 | 476 | 392 | True | nan | BOF:not cleared | DEAD |
| G1_0435__SM | ASIA | SESSION-CANDIDATE | 242 | 1,193 | 1,394 | 113 | 302 | 1,568 | 86.23 | 1,148 | 545 | 435 | 1,190 | 658 | 1,148 | 923 | 14.74 | True | nan | BOF:not cleared | DEAD |
| G1_0092__SM | ASIA | SESSION-CANDIDATE | 242 | 1,101 | 1,286 | 113 | 423 | 1,455 | 21.28 | 1,996 | 723 | 554 | 1,143 | 589 | 1,996 | 809 | 115 | True | nan | BOF:not cleared | DEAD |
| G1_0701__SM | ASIA | SESSION-CANDIDATE | 242 | 1,099 | 1,286 | 113 | 439 | 1,443 | 25.17 | 2,057 | 712 | 542 | 1,120 | 609 | 2,057 | 807 | 130 | True | nan | BOF:not cleared | DEAD |
| G1_0613__SM | ASIA | SESSION-CANDIDATE | 242 | 1,097 | 1,285 | 113 | 405 | 1,450 | 3.50 | 1,976 | 721 | 552 | 1,127 | 590 | 1,976 | 806 | 96.38 | True | nan | BOF:not cleared | DEAD |
| G1_0532__SM | ASIA | SESSION-CANDIDATE | 242 | 1,096 | 1,283 | 113 | 406 | 1,455 | 2.39 | 1,987 | 724 | 564 | 1,113 | 596 | 1,987 | 804 | 97.70 | True | nan | BOF:not cleared | DEAD |
| G1_0166__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 832 | 249 | 751 | 1,662 | 485 | 1,895 | 89.80 | 72.43 | 1,002 | 307 | 1,895 | 440 | 481 | True | nan | BOF:not cleared | DEAD |
| G1_0143__HM | NY-AM | SESSION-CANDIDATE | 554 | 648 | 759 | 249 | 570 | 1,563 | 191 | 2,201 | -342 | -420 | 861 | 210 | 2,201 | 374 | 297 | True | nan | BOF:not cleared | DEAD |
| G1_0945__HM | NY-AM | SESSION-CANDIDATE | 554 | 722 | 847 | 249 | 1,282 | 1,717 | 864 | 3,080 | -400 | -314 | 680 | 710 | 3,080 | 467 | 1,038 | True | nan | BOF:not cleared | DEAD |
| G1_0338__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 1,285 | 113 | 412 | 1,455 | 8.50 | 1,991 | 734 | 573 | 1,121 | 590 | 1,991 | 803 | 103 | True | nan | BOF:not cleared | DEAD |
| G1_0366__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 1,284 | 113 | 439 | 1,438 | 14.06 | 2,102 | 722 | 558 | 1,109 | 605 | 2,102 | 802 | 130 | True | nan | BOF:not cleared | DEAD |
| G1_0892__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 1,286 | 113 | 429 | 1,445 | 16.28 | 2,046 | 712 | 547 | 1,114 | 601 | 2,046 | 803 | 121 | True | nan | BOF:not cleared | DEAD |
| G1_0306__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,380 | 113 | 295 | 1,562 | 50.12 | 1,254 | 628 | 519 | 1,150 | 653 | 1,254 | 897 | 1.64 | True | nan | BOF:not cleared | DEAD |
| G1_0167__SM | ASIA | SESSION-CANDIDATE | 242 | 1,092 | 1,286 | 113 | 413 | 1,452 | 11.28 | 1,987 | 718 | 553 | 1,110 | 600 | 1,987 | 800 | 105 | True | nan | BOF:not cleared | DEAD |
| G1_0514__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 1,284 | 113 | 406 | 1,452 | 4.06 | 1,981 | 725 | 567 | 1,097 | 603 | 1,981 | 799 | 97.70 | True | nan | BOF:not cleared | DEAD |
| G1_0383__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 1,375 | 113 | 278 | 1,571 | 29.01 | 1,254 | 622 | 508 | 1,150 | 639 | 1,254 | 893 | -15.17 | False | nan | BOF:not cleared | DEAD |
| G1_0579__EM | NY | SESSION-CANDIDATE | 323 | 1,201 | 1,415 | 125 | 1,135 | 2,369 | 765 | 3,076 | -400 | -173 | 1,278 | 638 | 3,076 | 967 | 905 | True | nan | BOF:not cleared | DEAD |
| G1_0678__HM | NY-AM | SESSION-CANDIDATE | 554 | 732 | 862 | 249 | 448 | 1,566 | 158 | 1,694 | -187 | -175 | 954 | 186 | 1,694 | 458 | 173 | True | nan | BOF:not cleared | DEAD |
| G1_0098__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 1,287 | 113 | 431 | 1,468 | 26.83 | 2,011 | 735 | 578 | 1,091 | 621 | 2,011 | 800 | 125 | True | nan | BOF:not cleared | DEAD |
| G1_0716__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 1,284 | 113 | 419 | 1,440 | 2.94 | 2,046 | 727 | 560 | 1,112 | 591 | 2,046 | 797 | 110 | True | nan | BOF:not cleared | DEAD |
| G1_0160__SM | ASIA | SESSION-CANDIDATE | 242 | 1,092 | 1,289 | 113 | 414 | 1,448 | 16.28 | 1,972 | 722 | 553 | 1,122 | 594 | 1,972 | 800 | 106 | True | nan | BOF:not cleared | DEAD |
| G1_0658__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,754 | 2,071 | 80 | 384 | 3,131 | 195 | 1,359 | 646 | 873 | 1,856 | 692 | 1,359 | 1,535 | 147 | True | nan | BOF:not cleared | DEAD |
| G1_0946__EM | ASIA | SESSION-CANDIDATE | 249 | 1,343 | 1,586 | 128 | 569 | 2,602 | 2.33 | 3,025 | 225 | 223 | 942 | 911 | 3,025 | 1,105 | 315 | True | nan | BOF:not cleared | DEAD |
| G1_0713__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 1,289 | 113 | 437 | 1,449 | 34.06 | 2,013 | 708 | 540 | 1,107 | 614 | 2,013 | 800 | 131 | True | nan | BOF:not cleared | DEAD |
| G1_0399__HM | ASIA | SESSION-CANDIDATE | 622 | 862 | 1,019 | 289 | 1,393 | 1,621 | 1,254 | 1,935 | -53.35 | -348 | 778 | 1,184 | 1,935 | 619 | 1,163 | True | nan | BOF:not cleared | DEAD |
| G1_0917__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 1,288 | 113 | 458 | 1,451 | 57.39 | 2,024 | 716 | 547 | 1,117 | 615 | 2,024 | 797 | 152 | True | nan | BOF:not cleared | DEAD |
| G1_0123__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 1,289 | 113 | 413 | 1,452 | 11.28 | 1,987 | 720 | 555 | 1,111 | 596 | 1,987 | 798 | 105 | True | nan | BOF:not cleared | DEAD |
| G1_0389__SM | ASIA | SESSION-CANDIDATE | 242 | 1,088 | 1,287 | 113 | 430 | 1,445 | 24.61 | 2,017 | 712 | 554 | 1,099 | 607 | 2,017 | 796 | 122 | True | nan | BOF:not cleared | DEAD |
| G1_0565__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 1,289 | 113 | 405 | 1,447 | 4.61 | 1,974 | 722 | 554 | 1,116 | 587 | 1,974 | 796 | 96.82 | True | nan | BOF:not cleared | DEAD |
| G1_0022__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 1,289 | 113 | 405 | 1,447 | 4.61 | 1,974 | 722 | 554 | 1,116 | 587 | 1,974 | 796 | 96.82 | True | nan | BOF:not cleared | DEAD |
| G1_0838__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 1,288 | 113 | 404 | 1,447 | 1.28 | 1,978 | 719 | 549 | 1,116 | 585 | 1,978 | 795 | 95.05 | True | nan | BOF:not cleared | DEAD |
| G1_0880__SM | ASIA | SESSION-CANDIDATE | 242 | 1,086 | 1,288 | 113 | 406 | 1,446 | 4.61 | 1,978 | 719 | 549 | 1,116 | 587 | 1,978 | 795 | 97.70 | True | nan | BOF:not cleared | DEAD |
| G2_TH_LIVE_JADE_m20_r3_t8_s1__EM | ASIA | SESSION-CANDIDATE | 280 | 964 | 1,143 | 142 | 486 | 1,364 | 93.98 | 2,157 | -809 | -638 | 504 | 689 | 2,157 | 853 | 362 | True | nan | BOF:not cleared | DEAD |
| G1_0242__SM | ASIA | SESSION-CANDIDATE | 242 | 1,090 | 1,293 | 113 | 471 | 1,461 | 22.94 | 2,224 | 730 | 559 | 1,113 | 605 | 2,224 | 799 | 165 | True | nan | BOF:not cleared | DEAD |
| G1_0215__HM | NY-AM | SESSION-CANDIDATE | 554 | 788 | 936 | 249 | 1,132 | 2,007 | 433 | 4,135 | 22.31 | 151 | 821 | 467 | 4,135 | 554 | 906 | True | nan | BOF:not cleared | DEAD |
| G1_0829__EM | ASIA | SESSION-CANDIDATE | 249 | 1,334 | 1,585 | 128 | 591 | 2,458 | 88.35 | 2,771 | -46.13 | -21.12 | 1,318 | 585 | 2,771 | 1,092 | 332 | True | nan | BOF:not cleared | DEAD |
| G1_0449__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 1,289 | 113 | 426 | 1,442 | 0.17 | 2,091 | 714 | 545 | 1,110 | 587 | 2,091 | 793 | 117 | True | nan | BOF:not cleared | DEAD |
| G1_0815__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 1,289 | 113 | 426 | 1,442 | 0.17 | 2,091 | 714 | 545 | 1,110 | 587 | 2,091 | 793 | 117 | True | nan | BOF:not cleared | DEAD |
| G1_0224__SM | ASIA | SESSION-CANDIDATE | 242 | 1,083 | 1,287 | 113 | 451 | 1,452 | 47.94 | 2,031 | 736 | 567 | 1,078 | 639 | 2,031 | 793 | 146 | True | nan | BOF:not cleared | DEAD |
| G1_0408__SM | ASIA | SESSION-CANDIDATE | 242 | 1,086 | 1,293 | 113 | 437 | 1,449 | 34.06 | 2,013 | 709 | 540 | 1,107 | 608 | 2,013 | 795 | 131 | True | nan | BOF:not cleared | DEAD |
| G1_0372__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 1,292 | 113 | 437 | 1,454 | 37.94 | 2,000 | 726 | 562 | 1,104 | 609 | 2,000 | 793 | 132 | True | nan | BOF:not cleared | DEAD |
| G1_0164__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 1,293 | 113 | 416 | 1,447 | 2.39 | 2,033 | 713 | 544 | 1,111 | 588 | 2,033 | 794 | 107 | True | nan | BOF:not cleared | DEAD |
| G1_0733__HM | NY-AM | SESSION-CANDIDATE | 554 | 569 | 678 | 249 | 399 | 1,521 | 76.24 | 1,788 | -249 | -329 | 550 | 334 | 1,788 | 284 | 109 | True | nan | BOF:not cleared | DEAD |
| G1_0593__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 1,293 | 113 | 443 | 1,449 | 41.83 | 2,013 | 707 | 539 | 1,108 | 609 | 2,013 | 794 | 137 | True | nan | BOF:not cleared | DEAD |
| G1_0433__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 1,292 | 113 | 436 | 1,446 | 33.50 | 2,011 | 716 | 546 | 1,108 | 605 | 2,011 | 793 | 130 | True | nan | BOF:not cleared | DEAD |
| G1_0624__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 1,292 | 113 | 436 | 1,446 | 33.50 | 2,011 | 714 | 546 | 1,107 | 605 | 2,011 | 793 | 130 | True | nan | BOF:not cleared | DEAD |
| G1_0468__SM | ASIA | SESSION-CANDIDATE | 242 | 1,479 | 1,764 | 113 | 319 | 2,427 | 185 | 845 | 568 | 275 | 1,193 | 1,207 | 845 | 1,251 | 67.80 | True | nan | BOF:not cleared | DEAD |
| G1_0563__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 968 | 249 | 937 | 2,131 | 463 | 2,976 | -211 | -8.86 | 943 | 350 | 2,976 | 572 | 700 | True | nan | BOF:not cleared | DEAD |
| G1_0632__SM | ASIA | SESSION-CANDIDATE | 242 | 1,082 | 1,294 | 113 | 456 | 1,447 | 53.50 | 2,033 | 717 | 549 | 1,106 | 614 | 2,033 | 791 | 151 | True | nan | BOF:not cleared | DEAD |
| G1_0654__EM | ASIA | SESSION-CANDIDATE | 249 | 1,438 | 1,720 | 128 | 465 | 2,483 | 105 | 2,025 | 124 | -12.13 | 1,246 | 914 | 2,025 | 1,216 | 229 | True | nan | BOF:not cleared | DEAD |
| G1_0296__ST | ASIA | SESSION-CANDIDATE | 712 | 874 | 1,046 | 347 | 263 | 1,738 | 318 | 76.60 | 338 | 197 | 745 | 740 | 76.60 | 649 | 25.87 | True | nan | BOF:not cleared | DEAD |
| G1_0659__SM | ASIA | SESSION-CANDIDATE | 242 | 1,074 | 1,288 | 113 | 442 | 1,459 | 12.94 | 2,120 | 718 | 547 | 1,080 | 608 | 2,120 | 782 | 136 | True | nan | BOF:not cleared | DEAD |
| G1_0727__HM | NY-AM | SESSION-CANDIDATE | 554 | 893 | 1,072 | 249 | 1,211 | 2,258 | 644 | 3,649 | -78.37 | 119 | 947 | 554 | 3,649 | 667 | 993 | True | nan | BOF:not cleared | DEAD |
| G1_0236__SM | ASIA | SESSION-CANDIDATE | 242 | 1,082 | 1,300 | 113 | 462 | 1,445 | 47.94 | 2,081 | 732 | 566 | 1,113 | 604 | 2,081 | 792 | 156 | True | nan | BOF:not cleared | DEAD |
| G1_0918__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 1,295 | 113 | 443 | 1,464 | 22.39 | 2,087 | 741 | 582 | 1,092 | 601 | 2,087 | 787 | 137 | True | nan | BOF:not cleared | DEAD |
| G1_0508__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,770 | 2,127 | 80 | 878 | 2,932 | 702 | 1,782 | 848 | 1,018 | 2,045 | 841 | 1,782 | 1,564 | 658 | True | nan | BOF:not cleared | DEAD |
| G1_0712__HM | NY-AM | SESSION-CANDIDATE | 554 | 729 | 878 | 249 | 742 | 1,928 | 332 | 2,503 | -317 | -325 | 786 | 420 | 2,503 | 467 | 483 | True | nan | BOF:not cleared | DEAD |
| G1_0802__HM | NY-AM | SESSION-CANDIDATE | 554 | 741 | 892 | 249 | 903 | 2,020 | 397 | 3,077 | 12.97 | 143 | 890 | 323 | 3,077 | 495 | 662 | True | nan | BOF:not cleared | DEAD |
| G1_0278__SM | ASIA | SESSION-CANDIDATE | 242 | 1,079 | 1,299 | 113 | 435 | 1,452 | 23.50 | 2,046 | 733 | 570 | 1,082 | 614 | 2,046 | 787 | 129 | True | nan | BOF:not cleared | DEAD |
| G1_0149__HM | NY-AM | SESSION-CANDIDATE | 554 | 799 | 965 | 249 | 1,113 | 2,066 | 408 | 4,143 | 195 | 384 | 740 | 522 | 4,143 | 566 | 889 | True | nan | BOF:not cleared | DEAD |
| G1_0875__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 1,302 | 113 | 454 | 1,445 | 37.94 | 2,081 | 741 | 576 | 1,113 | 594 | 2,081 | 788 | 148 | True | nan | BOF:not cleared | DEAD |
| G1_0302__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 1,304 | 113 | 453 | 1,448 | 36.83 | 2,081 | 729 | 563 | 1,110 | 596 | 2,081 | 788 | 147 | True | nan | BOF:not cleared | DEAD |
| G1_0451__HM | NY-AM | SESSION-CANDIDATE | 554 | 840 | 1,016 | 249 | 800 | 2,279 | 159 | 3,554 | 33.98 | 214 | 956 | 255 | 3,554 | 612 | 571 | True | nan | BOF:not cleared | DEAD |
| G1_0860__SM | ASIA | SESSION-CANDIDATE | 242 | 1,073 | 1,301 | 113 | 443 | 1,451 | 34.61 | 2,041 | 731 | 559 | 1,094 | 606 | 2,041 | 783 | 137 | True | nan | BOF:not cleared | DEAD |
| G1_0711__HM | NY-AM | SESSION-CANDIDATE | 554 | 748 | 907 | 249 | 943 | 2,115 | 269 | 3,839 | 423 | 699 | 612 | 468 | 3,839 | 503 | 709 | True | nan | BOF:not cleared | DEAD |
| G1_0937__EM | NY | SESSION-CANDIDATE | 323 | 679 | 824 | 125 | 501 | 1,630 | 256 | 1,790 | -297 | -127 | 406 | 551 | 1,790 | 379 | 198 | True | nan | BOF:not cleared | DEAD |
| G1_0865__SM | ASIA | SESSION-CANDIDATE | 242 | 1,076 | 1,305 | 113 | 452 | 1,447 | 37.94 | 2,072 | 726 | 562 | 1,108 | 594 | 2,072 | 784 | 146 | True | nan | BOF:not cleared | DEAD |
| G1_0610__SM | ASIA | SESSION-CANDIDATE | 242 | 1,077 | 1,308 | 113 | 479 | 1,441 | 72.94 | 2,067 | 708 | 542 | 1,114 | 607 | 2,067 | 787 | 173 | True | nan | BOF:not cleared | DEAD |
| G1_0772__SM | ASIA | SESSION-CANDIDATE | 242 | 1,075 | 1,307 | 113 | 459 | 1,447 | 44.61 | 2,081 | 732 | 569 | 1,110 | 594 | 2,081 | 785 | 153 | True | nan | BOF:not cleared | DEAD |
| G1_0710__SM | ASIA | SESSION-CANDIDATE | 242 | 1,074 | 1,306 | 113 | 446 | 1,448 | 30.17 | 2,072 | 725 | 558 | 1,107 | 589 | 2,072 | 782 | 140 | True | nan | BOF:not cleared | DEAD |
| G1_0533__HM | NY-AM | SESSION-CANDIDATE | 554 | 580 | 706 | 249 | 645 | 1,713 | 327 | 2,011 | -514 | -607 | 691 | 334 | 2,011 | 301 | 369 | True | nan | BOF:not cleared | DEAD |
| G1_0539__SM | ASIA | SESSION-CANDIDATE | 242 | 1,073 | 1,307 | 113 | 454 | 1,445 | 37.94 | 2,081 | 741 | 576 | 1,113 | 587 | 2,081 | 783 | 148 | True | nan | BOF:not cleared | DEAD |
| G1_0567__HM | NY-AM | SESSION-CANDIDATE | 554 | 676 | 823 | 249 | 1,209 | 1,817 | 731 | 3,261 | -242 | -170 | 580 | 691 | 3,261 | 434 | 977 | True | nan | BOF:not cleared | DEAD |
| G1_0293__SM | ASIA | SESSION-CANDIDATE | 242 | 1,397 | 1,703 | 113 | 198 | 2,180 | 5.51 | 952 | 851 | 587 | 1,336 | 870 | 952 | 1,162 | -62.38 | False | nan | BOF:not cleared | DEAD |
| G1_0100__EM | ASIA | SESSION-CANDIDATE | 249 | 1,348 | 1,647 | 128 | 796 | 2,596 | 389 | 2,560 | -140 | -324 | 1,492 | 756 | 2,560 | 1,121 | 560 | True | nan | BOF:not cleared | DEAD |
| G1_0915__SM | ASIA | SESSION-CANDIDATE | 242 | 1,070 | 1,310 | 113 | 455 | 1,447 | 40.17 | 2,081 | 730 | 564 | 1,106 | 590 | 2,081 | 780 | 150 | True | nan | BOF:not cleared | DEAD |
| G1_0241__SM | ASIA | SESSION-CANDIDATE | 242 | 1,070 | 1,310 | 113 | 455 | 1,447 | 40.17 | 2,081 | 732 | 564 | 1,108 | 590 | 2,081 | 780 | 150 | True | nan | BOF:not cleared | DEAD |
| G1_0692__HM | ASIA | SESSION-CANDIDATE | 622 | 842 | 1,031 | 289 | 1,676 | 1,545 | 1,441 | 2,590 | 239 | -164 | 768 | 1,315 | 2,590 | 599 | 1,451 | True | nan | BOF:not cleared | DEAD |
| G1_0715__SM | ASIA | SESSION-CANDIDATE | 242 | 1,607 | 1,969 | 113 | 410 | 2,775 | 234 | 1,098 | 1,159 | 1,105 | 1,441 | 1,069 | 1,098 | 1,376 | 162 | True | nan | BOF:not cleared | DEAD |
| G1_0947__HM | ASIA | SESSION-CANDIDATE | 622 | 846 | 1,036 | 289 | 1,520 | 1,559 | 1,407 | 1,962 | -8.14 | -392 | 792 | 1,264 | 1,962 | 601 | 1,290 | True | nan | BOF:not cleared | DEAD |
| G1_0218__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,642 | 2,016 | 80 | 518 | 2,714 | 307 | 1,606 | 423 | 465 | 1,849 | 712 | 1,606 | 1,399 | 264 | True | nan | BOF:not cleared | DEAD |
| G2_m20_r3_t4_s1__EM | ASIA | SESSION-CANDIDATE | 281 | 910 | 1,118 | 142 | 624 | 1,367 | 186 | 2,489 | -676 | -485 | 455 | 706 | 2,489 | 799 | 500 | True | nan | BOF:not cleared | DEAD |
| G1_0253__HM | NY-AM | SESSION-CANDIDATE | 554 | 743 | 914 | 249 | 750 | 2,096 | 82.98 | 3,614 | 303 | 497 | 761 | 273 | 3,614 | 509 | 517 | True | nan | BOF:not cleared | DEAD |
| G1_0598__EM | ASIA | SESSION-CANDIDATE | 249 | 1,264 | 1,554 | 128 | 567 | 2,390 | 159 | 2,338 | -18.86 | -197 | 974 | 977 | 2,338 | 1,029 | 323 | True | nan | BOF:not cleared | DEAD |
| G1_0319__SM | ASIA | SESSION-CANDIDATE | 242 | 1,051 | 1,293 | 113 | 423 | 1,457 | 9.61 | 2,039 | 706 | 547 | 1,088 | 559 | 2,039 | 759 | 114 | True | nan | BOF:not cleared | DEAD |
| G1_0801__SM | ASIA | SESSION-CANDIDATE | 242 | 1,068 | 1,316 | 113 | 435 | 1,487 | 7.39 | 2,107 | 735 | 571 | 1,092 | 583 | 2,107 | 781 | 129 | True | nan | BOF:not cleared | DEAD |
| G1_0807__HM | ASIA | SESSION-CANDIDATE | 622 | 842 | 1,038 | 289 | 962 | 1,420 | 864 | 1,345 | -317 | -548 | 524 | 1,130 | 1,345 | 613 | 733 | True | nan | BOF:not cleared | DEAD |
| G1_0089__HM | NY-AM | SESSION-CANDIDATE | 554 | 813 | 1,002 | 249 | 966 | 2,085 | 430 | 3,273 | -79.27 | 180 | 973 | 286 | 3,273 | 568 | 727 | True | nan | BOF:not cleared | DEAD |
| G1_0429__SM | ASIA | SESSION-CANDIDATE | 242 | 1,059 | 1,307 | 113 | 457 | 1,439 | 22.94 | 2,154 | 734 | 561 | 1,079 | 596 | 2,154 | 768 | 151 | True | nan | BOF:not cleared | DEAD |
| G1_0445__HM | NY-AM | SESSION-CANDIDATE | 554 | 778 | 961 | 249 | 769 | 2,086 | 106 | 3,623 | 397 | 596 | 733 | 360 | 3,623 | 545 | 537 | True | nan | BOF:not cleared | DEAD |
| G1_0735__HM | NY-AM | SESSION-CANDIDATE | 554 | 661 | 817 | 249 | 1,260 | 1,843 | 649 | 3,886 | -242 | -145 | 569 | 628 | 3,886 | 408 | 1,019 | True | nan | BOF:not cleared | DEAD |
| G1_0379__HM | NY-AM | SESSION-CANDIDATE | 554 | 823 | 1,018 | 249 | 912 | 2,133 | 306 | 3,517 | 169 | 466 | 950 | 256 | 3,517 | 586 | 674 | True | nan | BOF:not cleared | DEAD |
| G1_0441__SM | ASIA | SESSION-CANDIDATE | 242 | 1,057 | 1,309 | 113 | 444 | 1,436 | 19.06 | 2,104 | 751 | 582 | 1,073 | 595 | 2,104 | 765 | 135 | True | nan | BOF:not cleared | DEAD |
| G1_0305__SM | ASIA | SESSION-CANDIDATE | 242 | 1,061 | 1,315 | 113 | 467 | 1,456 | 22.39 | 2,204 | 734 | 568 | 1,098 | 576 | 2,204 | 769 | 161 | True | nan | BOF:not cleared | DEAD |
| G1_0145__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 1,303 | 113 | 467 | 1,494 | 71.28 | 2,017 | 681 | 496 | 1,090 | 603 | 2,017 | 760 | 168 | True | nan | BOF:not cleared | DEAD |
| G1_0617__HM | NY-AM | SESSION-CANDIDATE | 554 | 624 | 773 | 249 | 724 | 1,541 | 344 | 2,356 | -330 | -406 | 869 | 246 | 2,356 | 350 | 454 | True | nan | BOF:not cleared | DEAD |
| G1_0025__EM | ASIA | SESSION-CANDIDATE | 249 | 1,333 | 1,653 | 128 | 797 | 2,513 | 149 | 3,606 | 519 | 519 | 895 | 1,032 | 3,606 | 1,092 | 548 | True | nan | BOF:not cleared | DEAD |
| G1_0711__SM | ASIA | SESSION-CANDIDATE | 242 | 1,702 | 2,112 | 113 | 475 | 3,298 | 409 | 736 | 741 | 625 | 1,376 | 1,359 | 736 | 1,496 | 254 | True | nan | BOF:not cleared | DEAD |
| G1_0480__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 1,306 | 113 | 474 | 1,442 | 66.28 | 2,067 | 724 | 559 | 1,074 | 605 | 2,067 | 759 | 168 | True | nan | BOF:not cleared | DEAD |
| G1_0430__HM | NY-AM | SESSION-CANDIDATE | 554 | 884 | 1,104 | 249 | 1,150 | 2,225 | 652 | 3,291 | 297 | 416 | 886 | 667 | 3,291 | 665 | 935 | True | nan | BOF:not cleared | DEAD |
| G1_0867__EM | ASIA | SESSION-CANDIDATE | 249 | 1,257 | 1,570 | 128 | 772 | 2,195 | 370 | 2,515 | -3.41 | -197 | 963 | 1,103 | 2,515 | 1,018 | 526 | True | nan | BOF:not cleared | DEAD |
| G1_0507__HM | NY-AM | SESSION-CANDIDATE | 554 | 650 | 814 | 249 | 1,242 | 1,841 | 627 | 3,886 | -240 | -143 | 555 | 615 | 3,886 | 397 | 1,001 | True | nan | BOF:not cleared | DEAD |
| G1_0468__EM | ASIA | SESSION-CANDIDATE | 249 | 1,242 | 1,558 | 128 | 463 | 2,183 | 112 | 1,985 | -156 | -385 | 1,308 | 664 | 1,985 | 1,007 | 214 | True | nan | BOF:not cleared | DEAD |
| G1_0246__SM | NY | SESSION-CANDIDATE | 328 | 1,055 | 1,325 | 131 | 1,711 | 2,931 | 1,371 | 3,599 | -0.84 | -27.27 | 1,109 | 1,081 | 3,599 | 819 | 1,482 | True | nan | BOF:not cleared | DEAD |
| G1_0365__HM | NY-AM | SESSION-CANDIDATE | 554 | 785 | 985 | 249 | 1,033 | 2,078 | 474 | 3,437 | 167 | 251 | 853 | 487 | 3,437 | 558 | 812 | True | nan | BOF:not cleared | DEAD |
| G1_0830__HM | NY-AM | SESSION-CANDIDATE | 554 | 699 | 879 | 249 | 508 | 1,918 | 45.26 | 2,494 | 165 | 213 | 839 | 194 | 2,494 | 444 | 249 | True | nan | BOF:not cleared | DEAD |
| G1_0445__SM | ASIA | SESSION-CANDIDATE | 242 | 1,379 | 1,734 | 113 | 334 | 2,181 | 77.13 | 1,339 | 806 | 539 | 1,318 | 898 | 1,339 | 1,145 | 76.49 | True | nan | BOF:not cleared | DEAD |
| G1_0850__HM | NY-AM | SESSION-CANDIDATE | 554 | 575 | 724 | 249 | 222 | 1,588 | 74.52 | 859 | -116 | -200 | 644 | 268 | 859 | 291 | -69.07 | False | nan | BOF:not cleared | DEAD |
| G1_0822__SM | ASIA | SESSION-CANDIDATE | 242 | 1,793 | 2,256 | 113 | 53.80 | 3,217 | 39.99 | 108 | 931 | 835 | 1,628 | 1,060 | 108 | 1,590 | -174 | False | nan | BOF:not cleared | DEAD |
| G1_0285__SM | ASIA | SESSION-CANDIDATE | 242 | 1,047 | 1,318 | 113 | 452 | 1,439 | 29.06 | 2,107 | 736 | 576 | 1,074 | 579 | 2,107 | 755 | 143 | True | nan | BOF:not cleared | DEAD |
| G1_0563__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,341 | 1,690 | 100 | 2,050 | 3,242 | 2,094 | 1,727 | 80.94 | 75.50 | 1,584 | 1,441 | 1,727 | 1,114 | 1,830 | True | nan | BOF:not cleared | DEAD |
| G1_0940__HM | NY-AM | SESSION-CANDIDATE | 554 | 701 | 885 | 249 | 1,048 | 1,998 | 336 | 4,108 | -316 | -152 | 557 | 498 | 4,108 | 458 | 812 | True | nan | BOF:not cleared | DEAD |
| G1_0454__EM | NY | SESSION-CANDIDATE | 323 | 791 | 1,000 | 125 | 608 | 1,962 | 273 | 2,367 | -489 | -357 | 459 | 678 | 2,367 | 498 | 319 | True | nan | BOF:not cleared | DEAD |
| G1_0476__HM | NY-AM | SESSION-CANDIDATE | 554 | 705 | 891 | 249 | 781 | 1,949 | 426 | 2,303 | -386 | -391 | 918 | 309 | 2,303 | 453 | 533 | True | nan | BOF:not cleared | DEAD |
| G1_0204__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 1,328 | 113 | 376 | 1,482 | 10.17 | 1,809 | 641 | 479 | 1,088 | 557 | 1,809 | 762 | 79.65 | True | nan | BOF:not cleared | DEAD |
| G1_0357__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,559 | 1,981 | 80 | 679 | 2,766 | 522 | 1,490 | 940 | 1,019 | 1,543 | 980 | 1,490 | 1,323 | 429 | True | nan | BOF:not cleared | DEAD |
| G1_0843__SM | ASIA | SESSION-CANDIDATE | 242 | 1,041 | 1,325 | 113 | 509 | 1,451 | 106 | 2,085 | 677 | 512 | 1,075 | 609 | 2,085 | 752 | 206 | True | nan | BOF:not cleared | DEAD |
| G1_0307__HM | NY-AM | SESSION-CANDIDATE | 554 | 796 | 1,014 | 249 | 975 | 2,134 | 369 | 3,578 | 221 | 326 | 719 | 563 | 3,578 | 576 | 758 | True | nan | BOF:not cleared | DEAD |
| G1_0170__EM | ASIA | SESSION-CANDIDATE | 249 | 1,199 | 1,530 | 128 | 680 | 2,336 | 322 | 2,233 | -166 | -370 | 949 | 1,013 | 2,233 | 960 | 434 | True | nan | BOF:not cleared | DEAD |
| G1_0500__SM | ASIA | SESSION-CANDIDATE | 242 | 1,033 | 1,318 | 113 | 482 | 1,516 | 57.39 | 2,144 | 726 | 559 | 1,075 | 577 | 2,144 | 741 | 179 | True | nan | BOF:not cleared | DEAD |
| G1_0867__HM | ASIA | SESSION-CANDIDATE | 622 | 803 | 1,024 | 289 | 1,611 | 1,582 | 1,388 | 2,484 | 164 | -220 | 891 | 1,136 | 2,484 | 553 | 1,378 | True | nan | BOF:not cleared | DEAD |
| G1_0246__EM | ASIA | SESSION-CANDIDATE | 249 | 1,207 | 1,540 | 128 | 510 | 2,012 | 32.47 | 2,581 | 54.47 | -174 | 1,031 | 829 | 2,581 | 963 | 253 | True | nan | BOF:not cleared | DEAD |
| G1_0474__HM | NY-AM | SESSION-CANDIDATE | 554 | 698 | 892 | 249 | 752 | 2,060 | 204 | 3,110 | 213 | 350 | 866 | 202 | 3,110 | 450 | 506 | True | nan | BOF:not cleared | DEAD |
| G1_0067__EM | ASIA | SESSION-CANDIDATE | 249 | 1,189 | 1,519 | 128 | 489 | 2,119 | 52.66 | 2,381 | -32.50 | -273 | 1,003 | 845 | 2,381 | 947 | 235 | True | nan | BOF:not cleared | DEAD |
| G1_0021__HM | NY-AM | SESSION-CANDIDATE | 554 | 722 | 923 | 249 | 989 | 2,125 | 317 | 3,881 | -110 | 7.41 | 792 | 345 | 3,881 | 484 | 758 | True | nan | BOF:not cleared | DEAD |
| G1_0155__SM | ASIA | SESSION-CANDIDATE | 242 | 1,268 | 1,621 | 113 | 283 | 2,255 | 142 | 835 | 843 | 584 | 1,151 | 932 | 835 | 1,031 | 25.13 | True | nan | BOF:not cleared | DEAD |
| G3_DIV_w60__EM | NY | SESSION-CANDIDATE | 323 | 997 | 1,276 | 125 | 911 | 2,542 | 464 | 3,259 | -230 | -164 | 1,058 | 544 | 3,259 | 826 | 747 | True | nan | BOF:not cleared | DEAD |
| G1_0654__HM | NY-AM | SESSION-CANDIDATE | 554 | 774 | 993 | 249 | 685 | 2,108 | 14.86 | 3,565 | 71.38 | 197 | 765 | 299 | 3,565 | 546 | 454 | True | nan | BOF:not cleared | DEAD |
| G1_0752__HM | NY-AM | SESSION-CANDIDATE | 554 | 653 | 838 | 249 | 1,155 | 1,882 | 654 | 3,308 | -72.94 | 13.40 | 671 | 545 | 3,308 | 411 | 922 | True | nan | BOF:not cleared | DEAD |
| G1_0508__HM | ASIA | SESSION-CANDIDATE | 622 | 860 | 1,104 | 289 | 1,732 | 1,630 | 1,630 | 2,128 | -178 | -373 | 675 | 1,382 | 2,128 | 643 | 1,529 | True | nan | BOF:not cleared | DEAD |
| G1_0238__HM | NY-AM | SESSION-CANDIDATE | 554 | 819 | 1,052 | 249 | 1,169 | 2,126 | 586 | 3,671 | 15.11 | 190 | 958 | 436 | 3,671 | 598 | 952 | True | nan | BOF:not cleared | DEAD |
| G1_0151__HM | NY-AM | SESSION-CANDIDATE | 554 | 657 | 844 | 249 | 1,192 | 1,810 | 697 | 3,321 | -120 | -45.06 | 673 | 572 | 3,321 | 412 | 958 | True | nan | BOF:not cleared | DEAD |
| G3_IMB_t70_w30_g1__HM | NY-AM | SESSION-CANDIDATE | 554 | 699 | 898 | 249 | 881 | 2,071 | 446 | 2,749 | 252 | 374 | 563 | 603 | 2,749 | 480 | 662 | True | nan | BOF:not cleared | DEAD |
| G1_0238__SM | ASIA | SESSION-CANDIDATE | 242 | 1,697 | 2,182 | 113 | 392 | 3,244 | 364 | 504 | 772 | 660 | 1,328 | 1,375 | 504 | 1,497 | 171 | True | nan | BOF:not cleared | DEAD |
| G1_0003__HM | NY-AM | SESSION-CANDIDATE | 554 | 731 | 940 | 249 | 512 | 1,728 | 54.00 | 2,481 | 397 | 352 | 765 | 371 | 2,481 | 481 | 262 | True | nan | BOF:not cleared | DEAD |
| G3_SESSEND_ASIA_x30__HM | ASIA | SESSION-CANDIDATE | 622 | 877 | 1,129 | 289 | 1,186 | 1,835 | 822 | 2,606 | -102 | -252 | 434 | 1,198 | 2,606 | 665 | 977 | True | nan | BOF:not cleared | DEAD |
| G1_0912__HM | NY-AM | SESSION-CANDIDATE | 554 | 563 | 726 | 249 | 902 | 1,648 | 664 | 1,927 | -293 | -380 | 721 | 462 | 1,927 | 287 | 633 | True | nan | BOF:not cleared | DEAD |
| G1_0468__HM | NY-AM | SESSION-CANDIDATE | 554 | 742 | 958 | 249 | 927 | 2,084 | 440 | 3,020 | 198 | 371 | 647 | 552 | 3,020 | 513 | 702 | True | nan | BOF:not cleared | DEAD |
| G1_0050__HM | NY-AM | SESSION-CANDIDATE | 554 | 711 | 919 | 249 | 1,054 | 2,059 | 344 | 4,106 | 35.55 | 244 | 705 | 383 | 4,106 | 476 | 827 | True | nan | BOF:not cleared | DEAD |
| G1_0008__SM | ASIA | SESSION-CANDIDATE | 242 | 1,019 | 1,317 | 113 | 315 | 2,112 | 199 | 767 | 301 | 261 | 855 | 735 | 767 | 761 | 42.26 | True | nan | BOF:not cleared | DEAD |
| G1_0887__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 918 | 249 | 865 | 2,052 | 412 | 2,810 | -81.29 | -34.97 | 965 | 260 | 2,810 | 462 | 622 | True | nan | BOF:not cleared | DEAD |
| G1_0725__HM | NY-AM | SESSION-CANDIDATE | 554 | 745 | 963 | 249 | 919 | 2,067 | 328 | 3,460 | 213 | 427 | 823 | 323 | 3,460 | 502 | 677 | True | nan | BOF:not cleared | DEAD |
| G1_0941__EM | NY | SESSION-CANDIDATE | 323 | 819 | 1,062 | 125 | 610 | 2,024 | 245 | 2,529 | -355 | -184 | 574 | 576 | 2,529 | 526 | 321 | True | nan | BOF:not cleared | DEAD |
| G1_0620__HM | NY-AM | SESSION-CANDIDATE | 554 | 678 | 880 | 249 | 759 | 1,907 | 333 | 2,591 | -283 | -319 | 863 | 300 | 2,591 | 414 | 499 | True | nan | BOF:not cleared | DEAD |
| G1_0502__HM | NY-AM | SESSION-CANDIDATE | 554 | 717 | 931 | 249 | 961 | 2,068 | 313 | 3,747 | -73.24 | 87.38 | 703 | 395 | 3,747 | 481 | 730 | True | nan | BOF:not cleared | DEAD |
| G1_0780__HM | NY-AM | SESSION-CANDIDATE | 554 | 742 | 965 | 249 | 892 | 2,008 | 319 | 3,356 | 227 | 320 | 755 | 440 | 3,356 | 506 | 662 | True | nan | BOF:not cleared | DEAD |
| G1_0508__SM | ASIA | SESSION-CANDIDATE | 242 | 1,704 | 2,219 | 113 | 616 | 3,165 | 658 | 449 | 742 | 626 | 1,550 | 1,325 | 449 | 1,501 | 394 | True | nan | BOF:not cleared | DEAD |
| G1_0418__HM | NY-AM | SESSION-CANDIDATE | 554 | 731 | 952 | 249 | 923 | 1,995 | 330 | 3,471 | -199 | -161 | 939 | 267 | 3,471 | 476 | 676 | True | nan | BOF:not cleared | DEAD |
| G1_0802__EM | ASIA | SESSION-CANDIDATE | 249 | 1,322 | 1,723 | 128 | 748 | 2,647 | 39.01 | 3,823 | 43.26 | 69.51 | 946 | 868 | 3,823 | 1,097 | 515 | True | nan | BOF:not cleared | DEAD |
| G1_0785__SM | ASIA | SESSION-CANDIDATE | 242 | 1,459 | 1,903 | 113 | 290 | 2,860 | 49.91 | 1,228 | 1,250 | 1,206 | 1,302 | 903 | 1,228 | 1,220 | 32.26 | True | nan | BOF:not cleared | DEAD |
| G2_m20_r3_t8_s2.0__EM | ASIA | SESSION-CANDIDATE | 280 | 886 | 1,156 | 142 | 525 | 1,430 | 15.29 | 2,694 | -810 | -637 | 463 | 581 | 2,694 | 773 | 400 | True | nan | BOF:not cleared | DEAD |
| G2_m20_r3_t8_s0.5__EM | ASIA | SESSION-CANDIDATE | 280 | 877 | 1,145 | 142 | 489 | 1,335 | 85.29 | 2,209 | -836 | -669 | 448 | 623 | 2,209 | 765 | 365 | True | nan | BOF:not cleared | DEAD |
| G2_m20_r2_t8_s1__EM | ASIA | SESSION-CANDIDATE | 280 | 849 | 1,111 | 142 | 443 | 1,384 | 1.38 | 2,326 | -810 | -640 | 464 | 528 | 2,326 | 739 | 322 | True | nan | BOF:not cleared | DEAD |
| G1_0336__EM | NY | SESSION-CANDIDATE | 323 | 825 | 1,080 | 125 | 611 | 2,034 | 252 | 2,497 | -365 | -188 | 601 | 557 | 2,497 | 534 | 324 | True | nan | BOF:not cleared | DEAD |
| G1_0738__SM | ASIA | SESSION-CANDIDATE | 242 | 1,668 | 2,184 | 113 | 495 | 3,052 | 365 | 1,002 | 875 | 738 | 1,497 | 1,197 | 1,002 | 1,455 | 261 | True | nan | BOF:not cleared | DEAD |
| G1_0488__HM | NY-AM | SESSION-CANDIDATE | 554 | 617 | 808 | 249 | 430 | 1,471 | 94.46 | 1,872 | -63.97 | -130 | 841 | 151 | 1,872 | 340 | 148 | True | nan | BOF:not cleared | DEAD |
| G1_0722__HM | NY-AM | SESSION-CANDIDATE | 554 | 833 | 1,091 | 249 | 1,271 | 2,084 | 869 | 3,000 | 43.76 | 250 | 921 | 611 | 3,000 | 612 | 1,059 | True | nan | BOF:not cleared | DEAD |
| G1_0026__HM | NY-AM | SESSION-CANDIDATE | 554 | 728 | 955 | 249 | 658 | 1,883 | 148 | 2,851 | 301 | 441 | 851 | 232 | 2,851 | 470 | 402 | True | nan | BOF:not cleared | DEAD |
| G3_IMB_t70_w60_g1__HM | NY-AM | SESSION-CANDIDATE | 554 | 878 | 1,152 | 249 | 970 | 2,239 | 392 | 3,455 | 250 | 497 | 719 | 612 | 3,455 | 669 | 763 | True | nan | BOF:not cleared | DEAD |
| G1_0166__SM | ASIA | SESSION-CANDIDATE | 242 | 1,595 | 2,095 | 113 | 343 | 2,828 | 157 | 1,070 | 1,182 | 1,069 | 1,554 | 944 | 1,070 | 1,373 | 97.43 | True | nan | BOF:not cleared | DEAD |
| G1_0321__SM | ASIA | SESSION-CANDIDATE | 242 | 1,252 | 1,643 | 113 | 468 | 2,643 | 8.22 | 2,265 | 796 | 928 | 858 | 882 | 2,265 | 1,013 | 210 | True | nan | BOF:not cleared | DEAD |
| G1_0837__SM | ASIA | SESSION-CANDIDATE | 242 | 1,426 | 1,878 | 113 | 637 | 2,491 | 432 | 1,437 | 1,425 | 1,337 | 1,157 | 1,226 | 1,437 | 1,202 | 394 | True | nan | BOF:not cleared | DEAD |
| G1_0238__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,644 | 2,168 | 80 | 433 | 2,695 | 429 | 451 | 1,188 | 1,354 | 1,614 | 939 | 451 | 1,434 | 204 | True | nan | BOF:not cleared | DEAD |
| G1_0851__EM | NY | SESSION-CANDIDATE | 323 | 884 | 1,166 | 125 | 1,121 | 2,089 | 553 | 4,107 | -419 | -109 | 752 | 540 | 4,107 | 607 | 862 | True | nan | BOF:not cleared | DEAD |
| G1_0649__EM | ASIA | SESSION-CANDIDATE | 249 | 1,189 | 1,570 | 128 | 671 | 2,407 | 139 | 2,973 | 245 | 224 | 697 | 1,014 | 2,973 | 945 | 419 | True | nan | BOF:not cleared | DEAD |
| G1_0059__HM | NY-AM | SESSION-CANDIDATE | 554 | 553 | 731 | 249 | 553 | 1,605 | 47.70 | 2,724 | 279 | 287 | 760 | 98.81 | 2,724 | 260 | 267 | True | nan | BOF:not cleared | DEAD |
| G2_m20_r2_t8_s2__EM | ASIA | SESSION-CANDIDATE | 280 | 844 | 1,115 | 142 | 507 | 1,363 | 88.33 | 2,292 | -825 | -656 | 472 | 560 | 2,292 | 729 | 386 | True | nan | BOF:not cleared | DEAD |
| G1_0580__EM | ASIA | SESSION-CANDIDATE | 249 | 1,046 | 1,383 | 128 | 690 | 2,117 | 157 | 2,998 | 333 | 205 | 820 | 817 | 2,998 | 780 | 417 | True | nan | BOF:not cleared | DEAD |
| G1_0100__SM | ASIA | SESSION-CANDIDATE | 242 | 1,439 | 1,904 | 113 | 277 | 2,808 | 88.60 | 1,015 | 613 | 369 | 1,118 | 1,146 | 1,015 | 1,216 | 31.63 | True | nan | BOF:not cleared | DEAD |
| G1_0492__HM | NY-AM | SESSION-CANDIDATE | 554 | 695 | 919 | 249 | 760 | 1,969 | 376 | 2,412 | -29.90 | 37.70 | 798 | 363 | 2,412 | 453 | 522 | True | nan | BOF:not cleared | DEAD |
| G1_0651__HM | NY-AM | SESSION-CANDIDATE | 554 | 681 | 902 | 249 | 1,065 | 1,836 | 630 | 2,938 | -267 | -227 | 923 | 357 | 2,938 | 422 | 812 | True | nan | BOF:not cleared | DEAD |
| G1_0820__HM | NY-AM | SESSION-CANDIDATE | 554 | 578 | 766 | 249 | 670 | 1,764 | 482 | 1,479 | -424 | -500 | 634 | 455 | 1,479 | 309 | 403 | True | nan | BOF:not cleared | DEAD |
| G1_0343__HM | NY-AM | SESSION-CANDIDATE | 554 | 556 | 738 | 249 | 746 | 1,642 | 377 | 2,334 | 51.45 | 85.99 | 760 | 235 | 2,334 | 287 | 482 | True | nan | BOF:not cleared | DEAD |
| G1_0067__HM | NY-AM | SESSION-CANDIDATE | 554 | 675 | 896 | 249 | 904 | 1,902 | 430 | 2,942 | 215 | 381 | 511 | 584 | 2,942 | 441 | 674 | True | nan | BOF:not cleared | DEAD |
| G3_IMB_t70_w30_g0__HM | NY-AM | SESSION-CANDIDATE | 554 | 658 | 875 | 249 | 999 | 2,004 | 531 | 3,007 | 207 | 296 | 512 | 651 | 3,007 | 442 | 786 | True | nan | BOF:not cleared | DEAD |
| G1_0545__EM | NY | SESSION-CANDIDATE | 323 | 841 | 1,119 | 125 | 852 | 2,288 | 387 | 3,294 | -191 | 42.50 | 566 | 654 | 3,294 | 555 | 574 | True | nan | BOF:not cleared | DEAD |
| G1_0598__HM | ASIA | SESSION-CANDIDATE | 622 | 793 | 1,055 | 289 | 1,466 | 1,727 | 1,148 | 2,704 | -77.49 | -467 | 911 | 988 | 2,704 | 548 | 1,236 | True | nan | BOF:not cleared | DEAD |
| G1_0567__HM | ASIA | SESSION-CANDIDATE | 622 | 775 | 1,032 | 289 | 1,285 | 1,550 | 1,044 | 2,226 | 31.45 | -287 | 555 | 1,162 | 2,226 | 533 | 1,053 | True | nan | BOF:not cleared | DEAD |
| G1_0009__HM | NY-AM | SESSION-CANDIDATE | 554 | 770 | 1,026 | 249 | 1,155 | 1,936 | 588 | 3,595 | 42.84 | 269 | 551 | 711 | 3,595 | 547 | 935 | True | nan | BOF:not cleared | DEAD |
| G1_0206__HM | ASIA | SESSION-CANDIDATE | 622 | 771 | 1,030 | 289 | 1,593 | 1,525 | 1,524 | 1,864 | 184 | -178 | 723 | 1,277 | 1,864 | 523 | 1,362 | True | nan | BOF:not cleared | DEAD |
| G1_0831__SM | ASIA | SESSION-CANDIDATE | 242 | 985 | 1,317 | 113 | 494 | 1,510 | 71.28 | 2,148 | 714 | 545 | 1,003 | 588 | 2,148 | 695 | 197 | True | nan | BOF:not cleared | DEAD |
| G1_0215__EM | ASIA | SESSION-CANDIDATE | 249 | 1,199 | 1,605 | 128 | 813 | 2,346 | 493 | 2,200 | -2.73 | -216 | 1,143 | 953 | 2,200 | 960 | 569 | True | nan | BOF:not cleared | DEAD |
| G1_0822__ST | ASIA | SESSION-CANDIDATE | 712 | 789 | 1,056 | 347 | 65.44 | 1,867 | 23.36 | 208 | 455 | 330 | 730 | 519 | 208 | 569 | -167 | False | nan | BOF:not cleared | DEAD |
| G2_m20_r2_t4_s1__EM | ASIA | SESSION-CANDIDATE | 281 | 802 | 1,075 | 142 | 520 | 1,419 | 38.34 | 2,570 | -707 | -514 | 405 | 529 | 2,570 | 692 | 398 | True | nan | BOF:not cleared | DEAD |
| G1_0502__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,182 | 1,586 | 100 | 1,521 | 3,640 | 1,601 | 939 | 481 | 499 | 1,368 | 1,176 | 939 | 957 | 1,298 | True | nan | BOF:not cleared | DEAD |
| G1_0508__HM | NY-AM | SESSION-CANDIDATE | 554 | 772 | 1,036 | 249 | 987 | 2,214 | 267 | 4,078 | 235 | 400 | 851 | 331 | 4,078 | 549 | 767 | True | nan | BOF:not cleared | DEAD |
| G1_0039__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,361 | 1,828 | 80 | 271 | 2,462 | 287 | 187 | -480 | -238 | 1,134 | 791 | 187 | 1,097 | -12.75 | False | nan | BOF:not cleared | DEAD |
| G1_0598__HM | NY-AM | SESSION-CANDIDATE | 554 | 660 | 887 | 249 | 1,173 | 1,931 | 728 | 3,089 | -89.29 | 2.36 | 707 | 555 | 3,089 | 420 | 943 | True | nan | BOF:not cleared | DEAD |
| G1_0580__SM | ASIA | SESSION-CANDIDATE | 242 | 1,227 | 1,650 | 113 | 515 | 2,461 | 408 | 937 | 1,032 | 1,078 | 976 | 1,007 | 937 | 968 | 249 | True | nan | BOF:not cleared | DEAD |
| G1_0077__SM | ASIA | SESSION-CANDIDATE | 242 | 1,175 | 1,582 | 113 | 268 | 2,100 | 104 | 911 | 1,272 | 1,029 | 811 | 1,122 | 911 | 924 | 1.61 | True | nan | BOF:not cleared | DEAD |
| G1_0515__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,579 | 113 | 273 | 2,102 | 111 | 907 | 1,272 | 1,027 | 823 | 1,112 | 907 | 921 | 6.48 | True | nan | BOF:not cleared | DEAD |
| G3_IMB_t70_w60_g0__HM | NY-AM | SESSION-CANDIDATE | 554 | 862 | 1,162 | 249 | 947 | 2,222 | 401 | 3,293 | 216 | 463 | 689 | 619 | 3,293 | 652 | 740 | True | nan | BOF:not cleared | DEAD |
| G1_0293__HM | NY-AM | SESSION-CANDIDATE | 554 | 661 | 891 | 249 | 879 | 1,917 | 403 | 2,922 | 118 | 269 | 510 | 555 | 2,922 | 427 | 649 | True | nan | BOF:not cleared | DEAD |
| G1_0736__HM | NY-AM | SESSION-CANDIDATE | 554 | 586 | 790 | 249 | 627 | 1,770 | 425 | 1,498 | -418 | -492 | 704 | 375 | 1,498 | 316 | 359 | True | nan | BOF:not cleared | DEAD |
| G1_0229__SM | ASIA | SESSION-CANDIDATE | 242 | 1,173 | 1,582 | 113 | 266 | 2,101 | 103 | 907 | 1,270 | 1,026 | 810 | 1,120 | 907 | 922 | -0.16 | False | nan | BOF:not cleared | DEAD |
| G1_0301__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,581 | 113 | 288 | 2,104 | 123 | 933 | 1,272 | 1,026 | 822 | 1,119 | 933 | 921 | 21.52 | True | nan | BOF:not cleared | DEAD |
| G1_0601__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,639 | 2,212 | 80 | 792 | 3,307 | 708 | 1,228 | 1,196 | 1,435 | 1,848 | 815 | 1,228 | 1,437 | 577 | True | nan | BOF:not cleared | DEAD |
| G1_0612__SM | ASIA | SESSION-CANDIDATE | 242 | 1,174 | 1,585 | 113 | 275 | 2,100 | 107 | 933 | 1,264 | 1,029 | 816 | 1,112 | 933 | 923 | 8.69 | True | nan | BOF:not cleared | DEAD |
| G1_0508__EM | NY | SESSION-CANDIDATE | 323 | 1,118 | 1,510 | 125 | 1,624 | 2,427 | 1,370 | 2,961 | -41.13 | 51.93 | 1,395 | 807 | 2,961 | 902 | 1,419 | True | nan | BOF:not cleared | DEAD |
| G1_0016__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 1,582 | 113 | 200 | 2,102 | 28.10 | 872 | 1,253 | 999 | 841 | 1,056 | 872 | 920 | -66.64 | False | nan | BOF:not cleared | DEAD |
| G1_0270__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 1,582 | 113 | 281 | 2,100 | 122 | 900 | 1,279 | 1,036 | 810 | 1,127 | 900 | 920 | 14.00 | True | nan | BOF:not cleared | DEAD |
| G1_0547__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,585 | 113 | 507 | 2,119 | 336 | 1,176 | 1,297 | 1,051 | 915 | 1,142 | 1,176 | 923 | 244 | True | nan | BOF:not cleared | DEAD |
| G1_0327__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 1,579 | 113 | 252 | 2,105 | 85.00 | 907 | 1,257 | 1,012 | 809 | 1,104 | 907 | 916 | -14.32 | False | nan | BOF:not cleared | DEAD |
| G1_0725__SM | ASIA | SESSION-CANDIDATE | 242 | 1,634 | 2,212 | 113 | 521 | 3,276 | 552 | 401 | 859 | 755 | 1,389 | 1,327 | 401 | 1,429 | 297 | True | nan | BOF:not cleared | DEAD |
| G1_0730__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 1,579 | 113 | 252 | 2,105 | 85.00 | 907 | 1,257 | 1,012 | 809 | 1,104 | 907 | 916 | -14.32 | False | nan | BOF:not cleared | DEAD |
| G1_0668__SM | ASIA | SESSION-CANDIDATE | 242 | 1,168 | 1,582 | 113 | 266 | 2,097 | 109 | 878 | 1,256 | 1,011 | 820 | 1,107 | 878 | 917 | -0.60 | False | nan | BOF:not cleared | DEAD |
| G1_0534__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 1,581 | 113 | 258 | 2,104 | 89.44 | 920 | 1,266 | 1,020 | 807 | 1,109 | 920 | 916 | -8.12 | False | nan | BOF:not cleared | DEAD |
| G1_0835__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 1,586 | 113 | 264 | 2,108 | 101 | 902 | 1,268 | 1,026 | 822 | 1,104 | 902 | 920 | -2.37 | False | nan | BOF:not cleared | DEAD |
| G1_0374__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,580 | 113 | 262 | 2,101 | 96.67 | 911 | 1,238 | 990 | 807 | 1,110 | 911 | 915 | -4.14 | False | nan | BOF:not cleared | DEAD |
| G1_0804__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 1,581 | 113 | 259 | 2,101 | 92.22 | 911 | 1,267 | 1,021 | 806 | 1,110 | 911 | 915 | -7.68 | False | nan | BOF:not cleared | DEAD |
| G1_0428__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 1,582 | 113 | 251 | 2,104 | 83.89 | 907 | 1,267 | 1,021 | 804 | 1,107 | 907 | 915 | -15.20 | False | nan | BOF:not cleared | DEAD |
| G1_0017__HM | ASIA | SESSION-CANDIDATE | 622 | 676 | 918 | 289 | 1,047 | 1,749 | 797 | 2,022 | -107 | -304 | 693 | 762 | 2,022 | 437 | 813 | True | nan | BOF:not cleared | DEAD |
| G1_0138__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 1,580 | 113 | 280 | 2,102 | 119 | 909 | 1,274 | 1,026 | 817 | 1,112 | 909 | 913 | 13.12 | True | nan | BOF:not cleared | DEAD |
| G1_0331__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,581 | 113 | 250 | 2,104 | 82.78 | 907 | 1,262 | 1,016 | 805 | 1,104 | 907 | 914 | -16.09 | False | nan | BOF:not cleared | DEAD |
| G1_0839__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,583 | 113 | 250 | 2,105 | 81.67 | 907 | 1,263 | 1,016 | 806 | 1,104 | 907 | 915 | -16.97 | False | nan | BOF:not cleared | DEAD |
| G1_0335__HM | NY-AM | SESSION-CANDIDATE | 554 | 654 | 889 | 249 | 1,239 | 1,798 | 734 | 3,409 | 297 | 477 | 671 | 560 | 3,409 | 415 | 1,009 | True | nan | BOF:not cleared | DEAD |
| G1_0615__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,582 | 113 | 254 | 2,102 | 86.11 | 911 | 1,265 | 1,018 | 806 | 1,106 | 911 | 914 | -12.55 | False | nan | BOF:not cleared | DEAD |
| G1_0622__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,582 | 113 | 254 | 2,102 | 86.11 | 911 | 1,265 | 1,018 | 806 | 1,106 | 911 | 914 | -12.55 | False | nan | BOF:not cleared | DEAD |
| G1_0813__HM | NY-AM | SESSION-CANDIDATE | 554 | 551 | 748 | 249 | 465 | 1,673 | 178 | 1,697 | -134 | -229 | 781 | 168 | 1,697 | 292 | 203 | True | nan | BOF:not cleared | DEAD |
| G1_0784__EM | NY | SESSION-CANDIDATE | 323 | 944 | 1,283 | 125 | 1,060 | 2,158 | 656 | 3,179 | -700 | -534 | 696 | 802 | 3,179 | 674 | 795 | True | nan | BOF:not cleared | DEAD |
| G1_0633__SM | ASIA | SESSION-CANDIDATE | 242 | 1,620 | 2,200 | 113 | 233 | 3,120 | 158 | 528 | 812 | 669 | 1,324 | 1,188 | 528 | 1,408 | -0.24 | False | nan | BOF:not cleared | DEAD |
| G1_0459__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 1,582 | 113 | 257 | 2,102 | 92.78 | 900 | 1,277 | 1,034 | 805 | 1,108 | 900 | 913 | -9.45 | False | nan | BOF:not cleared | DEAD |
| G1_0861__SM | ASIA | SESSION-CANDIDATE | 242 | 1,168 | 1,588 | 113 | 374 | 2,058 | 104 | 1,428 | 1,239 | 1,001 | 868 | 1,055 | 1,428 | 919 | 110 | True | nan | BOF:not cleared | DEAD |
| G1_0106__SM | ASIA | SESSION-CANDIDATE | 242 | 1,174 | 1,595 | 113 | 213 | 2,115 | 31.63 | 922 | 1,219 | 995 | 930 | 958 | 922 | 927 | -53.72 | False | nan | BOF:not cleared | DEAD |
| G1_0210__SM | ASIA | SESSION-CANDIDATE | 242 | 1,162 | 1,581 | 113 | 301 | 2,088 | 128 | 980 | 1,212 | 976 | 880 | 1,044 | 980 | 913 | 34.80 | True | nan | BOF:not cleared | DEAD |
| G1_0117__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,595 | 113 | 262 | 2,103 | 98.33 | 902 | 1,282 | 1,038 | 827 | 1,100 | 902 | 921 | -4.58 | False | nan | BOF:not cleared | DEAD |
| G1_0621__HM | NY-AM | SESSION-CANDIDATE | 554 | 562 | 765 | 249 | 517 | 1,479 | 287 | 1,502 | 31.13 | -25.61 | 719 | 282 | 1,502 | 277 | 230 | True | nan | BOF:not cleared | DEAD |
| G1_0817__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,586 | 113 | 276 | 2,100 | 116 | 902 | 1,270 | 1,026 | 824 | 1,104 | 902 | 915 | 9.58 | True | nan | BOF:not cleared | DEAD |
| G1_0914__HM | ASIA | SESSION-CANDIDATE | 622 | 762 | 1,038 | 289 | 1,395 | 1,631 | 1,141 | 2,384 | -152 | -456 | 707 | 1,061 | 2,384 | 521 | 1,167 | True | nan | BOF:not cleared | DEAD |
| G1_0952__HM | NY-AM | SESSION-CANDIDATE | 554 | 747 | 1,017 | 249 | 1,039 | 2,116 | 449 | 3,578 | 212 | 318 | 689 | 562 | 3,578 | 526 | 824 | True | nan | BOF:not cleared | DEAD |
| G1_0510__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,632 | 2,222 | 80 | 548 | 3,269 | 416 | 1,228 | 920 | 1,197 | 1,749 | 711 | 1,228 | 1,433 | 332 | True | nan | BOF:not cleared | DEAD |
| G1_0837__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 887 | 249 | 1,076 | 1,960 | 436 | 3,825 | -3.39 | 175 | 646 | 414 | 3,825 | 409 | 840 | True | nan | BOF:not cleared | DEAD |
| G1_0728__SM | ASIA | SESSION-CANDIDATE | 242 | 1,177 | 1,602 | 113 | 280 | 2,102 | 121 | 902 | 1,263 | 1,021 | 823 | 1,121 | 902 | 926 | 13.12 | True | nan | BOF:not cleared | DEAD |
| G1_0401__HM | ASIA | SESSION-CANDIDATE | 622 | 736 | 1,002 | 289 | 1,519 | 1,643 | 1,361 | 2,135 | 26.66 | -298 | 690 | 1,160 | 2,135 | 491 | 1,290 | True | nan | BOF:not cleared | DEAD |
| G1_0803__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 1,580 | 113 | 260 | 2,101 | 93.89 | 911 | 1,261 | 1,015 | 798 | 1,109 | 911 | 909 | -6.35 | False | nan | BOF:not cleared | DEAD |
| G1_0663__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 1,580 | 113 | 260 | 2,101 | 93.89 | 911 | 1,261 | 1,015 | 798 | 1,109 | 911 | 909 | -6.35 | False | nan | BOF:not cleared | DEAD |
| G1_0882__SM | ASIA | SESSION-CANDIDATE | 242 | 1,169 | 1,593 | 113 | 257 | 2,105 | 91.67 | 902 | 1,251 | 1,005 | 824 | 1,096 | 902 | 918 | -9.89 | False | nan | BOF:not cleared | DEAD |
| G1_0753__SM | ASIA | SESSION-CANDIDATE | 242 | 1,180 | 1,609 | 113 | 308 | 2,081 | 123 | 1,030 | 1,217 | 985 | 798 | 1,141 | 1,030 | 932 | 41.44 | True | nan | BOF:not cleared | DEAD |
| G1_0150__SM | ASIA | SESSION-CANDIDATE | 242 | 1,160 | 1,582 | 113 | 262 | 2,101 | 96.67 | 911 | 1,273 | 1,028 | 803 | 1,107 | 911 | 909 | -4.14 | False | nan | BOF:not cleared | DEAD |
| G1_0825__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,599 | 113 | 256 | 2,105 | 90.56 | 902 | 1,272 | 1,029 | 814 | 1,109 | 902 | 922 | -10.78 | False | nan | BOF:not cleared | DEAD |
| G1_0929__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 1,599 | 113 | 260 | 2,103 | 95.56 | 902 | 1,275 | 1,032 | 813 | 1,111 | 902 | 921 | -6.79 | False | nan | BOF:not cleared | DEAD |
| G1_0407__HM | NY-AM | SESSION-CANDIDATE | 554 | 549 | 749 | 249 | 182 | 1,244 | 49.76 | 749 | 4.26 | -15.01 | 800 | 54.28 | 749 | 245 | -126 | False | nan | BOF:not cleared | DEAD |
| G1_0053__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 1,585 | 113 | 354 | 2,067 | 186 | 1,011 | 1,251 | 1,003 | 870 | 1,091 | 1,011 | 910 | 87.45 | True | nan | BOF:not cleared | DEAD |
| G1_0483__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 1,593 | 113 | 266 | 2,104 | 104 | 902 | 1,273 | 1,026 | 823 | 1,102 | 902 | 915 | -0.16 | False | nan | BOF:not cleared | DEAD |
| G1_0298__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 1,581 | 113 | 260 | 2,101 | 93.89 | 911 | 1,262 | 1,016 | 795 | 1,109 | 911 | 906 | -6.35 | False | nan | BOF:not cleared | DEAD |
| G1_0486__SM | ASIA | SESSION-CANDIDATE | 242 | 1,169 | 1,597 | 113 | 302 | 2,113 | 171 | 815 | 1,251 | 1,016 | 824 | 1,129 | 815 | 922 | 38.25 | True | nan | BOF:not cleared | DEAD |
| G1_0431__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 1,595 | 113 | 265 | 2,103 | 103 | 902 | 1,250 | 998 | 824 | 1,102 | 902 | 917 | -1.04 | False | nan | BOF:not cleared | DEAD |
| G1_0571__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 1,589 | 113 | 249 | 2,103 | 81.67 | 902 | 1,262 | 1,015 | 813 | 1,094 | 902 | 912 | -17.86 | False | nan | BOF:not cleared | DEAD |
| G1_0012__HM | NY-AM | SESSION-CANDIDATE | 554 | 644 | 881 | 249 | 704 | 1,959 | 145 | 3,105 | -77.12 | 16.10 | 472 | 458 | 3,105 | 413 | 478 | True | nan | BOF:not cleared | DEAD |
| G1_0051__HM | ASIA | SESSION-CANDIDATE | 622 | 615 | 841 | 289 | 393 | 1,283 | 344 | 585 | -54.00 | -460 | 788 | 500 | 585 | 326 | 91.80 | True | nan | BOF:not cleared | DEAD |
| G1_0553__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 1,588 | 113 | 253 | 2,104 | 86.67 | 902 | 1,262 | 1,015 | 814 | 1,092 | 902 | 910 | -13.87 | False | nan | BOF:not cleared | DEAD |
| G1_0413__HM | ASIA | SESSION-CANDIDATE | 622 | 583 | 798 | 289 | 363 | 1,358 | 239 | 847 | -153 | -501 | 704 | 445 | 847 | 287 | 59.19 | True | nan | BOF:not cleared | DEAD |
| G1_0664__HM | NY-AM | SESSION-CANDIDATE | 554 | 774 | 1,059 | 249 | 1,436 | 2,191 | 864 | 3,896 | 54.77 | 119 | 752 | 757 | 3,896 | 555 | 1,228 | True | nan | BOF:not cleared | DEAD |
| G1_0910__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,594 | 113 | 266 | 2,101 | 103 | 902 | 1,275 | 1,027 | 820 | 1,102 | 902 | 914 | -0.60 | False | nan | BOF:not cleared | DEAD |
| G1_0134__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 1,596 | 113 | 251 | 2,104 | 85.00 | 902 | 1,264 | 1,018 | 816 | 1,097 | 902 | 915 | -15.20 | False | nan | BOF:not cleared | DEAD |
| G1_0924__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 1,596 | 113 | 251 | 2,104 | 85.00 | 902 | 1,264 | 1,018 | 816 | 1,097 | 902 | 915 | -15.20 | False | nan | BOF:not cleared | DEAD |
| G1_0901__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 1,592 | 113 | 264 | 2,103 | 102 | 900 | 1,253 | 1,008 | 821 | 1,095 | 900 | 912 | -2.37 | False | nan | BOF:not cleared | DEAD |
| G1_0603__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 1,592 | 113 | 264 | 2,103 | 102 | 900 | 1,253 | 1,008 | 821 | 1,095 | 900 | 912 | -2.37 | False | nan | BOF:not cleared | DEAD |
| G1_0595__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 1,592 | 113 | 264 | 2,103 | 102 | 900 | 1,253 | 1,008 | 821 | 1,095 | 900 | 912 | -2.37 | False | nan | BOF:not cleared | DEAD |
| G1_0834__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 1,595 | 113 | 249 | 2,106 | 81.67 | 902 | 1,264 | 1,019 | 817 | 1,091 | 902 | 914 | -17.86 | False | nan | BOF:not cleared | DEAD |
| G1_0581__SM | ASIA | SESSION-CANDIDATE | 242 | 1,267 | 1,735 | 113 | 419 | 2,280 | 266 | 1,015 | 902 | 942 | 1,076 | 890 | 1,015 | 1,006 | 146 | True | nan | BOF:not cleared | DEAD |
| G1_0103__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 1,582 | 113 | 265 | 2,098 | 100.00 | 909 | 1,264 | 1,023 | 803 | 1,099 | 909 | 904 | -1.93 | False | nan | BOF:not cleared | DEAD |
| G1_0447__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 892 | 249 | 878 | 1,974 | 416 | 2,864 | -271 | -258 | 845 | 295 | 2,864 | 398 | 635 | True | nan | BOF:not cleared | DEAD |
| G1_0393__HM | NY-AM | SESSION-CANDIDATE | 554 | 551 | 755 | 249 | 959 | 1,663 | 721 | 1,981 | -472 | -522 | 509 | 631 | 1,981 | 282 | 696 | True | nan | BOF:not cleared | DEAD |
| G1_0786__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 1,598 | 113 | 317 | 2,076 | 151 | 965 | 1,241 | 1,000 | 844 | 1,098 | 965 | 917 | 50.29 | True | nan | BOF:not cleared | DEAD |
| G1_0007__HM | NY-AM | SESSION-CANDIDATE | 554 | 629 | 864 | 249 | 627 | 1,618 | 135 | 2,740 | 318 | 303 | 572 | 426 | 2,740 | 383 | 380 | True | nan | BOF:not cleared | DEAD |
| G1_0712__EM | NY | SESSION-CANDIDATE | 323 | 974 | 1,336 | 125 | 1,074 | 2,141 | 819 | 2,412 | -619 | -365 | 634 | 927 | 2,412 | 712 | 818 | True | nan | BOF:not cleared | DEAD |
| G1_0197__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 1,594 | 113 | 271 | 2,104 | 110 | 902 | 1,265 | 1,019 | 834 | 1,085 | 902 | 910 | 4.71 | True | nan | BOF:not cleared | DEAD |
| G1_0234__EM | NY | SESSION-CANDIDATE | 323 | 784 | 1,077 | 125 | 934 | 1,909 | 472 | 3,362 | -353 | -171 | 521 | 676 | 3,362 | 494 | 656 | True | nan | BOF:not cleared | DEAD |
| G1_0638__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 1,595 | 113 | 268 | 2,101 | 106 | 902 | 1,264 | 1,018 | 830 | 1,085 | 902 | 909 | 1.17 | True | nan | BOF:not cleared | DEAD |
| G1_0496__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 1,597 | 113 | 268 | 2,103 | 106 | 902 | 1,280 | 1,037 | 815 | 1,100 | 902 | 910 | 1.17 | True | nan | BOF:not cleared | DEAD |
| G1_0350__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 1,595 | 113 | 270 | 2,100 | 108 | 902 | 1,264 | 1,018 | 830 | 1,086 | 902 | 908 | 3.38 | True | nan | BOF:not cleared | DEAD |
| G1_0391__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 1,594 | 113 | 251 | 2,103 | 84.44 | 902 | 1,254 | 1,006 | 811 | 1,089 | 902 | 906 | -15.64 | False | nan | BOF:not cleared | DEAD |
| G1_0230__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 1,594 | 113 | 249 | 2,103 | 81.67 | 902 | 1,261 | 1,014 | 812 | 1,086 | 902 | 906 | -17.86 | False | nan | BOF:not cleared | DEAD |
| G1_0219__SM | ASIA | SESSION-CANDIDATE | 242 | 1,160 | 1,598 | 113 | 264 | 2,105 | 101 | 902 | 1,279 | 1,036 | 815 | 1,095 | 902 | 909 | -2.81 | False | nan | BOF:not cleared | DEAD |
| G1_0237__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,592 | 113 | 265 | 2,102 | 102 | 902 | 1,273 | 1,028 | 816 | 1,091 | 902 | 905 | -1.93 | False | nan | BOF:not cleared | DEAD |
| G1_0778__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 1,594 | 113 | 248 | 2,104 | 81.11 | 902 | 1,261 | 1,014 | 811 | 1,087 | 902 | 906 | -18.30 | False | nan | BOF:not cleared | DEAD |
| G1_0666__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 1,594 | 113 | 248 | 2,104 | 81.11 | 902 | 1,261 | 1,014 | 811 | 1,087 | 902 | 906 | -18.30 | False | nan | BOF:not cleared | DEAD |
| G1_0102__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 1,596 | 113 | 249 | 2,103 | 81.67 | 902 | 1,266 | 1,020 | 809 | 1,091 | 902 | 907 | -17.86 | False | nan | BOF:not cleared | DEAD |
| G1_0640__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 1,595 | 113 | 253 | 2,104 | 86.67 | 902 | 1,270 | 1,024 | 809 | 1,093 | 902 | 907 | -13.87 | False | nan | BOF:not cleared | DEAD |
| G1_0080__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 1,595 | 113 | 253 | 2,104 | 86.67 | 902 | 1,270 | 1,024 | 809 | 1,093 | 902 | 907 | -13.87 | False | nan | BOF:not cleared | DEAD |
| G1_0291__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,595 | 113 | 246 | 2,104 | 78.33 | 902 | 1,261 | 1,015 | 810 | 1,086 | 902 | 905 | -20.51 | False | nan | BOF:not cleared | DEAD |
| G1_0518__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,595 | 113 | 249 | 2,103 | 82.22 | 902 | 1,261 | 1,014 | 812 | 1,085 | 902 | 905 | -17.41 | False | nan | BOF:not cleared | DEAD |
| G1_0401__SM | ASIA | SESSION-CANDIDATE | 242 | 1,195 | 1,650 | 113 | 311 | 2,526 | 295 | 372 | 1,288 | 1,141 | 1,091 | 929 | 372 | 959 | 59.31 | True | nan | BOF:not cleared | DEAD |
| G1_0519__HM | NY-AM | SESSION-CANDIDATE | 554 | 561 | 775 | 249 | 836 | 1,711 | 623 | 1,752 | -39.77 | -55.52 | 601 | 525 | 1,752 | 297 | 577 | True | nan | BOF:not cleared | DEAD |
| G1_0158__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,596 | 113 | 254 | 2,103 | 88.89 | 902 | 1,269 | 1,023 | 807 | 1,094 | 902 | 905 | -12.10 | False | nan | BOF:not cleared | DEAD |
| G1_0829__SM | ASIA | SESSION-CANDIDATE | 242 | 1,417 | 1,957 | 113 | 423 | 2,530 | 96.18 | 1,700 | 844 | 604 | 1,594 | 686 | 1,700 | 1,178 | 162 | True | nan | BOF:not cleared | DEAD |
| G1_0722__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,567 | 2,164 | 80 | 444 | 2,836 | 328 | 1,043 | 706 | 950 | 1,650 | 681 | 1,043 | 1,354 | 216 | True | nan | BOF:not cleared | DEAD |
| G1_0248__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,597 | 113 | 246 | 2,105 | 78.89 | 902 | 1,268 | 1,022 | 804 | 1,091 | 902 | 905 | -20.07 | False | nan | BOF:not cleared | DEAD |
| G1_0078__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,597 | 113 | 246 | 2,105 | 78.89 | 902 | 1,268 | 1,022 | 804 | 1,091 | 902 | 905 | -20.07 | False | nan | BOF:not cleared | DEAD |
| G1_0524__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 1,597 | 113 | 246 | 2,105 | 78.89 | 902 | 1,268 | 1,022 | 804 | 1,091 | 902 | 905 | -20.07 | False | nan | BOF:not cleared | DEAD |
| G1_0940__SM | ASIA | SESSION-CANDIDATE | 242 | 1,468 | 2,028 | 113 | 714 | 2,497 | 536 | 1,409 | 1,154 | 973 | 1,207 | 1,325 | 1,409 | 1,243 | 474 | True | nan | BOF:not cleared | DEAD |
| G1_0717__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 1,597 | 113 | 244 | 2,105 | 75.56 | 902 | 1,265 | 1,019 | 804 | 1,088 | 902 | 904 | -22.72 | False | nan | BOF:not cleared | DEAD |
| G1_0348__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 1,597 | 113 | 244 | 2,105 | 75.56 | 902 | 1,265 | 1,019 | 804 | 1,088 | 902 | 904 | -22.72 | False | nan | BOF:not cleared | DEAD |
| G1_0681__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 1,597 | 113 | 250 | 2,103 | 82.78 | 902 | 1,268 | 1,022 | 802 | 1,093 | 902 | 904 | -16.97 | False | nan | BOF:not cleared | DEAD |
| G1_0320__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 1,597 | 113 | 270 | 2,102 | 108 | 902 | 1,269 | 1,024 | 834 | 1,077 | 902 | 904 | 3.38 | True | nan | BOF:not cleared | DEAD |
| G1_0867__HM | NY-AM | SESSION-CANDIDATE | 554 | 592 | 819 | 249 | 1,285 | 1,938 | 729 | 3,677 | -235 | -105 | 548 | 575 | 3,677 | 343 | 1,050 | True | nan | BOF:not cleared | DEAD |
| G1_0672__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 1,595 | 113 | 260 | 2,101 | 95.56 | 902 | 1,269 | 1,023 | 808 | 1,089 | 902 | 901 | -6.79 | False | nan | BOF:not cleared | DEAD |
| G1_0677__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 1,595 | 113 | 260 | 2,101 | 95.56 | 902 | 1,269 | 1,023 | 808 | 1,089 | 902 | 901 | -6.79 | False | nan | BOF:not cleared | DEAD |
| G1_0690__HM | NY-AM | SESSION-CANDIDATE | 554 | 646 | 895 | 249 | 846 | 1,952 | 304 | 3,173 | -406 | -428 | 823 | 263 | 3,173 | 384 | 591 | True | nan | BOF:not cleared | DEAD |
| G1_0764__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 1,595 | 113 | 389 | 2,081 | 261 | 894 | 1,243 | 1,000 | 842 | 1,138 | 894 | 900 | 126 | True | nan | BOF:not cleared | DEAD |
| G1_0296__HM | NY-AM | SESSION-CANDIDATE | 554 | 695 | 964 | 249 | 1,064 | 2,058 | 346 | 4,148 | -60.45 | 194 | 636 | 394 | 4,148 | 462 | 837 | True | nan | BOF:not cleared | DEAD |
| G1_0520__SM | ASIA | SESSION-CANDIDATE | 242 | 1,148 | 1,593 | 113 | 279 | 2,121 | 127 | 872 | 1,319 | 1,083 | 871 | 1,040 | 872 | 898 | 12.23 | True | nan | BOF:not cleared | DEAD |
| G1_0549__HM | NY-AM | SESSION-CANDIDATE | 554 | 571 | 793 | 249 | 803 | 1,721 | 583 | 1,752 | -33.04 | -47.27 | 594 | 524 | 1,752 | 308 | 544 | True | nan | BOF:not cleared | DEAD |
| G1_0708__HM | ASIA | SESSION-CANDIDATE | 622 | 709 | 985 | 289 | 631 | 1,467 | 741 | 202 | -279 | -511 | 559 | 884 | 202 | 461 | 379 | True | nan | BOF:not cleared | DEAD |
| G1_0129__SM | ASIA | SESSION-CANDIDATE | 242 | 1,143 | 1,588 | 113 | 359 | 2,047 | 196 | 996 | 1,256 | 1,015 | 871 | 1,067 | 996 | 894 | 92.32 | True | nan | BOF:not cleared | DEAD |
| G1_0584__SM | ASIA | SESSION-CANDIDATE | 242 | 1,154 | 1,605 | 113 | 277 | 2,103 | 118 | 902 | 1,237 | 990 | 829 | 1,084 | 902 | 903 | 10.91 | True | nan | BOF:not cleared | DEAD |
| G1_0563__SM | ASIA | SESSION-CANDIDATE | 242 | 1,591 | 2,214 | 113 | 326 | 3,227 | 215 | 760 | 661 | 537 | 1,363 | 1,121 | 760 | 1,383 | 98.57 | True | nan | BOF:not cleared | DEAD |
| G1_0194__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 1,602 | 113 | 331 | 2,082 | 137 | 1,091 | 1,334 | 1,104 | 854 | 1,062 | 1,091 | 902 | 64.45 | True | nan | BOF:not cleared | DEAD |
| G1_0116__HM | ASIA | SESSION-CANDIDATE | 622 | 770 | 1,072 | 289 | 1,580 | 1,489 | 1,391 | 2,315 | 50.28 | -223 | 611 | 1,254 | 2,315 | 530 | 1,357 | True | nan | BOF:not cleared | DEAD |
| G1_0144__SM | ASIA | SESSION-CANDIDATE | 242 | 1,153 | 1,607 | 113 | 261 | 2,102 | 96.67 | 902 | 1,260 | 1,014 | 821 | 1,080 | 902 | 902 | -5.91 | False | nan | BOF:not cleared | DEAD |
| G1_0246__HM | NY-AM | SESSION-CANDIDATE | 554 | 581 | 809 | 249 | 1,211 | 1,940 | 658 | 3,585 | 58.93 | 170 | 538 | 564 | 3,585 | 337 | 978 | True | nan | BOF:not cleared | DEAD |
| G1_0579__SM | ASIA | SESSION-CANDIDATE | 242 | 1,575 | 2,196 | 113 | 150 | 3,348 | 116 | 282 | 610 | 481 | 1,234 | 1,170 | 282 | 1,368 | -80.54 | False | nan | BOF:not cleared | DEAD |
| G1_0326__SM | ASIA | SESSION-CANDIDATE | 242 | 1,153 | 1,607 | 113 | 261 | 2,102 | 96.67 | 902 | 1,260 | 1,014 | 821 | 1,080 | 902 | 902 | -5.91 | False | nan | BOF:not cleared | DEAD |
| G1_0658__EM | NY | SESSION-CANDIDATE | 323 | 1,063 | 1,482 | 125 | 1,332 | 2,639 | 1,015 | 2,999 | -318 | -71.15 | 1,246 | 581 | 2,999 | 835 | 1,114 | True | nan | BOF:not cleared | DEAD |
| G1_0823__HM | NY-AM | SESSION-CANDIDATE | 554 | 612 | 853 | 249 | 679 | 1,613 | 500 | 1,447 | -206 | -231 | 639 | 492 | 1,447 | 345 | 412 | True | nan | BOF:not cleared | DEAD |
| G2_m30_r3_t4_s1__HM | ASIA | SESSION-CANDIDATE | 834 | 575 | 802 | 396 | 567 | 1,000 | 300 | 1,543 | -393 | -486 | 627 | 400 | 1,543 | 425 | 419 | True | nan | BOF:not cleared | DEAD |
| G1_0020__HM | NY-AM | SESSION-CANDIDATE | 554 | 638 | 892 | 249 | 637 | 2,066 | 100 | 2,945 | -174 | -134 | 710 | 236 | 2,945 | 381 | 382 | True | nan | BOF:not cleared | DEAD |
| G1_0808__SM | ASIA | SESSION-CANDIDATE | 242 | 1,146 | 1,602 | 113 | 255 | 2,104 | 90.00 | 902 | 1,261 | 1,015 | 817 | 1,071 | 902 | 896 | -11.22 | False | nan | BOF:not cleared | DEAD |
| G1_0482__SM | ASIA | SESSION-CANDIDATE | 242 | 1,144 | 1,599 | 113 | 308 | 2,088 | 164 | 872 | 1,253 | 1,005 | 839 | 1,086 | 872 | 893 | 41.88 | True | nan | BOF:not cleared | DEAD |
| G1_0105__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 1,608 | 113 | 307 | 2,076 | 122 | 1,028 | 1,085 | 850 | 837 | 1,057 | 1,028 | 903 | 43.12 | True | nan | BOF:not cleared | DEAD |
| G2_m30_r3_t12_s1__HM | ASIA | SESSION-CANDIDATE | 816 | 586 | 819 | 390 | 427 | 1,074 | 161 | 1,440 | -426 | -551 | 679 | 328 | 1,440 | 438 | 278 | True | nan | BOF:not cleared | DEAD |
| G1_0642__HM | ASIA | SESSION-CANDIDATE | 622 | 657 | 919 | 289 | 977 | 1,382 | 670 | 2,170 | -464 | -902 | 949 | 572 | 2,170 | 397 | 722 | True | nan | BOF:not cleared | DEAD |
| G1_0084__SM | ASIA | SESSION-CANDIDATE | 242 | 1,145 | 1,603 | 113 | 256 | 2,105 | 91.11 | 902 | 1,264 | 1,017 | 822 | 1,066 | 902 | 895 | -10.33 | False | nan | BOF:not cleared | DEAD |
| G1_0172__HM | NY-AM | SESSION-CANDIDATE | 554 | 696 | 974 | 249 | 853 | 1,865 | 391 | 2,837 | 390 | 529 | 934 | 240 | 2,837 | 451 | 614 | True | nan | BOF:not cleared | DEAD |
| G1_0609__SM | ASIA | SESSION-CANDIDATE | 242 | 1,140 | 1,597 | 113 | 358 | 2,068 | 192 | 1,009 | 1,250 | 1,002 | 850 | 1,084 | 1,009 | 889 | 91.88 | True | nan | BOF:not cleared | DEAD |
| G1_0081__SM | ASIA | SESSION-CANDIDATE | 242 | 1,141 | 1,599 | 113 | 303 | 2,091 | 161 | 859 | 1,252 | 1,004 | 836 | 1,084 | 859 | 890 | 36.57 | True | nan | BOF:not cleared | DEAD |
| G1_0724__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,256 | 1,759 | 100 | 1,652 | 3,336 | 1,718 | 1,164 | 443 | 507 | 1,526 | 1,155 | 1,164 | 1,031 | 1,429 | True | nan | BOF:not cleared | DEAD |
| G1_0800__SM | ASIA | SESSION-CANDIDATE | 242 | 1,312 | 1,839 | 113 | 113 | 2,590 | 129 | 51.77 | 868 | 669 | 1,158 | 946 | 51.77 | 1,089 | -129 | False | nan | BOF:not cleared | DEAD |
| G1_0179__SM | ASIA | SESSION-CANDIDATE | 242 | 1,146 | 1,607 | 113 | 250 | 2,103 | 83.89 | 902 | 1,261 | 1,015 | 814 | 1,071 | 902 | 895 | -16.09 | False | nan | BOF:not cleared | DEAD |
| G1_0088__SM | ASIA | SESSION-CANDIDATE | 242 | 1,132 | 1,589 | 113 | 292 | 2,088 | 139 | 894 | 1,254 | 1,010 | 831 | 1,062 | 894 | 882 | 25.95 | True | nan | BOF:not cleared | DEAD |
| G1_0342__SM | ASIA | SESSION-CANDIDATE | 242 | 1,145 | 1,607 | 113 | 249 | 2,103 | 82.22 | 902 | 1,263 | 1,016 | 812 | 1,070 | 902 | 894 | -17.41 | False | nan | BOF:not cleared | DEAD |
| G3_IMB_t70_w30_g1__EM | NY | SESSION-CANDIDATE | 323 | 979 | 1,375 | 125 | 671 | 2,341 | 345 | 2,381 | -123 | -95.26 | 1,282 | 281 | 2,381 | 744 | 447 | True | nan | BOF:not cleared | DEAD |
| G1_0038__HM | NY-AM | SESSION-CANDIDATE | 554 | 627 | 880 | 249 | 626 | 1,870 | 47.25 | 3,111 | 42.06 | 91.95 | 692 | 221 | 3,111 | 366 | 367 | True | nan | BOF:not cleared | DEAD |
| G1_0399__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 914 | 249 | 1,281 | 2,023 | 558 | 4,387 | -101 | 94.31 | 561 | 534 | 4,387 | 410 | 1,053 | True | nan | BOF:not cleared | DEAD |
| G1_0933__SM | ASIA | SESSION-CANDIDATE | 242 | 1,140 | 1,601 | 113 | 449 | 2,046 | 243 | 1,257 | 1,249 | 1,005 | 829 | 1,127 | 1,257 | 891 | 189 | True | nan | BOF:not cleared | DEAD |
| G1_0895__EM | NY | SESSION-CANDIDATE | 323 | 813 | 1,142 | 125 | 662 | 2,200 | 166 | 3,267 | -292 | -59.81 | 543 | 526 | 3,267 | 529 | 381 | True | nan | BOF:not cleared | DEAD |


### 5b. What the alive TH cell-sessions are: the base entry earning in a session, or the TH rule? (paired delta vs the entry's own base bracket, same trades, G1/G3 cells)
Alive cell-sessions with a base to pair: 405. Mean delta vs base: PRE -269 $/trade, HOLD -211 $/trade; share with delta>0: PRE 33%, HOLD 15%; delta>0 in both: 48. The session P&L of a TH cell is therefore mostly the BASE entry's session P&L (ST/HM/KB/SM/EM, 5 overlap clusters), not an effect of the TH rule; the TH rule itself cuts winners as often as losers (source verdict DEAD).
| cid | session | n | pre_mean | d_pre | d_pre_n | d_hold | d_hold_n |
|---|---|---|---|---|---|---|---|
| G1_0508__EM | NY | 323 | 1,118 | 175 | 323 | 478 | 125 |
| G1_0296__ST | ASIA | 712 | 874 | 94.96 | 712 | 430 | 347 |
| G1_0508__HM | ASIA | 622 | 860 | 77.67 | 622 | 371 | 289 |
| G1_0508__EM | NY-AM | 183 | 1,770 | 200 | 183 | 351 | 80 |
| G1_0215__EM | ASIA | 249 | 1,199 | 277 | 249 | 349 | 128 |
| G1_0025__EM | ASIA | 249 | 1,333 | 410 | 249 | 334 | 128 |
| G1_0100__EM | ASIA | 249 | 1,348 | 426 | 249 | 332 | 128 |
| G1_0692__HM | ASIA | 622 | 842 | 59.90 | 622 | 315 | 289 |
| G1_0867__EM | ASIA | 249 | 1,257 | 335 | 249 | 308 | 128 |
| G1_0802__EM | ASIA | 249 | 1,322 | 400 | 249 | 285 | 128 |
| G1_0563__SM | NY-AM | 220 | 1,341 | 514 | 220 | 266 | 100 |
| G1_0601__EM | NY-AM | 183 | 1,639 | 69.41 | 183 | 266 | 80 |
| G3_OPP_EM__HM | ASIA | 622 | 1,048 | 266 | 622 | 263 | 289 |
| G1_0867__HM | ASIA | 622 | 803 | 20.60 | 622 | 251 | 289 |
| G3_OPP_SM__HM | ASIA | 622 | 987 | 205 | 622 | 248 | 289 |


## 6. Dead pooled, alive in a session
Selection: pooled all-hours PRE mean <= 0 OR the source label contains DEAD, and tier SESSION-CANDIDATE/PASS. 405 cell-sessions.

| cid | session | tier | n | pre_mean | pool_pre_mean | hold_mean | x_mean | hold_meas_mean | verdict_label | bof_label |
|---|---|---|---|---|---|---|---|---|---|---|
| G3_OPP_EM__HM | ASIA | SESSION-CANDIDATE | 622 | 1,048 | 431 | 1,623 | -103 | 1,401 | DEAD | BOF_Feff:clear |
| G1_0506__HM | NY-AM | SESSION-CANDIDATE | 554 | 749 | 171 | 987 | -479 | 722 | DEAD | BOF_Feff:clear |
| G2_m40_r3_t8_s1__HM | ASIA | SESSION-CANDIDATE | 736 | 981 | 204 | 658 | -269 | 489 | DEAD | BOF:not cleared |
| G1_0180__HM | NY-AM | SESSION-CANDIDATE | 554 | 845 | 317 | 465 | 125 | 202 | DEAD | BOF:not cleared |
| G3_OPP_SM__HM | ASIA | SESSION-CANDIDATE | 622 | 987 | 409 | 1,608 | -201 | 1,392 | DEAD | BOF:not cleared |
| G2_m40_r2_t8_s1__HM | ASIA | SESSION-CANDIDATE | 737 | 959 | 168 | 643 | -333 | 474 | DEAD | BOF:not cleared |
| G1_0031__HM | NY-AM | SESSION-CANDIDATE | 554 | 798 | 408 | 287 | 8.00 | 13.57 | DEAD | BOF:not cleared |
| G2_TRAILONLY_m40_t8__HM | ASIA | SESSION-CANDIDATE | 737 | 906 | 124 | 656 | -333 | 487 | DEAD | BOF:not cleared |
| G1_0069__HM | NY-AM | SESSION-CANDIDATE | 554 | 957 | 567 | 880 | -261 | 646 | DEAD | BOF:not cleared |
| G1_0030__HM | NY-AM | SESSION-CANDIDATE | 554 | 760 | 277 | 394 | -324 | 119 | DEAD | BOF:not cleared |
| G1_0029__HM | NY-AM | SESSION-CANDIDATE | 554 | 760 | 250 | 340 | -277 | 61.73 | DEAD | BOF:not cleared |
| G1_0569__HM | NY-AM | SESSION-CANDIDATE | 554 | 1,017 | 406 | 874 | -82.36 | 654 | DEAD | BOF:not cleared |
| G1_0548__HM | NY-AM | SESSION-CANDIDATE | 554 | 628 | 146 | 867 | -361 | 597 | DEAD | BOF:not cleared |
| G1_0876__SM | ASIA | SESSION-CANDIDATE | 242 | 1,283 | 91.08 | 274 | 622 | -19.60 | DEAD | BOF:not cleared |
| G2_m40_r4_t8_s1__HM | ASIA | SESSION-CANDIDATE | 677 | 1,001 | 240 | 1,011 | -455 | 826 | DEAD | BOF:not cleared |
| G1_0273__HM | NY-AM | SESSION-CANDIDATE | 554 | 814 | 398 | 662 | -290 | 402 | DEAD | BOF:not cleared |
| G1_0359__HM | NY-AM | SESSION-CANDIDATE | 554 | 904 | 442 | 1,318 | 231 | 1,099 | DEAD | BOF:not cleared |
| G1_0832__HM | NY-AM | SESSION-CANDIDATE | 554 | 732 | 271 | 545 | 95.93 | 283 | DEAD | BOF:not cleared |
| G1_0292__SM | ASIA | SESSION-CANDIDATE | 242 | 1,259 | 56.07 | 317 | 616 | 23.33 | DEAD | BOF:not cleared |
| G1_0579__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,923 | 721 | 437 | 64.08 | 196 | DEAD | BOF:not cleared |
| G1_0956__HM | ASIA | SESSION-CANDIDATE | 622 | 938 | 460 | 1,488 | 7.69 | 1,257 | DEAD | BOF:not cleared |
| G1_0155__EM | ASIA | SESSION-CANDIDATE | 249 | 1,404 | 428 | 622 | -71.06 | 371 | DEAD | BOF:not cleared |
| G1_0705__HM | NY-AM | SESSION-CANDIDATE | 554 | 833 | 262 | 941 | 446 | 698 | DEAD | BOF:not cleared |
| G1_0715__EM | ASIA | SESSION-CANDIDATE | 249 | 1,467 | 678 | 514 | 200 | 263 | DEAD | BOF:not cleared |
| G1_0293__EM | ASIA | SESSION-CANDIDATE | 249 | 1,324 | 471 | 657 | -74.98 | 405 | DEAD | BOF:not cleared |
| G1_0254__SM | ASIA | SESSION-CANDIDATE | 242 | 1,227 | 42.68 | 335 | 616 | 44.03 | DEAD | BOF:not cleared |
| G1_0127__HM | NY-AM | SESSION-CANDIDATE | 554 | 904 | 211 | 1,072 | 600 | 839 | DEAD | BOF:not cleared |
| G1_0947__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 518 | 1,074 | -266 | 840 | DEAD | BOF:not cleared |
| G1_0101__SM | ASIA | SESSION-CANDIDATE | 242 | 1,224 | 44.89 | 278 | 606 | -15.17 | DEAD | BOF:not cleared |
| G1_0709__HM | ASIA | SESSION-CANDIDATE | 622 | 931 | 444 | 1,404 | 146 | 1,170 | DEAD | BOF:not cleared |
| G1_0589__HM | NY-AM | SESSION-CANDIDATE | 554 | 749 | 235 | 809 | -309 | 547 | DEAD | BOF:not cleared |
| G1_0649__HM | NY-AM | SESSION-CANDIDATE | 554 | 753 | 412 | 744 | -494 | 484 | DEAD | BOF:not cleared |
| G1_0249__HM | ASIA | SESSION-CANDIDATE | 622 | 921 | 368 | 1,513 | -558 | 1,294 | DEAD | BOF:not cleared |
| G1_0005__HM | NY-AM | SESSION-CANDIDATE | 554 | 938 | 307 | 1,002 | 238 | 778 | DEAD | BOF:not cleared |
| G1_0807__SM | ASIA | SESSION-CANDIDATE | 242 | 1,983 | 479 | 308 | 1,177 | 77.45 | DEAD | BOF:not cleared |
| G1_0700__HM | NY-AM | SESSION-CANDIDATE | 554 | 898 | 421 | 840 | 186 | 610 | DEAD | BOF:not cleared |
| G1_0895__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 242 | 500 | -57.87 | 222 | DEAD | BOF:not cleared |
| G1_0246__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,451 | 508 | 1,924 | 761 | 1,701 | DEAD | BOF:not cleared |
| G1_0696__HM | NY-AM | SESSION-CANDIDATE | 554 | 831 | 336 | 819 | -232 | 575 | DEAD | BOF:not cleared |
| G1_0652__SM | ASIA | SESSION-CANDIDATE | 242 | 1,212 | 63.58 | 275 | 634 | -18.71 | DEAD | BOF:not cleared |
| G1_0394__SM | ASIA | SESSION-CANDIDATE | 242 | 1,118 | 41.81 | 409 | 717 | 99.92 | DEAD | BOF:not cleared |
| G1_0066__SM | ASIA | SESSION-CANDIDATE | 242 | 1,210 | 53.02 | 255 | 608 | -38.62 | DEAD | BOF:not cleared |
| G1_0633__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,689 | 555 | 641 | 312 | 379 | DEAD | BOF:not cleared |
| G1_0096__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 345 | 707 | 192 | 455 | DEAD | BOF:not cleared |
| G1_0328__HM | NY-AM | SESSION-CANDIDATE | 554 | 716 | 259 | 606 | 794 | 351 | DEAD | BOF:not cleared |
| G1_0069__HM | ASIA | SESSION-CANDIDATE | 622 | 994 | 567 | 1,376 | -140 | 1,164 | DEAD | BOF:not cleared |
| G1_0592__HM | ASIA | SESSION-CANDIDATE | 622 | 864 | 447 | 890 | -363 | 642 | DEAD | BOF:not cleared |
| G1_0235__SM | ASIA | SESSION-CANDIDATE | 242 | 1,214 | 61.49 | 257 | 653 | -36.85 | DEAD | BOF:not cleared |
| G1_0940__HM | ASIA | SESSION-CANDIDATE | 622 | 926 | 475 | 1,415 | -4.89 | 1,190 | DEAD | BOF:not cleared |
| G1_0004__HM | NY-AM | SESSION-CANDIDATE | 554 | 876 | 339 | 856 | 59.64 | 625 | DEAD | BOF:not cleared |
| G1_0760__SM | ASIA | SESSION-CANDIDATE | 242 | 1,141 | 103 | 440 | 720 | 137 | DEAD | BOF:not cleared |
| G1_0837__HM | ASIA | SESSION-CANDIDATE | 622 | 926 | 476 | 1,552 | 187 | 1,329 | DEAD | BOF:not cleared |
| G1_0586__SM | ASIA | SESSION-CANDIDATE | 242 | 1,113 | 25.55 | 417 | 728 | 108 | DEAD | BOF:not cleared |
| G1_0148__HM | NY-AM | SESSION-CANDIDATE | 554 | 824 | 370 | 653 | -65.57 | 404 | DEAD | BOF:not cleared |
| G1_0478__SM | ASIA | SESSION-CANDIDATE | 242 | 1,197 | 56.67 | 270 | 627 | -23.13 | DEAD | BOF:not cleared |
| G1_0616__HM | NY-AM | SESSION-CANDIDATE | 554 | 672 | 335 | 420 | 73.95 | 135 | DEAD | BOF:not cleared |
| G1_0623__SM | ASIA | SESSION-CANDIDATE | 242 | 1,108 | 30.92 | 420 | 732 | 111 | DEAD | BOF:not cleared |
| G1_0911__HM | NY-AM | SESSION-CANDIDATE | 554 | 890 | 360 | 1,044 | 7.22 | 821 | DEAD | BOF:not cleared |
| G1_0784__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,615 | 535 | 363 | -89.32 | 79.63 | DEAD | BOF:not cleared |
| G1_0879__SM | ASIA | SESSION-CANDIDATE | 242 | 1,928 | 458 | 559 | 856 | 334 | DEAD | BOF:not cleared |
| G1_0017__HM | NY-AM | SESSION-CANDIDATE | 554 | 791 | 420 | 1,058 | 53.18 | 825 | DEAD | BOF:not cleared |
| G1_0687__SM | ASIA | SESSION-CANDIDATE | 242 | 1,116 | 63.21 | 418 | 709 | 112 | DEAD | BOF:not cleared |
| G1_0707__HM | NY-AM | SESSION-CANDIDATE | 554 | 793 | 387 | 557 | -224 | 293 | DEAD | BOF:not cleared |
| G1_0665__SM | ASIA | SESSION-CANDIDATE | 242 | 1,186 | 31.01 | 330 | 620 | 39.61 | DEAD | BOF:not cleared |
| G1_0456__HM | NY-AM | SESSION-CANDIDATE | 554 | 763 | 370 | 600 | -340 | 342 | DEAD | BOF:not cleared |
| G1_0008__HM | NY-AM | SESSION-CANDIDATE | 554 | 779 | 271 | 714 | -98.82 | 484 | DEAD | BOF:not cleared |
| G1_0206__HM | NY-AM | SESSION-CANDIDATE | 554 | 772 | 472 | 1,040 | -217 | 804 | DEAD | BOF:not cleared |
| G1_0203__SM | ASIA | SESSION-CANDIDATE | 242 | 1,193 | 75.70 | 267 | 564 | -26.23 | DEAD | BOF:not cleared |
| G1_0031__HM | ASIA | SESSION-CANDIDATE | 622 | 746 | 408 | 661 | -85.47 | 392 | DEAD | BOF:not cleared |
| G1_0435__SM | ASIA | SESSION-CANDIDATE | 242 | 1,193 | 48.21 | 302 | 545 | 14.74 | DEAD | BOF:not cleared |
| G1_0092__SM | ASIA | SESSION-CANDIDATE | 242 | 1,101 | 55.14 | 423 | 723 | 115 | DEAD | BOF:not cleared |
| G1_0701__SM | ASIA | SESSION-CANDIDATE | 242 | 1,099 | 49.78 | 439 | 712 | 130 | DEAD | BOF:not cleared |
| G1_0613__SM | ASIA | SESSION-CANDIDATE | 242 | 1,097 | 43.03 | 405 | 721 | 96.38 | DEAD | BOF:not cleared |
| G1_0532__SM | ASIA | SESSION-CANDIDATE | 242 | 1,096 | 52.87 | 406 | 724 | 97.70 | DEAD | BOF:not cleared |
| G1_0166__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 385 | 751 | 89.80 | 481 | DEAD | BOF:not cleared |
| G1_0143__HM | NY-AM | SESSION-CANDIDATE | 554 | 648 | 163 | 570 | -342 | 297 | DEAD | BOF:not cleared |
| G1_0945__HM | NY-AM | SESSION-CANDIDATE | 554 | 722 | 264 | 1,282 | -400 | 1,038 | DEAD | BOF:not cleared |
| G1_0338__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 48.95 | 412 | 734 | 103 | DEAD | BOF:not cleared |
| G1_0366__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 36.94 | 439 | 722 | 130 | DEAD | BOF:not cleared |
| G1_0892__SM | ASIA | SESSION-CANDIDATE | 242 | 1,094 | 42.59 | 429 | 712 | 121 | DEAD | BOF:not cleared |
| G1_0306__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 65.46 | 295 | 628 | 1.64 | DEAD | BOF:not cleared |
| G1_0167__SM | ASIA | SESSION-CANDIDATE | 242 | 1,092 | 46.96 | 413 | 718 | 105 | DEAD | BOF:not cleared |
| G1_0514__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 54.97 | 406 | 725 | 97.70 | DEAD | BOF:not cleared |
| G1_0383__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 69.22 | 278 | 622 | -15.17 | DEAD | BOF:not cleared |
| G1_0579__EM | NY | SESSION-CANDIDATE | 323 | 1,201 | 721 | 1,135 | -400 | 905 | DEAD | BOF:not cleared |
| G1_0678__HM | NY-AM | SESSION-CANDIDATE | 554 | 732 | 257 | 448 | -187 | 173 | DEAD | BOF:not cleared |
| G1_0098__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 64.20 | 431 | 735 | 125 | DEAD | BOF:not cleared |
| G1_0716__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 41.20 | 419 | 727 | 110 | DEAD | BOF:not cleared |
| G1_0160__SM | ASIA | SESSION-CANDIDATE | 242 | 1,092 | 48.45 | 414 | 722 | 106 | DEAD | BOF:not cleared |
| G1_0658__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,754 | 696 | 384 | 646 | 147 | DEAD | BOF:not cleared |
| G1_0946__EM | ASIA | SESSION-CANDIDATE | 249 | 1,343 | 493 | 569 | 225 | 315 | DEAD | BOF:not cleared |
| G1_0713__SM | ASIA | SESSION-CANDIDATE | 242 | 1,091 | 63.55 | 437 | 708 | 131 | DEAD | BOF:not cleared |
| G1_0399__HM | ASIA | SESSION-CANDIDATE | 622 | 862 | 409 | 1,393 | -53.35 | 1,163 | DEAD | BOF:not cleared |
| G1_0917__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 64.76 | 458 | 716 | 152 | DEAD | BOF:not cleared |
| G1_0123__SM | ASIA | SESSION-CANDIDATE | 242 | 1,089 | 46.57 | 413 | 720 | 105 | DEAD | BOF:not cleared |
| G1_0389__SM | ASIA | SESSION-CANDIDATE | 242 | 1,088 | 41.92 | 430 | 712 | 122 | DEAD | BOF:not cleared |
| G1_0565__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 39.21 | 405 | 722 | 96.82 | DEAD | BOF:not cleared |
| G1_0022__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 39.21 | 405 | 722 | 96.82 | DEAD | BOF:not cleared |
| G1_0838__SM | ASIA | SESSION-CANDIDATE | 242 | 1,087 | 37.83 | 404 | 719 | 95.05 | DEAD | BOF:not cleared |
| G1_0880__SM | ASIA | SESSION-CANDIDATE | 242 | 1,086 | 37.77 | 406 | 719 | 97.70 | DEAD | BOF:not cleared |
| G2_TH_LIVE_JADE_m20_r3_t8_s1__EM | ASIA | SESSION-CANDIDATE | 280 | 964 | 386 | 486 | -809 | 362 | DEAD | BOF:not cleared |
| G1_0242__SM | ASIA | SESSION-CANDIDATE | 242 | 1,090 | 68.96 | 471 | 730 | 165 | DEAD | BOF:not cleared |
| G1_0215__HM | NY-AM | SESSION-CANDIDATE | 554 | 788 | 411 | 1,132 | 22.31 | 906 | DEAD | BOF:not cleared |
| G1_0829__EM | ASIA | SESSION-CANDIDATE | 249 | 1,334 | 491 | 591 | -46.13 | 332 | DEAD | BOF:not cleared |
| G1_0449__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 35.06 | 426 | 714 | 117 | DEAD | BOF:not cleared |
| G1_0815__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 35.06 | 426 | 714 | 117 | DEAD | BOF:not cleared |
| G1_0224__SM | ASIA | SESSION-CANDIDATE | 242 | 1,083 | 60.83 | 451 | 736 | 146 | DEAD | BOF:not cleared |
| G1_0408__SM | ASIA | SESSION-CANDIDATE | 242 | 1,086 | 63.22 | 437 | 709 | 131 | DEAD | BOF:not cleared |
| G1_0372__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 30.08 | 437 | 726 | 132 | DEAD | BOF:not cleared |
| G1_0164__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 40.10 | 416 | 713 | 107 | DEAD | BOF:not cleared |
| G1_0733__HM | NY-AM | SESSION-CANDIDATE | 554 | 569 | 115 | 399 | -249 | 109 | DEAD | BOF:not cleared |
| G1_0593__SM | ASIA | SESSION-CANDIDATE | 242 | 1,085 | 62.66 | 443 | 707 | 137 | DEAD | BOF:not cleared |
| G1_0433__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 61.39 | 436 | 716 | 130 | DEAD | BOF:not cleared |
| G1_0624__SM | ASIA | SESSION-CANDIDATE | 242 | 1,084 | 61.39 | 436 | 714 | 130 | DEAD | BOF:not cleared |
| G1_0468__SM | ASIA | SESSION-CANDIDATE | 242 | 1,479 | 485 | 319 | 568 | 67.80 | DEAD | BOF:not cleared |
| G1_0563__HM | NY-AM | SESSION-CANDIDATE | 554 | 812 | 423 | 937 | -211 | 700 | DEAD | BOF:not cleared |
| G1_0632__SM | ASIA | SESSION-CANDIDATE | 242 | 1,082 | 61.50 | 456 | 717 | 151 | DEAD | BOF:not cleared |
| G1_0654__EM | ASIA | SESSION-CANDIDATE | 249 | 1,438 | 575 | 465 | 124 | 229 | DEAD | BOF:not cleared |
| G1_0296__ST | ASIA | SESSION-CANDIDATE | 712 | 874 | 205 | 263 | 338 | 25.87 | DEAD | BOF:not cleared |
| G1_0659__SM | ASIA | SESSION-CANDIDATE | 242 | 1,074 | 77.15 | 442 | 718 | 136 | DEAD | BOF:not cleared |
| G1_0727__HM | NY-AM | SESSION-CANDIDATE | 554 | 893 | 381 | 1,211 | -78.37 | 993 | DEAD | BOF:not cleared |
| G1_0236__SM | ASIA | SESSION-CANDIDATE | 242 | 1,082 | 39.75 | 462 | 732 | 156 | DEAD | BOF:not cleared |
| G1_0918__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 80.68 | 443 | 741 | 137 | DEAD | BOF:not cleared |
| G1_0508__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,770 | 868 | 878 | 848 | 658 | DEAD | BOF:not cleared |
| G1_0712__HM | NY-AM | SESSION-CANDIDATE | 554 | 729 | 368 | 742 | -317 | 483 | DEAD | BOF:not cleared |
| G1_0802__HM | NY-AM | SESSION-CANDIDATE | 554 | 741 | 411 | 903 | 12.97 | 662 | DEAD | BOF:not cleared |
| G1_0278__SM | ASIA | SESSION-CANDIDATE | 242 | 1,079 | 87.55 | 435 | 733 | 129 | DEAD | BOF:not cleared |
| G1_0149__HM | NY-AM | SESSION-CANDIDATE | 554 | 799 | 432 | 1,113 | 195 | 889 | DEAD | BOF:not cleared |
| G1_0875__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 42.14 | 454 | 741 | 148 | DEAD | BOF:not cleared |
| G1_0302__SM | ASIA | SESSION-CANDIDATE | 242 | 1,078 | 41.09 | 453 | 729 | 147 | DEAD | BOF:not cleared |
| G1_0451__HM | NY-AM | SESSION-CANDIDATE | 554 | 840 | 444 | 800 | 33.98 | 571 | DEAD | BOF:not cleared |
| G1_0860__SM | ASIA | SESSION-CANDIDATE | 242 | 1,073 | 47.50 | 443 | 731 | 137 | DEAD | BOF:not cleared |
| G1_0711__HM | NY-AM | SESSION-CANDIDATE | 554 | 748 | 317 | 943 | 423 | 709 | DEAD | BOF:not cleared |
| G1_0937__EM | NY | SESSION-CANDIDATE | 323 | 679 | 265 | 501 | -297 | 198 | DEAD | BOF:not cleared |
| G1_0865__SM | ASIA | SESSION-CANDIDATE | 242 | 1,076 | 35.99 | 452 | 726 | 146 | DEAD | BOF:not cleared |
| G1_0610__SM | ASIA | SESSION-CANDIDATE | 242 | 1,077 | 73.32 | 479 | 708 | 173 | DEAD | BOF:not cleared |
| G1_0772__SM | ASIA | SESSION-CANDIDATE | 242 | 1,075 | 38.04 | 459 | 732 | 153 | DEAD | BOF:not cleared |
| G1_0710__SM | ASIA | SESSION-CANDIDATE | 242 | 1,074 | 34.39 | 446 | 725 | 140 | DEAD | BOF:not cleared |
| G1_0533__HM | NY-AM | SESSION-CANDIDATE | 554 | 580 | 247 | 645 | -514 | 369 | DEAD | BOF:not cleared |
| G1_0539__SM | ASIA | SESSION-CANDIDATE | 242 | 1,073 | 39.98 | 454 | 741 | 148 | DEAD | BOF:not cleared |
| G1_0567__HM | NY-AM | SESSION-CANDIDATE | 554 | 676 | 423 | 1,209 | -242 | 977 | DEAD | BOF:not cleared |
| G1_0293__SM | ASIA | SESSION-CANDIDATE | 242 | 1,397 | 525 | 198 | 851 | -62.38 | DEAD | BOF:not cleared |
| G1_0100__EM | ASIA | SESSION-CANDIDATE | 249 | 1,348 | 489 | 796 | -140 | 560 | DEAD | BOF:not cleared |
| G1_0915__SM | ASIA | SESSION-CANDIDATE | 242 | 1,070 | 35.83 | 455 | 730 | 150 | DEAD | BOF:not cleared |
| G1_0241__SM | ASIA | SESSION-CANDIDATE | 242 | 1,070 | 35.99 | 455 | 732 | 150 | DEAD | BOF:not cleared |
| G1_0692__HM | ASIA | SESSION-CANDIDATE | 622 | 842 | 428 | 1,676 | 239 | 1,451 | DEAD | BOF:not cleared |
| G1_0715__SM | ASIA | SESSION-CANDIDATE | 242 | 1,607 | 494 | 410 | 1,159 | 162 | DEAD | BOF:not cleared |
| G1_0947__HM | ASIA | SESSION-CANDIDATE | 622 | 846 | 518 | 1,520 | -8.14 | 1,290 | DEAD | BOF:not cleared |
| G1_0218__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,642 | 528 | 518 | 423 | 264 | DEAD | BOF:not cleared |
| G2_m20_r3_t4_s1__EM | ASIA | SESSION-CANDIDATE | 281 | 910 | 390 | 624 | -676 | 500 | DEAD | BOF:not cleared |
| G1_0253__HM | NY-AM | SESSION-CANDIDATE | 554 | 743 | 422 | 750 | 303 | 517 | DEAD | BOF:not cleared |
| G1_0598__EM | ASIA | SESSION-CANDIDATE | 249 | 1,264 | 572 | 567 | -18.86 | 323 | DEAD | BOF:not cleared |
| G1_0319__SM | ASIA | SESSION-CANDIDATE | 242 | 1,051 | 72.00 | 423 | 706 | 114 | DEAD | BOF:not cleared |
| G1_0801__SM | ASIA | SESSION-CANDIDATE | 242 | 1,068 | 62.65 | 435 | 735 | 129 | DEAD | BOF:not cleared |
| G1_0807__HM | ASIA | SESSION-CANDIDATE | 622 | 842 | 421 | 962 | -317 | 733 | DEAD | BOF:not cleared |
| G1_0089__HM | NY-AM | SESSION-CANDIDATE | 554 | 813 | 424 | 966 | -79.27 | 727 | DEAD | BOF:not cleared |
| G1_0429__SM | ASIA | SESSION-CANDIDATE | 242 | 1,059 | 65.97 | 457 | 734 | 151 | DEAD | BOF:not cleared |
| G1_0445__HM | NY-AM | SESSION-CANDIDATE | 554 | 778 | 433 | 769 | 397 | 537 | DEAD | BOF:not cleared |
| G1_0735__HM | NY-AM | SESSION-CANDIDATE | 554 | 661 | 329 | 1,260 | -242 | 1,019 | DEAD | BOF:not cleared |
| G1_0379__HM | NY-AM | SESSION-CANDIDATE | 554 | 823 | 436 | 912 | 169 | 674 | DEAD | BOF:not cleared |
| G1_0441__SM | ASIA | SESSION-CANDIDATE | 242 | 1,057 | 86.71 | 444 | 751 | 135 | DEAD | BOF:not cleared |
| G1_0305__SM | ASIA | SESSION-CANDIDATE | 242 | 1,061 | 76.53 | 467 | 734 | 161 | DEAD | BOF:not cleared |
| G1_0145__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 94.35 | 467 | 681 | 168 | DEAD | BOF:not cleared |
| G1_0617__HM | NY-AM | SESSION-CANDIDATE | 554 | 624 | 174 | 724 | -330 | 454 | DEAD | BOF:not cleared |
| G1_0025__EM | ASIA | SESSION-CANDIDATE | 249 | 1,333 | 560 | 797 | 519 | 548 | DEAD | BOF:not cleared |
| G1_0711__SM | ASIA | SESSION-CANDIDATE | 242 | 1,702 | 377 | 475 | 741 | 254 | DEAD | BOF:not cleared |
| G1_0480__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 60.82 | 474 | 724 | 168 | DEAD | BOF:not cleared |
| G1_0430__HM | NY-AM | SESSION-CANDIDATE | 554 | 884 | 340 | 1,150 | 297 | 935 | DEAD | BOF:not cleared |
| G1_0867__EM | ASIA | SESSION-CANDIDATE | 249 | 1,257 | 588 | 772 | -3.41 | 526 | DEAD | BOF:not cleared |
| G1_0507__HM | NY-AM | SESSION-CANDIDATE | 554 | 650 | 330 | 1,242 | -240 | 1,001 | DEAD | BOF:not cleared |
| G1_0468__EM | ASIA | SESSION-CANDIDATE | 249 | 1,242 | 338 | 463 | -156 | 214 | DEAD | BOF:not cleared |
| G1_0246__SM | NY | SESSION-CANDIDATE | 328 | 1,055 | 508 | 1,711 | -0.84 | 1,482 | DEAD | BOF:not cleared |
| G1_0365__HM | NY-AM | SESSION-CANDIDATE | 554 | 785 | 354 | 1,033 | 167 | 812 | DEAD | BOF:not cleared |
| G1_0830__HM | NY-AM | SESSION-CANDIDATE | 554 | 699 | 218 | 508 | 165 | 249 | DEAD | BOF:not cleared |
| G1_0445__SM | ASIA | SESSION-CANDIDATE | 242 | 1,379 | 481 | 334 | 806 | 76.49 | DEAD | BOF:not cleared |
| G1_0850__HM | NY-AM | SESSION-CANDIDATE | 554 | 575 | 118 | 222 | -116 | -69.07 | DEAD | BOF:not cleared |
| G1_0822__SM | ASIA | SESSION-CANDIDATE | 242 | 1,793 | 634 | 53.80 | 931 | -174 | DEAD | BOF:not cleared |
| G1_0285__SM | ASIA | SESSION-CANDIDATE | 242 | 1,047 | 63.31 | 452 | 736 | 143 | DEAD | BOF:not cleared |
| G1_0563__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,341 | 639 | 2,050 | 80.94 | 1,830 | DEAD | BOF:not cleared |
| G1_0940__HM | NY-AM | SESSION-CANDIDATE | 554 | 701 | 475 | 1,048 | -316 | 812 | DEAD | BOF:not cleared |
| G1_0454__EM | NY | SESSION-CANDIDATE | 323 | 791 | 342 | 608 | -489 | 319 | DEAD | BOF:not cleared |
| G1_0476__HM | NY-AM | SESSION-CANDIDATE | 554 | 705 | 378 | 781 | -386 | 533 | DEAD | BOF:not cleared |
| G1_0204__SM | ASIA | SESSION-CANDIDATE | 242 | 1,050 | 93.28 | 376 | 641 | 79.65 | DEAD | BOF:not cleared |
| G1_0357__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,559 | 514 | 679 | 940 | 429 | DEAD | BOF:not cleared |
| G1_0843__SM | ASIA | SESSION-CANDIDATE | 242 | 1,041 | 86.59 | 509 | 677 | 206 | DEAD | BOF:not cleared |
| G1_0307__HM | NY-AM | SESSION-CANDIDATE | 554 | 796 | 385 | 975 | 221 | 758 | DEAD | BOF:not cleared |
| G1_0170__EM | ASIA | SESSION-CANDIDATE | 249 | 1,199 | 522 | 680 | -166 | 434 | DEAD | BOF:not cleared |
| G1_0500__SM | ASIA | SESSION-CANDIDATE | 242 | 1,033 | 67.24 | 482 | 726 | 179 | DEAD | BOF:not cleared |
| G1_0867__HM | ASIA | SESSION-CANDIDATE | 622 | 803 | 478 | 1,611 | 164 | 1,378 | DEAD | BOF:not cleared |
| G1_0246__EM | ASIA | SESSION-CANDIDATE | 249 | 1,207 | 483 | 510 | 54.47 | 253 | DEAD | BOF:not cleared |
| G1_0474__HM | NY-AM | SESSION-CANDIDATE | 554 | 698 | 305 | 752 | 213 | 506 | DEAD | BOF:not cleared |
| G1_0067__EM | ASIA | SESSION-CANDIDATE | 249 | 1,189 | 384 | 489 | -32.50 | 235 | DEAD | BOF:not cleared |
| G1_0021__HM | NY-AM | SESSION-CANDIDATE | 554 | 722 | 473 | 989 | -110 | 758 | DEAD | BOF:not cleared |
| G1_0155__SM | ASIA | SESSION-CANDIDATE | 242 | 1,268 | 504 | 283 | 843 | 25.13 | DEAD | BOF:not cleared |
| G3_DIV_w60__EM | NY | SESSION-CANDIDATE | 323 | 997 | 505 | 911 | -230 | 747 | DEAD | BOF:not cleared |
| G1_0654__HM | NY-AM | SESSION-CANDIDATE | 554 | 774 | 469 | 685 | 71.38 | 454 | DEAD | BOF:not cleared |
| G1_0752__HM | NY-AM | SESSION-CANDIDATE | 554 | 653 | 322 | 1,155 | -72.94 | 922 | DEAD | BOF:not cleared |
| G1_0508__HM | ASIA | SESSION-CANDIDATE | 622 | 860 | 449 | 1,732 | -178 | 1,529 | DEAD | BOF:not cleared |
| G1_0238__HM | NY-AM | SESSION-CANDIDATE | 554 | 819 | 452 | 1,169 | 15.11 | 952 | DEAD | BOF:not cleared |
| G1_0151__HM | NY-AM | SESSION-CANDIDATE | 554 | 657 | 290 | 1,192 | -120 | 958 | DEAD | BOF:not cleared |
| G3_IMB_t70_w30_g1__HM | NY-AM | SESSION-CANDIDATE | 554 | 699 | 221 | 881 | 252 | 662 | DEAD | BOF:not cleared |
| G1_0238__SM | ASIA | SESSION-CANDIDATE | 242 | 1,697 | 807 | 392 | 772 | 171 | DEAD | BOF:not cleared |
| G1_0003__HM | NY-AM | SESSION-CANDIDATE | 554 | 731 | 346 | 512 | 397 | 262 | DEAD | BOF:not cleared |
| G3_SESSEND_ASIA_x30__HM | ASIA | SESSION-CANDIDATE | 622 | 877 | 371 | 1,186 | -102 | 977 | DEAD | BOF:not cleared |
| G1_0912__HM | NY-AM | SESSION-CANDIDATE | 554 | 563 | 188 | 902 | -293 | 633 | DEAD | BOF:not cleared |
| G1_0468__HM | NY-AM | SESSION-CANDIDATE | 554 | 742 | 359 | 927 | 198 | 702 | DEAD | BOF:not cleared |
| G1_0050__HM | NY-AM | SESSION-CANDIDATE | 554 | 711 | 391 | 1,054 | 35.55 | 827 | DEAD | BOF:not cleared |
| G1_0008__SM | ASIA | SESSION-CANDIDATE | 242 | 1,019 | 357 | 315 | 301 | 42.26 | DEAD | BOF:not cleared |
| G1_0887__HM | NY-AM | SESSION-CANDIDATE | 554 | 710 | 335 | 865 | -81.29 | 622 | DEAD | BOF:not cleared |
| G1_0725__HM | NY-AM | SESSION-CANDIDATE | 554 | 745 | 390 | 919 | 213 | 677 | DEAD | BOF:not cleared |
| G1_0941__EM | NY | SESSION-CANDIDATE | 323 | 819 | 177 | 610 | -355 | 321 | DEAD | BOF:not cleared |
| G1_0620__HM | NY-AM | SESSION-CANDIDATE | 554 | 678 | 360 | 759 | -283 | 499 | DEAD | BOF:not cleared |
| G1_0502__HM | NY-AM | SESSION-CANDIDATE | 554 | 717 | 383 | 961 | -73.24 | 730 | DEAD | BOF:not cleared |
| G1_0780__HM | NY-AM | SESSION-CANDIDATE | 554 | 742 | 303 | 892 | 227 | 662 | DEAD | BOF:not cleared |
| G1_0508__SM | ASIA | SESSION-CANDIDATE | 242 | 1,704 | 737 | 616 | 742 | 394 | DEAD | BOF:not cleared |
| G1_0418__HM | NY-AM | SESSION-CANDIDATE | 554 | 731 | 352 | 923 | -199 | 676 | DEAD | BOF:not cleared |
| G1_0802__EM | ASIA | SESSION-CANDIDATE | 249 | 1,322 | 416 | 748 | 43.26 | 515 | DEAD | BOF:not cleared |
| G1_0785__SM | ASIA | SESSION-CANDIDATE | 242 | 1,459 | 321 | 290 | 1,250 | 32.26 | DEAD | BOF:not cleared |
| G2_m20_r3_t8_s2.0__EM | ASIA | SESSION-CANDIDATE | 280 | 886 | 408 | 525 | -810 | 400 | DEAD | BOF:not cleared |
| G2_m20_r3_t8_s0.5__EM | ASIA | SESSION-CANDIDATE | 280 | 877 | 394 | 489 | -836 | 365 | DEAD | BOF:not cleared |
| G2_m20_r2_t8_s1__EM | ASIA | SESSION-CANDIDATE | 280 | 849 | 347 | 443 | -810 | 322 | DEAD | BOF:not cleared |
| G1_0336__EM | NY | SESSION-CANDIDATE | 323 | 825 | 264 | 611 | -365 | 324 | DEAD | BOF:not cleared |
| G1_0738__SM | ASIA | SESSION-CANDIDATE | 242 | 1,668 | 514 | 495 | 875 | 261 | DEAD | BOF:not cleared |
| G1_0488__HM | NY-AM | SESSION-CANDIDATE | 554 | 617 | 98.77 | 430 | -63.97 | 148 | DEAD | BOF:not cleared |
| G1_0722__HM | NY-AM | SESSION-CANDIDATE | 554 | 833 | 449 | 1,271 | 43.76 | 1,059 | DEAD | BOF:not cleared |
| G1_0026__HM | NY-AM | SESSION-CANDIDATE | 554 | 728 | 384 | 658 | 301 | 402 | DEAD | BOF:not cleared |
| G3_IMB_t70_w60_g1__HM | NY-AM | SESSION-CANDIDATE | 554 | 878 | 309 | 970 | 250 | 763 | DEAD | BOF:not cleared |
| G1_0166__SM | ASIA | SESSION-CANDIDATE | 242 | 1,595 | 157 | 343 | 1,182 | 97.43 | DEAD | BOF:not cleared |
| G1_0321__SM | ASIA | SESSION-CANDIDATE | 242 | 1,252 | 323 | 468 | 796 | 210 | DEAD | BOF:not cleared |
| G1_0837__SM | ASIA | SESSION-CANDIDATE | 242 | 1,426 | 439 | 637 | 1,425 | 394 | DEAD | BOF:not cleared |
| G1_0238__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,644 | 731 | 433 | 1,188 | 204 | DEAD | BOF:not cleared |
| G1_0851__EM | NY | SESSION-CANDIDATE | 323 | 884 | 236 | 1,121 | -419 | 862 | DEAD | BOF:not cleared |
| G1_0649__EM | ASIA | SESSION-CANDIDATE | 249 | 1,189 | 497 | 671 | 245 | 419 | DEAD | BOF:not cleared |
| G1_0059__HM | NY-AM | SESSION-CANDIDATE | 554 | 553 | -12.14 | 553 | 279 | 267 | DEAD | BOF:not cleared |
| G2_m20_r2_t8_s2__EM | ASIA | SESSION-CANDIDATE | 280 | 844 | 335 | 507 | -825 | 386 | DEAD | BOF:not cleared |
| G1_0580__EM | ASIA | SESSION-CANDIDATE | 249 | 1,046 | 458 | 690 | 333 | 417 | DEAD | BOF:not cleared |
| G1_0100__SM | ASIA | SESSION-CANDIDATE | 242 | 1,439 | 400 | 277 | 613 | 31.63 | DEAD | BOF:not cleared |
| G1_0492__HM | NY-AM | SESSION-CANDIDATE | 554 | 695 | 296 | 760 | -29.90 | 522 | DEAD | BOF:not cleared |
| G1_0651__HM | NY-AM | SESSION-CANDIDATE | 554 | 681 | 405 | 1,065 | -267 | 812 | DEAD | BOF:not cleared |
| G1_0820__HM | NY-AM | SESSION-CANDIDATE | 554 | 578 | 242 | 670 | -424 | 403 | DEAD | BOF:not cleared |
| G1_0343__HM | NY-AM | SESSION-CANDIDATE | 554 | 556 | 168 | 746 | 51.45 | 482 | DEAD | BOF:not cleared |
| G1_0067__HM | NY-AM | SESSION-CANDIDATE | 554 | 675 | 303 | 904 | 215 | 674 | DEAD | BOF:not cleared |
| G3_IMB_t70_w30_g0__HM | NY-AM | SESSION-CANDIDATE | 554 | 658 | 183 | 999 | 207 | 786 | DEAD | BOF:not cleared |
| G1_0545__EM | NY | SESSION-CANDIDATE | 323 | 841 | 204 | 852 | -191 | 574 | DEAD | BOF:not cleared |
| G1_0598__HM | ASIA | SESSION-CANDIDATE | 622 | 793 | 447 | 1,466 | -77.49 | 1,236 | DEAD | BOF:not cleared |
| G1_0567__HM | ASIA | SESSION-CANDIDATE | 622 | 775 | 423 | 1,285 | 31.45 | 1,053 | DEAD | BOF:not cleared |
| G1_0009__HM | NY-AM | SESSION-CANDIDATE | 554 | 770 | 277 | 1,155 | 42.84 | 935 | DEAD | BOF:not cleared |
| G1_0206__HM | ASIA | SESSION-CANDIDATE | 622 | 771 | 472 | 1,593 | 184 | 1,362 | DEAD | BOF:not cleared |
| G1_0831__SM | ASIA | SESSION-CANDIDATE | 242 | 985 | 88.20 | 494 | 714 | 197 | DEAD | BOF:not cleared |
| G1_0215__EM | ASIA | SESSION-CANDIDATE | 249 | 1,199 | 537 | 813 | -2.73 | 569 | DEAD | BOF:not cleared |
| G1_0822__ST | ASIA | SESSION-CANDIDATE | 712 | 789 | 275 | 65.44 | 455 | -167 | DEAD | BOF:not cleared |
| G2_m20_r2_t4_s1__EM | ASIA | SESSION-CANDIDATE | 281 | 802 | 342 | 520 | -707 | 398 | DEAD | BOF:not cleared |
| G1_0502__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,182 | 535 | 1,521 | 481 | 1,298 | DEAD | BOF:not cleared |
| G1_0508__HM | NY-AM | SESSION-CANDIDATE | 554 | 772 | 449 | 987 | 235 | 767 | DEAD | BOF:not cleared |
| G1_0039__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,361 | 463 | 271 | -480 | -12.75 | DEAD | BOF:not cleared |
| G1_0598__HM | NY-AM | SESSION-CANDIDATE | 554 | 660 | 447 | 1,173 | -89.29 | 943 | DEAD | BOF:not cleared |
| G1_0580__SM | ASIA | SESSION-CANDIDATE | 242 | 1,227 | 287 | 515 | 1,032 | 249 | DEAD | BOF:not cleared |
| G1_0077__SM | ASIA | SESSION-CANDIDATE | 242 | 1,175 | 427 | 268 | 1,272 | 1.61 | DEAD | BOF:not cleared |
| G1_0515__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 430 | 273 | 1,272 | 6.48 | DEAD | BOF:not cleared |
| G3_IMB_t70_w60_g0__HM | NY-AM | SESSION-CANDIDATE | 554 | 862 | 323 | 947 | 216 | 740 | DEAD | BOF:not cleared |
| G1_0293__HM | NY-AM | SESSION-CANDIDATE | 554 | 661 | 340 | 879 | 118 | 649 | DEAD | BOF:not cleared |
| G1_0736__HM | NY-AM | SESSION-CANDIDATE | 554 | 586 | 250 | 627 | -418 | 359 | DEAD | BOF:not cleared |
| G1_0229__SM | ASIA | SESSION-CANDIDATE | 242 | 1,173 | 429 | 266 | 1,270 | -0.16 | DEAD | BOF:not cleared |
| G1_0301__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 425 | 288 | 1,272 | 21.52 | DEAD | BOF:not cleared |
| G1_0601__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,639 | 629 | 792 | 1,196 | 577 | DEAD | BOF:not cleared |
| G1_0612__SM | ASIA | SESSION-CANDIDATE | 242 | 1,174 | 429 | 275 | 1,264 | 8.69 | DEAD | BOF:not cleared |
| G1_0508__EM | NY | SESSION-CANDIDATE | 323 | 1,118 | 868 | 1,624 | -41.13 | 1,419 | DEAD | BOF:not cleared |
| G1_0016__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 431 | 200 | 1,253 | -66.64 | DEAD | BOF:not cleared |
| G1_0270__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 429 | 281 | 1,279 | 14.00 | DEAD | BOF:not cleared |
| G1_0547__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 429 | 507 | 1,297 | 244 | DEAD | BOF:not cleared |
| G1_0327__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 425 | 252 | 1,257 | -14.32 | DEAD | BOF:not cleared |
| G1_0725__SM | ASIA | SESSION-CANDIDATE | 242 | 1,634 | 576 | 521 | 859 | 297 | DEAD | BOF:not cleared |
| G1_0730__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 425 | 252 | 1,257 | -14.32 | DEAD | BOF:not cleared |
| G1_0668__SM | ASIA | SESSION-CANDIDATE | 242 | 1,168 | 426 | 266 | 1,256 | -0.60 | DEAD | BOF:not cleared |
| G1_0534__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 420 | 258 | 1,266 | -8.12 | DEAD | BOF:not cleared |
| G1_0835__SM | ASIA | SESSION-CANDIDATE | 242 | 1,171 | 432 | 264 | 1,268 | -2.37 | DEAD | BOF:not cleared |
| G1_0374__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 417 | 262 | 1,238 | -4.14 | DEAD | BOF:not cleared |
| G1_0804__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 418 | 259 | 1,267 | -7.68 | DEAD | BOF:not cleared |
| G1_0428__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 422 | 251 | 1,267 | -15.20 | DEAD | BOF:not cleared |
| G1_0017__HM | ASIA | SESSION-CANDIDATE | 622 | 676 | 420 | 1,047 | -107 | 813 | DEAD | BOF:not cleared |
| G1_0138__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 420 | 280 | 1,274 | 13.12 | DEAD | BOF:not cleared |
| G1_0331__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 422 | 250 | 1,262 | -16.09 | DEAD | BOF:not cleared |
| G1_0839__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 421 | 250 | 1,263 | -16.97 | DEAD | BOF:not cleared |
| G1_0335__HM | NY-AM | SESSION-CANDIDATE | 554 | 654 | 367 | 1,239 | 297 | 1,009 | DEAD | BOF:not cleared |
| G1_0615__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 417 | 254 | 1,265 | -12.55 | DEAD | BOF:not cleared |
| G1_0622__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 417 | 254 | 1,265 | -12.55 | DEAD | BOF:not cleared |
| G1_0813__HM | NY-AM | SESSION-CANDIDATE | 554 | 551 | 113 | 465 | -134 | 203 | DEAD | BOF:not cleared |
| G1_0784__EM | NY | SESSION-CANDIDATE | 323 | 944 | 535 | 1,060 | -700 | 795 | DEAD | BOF:not cleared |
| G1_0633__SM | ASIA | SESSION-CANDIDATE | 242 | 1,620 | 430 | 233 | 812 | -0.24 | DEAD | BOF:not cleared |
| G1_0459__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 421 | 257 | 1,277 | -9.45 | DEAD | BOF:not cleared |
| G1_0861__SM | ASIA | SESSION-CANDIDATE | 242 | 1,168 | 444 | 374 | 1,239 | 110 | DEAD | BOF:not cleared |
| G1_0106__SM | ASIA | SESSION-CANDIDATE | 242 | 1,174 | 429 | 213 | 1,219 | -53.72 | DEAD | BOF:not cleared |
| G1_0210__SM | ASIA | SESSION-CANDIDATE | 242 | 1,162 | 434 | 301 | 1,212 | 34.80 | DEAD | BOF:not cleared |
| G1_0117__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 420 | 262 | 1,282 | -4.58 | DEAD | BOF:not cleared |
| G1_0621__HM | NY-AM | SESSION-CANDIDATE | 554 | 562 | 81.12 | 517 | 31.13 | 230 | DEAD | BOF:not cleared |
| G1_0817__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 408 | 276 | 1,270 | 9.58 | DEAD | BOF:not cleared |
| G1_0914__HM | ASIA | SESSION-CANDIDATE | 622 | 762 | 399 | 1,395 | -152 | 1,167 | DEAD | BOF:not cleared |
| G1_0952__HM | NY-AM | SESSION-CANDIDATE | 554 | 747 | 357 | 1,039 | 212 | 824 | DEAD | BOF:not cleared |
| G1_0510__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,632 | 679 | 548 | 920 | 332 | DEAD | BOF:not cleared |
| G1_0837__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 476 | 1,076 | -3.39 | 840 | DEAD | BOF:not cleared |
| G1_0728__SM | ASIA | SESSION-CANDIDATE | 242 | 1,177 | 414 | 280 | 1,263 | 13.12 | DEAD | BOF:not cleared |
| G1_0401__HM | ASIA | SESSION-CANDIDATE | 622 | 736 | 411 | 1,519 | 26.66 | 1,290 | DEAD | BOF:not cleared |
| G1_0803__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 415 | 260 | 1,261 | -6.35 | DEAD | BOF:not cleared |
| G1_0663__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 415 | 260 | 1,261 | -6.35 | DEAD | BOF:not cleared |
| G1_0882__SM | ASIA | SESSION-CANDIDATE | 242 | 1,169 | 412 | 257 | 1,251 | -9.89 | DEAD | BOF:not cleared |
| G1_0753__SM | ASIA | SESSION-CANDIDATE | 242 | 1,180 | 370 | 308 | 1,217 | 41.44 | DEAD | BOF:not cleared |
| G1_0150__SM | ASIA | SESSION-CANDIDATE | 242 | 1,160 | 417 | 262 | 1,273 | -4.14 | DEAD | BOF:not cleared |
| G1_0825__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 411 | 256 | 1,272 | -10.78 | DEAD | BOF:not cleared |
| G1_0929__SM | ASIA | SESSION-CANDIDATE | 242 | 1,172 | 411 | 260 | 1,275 | -6.79 | DEAD | BOF:not cleared |
| G1_0407__HM | NY-AM | SESSION-CANDIDATE | 554 | 549 | 4.79 | 182 | 4.26 | -126 | DEAD | BOF:not cleared |
| G1_0053__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 423 | 354 | 1,251 | 87.45 | DEAD | BOF:not cleared |
| G1_0483__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 408 | 266 | 1,273 | -0.16 | DEAD | BOF:not cleared |
| G1_0298__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 415 | 260 | 1,262 | -6.35 | DEAD | BOF:not cleared |
| G1_0486__SM | ASIA | SESSION-CANDIDATE | 242 | 1,169 | 409 | 302 | 1,251 | 38.25 | DEAD | BOF:not cleared |
| G1_0431__SM | ASIA | SESSION-CANDIDATE | 242 | 1,167 | 409 | 265 | 1,250 | -1.04 | DEAD | BOF:not cleared |
| G1_0571__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 404 | 249 | 1,262 | -17.86 | DEAD | BOF:not cleared |
| G1_0012__HM | NY-AM | SESSION-CANDIDATE | 554 | 644 | 185 | 704 | -77.12 | 478 | DEAD | BOF:not cleared |
| G1_0051__HM | ASIA | SESSION-CANDIDATE | 622 | 615 | 175 | 393 | -54.00 | 91.80 | DEAD | BOF:not cleared |
| G1_0553__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 406 | 253 | 1,262 | -13.87 | DEAD | BOF:not cleared |
| G1_0413__HM | ASIA | SESSION-CANDIDATE | 622 | 583 | 148 | 363 | -153 | 59.19 | DEAD | BOF:not cleared |
| G1_0664__HM | NY-AM | SESSION-CANDIDATE | 554 | 774 | 395 | 1,436 | 54.77 | 1,228 | DEAD | BOF:not cleared |
| G1_0910__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 407 | 266 | 1,275 | -0.60 | DEAD | BOF:not cleared |
| G1_0134__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 410 | 251 | 1,264 | -15.20 | DEAD | BOF:not cleared |
| G1_0924__SM | ASIA | SESSION-CANDIDATE | 242 | 1,166 | 410 | 251 | 1,264 | -15.20 | DEAD | BOF:not cleared |
| G1_0901__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 406 | 264 | 1,253 | -2.37 | DEAD | BOF:not cleared |
| G1_0603__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 406 | 264 | 1,253 | -2.37 | DEAD | BOF:not cleared |
| G1_0595__SM | ASIA | SESSION-CANDIDATE | 242 | 1,163 | 406 | 264 | 1,253 | -2.37 | DEAD | BOF:not cleared |
| G1_0834__SM | ASIA | SESSION-CANDIDATE | 242 | 1,164 | 411 | 249 | 1,264 | -17.86 | DEAD | BOF:not cleared |
| G1_0581__SM | ASIA | SESSION-CANDIDATE | 242 | 1,267 | 315 | 419 | 902 | 146 | DEAD | BOF:not cleared |
| G1_0103__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 415 | 265 | 1,264 | -1.93 | DEAD | BOF:not cleared |
| G1_0447__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 366 | 878 | -271 | 635 | DEAD | BOF:not cleared |
| G1_0393__HM | NY-AM | SESSION-CANDIDATE | 554 | 551 | 213 | 959 | -472 | 696 | DEAD | BOF:not cleared |
| G1_0786__SM | ASIA | SESSION-CANDIDATE | 242 | 1,165 | 407 | 317 | 1,241 | 50.29 | DEAD | BOF:not cleared |
| G1_0007__HM | NY-AM | SESSION-CANDIDATE | 554 | 629 | 296 | 627 | 318 | 380 | DEAD | BOF:not cleared |
| G1_0712__EM | NY | SESSION-CANDIDATE | 323 | 974 | 511 | 1,074 | -619 | 818 | DEAD | BOF:not cleared |
| G1_0197__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 400 | 271 | 1,265 | 4.71 | DEAD | BOF:not cleared |
| G1_0234__EM | NY | SESSION-CANDIDATE | 323 | 784 | 362 | 934 | -353 | 656 | DEAD | BOF:not cleared |
| G1_0638__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 409 | 268 | 1,264 | 1.17 | DEAD | BOF:not cleared |
| G1_0496__SM | ASIA | SESSION-CANDIDATE | 242 | 1,161 | 416 | 268 | 1,280 | 1.17 | DEAD | BOF:not cleared |
| G1_0350__SM | ASIA | SESSION-CANDIDATE | 242 | 1,159 | 410 | 270 | 1,264 | 3.38 | DEAD | BOF:not cleared |
| G1_0391__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 405 | 251 | 1,254 | -15.64 | DEAD | BOF:not cleared |
| G1_0230__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 405 | 249 | 1,261 | -17.86 | DEAD | BOF:not cleared |
| G1_0219__SM | ASIA | SESSION-CANDIDATE | 242 | 1,160 | 416 | 264 | 1,279 | -2.81 | DEAD | BOF:not cleared |
| G1_0237__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 408 | 265 | 1,273 | -1.93 | DEAD | BOF:not cleared |
| G1_0778__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 408 | 248 | 1,261 | -18.30 | DEAD | BOF:not cleared |
| G1_0666__SM | ASIA | SESSION-CANDIDATE | 242 | 1,157 | 408 | 248 | 1,261 | -18.30 | DEAD | BOF:not cleared |
| G1_0102__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 407 | 249 | 1,266 | -17.86 | DEAD | BOF:not cleared |
| G1_0640__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 405 | 253 | 1,270 | -13.87 | DEAD | BOF:not cleared |
| G1_0080__SM | ASIA | SESSION-CANDIDATE | 242 | 1,158 | 405 | 253 | 1,270 | -13.87 | DEAD | BOF:not cleared |
| G1_0291__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 407 | 246 | 1,261 | -20.51 | DEAD | BOF:not cleared |
| G1_0518__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 403 | 249 | 1,261 | -17.41 | DEAD | BOF:not cleared |
| G1_0401__SM | ASIA | SESSION-CANDIDATE | 242 | 1,195 | 341 | 311 | 1,288 | 59.31 | DEAD | BOF:not cleared |
| G1_0519__HM | NY-AM | SESSION-CANDIDATE | 554 | 561 | 223 | 836 | -39.77 | 577 | DEAD | BOF:not cleared |
| G1_0158__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 404 | 254 | 1,269 | -12.10 | DEAD | BOF:not cleared |
| G1_0829__SM | ASIA | SESSION-CANDIDATE | 242 | 1,417 | 508 | 423 | 844 | 162 | DEAD | BOF:not cleared |
| G1_0722__EM | NY-AM | SESSION-CANDIDATE | 183 | 1,567 | 498 | 444 | 706 | 216 | DEAD | BOF:not cleared |
| G1_0248__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 407 | 246 | 1,268 | -20.07 | DEAD | BOF:not cleared |
| G1_0078__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 407 | 246 | 1,268 | -20.07 | DEAD | BOF:not cleared |
| G1_0524__SM | ASIA | SESSION-CANDIDATE | 242 | 1,156 | 407 | 246 | 1,268 | -20.07 | DEAD | BOF:not cleared |
| G1_0940__SM | ASIA | SESSION-CANDIDATE | 242 | 1,468 | 283 | 714 | 1,154 | 474 | DEAD | BOF:not cleared |
| G1_0717__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 403 | 244 | 1,265 | -22.72 | DEAD | BOF:not cleared |
| G1_0348__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 403 | 244 | 1,265 | -22.72 | DEAD | BOF:not cleared |
| G1_0681__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 408 | 250 | 1,268 | -16.97 | DEAD | BOF:not cleared |
| G1_0320__SM | ASIA | SESSION-CANDIDATE | 242 | 1,155 | 399 | 270 | 1,269 | 3.38 | DEAD | BOF:not cleared |
| G1_0867__HM | NY-AM | SESSION-CANDIDATE | 554 | 592 | 478 | 1,285 | -235 | 1,050 | DEAD | BOF:not cleared |
| G1_0672__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 402 | 260 | 1,269 | -6.79 | DEAD | BOF:not cleared |
| G1_0677__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 402 | 260 | 1,269 | -6.79 | DEAD | BOF:not cleared |
| G1_0690__HM | NY-AM | SESSION-CANDIDATE | 554 | 646 | 348 | 846 | -406 | 591 | DEAD | BOF:not cleared |
| G1_0764__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 410 | 389 | 1,243 | 126 | DEAD | BOF:not cleared |
| G1_0296__HM | NY-AM | SESSION-CANDIDATE | 554 | 695 | 437 | 1,064 | -60.45 | 837 | DEAD | BOF:not cleared |
| G1_0520__SM | ASIA | SESSION-CANDIDATE | 242 | 1,148 | 398 | 279 | 1,319 | 12.23 | DEAD | BOF:not cleared |
| G1_0549__HM | NY-AM | SESSION-CANDIDATE | 554 | 571 | 235 | 803 | -33.04 | 544 | DEAD | BOF:not cleared |
| G1_0708__HM | ASIA | SESSION-CANDIDATE | 622 | 709 | 481 | 631 | -279 | 379 | DEAD | BOF:not cleared |
| G1_0129__SM | ASIA | SESSION-CANDIDATE | 242 | 1,143 | 432 | 359 | 1,256 | 92.32 | DEAD | BOF:not cleared |
| G1_0584__SM | ASIA | SESSION-CANDIDATE | 242 | 1,154 | 395 | 277 | 1,237 | 10.91 | DEAD | BOF:not cleared |
| G1_0563__SM | ASIA | SESSION-CANDIDATE | 242 | 1,591 | 639 | 326 | 661 | 98.57 | DEAD | BOF:not cleared |
| G1_0194__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 397 | 331 | 1,334 | 64.45 | DEAD | BOF:not cleared |
| G1_0116__HM | ASIA | SESSION-CANDIDATE | 622 | 770 | 431 | 1,580 | 50.28 | 1,357 | DEAD | BOF:not cleared |
| G1_0144__SM | ASIA | SESSION-CANDIDATE | 242 | 1,153 | 393 | 261 | 1,260 | -5.91 | DEAD | BOF:not cleared |
| G1_0246__HM | NY-AM | SESSION-CANDIDATE | 554 | 581 | 243 | 1,211 | 58.93 | 978 | DEAD | BOF:not cleared |
| G1_0579__SM | ASIA | SESSION-CANDIDATE | 242 | 1,575 | 636 | 150 | 610 | -80.54 | DEAD | BOF:not cleared |
| G1_0326__SM | ASIA | SESSION-CANDIDATE | 242 | 1,153 | 393 | 261 | 1,260 | -5.91 | DEAD | BOF:not cleared |
| G1_0658__EM | NY | SESSION-CANDIDATE | 323 | 1,063 | 696 | 1,332 | -318 | 1,114 | DEAD | BOF:not cleared |
| G1_0823__HM | NY-AM | SESSION-CANDIDATE | 554 | 612 | 346 | 679 | -206 | 412 | DEAD | BOF:not cleared |
| G2_m30_r3_t4_s1__HM | ASIA | SESSION-CANDIDATE | 834 | 575 | 162 | 567 | -393 | 419 | DEAD | BOF:not cleared |
| G1_0020__HM | NY-AM | SESSION-CANDIDATE | 554 | 638 | 460 | 637 | -174 | 382 | DEAD | BOF:not cleared |
| G1_0808__SM | ASIA | SESSION-CANDIDATE | 242 | 1,146 | 394 | 255 | 1,261 | -11.22 | DEAD | BOF:not cleared |
| G1_0482__SM | ASIA | SESSION-CANDIDATE | 242 | 1,144 | 409 | 308 | 1,253 | 41.88 | DEAD | BOF:not cleared |
| G1_0105__SM | ASIA | SESSION-CANDIDATE | 242 | 1,151 | 381 | 307 | 1,085 | 43.12 | DEAD | BOF:not cleared |
| G2_m30_r3_t12_s1__HM | ASIA | SESSION-CANDIDATE | 816 | 586 | 81.44 | 427 | -426 | 278 | DEAD | BOF:not cleared |
| G1_0642__HM | ASIA | SESSION-CANDIDATE | 622 | 657 | 312 | 977 | -464 | 722 | DEAD | BOF:not cleared |
| G1_0084__SM | ASIA | SESSION-CANDIDATE | 242 | 1,145 | 394 | 256 | 1,264 | -10.33 | DEAD | BOF:not cleared |
| G1_0172__HM | NY-AM | SESSION-CANDIDATE | 554 | 696 | 381 | 853 | 390 | 614 | DEAD | BOF:not cleared |
| G1_0609__SM | ASIA | SESSION-CANDIDATE | 242 | 1,140 | 416 | 358 | 1,250 | 91.88 | DEAD | BOF:not cleared |
| G1_0081__SM | ASIA | SESSION-CANDIDATE | 242 | 1,141 | 406 | 303 | 1,252 | 36.57 | DEAD | BOF:not cleared |
| G1_0724__SM | NY-AM | SESSION-CANDIDATE | 220 | 1,256 | 485 | 1,652 | 443 | 1,429 | DEAD | BOF:not cleared |
| G1_0800__SM | ASIA | SESSION-CANDIDATE | 242 | 1,312 | 550 | 113 | 868 | -129 | DEAD | BOF:not cleared |
| G1_0179__SM | ASIA | SESSION-CANDIDATE | 242 | 1,146 | 390 | 250 | 1,261 | -16.09 | DEAD | BOF:not cleared |
| G1_0088__SM | ASIA | SESSION-CANDIDATE | 242 | 1,132 | 421 | 292 | 1,254 | 25.95 | DEAD | BOF:not cleared |
| G1_0342__SM | ASIA | SESSION-CANDIDATE | 242 | 1,145 | 389 | 249 | 1,263 | -17.41 | DEAD | BOF:not cleared |
| G3_IMB_t70_w30_g1__EM | NY | SESSION-CANDIDATE | 323 | 979 | 465 | 671 | -123 | 447 | DEAD | BOF:not cleared |
| G1_0038__HM | NY-AM | SESSION-CANDIDATE | 554 | 627 | 301 | 626 | 42.06 | 367 | DEAD | BOF:not cleared |
| G1_0399__HM | NY-AM | SESSION-CANDIDATE | 554 | 651 | 409 | 1,281 | -101 | 1,053 | DEAD | BOF:not cleared |
| G1_0933__SM | ASIA | SESSION-CANDIDATE | 242 | 1,140 | 402 | 449 | 1,249 | 189 | DEAD | BOF:not cleared |
| G1_0895__EM | NY | SESSION-CANDIDATE | 323 | 813 | 281 | 662 | -292 | 381 | DEAD | BOF:not cleared |


## 7. Replay queue (survivors_for_A)
Replayable static-OCO survivors: 0 cells / 0 entries written to out/sb2/hold/survivors_for_A.parquet (columns of out/ssa/entries.parquet: t_ent, side, st, tt, t_fl, lc, lots100 + cell, session, family, stop_pts; t_ent = stored instant, t_fl = 16:55 ET of the label day). Not replayable (405 alive cell-sessions): path-dependent or non-market-entry rules, reasons in out/sb2/hold/not_replayable.json. Cells with a stop < 15 pt are not MEASURED-reliable on the stored basis and are flagged by med_stop.

Reasons: trade-health modifier (path-dependent cut), not a static bracket x405


## 8. Conventions and limits
$ per trade: PBX = ptsE x 200 (10-lot-equivalent net pts of the mapped conservative basis, costs and sweep surcharge inside); PB2/PB3/T4A = the lock-engine net $ at the cell's lot sizing (R = $12,000); T-HOLD/T4G1 = pts x 200 at 10 lots (base bracket net of exit costs and $4.84 commission, cut legs at the live cut cost 0.995/1.01 pt). MEASURED-analytic = pnl - 200 x lots/10 x (0.25 entry tick + stop slippage(lots, DS3_DN_STOPFILL: 1.44 pt at 10 lots, x1.18 recent drift) on losing trades); it does not remove mapped stop credit that a family may carry and is an estimate, not the replay. Placebo: weekly sign-flip, 200 draws. 2023 span (X) and by-year are printed, never a gate. Week-cluster SE across all label weeks of the window.
