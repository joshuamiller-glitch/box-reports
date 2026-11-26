# Rotation test 2: qualify on history first, pick families, switch on by recent results (order from Josh, relayed)

Josh, 26 Nov 17:06Z, verbatim: "order another test you think will pass with all servers for rotation of some kind"
Josh, 26 Nov 17:09Z, on the note below (shown to him in full): "post this yourself now"

(relay) The note he approved, body word for word:

New rotation test, all cores on all servers after stage B's sets are queued. Quick screen first on the whole stored candidate set, then exact re-score of the picks, same as before.

ROTATION TEST 2: qualify on history first, pick families, switch on by recent results.

At each date, using ONLY data before that date:
1. QUALIFY: a cell is eligible only if (a) it has at least 30 trades to date, (b) it was profitable in every fully-past calendar half-year, and (c) at least half of the cells in its own family were profitable over all history to date.
2. ONE PICK PER FAMILY: score each family by the median of its eligible cells; the pick is that family's median cell.
3. SCORE = income per unit of drawdown, as a blend of all history to date and the trailing window. Blend weights to test: 100% history, 50/50, 100% trailing. Trailing window: 3 months and 4 months.
4. BASKET: top 5, 8 and 12 families per session. Refit every 1, 2 and 4 weeks.
5. ON/OFF: run each basket two ways: every book always on; and a book trades the next period only if its own trailing 3-month result is above zero.

That is 3 blends x 2 windows x 3 basket sizes x 3 refits x 2 on/off = 108 versions per session. Do not add versions.

COMPARE AGAINST (no hindsight): zero; all eligible families held equal weight with no ranking; and the 100%-history version (does recency add anything).

REPORT, page ROTATION_TEST_2.md, answer first: per session and four sessions summed, out-of-sample Oct 2023 to Oct 2026, recent 6 and 3 months first, then by year: income per lot per week, max drawdown, worst week, share of periods beating the equal-weight basket, book turnover per refit, how many eligible families exist at each date, and how many different books the last 6 months would have needed. Apply the best-of-rows luck penalty over the 108 versions. Say plainly per session: PASS or FAIL against zero and against the equal-weight basket.

Then exact re-score of the picked books for the best version per session and the equal-weight basket. Post a LEAD TO JOSH line with the time estimate before starting.
