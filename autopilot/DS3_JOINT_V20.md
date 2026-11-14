# DS3_JOINT_V20 - joint of the shelved candidates on JN05W2 (PRIORITY 4) - W-JV

VERDICT (3 of 5 windows complete for the leader): best joint set so far is JV_AB: worst-window max-DD cut 15.6 % vs JN05W2, mean 991 $/wk avg; passes the tolerant gate in every complete window. Recent max DD is the single week 2026-W44, so read section 2 and section 5 before believing any recent cut; no PASS claim.

Generated 2026-11-14 17:16 UTC (epoch 1794676580). Exact engine (TP), base JN05W2 = live panel + F3 + E1 + C22 + BR3S + FLAT45K, all layers ON, measured fills (engine slip 0.8; structure stop 1.4 adverse; $4.84 RT). Shadow only, no PASS claim. Prereg autopilot/JOINTV20_PREREG.md (sha in DECISIONS.md).

Candidates: **A** = SM_A6_halfNP7 (first trade of a book-session lost -> later signals of that book-session at half lots, books K7 M7 U7 H7 A7; P7 untouched). **B** = U7 time stop on fresh entries (at 15:00 after the first fill, if open P&L < -10 pts: market exit, fresh context only). **C** = U7 Keltner-mid structure stop (stop at 5-min EMA20 mid - 2 pts, filled 1.4 pt adverse, lots x 60/stop distance clamped 25..60). Full specs in section 6.

Identity: TL3_JV_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Drawdown first: all combinations vs JN05W2 (cut % = max-DD of the weekly series vs JN05W2, + = shallower; worst wk d = change of the worst week; stops/wk; 5 best JN05W2 weeks kept; winning weeks turned losing; d mean $/wk)

### L1M

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 4 | 32090 | 36371 | 11.8 | -32090 | 4280 | 13.8 (13.2) | - | 0 (2) | -1561 | -2168 |
| JV_B | 4 | 31572 | 36371 | 13.2 | -31572 | 4799 | 12.0 (13.2) | - | 0 (2) | 3190 | 2584 |
| JV_C | 4 | 35985 | 36371 | 1.1 | -35985 | 385 | 11.0 (13.2) | - | 0 (2) | 2962 | 2356 |
| JV_AB | 4 | 27291 | 36371 | 25.0 | -27291 | 9079 | 12.2 (13.2) | - | 0 (2) | 849 | 242 |
| JV_AC | 4 | 31705 | 36371 | 12.8 | -31705 | 4666 | 11.0 (13.2) | - | 0 (2) | 2468 | 1861 |
| JV_BC | 4 | 32311 | 36371 | 11.2 | -32311 | 4059 | 10.5 (13.2) | - | 0 (2) | 4757 | 4150 |
| JV_ABC | 4 | 28031 | 36371 | 22.9 | -28031 | 8340 | 10.8 (13.2) | - | 0 (2) | 3627 | 3021 |

### L3M

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 13 | 32090 | 36371 | 11.8 | -32090 | 4280 | 10.6 (10.5) | 94% | 0 (9) | 15324 | -691 |
| JV_B | 13 | 32117 | 36371 | 11.7 | -31572 | 4799 | 9.5 (10.5) | 106% | 0 (9) | 17259 | 1244 |
| JV_C | 13 | 35985 | 36371 | 1.1 | -35985 | 385 | 8.1 (10.5) | 108% | 0 (9) | 17761 | 1746 |
| JV_AB | 13 | 27291 | 36371 | 25.0 | -27291 | 9079 | 9.6 (10.5) | 99% | 0 (9) | 16651 | 636 |
| JV_AC | 13 | 31705 | 36371 | 12.8 | -31705 | 4666 | 8.3 (10.5) | 105% | 0 (9) | 17218 | 1203 |
| JV_BC | 13 | 32311 | 36371 | 11.2 | -32311 | 4059 | 7.6 (10.5) | 112% | 0 (9) | 18754 | 2739 |
| JV_ABC | 13 | 28031 | 36371 | 22.9 | -28031 | 8340 | 7.9 (10.5) | 108% | 0 (9) | 18016 | 2001 |

