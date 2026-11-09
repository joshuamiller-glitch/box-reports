# EXH_STAGE2 - the decisive table: do the per-book cells still lower drawdown in the ENGINE cascade? (auto-generated 2026-11-09 08:45Z)
Engine S2 = the set run through the replica engine (re-entries, locks, stack gates, other books) vs engine never-cut (base_b/NOCUT) and vs the S1b-COMB live reference row; months/windows covered are in the stage tag. Stage 1 here = the same rule first-order on U2 (kernel re-run, panels from the state files of the previous and the label day). Live week = 186 live trades first-order (the engine run does not include 2026-11). S2 rows carry no placebo draws, so no S2 row can be ENTER; Stage 1 placebo/WY/WF of the finalists are in the owners reports (EXH_*.md) and the ledger.
USD per ISO week at live lots, net of 4.84/contract; delta = rule minus never-cut with the carrying week dropped; maxDD/worst-20 on all weeks of the window.

## Plain reading (auto)
Every per-book cell below that lowers the L6M maxDD in the engine while keeping PRE maxDD within +5% (weak) or both at least 2% lower (STRICT). A cell that lowers drawdown but has a negative L6M/PRE mean is a drawdown-for-profit trade, not an improvement; the label column applies the page rules (CANDIDATE-DD needs L6M mean >= 0). No S2 row can be ENTER (no placebo draws).
- ldef_perbook_u2 M7 (weak): L6M maxDD 37,288 vs 48,019, PRE maxDD 44,115 vs 44,205, L6M mean -133/wk, PRE mean -212/wk, live week -1,985, recents ok, label no; Stage 1 L6M gain kept in the engine: 35%.
- ldef_perbook_u2 U7 (weak): L6M maxDD 13,232 vs 17,816, PRE maxDD 39,558 vs 39,542, L6M mean -93/wk, PRE mean -369/wk, live week 346, recents ok, label no; Stage 1 L6M gain kept in the engine: 37%.
- ldef_perbook_u2 A7 (STRICT): L6M maxDD 5,897 vs 9,361, PRE maxDD 5,370 vs 8,625, L6M mean 129/wk, PRE mean -167/wk, live week -1,314, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 45%.
- ldef_perbook_u2 O7 (STRICT): L6M maxDD 6,088 vs 6,958, PRE maxDD 3,761 vs 4,797, L6M mean 155/wk, PRE mean -28/wk, live week -11, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 63%.
- pjkl_PB P7 (weak): L6M maxDD 200,861 vs 203,542, PRE maxDD 120,071 vs 122,169, L6M mean 627/wk, PRE mean 66/wk, live week -1,177, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 10%.
- pjkl_PB M7 (weak): L6M maxDD 45,824 vs 48,019, PRE maxDD 43,648 vs 44,205, L6M mean -186/wk, PRE mean -18/wk, live week -382, recents ok, label no; Stage 1 L6M gain kept in the engine: 11%.
- pjkl_PB U7 (STRICT): L6M maxDD 8,119 vs 17,816, PRE maxDD 30,546 vs 39,542, L6M mean -570/wk, PRE mean -299/wk, live week -2,110, recents ok, label no; Stage 1 L6M gain kept in the engine: 89%.
- pjkl_PB H7 (STRICT): L6M maxDD 12,781 vs 16,242, PRE maxDD 11,190 vs 18,436, L6M mean -348/wk, PRE mean -717/wk, live week 3,175, recents ok, label no; Stage 1 L6M gain kept in the engine: 45%.
- bc_a_recent M7 (STRICT): L6M maxDD 39,410 vs 48,019, PRE maxDD 28,806 vs 44,205, L6M mean 108/wk, PRE mean 449/wk, live week -620, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: n/a.
- bc_a_recent U7 (weak): L6M maxDD 14,897 vs 17,816, PRE maxDD 40,537 vs 39,542, L6M mean -550/wk, PRE mean -117/wk, live week 4,315, recents ok, label no; Stage 1 L6M gain kept in the engine: 19%.
- exla_pb1 K7 (STRICT): L6M maxDD 32,823 vs 35,969, PRE maxDD 19,161 vs 22,188, L6M mean -179/wk, PRE mean -22/wk, live week 477, recents ok, label no; Stage 1 L6M gain kept in the engine: 40%.
- exla_pb1 P7 (STRICT): L6M maxDD 170,616 vs 203,542, PRE maxDD 111,795 vs 122,169, L6M mean -62/wk, PRE mean -825/wk, live week -15,056, recents ok, label no; Stage 1 L6M gain kept in the engine: 39%.
- exla_pb1 M7 (STRICT): L6M maxDD 30,434 vs 48,019, PRE maxDD 28,296 vs 44,205, L6M mean 615/wk, PRE mean 398/wk, live week 724, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 57%.
- exla_pb1 U7 (weak): L6M maxDD 12,944 vs 17,816, PRE maxDD 40,501 vs 39,542, L6M mean 136/wk, PRE mean -243/wk, live week 0, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 35%.
- exla_pb1 A7 (STRICT): L6M maxDD 6,849 vs 9,361, PRE maxDD 5,200 vs 8,625, L6M mean -532/wk, PRE mean -225/wk, live week -1,305, recents ok, label no; Stage 1 L6M gain kept in the engine: 34%.
- exla_pb1 H7 (STRICT): L6M maxDD 7,348 vs 16,242, PRE maxDD 16,721 vs 18,436, L6M mean 286/wk, PRE mean -157/wk, live week 319, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 109%.
- exla_pb1 O7 (STRICT): L6M maxDD 5,668 vs 6,958, PRE maxDD 4,172 vs 4,797, L6M mean 70/wk, PRE mean 11/wk, live week 77, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 54%.

