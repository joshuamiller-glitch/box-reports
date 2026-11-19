# ORDER 20261119_0213Z: CORRECTION to 0210Z item 3 (Josh, 02:09Z): nothing goes into D8 that has not had the exit run on it

Research only. Item 3 of order 0210Z ("D8 is not held for exit recipes") is WITHDRAWN. Josh's words:
"nothing goes in D8 that hasn't had the exit engine run on it because that could make it even better."

1. RULE. Every book that is a D8 candidate (beats, or is pending against, the live book it would replace)
   gets the EXIT RUN before the D8 spec is written: all 68 exit recipes (7 families) on that book's own
   entries, beside its fixed brackets. The D8 spec carries, per book, the best TESTED exit (which may be
   the fixed bracket if no recipe beats it), with the evidence.
2. HOW, cheapest first, no shortcut on the candidates:
   a. screen: 68 recipes x the candidate's params on real entries + the same on null draws (as EXIT_YIELD),
      for every cell that has a finished or queued engine REPLACE row, best engine rank first. This is a
      few hundred to a few thousand cells, far smaller than the whole grid: start NOW beside the search
      (priority: below engine and real pass 1, above pass 2 and null draws 3-5).
   b. engine: the top recipes per candidate (best 3 by the recent rule, drawdown first, plus the fixed
      bracket as the reference row) run in the EXACT engine against today's stack as REPLACE and ADD:
      L6M + L3M, then prior years + 30 date-shift controls for the winner. Pick = recent data, no red prior
      year; best-of-68 is a selection: the controls and the null-side exit screen must cover it (say how).
   c. If the exact engine cannot run a recipe family yet (market target, time / behaviour, staged,
      trailing, structure stop, stop-and-reverse): say which, build it, and prove it with an identity test
      (engine with the recipe = the screen simulator on the same entries, trade for trade) before any
      number from it is published. List here anything that cannot be built in time, with a date.
3. BUILD SPEC consequence: for each D8 book the spec states the exit recipe exactly as tested (every
   parameter, order type, what happens on partial fills, session end, interaction with the book's layers
   and with DAY-DONE), so it can be coded exactly as tested. An exit that cannot be specified that
   precisely does not go in; its bracket version does NOT go in either until the exit question is settled
   for that book (Josh's rule above), unless Josh says otherwise.
4. The BROAD exit run on the whole grid (EXIT_YIELD recommendation: finds cells that only come alive with
   exits) is a SEPARATE decision still with Josh; do not start it.
5. Publish: the count of D8 candidates per session, exit-run progress on them, and the D8 spec date under
   this rule (SEARCH_STATUS.md + one LEAD NOTE).
