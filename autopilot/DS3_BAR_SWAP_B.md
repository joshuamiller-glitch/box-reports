# DS3 BAR SWAP B (W-SWB): P7 / H7 / A7 / O7 on every bar row

Rule: standing selection rule (CLAUDE.md, user 11-17 18:10Z/18:13Z): pick on the trailing 6 months to the newest data, trailing 3M beside it; validated by rolling walk-forward; older years tolerant (AMBER 15-30% / RED >30% worse than the live bar). FIRST PASS standalone (tape fills, raw chassis, live bracket); engine swap test is section 4.
Pick window: 2026-05-04..2026-10-30 (trailing 6M); data end 2026-10-30; refit 2026-11-17 18:40:28 UTC (loop every 30 min, bi-weekly refit rule); trials counted 3043 candidates (rows x param sets x cells), correction White RC / Hansen SPA per cell on weekly differences vs the live bar; PBO not used (rolling walk-forward instead); in-sample = trailing window, walk-forward = month-end picks from 2023-10, untouched = none frozen.

## Plain summary
- Tried: every available bar row (time, activity, information, price, composite as they land) as the signal clock of P7, H7, A7, O7, standalone on the tape with live brackets.
- Holds / does not: see cell tables; "pick" is the best trailing-6M row, label shows whether walk-forward persistence and the older-year check support it.
- Needs in DS7: per row (native NT8 bar type or a custom BarsType with the build rule given).
- Engine: swap test (section 4) runs only on the picks; until it lands nothing is CONFIRMED.
- Next: grid re-fit for the top rows, random-clock nulls, engine swap sets TL3_SWB_*.

## 1. Fidelity (live time bar vs engine raw chassis S0, sig_ts within 2 s)

Pipeline bars (MBO trades table, tm60):

|           |   mean |   sum |   size |
|:----------|-------:|------:|-------:|
| ('A7', 0) | 0.9589 |   816 |    851 |
| ('H7', 0) | 0.9752 |   512 |    525 |
| ('H7', 3) | 0.9938 |   320 |    322 |
| ('O7', 3) | 0.9714 |   374 |    385 |
| ('P7', 0) | 0.9931 |  1579 |   1590 |
| ('P7', 1) | 1      |  1231 |   1231 |
| ('P7', 3) | 0.9882 |  1342 |   1358 |

Engine own 1-min bars (month cache, all 43 months):

|           |   mean |   size |
|:----------|-------:|-------:|
| ('A7', 0) | 0.9966 |   1165 |
| ('H7', 0) | 0.9898 |    684 |
| ('H7', 3) | 1      |    411 |
| ('O7', 3) | 1      |    506 |
| ('P7', 0) | 0.9991 |   2128 |
| ('P7', 1) | 1      |   1664 |
| ('P7', 3) | 1      |   1803 |

Finding: the live bar closes at the FIRST PRINT AFTER the boundary (thin Asia/London: 2-14 s late); regime / HMA / ATR buckets use the NOMINAL boundary. Remaining pipeline misses (A7 ~96%) are ts_event vs ts_recv on thin Asia / Sunday-open minutes and months missing from the bar store (O7 median history).

## 2. Book-on-bar by cell (standalone, net points per 1 lot incl. 4.84 RT and slip; $ = pts x 20 x live lots)

### P7 NY AM

