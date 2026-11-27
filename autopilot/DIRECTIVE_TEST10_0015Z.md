# Test 10: the exact engine does not confirm the two-sided level result. Find out which is right before anything else is built on levels (ordered by the relay under Josh's standing order)

Josh, 26 Nov 18:22Z, verbatim: "this is the order to you once the results come back in order a new test over the next 48 hours and keep reporting to me"

(relay) My design. Research only. Exact confirms the Test 5 primary (signs 4/4) but is far weaker than the quick screen on Test 8's two-sided level books (Asia 123 vs 378, NY AM -66 vs +507). Yet the Test 9 spec pages say the grid, the rebuilt bars and a print-by-print scan agree on every trade for the 24 stack books. Both cannot be right for the same books. This goes AHEAD of Q1 and behind nothing except rows already being served.

A. RECONCILE, BOOK BY BOOK. For every Test 8 held cell with exact rows landed: quick-screen vs exact weekly points over the held weeks, trades count both ways, and the difference split into causes: (1) different trades (entries present in one and not the other), (2) same entries, different exits, (3) fills/cost basis, (4) session window or flatten rule, (5) one-position blocking, (6) level file version (stale vs current), (7) bar builder (print-rule vs live-identical). Give the 10 worst books a trade-by-trade diff for one month each. Say plainly which side is closer to what a live NT8 strategy would do, and why.

B. WHICH BOOKS SURVIVE. Split the Test 8 held cells into AGREE (exact within 30% of quick over held weeks, same sign) and DISAGREE. Re-score the Test 8 primary on the AGREE books only, exact numbers, against the quick drift null: per session and summed, L3M/L6M first, by year, first half vs second half. Report how many books and which level types are in AGREE. This is a diagnostic, not a new rule.

C. EXACT DRIFT NULL, SMALL. 20 draws (not 200) on the exact engine for the Test 8 held cells of Asia and NY AM only; post the count and start if under 15 h of fleet. Same for the Test 5 primary's Asia held cells if under 15 h more.

D. LEVEL FILES. Finish verifying the level files (the unfinished fleet re-run): list each level module as VERIFIED CURRENT / STALE-REBUILT / STALE-DROPPED, and say whether any Test 5, 6, 8 conclusion changes on verified-only data.

E. HOUSEKEEPING THAT BLOCKS RESULTS: a scorer for Test 6 exact and for Part C rows (4,736 done, unscored); Q2 re-queued with the safe script; every agent on queue_rows_safe.py. Report done or not.

Page TEST10_EXACT_VS_QUICK_LEVELS.md, answer first. Post a LEAD TO JOSH line with the time estimate.
