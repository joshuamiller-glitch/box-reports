# DS3_DEEPEN_LOSS_B - T-DEEPEN PART 1 item 6 (SKIPS) and item 9 (EXECUTION COSTS), W-LB

**VERDICT (plain): 90 of 447 cells have an exact L3M result so far; 30 pass the tolerant gate in L3M with a positive mean (candidates for promotion, none claimed). Item 9 cost measurement is in section 1: fees plus excess slippage are 16.0% of L6M gross, the 08:30 bump is only about $50-60/wk of it. No PASS claim.**

Written 2026-11-15T12:33Z (date -u). Research only, shadow, no PASS claims. Prereg autopilot/DEEPEN_LB_PREREG.md (sha 9d2b5bd88f64ed49 in DECISIONS.md). Code code/th_deepen_lb (lb_hooks.py outermost additive hook; lb_cells.py registry; lb_score.py; lb_page.py), bulk /mnt/l2/l2vast/_deepen_lb. Identity: TL3_LB_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_LB_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.

**LOT BASIS.** Sets run at BASE lots (live user lots x1.75; live caps = engine caps x1.75, P7 day cap 8,400 engine = 14,700 live). The engine charges $1.18/contract RT in net_fee; FEES.md standard is $4.84 (NQ proxy), MNQ $1.78. Every table carries a $4.84 column (d mean $4.84 = d mean repriced on the change in contracts) and a live-excess column (adds entry +0.23, cut +0.40, stop +0.44, target 0 pt, +1.36 pt on non-target exits 08:30-08:44 ET; passive fills carry no entry excess). Noise floor (DS3_REDO_R4_ENTRY): |maxDD cut| below ~8% and |mean delta| below ~$1,238/wk is path-dependence level.

## 1. Item 9 measured first: what each book and session pays per dollar earned (JN05W2 exact trade list)

Cost = FEES.md $4.84/contract RT + live-excess slip (entry +0.23 pt, market cut +0.40, stop +0.44, target 0, +1.36 pt on non-target exits starting 08:30-08:44 ET), points x $20 x contracts (model of th_smart_b/b1_cost_audit.py; slip means from the 187 frozen live trades and the DN stop-fill study). Cost per contract is lot-invariant: fee 4.84 + entry 4.60 = 9.44 for a target round trip, 17.4 for a cut, 18.2 for a stop, +27.2 more at 08:30-08:44. Code m1_cost.py, m2_section.py.

### 1.1 Where the cost goes (all books)

| window | gross $ | fee $ | entry excess $ | cut excess $ | stop excess $ | 08:30 bump $ | total cost $ | cost % of gross | cost $/wk | 08:30 bump $/wk | contracts/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | 255494 | 16369 | 15557 | 13688 | 1918 | 789 | 48321 | 18.9 | 3677 | 60 | 257 |
| L6M | 669769 | 36697 | 34877 | 30400 | 4092 | 1414 | 107480 | 16.0 | 4112 | 54 | 290 |
| HOLD | 968266 | 65626 | 62371 | 54312 | 8246 | 3509 | 194063 | 20.0 | 3732 | 67 | 261 |
| PRE | 471952 | 37587 | 35724 | 29928 | 5914 | 4406 | 113559 | 24.1 | 1320 | 51 | 90 |
| X' | 470362 | 52562 | 49956 | 37456 | 13050 | 9493 | 162518 | 34.6 | 2084 | 122 | 139 |

Reading: the three big pieces are the fee, the entry excess (0.23 pt on EVERY contract) and the market-cut excess; the 08:30-08:44 bump is a rounding error at stack level (about $40-50/wk against ~$21k/wk of L6M gross), so avoiding the 08:30 fill cannot be worth more than that and any rule that gives up entries or exits to dodge it must be judged against that ceiling.

### 1.2 Ranking: books by cost per dollar earned (cost / net, lower is better; cost > net means the book is net negative after cost)

**L3M**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 20 | 20 | 6005 | 296 | 5709 | 0.05 | 4.9 | 23 | 434 | 14.8 | 285.4 |
| U7 | 121 | 330 | 63097 | 4488 | 58609 | 0.08 | 7.1 | 342 | 4460 | 37.1 | 177.6 |
| H7 | 84 | 150 | 13804 | 2119 | 11685 | 0.18 | 15.4 | 161 | 889 | 25.2 | 77.9 |
| P7 | 467 | 1530 | 120025 | 21929 | 98096 | 0.22 | 18.3 | 1669 | 7465 | 47.0 | 64.1 |
| K7 | 687 | 790 | 47560 | 11334 | 36226 | 0.31 | 23.8 | 863 | 2757 | 16.5 | 45.9 |
| M7 | 336 | 402 | 5976 | 5888 | 88 | 67.04 | 98.5 | 448 | 7 | 17.5 | 0.2 |
| A7 | 160 | 160 | -971 | 2268 | -3239 | net<0 | gross<0 | 173 | -247 | 14.2 | -20.2 |

