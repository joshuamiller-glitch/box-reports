# 1722Z — PLAN CHANGE: NO GLOBEX DEADLINE. Full search first, then controls, then gates, then D8 (Josh's order of work)

From: Josh's chat assistant (relay). Research orders only; no spend; nothing here touches the execution server or a live chart.

Josh: "shouldn't we do all testing for all sessions first, huge test - no Globex deadline - then run the 30 controls - and then add the gates to see what helps/hurts - then re-build for D8?" Yes. This REPLACES the timed funnel of 1333Z / 1415Z / 1450Z (their 19:00Z / 21:00Z / 23:00Z deadlines are cancelled; nothing is to be cut short to hit a clock; no build tonight). What has landed stays valid and stays on its pages.

PHASE 1 - FINISH THE WHOLE SEARCH (all four sessions; this is now the main use of both machines):
1a. Pass 1 to completion: every trigger module x every bar row x sides x brackets (about 77,000 jobs parked) - give it the cores back NOW. State jobs/hour and the ETA in MORNING.md every hour; if a module or bar row cannot run (missing feature store etc.) list it, do not skip it silently.
1b. Exit families (68 recipes) on every cell that shows life, and the level / supply-demand modules by zone definition and entry type, as already ordered.
1c. SCORE EVERY CELL TWO WAYS at screen level: (i) bare; (ii) under the ACCOUNT rules a book inside D7 cannot avoid, first of all DAY-DONE (no new entries once the live stack has >= 22 closes in the trading day and the day is <= -$4,200 live) using the live stack's own day-state from JL3, plus one-position. Today's engine rows showed this flips results both ways (WP10 bare +$5,101 -> +$42,116 in the engine; XA3 bare +$4,511 -> +$57,241; NP1 bare +$23,850 -> -$30,526), so a bare-only ranking buries real candidates. Build the JL3 day-state table once (per date: time DAY-DONE trips, if it does) and apply it as a mask in the grid scorer - cheap, no engine runs. Re-rank everything already scored the same way first (today).
1d. Rank per session on the standing rule (pick on the trailing 6 months, 3 months beside; prior years not a disaster: amber 15-30% worse, red > 30%; persistence; rolling pick -> next 2 weeks), on EQUAL RISK (wide brackets are fine), both rankings (bare, account-rules) side by side.

PHASE 2 - PROVE THE SHORTLIST IS NOT LUCK (after phase 1 for a session, session by session as each completes):
2a. 30 random-entry controls with the SAME bracket per shortlisted cell, and 30 date-shift controls on the engine for the engine candidates.
2b. The selection-corrected test: the best-pick null for the whole session grid (random-entry versions of the SAME search, >= 20 draws) so "best of millions" is paid for; and the rolling-procedure result out of sample.
2c. Trust audit (brute force, truncation cuts, fills) and look-ahead gate on every shortlisted cell.

PHASE 3 - GATES AND LAYERS, ONE AT A TIME THEN JOINTLY (exact engine; identity first):
3a. Per surviving candidate, a table "what helps / what hurts": bare-in-engine -> + each account rule alone (DAY-DONE, stack cap, day caps) -> + each layer alone (no-trade zones, context check, trade-health cuts on the loss side and locks / takes on the profit side, sizer, give-back lock) with the SETTING fitted to this book on the trailing 6 months -> then all jointly. Drawdown first. No layer inherited from K7/P7/M7 by default; every layer the book ends up with is its own best setting ("off" is a reference row only).
3b. Stack questions per session: replace vs add vs mixed against the live books, risk-matched; account-rule settings that fit a stack with wider-stop books (day cap, close count).
3c. Joint stage across sessions for the final set (new books + kept live books + all layers together), prior years and 2-week roll, 30 controls.

PHASE 4 - D8 SPEC: one build-spec page for the whole new stack (every book: bar construction, trigger, order, session window, its own layers and settings, example trades; account rules; what is native NT8 and what needs custom code). The chat assistant codes D8 from that page only. Label per book: BUILD-READY only after phases 2 and 3.

KEEP RUNNING IN PARALLEL (they are cheap and already in flight; do not stop them, do not rush them): the NY leads WP10 (NY PM money flow, keep K7 + add) and XA3 (NY AM VWAP retest on 5000-tick) to the FULL standard (30 controls, selection-corrected null, own fitted layers, prior years, swap vs add); the London replacement programme (K7 / M7 are the targets); the near-target K7 lock controls; ORB fade controls to 30.

REPORTING: one page autopilot/SEARCH_STATUS.md, refreshed hourly, plain words: phase 1 % done per session and ETA; what is in phase 2 / 3; the current top 10 per session under both rankings; anything blocked. Reply in MORNING.md now: accepted, pass-1 jobs/hour with the cores returned, and the ETA for phase 1 per session.
