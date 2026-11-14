# DS3_REENTRY_ALL - re-entry discipline for K7 M7 U7 H7 A7 O7 (W-RA, priority 6)

**VERDICT: 3 of 84 re-entry cells x windows scored (14 cell-months); 4 (cell, book:session) leads pass the tolerant gate before placebos; best stack-level DD cut TL3_RA_BLKiii30 L3M 20.4% (-1928 $/wk). No PASS claim.**

Built epoch 1794674163. Prereg autopilot/REENTRY_ALL_PREREG.md (sha in DECISIONS.md). Base JN05W2 exact engine all layers ON, measured fills, $4.84 RT. TL3_RA_ID 202610 (hook path active, never fires): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL. P7 Asia is W-PR (not duplicated); the cells apply to the six books in all sessions, P7 untouched but coupled through the stack. Sessions: engine index asia 0, london 1, pre 2, nyam 3, nypm 4, close 5 (pre and close carry no trades in JN05W2).

## 1. Where the money is by entry number and fresh vs rechase (JN05W2, exact engine trades; $/wk by window)

Rechase = same-side entry whose most recent closed trade in the same (book, session, Globex day) was a loser. Entry number = order within the instance. wk = $/wk, mean = $/trade.

### window ALL

| book | sess | n_fresh | wk_fresh | n_rechase | wk_rechase | n_opp_after_loser | wk_opp_after_loser | n_same_after_win | wk_same_after_win | rechase_mean$ | rechase_win | rechase_fullstop |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 687.0 | 341.5 | 76.0 | 50.9 | 121.0 | 55.4 | 261.0 | 224.2 | 125.4 | 0.5 | 0.2 |
| H7 | asia | 587.0 | 733.5 | 34.0 | -7.9 | 33.0 | -85.0 | 41.0 | 140.5 | -43.4 | 0.4 | 0.1 |
| H7 | nyam | 306.0 | 86.5 | 12.0 | 46.3 | 24.0 | -48.9 | 1.0 | -2.9 | 721.7 | 0.8 | 0.0 |
| K7 | asia | 918.0 | 354.5 | 262.0 | 136.7 | 714.0 | 417.9 | 513.0 | 296.1 | 97.6 | 0.4 | 0.0 |
| K7 | london | 727.0 | 218.5 | 150.0 | 57.2 | 484.0 | 98.5 | 311.0 | 15.8 | 71.3 | 0.4 | 0.0 |
| K7 | nyam | 737.0 | 210.4 | 187.0 | 42.1 | 328.0 | -156.4 | 252.0 | -76.5 | 42.1 | 0.4 | 0.0 |
| K7 | nypm | 561.0 | 366.6 | 97.0 | -23.9 | 236.0 | -102.4 | 185.0 | 70.6 | -46.1 | 0.4 | 0.0 |
| M7 | london | 916.0 | 242.2 | 311.0 | -112.2 | 674.0 | 106.8 | 552.0 | -309.3 | -67.5 | 0.4 | 0.1 |
| M7 | nyam | 758.0 | 212.7 | 277.0 | 53.4 | 133.0 | -68.9 | 324.0 | 106.8 | 36.1 | 0.4 | 0.1 |
| O7 | nyam | 452.0 | 425.2 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| U7 | asia | 571.0 | 1215.4 | 3.0 | 44.8 | 70.0 | 103.6 | 0.0 | 0.0 | 2792.2 | 1.0 | 0.0 |
| U7 | london | 526.0 | 492.3 | 9.0 | -58.7 | 65.0 | 167.5 | 0.0 | 0.0 | -1221.2 | 0.2 | 0.7 |