**L6M**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 46 | 46 | 10742 | 694 | 10048 | 0.07 | 6.5 | 27 | 384 | 15.1 | 218.4 |
| H7 | 176 | 329 | 53350 | 4563 | 48786 | 0.09 | 8.6 | 175 | 1866 | 25.9 | 148.3 |
| U7 | 271 | 731 | 105206 | 9933 | 95272 | 0.10 | 9.4 | 380 | 3645 | 36.7 | 130.3 |
| P7 | 1037 | 3469 | 344599 | 49282 | 295317 | 0.17 | 14.3 | 1885 | 11298 | 47.5 | 85.1 |
| K7 | 1553 | 1780 | 132978 | 25282 | 107696 | 0.23 | 19.0 | 967 | 4120 | 16.3 | 60.5 |
| A7 | 353 | 353 | 20714 | 4891 | 15823 | 0.31 | 23.6 | 187 | 605 | 13.9 | 44.8 |
| M7 | 733 | 874 | 2181 | 12835 | -10654 | net<0 | 588.5 | 491 | -408 | 17.5 | -12.2 |

**HOLD**

| book | trades | contracts | gross $ | cost $ | net $ | cost per $ net | cost % gross | cost $/wk | net $/wk | cost $/trade | net $/contract |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 | 104 | 104 | 28356 | 1559 | 26797 | 0.06 | 5.5 | 30 | 515 | 15.0 | 257.7 |
| U7 | 484 | 1290 | 125129 | 17905 | 107224 | 0.17 | 14.3 | 344 | 2062 | 37.0 | 83.1 |
| P7 | 1838 | 6163 | 551061 | 88051 | 463010 | 0.19 | 16.0 | 1693 | 8904 | 47.9 | 75.1 |
| A7 | 564 | 564 | 42234 | 7815 | 34419 | 0.23 | 18.5 | 150 | 662 | 13.9 | 61.0 |
| H7 | 307 | 580 | 35822 | 8298 | 27524 | 0.30 | 23.2 | 160 | 529 | 27.0 | 47.5 |
| K7 | 2747 | 3179 | 186248 | 45359 | 140889 | 0.32 | 24.4 | 872 | 2709 | 16.5 | 44.3 |
| M7 | 1408 | 1679 | -584 | 25077 | -25661 | net<0 | gross<0 | 482 | -493 | 17.8 | -15.3 |

### 1.3 Book x session where cost is more than half of gross (L6M or L3M), the places a cost cut is worth most

| window | book | session | trades | gross $ | cost $ | net $ | cost % gross |
|---|---|---|---|---|---|---|---|
| L3M | A7 | asia | 160 | -971 | 2268 | -3239 | gross<0 |
| L3M | K7 | nyam | 88 | -1844 | 1263 | -3107 | gross<0 |
| L3M | M7 | london | 248 | -5159 | 4671 | -9830 | gross<0 |
| L3M | P7 | nyam | 58 | -3765 | 1811 | -5576 | gross<0 |
| L6M | K7 | london | 427 | 11892 | 7347 | 4545 | 62 |
| L6M | K7 | nyam | 188 | 5175 | 2656 | 2519 | 51 |
| L6M | M7 | london | 519 | -8433 | 9814 | -18247 | gross<0 |
| L6M | P7 | london | 346 | 14036 | 11389 | 2647 | 81 |
| HOLD | H7 | nyam | 73 | 211 | 1025 | -814 | 486 |
| HOLD | K7 | nyam | 408 | -12749 | 5839 | -18588 | gross<0 |
| HOLD | M7 | london | 976 | -15691 | 18950 | -34641 | gross<0 |

### 1.4 Micro contracts for the odd lot (analytic, no engine cell)

MNQ is 1/10 of an NQ contract at $1.78 RT (FEES.md, proxy) = $17.80 per NQ-equivalent against $4.84 for NQ: micros cost 3.7x more per unit of exposure, so they can only be used for the fractional remainder, never to cut the fee bill. Typical use: the half-size rules round an odd lot UP (7 -> 4, user lots K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2); holding 3 NQ + 5 MNQ = 3.5 exactly costs 3 x 4.84 + 5 x 1.78 = $23.4 vs 4 x 4.84 = $19.4, i.e. +$4.0 per trade, and the same for entry slip (+0.23 pt on 5 micro contracts is $0.23 x 5 x $2 = $2.3 vs 0.5 NQ $2.3, the same per unit). It removes a 14% size overshoot on odd-lot half trades; with P7 net per contract about $85 (L6M) the overshoot is worth about 0.5 x $85 x (share of halved trades) in variance terms but zero in expectation (the rounding is symmetric across lots), so it is a risk-exactness tool, not an edge. Verdict: no cell run; it would only matter inside a sizing layer that halves, and costs +$4 per such trade.


## 2. Exact cells (JN05W2 base, all layers ON; delta vs JN05W2 on the same months; cut % positive = shallower maxDD)

Columns: L3M/L6M/HOLD = maxDD cut % / d mean $/wk (engine) / d mean $/wk at $4.84 and live-excess / worst-week change / gate (tolerant) ; x44 = DD cut with 2026-W44 removed from both; b5 = 5 best base weeks kept; w2l = winning weeks turned losing. A window shows only when all its months exist.

