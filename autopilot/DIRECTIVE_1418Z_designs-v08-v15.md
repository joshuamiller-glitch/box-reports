# Josh: keep manager testing running until Sunday Globex: eight more designs + a walk-forward judge (RESEARCH order)

Josh, typed 14:12Z 28 Nov, verbatim:

> ou need to have this testing until Sunday globex so come up with more

(relay) More DIFFERENT IDEAS (not threshold grids), each written here, replayed ONCE on the exact engine with the same windows, scorecard, same-trade counts and largest give-back per book; each a logged post-result design (changes 11-18); all go into DESK_DESIGNS_COMPARED.md. Run in parallel behind the Sunday rows and v0.4-v0.7; NY AM and Asia first, then London and NY PM. Where a number is not given, choose ONE sensible value in the book's own units, write it down, never vary it. Base for all: bare entry, the book's OWN stop.
- v0.8 SCALE OUT IN THIRDS: one third off at 50% of the old target, one third at the old target, last third no target on the v0.4 ratchet; stop to entry after the first third. (1-2 lots: say exactly how you round.)
- v0.9 VOLATILITY-SIZED GIVE-BACK: no target; the give-back allowed is 2 x NQ's typical 5-minute move at that moment (s5), not a % of the peak; armed once up 1 x s5; never looser than the own stop.
- v0.10 LEVEL-ANCHORED STOP (supply / demand style): no target; once up 2 units the stop sits just behind the nearest level the trade has already cleared (prior day / overnight high-low, session VWAP, round 50 / 100, swing) and steps up level by level; target = none.
- v0.11 TREND DAY vs RANGE DAY: decide AT ENTRY from the session so far: if the session's range used is above its typical for that time of day AND price is beyond the opening range in the trade's direction -> "trend": no target, v0.4 ratchet; otherwise "range": the book's own bracket untouched.
- v0.12 MOMENTUM ROLL-OVER (squeeze / MACD style): own stop and own target stay; once the trade is up 1 unit, if 1-minute momentum (MACD histogram 12-26-9 on NQ 1-minute closes) crosses against the trade -> stop to the nearest swing or entry, whichever is tighter. Nothing else.
- v0.13 TAPE-LED DEFENCE, ASIA AND LONDON ONLY (the one steady lead in WHAT_MOVES_NQ): own stop and target; while the trade is under water, if NQ's own book turns against it (10-level imbalance flip AND liquidity wall against, your S2 flags, held 20 s) -> out. No other rule.
- v0.14 TIME-OF-SESSION: first half of the session: no target, v0.4 ratchet; second half: the book's own bracket; last 30 minutes: halve new entries (late rule) and bank at 70% of the target.
- v0.15 PER-BOOK WINNER PROFILE: target = the book's own causal median winner excursion (expanding, past winners only) for half the lots; the other half no target on the v0.4 ratchet.
THE JUDGE (so picking a design per book is not fitting the past), after the designs land: (1) per book, the best design by drawdown-first scorecard on the whole window; (2) WALK-FORWARD of that choice: at each quarter start pick each book's design from the trailing 12 months (all designs v0.2.2 ... v0.15 + own bracket eligible), apply it to the next quarter; report the walked-forward session mixes vs the bracket: income, max DD, worst week, largest give-back, share of quarters better. That table decides what goes live after Sunday.
Keep the fleet full with this through Sunday 23:00Z; say in each hourly line which designs are done and the queue hours left; if under 3 hours, say so at the top.
