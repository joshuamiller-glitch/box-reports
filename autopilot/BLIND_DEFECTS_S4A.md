# BLIND_DEFECTS_S4A - live D7 week vs the blind-week rules: locks, halts, policy cuts, U7 blackout, split / resting add, blocks (S4a, 2026-11-06)
Research only, nothing live, no PASS claim. Seal: DS3_BLIND_WEEK.md sha256 1ffc16d5... (DECISIONS.md 2026-11-06T00:50:57Z); live file data/live/StratTrades_DS7_<acct>.csv sha256 d918fee4e83e18521538aa37728c563036ca3597f8c6759b9610d1bf14565d00 (187 trades, DECISIONS.md 2026-11-06T15:59Z) read AFTER the seal. Sealed files untouched; every counterfactual below is a variant on copies. Code l2vast/ds3/code/blind/blind_defects.py (modes scan, epath2, misc, split, locksall, rank), lock_rules.py unchanged; NQ 1-s path = /mnt/l2/l2vast/tables/NQ/1s/2026-11__ext_20261101_20261105.parquet (last-trade price per second, NQZ6). Live times are ET wall clock; live books are the engine's X7 = X6 (P7 = P6, K7 = K6, A7 = A6, H7 = H6, U7 = U6, M7 = M6).

## 0. Answers in one block
1. **Halts.** P7's BookLock is **Wed 11-04 07:25:04** (5-lot short entered 07:25:00, flattened 4 s later, -$90); P7 traded straight through Wed 01:44 (7-lot long entered 01:31:01, target 02:11:45; entries 02:45, 03:36, 05:02, 06:45) and re-entered at **18:48:00** (first entry after the 18:00 roll). The Wed 01:44 lock in the directive is **A7's, on Monday**: A7 BookLock Mon 11-02 01:44:15 (1-lot long entered Sun 22:13; next A7 entry Tue 00:36). K7's BookLock is **Thu 11-05 04:35:14** (1-lot short entered 04:27:00), no K7 entry afterwards to the end of the file (11:05). So the directive's "P7 halted Wed 01:44 -> 18:00" should read "A7 Mon 01:44; P7 Wed 07:25 -> 18:00".
2. **My lock rules on the live trades** (sealed lock_rules.py, R = planned lots x 60 pt x $20 = P 8,400 / K 2,400 / A 1,200 / M 2,400 / H 4,800 / U 4,800, 1-s path): A7 reproduced to 2 s (fires 01:44:13, live 01:44:15); K7 Thursday fires 04:33:12, 2 min before live 04:35:14 (e/pk .50, borderline); **K7 Monday fires a lock the live book did not have** (01:12:57, e/pk .49 at 3 lots open; live kept trading K7: 10 trades, +$7,035 live; variant delta -$6.3k); **P7 never fires** at R = 8,400 (peak e $16,076 vs arm 2R = $16,800, 4.3% short) while live locked Wed 07:25. M7, H7, U7: no lock either way; entry caps (+5R / -2R realised) never bind in the live week under the rules (0 skips), consistent with live. Verdict: the rules reproduce 1 of 3 live BookLocks exactly, 1 within 2 min (with an extra Monday fire), 1 not (see section 2 for why).
3. **Policy cuts.** No live PolicyCut before the loss line starts (Mon 08:20; earliest 08:36:46); the two PolicyTakes fall in the take-file window (Mon 08:05:09 X5 +$1,765, 08:05:20 M7 +$840). Live 39 PolicyCut (-$66,880) + 53 ThL2Cut (-$73,470) = **92 cuts, -$140,350** vs engine 85 'thl2_cut', **-$139,546** (the engine does not label policy cuts separately): the cut layer is worth **-$804** of the gap, the smallest item. Adverse points at the cut are the same (PolicyCut mean 36.0 / median 34.0 pt, ThL2Cut 35.3 / 34.2), median hold 489 s vs 545 s.
4. **U7 30-min same-side blackout:** live U7 had 3 ThL2Cuts (Mon 03:01:49 short 6 lots -$3,890; Thu 02:16:10 long 2 -$1,320; Thu 08:04:52 short 4 -$2,550) and **no same-side U7 entry within 30 min after any**; no contradiction, but with 6 U7 trades the rule is not testable (the engine's blocked-signal list would be needed).
5. **70/30 split and resting add:** nt8 log (Thu 00:09 -> 16:42 only): 67 Entry fills, 9 add-like fills (>= 20 s after the first fill of the trade; median delay 92 s; P7 6, U7 2, K7 1; e.g. P7 short Thu 00:14: five 1-lot fills at +0.3 / 2.9 / 8.0 / 11.0 / 16.1 s, then a 2-lot add at +123 s, 8.4 pt worse), and **0 of 67 fills after the covering trade's exit**: the add is cancelled on every exit as modelled. Slices are about 3 s apart per lot (engine: 1 lot per 2 s): a second-order fill-cost difference.
6. **Blocks:** live entries inside 09:00-09:59 / 18:00-18:04 / 15:00-17:59 ET: 0 for the six core books; 3 for O7 (09:41-09:43, +$660; O7 is the NY-open book and outside the core-book blocks); engine entries in the windows: 0. No block defect.
7. **$ rank (live minus engine = +$69,216: live +$104,095, engine +$34,879):** see section 6; the whole gap is the TARGET class (+$54,951) and STOPS (+$11,063), concentrated in **P7 targets (+$77,978)**; locks +$2,089, trail / take +$1,917, cuts -$804. None of the rules in my slice (locks, policy cuts, split, blocks) explains more than 3% of the gap.

## 1. Live BookLock exits and what the rules do (R = planned lots x $1,200, per-second path)
| book | live BookLock (exit) | last trade entered before / first after | my rule fires (flatten) | R range that reproduces the live lock DAY (step scan) | note |
|--|--|--|--|--|--|
| A7 | Mon 11-02 01:44:15, 1 lot long, -$395 | entered Sun 22:13 / next entry Tue 00:36 | Mon 01:44:13 (01:44:14) | R 800-1,300 (planned 1,200) | exact |
| K7 | Thu 11-05 04:35:14, 1 lot short, -$855 | entered 04:27:00 / none to 11:05 | Thu 04:33:12 (04:33:13); ALSO Mon 01:12:57 | R 2,850-3,200 (planned 2,400) | Monday false positive at 2,400; fits R x 1.5 on the old-panel day |
| P7 | Wed 11-04 07:25:04, 5 lots short, -$90 | entered 07:25:00 / next entry 18:48:00 | none at 8,400; R 6,900-7,800 fires Wed 07:00:02 AND Tue 01:34:39 | no R reproduces the live lock day alone | live lock acts on the first entry after the trigger |
Why: (i) K7. With R = 2,400 on both days the Monday lock fires at e/pk 0.49 with pk $5,640; the live Monday day was not locked, which requires 2R > $5,640 (R > 2,820) on Monday and 2R <= $6,490 on Thursday (R <= 3,245). The sealed config's lock R is documented as 'multiplied by the running-max SizeMult of the day when > 1 (never under Q1-A)'; the Monday label day (Sun 18:00 -> Mon 18:00) ran the OLD PANEL / ER x0.5-x1.5 ladder (BLIND_WEEK_CONFIG_FREEZE.md), so R_Monday = 2,400 x 1.5 = 3,600 and R_Thursday = 2,400 reproduce both K7 days (Monday no fire; Thursday fires). This is a reading consistent with the numbers, not something the live file proves. (ii) P7. At the 07:00:02 ThL2Cut the book became flat with e = $6,921 < half of its $16,076 peak; per-second rules halt from there. Live did not: P7 re-entered at 07:25:00 and was flattened by BookLock 4 s later, the same pattern as A7 (flatten 2 s after the per-second trigger, position open) and K7 (14 s after a minute boundary), i.e. the live lock acts when it evaluates a book that has an open position, and does not block the next entry after the trigger. Cost: one 5-lot entry, -$90. (iii) the P7 arm shortfall ($724, 4.3%) is a mark-to-market basis difference (last-trade 1-s path vs NT8's) that no scan of R removes: R <= 8,000 would arm it but also fires Tue 01:34:39, which live did not. A 1-minute-close basis does not fix it either (K7 Thu 04:35:00 matches live within 14 s, A7 fires 01:45:00 = 45 s after live, P7 none).
Engine locks (sealed list): 4 = A6 Sun 20:59 -$450, K6 Mon 10:15 +$26, H6 Wed 01:13 -$2,001, A6 Thu 01:15 -$1,005 (-$3,429) vs live 3 = A7 / P7 / K7 (-$1,340): different books and times, because the engine's P / K paths differ; $ effect +$2,089 (live minus engine).