### BR  breadth-extreme skip to the other books (parent BR3S = P7 breadth_ext15 == 3 skip, already in JN05W2)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| BR_K7_X15 | 3 | -7.2 / -3577 / -3566 / -3545 / -3809 / False / 11.1 / 0.88 / 0 | - / - / - / - | - / - | - / - |
| BR_K7_H15 | 3 | 14.8 / -602 / -598 / -584 / 7753 / False / 2.5 / 0.98 / 0 | - / - / - / - | - / - | - / - |
| BR_U7_X15 | 3 | 0.5 / -1409 / -1376 / -1307 / 2643 / False / 0.7 / 0.98 / 1 | - / - / - / - | - / - | - / - |
| BR_U7_H15 | 3 | 4.8 / -540 / -519 / -470 / 3687 / True / 0.1 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| BR_H7_X15 | 3 | -12.2 / -819 / -816 / -813 / -6390 / False / -5.3 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| BR_H7_H15 | 3 | -4.6 / -82 / -77 / -61 / -2403 / False / -0.4 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_M7_X15 | 3 | -6.1 / -1491 / -1489 / -1490 / -2520 / False / 3.9 / 0.97 / 0 | - / - / - / - | - / - | - / - |
| BR_M7_H15 | 3 | 1.2 / 144 / 147 / 157 / 615 / True / 5.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_X15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_O7_X15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_O7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_ALL6_X15 | 3 | -16.1 / -5079 / -5030 / -4925 / -6601 / False / 24.7 / 0.85 / 0 | - / - / - / - | - / - | - / - |
| BR_ALL6_H15 | 3 | 10.2 / -1631 / -1601 / -1526 / 6505 / False / 14.5 / 0.94 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_X30 | 3 | -9.3 / -4193 / -4146 / -4051 / 7835 / False / -31.6 / 0.84 / 1 | - / - / - / - | - / - | - / - |
| BR_P7_X5 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_H2 | 3 | 0.4 / -1321 / -1286 / -1222 / 187 / False / -6.5 / 0.97 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_V19 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### EV  skips / half before scheduled events (calendar from 2024-10; identity before)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| EV_T0830_P10_S | 3 | 0.0 / -37 / -36 / -29 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P10_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P20_S | 3 | 0.0 / -71 / -70 / -62 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P20_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P30_S | 3 | 0.0 / -71 / -70 / -62 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P30_H | 3 | 0.0 / 51 / 52 / 55 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P60_S | 3 | 0.0 / 206 / 209 / 222 / 0 / True / -0.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_T0830_P60_H | 3 | 0.0 / 102 / 103 / 107 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P15_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P15_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P30_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P30_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P60_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_FOMC_P60_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q60_S | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q60_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q120_S | 3 | 0.0 / -91 / -91 / -91 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| EV_EARN_Q120_H | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### RB  range used up AND breadth / event day (HAR+CME forecast; plain range rule is W-EC)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| RB_asia_K100_EV | 3 | 16.3 / 1584 / 1596 / 1642 / 10024 / True / -0.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### TG  target 1-2 ticks short

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| TG1_K7 | 3 | -0.2 / 455 / 457 / 464 / -105 / True / -0.3 / 1.03 / 0 | - / - / - / - | - / - | - / - |
| TG1_P7 | 3 | -0.2 / -230 / -230 / -230 / -95 / True / -0.5 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| TG1_U7 | 3 | -0.1 / -69 / -69 / -69 / -50 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_H7 | 3 | -0.1 / -22 / -22 / -22 / -30 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_M7 | 3 | -0.1 / -61 / -61 / -61 / -35 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_A7 | 3 | -0.1 / 208 / 208 / 209 / -45 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG1_ALL | 3 | -0.7 / 368 / 369 / 377 / -360 / True / -1.3 / 1.02 / 0 | - / - / - / - | - / - | - / - |
| TG2_K7 | 3 | 6.7 / 795 / 794 / 797 / 3518 / True / -0.6 / 1.03 / 0 | - / - / - / - | - / - | - / - |
| TG2_P7 | 3 | -0.4 / -362 / -363 / -363 / -190 / True / -1.0 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| TG2_U7 | 3 | -0.2 / -138 / -138 / -138 / -100 / True / -0.5 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG2_H7 | 3 | -0.1 / -36 / -36 / -38 / -60 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG2_M7 | 3 | -0.2 / -86 / -86 / -86 / -70 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG2_A7 | 3 | -0.2 / 94 / 93 / 94 / -90 / True / -0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| TG2_ALL | 3 | 5.7 / 194 / 191 / 194 / 3008 / True / -2.5 / 1.01 / 0 | - / - / - / - | - / - | - / - |