| book | sess | wk_entry_1 | wk_entry_2 | wk_entry_3 | wk_entry_4 | wk_entry_5 | n_entry_1 | n_entry_2 | n_entry_3 | n_entry_4 | n_entry_5 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 342 | 217 | 59 | 77 | 15 | 687 | 264 | 117 | 46 | 42 |
| H7 | asia | 734 | 66 | -0 | 8 | 0 | 587 | 99 | 12 | 2 | 0 |
| H7 | nyam | 86 | -8 | 0 | 0 | 0 | 306 | 40 | 2 | 0 | 0 |
| K7 | asia | 354 | 312 | 150 | 139 | 279 | 918 | 570 | 355 | 244 | 509 |
| K7 | london | 218 | 29 | 158 | -129 | 62 | 727 | 441 | 260 | 158 | 195 |
| K7 | nyam | 210 | -3 | -105 | -4 | -14 | 737 | 504 | 223 | 76 | 25 |
| K7 | nypm | 367 | 0 | 48 | -57 | 18 | 561 | 327 | 142 | 64 | 42 |
| M7 | london | 242 | 46 | 42 | -118 | -252 | 916 | 672 | 427 | 245 | 229 |
| M7 | nyam | 213 | 78 | 67 | -31 | -6 | 758 | 469 | 174 | 59 | 36 |
| O7 | nyam | 425 | 0 | 0 | 0 | 0 | 452 | 0 | 0 | 0 | 0 |
| U7 | asia | 1215 | 54 | 98 | 45 | 0 | 571 | 94 | 18 | 3 | 0 |
| U7 | london | 492 | -176 | 146 | 0 | 0 | 526 | 107 | 12 | 0 | 0 |

### window HOLD

| book | sess | n_fresh | wk_fresh | n_rechase | wk_rechase | n_opp_after_loser | wk_opp_after_loser | n_same_after_win | wk_same_after_win | rechase_mean$ | rechase_win | rechase_fullstop |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 234.0 | 338.5 | 61.0 | -12.4 | 84.0 | 1.7 | 178.0 | 424.0 | -10.6 | 0.4 | 0.3 |
| H7 | asia | 171.0 | 744.6 | 22.0 | 202.8 | 18.0 | -279.3 | 20.0 | -76.1 | 480.6 | 0.5 | 0.0 |
| H7 | nyam | 64.0 | -7.7 | 3.0 | 34.3 | 3.0 | -55.5 | 0.0 | 0.0 | 596.0 | 0.7 | 0.0 |
| K7 | asia | 256.0 | 335.4 | 156.0 | 428.9 | 426.0 | 1185.1 | 323.0 | 809.9 | 143.4 | 0.4 | 0.0 |
| K7 | london | 224.0 | 55.3 | 72.0 | 189.0 | 245.0 | 508.4 | 181.0 | 10.2 | 136.9 | 0.5 | 0.0 |
| K7 | nyam | 164.0 | 25.2 | 62.0 | 172.5 | 81.0 | -204.3 | 83.0 | -288.5 | 145.1 | 0.5 | 0.0 |
| K7 | nypm | 114.0 | 244.2 | 39.0 | -25.6 | 61.0 | -114.0 | 56.0 | 335.5 | -34.2 | 0.4 | 0.0 |
| M7 | london | 249.0 | 132.1 | 178.0 | -495.1 | 264.0 | 438.7 | 270.0 | -466.0 | -145.0 | 0.3 | 0.1 |
| M7 | nyam | 176.0 | 392.7 | 110.0 | -144.6 | 27.0 | -97.1 | 119.0 | 129.0 | -68.5 | 0.4 | 0.1 |
| O7 | nyam | 104.0 | 541.5 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| U7 | asia | 189.0 | 986.7 | 1.0 | 45.9 | 47.0 | -69.5 | 0.0 | 0.0 | 2392.6 | 1.0 | 0.0 |
| U7 | london | 161.0 | 734.9 | 1.0 | 69.0 | 32.0 | 354.9 | 0.0 | 0.0 | 3596.5 | 1.0 | 0.0 |