## 2. Variants run (counterfactual only; sealed files untouched; /mnt/l2/l2vast/ds3_blind_defects/locksall.pkl)
| variant | change vs the live P&L |
|--|--|
| my locks on the live trades, R = planned lots x 1,200 | A7 +$45, K7 **-$6,302** (Monday false positive cancels 10 trades worth +$7,035), P7 $0, M7 / H7 / U7 $0 |
| K7 Monday R x 1.5 (3,600), Thursday 2,400 | K7 Monday no fire, Thursday fire 04:33:12: delta about -$0.9k (the Thursday lock, live -$855 already) |
| entry caps +5R / -2R | 0 skips in all six books |

## 3. Policy cuts and takes (live vs engine)
| | live | engine (sealed) |
|--|--|--|
| cut exits | 92 = 39 PolicyCut + 53 ThL2Cut, -$140,350 | 85 'thl2_cut', -$139,546 |
| ThL2Trail / PolicyTake / 'other' | 2 trails +$1,045; 2 takes +$2,605 | 2 'other' +$1,733 |
| cuts by book (live / engine) | P 24 / 27, K 30 / 29, M 13 / 17, U 3 / 3, H 2 / 9, **A 14 / 0**, O 2, X 4 | |
| live PolicyCut before 08:20 Mon | 0 (earliest 08:36:46) | |
Reading: the loss-line policy fires at the same adverse distance as the panel cut (36.0 vs 35.3 pt), so it is not a second, tighter loss limiter; the engine's single 'thl2_cut' class reproduces the cut P&L within 0.6%. The one book where the cut count differs by a lot is A (live 14, engine 0 cuts, 12 target exits vs 7, A7 net -$1,415 vs engine +$9,067).