### L6M

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 26 | 32090 | 36371 | 11.8 | -32090 | 4280 | 11.1 (11.1) | 104% | 0 (19) | 25520 | 383 |
| JV_B | 26 | 32117 | 36371 | 11.7 | -31572 | 4799 | 10.4 (11.1) | 97% | 0 (19) | 25710 | 573 |
| JV_C | 26 | 35985 | 36371 | 1.1 | -35985 | 385 | 8.8 (11.1) | 107% | 1 (19) | 25849 | 712 |
| JV_AB | 26 | 27641 | 36371 | 24.0 | -27641 | 8729 | 10.3 (11.1) | 101% | 0 (19) | 26083 | 946 |
| JV_AC | 26 | 33171 | 36371 | 8.8 | -33171 | 3199 | 8.9 (11.1) | 109% | 1 (19) | 26253 | 1116 |
| JV_BC | 26 | 33163 | 36371 | 8.8 | -33163 | 3207 | 8.5 (11.1) | 105% | 1 (19) | 26354 | 1217 |
| JV_ABC | 26 | 33171 | 36371 | 8.8 | -33171 | 3199 | 8.6 (11.1) | 108% | 1 (19) | 26608 | 1472 |

### HOLD

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 52 | 55870 | 63185 | 11.6 | -55870 | -725 | 10.7 (10.7) | 103% | 0 (37) | 18213 | 724 |
| JV_B | 52 | 61073 | 63185 | 3.3 | -55145 | 0 | 10.1 (10.7) | 99% | 0 (37) | 18288 | 799 |
| JV_C | 52 | 73536 | 63185 | -16.4 | -57536 | -2390 | 8.3 (10.7) | 97% | 2 (37) | 17634 | 145 |
| JV_AB | 52 | 53321 | 63185 | 15.6 | -53321 | 1825 | 10.0 (10.7) | 102% | 0 (37) | 18881 | 1391 |
| JV_AC | 52 | 76099 | 63185 | -20.4 | -57490 | -2345 | 8.4 (10.7) | 98% | 1 (37) | 18093 | 604 |
| JV_BC | 52 | 71971 | 63185 | -13.9 | -56582 | -1437 | 8.1 (10.7) | 95% | 2 (37) | 18186 | 697 |

### PRE

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 75 | 81965 | 76186 | -7.6 | -51421 | 1126 | 9.2 (9.3) | 97% | 0 (48) | 10126 | -42 |
| JV_B | 75 | 76961 | 76186 | -1.0 | -52547 | 0 | 9.0 (9.3) | 101% | 0 (48) | 10078 | -90 |

### X'

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 44 | 50995 | 55326 | 7.8 | -21733 | -70 | 10.8 (10.8) | 99% | 0 (25) | 3828 | 243 |
| JV_B | 44 | 45376 | 55326 | 18.0 | -21663 | 0 | 10.6 (10.8) | 98% | 0 (25) | 3834 | 249 |

### GAP

| set | weeks | maxDD | JN05W2 | cut % | worst wk | d worst wk | full stops/wk (ref) | 5 best wks kept | win->lose (of) | mean $/wk | d mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| JV_A | 18 | 67381 | 68947 | 2.3 | -67381 | 1566 | 9.6 (9.7) | 94% | 1 (13) | 11461 | -915 |
| JV_B | 18 | 68947 | 68947 | 0.0 | -68947 | 0 | 9.6 (9.7) | 101% | 0 (13) | 12381 | 5 |

## 2. The recent max drawdown is one week (2026-W44): L6M / L3M with W44 removed from both cell and JN05W2

