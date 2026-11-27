# Dynamic exits: add resting-order targets/stops and every level type (order from Josh, relayed)

Josh, 27 Nov 03:03Z, verbatim: "what about targets where there is more orders sitting? what about levels stops and targets? so many things not tested"

(relay) My reading and design. Amends the 03:01Z DYNEXIT order; same subjects, same walk-forward, same PASS rule, drawdown first. Uses only data already on the box (depth/MBO tape, level files, UW files); nothing bought.

X8. RESTING ORDERS (order book).
 a. Target just in front of the largest resting size ahead of the trade (largest cluster within the next N points on the depth book at entry; N = 30, 60, 120; "in front" = 1, 2, 4 ticks before it).
 b. Stop just behind the largest resting size behind the trade (same definitions), with a volatility cap.
 c. Live updating: move the target when the cluster ahead moves or is pulled; exit at market if the size protecting the stop is pulled or eaten; take profit early if a new large size appears ahead.
 d. Persistence filter: count a cluster only if it has rested for at least 30 s / 2 min / 10 min (spoof guard); report each.
 e. Executed-volume version: target at the nearest high-volume node of the session and of the prior session; stop beyond the nearest low-volume gap.
 State exactly which book depth is available per month (10 levels? full MBO?) and how far a cluster can be seen; say where coverage is missing.

X9. LEVELS AS STOPS AND TARGETS, EVERY LEVEL TYPE SEPARATELY AND "NEAREST OF ANY".
 Types: prior-day high / low / close; overnight and session high / low; session and weekly opens; initial-balance high / low; VWAP and its bands, anchored VWAPs; floor and weekly pivots; fib retracements and extensions of the prior day and the current leg; volume-profile POC / value-area edges / nodes; supply and demand zones; swing support and resistance, trendlines and channels; round numbers; Unusual Whales gamma flip, call wall and put wall (mapped to NQ, history 2024-10 on).
 For each: (i) target at the next level ahead; (ii) target at the second level ahead; (iii) stop beyond the nearest level behind plus a buffer of 1, 4, 8 ticks; (iv) both; (v) minimum reward:risk filter 1.0 / 1.5 / 2.0 (skip the trade when the room to the next level is too small); (vi) confluence: use a level as a target only where two or more level types sit within 5 points.
 Report per level type: how often price actually reaches / stalls at it after entry (a plain hit-rate table against a same-distance random level), then the walk-forward result.

JUDGING ADDITIONS: X8 and X9 join the per-book pick menu with X1-X7. Also give one table "family by family, live books only, forward": which family lowers drawdown most, which raises income most. Keep the luck accounting on the scoreboard (this menu is large: say how many recipes in total and charge the pick for it).
ORDER OF WORK: quick screen for X8/X9 on the Asia and NY AM live books first; engine hooks as needed (research code), identity-tested. Post the count and start. If the depth data makes X8c too heavy for the fleet, run X8a/b/d/e first and post the cost of X8c.
