# DS3 BAR SWAP B (W-SWB): P7 / H7 / A7 / O7 on every bar row

Rule: standing selection rule (CLAUDE.md, user 11-17 18:10Z/18:13Z): pick on the trailing 6 months to the newest data, trailing 3M beside it; validated by rolling walk-forward; older years tolerant (AMBER 15-30% / RED >30% worse than the live bar). FIRST PASS standalone (tape fills, raw chassis, live bracket); engine swap test is section 4.
Pick window: 2026-05-18..2026-11-13 (trailing 6M); data end 2026-11-13; refit 2026-11-17 19:34:44 UTC (loop every 30 min, bi-weekly refit rule); trials counted 4704 candidates (rows x param sets x cells), correction White RC / Hansen SPA per cell on weekly differences vs the live bar; PBO not used (rolling walk-forward instead); in-sample = trailing window, walk-forward = month-end picks from 2023-10, untouched = none frozen.

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

Live bar row `tm60__A`: 6M -1939 pts (n 529, ulcer 1136, maxDD 2315), 3M -1857 pts. PICK (trailing 6M, pick): `cdr_1000__A` 967 pts (n 69, ulcer 39, maxDD 134); 3M-pick: `cdr_1000__A` (agrees).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cdr_1000__A | 967 | 69 | 39 | 134 | 625 | 5206 |
| cdr_1000__G20t5 | 967 | 69 | 39 | 134 | 625 | 5206 |
| cdr_1000__G20k3 | 614 | 64 | 56 | 149 | 329 | 3308 |
| frenko_112__A | 682 | 65 | 77 | 186 | 290 | 3671 |
| mrenko_56__A | 1053 | 166 | 186 | 456 | 424 | 5669 |
| rc1200s1__A | 534 | 74 | 97 | 244 | 439 | 2877 |
| frenko_112__B | 506 | 58 | 105 | 199 | 318 | 2727 |
| cdr_250__G40k8 | 1011 | 359 | 211 | 497 | 488 | 5443 |
| drb_3500__B | 1253 | 225 | 272 | 608 | 881 | 6747 |
| mom_112__A | 886 | 81 | 205 | 524 | 194 | 4772 |
| mom_80__A | 786 | 168 | 187 | 469 | 543 | 4234 |
| trb_10000__A | 594 | 104 | 141 | 359 | 350 | 3196 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -73.4 | -74.6 | 0.43 | 1756 | 2066 |
| 6M->3M | 37 | -39.5 | -88.1 | 0.59 | 3210 | 5992 |
| 3M->1M | 37 | -7.7 | -74.6 | 0.59 | 748 | 2066 |
| 3M->3M | 37 | -21.4 | -88.1 | 0.68 | 2062 | 5992 |
| 12M->1M | 37 | 1.4 | -74.6 | 0.49 | 1059 | 2066 |
| 12M->3M | 37 | -10.8 | -88.1 | 0.65 | 2180 | 5992 |
| 6M->2w | 37 | -12.5 | 10.7 | 0.49 | 1085 | 1648 |

Nulls (same pick procedure): shift11: OOS -54.9/mo share beat 0.49; shift23: OOS -85.6/mo share beat 0.46; shift37: OOS -58.9/mo share beat 0.65; random-clock pool: OOS -13.7/mo share beat 0.51

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -75 vs -79 (n 36); +3M 2 vs -102 (n 34); +6M -32 vs -98 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 9.8 | -41.1 | -124% | -90% | -82% | GREEN |
| Y2023 | 0.0 | 77.9 | +100% | -100% | -100% | RED |
| Y2024 | 0.0 | 1.6 | +100% | -100% | -100% | RED |
| Y2025 | 12.5 | -30.5 | -141% | -89% | -83% | GREEN |
| Y2026 | 1.5 | -7.7 | -120% | -77% | -75% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.203, 'spa_p': 0.189, 'T': 26, 'K': 628}

