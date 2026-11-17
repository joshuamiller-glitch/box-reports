RESEARCH ORDER (relay, 11-17 15:09Z): DAY-DONE addendum: CONDITIONAL RESUME. User question: "trading is halted, but can we resume if certain conditions are met?" Add to W-DD (order 1331Z); these rows go to Table 4 of the deliverables page. Put the L6M + HOLD months of these cells in _dd/first.txt so they have numbers with the other DAY-DONE variants.

After a DAY-DONE trip (live form: >= 22 closes and day <= -4,200 live dollars), resume entries before the 18:00 ET reset when a condition is met. Test each alone and the best two together, on JL3 (JL2 for comparison), 43 months, ulcer primary, 30 persistent random-day-halt controls matched on halted share, walk-forward pick:

 R1 SHADOW RECOVERY: keep computing the skipped signals as shadow trades (same brackets, cuts, lots). Resume when the last N shadow trades net positive (N 2, 3, 4) or shadow P&L since the halt >= +X (X 1,000 / 2,000 / 3,000 base). This is "paper-trade until the system is working again".
 R2 NEW SESSION + HEALTH: resume at the next session open (02:00, 09:30, 12:00 ET) only if a health check passes at that open: atr_rel below 1.3 (and a 1.6 variant), OR the first shadow trade of the new session is a winner.
 R3 DAY P&L RECOVERY: resume when realised + open day P&L climbs back above the trip level by a margin (trip +1,000 / +2,000 / +3,000 live). Last night the day went from -9,660 at the trip to -5,450 as open winners closed.
 R4 PROBATION SIZE: resume at the next session at half size; back to full size after 2 winners; halt again for the day after 2 more losers.
 R5 SIDE-SPECIFIC: after the trip only the side that produced the losses stays halted; the other side may trade (pairs with the same-side-loser rule in part E).
 R6 BOOK-SPECIFIC: books that are net positive on the day keep trading (per-book version f in 1331Z) plus R4 for the halted books at the next session.

Also settle two facts and state them on the page: (i) LATCH: W-DD found the engine gate is not latched (re-evaluated at each entry attempt) while live may latch; read DS7 v2.0 (V9Gate, the DAY-DONE block) and say exactly which the live code does, and run both forms; (ii) what happened in the SKIPPED sessions historically: for every tripped day in 43 months, the shadow P&L of the sessions that were skipped afterwards (by session: London, NY AM, NY PM), mean, share positive, and worst: this is the direct measure of what the halt costs or saves.

Deliver: the best resume rule with its numbers and label, the exact condition in plain words, and what it needs in DS7 (the shadow-trade bookkeeping exists for Shadow modes; say what is missing). Research only.
