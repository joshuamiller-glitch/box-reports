# Selection-rule bake-off: walk five ways of picking through history and keep the one that works (order from Josh, relayed)

Josh, 25 Nov 21:03Z, verbatim: "for futures intraday can you find a formula or precedent for the best way to do this now that we have scored everything? maybe multiple ones and present them with refit schedules"
Josh, 25 Nov 21:18Z, verbatim (after the relay explained option A = walk every selection rule forward through history and use the one whose picks did best in the following period): "ok let's go with option A if you think it the absolute best - mac online - order it"

(relay) Reading. Research only. Method = walk-forward analysis (Pardo) applied to the SELECTION RULES themselves. Re-ranking of stored month rows wherever they exist; say plainly where a rule would need new engine rows before running them.

1. WHAT IS COMPARED (keep the list to these; no variants added after seeing results):
   R1 CURRENT: best L6M (drawdown first), no prior-year filter (what the joint fits did today).
   R2 FILTER THEN RANK (his rule as he states it): drop every candidate that loses money or is RED in a prior year available at that date, then best L6M drawdown first.
   R3 WINDOW: as R2 but the lookback is 3, 12 and 24 months instead of 6 (three rows).
   R4 RECENCY BLEND: as R2's filter, score = 0.5 x last 6 months + 0.5 x all older months available at that date (per-week income and drawdown both blended; drawdown first).
   R5 ENSEMBLE: as R2's filter, then not the top combo but the per-factor MOST COMMON setting among the top 10 by L6M (ties: the milder setting); if that exact combo was not run, the nearest run combo of the 80 and say so.
   Reference rows only: bare (no settings), and the fixed pick each stack has today.
2. HOW: for each stack with a landed 80-combo x 42-month joint (Asia STKd8da2eb47b, NY AM nine STKd8cd0279ff and eight STKd8w42, NY PM primary STKd8w42pm / all-history pmb / equal pme / delivered four STKd893133bd8, London STKd8w42lo): step through history every 2 weeks (his refit schedule; also show 4-week and 6-week steps); at each date each rule picks using ONLY months before that date ("prior years" = the calendar years fully before that date; early dates have fewer: say how they were handled); score the pick on the NEXT step. Chain the next-step results into one out-of-sample curve per rule.
3. REPORT, page SELECTION_RULE_BAKEOFF.md, per stack and for the four sessions' live stacks summed on one calendar: out-of-sample $ per week, max DD, ulcer, worst week, worst day, share of steps the rule beat bare and beat R1, how often the pick changed. Recent first (the last 6 and 3 months of the out-of-sample curve), then by year. Drawdown first. Name the winner per session and overall, and say honestly if the differences are inside noise (42 months = about 80 two-week steps; 7 rule rows is few, but give the best-of-rows luck label anyway).
4. SAME QUESTION ONE LEVEL UP, as a second table if the stored book-month rows allow it without new engine runs: the MIX choice (which books, which weights) under R1 / R2 / R4, because today's prior-year failures look like recent-only BOOKS as much as settings. If it needs new runs, give the count and wait for his yes.
5. Nothing live changes from this page; no gate changes until he has seen it. The prior-year-filtered re-rank (order 2057Z) still comes FIRST: it is the rule he already set.
Spare capacity: the combined-at-6 and session-lots frontier (order 1930Z).
