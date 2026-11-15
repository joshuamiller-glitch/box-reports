# DS3_DEEPEN_LOSS_B - T-DEEPEN PART 1 item 6 (SKIPS) and item 9 (EXECUTION COSTS), W-LB

**VERDICT (plain): 8 of 127 cells have an exact L3M result so far; 1 pass the tolerant gate in L3M with a positive mean (candidates for promotion, none claimed). Item 9 cost measurement is in section 1: fees plus excess slippage are 16.0% of L6M gross, the 08:30 bump is only about $50-60/wk of it. No PASS claim.**

Written 2026-11-15T02:31Z (date -u). Research only, shadow, no PASS claims. Prereg autopilot/DEEPEN_LB_PREREG.md (sha 9d2b5bd88f64ed49 in DECISIONS.md). Code code/th_deepen_lb (lb_hooks.py outermost additive hook; lb_cells.py registry; lb_score.py; lb_page.py), bulk /mnt/l2/l2vast/_deepen_lb. Identity: TL3_LB_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_LB_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.

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
| BR_M7_X15 | 3 | -6.1 / -1491 / -1489 / -1490 / -2520 / False / 3.9 / 0.97 / 0 | - / - / - / - | - / - | - / - |
| BR_M7_H15 | 3 | 1.2 / 144 / 147 / 157 / 615 / True / 5.7 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_X15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_A7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_O7_H15 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |
| BR_P7_X5 | 3 | 0.0 / 0 / 0 / 0 / 0 / True / 0.0 / 1.00 / 0 | - / - / - / - | - / - | - / - |

### EV  skips / half before scheduled events (calendar from 2024-10; identity before)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### RB  range used up AND breadth / event day (HAR+CME forecast; plain range rule is W-EC)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### TG  target 1-2 ticks short

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### LE  passive vs market entry per book / session (through-1-tick fill rule, market on timeout)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### WK  work the cut with a resting limit (per book / session / 08:30)

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

### SJ  join-then-market stop seconds

| cell | months | L3M cut / d mean / $4.84 / live-exc / d ww / gate / x44 cut / b5 / w2l | L6M cut / d mean / live-exc / gate | HOLD cut / d mean | PRE cut / d mean |
|---|---|---|---|---|---|

## 3. Hits and auto-expansions (PART 0)

Hits (L3M tolerant gate and d mean > 0): BR_M7_H15

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

## 4. Not run / limits
- Passive-entry fill rule: a print through the limit by 1 tick (primary). Engine has no queue position model; real fill rates for resting limits are not in the frozen live set. Treat LE rows as an upper bound on fills.
- 08:30: bump of +1.36 pt applies to market/stop exits starting 08:30-08:44 ET and is NOT inside the engine; it is added in the live-exc column only.
- Stop-limit cut, depth-conditional passive entry and per-slot refits (SMART_B not-run list) are queued only after the first hits.