Live bar row `tm60__A`: 6M -1705 pts (n 537, ulcer 1027, maxDD 2292), 3M -1431 pts. PICK (trailing 6M, pick): `mrenko_80__A` 722 pts (n 88, ulcer 102, maxDD 303); 3M-pick: `cdr_1000__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| frenko_112__A | 624 | 52 | 73 | 186 | 350 | 3361 |
| mrenko_80__A | 722 | 88 | 102 | 303 | 254 | 3889 |
| mrenko_56__A | 1001 | 176 | 182 | 456 | 205 | 5391 |
| trb_10000__A | 681 | 108 | 138 | 359 | 296 | 3668 |
| cdr_1000__A | 362 | 39 | 74 | 123 | 236 | 1951 |
| mom_80__A | 771 | 138 | 158 | 469 | 549 | 4149 |
| tsf_25_250__A | 579 | 41 | 122 | 229 | -111 | 3118 |
| tib_400__B | 2858 | 1626 | 653 | 1697 | 294 | 15391 |
| drb_10000__A | 569 | 92 | 150 | 405 | 141 | 3062 |
| urenko_80__A | 796 | 94 | 222 | 520 | 49 | 4283 |
| tm1200__B | 566 | 80 | 162 | 434 | 497 | 3046 |
| drb_3500__B | 935 | 195 | 268 | 608 | 422 | 5034 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | -159.2 | -421.8 | 0.60 | 717 | 1245 |
| 6M->3M | 5 | -95.5 | -312.0 | 0.60 | 1683 | 2224 |
| 3M->1M | 5 | 20.1 | -421.8 | 0.80 | 205 | 1245 |
| 3M->3M | 5 | -34.6 | -312.0 | 0.80 | 915 | 2224 |
| 12M->1M | 5 | -280.6 | -421.8 | 0.60 | 1119 | 1245 |
| 12M->3M | 5 | -144.6 | -312.0 | 0.60 | 2077 | 2224 |
| 6M->2w | 5 | -187.4 | -99.3 | 0.40 | 540 | 286 |

Nulls (same pick procedure): shift11: OOS -17.0/mo share beat 0.80; shift23: OOS 75.0/mo share beat 0.80; shift37: OOS -98.8/mo share beat 0.80

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -159 vs -422 (n 5); +3M -82 vs -426 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.133, 'spa_p': 0.154, 'T': 26, 'K': 415}

**Deliverable row**: P7 NY AM: bar today 1-minute time (live) -> proposed mrenko_80 | construction: mrenko_80 (median / mean Renko: brick N; reversal brick opens at the midpoint of last brick, triggers at 1.5N from last close) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (MedianRenko / MeanRenko third-party) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### P7 London

Live bar row `tm60__A`: 6M 2026 pts (n 559, ulcer 234, maxDD 558), 3M 805 pts. PICK (trailing 6M, pick): `cusum_14__A` 1588 pts (n 150, ulcer 40, maxDD 185); 3M-pick: `cusum_14__A` (agrees).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cusum_14__A | 1588 | 150 | 40 | 185 | 1588 | 8552 |
| cusum_10__B | 1709 | 169 | 44 | 222 | 1709 | 9202 |
| rng_80__A | 1881 | 110 | 56 | 188 | 481 | 10127 |
| cusum_14__B | 1430 | 153 | 61 | 280 | 1430 | 7700 |
| dchg_14__A | 1138 | 124 | 56 | 307 | 1138 | 6125 |
| rng_80__B | 1340 | 101 | 67 | 255 | 493 | 7216 |
| dchg_40__B | 644 | 47 | 39 | 144 | 644 | 3467 |
| dchg_14__B | 1084 | 125 | 70 | 243 | 1084 | 5836 |
| kagi_40__B | 1408 | 121 | 93 | 298 | 1032 | 7583 |
| cusum_10__A | 1174 | 170 | 88 | 300 | 1174 | 6322 |
| mom_28__A | 1409 | 243 | 125 | 561 | 880 | 7586 |
| tm120__A | 1712 | 451 | 154 | 483 | 525 | 9217 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | -33.4 | 391.6 | 0.20 | 590 | 187 |
| 6M->3M | 5 | -3.3 | 282.9 | 0.00 | 989 | 185 |
| 3M->1M | 5 | 133.1 | 391.6 | 0.40 | 268 | 187 |
| 3M->3M | 5 | 120.0 | 282.9 | 0.20 | 239 | 185 |
| 12M->1M | 5 | -57.8 | 391.6 | 0.20 | 638 | 187 |
| 12M->3M | 5 | -10.8 | 282.9 | 0.00 | 981 | 185 |
| 6M->2w | 5 | 24.4 | 476.2 | 0.20 | 304 | 121 |

Nulls (same pick procedure): shift11: OOS 166.9/mo share beat 0.20; shift23: OOS 73.4/mo share beat 0.40; shift37: OOS 225.7/mo share beat 0.20

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -33 vs 392 (n 5); +3M 88 vs 263 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.999, 'spa_p': 0.995, 'T': 26, 'K': 348}

**Deliverable row**: P7 London: bar today 1-minute time (live) -> proposed cusum_14 | construction: cusum_14 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### H7 NY AM

Live bar row `tm60__A`: 6M 915 pts (n 92, ulcer 147, maxDD 366), 3M 608 pts. PICK (trailing 6M, pick): `drb_2000__B` 903 pts (n 40, ulcer 49, maxDD 182); 3M-pick: `lbrk_4_10__B` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| drb_2000__B | 903 | 40 | 49 | 182 | 728 | 1389 |
| rng_56__A | 944 | 49 | 60 | 154 | 701 | 1452 |
| vnorm_150__A | 885 | 47 | 57 | 182 | 423 | 1362 |
| pnf_10__A | 863 | 47 | 59 | 219 | 483 | 1328 |
| mrenko_28__B | 796 | 43 | 55 | 132 | 351 | 1225 |
| dib_400__A | 981 | 72 | 70 | 184 | 473 | 1509 |
| tm300__C | 1051 | 88 | 75 | 182 | 532 | 1616 |
| tm300__A | 1051 | 88 | 75 | 182 | 532 | 1616 |
| dib_6000__B | 1200 | 101 | 98 | 295 | 793 | 1846 |
| trb_1200__B | 1033 | 72 | 86 | 232 | 460 | 1589 |
| lbrk_3_10__A | 630 | 42 | 52 | 153 | 351 | 969 |
| renko_56__C | 790 | 44 | 68 | 182 | 350 | 1215 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | -123.3 | 160.7 | 0.00 | 849 | 106 |
| 6M->3M | 5 | -224.7 | 168.7 | 0.00 | 2547 | 70 |
| 3M->1M | 5 | -169.4 | 160.7 | 0.00 | 1041 | 106 |
| 3M->3M | 5 | -67.7 | 168.7 | 0.00 | 1441 | 70 |
| 12M->1M | 5 | -163.1 | 160.7 | 0.20 | 868 | 106 |
| 12M->3M | 5 | -257.8 | 168.7 | 0.00 | 2587 | 70 |
| 6M->2w | 5 | 61.4 | 112.8 | 0.40 | 132 | 58 |

Nulls (same pick procedure): shift11: OOS -72.7/mo share beat 0.20; shift23: OOS -210.9/mo share beat 0.00; shift37: OOS 82.5/mo share beat 0.40

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -123 vs 161 (n 5); +3M -482 vs 222 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 1.0, 'spa_p': 0.996, 'T': 26, 'K': 451}

**Deliverable row**: H7 NY AM: bar today 1-minute time (live) -> proposed drb_2000 | construction: drb_2000 (dollar-run bar (Lopez de Prado): close when max(sum of w over buys, sum over sells) >= E[T]*max(P(buy)E[w|buy],P(sell)E[w|sell])) | param set B | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (new code) | scaling: size x s_ntr (same, daily trade-print count) (new custom BarsType)

### O7 NY AM

Live bar row `tm60__A`: 6M 201 pts (n 66, ulcer 218, maxDD 445), 3M -4 pts. PICK (trailing 6M, pick): `urenko_20__A` 566 pts (n 72, ulcer 109, maxDD 250); 3M-pick: `tm10__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| urenko_20__A | 566 | 72 | 109 | 250 | 55 | 870 |
| vib_400__A | 541 | 67 | 112 | 267 | 398 | 833 |
| tm10__A | 623 | 65 | 129 | 321 | 608 | 959 |
| tsf_5_200__A | 583 | 62 | 129 | 397 | 177 | 897 |
| urenko_28__A | 540 | 67 | 137 | 354 | 527 | 831 |
| tsf_2_2000__A | 596 | 49 | 161 | 478 | 69 | 917 |
| tm30__A | 515 | 70 | 166 | 388 | 316 | 792 |
| tsf_2_200__A | 412 | 67 | 142 | 345 | 397 | 634 |
| vib_240__A | 449 | 66 | 164 | 373 | 436 | 691 |
| vib_6000__A | 363 | 66 | 142 | 389 | -42 | 559 |
| trb_400__A | 262 | 61 | 108 | 267 | 307 | 403 |
| tsf_2_400__A | 334 | 65 | 142 | 299 | 307 | 514 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 4 | 7.8 | 50.4 | 0.25 | 241 | 151 |
| 6M->3M | 4 | -17.7 | -22.6 | 0.50 | 375 | 440 |
| 3M->1M | 5 | -83.1 | -30.9 | 0.40 | 292 | 230 |
| 3M->3M | 5 | -35.0 | 0.2 | 0.40 | 495 | 397 |
| 12M->1M | 1 | -225.9 | -364.9 | 1.00 | 122 | 209 |
| 12M->3M | 1 | -75.3 | -121.6 | 1.00 | 122 | 209 |
| 6M->2w | 4 | -14.5 | -19.6 | 0.75 | 129 | 113 |