**Deliverable row**: P7 NY AM: bar today 1-minute time (live) -> proposed cdr_1000 | construction: cdr_1000 (cumulative-delta-range bar: closes when (max - min) of the running cumulative delta inside the bar >= D) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType | scaling: size x s_vol; s_vol = trailing-20-prior-trading-date median of daily volume / R0 (R0 = median of the first 60 trading dates 2023-04..06, a unit consta (new custom BarsType)

### P7 London

Live bar row `tm60__A`: 6M 1575 pts (n 559, ulcer 200, maxDD 470), 3M 450 pts. PICK (trailing 6M, pick): `rng_80__A` 1804 pts (n 110, ulcer 69, maxDD 212); 3M-pick: `cdr_400__G10k5` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| rng_80__A | 1804 | 110 | 69 | 212 | 408 | 9713 |
| cusum_80__A | 1918 | 112 | 85 | 272 | 349 | 10330 |
| tm1800__A | 1156 | 65 | 64 | 189 | 306 | 6224 |
| cdr_400__G10k5 | 1203 | 82 | 70 | 186 | 727 | 6476 |
| cusum_80__B | 1585 | 110 | 94 | 283 | 276 | 8536 |
| kagi_40__B | 1618 | 153 | 98 | 298 | 929 | 8714 |
| dchg_40__B | 1618 | 153 | 98 | 298 | 929 | 8714 |
| cdr_400__G10k3 | 1156 | 94 | 72 | 186 | 580 | 6223 |
| rng_80__B | 1257 | 105 | 80 | 255 | 304 | 6770 |
| rc60s4__B | 2808 | 527 | 207 | 498 | 1213 | 15120 |
| rng_40__A | 1972 | 299 | 149 | 496 | 1162 | 10616 |
| rc60s3__B | 2114 | 547 | 162 | 501 | 820 | 11383 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -17.3 | -17.6 | 0.46 | 607 | 1806 |
| 6M->3M | 37 | -41.2 | -18.0 | 0.46 | 3841 | 5373 |
| 3M->1M | 37 | -10.4 | -17.6 | 0.51 | 708 | 1806 |
| 3M->3M | 37 | -1.7 | -18.0 | 0.62 | 1300 | 5373 |
| 12M->1M | 37 | -42.0 | -17.6 | 0.49 | 1075 | 1806 |
| 12M->3M | 37 | -49.1 | -18.0 | 0.43 | 4787 | 5373 |
| 6M->2w | 37 | -0.8 | -101.3 | 0.54 | 404 | 2126 |

Nulls (same pick procedure): shift11: OOS -3.9/mo share beat 0.49; shift23: OOS -26.1/mo share beat 0.49; shift37: OOS 20.6/mo share beat 0.51; random-clock pool: OOS -31.6/mo share beat 0.39

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -18 vs -14 (n 36); +3M -99 vs -22 (n 34); +6M -63 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 18.7 | 0.7 | -2713% | -74% | -73% | GREEN |
| Y2023 | 0.0 | 20.1 | +100% | -100% | -100% | RED |
| Y2024 | -13.9 | -32.4 | -57% | -79% | -64% | GREEN |
| Y2025 | 20.2 | -11.3 | -278% | -89% | -83% | GREEN |
| Y2026 | 10.6 | -4.6 | -329% | -79% | -70% | GREEN |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.894, 'spa_p': 0.772, 'T': 26, 'K': 558}

**Deliverable row**: P7 London: bar today 1-minute time (live) -> proposed rng_80 | construction: rng_80 (true range bar: bar closes when a print would make high-low > N ticks; that print opens the next bar; known at that print) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native Range (verify: NT8 closes when range reaches N ticks; see step C) | scaling: size x s_rng (same, daily high-low range in points) (native)

### H7 NY AM