| book | sess | wk_entry_1 | wk_entry_2 | wk_entry_3 | wk_entry_4 | wk_entry_5 | n_entry_1 | n_entry_2 | n_entry_3 | n_entry_4 | n_entry_5 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 339 | 180 | 2 | 174 | 103 | 234 | 156 | 97 | 38 | 39 |
| H7 | asia | 745 | -120 | 19 | 27 | 0 | 171 | 52 | 9 | 2 | 0 |
| H7 | nyam | -8 | 10 | 0 | 0 | 0 | 64 | 9 | 0 | 0 | 0 |
| K7 | asia | 335 | 1144 | 172 | 431 | 633 | 256 | 243 | 205 | 167 | 410 |
| K7 | london | 55 | 541 | 334 | -202 | -90 | 224 | 178 | 136 | 97 | 135 |
| K7 | nyam | 25 | 238 | -413 | -36 | -69 | 164 | 127 | 73 | 30 | 14 |
| K7 | nypm | 244 | 20 | 89 | -50 | 96 | 114 | 82 | 44 | 26 | 22 |
| M7 | london | 132 | 342 | 369 | -636 | -536 | 249 | 232 | 203 | 143 | 149 |
| M7 | nyam | 393 | 52 | 16 | -221 | 40 | 176 | 121 | 69 | 36 | 30 |
| O7 | nyam | 541 | 0 | 0 | 0 | 0 | 104 | 0 | 0 | 0 | 0 |
| U7 | asia | 987 | 109 | 351 | 69 | 0 | 189 | 61 | 15 | 2 | 0 |
| U7 | london | 735 | -201 | 322 | 0 | 0 | 161 | 50 | 6 | 0 | 0 |

### window L6M

| book | sess | n_fresh | wk_fresh | n_rechase | wk_rechase | n_opp_after_loser | wk_opp_after_loser | n_same_after_win | wk_same_after_win | rechase_mean$ | rechase_win | rechase_fullstop |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 126.0 | 324.8 | 48.0 | 34.7 | 57.0 | -447.0 | 117.0 | 787.9 | 19.0 | 0.5 | 0.3 |
| H7 | asia | 94.0 | 1268.9 | 19.0 | 278.3 | 8.0 | 17.6 | 16.0 | 109.4 | 385.1 | 0.5 | 0.0 |
| H7 | nyam | 31.0 | 163.8 | 1.0 | -23.2 | 1.0 | -19.7 | 0.0 | 0.0 | -609.7 | 0.0 | 0.0 |
| K7 | asia | 131.0 | 551.0 | 110.0 | 270.6 | 260.0 | 1485.8 | 203.0 | 376.7 | 64.7 | 0.4 | 0.0 |
| K7 | london | 111.0 | -212.3 | 39.0 | 387.1 | 146.0 | 770.8 | 100.0 | -360.9 | 260.9 | 0.5 | 0.1 |
| K7 | nyam | 77.0 | 164.1 | 27.0 | 373.1 | 37.0 | -323.9 | 35.0 | -159.2 | 363.2 | 0.6 | 0.0 |
| K7 | nypm | 56.0 | 1049.3 | 20.0 | 372.9 | 24.0 | 252.8 | 37.0 | 84.2 | 490.1 | 0.6 | 0.0 |
| M7 | london | 124.0 | 353.0 | 107.0 | -511.7 | 133.0 | 178.5 | 146.0 | -421.1 | -125.7 | 0.3 | 0.1 |
| M7 | nyam | 84.0 | 327.5 | 60.0 | 20.4 | 16.0 | -71.5 | 54.0 | 117.7 | 8.9 | 0.4 | 0.0 |
| O7 | nyam | 46.0 | 406.6 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| U7 | asia | 102.0 | 1604.8 | 1.0 | 91.0 | 33.0 | 93.3 | 0.0 | 0.0 | 2392.6 | 1.0 | 0.0 |
| U7 | london | 80.0 | 1971.9 | 0.0 | 0.0 | 21.0 | 207.3 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |

| book | sess | wk_entry_1 | wk_entry_2 | wk_entry_3 | wk_entry_4 | wk_entry_5 | n_entry_1 | n_entry_2 | n_entry_3 | n_entry_4 | n_entry_5 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 | asia | 325 | 82 | -100 | 170 | 296 | 126 | 99 | 67 | 31 | 30 |
| H7 | asia | 1269 | 471 | 38 | 54 | 0 | 94 | 35 | 9 | 2 | 0 |
| H7 | nyam | 164 | 19 | 0 | 0 | 0 | 31 | 5 | 0 | 0 | 0 |
| K7 | asia | 551 | 1238 | 180 | 180 | 487 | 131 | 130 | 123 | 109 | 294 |
| K7 | london | -212 | 553 | 341 | -338 | 87 | 111 | 98 | 79 | 59 | 80 |
| K7 | nyam | 164 | 304 | -377 | 20 | 77 | 77 | 59 | 33 | 14 | 5 |
| K7 | nypm | 1049 | 169 | 371 | 32 | 103 | 56 | 41 | 23 | 15 | 16 |
| M7 | london | 353 | 509 | 531 | -674 | -1069 | 124 | 119 | 104 | 78 | 94 |
| M7 | nyam | 328 | 21 | 22 | -191 | 215 | 84 | 55 | 35 | 20 | 20 |
| O7 | nyam | 407 | 0 | 0 | 0 | 0 | 46 | 0 | 0 | 0 | 0 |
| U7 | asia | 1605 | 267 | 584 | 46 | 0 | 102 | 43 | 11 | 1 | 0 |
| U7 | london | 1972 | -1051 | 547 | 0 | 0 | 80 | 29 | 5 | 0 | 0 |

## 2. Stack level: each rule on all six books (exact engine, all layers ON)

d_mean = $/wk vs JN05W2; DD = max drawdown of cumulative daily P&L; dd_cut_pct positive = shallower; d_ww = worst week change; best5 = share of the reference 5 best weeks kept; w2l = winning weeks turned losing.

| cell | win | d_mean | dd | dd_ref | dd_cut_pct | ww | d_ww | stops_wk | stops_ref | best5 | w2l |
|---|---|---|---|---|---|---|---|---|---|---|---|
| BLKi | L3M | -5263.0 | -54370.8 | -52233.1 | -4.1 | -37161.9 | -791.3 | 10.3 | 10.3 | 0.9 | 1 |
| BLKii | L3M | -3703.3 | -53264.3 | -52233.1 | -2.0 | -38354.8 | -1984.3 | 10.6 | 10.3 | 0.9 | 1 |
| BLKiii30 | L3M | -1928.3 | -41581.1 | -52233.1 | 20.4 | -29142.4 | 7228.1 | 10.2 | 10.3 | 1.0 | 1 |

### recent windows with 2026-W44 removed from both sides (stack level)

| cell | win | d_mean | dd | dd_ref | dd_cut_pct | d_ww |
|---|---|---|---|---|---|---|
| BLKi | L3M | -5202.8 | -49756.3 | -43405.1 | -14.6 | -8152.3 |
| BLKii | L3M | -3585.5 | -50501.0 | -43405.1 | -16.3 | -12328.9 |
| BLKiii30 | L3M | -2875.9 | -41581.1 | -43405.1 | 4.2 | -3116.6 |

## 3. Book x session: rules that pass the tolerant gate (before placebos)