### LE  passive vs market entry per book / session (through-1-tick fill rule, market on timeout)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| LE_C1_K7 | 3 | 6.8 / 1719 / 1713 / 1906 / 3656 / True / -3.3 / 1.01 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_P7 | 3 | -2.4 / -492 / -507 / -141 / -1107 / False / -4.7 / 1.01 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_U7 | 3 | 0.3 / 523 / 520 / 607 / 130 / True / 0.2 / 1.02 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_H7 | 3 | 0.0 / -227 / -228 / -186 / -90 / True / -0.1 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_M7 | 3 | -7.6 / -208 / -208 / -102 / -2506 / False / -4.7 / 1.01 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_A7 | 3 | 15.5 / 233 / 234 / 277 / 8023 / True / -0.2 / 0.98 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_asia | 3 | 5.9 / 1063 / 1047 / 1503 / 3182 / True / -5.7 / 1.02 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_london | 3 | -1.0 / -721 / -724 / -459 / 925 / False / -7.5 / 0.95 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_nyam | 3 | -0.0 / -260 / -259 / -163 / -10 / True / 0.3 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_nypm | 3 | 0.0 / -50 / -49 / -29 / 0 / True / -2.9 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_K7 | 3 | 0.4 / 744 / 745 / 994 / 333 / True / -2.9 / 1.05 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_P7 | 3 | -2.7 / -2082 / -2094 / -1658 / -1367 / False / 4.7 / 0.90 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_U7 | 3 | 0.1 / 590 / 587 / 690 / 25 / True / 0.0 / 1.03 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_H7 | 3 | 0.2 / -127 / -128 / -80 / 10 / True / -0.1 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_M7 | 3 | -6.6 / -1513 / -1505 / -1369 / -1961 / False / -0.8 / 1.02 / 1 | - / - / - / - | - / - | - / - |
| LE_C2_A7 | 3 | 15.2 / 737 / 738 / 794 / 7920 / True / 0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_asia | 3 | -1.7 / 43 / 31 / 601 / -832 / False / 5.5 / 1.03 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_london | 3 | 0.8 / -1825 / -1822 / -1501 / 1897 / False / -3.7 / 0.97 / 1 | - / - / - / - | - / - | - / - |
| LE_C2_nyam | 3 | -0.2 / -227 / -226 / -122 / -108 / True / 0.2 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C2_nypm | 3 | 0.0 / -49 / -49 / -26 / 0 / True / -2.9 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_P7_london | 3 | 0.0 / -1329 / -1330 / -1237 / 0 / False / -0.3 / 0.93 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_K7_london | 3 | 6.3 / 415 / 413 / 470 / 3291 / True / -0.5 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_K7_nyam | 3 | -0.0 / 72 / 72 / 99 / -10 / True / 0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_M7_london | 3 | -7.6 / -9 / -9 / 72 / -2506 / False / -4.7 / 1.02 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_M7_nyam | 3 | 0.0 / -215 / -215 / -188 / 0 / True / 0.0 / 0.99 / 0 | - / - / - / - | - / - | - / - |
| LE_C1_A7_asia | 3 | 15.5 / 233 / 234 / 277 / 8023 / True / -0.2 / 0.98 / 0 | - / - / - / - | - / - | - / - |

### WK  work the cut with a resting limit (per book / session / 08:30)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|
| WK2_K7 | 3 | 0.2 / -23 / -28 / -41 / 54 / True / 2.6 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_P7 | 3 | -2.8 / -168 / -173 / -188 / -1158 / False / -0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_U7 | 3 | 0.1 / 77 / 77 / 76 / 32 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_H7 | 3 | 0.0 / 27 / 27 / 27 / 82 / True / 0.3 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_M7 | 3 | 0.1 / -59 / -59 / -61 / 22 / True / -0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_A7 | 3 | 0.1 / 86 / 85 / 85 / -6 / True / 0.1 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_asia | 3 | -2.5 / 9 / 4 / -12 / -1043 / False / 2.3 / 1.01 / 0 | - / - / - / - | - / - | - / - |
| WK2_london | 3 | 0.1 / -183 / -184 / -189 / 42 / True / -1.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_nyam | 3 | 0.0 / 19 / 19 / 18 / 19 / True / -0.3 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_nypm | 3 | 0.0 / 12 / 12 / 12 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_W830 | 3 | 0.0 / 9 / 9 / 9 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK5_W830 | 3 | 0.0 / 15 / 15 / 15 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| WK2_ALLCUTS | 3 | -2.2 / -75 / -82 / -101 / -943 / False / 1.4 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### SJ  join-then-market stop seconds

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

## 3. Hits and auto-expansions (PART 0)

Hits (L3M tolerant gate and d mean > 0): BR_M7_H15, EV_T0830_P10_H, EV_T0830_P20_H, EV_T0830_P30_H, EV_T0830_P60_S, EV_T0830_P60_H, RB_asia_K100_EV, TG1_K7, TG1_A7, TG1_ALL, TG2_K7, TG2_A7, TG2_ALL, LE_C1_K7, LE_C1_U7, LE_C1_A7, LE_C1_asia, LE_C2_K7, LE_C2_U7, LE_C2_A7, LE_C1_K7_london, LE_C1_K7_nyam, LE_C1_A7_asia, WK2_U7, WK2_H7, WK2_A7, WK2_nyam, WK2_nypm, WK2_W830, WK5_W830

