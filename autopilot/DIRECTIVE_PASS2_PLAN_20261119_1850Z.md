# ORDER 20261119_1850Z - PASS 2 ("best tech on the best books"): prepare NOW, start the minute the bar x trigger first looks finish

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

Josh (18:42Z): "yes draft it to start the minute the broad search for bar/trigger is done ... this is very encouraging - we are getting good results that are better or close to current live books that have many layers on top of them - best testing method we have done so far"

Context: SEARCH_COVERAGE.md shows the search varies bar, trigger, fixed bracket and side only. Pass 2 adds the components that are NOT varied today, on the best own-merit books. It must not slow the first looks: until the Asia and NY AM first looks are done, pass 2 gets BUILDERS ONLY (code, hooks, identity tests, pre-registration, cost estimate), no engine slots beyond small identity runs. When a session's first looks finish, its freed first-look share goes to pass 2 for that session automatically (Asia first, then NY AM); follow-ups of ranked books keep their 30%.

## A. Which books
Top own-merit books per session from BEST_BOOKS_*.csv, distinct streams, in rank order, no cap (start with the top 50 per session, keep going down the list). Live books are ordinary rows and may enter on the same terms.

## B. Components to add (each is a "column" of settings on a book)
1. FILTERS / CONFLUENCE on top of the trigger (the generic combiner that was never built): entry = trigger AND k-of-N conditions, any k, any N. Condition families: (a) level proximity / reaction: supply-demand zones, session levels, prior day / week H-L, VWAP and bands, volume-profile nodes and value area, pivots, round numbers; (b) higher-timeframe agreement (trend of a larger bar of the SAME bar family; never a time-bar indicator transplanted onto an alt bar); (c) momentum / state: squeeze, MACD-type, CCI (Josh's manual set), plus the grid's own momentum modules; (d) tape / volume state; (e) order-book state; (f) cross-market agreement (ES, RTY, megacaps, TICK). No limit on how many conditions line up.
2. MARKET-TYPE GATE: trend vs range (efficiency ratio, ADX-type, squeeze, range vs its own median): gate entries on / off, choose side by state, and let a session switch between a trend book and a range book by state.
3. TIME-OF-DAY windows inside the session (30-minute blocks on / off; day-of-week).
4. ENTRY METHOD: market on signal vs limit / dip entry vs split entry vs order-book-confirmed entry.
5. EXITS: all 68 recipes / 7 families in the exact engine on every pass-2 book (not only a screen pick), once W-XB1 / W-XB2 pass identity.
6. IN-TRADE MANAGEMENT: early loss cut, early profit take / lock, no-progress exit; RE-ENTRY: cooldown after a loss, no re-chasing a failed idea.
7. SIZER: efficiency-ratio trend sizer and a signal-quality sizer (lots up / down by state), judged at equal average risk.

## C. Method (Josh's standing rules; do not reinterpret)
- Per-component studies are only the SCREEN: for each book and component, score every setting on the fast screen, keep the top few settings per component (state the number; no component is dropped: a weak-but-positive best setting is carried with its evidence).
- Every filter-type result must beat a MATCHED RANDOM-SKIP null with the same number of trades kept (the gain must not come just from taking fewer trades), and must not push the book below a stated minimum trade count per week (propose it per session).
- The VERDICT is a JOINT stage in the exact engine (production driver): all components varied together per book around the screen's top settings, drawdown first (own ulcer, max DD, worst week), then dollars; L6M pick with L3M beside; prior years "not a disaster" (15-30% amber, >30% red vs the book's own recent level); persistence >= 0.58; 30 date-shift controls on the final setting per book; 2-week roll of the fitted settings walked forward through history.
- Then the stack is built per session from EMPTY with these upgraded books (W-COMBO forward selection, joint refit of account-level rules), and only then compared with today's D7.
- Bar rule: indicators native to the bar type; no 1-minute bars as a deliverable in NY or London.
- Label everything with the standing labels; "none" / "off" rows are reference only.

## D. Prepare NOW (builders, no engine slots)
1. The generic combiner on the grid side (any trigger x k-of-N conditions) with the random-skip null built in; condition library from the existing level / momentum / tape / book / cross-market feature code.
2. Engine hooks for: entry filter flags per event, regime gate, time windows, entry methods (limit / dip / split / book-confirmed), in-trade cut / take, re-entry cooldown, sizer: each with an identity test (inert hook == plain book trade for trade; then active hook vs the screen walker), on the production driver, and each added to the fast-path templates before it is used at scale.
3. PREREG_PASS2.md (settings grids, null, gates, minimum trade counts) with its hash in DECISIONS.md.
4. A cost table: set-months per book for the screen-to-joint path, and the dates for top 50 / 100 / 200 per session at the measured fleet rate.
5. autopilot/PASS2_PLAN.md (plain words) and a status line every hour; say at once if any part of this cannot be built by the time the Asia first looks finish (~23:20Z) and what would start first instead.

## E. Small additions to the running work (report tweaks, no engine time)
- BEST_BOOKS tables: add a plain "what it is" column per book (bar type and size, trigger family and key settings, side, bracket) and a ranking by L3M beside L6M.
- NY AM list shrank from 9,081 to 6,493 cells ("2,588 old-seed-only cells never built"): say whether those are duplicates / superseded or untested books. If untested and not duplicates, they stay in the search (no cap).

One LEAD NOTE: plan accepted, who builds what, what will be ready when the Asia first looks finish.