## ldef_perbook_u2  (LDEF_perbook, side loss, stage S2, 43 of 43 months run)

| book | rule | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | live week | S1 L6M maxDD w/wo | S1 L6M gain kept in S2 | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | [4.0, 30.0, 120.0, 0.3, 0.0, 0.0, 0.0, 0 | 2,762 | -235 | 567 | 642 | -352 | -2,397 | -1,045 | 438 | 27,455 / 35,969 | 25,051 / 22,188 | -9,348 / -20,829 | 1,189 | 16,066 / 20,902 | 176% | rec-ok | LEAD |
| P7 | [0.0, 40.0, 0.0, 0.0, 0.0, 2.0, 2.0, 0.0 | 2,368 | 299 | -86 | 321 | 1,242 | -1,562 | 1,507 | 160 | 203,778 / 203,542 | 113,897 / 122,169 | -151,804 / -181,468 | -7,065 | 73,646 / 133,887 | -0% | rec-ok | no FAILS-LIVE-WEEK |
| M7 | [0.0, 10.0, 0.0, 0.0, 0.0, 2.0, 0.0, 0.0 | -522 | -201 | 634 | -133 | -632 | -463 | -212 | -545 | 37,288 / 48,019 | 44,115 / 44,205 | -59,617 / -73,536 | -1,985 | 13,450 / 44,425 | 35% | rec-ok | no |
| U7 | [3.0, 10.0, 50.0, 0.0, 0.0, 0.0, 0.0, 0. | 1,047 | -171 | 229 | -93 | 19 | -440 | -369 | -320 | 13,232 / 17,816 | 39,558 / 39,542 | 15,665 / 17,704 | 346 | 9,322 / 21,561 | 37% | rec-ok | no |
| A7 | [3.0, 20.0, 50.0, 0.0, 0.0, 0.0, 0.0, 0. | 599 | 239 | 369 | 129 | 40 | -96 | -167 | 38 | 5,897 / 9,361 | 5,370 / 8,625 | -244 / -7,321 | -1,314 | 4,760 / 12,461 | 45% | rec-ok | CANDIDATE-DD FAILS-LIVE-WEEK |
| H7 | [1.0, 15.0, 30.0, 12.0, 0.0, 0.0, 0.0, 0 | 145 | 398 | 454 | -585 | -362 | 253 | -457 | 106 | 11,961 / 16,242 | 24,640 / 18,436 | -17,621 / -13,688 | 697 | 8,823 / 15,477 | 64% | rec-ok | no |
| O7 | [3.0, 20.0, 30.0, 0.0, 0.0, 0.0, 0.0, 0. | 387 | 311 | 378 | 155 | -146 | -179 | -28 | -17 | 6,088 / 6,958 | 3,761 / 4,797 | -6,479 / -11,023 | -11 | 6,093 / 7,469 | 63% | rec-ok | CANDIDATE-DD |

Stack (all books of the set together, engine):
- L6M maxDD 186,059 vs 191,045 never-cut vs 82,873 S1b-COMB; PRE maxDD 123,968 vs 130,824; L6M mean delta -845 (MDE 5,893); worst-20 L6M -43,367 vs -63,404.

**Decisive reading for ldef_perbook_u2:** STRICT (L6M and PRE maxDD both at least 2% lower than the engine never-cut, recents ok, live week not failing): O7. WEAK (L6M maxDD lower, PRE within +5%, recents ok, live ok): M7, U7, O7. (strict-lowering: A7, O7; weak-lowering: M7, U7, A7, O7; recents-ok: K7, P7, M7, U7, A7, H7, O7; live-ok: K7, M7, U7, H7, O7).

## pjkl_PB  (PJKL_perbook_best, side profit, stage S2, 43 of 43 months run)

| book | rule | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | live week | S1 L6M maxDD w/wo | S1 L6M gain kept in S2 | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | [0.0, 0.5, 0.0, 0.0, 0.0, 0.0] | -936 | 1,807 | 2,117 | -529 | -1,643 | -3,837 | -861 | 944 | 21,984 / 35,969 | 25,019 / 22,188 | -21,121 / -20,829 | -660 | 8,253 / 20,902 | 111% | rec-ok | no |
| P7 | [0.9, 2.0, 2.0, 1.0] | -313 | 517 | 211 | 627 | 151 | 534 | 66 | -46 | 200,861 / 203,542 | 120,071 / 122,169 | -161,384 / -181,468 | -1,177 | 106,705 / 133,887 | 10% | rec-ok | CANDIDATE-DD |
| M7 | [0.3, 1.0, 10.0, 1.0] | -328 | 0 | -88 | -186 | -93 | -4 | -18 | 13 | 45,824 / 48,019 | 43,648 / 44,205 | -76,678 / -73,536 | -382 | 25,111 / 44,425 | 11% | rec-ok | no FAILS-LIVE-WEEK |
| U7 | [0.0, 0.75, 0.0, 0.0, 0.0, 0.0] | 2,179 | -1,976 | -508 | -570 | -168 | -1,394 | -299 | -622 | 8,119 / 17,816 | 30,546 / 39,542 | 19,791 / 17,704 | -2,110 | 10,661 / 21,561 | 89% | rec-ok | no |
| H7 | [0.0, 0.5, 0.0, 0.0, 0.0, 0.0] | 454 | -625 | -49 | -348 | -12 | -310 | -717 | -292 | 12,781 / 16,242 | 11,190 / 18,436 | -1,938 / -13,688 | 3,175 | 7,798 / 15,477 | 45% | rec-ok | no |

Stack (all books of the set together, engine):
- L6M maxDD 153,389 vs 191,045 never-cut vs 82,873 S1b-COMB; PRE maxDD 149,858 vs 130,824; L6M mean delta -1,665 (MDE 5,919); worst-20 L6M -50,573 vs -63,404.

**Decisive reading for pjkl_PB:** STRICT (L6M and PRE maxDD both at least 2% lower than the engine never-cut, recents ok, live week not failing): U7, H7. WEAK (L6M maxDD lower, PRE within +5%, recents ok, live ok): P7, U7, H7. (strict-lowering: U7, H7; weak-lowering: P7, M7, U7, H7; recents-ok: K7, P7, M7, U7, H7; live-ok: K7, P7, U7, H7).

## bc_a_recent  (LBC_A_recent, side loss, stage S2, 43 of 43 months run)

| book | rule | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | live week | S1 L6M maxDD w/wo | S1 L6M gain kept in S2 | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | [1, 0.4042550027370453, 2, 1, 1, 0.45] | 4,915 | 894 | 1,826 | 1,491 | 1,065 | 1,075 | -425 | 97 | 22,732 / 35,969 | 26,891 / 22,188 | -1,823 / -20,829 | 365 | 52,168 / 20,902 | n/a | rec-ok | LEAD |
| P7 | [-1, -43.415122985839844, 20, 1, 0, 35.0 | 695 | -966 | -490 | 331 | 9 | -2,278 | -81 | -92 | 203,570 / 203,542 | 129,571 / 122,169 | -149,853 / -181,468 | 0 | 133,887 / 133,887 | n/a | rec-ok | no |
| M7 | [-1, -0.5588240027427673, 2, 0, 0, 15.0] | 1,315 | 57 | 946 | 108 | -453 | 214 | 449 | -489 | 39,410 / 48,019 | 28,806 / 44,205 | -62,453 / -73,536 | -620 | 44,425 / 44,425 | n/a | rec-ok | CANDIDATE-DD |
| U7 | [1, 4.0, 5, 1, 1, 0.15] | 894 | -980 | 189 | -550 | -223 | 50 | -117 | 50 | 14,897 / 17,816 | 40,537 / 39,542 | 1,066 / 17,704 | 4,315 | 6,061 / 21,561 | 19% | rec-ok | no |
| A7 | [-1, -1.3333330154418945, 1, 1, 0, 40.0] | 0 | 40 | 27 | -50 | 5 | 189 | 86 | 8 | 9,821 / 9,361 | 5,949 / 8,625 | -9,516 / -7,321 | -1,925 | 12,461 / 12,461 | n/a | rec-ok | no FAILS-LIVE-WEEK |
| H7 | [1, 4.0, 3, 0, 0, 10.0] | -1,676 | -77 | -266 | -1,007 | -363 | 633 | -248 | 155 | 19,900 / 16,242 | 14,020 / 18,436 | -24,945 / -13,688 | 1,660 | 33,502 / 15,477 | n/a | rec-ok | no |
| O7 | [1, 4.0, 5, 1, 1, 0.15] | 973 | 389 | -4 | 111 | -150 | 84 | -242 | 2 | 3,284 / 6,958 | 5,225 / 4,797 | -6,061 / -11,023 | 394 | 3,639 / 7,469 | 96% | rec-ok | LEAD |

Stack (all books of the set together, engine):
- L6M maxDD 194,286 vs 191,045 never-cut vs 82,873 S1b-COMB; PRE maxDD 139,790 vs 130,824; L6M mean delta 523 (MDE 5,531); worst-20 L6M -57,815 vs -63,404.

**Decisive reading for bc_a_recent:** STRICT (L6M and PRE maxDD both at least 2% lower than the engine never-cut, recents ok, live week not failing): M7. WEAK (L6M maxDD lower, PRE within +5%, recents ok, live ok): M7, U7. (strict-lowering: M7; weak-lowering: M7, U7; recents-ok: K7, P7, M7, U7, A7, H7, O7; live-ok: K7, P7, M7, U7, H7, O7).

## exla_pb1  (A_perbook_best1, side loss, stage S2, 43 of 43 months run)

| book | rule | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | live week | S1 L6M maxDD w/wo | S1 L6M gain kept in S2 | recents | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | [0, 45, 8, 5, 10, 1, 5, 0, 0, 0] | 1,176 | 472 | 851 | -179 | -88 | 367 | -22 | 12 | 32,823 / 35,969 | 19,161 / 22,188 | -26,743 / -20,829 | 477 | 12,998 / 20,902 | 40% | rec-ok | no |
| P7 | [0, 25, 15, 5, 3, 1, 5, 0, 0, 0] | -705 | -1,855 | -748 | -62 | 232 | -2,427 | -825 | -170 | 170,616 / 203,542 | 111,795 / 122,169 | -118,319 / -181,468 | -15,056 | 49,143 / 133,887 | 39% | rec-ok | no FAILS-LIVE-WEEK |
| M7 | [0, 10, 4, 5, 20, 1, 5, 0, 0, 0] | 1,355 | -343 | 471 | 615 | -388 | -707 | 398 | 328 | 30,434 / 48,019 | 28,296 / 44,205 | -57,004 / -73,536 | 724 | 13,483 / 44,425 | 57% | rec-ok | CANDIDATE-DD |
| U7 | [0, 30, 20, 5, 3, 0, 0, 0, 2, 0] | 1,593 | 663 | 810 | 136 | 382 | 601 | -243 | 148 | 12,944 / 17,816 | 40,501 / 39,542 | 19,591 / 17,704 | 0 | 7,821 / 21,561 | 35% | rec-ok | CANDIDATE-DD |
| A7 | [0, 15, 8, 1, 1, 1, 1, 0, 0, 0] | -53 | -186 | 224 | -532 | -162 | 820 | -225 | -103 | 6,849 / 9,361 | 5,200 / 8,625 | -10,164 / -7,321 | -1,305 | 5,010 / 12,461 | 34% | rec-ok | no |
| H7 | [0, 10, 30, 10, 3, 1, 10, 0, 0, 0] | 332 | 359 | 834 | 286 | -37 | -357 | -157 | 34 | 7,348 / 16,242 | 16,721 / 18,436 | -8,214 / -13,688 | 319 | 7,329 / 15,477 | 109% | rec-ok | CANDIDATE-DD |
| O7 | [5, 0.25, 60, 15, 1, 0, 0, 0, 0, 0] | 344 | 462 | 290 | 70 | -36 | 243 | 11 | 31 | 5,668 / 6,958 | 4,172 / 4,797 | -7,698 / -11,023 | 77 | 5,063 / 7,469 | 54% | rec-ok | CANDIDATE-DD |

Stack (all books of the set together, engine):
- L6M maxDD 146,479 vs 191,045 never-cut vs 82,873 S1b-COMB; PRE maxDD 127,482 vs 130,824; L6M mean delta -1,626 (MDE 6,510); worst-20 L6M -17,450 vs -63,404.

**Decisive reading for exla_pb1:** STRICT (L6M and PRE maxDD both at least 2% lower than the engine never-cut, recents ok, live week not failing): K7, M7, A7, H7, O7. WEAK (L6M maxDD lower, PRE within +5%, recents ok, live ok): K7, M7, U7, A7, H7, O7. (strict-lowering: K7, P7, M7, A7, H7, O7; weak-lowering: K7, P7, M7, U7, A7, H7, O7; recents-ok: K7, P7, M7, U7, A7, H7, O7; live-ok: K7, M7, U7, A7, H7, O7).