Auto-expansions launched (expansion of <parent>):

- HIT BR_M7_H15: L3M cut 1.2% d mean 144 (adj 157) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - BR_M7_H15_Sasi: expansion of BR_M7_H15
- - BR_M7_H15_Slon: expansion of BR_M7_H15
- - BR_M7_H15_Snya: expansion of BR_M7_H15
- - BR_M7_H15_Snyp: expansion of BR_M7_H15
- - BR_M7_H15_xt5: expansion of BR_M7_H15
- - BR_M7_H15_30: expansion of BR_M7_H15
- - BR_M7_H15_v19: expansion of BR_M7_H15
- - BR_M7_H15_G2: expansion of BR_M7_H15
- - BR_M7_H15_K7: expansion of BR_M7_H15
- - BR_M7_H15_P7: expansion of BR_M7_H15
- - BR_M7_H15_U7: expansion of BR_M7_H15
- - BR_M7_H15_H7: expansion of BR_M7_H15
- - BR_M7_H15_A7: expansion of BR_M7_H15
- - BR_M7_H15_O7: expansion of BR_M7_H15
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P30_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P30_H_p5: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p15: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p45: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_p90: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_sasi: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_slon: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_snya: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_snyp: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_oth: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kCPI: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kPCE: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kISM_MFG: expansion of EV_T0830_P30_H
- - EV_T0830_P30_H_kFOMC: expansion of EV_T0830_P30_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P60_S: L3M cut 0.0% d mean 206 (adj 222) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P60_S_p5: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p15: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p45: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_p90: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_sasi: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_slon: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_snya: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_snyp: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_oth: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kCPI: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kPCE: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kISM_MFG: expansion of EV_T0830_P60_S
- - EV_T0830_P60_S_kFOMC: expansion of EV_T0830_P60_S
- HIT EV_T0830_P60_H: L3M cut 0.0% d mean 102 (adj 107) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P60_H_p5: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p15: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p45: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_p90: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_sasi: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_slon: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_snya: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_snyp: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_oth: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kCPI: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kPCE: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kISM_MFG: expansion of EV_T0830_P60_H
- - EV_T0830_P60_H_kFOMC: expansion of EV_T0830_P60_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT EV_T0830_P10_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P10_H_p5: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p15: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p45: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_p90: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_sasi: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_slon: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_snya: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_snyp: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_oth: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kCPI: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kPCE: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kISM_MFG: expansion of EV_T0830_P10_H
- - EV_T0830_P10_H_kFOMC: expansion of EV_T0830_P10_H
- HIT EV_T0830_P20_H: L3M cut 0.0% d mean 51 (adj 55) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - EV_T0830_P20_H_p5: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p15: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p45: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_p90: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_sasi: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_slon: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_snya: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_snyp: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_oth: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kCPI: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kPCE: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kISM_MFG: expansion of EV_T0830_P20_H
- - EV_T0830_P20_H_kFOMC: expansion of EV_T0830_P20_H
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG1_K7: L3M cut -0.2% d mean 455 (adj 464) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_K7_t3: expansion of TG1_K7
- - TG1_K7_t4: expansion of TG1_K7
- - TG1_K7_K7: expansion of TG1_K7
- - TG1_K7_P7: expansion of TG1_K7
- - TG1_K7_U7: expansion of TG1_K7
- - TG1_K7_H7: expansion of TG1_K7
- - TG1_K7_M7: expansion of TG1_K7
- - TG1_K7_A7: expansion of TG1_K7
- - TG1_K7_sasi: expansion of TG1_K7
- - TG1_K7_slon: expansion of TG1_K7
- - TG1_K7_snya: expansion of TG1_K7
- - TG1_K7_snyp: expansion of TG1_K7
- HIT TG1_A7: L3M cut -0.1% d mean 208 (adj 209) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_A7_t3: expansion of TG1_A7
- - TG1_A7_t4: expansion of TG1_A7
- - TG1_A7_K7: expansion of TG1_A7
- - TG1_A7_P7: expansion of TG1_A7
- - TG1_A7_U7: expansion of TG1_A7
- - TG1_A7_H7: expansion of TG1_A7
- - TG1_A7_M7: expansion of TG1_A7
- - TG1_A7_A7: expansion of TG1_A7
- - TG1_A7_sasi: expansion of TG1_A7
- - TG1_A7_slon: expansion of TG1_A7
- - TG1_A7_snya: expansion of TG1_A7
- - TG1_A7_snyp: expansion of TG1_A7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG1_ALL: L3M cut -0.7% d mean 368 (adj 377) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG1_ALL_t3: expansion of TG1_ALL
- - TG1_ALL_t4: expansion of TG1_ALL
- - TG1_ALL_K7: expansion of TG1_ALL
- - TG1_ALL_P7: expansion of TG1_ALL
- - TG1_ALL_U7: expansion of TG1_ALL
- - TG1_ALL_H7: expansion of TG1_ALL
- - TG1_ALL_M7: expansion of TG1_ALL
- - TG1_ALL_A7: expansion of TG1_ALL
- - TG1_ALL_sasi: expansion of TG1_ALL
- - TG1_ALL_slon: expansion of TG1_ALL
- - TG1_ALL_snya: expansion of TG1_ALL
- - TG1_ALL_snyp: expansion of TG1_ALL
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG2_K7: L3M cut 6.7% d mean 795 (adj 797) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG2_K7_t3: expansion of TG2_K7
- - TG2_K7_t4: expansion of TG2_K7
- - TG2_K7_K7: expansion of TG2_K7
- - TG2_K7_P7: expansion of TG2_K7
- - TG2_K7_U7: expansion of TG2_K7
- - TG2_K7_H7: expansion of TG2_K7
- - TG2_K7_M7: expansion of TG2_K7
- - TG2_K7_A7: expansion of TG2_K7
- - TG2_K7_sasi: expansion of TG2_K7
- - TG2_K7_slon: expansion of TG2_K7
- - TG2_K7_snya: expansion of TG2_K7
- - TG2_K7_snyp: expansion of TG2_K7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT WK2_U7: L3M cut 0.1% d mean 77 (adj 76) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_U7_w1: expansion of WK2_U7
- - WK2_U7_w3: expansion of WK2_U7
- - WK2_U7_w5: expansion of WK2_U7
- - WK2_U7_touch: expansion of WK2_U7
- - WK2_U7_fb12: expansion of WK2_U7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT TG2_A7: L3M cut -0.2% d mean 94 (adj 94) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG2_A7_t3: expansion of TG2_A7
- - TG2_A7_t4: expansion of TG2_A7
- - TG2_A7_K7: expansion of TG2_A7
- - TG2_A7_P7: expansion of TG2_A7
- - TG2_A7_U7: expansion of TG2_A7
- - TG2_A7_H7: expansion of TG2_A7
- - TG2_A7_M7: expansion of TG2_A7
- - TG2_A7_A7: expansion of TG2_A7
- - TG2_A7_sasi: expansion of TG2_A7
- - TG2_A7_slon: expansion of TG2_A7
- - TG2_A7_snya: expansion of TG2_A7
- - TG2_A7_snyp: expansion of TG2_A7
- HIT TG2_ALL: L3M cut 5.7% d mean 194 (adj 194) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - TG2_ALL_t3: expansion of TG2_ALL
- - TG2_ALL_t4: expansion of TG2_ALL
- - TG2_ALL_K7: expansion of TG2_ALL
- - TG2_ALL_P7: expansion of TG2_ALL
- - TG2_ALL_U7: expansion of TG2_ALL
- - TG2_ALL_H7: expansion of TG2_ALL
- - TG2_ALL_M7: expansion of TG2_ALL
- - TG2_ALL_A7: expansion of TG2_ALL
- - TG2_ALL_sasi: expansion of TG2_ALL
- - TG2_ALL_slon: expansion of TG2_ALL
- - TG2_ALL_snya: expansion of TG2_ALL
- - TG2_ALL_snyp: expansion of TG2_ALL
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT WK2_H7: L3M cut 0.0% d mean 27 (adj 27) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_H7_w1: expansion of WK2_H7
- - WK2_H7_w3: expansion of WK2_H7
- - WK2_H7_w5: expansion of WK2_H7
- - WK2_H7_touch: expansion of WK2_H7
- - WK2_H7_fb12: expansion of WK2_H7
- HIT WK2_A7: L3M cut 0.1% d mean 86 (adj 85) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_A7_w1: expansion of WK2_A7
- - WK2_A7_w3: expansion of WK2_A7
- - WK2_A7_w5: expansion of WK2_A7
- - WK2_A7_touch: expansion of WK2_A7
- - WK2_A7_fb12: expansion of WK2_A7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C1_K7: L3M cut 6.8% d mean 1719 (adj 1906) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_K7_T3: expansion of LE_C1_K7
- - LE_C1_K7_T15: expansion of LE_C1_K7
- - LE_C1_K7_T30: expansion of LE_C1_K7
- - LE_C1_K7_bid: expansion of LE_C1_K7
- - LE_C1_K7_mid: expansion of LE_C1_K7
- - LE_C1_K7_touch: expansion of LE_C1_K7
- - LE_C1_K7_skip: expansion of LE_C1_K7
- - LE_C1_K7_K7: expansion of LE_C1_K7
- - LE_C1_K7_P7: expansion of LE_C1_K7
- - LE_C1_K7_U7: expansion of LE_C1_K7
- - LE_C1_K7_H7: expansion of LE_C1_K7
- - LE_C1_K7_M7: expansion of LE_C1_K7
- - LE_C1_K7_A7: expansion of LE_C1_K7
- HIT WK2_W830: L3M cut 0.0% d mean 9 (adj 9) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_W830_w1: expansion of WK2_W830
- - WK2_W830_w3: expansion of WK2_W830
- - WK2_W830_w5: expansion of WK2_W830
- - WK2_W830_touch: expansion of WK2_W830
- - WK2_W830_fb12: expansion of WK2_W830
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C1_U7: L3M cut 0.3% d mean 523 (adj 607) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_U7_T3: expansion of LE_C1_U7
- - LE_C1_U7_T15: expansion of LE_C1_U7
- - LE_C1_U7_T30: expansion of LE_C1_U7
- - LE_C1_U7_bid: expansion of LE_C1_U7
- - LE_C1_U7_mid: expansion of LE_C1_U7
- - LE_C1_U7_touch: expansion of LE_C1_U7
- - LE_C1_U7_skip: expansion of LE_C1_U7
- - LE_C1_U7_K7: expansion of LE_C1_U7
- - LE_C1_U7_P7: expansion of LE_C1_U7
- - LE_C1_U7_U7: expansion of LE_C1_U7
- - LE_C1_U7_H7: expansion of LE_C1_U7
- - LE_C1_U7_M7: expansion of LE_C1_U7
- - LE_C1_U7_A7: expansion of LE_C1_U7
- HIT LE_C1_asia: L3M cut 5.9% d mean 1063 (adj 1503) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_asia_T3: expansion of LE_C1_asia
- - LE_C1_asia_T15: expansion of LE_C1_asia
- - LE_C1_asia_T30: expansion of LE_C1_asia
- - LE_C1_asia_bid: expansion of LE_C1_asia
- - LE_C1_asia_mid: expansion of LE_C1_asia
- - LE_C1_asia_touch: expansion of LE_C1_asia
- - LE_C1_asia_skip: expansion of LE_C1_asia
- - LE_C1_asia_K7: expansion of LE_C1_asia
- - LE_C1_asia_P7: expansion of LE_C1_asia
- - LE_C1_asia_U7: expansion of LE_C1_asia
- - LE_C1_asia_H7: expansion of LE_C1_asia
- - LE_C1_asia_M7: expansion of LE_C1_asia
- - LE_C1_asia_A7: expansion of LE_C1_asia
- HIT WK2_nypm: L3M cut 0.0% d mean 12 (adj 12) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_nypm_w1: expansion of WK2_nypm
- - WK2_nypm_w3: expansion of WK2_nypm
- - WK2_nypm_w5: expansion of WK2_nypm
- - WK2_nypm_touch: expansion of WK2_nypm
- - WK2_nypm_fb12: expansion of WK2_nypm
- HIT WK5_W830: L3M cut 0.0% d mean 15 (adj 15) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK5_W830_w1: expansion of WK5_W830
- - WK5_W830_w3: expansion of WK5_W830
- - WK5_W830_w5: expansion of WK5_W830
- - WK5_W830_touch: expansion of WK5_W830
- - WK5_W830_fb12: expansion of WK5_W830
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C1_A7: L3M cut 15.5% d mean 233 (adj 277) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_A7_T3: expansion of LE_C1_A7
- - LE_C1_A7_T15: expansion of LE_C1_A7
- - LE_C1_A7_T30: expansion of LE_C1_A7
- - LE_C1_A7_bid: expansion of LE_C1_A7
- - LE_C1_A7_mid: expansion of LE_C1_A7
- - LE_C1_A7_touch: expansion of LE_C1_A7
- - LE_C1_A7_skip: expansion of LE_C1_A7
- - LE_C1_A7_K7: expansion of LE_C1_A7
- - LE_C1_A7_P7: expansion of LE_C1_A7
- - LE_C1_A7_U7: expansion of LE_C1_A7
- - LE_C1_A7_H7: expansion of LE_C1_A7
- - LE_C1_A7_M7: expansion of LE_C1_A7
- - LE_C1_A7_A7: expansion of LE_C1_A7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C2_U7: L3M cut 0.1% d mean 590 (adj 690) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C2_U7_T3: expansion of LE_C2_U7
- - LE_C2_U7_T15: expansion of LE_C2_U7
- - LE_C2_U7_T30: expansion of LE_C2_U7
- - LE_C2_U7_bid: expansion of LE_C2_U7
- - LE_C2_U7_mid: expansion of LE_C2_U7
- - LE_C2_U7_touch: expansion of LE_C2_U7
- - LE_C2_U7_skip: expansion of LE_C2_U7
- - LE_C2_U7_K7: expansion of LE_C2_U7
- - LE_C2_U7_P7: expansion of LE_C2_U7
- - LE_C2_U7_U7: expansion of LE_C2_U7
- - LE_C2_U7_H7: expansion of LE_C2_U7
- - LE_C2_U7_M7: expansion of LE_C2_U7
- - LE_C2_U7_A7: expansion of LE_C2_U7
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C2_K7: L3M cut 0.4% d mean 744 (adj 994) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C2_K7_T3: expansion of LE_C2_K7
- - LE_C2_K7_T15: expansion of LE_C2_K7
- - LE_C2_K7_T30: expansion of LE_C2_K7
- - LE_C2_K7_bid: expansion of LE_C2_K7
- - LE_C2_K7_mid: expansion of LE_C2_K7
- - LE_C2_K7_touch: expansion of LE_C2_K7
- - LE_C2_K7_skip: expansion of LE_C2_K7
- - LE_C2_K7_K7: expansion of LE_C2_K7
- - LE_C2_K7_P7: expansion of LE_C2_K7
- - LE_C2_K7_U7: expansion of LE_C2_K7
- - LE_C2_K7_H7: expansion of LE_C2_K7
- - LE_C2_K7_M7: expansion of LE_C2_K7
- - LE_C2_K7_A7: expansion of LE_C2_K7
- HIT LE_C2_A7: L3M cut 15.2% d mean 737 (adj 794) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C2_A7_T3: expansion of LE_C2_A7
- - LE_C2_A7_T15: expansion of LE_C2_A7
- - LE_C2_A7_T30: expansion of LE_C2_A7
- - LE_C2_A7_bid: expansion of LE_C2_A7
- - LE_C2_A7_mid: expansion of LE_C2_A7
- - LE_C2_A7_touch: expansion of LE_C2_A7
- - LE_C2_A7_skip: expansion of LE_C2_A7
- - LE_C2_A7_K7: expansion of LE_C2_A7
- - LE_C2_A7_P7: expansion of LE_C2_A7
- - LE_C2_A7_U7: expansion of LE_C2_A7
- - LE_C2_A7_H7: expansion of LE_C2_A7
- - LE_C2_A7_M7: expansion of LE_C2_A7
- - LE_C2_A7_A7: expansion of LE_C2_A7
- HIT WK2_nyam: L3M cut 0.0% d mean 19 (adj 18) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - WK2_nyam_w1: expansion of WK2_nyam
- - WK2_nyam_w3: expansion of WK2_nyam
- - WK2_nyam_w5: expansion of WK2_nyam
- - WK2_nyam_touch: expansion of WK2_nyam
- - WK2_nyam_fb12: expansion of WK2_nyam
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT LE_C1_K7_london: L3M cut 6.3% d mean 415 (adj 470) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_K7_london_T3: expansion of LE_C1_K7_london
- - LE_C1_K7_london_T15: expansion of LE_C1_K7_london
- - LE_C1_K7_london_T30: expansion of LE_C1_K7_london
- - LE_C1_K7_london_bid: expansion of LE_C1_K7_london
- - LE_C1_K7_london_mid: expansion of LE_C1_K7_london
- - LE_C1_K7_london_touch: expansion of LE_C1_K7_london
- - LE_C1_K7_london_skip: expansion of LE_C1_K7_london
- - LE_C1_K7_london_K7: expansion of LE_C1_K7_london
- - LE_C1_K7_london_P7: expansion of LE_C1_K7_london
- - LE_C1_K7_london_U7: expansion of LE_C1_K7_london
- - LE_C1_K7_london_H7: expansion of LE_C1_K7_london
- - LE_C1_K7_london_M7: expansion of LE_C1_K7_london
- - LE_C1_K7_london_A7: expansion of LE_C1_K7_london
- HIT LE_C1_K7_nyam: L3M cut -0.0% d mean 72 (adj 99) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_K7_nyam_T3: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_T15: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_T30: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_bid: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_mid: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_touch: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_skip: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_K7: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_P7: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_U7: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_H7: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_M7: expansion of LE_C1_K7_nyam
- - LE_C1_K7_nyam_A7: expansion of LE_C1_K7_nyam
- HIT LE_C1_A7_asia: L3M cut 15.5% d mean 233 (adj 277) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - LE_C1_A7_asia_T3: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_T15: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_T30: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_bid: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_mid: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_touch: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_skip: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_K7: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_P7: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_U7: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_H7: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_M7: expansion of LE_C1_A7_asia
- - LE_C1_A7_asia_A7: expansion of LE_C1_A7_asia
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)
- HIT RB_asia_K100_EV: L3M cut 16.3% d mean 1584 (adj 1642) -> promoted to L6M/HOLD/GAP/PRE and battery launched
- - RB_asia_K100_EV_k50: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_k60: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_k90: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_k110: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_k150: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_sasi: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_slon: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_snya: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_snyp: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_b3: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_bnone: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_oth: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_K7: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_P7: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_U7: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_H7: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_M7: expansion of RB_asia_K100_EV
- - RB_asia_K100_EV_A7: expansion of RB_asia_K100_EV
- - NOT SUPPORTED in this registry: size-UP mirror (needs a size-up hook), carry to next session, fresh/rechase split, joint (sent to W-JV)

## 4. Not run / limits
- Passive-entry fill rule: a print through the limit by 1 tick (primary). Engine has no queue position model; real fill rates for resting limits are not in the frozen live set. Treat LE rows as an upper bound on fills.
- 08:30: bump of +1.36 pt applies to market/stop exits starting 08:30-08:44 ET and is NOT inside the engine; it is added in the live-exc column only.
- Stop-limit cut, depth-conditional passive entry and per-slot refits (SMART_B not-run list) are queued only after the first hits.
