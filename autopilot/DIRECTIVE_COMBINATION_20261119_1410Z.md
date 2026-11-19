# ORDER 20261119_1410Z - Josh: after the winners, COMBINE them and pick the best stack

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

Josh's words (14:06Z): "and then we have to combine the winning books to see which ones give the best profit and drawdown numbers"

This is the last step of stage 1, before the D8 build spec. Design it NOW so it runs the moment the ladders finish; do not take engine slots from first looks for it yet (design, tooling and a dry run on the current provisional passers only).

1. WHAT IS COMBINED. Each live book in a session is a slot (Asia: A7, K7, P7, H7, U7; NY AM: K7 and the other NY AM books). For each slot the choices are: keep the live book, or one of the REPLACE passers for that slot (with its own best layers and its tested exit). A combination = one choice per slot across Asia and NY AM together. Individual verdicts were each measured against today's stack with ONE replacement; books interact through the account layers (day halt, stack cuts, book lock, sizer), so the combined stack must be run, not added up.

2. HOW. (a) Screen: build a fast combination scorer from the landed per-trade results (weekly P&L streams per book) to rank combinations and to drop only combinations that are clearly dominated; state its error against the exact engine on a sample of real combined runs before trusting it. (b) Verdict: the exact engine on the combined sets: all single replacements, all pairs, then the best combinations found by the screen and by forward / backward stepwise selection (add the replacement that most improves the stack, drawdown first; then try removing each). No cap on how many passers enter; if the count makes exhaustive runs impossible say so with numbers and show how the stepwise + screen search covers it.

3. HOW IT IS JUDGED (same standing rules): drawdown first (stack ulcer, max DD, worst week), then dollars; L6M pick with L3M beside; each prior year 2023 / 2024 / 2025 not a disaster vs today's stack (rule B); engine persistence >= 0.58 for the combined stack vs today's stack; 30 date-shift controls on the final few combinations. Deliver a table: today's stack / best combination / next best few, with every column, plus which book fills each slot.

4. Layers: per-book layers were fitted one book at a time. The final combinations get a JOINT layer refit (all layers varied together on the combined stack), as the standing rule requires.

5. Post: the design note (autopilot/D8_COMBINATION_PLAN.md), the estimated engine cost as a function of the number of passers per slot, and a dry run on today's provisional REPLACE passers (2 NY AM vs K7, the Asia one vs A7) so the tooling is proven before the ladders finish.

One LEAD NOTE answering 1-5.