Gate: DD not worse by >2%, worst week not worse by >2%, mean not lower by >3% of the scope mean, in every window present, a DD cut in at least one; recent (L3M or L6M) must be present; a lead needs older windows (HOLD, PREUW, X', GAP) to count as holding in both. Scope numbers are on the scope's own trades inside the all-books run (other books' coupling included).

| cell | scope | wins | holds_recent_and_older | dMean_L6M | ddcut_L6M | dMean_HOLD | ddcut_HOLD | dMean_PRE | ddcut_PRE | stops_wk_L6M | stops_ref_L6M | best5_L6M | w2l_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BLKii | A7:asia | L3M | recent only | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0 |
| BLKiii30 | *:asia | L3M | recent only | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0 |
| BLKiii30 | A7:asia | L3M | recent only | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0 |
| BLKiii30 | K7:asia | L3M | recent only | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0 |

## 4. Best rule per book x session (always delivered, with plain strength)

## 6. Live night 2026-11-13 (K7 and M7, London 02:00-08:30 ET), what each rule would have done

Positions from data/live/StratTrades_DS7_<acct>.csv (entry/exit ET, qty, pnlNet) with the initial stop distance from nt8log_latest.txt; R = pnl / (qty x stop x 20). K7 entry ORDERS counted 6 (5 positions + the 02:41 add); M7 6 positions (8 entry orders with the 02:13 and 04:02 adds). M7 full stops: 03:22 and 07:12 positions, plus a 2-minute StopJoin at 08:30 (-435).

| book | n | en | ex | side | qty | epx | xpx | exit | pnl | stop_pts | R |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 | 1 | 2026-11-13 02:39:00 | 2026-11-13 03:24:35 | S | 2 | 28323.25 | 28264.25 | Target | 2360.00 | 72.00 | 0.82 |
| K7 | 2 | 2026-11-13 03:45:02 | 2026-11-13 04:02:31 | S | 1 | 28267.50 | 28313.25 | PolicyCut | -915.00 | 79.00 | -0.58 |
| K7 | 3 | 2026-11-13 04:03:00 | 2026-11-13 05:08:52 | L | 2 | 28311.00 | 28370.00 | Target | 2360.00 | 79.00 | 0.75 |
| K7 | 4 | 2026-11-13 05:18:01 | 2026-11-13 06:07:32 | L | 2 | 28370.50 | 28429.50 | Target | 2360.00 | 79.00 | 0.75 |
| K7 | 5 | 2026-11-13 06:18:02 | 2026-11-13 07:47:36 | L | 1 | 28417.50 | 28366.25 | PolicyCut | -1025.00 | 78.75 | -0.65 |
| M7 | 1 | 2026-11-13 02:02:00 | 2026-11-13 03:13:38 | L | 2 | 28366.25 | 28318.75 | PolicyCut | -1900.00 | 95.50 | -0.50 |
| M7 | 2 | 2026-11-13 03:22:00 | 2026-11-13 05:03:18 | S | 2 | 28301.88 | 28359.00 | StopJoin | -2285.00 | 78.87 | -0.72 |
| M7 | 3 | 2026-11-13 05:04:00 | 2026-11-13 06:07:20 | L | 2 | 28364.13 | 28423.75 | Target | 2385.00 | 91.38 | 0.65 |
| M7 | 4 | 2026-11-13 06:15:01 | 2026-11-13 07:02:56 | L | 4 | 28406.63 | 28466.25 | Target | 4770.00 | 76.13 | 0.78 |
| M7 | 5 | 2026-11-13 07:12:00 | 2026-11-13 07:39:24 | L | 4 | 28451.19 | 28392.50 | StopJoin | -4680.00 | 78.19 | -0.75 |
| M7 | 6 | 2026-11-13 08:28:02 | 2026-11-13 08:30:03 | L | 2 | 28440.63 | 28429.75 | StopJoin | -435.00 | 76.63 | -0.14 |

Rule effect on the night (change = $ with rule minus actual; a blocked trade leaves no history):

| rule | book | actual | with_rule | change | blocked |
|---|---|---|---|---|---|
| ('blk', 'ii') | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'ii') | M7 | -2145 | -1710 | 435 | 6 |
| ('blk', 'iii', 30) | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'iii', 30) | M7 | -2145 | -2145 | 0 | nan |
| ('blk', 'iii', 60) | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'iii', 60) | M7 | -2145 | -1710 | 435 | 6 |
| ('blk', 'iii', 120) | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'iii', 120) | M7 | -2145 | -1710 | 435 | 6 |
| ('blk', 'i') | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'i') | M7 | -2145 | -1710 | 435 | 6 |
| ('blk', 'iv') | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'iv') | M7 | -2145 | -1710 | 435 | 6 |
| ('blk', 'v') | K7 | 5140 | 5140 | 0 | nan |
| ('blk', 'v') | M7 | -2145 | -2145 | 0 | nan |
| ('half',) | K7 | 5140 | 5140 | 0 | nan |
| ('half',) | M7 | -2145 | -1928 | 218 | nan |
| ('capn', 2) | K7 | 5140 | 1445 | -3695 | 3,4,5 |
| ('capn', 2) | M7 | -2145 | -4185 | -2040 | 3,4,5,6 |
| ('capn', 3) | K7 | 5140 | 3805 | -1335 | 4,5 |
| ('capn', 3) | M7 | -2145 | -1800 | 345 | 4,5,6 |
| ('capn', 4) | K7 | 5140 | 6165 | 1025 | 5 |
| ('capn', 4) | M7 | -2145 | 2970 | 5115 | 5,6 |
| ('capr', 1.0) | K7 | 5140 | 5140 | 0 | nan |
| ('capr', 1.0) | M7 | -2145 | -4185 | -2040 | 3,4,5,6 |
| ('capr', 1.5) | K7 | 5140 | 5140 | 0 | nan |
| ('capr', 1.5) | M7 | -2145 | -2145 | 0 | nan |
| ('capr', 2.0) | K7 | 5140 | 5140 | 0 | nan |
| ('capr', 2.0) | M7 | -2145 | -2145 | 0 | nan |

