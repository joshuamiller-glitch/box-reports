# Test 4: how strict must qualification be? (no picking) + scope for Part C (ordered by the relay under Josh's standing order)

Josh, 26 Nov 18:22Z, verbatim: "this is the order to you once the results come back in order a new test over the next 48 hours and keep reporting to me"

(relay) Everything below is my design, not Josh's words. Research only. Test 3 said: picking hurts (S below random in Asia and NY AM), the QUALIFICATION carries whatever edge exists. Table T2 shows the live books sit far above the qualified pool and have 600 to 3,800 trades each, while the pool was admitted at 30 or 60. So the next question is one thing only: does a STRICTER qualification, with no picking at all, earn out of sample?

TEST 4, quick screen, whole stored set, each session, same out-of-sample span and same no-look-ahead rule (only data before each date):
- Qualify a CELL at a date if ALL hold: (1) trades to date >= N, N = 100, 300, 1000; (2) t-statistic of its weekly P&L to date >= T, T = 2, 3, 4; (3) profitable in at least 75% of fully-past half-years; (4) family share >= 70% (Test 3's definition).
- One cell per BOOK (same bar type and size, module, variant, params, side: the Part B group), the lower-median qualified bracket. Then at most one book per test-2 family: the one with the most trades.
- HOLD ALL of them, equal weight. No ranking, no K, no spread rule. Re-qualify every 13 weeks; a held book leaves only when it fails.
- 3 x 3 = 9 versions per session. Do not add versions.
REPORT (page TEST4_STRICT_QUALIFICATION.md, answer first, L3M and L6M first, then all and by year): $/lot/wk, max DD and worst week per lot, number of books held at each date, turnover; best-of-9 luck penalty and reality-check p vs zero; PASS = after penalty above zero with p <= 0.10, per session and summed. Show the 3 x 3 grid so it is visible whether results improve steadily as N and T rise (a steady slope matters more than the single best cell).
Also T2 again for the 20 live books under each of the 9 rules: first date qualified and result after.
One extra row per session, marked REFERENCE: the same rule with requirement (2) measured on the trailing 52 weeks only instead of all history.
EXACT: the best version's held cells per session, bare R0, held periods, queued after Test 3's exact rows; include in the quick-vs-exact calibration.

PART C (fittings only), scope decided so the fleet is not tied up 90 h on a basket that failed:
- Do NOT run Part C on the Test 3 S baskets.
- Run it on the 20 LIVE books only (about 20 x 8 x 42 = 6.7k set-months minus sets that already exist). Menu for now = your 8 exit settings + bare. Note for the record: by "fittings" Josh means the per-book Trade Health and layer settings (the JT menus); if a dated JT menu per book can be built from data before each date, post its set-month count as a LEAD NOTE and wait; do not queue it.
- Label it plainly: the 20 books were chosen with hindsight, so Part C answers "does re-fitting beat holding one fit or bare on these books", not whether the books are good.

ORDER OF WORK: stage B (test 1) and test 2 exact first; Test 3 exact rows; Test 4 quick screen now on server C; Part C live-books rows and Test 4 exact rows on free cores. Backlog stays paused. No server released, resized or wiped. Post a LEAD TO JOSH line with the time estimate.