Live bar row `tm60__A`: 6M 874 pts (n 86, ulcer 86, maxDD 245), 3M 445 pts. PICK (trailing 6M, pick): `vol_6000__A` 992 pts (n 43, ulcer 42, maxDD 135); 3M-pick: `drb_2000__B` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| vol_6000__A | 992 | 43 | 42 | 135 | 452 | 1527 |
| tm300__A | 1010 | 80 | 49 | 181 | 490 | 1554 |
| tm300__C | 1010 | 80 | 49 | 181 | 490 | 1554 |
| drb_2000__B | 1073 | 45 | 61 | 207 | 698 | 1651 |
| vsess_200__A | 1071 | 88 | 66 | 172 | 440 | 1648 |
| mrenko_28__B | 852 | 46 | 56 | 132 | 373 | 1311 |
| tsf_10_60__B | 784 | 30 | 53 | 181 | 204 | 1207 |
| trb_3500__A | 710 | 49 | 49 | 167 | 443 | 1092 |
| vnorm_150__A | 823 | 50 | 58 | 182 | 380 | 1266 |
| rc60s3__B | 840 | 73 | 63 | 185 | 540 | 1292 |
| dib_6000__B | 1371 | 125 | 105 | 295 | 793 | 2110 |
| vib_400__A | 960 | 86 | 74 | 184 | 381 | 1478 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | -63.5 | 12.1 | 0.41 | 2059 | 668 |
| 6M->3M | 37 | -7.3 | 4.9 | 0.51 | 1899 | 2222 |
| 3M->1M | 37 | 48.5 | 12.1 | 0.68 | 346 | 668 |
| 3M->3M | 37 | 23.5 | 4.9 | 0.65 | 656 | 2222 |
| 12M->1M | 37 | -33.9 | 12.1 | 0.41 | 724 | 668 |
| 12M->3M | 37 | -15.0 | 4.9 | 0.43 | 1750 | 2222 |
| 6M->2w | 37 | -35.4 | 4.3 | 0.46 | 680 | 458 |

Nulls (same pick procedure): shift11: OOS -29.3/mo share beat 0.49; shift23: OOS -16.8/mo share beat 0.54; shift37: OOS -23.0/mo share beat 0.54; random-clock pool: OOS 20.4/mo share beat 0.68

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M -68 vs 12 (n 36); +3M 43 vs 10 (n 34); +6M 68 vs 27 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -1.0 | -7.5 | -86% | -37% | -24% | GREEN |
| Y2023 | 0.0 | 1.9 | +100% | -100% | -100% | RED |
| Y2024 | 8.2 | -27.5 | -130% | -88% | -82% | GREEN |
| Y2025 | -0.4 | 14.1 | +103% | -61% | -33% | RED |
| Y2026 | 1.3 | 4.8 | +73% | -46% | -58% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 1.0, 'spa_p': 0.987, 'T': 26, 'K': 693}

