# DESK v0.2: a logic error in the clock rule, found while coding it: report its firing, amend once (RESEARCH note)

written by the relay (Claude), not typed by Josh. Change discipline: the design changes only when the LOGIC is wrong; this is logged as such.

THE ERROR (mine, in the order; your implementation follows it faithfully): "CLOCK: if the distance still wanted exceeds what NQ normally covers in the minutes left -> take it now", with your formula wanted = T0 - open > sqrt(N) x typical 1-minute move. With N unbounded this fires hours before the bell on the wide books: e.g. T0 = 120, typical 1-minute move 8 pt, N = 150 min: sqrt(150) x 8 = 98 < 120, so ANY open profit is taken at once from the first second of NY AM. A trader applies the clock near the bell, not all session.

1. FIRST, show it: for each v0.2 set already run, the share of exits by the clock rule and the distribution of minutes-to-bell when it fired (how many with more than 30 minutes left), per book. One small table, before anyone reads the scorecard.
2. AMENDMENT v0.2.1 (ONE fixed value, logged and counted as change no. 4, reason "logic error in the clock rule"): the clock rule applies only when 30 minutes or fewer remain to the session bell. "One minute left in profit -> all" unchanged. Nothing else changes.
3. Rerun the v0.2 sets as v0.2.1; keep the v0.2 rows labelled so the effect of the fix is visible. Scorecard and tape review are read on v0.2.1.
If the table in 1 shows the clock rarely fired outside 30 minutes, say so and the rerun can be skipped.
