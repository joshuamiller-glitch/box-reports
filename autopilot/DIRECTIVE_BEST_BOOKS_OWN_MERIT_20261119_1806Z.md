# ORDER 20261119_1806Z - Josh: the goal is the BEST BOOKS, judged on their own merit; D7 is only the final sanity check

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

Josh's words (18:01Z): "there seems to be some hyper focus on D7 - and i'm fine with the comparison to make sure it's 'better' but the whole point of this is to find better books from a poor search last time and trying to artificially stack things on top of each other and freeze them - this is geared towards finding the best tech and books to run this algo on"

Coordinator's reading: the pipeline has drifted into "does this cell beat A7 / K7 when swapped into today's frozen stack". That makes today's stack the judge of every book. Josh wants the search to find the best books (and bar types / triggers / exits) in their own right, then build the best stack from them, and only then check that the result is better than D7. The live books are not a base to protect; they are just other candidates.

First looks keep running exactly as queued (their landed trades are the data for everything below). What changes is how books are RANKED, which books get follow-ups, and how the stack is built.

## 1. OWN-MERIT SCORECARD for every cell with a landed first look (no new engine runs)
From the landed set-months, take the new book's OWN trades (its book tag) and score the book by itself, per session, at 1 lot: L6M and L3M $/week, own ulcer, own max drawdown, worst week, trades/week, win rate, average win / loss; persistence of the book's own 2-week results (>= 0.58); prior years 2023 / 2024 / 2025 "not a disaster" against the book's own recent level per Josh's standing 15-30% rule, shown beside the absolute numbers; the calibration / luck numbers for its family. Rank all cells per session by drawdown-adjusted return (state the formula: e.g. $/week divided by own ulcer, with $/week and ulcer shown), recent windows first. Put the live books (A7, K7, P7, H7, U7, M7, O7 per session) IN THE SAME TABLE scored the same way from the baseline's own trades, as ordinary rows.
Note the caveat honestly: a book's trades inside a stack are affected a little by account layers (day halt, stack cuts); say how much (compare own-stream totals of the same book in two different stacks).
Deliver: autopilot/BEST_BOOKS_ASIA.md and BEST_BOOKS_NYAM.md, top 50 per session + where each live book ranks, refreshed every 30 min as first looks land.

## 2. Follow-ups go to the BEST BOOKS, not to "beats A7 / K7 in today's stack"
The 30% follow-up stream (prior years, 30 date-shift controls, exit run, layers) now takes cells in own-merit rank order per session (top of BEST_BOOKS first; distinct streams only; no cap, just order). The strict "beats the live book in today's stack" test is no longer the gate for follow-ups; keep computing it as a column.
First-look form: keep the queued REPLACE-vs-A7 / vs-K7 first looks (they carry the book's own trades). Do NOT spend first-look or a2 engine time on "the same cell vs each other live book" (vs K7 / P7 / H7 / U7 rows) any more: that question belongs to the stack-building step. Park those lines; say how many set-months that frees.

## 3. Build the best stack from the best books (replaces "one swap at a time into D7")
Extend the combination tool: candidates = top own-merit books per session that survive prior years + controls + exit run, PLUS the live books as equal candidates. Build stacks by forward selection from an EMPTY stack per session (add the book that most improves the session stack: drawdown first, then dollars; stop when adding hurts), with the account layers ON and refitted jointly on the final stacks (layers are fitted to the new stack, not inherited). Use the fast scorer to rank and the exact engine (production driver) for every verdict. No fixed number of slots: the number of books per session is an output. Report for each session the best stack, the next best few, and which live books (if any) earned a place.

## 4. D7 comparison = the last line
Only at the end: best new stack vs today's D7 stack (L6M, L3M, each prior year, drawdown first), same lots basis, to confirm it is better. That is the only place D7 is the benchmark.

## 5. Post now
(a) the first BEST_BOOKS tables from what has landed (about 1,130 Asia and ~300 NY AM first looks); (b) set-months freed by parking the other-book rows; (c) how the stage-1 date changes; (d) anything in this order that conflicts with a standing rule, stated plainly (do not silently reinterpret).

One LEAD NOTE answering 1-5.
