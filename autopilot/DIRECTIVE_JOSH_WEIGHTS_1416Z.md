# Order 1416Z Sat Nov 21 — Josh approved two new tests; the design text is written by the relay (Claude)

## Josh's words (14:11Z to 14:13Z, verbatim)
- "isn't option A scaled up greatly the best option with another book in the mix scaled down?"
- "why are we trying to add books at equal weights?"
- "does a weight search add more time or easy?"
- "yes both"  (his answer to the relay's two proposals below)

What he said yes to, as the relay put it to him: (1) "A weight search on the current options: size each book in A, B and C to its own long-run drawdown, not only the recent one, then find the best mix; judged at equal worst-prior-year drawdown, with walk-forward and prior years shown; uses daily results the box already has." (2) "A weighted add rule in the loop: a new book is tried at several sizes before it is rejected."

Everything below is the RELAY'S READING of how to run that. Where a detail is my choice it is marked (relay). If a detail is wrong for the engine, say so and propose the nearest correct thing; do not silently change it. Research only. Nothing on the execution server or any live chart.

## PART 1 — weights for the books already in the options (do this FIRST; no engine slots for the search)
Scope: Asia option A book (L385f4f2e.J502), option B (L7c368a4f + La010c3eb _CANF), option C (L7c368a4f + L578701ed + L385f4f2e.J502); also the union of those four books as one free mix; and the NY AM five-book final (L7cc56d99, L488784d8, B7bfd33b7, B6f77f23d, L6547965c).
1. From the landed book-alone daily series (42 months, base 1 lot), search weights per book on the grid 0, 0.25, 0.5, 1, 1.5, 2, 3, 4 (relay). Weight 0 = book dropped. State plainly that this is a SUM of book-alone series (approximation: no stack interaction, account layers per book).
2. Selection (Josh's standing method): pick on RECENT data (L6M, with L3M beside), drawdown first. Compare mixes AT EQUAL RISK where risk = the mix's WORST PRIOR-YEAR max drawdown (2023, 2024, 2025), not its L6M ulcer (relay: this is the point of Josh's question; a book whose prior-year drawdowns are 5-9x its L6M drawdown must be sized by the larger). Show beside it the same ranking at equal L6M ulcer so he can see both.
3. Report per scope ONE table: equal weights (reference row) and the top 5 mixes: weights; ulcer / max DD / worst week / $ per week for L6M, L3M, 2023, 2024, 2025, all scaled to the same worst-prior-year max drawdown as the equal-weight reference; own persistence (14-day blocks).
4. Gates = the fitted-setting gates Josh approved 18:10Z Nov 20 (weights are a fitted setting): walk-forward (trailing 182 days pick the weights, next 14 days judged, weighted mix beats equal weights in >= 58% of periods, drawdown-first as in the layer walk-forward); prior years inside the 15-30% "not a disaster" band versus equal weights at equal risk; best-of-many null >= 4/5 (the null must redo the weight search). 27/30 date-shift count shown, not a gate.
5. For the winning mix of each scope (and for equal weights if not already landed): ONE exact engine stack run at those weights (lots scaled to whole numbers, e.g. weights x4, relay) + its 30 controls, so the sum approximation is checked against the engine. Report sum vs engine side by side.
6. Bare D7 at the same drawdown beside every row, as usual (bare vs bare only).
Deliver: autopilot/WEIGHTS_ASIA.md and autopilot/WEIGHTS_NYAM.md + one MORNING.md line per scope. Target: first tables within about 1 hour.

## PART 2 — weighted add rule in the stack loops (behind part 1)
1. NEW loops beside the existing ones (do not overwrite the equal-weight finals; they stay as reference rows): asia-own-w, asia-stay-w, ny-own-w (relay: names). Same pool, same own-checks gates, same guards.
2. Change only this: when a candidate is tried, try it at sizes 0.25, 0.5, 1 and 2 relative to 1 lot (relay), and judge the best size; in the moves phase also allow re-sizing a member (same grid) as a move. The first book is chosen as today; then test whether scaling the stack's members changes the pick.
3. Risk basis for every comparison: report BOTH (a) today's basis and (b) equal worst-prior-year max drawdown; the loop's decision uses (b) for the "-w" loops (relay), and say so on every FINAL line.
4. FINAL lines carry the weights, the full window table, persistence, controls (30), and the equal-weight final of the same loop beside it.
5. Any book entering a weighted FINAL that is not fully fitted gets its fits through the pool watchers as usual.
6. Before running: W-COMBO posts the plan in 5 lines (what changes in code, set-months expected, finish time) and the lead checks it against this order. Unit test the changed code on pool 35 with all sizes fixed at 1: it must reproduce today's four Asia finals exactly; post that check.

## Order of work
Part 1 first. Part 2 behind it. Neither may delay the answers already owed to Josh (orders 1409Z full-Asia-search time, 1414Z daily stops). The rest of the queue order is unchanged; Josh has not yet decided whether the Asia search goes ahead of NY AM.
