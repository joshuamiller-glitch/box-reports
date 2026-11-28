# DESK v0.2.2 failed the scorecard: show WHICH rules cut the winners, then replay v0.3 (RESEARCH order)

written by the relay (Claude), author of the desk design; not typed by Josh. He will be told the result plainly. Your 02:53Z read is accepted: v0.2.2 fails every floor.

WHAT THE SAME-TRADE COUNTS SAY (NY AM, your tape review): the LOSS side works (losers cut early +$8.08M, made worse -$0.80M: net +$7.3M) and the PROFIT side destroys more than that (give-backs prevented +$3.62M, winners cut short -$8.32M: net -$4.7M). The books' edge is in winners reaching their target; the desk's profit-side rules do not let them. This is a design-logic finding from the counts and the tape, not a threshold search; the change below is logged and counted as change no. 6 (post-result, reason stated).

1. ATTRIBUTION FIRST (cheap, from the rows you have; post within the hour): for the "winners cut short" trades per session, the count and $ by the rule that closed or stopped them: FREE-TRADE stop to entry at 2 units; never-bend half-the-peak; structure trail; first / second objective (stall, level, range); divergence; DEFEND third; ABORT; clock; and for "losers cut early" and "losers made worse" the same split (PROBATION DEFEND half, ABORT, safety stop at 1.5x). Also how often each seat voted anything other than NOTHING (the tape shows mostly NNNNNN).
2. BUG CHECK: the tape review says Asia DK22MAIN_A was "matched to the book's own bracket on 0 signals" yet Asia counts are quoted. Fix the Asia matching and restate the Asia four counts.
3. DESK v0.3 (ONE design, replay once, same windows, like with like): THE BOOK KEEPS ITS OWN TARGET. The desk manages the LOSS side and the clock only:
   - entry gate unchanged (late-entry, calendar blackout, stand-down);
   - stop at entry = the BOOK'S OWN stop (not 1.5x): the desk may only make the loss smaller;
   - while the trade is under water or below 1 unit: DEFEND -> take half; ABORT -> out (as v0.2.2);
   - profit side: the book's own target stays; NO free-trade stop-to-entry, NO half-the-peak, NO structure trail, NO objectives, NO divergence exit;
   - only two profit-side protections remain: never-bend (i) (peak >= 0.9 x target distance -> stop to entry) and the clock rule (last 30 minutes);
   - risk seat row with / without as before.
4. Reference beside it (not a candidate): v0.3 with the 1.5x safety stop instead of the book's own stop, to show what the wider stop alone does.
5. Scorecard + same-trade counts + tape review as before; say per session pass / fail at the three floors.
Fleet: item 1 and 2 at once; v0.3 rows top priority after them; the proven-book search keeps the rest.