## 4. Ranking of the live - engine gap by $ (+$69,216)
By exit class:
| class | live n / $ | engine n / $ | delta $ |
|--|--|--|--|
| target | 86 / +245,410 | 84 / +190,459 | **+54,951** |
| stop | 2 / -3,275 | 7 / -14,338 | **+11,063** |
| lock | 3 / -1,340 | 4 / -3,429 | +2,089 |
| trail / take / other | 4 / +3,650 | 2 / +1,733 | +1,917 |
| cut (policy + panel) | 92 / -140,350 | 85 / -139,546 | -804 |
By book (delta $, largest first): **P7 +83,606** (targets +77,978, cuts +5,719; live 53 trades, 28 targets = 53% vs engine P6 43 trades, 37% targets, same lots per trade 4.7 vs 4.8; net per trade $1,623 vs $56), A7 -10,482 (cuts -9,925, targets -7,137, stops +5,015), H7 -10,036 (live took 3 trades, all Sun-Mon 11:24; engine H6 took 15 Asia trades Tue-Thu, +$8.8k: H7 shows no entry after Mon 11:24 in live), U7 -8,430 (live 6 trades -$1,755, engine 7 trades +$6,675), K7 +5,746, X3 +5,310, M7 +3,525, X5 -2,030, X4 +1,347, O7 +660.
Items in my slice: locks +$2,089, cuts -$804, blocks $0, split / add not separable from the target class, U7 -$8,430 (book-level, not caused by the blackout). **The P7 target hit rate (53% live vs 37% engine at the same lots) is the defect that matters: +$78k with no lock, policy, split or block explanation in the live file.** Also the 10-lot Sunday P7 trade (7 planned x 1.5 SizeHi of the old panel, +$12,010) exists live and not in the engine (max 7): the SizeHi rule is an APPROX in BLIND_WEEK_CONFIG_FREEZE.md; worth about +$3.6k.

## 5. What this says about my lock / block / policy / split config
* Lock rules: validated on live for the DAY and timing of A7 (2 s) and K7 Thursday (2 min); R must carry the SizeMult scaling on old-panel days (K7 Monday) - the sealed lock_rules.py has no such scaling, and a halt-at-trigger rule differs from the live implementation for a book that is flat when the condition becomes true (P7 Wed).
* Policy file windows: correct (take 08:05, loss line from 08:20); no policy-specific defect.
* U7 blackout, 70/30 split, add cancelled on exit, blocks: no contradiction in the live file; U7 not testable.
* Not mine but found: H7 absent after Mon 11:24 (engine +$8.8k), A7 cut regime (14 cuts), P7 target rate.

## 6. Corrections (appended, same day)
* Section 2, second row: the K7 variant with R x 1.5 on Monday and R = 2,400 on Thursday changes the live P&L by **+$178** (the Thursday lock alone; at R = 2,400 the Monday day alone is -$6,480, the Thursday day +$178; total -$6,302), not -$0.9k as written.
* Section 3, last sentence: A has 12 TARGET exits in the engine (18 trades, 67%) and 7 in live (23 trades, 30%); the sentence 'engine 0 cuts, 12 target exits vs 7' reads engine 12 vs live 7.
