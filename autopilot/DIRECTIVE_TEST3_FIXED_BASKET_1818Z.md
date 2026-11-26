# Test 3: a FIXED basket of qualified books, re-qualified slowly, picked for spread not for rank (order from Josh, relayed)

Josh, 26 Nov 18:13Z, verbatim: "order a new test keep all servers going based on your recommendations"

(relay) My recommendation to him after tests 1 and 2: no rotation; hold a fixed set of books that qualify on multi-year history, re-check the set on a slow schedule, size from out-of-sample results. Test 2 showed the only thing that earned out of sample was the QUALIFICATION itself (Asia equal-weight basket +108 $/lot/wk); ranking made it worse. This test asks whether a small, buildable basket chosen that way works. Research only. Quick screen first on the whole stored set, then exact engine; keep every server busy (order of work at the end).

AT EACH RE-QUALIFY DATE, using ONLY data before that date:
1. QUALIFY a cell: (a) trades to date >= 30 or >= 60; (b) profitable in every fully-past calendar half-year, or in at least three quarters of them; (c) at least 50% or at least 70% of the cells in its family profitable over all history to date. That is 2 x 2 x 2 = 8 qualification rules.
2. ONE CELL PER FAMILY: the family's median eligible cell (as in test 2).
3. CHOOSE K FAMILIES FOR SPREAD, NOT RANK: K = 8, 12, 20 per session (London 3, 5, 8). Method S: greedy lowest average weekly-P&L correlation with the families already chosen, starting from the family with the most trades. Reference method R: K families drawn at random from the qualified set (mean and 5-95% range of 200 draws). Reference method H: top K by all-history income per drawdown.
4. HOLD the basket unchanged until the next re-qualify date. Re-qualify every 13 weeks and every 26 weeks. A held book is dropped at a re-qualify date only if it no longer qualifies; empty slots are refilled by method S.
Versions per session: 8 rules x 3 K x 2 schedules x method S = 48, plus the R and H reference rows. Do not add versions.

COMPARE AGAINST (no hindsight): zero; all qualified families held equal weight.
PASS per session = method S after the best-of-48 luck penalty is above zero with reality-check p <= 0.10. Say PASS or FAIL per session and for the four summed.

REPORT, page TEST3_FIXED_BASKET.md, answer first, out-of-sample Oct 2023 to Oct 2026, recent 6 and 3 months first, then by year: income per lot per week, max drawdown, worst week, how many books ever held, books replaced per re-qualify date.
Then three practical tables:
 T1. THE BASKET TODAY: for the best rule per session, the K books the rule would hold as of the last data date (book id, trigger, bar type, bracket, family size, trades, income per lot per week by year). Mark which are already coded in D8Asia.cs (the relay will confirm) and which are near-twins of a live book.
 T2. THE 20 LIVE BOOKS under the same rules: for each, the first date it qualified under the best rule (or "never"), and its quick-screen result AFTER that date only. This is the honest forward record of what the file trades now.
 T3. SESSION SIZE: from the out-of-sample curve of the best basket per session (not from the last 6 months), income and max drawdown per lot, so session lots can be set from out-of-sample numbers.

EXACT ENGINE (this is what keeps the fleet busy): (i) the best version per session + the equal-weight basket, held periods only; (ii) every book in table T1, truly bare R0, all 41 months, 1 lot; (iii) the 20 live books bare R0 all 41 months where a full set does not already exist. Report quick screen against exact side by side for the same books and periods (calibration), because both rotation tests so far rest on a quick screen that was never calibrated.

ORDER OF WORK: 1) stage B of test 1 and the exact re-score of test 2 keep their place; 2) this test's quick screen on server C now; 3) this test's exact sets on every free core as soon as the lists exist. The paused candidate backlog stays paused. No server released, resized or wiped; if box 1's disk blocks anything, say so in a LEAD TO JOSH line (freeing space is his call only).
Post a LEAD TO JOSH line with the time estimate before starting.
