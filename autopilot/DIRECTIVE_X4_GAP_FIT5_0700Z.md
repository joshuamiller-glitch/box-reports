# Order 0700Z Sun Nov 22 — written by the relay (Claude), not typed by Josh — information + plumbing (no new gate, no new candidate)

## 1. The x4-lot run does not scale: explain it (W-LAYERS + W-COMBO, LEAD to sign off)
LEAD TO JOSH 06:44Z: the 5-book Asia stack TL3_ALN_AS_STKd8106b26ef at 1 lot per book makes $9,103/wk (R1; bare R0 $10,834) with max drawdown -11,350; the SAME stack at 4 lots per book makes $11,086/wk in total (1.22x), ulcer 15,090 (4.4x), max drawdown -42,733 (3.8x), worst week -31,261. Calibration 2 (15:08Z) said about -14% per lot at 4 lots. This is far worse, and Josh will size above 1 lot, so he needs to know which it is:
a. Decompose the gap on that stack, last 6 months: (i) fills only: truly bare R0 at 1, 2, 3 and 4 lots per book (no D7 rule at all); (ii) R1 at 4 lots with the dollar rules scaled x4 versus not scaled (which of BookLock R, DayHalt, same-side lot cap, StackCut, the sizer, NTS halving, c_gov bind at 4 lots and not at 1?); (iii) per book: which of the five loses the most per lot at 4 lots, with its average entry and stop slippage in points at 1 lot and at 4 lots, and how many levels of the 10-level book the 4-lot market order walks in Asia hours.
b. Say in one plain line each: how much of the gap is real fill cost at size, how much is a rule binding, how much is an engine artefact (for example the stop "market order walking the book" at 4 lots, or a day cap that was not scaled).
c. The weighted search judges every add at x4 lots and then reports "1-lot units". Say whether its adds and rejects were decided on the x4 numbers. If yes, the weighted search may be rejecting books for a size effect, not for the book: say so, and post beside each weighted FINAL the same stack judged at 1 lot.
These are reference rows and an explanation, not candidates.

## 2. Keep fitting the 5-book Asia stack (W-LAYERS)
The weighted Asia search reached FINAL on those five books (pool 47, 06:38Z), then restarted on the full pool and is rebuilding the same path (step 2 at 06:43Z). W-LAYERS marked the 5-book stack SUPERSEDED and moved to the 1-book stack. Do not drop it: keep the stack-rule + daily-stop fit running on TL3_ALN_AS_STKd8106b26ef (landed rows reused) until the re-run on the full pool posts its FINAL; a 1-book or 2-book intermediate step of a restarted search is not a stack to fit. General rule for tonight: fit the LAST posted FINAL of each weighted/equal search (provisional or not), not the search's current intermediate step. Post the Asia fit verdict as PROVISIONAL with the pool size.

## 3. Reply
One line per item with a time.