Nulls (same pick procedure): shift11: OOS 25.8/mo share beat 0.50; shift23: OOS 72.3/mo share beat 1.00; shift37: OOS 162.2/mo share beat 1.00

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 8 vs 50 (n 4); +3M -55 vs -190 (n 2); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.742, 'spa_p': 0.664, 'T': 26, 'K': 41}

**Deliverable row**: O7 NY AM: bar today 1-minute time (live) -> proposed urenko_20 | construction: urenko_20 (UniRenko: brick N, reversal brick opens at last close and closes N beyond (reversal 1N)) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (user has UniRenko) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### A7 Asia (phase 2)

Live bar row `tm60__A`: 6M 57 pts (n 367, ulcer 418, maxDD 972), 3M -592 pts. PICK (trailing 6M, pick): `tm900__A` 723 pts (n 33, ulcer 30, maxDD 106); 3M-pick: `tsf_5_200__B` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| tm900__A | 723 | 33 | 30 | 106 | 115 | 1113 |
| tm300__A | 768 | 55 | 58 | 154 | 522 | 1181 |
| drb_700__B | 958 | 129 | 83 | 191 | 312 | 1474 |
| dib_10000__B | 1202 | 117 | 111 | 318 | 644 | 1849 |
| renko_40__B | 682 | 60 | 63 | 182 | 385 | 1049 |
| renko_14__A | 1630 | 343 | 157 | 410 | 547 | 2508 |
| mrenko_40__B | 666 | 75 | 65 | 189 | 336 | 1024 |
| tick_5000__B | 525 | 33 | 52 | 121 | 132 | 807 |
| trb_700__B | 975 | 156 | 106 | 285 | 349 | 1501 |
| dchg_28__B | 379 | 30 | 44 | 121 | 379 | 583 |
| tsf_5_200__B | 708 | 49 | 86 | 344 | 619 | 1089 |
| swing_pct_12__B | 287 | 50 | 36 | 126 | 271 | 442 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | 61.6 | 11.2 | 0.60 | 313 | 484 |
| 6M->3M | 5 | -60.8 | -75.4 | 0.60 | 1341 | 1090 |
| 3M->1M | 5 | 156.9 | 11.2 | 0.80 | 159 | 484 |
| 3M->3M | 5 | -18.0 | -75.4 | 0.60 | 1106 | 1090 |
| 12M->1M | 5 | 115.8 | 11.2 | 0.60 | 278 | 484 |
| 12M->3M | 5 | -42.7 | -75.4 | 0.60 | 1321 | 1090 |
| 6M->2w | 5 | -319.5 | -53.8 | 0.40 | 880 | 327 |

