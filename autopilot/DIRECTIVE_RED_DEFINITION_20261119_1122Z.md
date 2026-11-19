# ORDER 20261119_1122Z - what "RED prior year" means on ENGINE rows (one definition, used everywhere)

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

The 11:09Z note says "engine prior years: REPLACE vs A7 rows show 2025 RED for every beater". Say which rule produced that. There are two different questions and they must not be mixed:

A) SCREEN rule (bare stream, standing rule): prior-year weekly R more than 30% worse than the cell's own L6M weekly R = RED. As you noted, the L6M is the selection window, so nearly every selected cell is RED by it. On the screen this only ORDERS the queue. It does not decide D8.

B) ENGINE rule for D8 (this is the one in the D8 inclusion rule "no red prior year", my reading of Josh's "prior years only need to be not a disaster"): compare the STACK WITH THE NEW BOOK (REPLACE row) against TODAY'S STACK in the same prior year (2023, 2024, 2025 each):
- drawdown first: stack ulcer (and max DD, worst week) with the new book vs today's stack in that year. More than 30% worse = RED; 15-30% worse = AMBER; otherwise GREEN.
- dollars: mean $/week with the new book vs today's stack in that year: more than 30% lower = RED; 15-30% lower = AMBER.
A candidate with no RED year under B passes the prior-year gate. Persistence > 0.60 is likewise measured on the engine REPLACE-minus-today weekly difference where available (share of 2-week windows where the new stack is not worse), with the bare-stream persistence shown beside it.

Do now:
1. For every Asia and NY AM beater with engine prior years landed, post the B table: per year, d ulcer %, d max DD %, d worst week %, d $/wk % vs today's stack, colour, and the overall verdict. Put it on NEW_BOOK_BEATS_LIVE_ASIA.md / _NYAM.md next to the three-row table, with the A (screen) colours in a separate, clearly labelled column.
2. State the sign convention at the top of every table (e.g. "d worst week +1,631 = worst week is $1,631 LESS bad than today's stack").
3. W-LAYERS gate tiers and D8_SPEC_STATUS use rule B once engine prior years exist for a cell; until then the tier is "pending", not "fail".
4. Fast path: ASI RU7, ADDLO, NYL layer-fit and EXE kinds are still missing from FAST_KINDS; the 11:09Z share was 0% on Frankfurt, Singapore and Dallas. Post the share again after the 11:09Z / 11:15Z additions take effect.

One LEAD NOTE with the B table for the beaters that have prior years.