| set | window | maxDD (W44 out) | JN05W2 (W44 out) | cut % | d mean $/wk (W44 out) | cut % with W44 in |
|--|--|--|--|--|--|--|
| JV_A | L3M | 22092 | 30533 | 27.6 | -1106 | 11.8 |
| JV_A | L6M | 28644 | 30533 | 6.2 | 228 | 11.8 |
| JV_B | L3M | 32117 | 30533 | -5.2 | 947 | 11.7 |
| JV_B | L6M | 32117 | 30533 | -5.2 | 404 | 11.7 |
| JV_C | L3M | 21896 | 30533 | 28.3 | 1859 | 1.1 |
| JV_C | L6M | 33163 | 30533 | -8.6 | 725 | 1.1 |
| JV_AB | L3M | 21889 | 30533 | 28.3 | -67 | 25.0 |
| JV_AB | L6M | 27641 | 30533 | 9.5 | 620 | 24.0 |
| JV_AC | L3M | 17808 | 30533 | 41.7 | 915 | 12.8 |
| JV_AC | L6M | 33171 | 30533 | -8.6 | 974 | 8.8 |
| JV_BC | L3M | 21896 | 30533 | 28.3 | 2629 | 11.2 |
| JV_BC | L6M | 33163 | 30533 | -8.6 | 1104 | 8.8 |
| JV_ABC | L3M | 17808 | 30533 | 41.7 | 1473 | 22.9 |
| JV_ABC | L6M | 33171 | 30533 | -8.6 | 1197 | 8.8 |

## 3. Trend-week clause (L6M, program convention: 5 best LPB_BASE weeks) and bi-weekly walk-forward vs JN05W2 (43 months)

| set | 5 best LPB wks $ (cell / JN05W2 / LPB_BASE) | LPB winning wks turned losing | weeks beating JN05W2 (of 26) | WF beat % | WF cut % | WF d mean $/wk |
|--|--|--|--|--|--|--|
| JV_A | 253399 / 255545 / 331449 | 0 of 19 | 9 | 41.8 | 0.8 | 88.5 |
| JV_B | 261019 / 255545 / 331449 | 0 of 19 | 15 | 16.5 | 0.0 | 24.5 |
| JV_C | 257064 / 255545 / 331449 | 3 of 19 | 14 | - | - | - |
| JV_AB | 258872 / 255545 / 331449 | 0 of 19 | 13 | - | - | - |
| JV_AC | 258347 / 255545 / 331449 | 2 of 19 | 12 | - | - | - |
| JV_BC | 265480 / 255545 / 331449 | 2 of 19 | 14 | - | - | - |
| JV_ABC | 266763 / 255545 / 331449 | 2 of 19 | 14 | - | - | - |

## 4. Interaction table (joint vs sum of the singles, L6M and HOLD; d = cell - JN05W2; synergy = joint - sum of singles; DD synergy in cut-% points)

| joint | window | joint DD cut % | sum of singles' cut % | synergy | joint d mean | sum singles d mean | synergy $/wk |
|--|--|--|--|--|--|--|--|
| JV_AB | L6M | 24.0 | 23.5 | 0.5 | 946 | 956 | -10 |
| JV_AB | HOLD | 15.6 | 14.9 | 0.7 | 1391 | 1523 | -131 |
| JV_AC | L6M | 8.8 | 12.8 | -4.0 | 1116 | 1095 | 21 |
| JV_AC | HOLD | -20.4 | -4.8 | -15.6 | 604 | 868 | -264 |
| JV_BC | L6M | 8.8 | 12.8 | -3.9 | 1217 | 1284 | -67 |
| JV_BC | HOLD | -13.9 | -13.0 | -0.9 | 697 | 944 | -247 |
| JV_ABC | L6M | 8.8 | 24.5 | -15.7 | 1472 | 1668 | -196 |

## 5. Exact placebos (A: first-trade-lost read from 11 / 23 / 37 days earlier; B and C: same trigger, exit at a random later second 1..60 min if still open; PLk_ABC = all three placebos together)

| real set | window | real cut % | real d mean | placebo cut % (11/23/37 or seeds 1/2/3) | placebo d mean | real beats all 3 placebos on cut? |
|--|--|--|--|--|--|--|

## 6. Ranking (tolerant gate in every complete window of L3M L6M HOLD PRE X': DD cut > -2 %, mean not lower than -3 %; then by the WORST-window DD cut)

| rank | set | passes gate | worst-window DD cut % | mean d $/wk (avg of windows) | complete windows |
|--|--|--|--|--|--|
| 1 | JV_AB | yes | 15.6 | 991 | 3 |
| 2 | JV_ABC | yes | 8.8 | 1736 | 2 |
| 3 | JV_B | yes | -1.0 | 555 | 5 |
| 4 | JV_A | no | -7.6 | 123 | 5 |
| 5 | JV_BC | no | -13.9 | 1551 | 3 |
| 6 | JV_C | no | -16.4 | 867 | 3 |
| 7 | JV_AC | no | -20.4 | 974 | 3 |

