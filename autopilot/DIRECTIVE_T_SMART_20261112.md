# T-SMART (user, 2026-11-12 18:30Z) — untested families: loss mitigation, cost cutting, efficiency, discretionary moves. Base = JN05W2J and JN05W2 (v1.9 survivors); exact, one set per job, four windows + GAP + WF, scorecard a-e, acceptance, trend-week clause first; per book x session; thresholds in R at the cell's own lots AND at the user's lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75). Beside T-NEXT-FEATURES; fill the box to the knee. First rows DS3_SMART.md 2026-11-13 03:00Z, every 4 h.

A. LOSS MITIGATION
A1. CUT, THEN GET BACK IN (recoveries cut = 12/wk, $48k/wk): after a state cut or flat cut, re-enter the same side when price proves it — back through the entry price / back above the cut price + k pts / new session extreme in the trade direction / book state turns (pulled_against, delta with) — within 2-30 min, full / half lots, original target or re-based, one re-entry per cut. Versus never cutting and versus the cut alone. Report recoveries recaptured, double slip paid, second-loss rate.
A2. ONE POSITION, NOT SEVEN BOOKS: when 2+ books are open on the same side treat them as one trade — a stack-level adverse stop in R on the combined position (cut all / cut the weakest / cut the last-in), a stack-level floor once the combined position is up X R, and no new same-side book while the combined open loss is worse than -Y R.
A3. STRUCTURE STOPS WITH EQUAL-$ LOTS (EC_UKCS on U7 was +19.8 % DD cut, +$930/wk L6M): stop behind the last 3/5/15-min swing, Keltner mid, VWAP, session level +/- buffer, lots sized so $ risk = the live 60-pt risk (cap the lots); every book; with the state cut on and off.
A4. HEDGE INSTEAD OF EXIT: at the cut trigger, sell/buy MNQ or ES against 50-100 % of the position for N min rather than closing; lift the hedge on recovery or close both at the stop. Cost of the hedge vs the recoveries kept.
A5. STOP AND REVERSE: after a full stop or cut with strong opposite evidence (session extreme broken against the trade, other books signalling the other side) take the opposite side at half lots. And OPPOSITE-BOOK CONFLICT: K7 long while P7 short — take both (live) / skip second / net / close the older.
A6. FIRST TRADE SETS THE SESSION: a book's first trade of the session loses -> the rest of that session at half / fresh-only / skip; first trade wins -> normal. Per book x session.
A7. NEVER GREEN: a trade that has not been +k pts within N s/min of entry and is at -X -> out (location + time only; the forward placebo must be beaten).

B. COST CUTTING
B1. COST AUDIT per book x session x 30-min slot, live-calibrated: fees + measured slip per order type (slice market, 30 % add, stop join, market cut, target) as $ per trade and as % of gross edge; rank the slots where cost > edge. Deliver the table before any rule.
B2. ENTRY EXECUTION: passive limit at bid/ask or mid with 2-20 s timeout then market / skip; pullback entry of 1-8 ticks with timeout; slices 1 vs 4, interval 0.5-5 s; the 70/30 split 100/0 to 50/50; by spread and depth at the signal (wide spread or thin Asia book -> limit only). Fill rate and missed winners stated.
B3. EXIT EXECUTION: work the cut 1-5 s at mid before market; stop join 0/1/3/5 s; cut as a stop-limit; target one tick inside when queue ahead is large.
B4. MICRO CONTRACTS FOR GRANULARITY: express K7, M7, A7 in MNQ (10 per NQ) so partial exits, staggered targets/stops and 0.5x layers are not rounded away (K7 partials were inert at 2-4 lots). Fees and slip of MNQ vs NQ stated; re-run the best partial-lot cells from T-BUILD-ON and near-zone on MNQ sizing.
B5. DUPLICATE RISK: two books firing the same side within 60-300 s = one idea paid twice (fees, slip, correlated stop). Second book skip / half / only if the first is in profit.

C. EFFICIENCY
C1. DEAD SLOTS: per book x 30-min slot net expectancy and drawdown contribution over trailing 26 weeks, bi-weekly refit: slots x0 / x0.5; lunch, the last hour, the first 5 min after 18:00 and 09:30.
C2. RISK BUDGET REALLOCATION at constant total stack risk: move lots between books every 2 weeks by trailing Calmar / expectancy per $ of stop (caps per book), instead of fixed tables. Does the same total risk earn more with less drawdown?
C3. ADD TO WINNERS, NOT RE-ENTER: at +25/40/60 % of target add 1/3-1/2 with the whole stop to breakeven; versus the re-entry trades it replaces.
C4. TRADE COUNT: the minimum set of trades that keeps 90 % of net (which signals are fee-and-slip churn); max trades per book per session 2/3/4.

D. JOINT: top-3 per family -> coordinate descent + 1,000 random combos on JN05W2J, exact; minimal set; v1.9-style code-level spec with 5 worked rows for every survivor. Family null and forward placebo for every family; report how many pass by chance.
