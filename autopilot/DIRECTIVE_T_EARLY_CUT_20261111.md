# ORDER (user, 2026-11-11 19:40Z) — T-EARLY-CUT: full stops must be rare
Mirror of T-NEAR-ZONE on the loss side; all books (P7 first), live panel base, stored 1-s paths for tables, exact for finalists, one set per job. Table in 1 h, rules 2026-11-12 03:00Z, FINAL with DS3_WORKS 15:00Z.
1. THE MAE TABLE (per book x session x entry context [fresh/re-entry/chasing], L6M / 3.5 y / frozen week): of trades whose MAE reached d pts (10,15,20,25,30,35,40,45,50), P(target next), P(breakeven next), P(full stop next), median minutes to each; and by TIME: trades not >= +X pts after N min (X 5-20, N 2-20) -> same probabilities. EV of exiting at d vs holding. Publish before any rule.
2. OBJECTIVE: full-stop $ per week and full-stop count per week (full stop = exit at <= -90% of the stop distance), minimised subject to recoveries lost (cut trades that would have reached target) — report both in $; stack maxDD and mean secondary. A cut that loses more in recoveries than it saves in stops on L6M is not a candidate.
3. RULE FAMILIES:
 a. THESIS INVALIDATION: exit when the structure that defined the entry breaks — pullback swing low/high (1/3/5-min fractal) for P7/A7, Keltner mid for K7, Supertrend line for U7, VWAP side for H7 — with buffer 0-6 pts; and the same as the INITIAL STOP (structure stop) with lots adjusted to equal $ risk vs the 60-pt stop.
 b. STOP GEOMETRY: stop 25-60 x target 45-90 per book x session x context (R7 extended), fixed lots and equal-$-risk lots; the P7 45/60 cell (L6M +5.5% / +$1,556) on all four windows first.
 c. NO FOLLOW-THROUGH: not >= +X after N min -> exit/half; back to entry after MFE >= Y -> exit.
 d. THE SCRATCH: after MAE >= d (25-45), exit at -s (0-10 pts) on the recovery instead of holding for the target; and stop-to-(-s) once recovered to -s.
 e. PARTIAL CUT: exit F (0.33/0.5/0.67) at -d (15-35), remainder keeps the stop; with and without re-add on recovery.
 f. CONTEXT: every family by entry context (fresh vs re-entry vs chasing) and by lots on (>=5 vs <5) — fast exit only where the MAE table says the trade is dead.
 g. the state cut (40/5x/p3 and v2) kept as reference rows; combinations with a-e.
4. ACCEPTANCE (trader test): list the 30 largest losing trades of L6M and of the frozen week under live rules and under the finalist (book, lots, context, MAE path, exit); PASS if full stops fall by >=50% in count and in $ on L6M AND recoveries lost <= stops saved in $ on L6M and HOLD. Plain sentence per book: "full stops were N/week costing $X; now M/week costing $Y; it gave up Z of recoveries".
5. Deliver per book in the policy grammar + v1.8 fields (structure stop, time/no-follow-through exit, scratch, partial cut), and feed the winners to the joint stage with T-NEAR-ZONE and the P7 fix.