Nulls (same pick procedure): shift11: OOS 166.7/mo share beat 0.60; shift23: OOS -56.3/mo share beat 0.40; shift37: OOS 242.7/mo share beat 0.60

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 62 vs 11 (n 5); +3M -121 vs -268 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.415, 'spa_p': 0.21, 'T': 26, 'K': 320}

**Deliverable row**: A7 Asia: bar today 1-minute time (live) -> proposed tm900 | construction: 15-minute time bar | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native NT8 Minute bar (OnBarClose at the first print after the boundary) (native)

### P7 Asia (phase 2)

Live bar row `tm60__A`: 6M 1474 pts (n 655, ulcer 300, maxDD 722), 3M 938 pts. PICK (trailing 6M, pick): `cusum_40__B` 659 pts (n 64, ulcer 34, maxDD 151); 3M-pick: `pnf_20__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cusum_40__B | 659 | 64 | 34 | 151 | 659 | 6083 |
| urenko_56__A | 892 | 81 | 55 | 188 | 364 | 8237 |
| renko_40__A | 967 | 94 | 63 | 152 | 551 | 8930 |
| cusum_14__A | 814 | 142 | 59 | 277 | 814 | 7515 |
| tick_8000__A | 534 | 33 | 46 | 125 | 222 | 4928 |
| tib_700__B | 2695 | 793 | 238 | 739 | 764 | 24880 |
| cusum_56__A | 410 | 43 | 36 | 121 | 410 | 3787 |
| cdr_400__B | 474 | 35 | 45 | 185 | 203 | 4375 |
| cusum_10__A | 830 | 158 | 80 | 293 | 830 | 7659 |
| tsf_2_100__A | 2065 | 594 | 205 | 545 | 1028 | 19062 |
| cdr_400__A | 468 | 36 | 46 | 185 | 321 | 4320 |
| drb_3500__B | 702 | 69 | 72 | 240 | 660 | 6482 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | -211.5 | 375.7 | 0.00 | 1076 | 292 |
| 6M->3M | 5 | 14.8 | 230.2 | 0.00 | 539 | 371 |
| 3M->1M | 5 | -197.2 | 375.7 | 0.00 | 1012 | 292 |
| 3M->3M | 5 | 15.9 | 230.2 | 0.00 | 548 | 371 |
| 12M->1M | 5 | 293.3 | 375.7 | 0.20 | 854 | 292 |
| 12M->3M | 5 | 143.8 | 230.2 | 0.20 | 961 | 371 |
| 6M->2w | 5 | -717.4 | 283.7 | 0.20 | 1455 | 208 |

Nulls (same pick procedure): shift11: OOS -206.1/mo share beat 0.00; shift23: OOS -254.7/mo share beat 0.00; shift37: OOS 36.1/mo share beat 0.20

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -211 vs 376 (n 5); +3M 230 vs 253 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.852, 'spa_p': 0.784, 'T': 26, 'K': 365}

**Deliverable row**: P7 Asia: bar today 1-minute time (live) -> proposed cusum_40 | construction: cusum_40 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set B | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### H7 Asia (phase 2)

Live bar row `tm60__A`: 6M 508 pts (n 133, ulcer 188, maxDD 392), 3M 115 pts. PICK (trailing 6M, pick): `dib_400__A` 1268 pts (n 113, ulcer 96, maxDD 301); 3M-pick: `tib_1200__B` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| pnf_5__A | 950 | 89 | 64 | 184 | 251 | 5118 |
| dib_400__A | 1268 | 113 | 96 | 301 | 434 | 6826 |
| tm1800__A | 768 | 35 | 59 | 183 | 426 | 4137 |
| tm1800__C | 768 | 35 | 59 | 183 | 426 | 4137 |
| tib_1200__B | 1425 | 136 | 111 | 368 | 877 | 7674 |
| trb_400__C | 2306 | 353 | 180 | 468 | 529 | 12414 |
| dlt_70__A | 818 | 89 | 68 | 148 | 537 | 4403 |
| urenko_28__C | 1512 | 141 | 139 | 381 | 948 | 8142 |
| drb_400__C | 1578 | 292 | 147 | 409 | 957 | 8499 |
| tsf_2_400__C | 1393 | 134 | 132 | 369 | 450 | 7502 |
| dib_1200__B | 1284 | 130 | 122 | 365 | -5 | 6912 |
| drb_400__A | 957 | 96 | 97 | 246 | 418 | 5152 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 5 | 221.1 | 140.4 | 0.40 | 142 | 142 |
| 6M->3M | 5 | 35.6 | 122.2 | 0.00 | 628 | 144 |
| 3M->1M | 5 | 193.0 | 140.4 | 0.40 | 158 | 142 |
| 3M->3M | 5 | 41.7 | 122.2 | 0.20 | 607 | 144 |
| 12M->1M | 5 | 77.4 | 140.4 | 0.20 | 631 | 142 |
| 12M->3M | 5 | 76.8 | 122.2 | 0.20 | 562 | 144 |
| 6M->2w | 5 | 109.5 | 300.6 | 0.20 | 130 | 101 |

Nulls (same pick procedure): shift11: OOS 37.2/mo share beat 0.40; shift23: OOS 168.3/mo share beat 0.60; shift37: OOS 305.2/mo share beat 0.60

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 221 vs 140 (n 5); +3M -102 vs 78 (n 3); +6M nan vs nan (n 0)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **GREEN**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.584, 'spa_p': 0.61, 'T': 26, 'K': 382}

**Deliverable row**: H7 Asia: bar today 1-minute time (live) -> proposed dib_400 | construction: dib_400 (dollar-imbalance bar (Lopez de Prado): theta = sum b_t*w_t (b = aggressor side, tick rule if none; w = dollars); close when |theta| >= E[T]*max(|EWMA(b w)|, EWMA|w|/sqrt(E[T])); E[T] = EWMA(0.2) of ba) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (stateful EWMA; buildable, new code) | scaling: size x s_ntr (same, daily trade-print count) (new custom BarsType)

## 4. Engine swap test
Not yet run (hook th_swb/swb_inject.py; sets TL3_SWB_*; queue /mnt/l2/l2vast/_major_sw/pending_b.txt).
