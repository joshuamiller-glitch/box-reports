# STANDING PRINCIPLE (user, 2026-11-11 19:45Z) — D7 MUST TRADE LIKE A WORLD-CLASS DISCRETIONARY RETAIL TRADER
Overrides "best-scoring parameter" as the definition of a result in T-WORKS, the P7 FIX (+ addenda), T-NEAR-ZONE, T-EARLY-CUT, the joint stage and every bi-weekly refit.
Three DEFECTS to remove (not parameters to tune):
 1. It sits in a losing trade until the FULL stop. A full stop must be rare, taken only when the trade never gave a reason to leave.
 2. It lets a trade that reached 80-90% of its target give the gain back (to half, breakeven, a loss). "Don't be a dick for a tick": once most of the move is made, keep it.
 3. It re-enters the same side again and again after the idea has failed and the trend has changed — 3, 4, 5 losses in a row in one session — at full size.
A world-class trader REMEMBERS what just failed, DEMANDS NEW EVIDENCE before trying the same idea again, gets SMALLER or STOPS when the tape has changed, leaves when the REASON for the trade is gone, PROTECTS a gain that is nearly made, takes a quick scratch when a bad trade offers one. Use everything on the box: 1-s book states, flow, structure, the trade's own path (MFE/MAE, time, follow-through), the session's history of this book's attempts, the other books, the other indices.
BEHAVIOURAL SCORECARD — for the LIVE stack and every finalist, per book and for the stack, L6M / HOLD / PRE / X' and the frozen live week, at the top of every FINAL page, in plain words:
 a. full stops per week and $ per week (exit at <= -90% of the stop distance);
 b. give-back events per week and $ (MFE >= 80% of target, closed below 50%) and round-trips (closed <= breakeven);
 c. consecutive same-side losing entries per session: max, 95th percentile, and $ lost on the 3rd-and-later;
 d. entries taken with no new evidence after a same-side failure (count, $);
 e. what it cost: recoveries cut, fills clipped, trend-week winners skipped ($), and net.
A finalist is acceptable only if (a), (b), (c) each fall by at least half on L6M without the cost in (e) exceeding the saving, and it does not turn a trend week into a losing one (replay the frozen week and the five best L6M weeks). Drawdown, mean and the bi-weekly WF are still reported and still matter — but a stack that scores well while still doing 1-3 is NOT a result. Every FINAL page ends with the worst 10 sessions replayed entry by entry, before and after.
Every layer stays ON (rule 1); recents first with the bi-weekly refit (rules 2/2a); joint, exact, one set per job. Zero workers is a failure state.
(Lead: scorecard tool owner = W-Q: code/th_works_q/behavior_scorecard.py `<SET|LPB_BASE>` -> table a-e per window/book + stack; W-J puts the scorecard at the top of DS3_WORKS.md FINAL and the worst-10-sessions replay at the end; every family agent gates its finalists on it. Acceptance tools acceptance_p7.py (W-C) feed c/d.)