**Deliverable row**: H7 NY AM: bar today 1-minute time (live) -> proposed vol_6000 | construction: vol_6000 (volume bar: closes when cumulative contracts >= N; closing print belongs to the closing bar (NT8 splits the closing print across bars; see C)) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native Volume | scaling: size x s_vol; s_vol = trailing-20-prior-trading-date median of daily volume / R0 (R0 = median of the first 60 trading dates 2023-04..06, a unit consta (native)

### O7 NY AM

Live bar row `tm60__A`: 6M 141 pts (n 65, ulcer 232, maxDD 445), 3M -3 pts. PICK (trailing 6M, pick): `frenko_56__A` 896 pts (n 56, ulcer 99, maxDD 225); 3M-pick: `tm10__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| frenko_56__A | 896 | 56 | 99 | 225 | 250 | 1379 |
| vsess_200__A | 692 | 60 | 85 | 188 | 289 | 1065 |
| vnorm_700__A | 841 | 66 | 111 | 266 | 437 | 1293 |
| mom_20__A | 702 | 63 | 95 | 250 | 518 | 1080 |
| cusum_28__A | 533 | 64 | 76 | 185 | 118 | 820 |
| frenko_28__A | 745 | 78 | 109 | 227 | 487 | 1146 |
| rng_40__A | 605 | 59 | 110 | 298 | 339 | 931 |
| cusum_40__A | 605 | 59 | 110 | 299 | 339 | 931 |
| rng_28__A | 483 | 62 | 89 | 234 | 118 | 744 |
| urenko_28__A | 663 | 64 | 124 | 330 | 428 | 1019 |
| swing_atr_0.4__A | 514 | 58 | 106 | 243 | 168 | 791 |
| tm10__A | 614 | 62 | 132 | 321 | 600 | 945 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 64.2 | 123.9 | 0.35 | 186 | 157 |
| 6M->3M | 37 | 78.0 | 125.9 | 0.30 | 292 | 202 |
| 3M->1M | 37 | 96.5 | 123.9 | 0.41 | 229 | 157 |
| 3M->3M | 37 | 78.7 | 125.9 | 0.35 | 357 | 202 |
| 12M->1M | 37 | 78.1 | 123.9 | 0.51 | 189 | 157 |
| 12M->3M | 37 | 88.2 | 125.9 | 0.38 | 209 | 202 |
| 6M->2w | 37 | 33.2 | 125.7 | 0.35 | 286 | 146 |

Nulls (same pick procedure): shift11: OOS 82.8/mo share beat 0.35; shift23: OOS 77.3/mo share beat 0.35; shift37: OOS 92.7/mo share beat 0.43; random-clock pool: OOS 0.0/mo share beat 1.00

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 63 vs 122 (n 36); +3M 82 vs 141 (n 34); +6M 86 vs 138 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 16.8 | 45.5 | +63% | +90% | +22% | RED |
| Y2023 | 0.0 | -13.3 | -100% | -100% | -100% | GREEN |
| Y2024 | 2.2 | 40.2 | +94% | -78% | -38% | RED |
| Y2025 | 16.4 | 26.6 | +38% | +9% | +22% | RED |
| Y2026 | 9.8 | 58.8 | +83% | +197% | +86% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.646, 'spa_p': 0.428, 'T': 26, 'K': 210}

**Deliverable row**: O7 NY AM: bar today 1-minute time (live) -> proposed frenko_56 | construction: frenko_56 (flex / hybrid Renko: trend brick N, reversal bar of 0.5N opening at last close) | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (FlexRenko/HybridRenko third-party) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

### A7 Asia (phase 2)

Live bar row `tm60__A`: 6M -160 pts (n 367, ulcer 475, maxDD 1039), 3M -323 pts. PICK (trailing 6M, pick): `tm900__A` 679 pts (n 31, ulcer 30, maxDD 106); 3M-pick: `tsf_5_200__B` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| tm900__A | 679 | 31 | 30 | 106 | 182 | 1045 |
| tm300__A | 856 | 55 | 62 | 154 | 670 | 1317 |
| renko_40__B | 801 | 62 | 59 | 182 | 325 | 1233 |
| tsf_5_200__B | 825 | 45 | 64 | 284 | 565 | 1269 |
| drb_2000__A | 651 | 41 | 57 | 122 | 363 | 1001 |
| lbrk_3_40__B | 539 | 39 | 54 | 182 | 370 | 829 |
| mrenko_40__B | 662 | 81 | 66 | 189 | 211 | 1018 |
| rc300s1__B | 843 | 143 | 90 | 242 | 203 | 1298 |
| renko_14__A | 1483 | 353 | 161 | 410 | 1063 | 2282 |
| tsf_5_200__A | 954 | 59 | 108 | 222 | 837 | 1468 |
| lbrk_4_10__B | 1224 | 222 | 141 | 361 | 622 | 1883 |
| cdr_400__Gt10k2 | 420 | 30 | 48 | 122 | 313 | 646 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 28.6 | 84.8 | 0.41 | 858 | 299 |
| 6M->3M | 37 | 36.9 | 90.4 | 0.35 | 882 | 571 |
| 3M->1M | 37 | 87.3 | 84.8 | 0.57 | 176 | 299 |
| 3M->3M | 37 | 60.0 | 90.4 | 0.46 | 543 | 571 |
| 12M->1M | 37 | 63.2 | 84.8 | 0.38 | 319 | 299 |
| 12M->3M | 37 | 57.9 | 90.4 | 0.35 | 309 | 571 |
| 6M->2w | 37 | 21.9 | 114.1 | 0.46 | 504 | 211 |

Nulls (same pick procedure): shift11: OOS 31.5/mo share beat 0.43; shift23: OOS 49.5/mo share beat 0.51; shift37: OOS 14.9/mo share beat 0.43; random-clock pool: OOS 75.9/mo share beat 0.46

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 28 vs 89 (n 36); +3M 48 vs 94 (n 34); +6M 78 vs 87 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | 23.3 | 31.5 | +26% | -91% | -88% | AMBER |
| Y2023 | 1.9 | 4.4 | +58% | -47% | -40% | RED |
| Y2024 | 15.6 | 26.1 | +40% | -79% | -75% | RED |
| Y2025 | 3.2 | 20.8 | +85% | -20% | -46% | RED |
| Y2026 | 39.7 | 55.3 | +28% | -86% | -87% | AMBER |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.025, 'spa_p': 0.134, 'T': 26, 'K': 517}

**Deliverable row**: A7 Asia: bar today 1-minute time (live) -> proposed tm900 | construction: 15-minute time bar | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: native NT8 Minute bar (OnBarClose at the first print after the boundary) (native)

### P7 Asia (phase 2)

Live bar row `tm60__A`: 6M 1200 pts (n 669, ulcer 358, maxDD 1021), 3M 914 pts. PICK (trailing 6M, pick): `rc600s2__A` 1923 pts (n 154, ulcer 69, maxDD 230); 3M-pick: `rc300s6__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| rc600s2__A | 1923 | 154 | 69 | 230 | 923 | 17752 |
| cdr_400__G40k8 | 852 | 62 | 56 | 127 | 200 | 7866 |
| rc60s3__B | 2409 | 631 | 166 | 423 | 1441 | 22241 |
| rc300s2__B | 2179 | 289 | 164 | 544 | 1434 | 20117 |
| cdr_250__G40k3 | 1430 | 142 | 109 | 327 | 1145 | 13204 |
| rc60s1__A | 2553 | 628 | 201 | 741 | 532 | 23567 |
| rc600s2__B | 1020 | 157 | 86 | 236 | 448 | 9416 |
| renko_40__A | 908 | 100 | 79 | 272 | 411 | 8379 |
| rc60s1__B | 3030 | 635 | 265 | 962 | 560 | 27971 |
| rc180s3__B | 1974 | 381 | 176 | 468 | 1133 | 18222 |
| vsess_600__A | 1917 | 828 | 173 | 467 | 879 | 17698 |
| cdr_250__G40k5 | 1226 | 144 | 120 | 326 | 1084 | 11320 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 12.2 | 75.0 | 0.38 | 769 | 416 |
| 6M->3M | 37 | 34.4 | 87.6 | 0.38 | 470 | 564 |
| 3M->1M | 37 | 29.7 | 75.0 | 0.49 | 425 | 416 |
| 3M->3M | 37 | 1.8 | 87.6 | 0.32 | 1607 | 564 |
| 12M->1M | 37 | -33.7 | 75.0 | 0.32 | 1065 | 416 |
| 12M->3M | 37 | -4.2 | 87.6 | 0.30 | 1673 | 564 |
| 6M->2w | 37 | 33.8 | 126.4 | 0.46 | 332 | 244 |

Nulls (same pick procedure): shift11: OOS 28.5/mo share beat 0.43; shift23: OOS 29.3/mo share beat 0.43; shift37: OOS -41.7/mo share beat 0.35; random-clock pool: OOS -26.4/mo share beat 0.42

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 15 vs 81 (n 36); +3M 45 vs 105 (n 34); +6M -1 vs 121 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -9.3 | 10.6 | +188% | +17% | -5% | RED |
| Y2023 | -2.6 | -18.4 | -86% | -73% | -66% | GREEN |
| Y2024 | -9.6 | 16.5 | +158% | +3% | +3% | RED |
| Y2025 | -7.3 | 21.5 | +134% | +214% | +53% | RED |
| Y2026 | -25.2 | 11.5 | +319% | +22% | -5% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.715, 'spa_p': 0.726, 'T': 26, 'K': 572}