**Evidence evaluated with the 2026-11-13 bars (tail_20261114 pull, spliced into a separate copy /mnt/l2/l2vast/_reentry_all/min1_NQ_ext.npz; overlap bar identical):** only candidate for any block rule is M7 entry 6 at 08:28 (long, same side as the 07:12 full stop, 49 min later, entry 28440.63 below the loser entry 28451.19). (i) blocks it: session high before the loser exit 28469.75, after 28444.75, no new extreme. (ii) blocks it. (iii) 30 min allows, 60 and 120 block. (iv) blocks it if no opposite-side signal occurred (no opposite M7 entry in the log; signals themselves are not logged, so (iv) is an assumption). (v) ALLOWS it: a confirmed 5-min higher low formed after the low of 28356.75. So (i)(ii)(iii60/120)(iv) would have saved the -435; (iii30) and (v) would not. **Exact-engine replay of 11-13:** the shared TP month cache 202611 covers 11-02..11-11 only; W-EV (a1878b57f61f46389) was asked for a separate cache copy, the shared store is untouched. Not run yet.

Reading: on that night the block rules were nearly irrelevant (one candidate, -435); the count caps decided the night: CAP4 would have stopped M7 before the 07:12 full stop (+5,115) and K7 before the last cut (+1,025); CAP2 would have cost -3,695 (K7) and -2,040 (M7) by stopping the two with-trend winners; a 1.0R loss cap fires after the second M7 loser and costs -2,040 for the same reason. The night was a with-trend London run (K7 longs +2,360 twice), which is the case where caps hurt.

## 7. How a discretionary trader would read these
A trader does not re-enter the same side after being stopped without something new (a new extreme, a reclaim of the entry, time, a higher low); that is the evidence rules. A flat count cap on closes is blunt: it also stops the with-trend re-entries that make a trend session, so it is judged on the best-5 weeks kept and the winning weeks turned losing columns above, not on mean alone. Half size on a rechase is the least intrusive version of the same instinct.

## 8. Status
No PASS claims. Walk-forward, combined best-per-scope cell and its placebos follow once the HOLD/PRE/X' months finish (see MORNING.md status lines).