## 7. FULL SPEC of each rule exactly as scored (for the v2.0 build)

Order of evaluation inside the engine (outermost last): wb_hooks (F3 context cut, E1/C22/BR3S panel) -> **sm_hooks (K7 flat -45, then B, then C; all three are exit rules plus C's lot scaling)** -> scr_hooks / c_gov (entry gates: skip rules, P7 governor) -> **A (sm1_hooks, outermost: entry-time lot multiplier)**. Exits B and C and the K7 flat are evaluated on 1-second rows of the state-base mid, decision at the close of row r, market exit at row r+1; the first rule of a trade that fires ends it (rule list order: K7 flat, B, C). The engine's native bracket (60-pt stop, 60-pt target for these books) and the 80-pt catastrophe stop stay in place as backstops; an engine exit that happens first simply wins (the rule exit event is dropped if the trade is no longer open).

**A = SM_A6_halfNP7 (entry sizing).** Books K7, M7, U7, H7, A7 (P7 and O7 untouched). At a signal of book B at time t, key K = the six-session ET key of t. Look at the book's CLOSED trades (exit already booked at the signal second) whose own signal key is K; take the first of them by entry time. If its net P&L after fees is < 0 (a loser, whatever the exit type: Stop, StateCut, EarlyCut/time-stop/structure exit all count), the lots of this signal are multiplied by 0.5 in trend_size, applied AFTER the live sizers and after C's equal-$ scaling: lots = max(1, floor(lots*0.5 + 0.5)). A winning (or no) first trade -> normal lots. No skip, no re-arming, applies to every later signal of that book-session (including the third, fourth ...). Stack caps and locks that clamp P7 are not touched (P7 is outside the rule); the day-done and lot-cap clamps for the other books see the already-halved lots. State carried: none beyond the trade list; resets with each new session key. In the live code this needs the per-book session ledger (first closed trade of the session and its sign), nothing else.

**B = U7 time stop on fresh entries.** Book U7 only. Context 'fresh' = chase_k <= 1.0 (side x (close - session first close)/ATR5 at the signal), at most the 2nd U7 entry of the session since the session start (n <= 2) and >= 30 min since the last U7 exit (P7_CONTEXT_DEFS, wb_ctx.Ctx). Rule: exactly 15.0 minutes (900 one-second rows) after the first fill row, if the open P&L at that second (mid, side x (mid - entry_px)) is < -10.0 points, exit the full position at market at the next row: mid - side*0.80 pts slip (engine); exit name EarlyCut. One check only (not a rolling condition); a trade that is at -10 or better at minute 15 is never touched by B. Interaction: B closes the trade, so for A it is a loser (a later U7 signal in the session gets half lots), and the post-cut blackout rules of the engine for EarlyCut exits apply as in the reference.

**C = U7 Keltner-mid structure stop (stop + equal-$ lots).** Book U7 only, all contexts. Level = Keltner mid = EMA20 of 5-min closes (struct_a3 kc) at the last completed bar before the signal minus 60 s; stop level = kc - 2.0 pts on the loss side (long: kc - 2; short: kc + 2); S = |entry - level| (stop distance, pts) must satisfy 0.5 <= distance-to-level < 60 else the rule is off for that trade (native 60-pt stop only), S clamped to 25..60. Dynamic level: the Keltner mid is re-read each second from the 5-min series (lagging the bar by 60 s) and the exit fires when side x (mid - entry) <= side x (kc_now - entry) - 2.0 (the stop follows the mid). Fill: modelled stop fill = min(stop level, current u) - 1.4 pts adverse (live native central), exit name EarlyCut. Lots: after the live sizers lots x 60/S (S clamped 25..60, so up to x2.4; round to nearest, min 1), so the $ risk at the structure stop equals the live 60-pt risk. Day caps/locks then apply to those lots. Interaction with B: B's check at minute 15 and C's stop run on the same trades; whichever fires first ends the trade. C changes the lots, which A then halves on a lost-first session.