**Deliverable row**: P7 Asia: bar today 1-minute time (live) -> proposed rc600s2 | construction: rc600s2 | param set A | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: see BAR_REGISTRY.md (see registry)

### H7 Asia (phase 2)

Live bar row `tm60__A`: 6M 624 pts (n 138, ulcer 156, maxDD 360), 3M 24 pts. PICK (trailing 6M, pick): `cusum_10__G12_34k5` 3076 pts (n 384, ulcer 118, maxDD 372); 3M-pick: `lbrk_5_20__A` (DISAGREES).
Top rows on trailing 6M (score = pts/(ulcer+1)):

| row__set | 6M pts | n | ulcer | maxDD | 3M pts | $/wk x live lots (6M) |
|---|---:|---:|---:|---:|---:|---:|
| cusum_10__G12_34k5 | 3076 | 384 | 118 | 372 | 1465 | 16564 |
| tib_1200__B | 1604 | 141 | 72 | 245 | 757 | 8638 |
| cusum_10__G12_34t5 | 1807 | 172 | 115 | 334 | 780 | 9730 |
| urenko_28__C | 1507 | 149 | 116 | 311 | 929 | 8112 |
| dlt_70__A | 848 | 86 | 69 | 148 | 537 | 4567 |
| rc300s1__C | 1604 | 140 | 133 | 362 | -131 | 8637 |
| trb_400__C | 2187 | 357 | 183 | 468 | 994 | 11776 |
| tm240__C | 1500 | 168 | 131 | 426 | 503 | 8076 |
| tsf_2_400__C | 1512 | 136 | 135 | 369 | 229 | 8143 |
| drb_400__C | 1880 | 356 | 168 | 409 | 1206 | 10124 |
| vib_700__A | 1127 | 133 | 102 | 249 | 165 | 6066 |
| dib_400__A | 1230 | 136 | 113 | 301 | 321 | 6624 |

