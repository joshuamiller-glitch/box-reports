# Josh-session-end-run-vs-flatten-test (research order, 2026-11-23 ~06:45Z)

Josh's words, verbatim (01:40 and 01:41 ET, 23 Nov):

> "why is it set to flatten open trades?"

and, to the relay's offer ("The box could score 'let an open Asia trade run to its own stop or target after 2am, with no new entries' against the current flatten rule, and the same question for NY AM at noon. Say yes and I'll order it as fall-through work behind the fits."):

> "yes"

Everything below is the relay's reading (relay = Claude, not typed by Josh).

Context (relay): every D8 book is tested with a scheduled session-end exit (Asia 02:00 ET, NY AM 12:00 ET, London 08:30 ET; executed 1.0 s later). On the first live night an Asia trade that was +40 points with 39 to its target was about to be closed by the clock.

1. (relay) On the pinned Asia 5-book stack TL3_ALN_AS_STKd8106b26ef and the settled NY AM stack TL3_ALN_NY_STKd8b76ecd35 (and the London book L19201dfc when its rows are cheap), truly bare engine, 1 / 2 / 4 lots per book, score these session-end variants against the current rule (reference row = flatten at session end):
   a. RUN: no new entries after the session end, but an open trade runs to its own stop or target (hard flat at the 17:00 ET Globex close and before a contract roll, as today).
   b. RUN WITH A TIME LIMIT: as (a) but closed after at most 15 / 30 / 60 / 120 minutes past the session end.
   c. RUN ONLY IF IN PROFIT: at the session end, close losers; a trade with open profit at or above 0 / 0.25 / 0.5 of its target distance keeps running under (a), with the stop moved to breakeven as a second row.
   d. TIGHTEN AT THE END: at the session end the stop moves to breakeven (or to lock half the open profit) and the target stays.
   The one-position rule keeps applying: say how a running Asia trade interacts with the same book the next session (it has none) and with the stack-level rules.
2. (relay) Report per book and per stack, per lot: how many trades are open at the session end per week, their P&L under flatten versus each variant, and for the stack ulcer / max drawdown / worst week / worst day / $ per week for L6M and L3M, prior years, walk-forward and persistence versus the flatten rule, year bands. Drawdown first. This is an exit-rule (fitted setting), judged by the approved method for fitted settings; the best-of-many null shown when it can run.
3. (relay) Also score the best variants on top of the delivered Asia joint layer pick (BF4_JT1), and include the family in the joint stage so it is not fixed sequentially; include it in the NY AM and London menus when they are next built.
4. (relay) Deliver the best setting with the exact engine definition (what closes when, which price), so the D8 file can copy it; "flatten" is the reference row, and if no variant beats it say so with the numbers.
5. (relay) Priority: fall-through behind the work already ordered and running (NY AM and London fits and joints, exit verdicts, NY PM stack, nulls) and beside the daily-loss-stop test of order 0640Z; ahead of the lifted first-look tail. One line at start with rows, rate, ETA.
6. (relay) Not in this order: any spend, new machine or data purchase; no change to gates or to the pinned stacks.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
