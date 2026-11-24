# ORDER (research, conditional): the Asia depth book and repeated same-side stops
**Josh's words are quoted; lines marked (relay) are the relay's reading. Research only: nothing live, no gate or rule change, no spend, no data deleted.**

What happened live tonight (relay, from the strategy's own trade file, 6 lots per book, td 20261124): L578701ed (the depth book) took SEVEN LONG full stops in a row between 01:24Z and 02:23Z while the market fell (entries 26,955 / 26,915 / 26,878 / 26,853 / 26,816 / 26,827 ...), 15 trades for about -$10,260 on the night so far. Its delivered settings (BF2_JT19: LK6, NRT2, book day loss -6R) have nothing that stops a book re-entering the same side after repeated stops.

The relay told Josh and suggested asking whether a skip rule on this one book helps. Josh, 23 Nov 19:44 MT: "put it to the box if that book still is on our mix after asia is done in a few hrs"

## What to do (relay)
CONDITION: only if L578701ed is still a member of the Asia stack after step (b) of the Asia-first plan (the combination re-run on the full pool). If it is replaced, write one line saying so and skip the rest.

If it stays, include in step (d) (the Asia 2-lot joint) these PER-BOOK candidates, for L578701ed alone and, as the same family, for each other Asia member alone (so the joint can keep it on one book and leave it off the others):
1. CGB per book: skip after n = 2 / 3 / 4 same-side losing closes with no new session extreme in the trade direction (the rule already coded in the D8 file for NY PM), governed book = that one book only.
2. Per-book stop run (DLC per book): after n = 3 / 4 / 5 full stops in a row on the SAME SIDE, pause that side of that book for 30 / 60 / 120 minutes, or until a new session extreme in the trade direction.
3. Reference rows only: the delivered pick; the whole-stack CGB2 of JT143.

Report, on the page SESSION_DONE_ASIA.md (or autopilot/ASIA_DEPTH_REPEAT_STOPS.md if sooner):
- how often the depth book has runs of 4+ / 6+ same-side stops inside one session in L6M and in each prior year, and what those sessions cost (so Josh can see whether tonight is typical);
- each candidate: L6M with L3M beside, $/wk, max drawdown, worst week, worst day, ulcer, for the book alone AND for the Asia stack; prior years; walk-forward; best-of-many null;
- the verdict the approved way (drawdown first; pick on recent; prior years not a disaster; null 4 of 5), and the exact parameters if one is delivered, so the relay can switch it on for that book only.

Rank: part of Asia step (d); if step (d) has already started when this arrives, run it as a small top-up screen right after and say so. Machines stay full.