Rolling walk-forward (pick at month ends from 2023-10; OOS mean pts per month; ref = live bar; share = periods pick beat live bar):

| procedure | periods | OOS mean/mo | live-bar mean/mo | share beat | OOS ulcer | live ulcer |
|---|---:|---:|---:|---:|---:|---:|
| 6M->1M | 37 | 23.1 | 13.1 | 0.46 | 693 | 552 |
| 6M->3M | 37 | 5.2 | 17.7 | 0.57 | 1866 | 1363 |
| 3M->1M | 37 | 11.0 | 13.1 | 0.51 | 371 | 552 |
| 3M->3M | 37 | -9.8 | 17.7 | 0.49 | 1592 | 1363 |
| 12M->1M | 37 | -18.4 | 13.1 | 0.49 | 877 | 552 |
| 12M->3M | 37 | -17.9 | 17.7 | 0.43 | 2303 | 1363 |
| 6M->2w | 37 | 61.7 | 47.2 | 0.54 | 335 | 254 |

Nulls (same pick procedure): shift11: OOS 27.0/mo share beat 0.49; shift23: OOS -39.7/mo share beat 0.43; shift37: OOS 42.9/mo share beat 0.59; random-clock pool: OOS 9.0/mo share beat 0.60

Decay (pick on trailing 6M, trade month +h; mean pts pick vs live): +1M 9 vs 14 (n 36); +3M 9 vs 18 (n 34); +6M 40 vs 6 (n 31)

Older-year check of the pick vs live bar (worse%: + = pick worse): worst = **RED**

| window | pick pts/wk | live pts/wk | mean | ulcer | maxDD | lab |
|---|---:|---:|---:|---:|---:|---|
| PRIOR12M | -4.5 | -18.2 | -75% | +12% | +21% | AMBER |
| Y2023 | 0.0 | 7.0 | +100% | -100% | -100% | RED |
| Y2024 | 0.0 | 17.0 | +100% | -100% | -100% | RED |
| Y2025 | -19.7 | -9.1 | +118% | +0% | +41% | RED |
| Y2026 | 40.9 | -23.7 | -272% | +37% | +68% | RED |

Reality check (pick pool vs live bar, weekly diffs on the pick window): {'rc_p': 0.379, 'spa_p': 0.063, 'T': 26, 'K': 607}

**Deliverable row**: H7 Asia: bar today 1-minute time (live) -> proposed cusum_10 | construction: cusum_10 (CUSUM-filter events (Lopez de Prado): S+ = max(0,S+ + dp), S- = min(0,S- + dp) on print price changes; event when S+ > h or S- < -h, then reset; h = k x trailing sigma-scale (ticks)) | param set G12_34k5 | label BEST-AVAILABLE-NOT-PROVEN | DS7 need: custom BarsType (event-driven) | scaling: size x s_rng (same, daily high-low range in points) (new custom BarsType)

## 4. Engine swap test
Not yet run (hook th_swb/swb_inject.py; sets TL3_SWB_*; queue /mnt/l2/l2vast/_major_sw/pending_b.txt).
