T-ZEN ADDENDUM 3 — the order book at the level (NQ mbp-10 / MBO), and execution reality for 15-pt stops (2026-10-28)

Same rules as T-ZEN. Applies to the top cells of every family (T-ZEN, Addendum 1 tiers, Addendum 2 best lines): the L2 element is tested as (a) a confirmation trigger at the level, (b) a filter on the top cells, and (c) the execution basis. Prior evidence to cite, not repeat: T-PBX block (iv) tape/footprint triggers 0/30 at 60-pt stops; T-OPEN footprint/L2 confirmations "filter only". The difference here is the 10-20 pt stop, where the reaction at the level is the trade.

B1. Book-state triggers at the touch (replace or combine with the "hold candle")

Measured in the 30 s / 60 s window around the touch of the entry line, with the book at the level ±2 ticks:

Absorption: passive size at the level (bid for longs) is hit by >= X contracts of aggressive selling and the level holds (price does not trade through by more than 1 tick); X = 200 / 500 / 1000.
Refresh / iceberg: resting size at the level is replenished >= 2 / 3 times within 10 s after being consumed.
Depth imbalance: sum of bid size over the 5 (10) levels below vs ask size over the 5 (10) above, ratio >= 1.5 / 2.0 at the touch; and its CHANGE from 60 s before.
Aggressor delta: cumulative trade delta over the touch bar flips from negative to positive (longs) within N s; and delta divergence (price makes a lower low at the level, delta does not).
Sweep-and-reclaim: price trades 1-3 ticks through the level, large passive size appears, price reclaims within 15 s (the "stop run" at the level).
Large prints: a single print >= 50 / 100 contracts at the level in the trade direction.
Pull: the opposite (passive size at the level is cancelled, not hit) as the "do not enter" signal and as the inverse trigger. Each as a trigger alone and combined with the hold candle; each as a filter on the top 10 bar-based cells. Random-in-regime placebo: same regime, window and bracket, random minute, with the SAME book-state requirement applied at that random minute (so the book state is credited only for what it adds beyond regime + bracket).

B2. Execution reality (the basis that decides whether 15-pt stops exist)

Every holdout cell replayed on the 1-s/L2 path with: market entry at the touch (+1 tick adverse, queue model), resting limit at the level with real queue position (fill only when the queue ahead is consumed or price trades through), 1-s and 3-s placement delays, stop at 10/15/20 pt as a stop-market with the measured stop-fill slippage (cite DS3_DN_STOPFILL: +1.4-1.7 pt at 10 lots; re-measure at 2, 5 and 10 lots for these stops), and the limit target filled only on trade-through. Report the realised stop in points (stop + slippage), the realised win rate vs the bar-fill win rate, and the lot level at which the slippage alone exceeds the per-trade edge. Also the passive-only variant (resting limit entry, no market) and its fill rate.

B3. Book-state as a day/session filter

Opening-hour book metrics (average depth, imbalance persistence, trade-through rate 09:30-10:00) as an ex-ante label for the 10:00-14:00 window: do ZEN cells perform differently on thick vs thin days; is thin-book = range-day a usable 10:00 label (compare with Addendum 1 Z6).

B4. Targets from the book

Resting size walls above (for longs) within 20-40 pt as the first-scale target vs the swing high; and the absence of a wall as the "hold the runner" condition. One cell each on the top entry cells.

Reporting

DS3_ZEN_L2.md: per trigger and per filter the effect vs the bar-based control paired on identical touches, vs random-in-regime with the same book requirement, win rate vs break-even at the realised stop, fill rate, and the plain line "the book adds X pts/trade at the 15-pt stop" or "the book only filters". Folded into DS3_ZEN_FINAL.md.
