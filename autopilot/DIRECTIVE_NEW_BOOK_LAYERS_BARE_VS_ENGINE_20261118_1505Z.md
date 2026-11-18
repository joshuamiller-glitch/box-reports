# 1505Z — NEW BOOKS: say exactly which layers touch them, and split "bare vs engine" (Josh: "if they beat without all these layers why are we forcing them on top?")

From: Josh's chat assistant (relay). Research orders only; no spend.

Josh's point is right in principle: the live layers (trade-health cuts, locks, context check, no-trade zones, flat-45 lines ...) were fitted to K7/P7/M7/U7/H7. They must NOT be forced onto a new book just because they exist. A new book gets its OWN layers, fitted to it, and only the account-level rules are unavoidable. Put this on NEW_BOOK_ENGINE.md (top of the page, plain words) and into the build specs:

1. STATE THE FACTS for the NYE / NYW / London sets: which rules act on the NEW book's own trades in these runs (list each: session window, own bracket, own day cap 4,800 / 12,000, flat at session end, anything else: no-trade zones? context check? stack cap? ER sizer? trade-health policy lines? give-back lock?), and which act only at ACCOUNT level (DAY-DONE 22 closes and day <= -4,200, stack cap, daily caps) where the new book and the live books affect each other.

2. BRIDGE TABLE per cell and window (L6M, L3M): (a) bare screen P&L of the cell on the same dates, same bracket, 1 lot; (b) the new book's OWN P&L inside the engine run; (c) the change in the OTHER books' P&L caused by the new book (day ended early by DAY-DONE or caps, entries blocked by the stack cap, etc.); (d) number of new-book entries blocked and exits forced by each rule. So Josh can see whether a weak engine row is the trigger itself being weak in that window, or a layer / account rule doing it.

3. THREE VARIANTS per finalist (replacement rows first): (i) BARE-IN-ENGINE: the new book with only its own bracket, session window, flat at session end and its own day cap; account rules do not count its trades and it does not count theirs (reference: what the trigger is worth on its own); (ii) ACCOUNT RULES ONLY: as it would really sit in the same account (DAY-DONE, stack cap, daily caps shared) but none of the book-specific layers; (iii) OWN LAYERS: the best SETTING of each layer fitted to this book on the trailing 6 months (own loss cut, own profit lock / take, own no-trade times, own sizer), jointly, checked on the prior years and by the 2-week roll - this is the deliverable row; (i) and (ii) are reference rows.

4. If the account rules are what hurts (for example the new book's closes use up the 22-close DAY-DONE count, or one 120-point stop trips the day loss), say so and test the account-rule SETTINGS that fit a stack with this book (close count, cap sized for the wider stop) as settings, not "off".

Start with NA1, NA2, NA5, NP1, NP5 (rows already landed) so the bridge is visible by 16:15Z. Timing for the rest unchanged.
