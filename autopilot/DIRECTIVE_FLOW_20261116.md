# USER ORDER 2026-11-16 (verbatim): T-FLOW (wide order-by-order search, cross-market condition, flow as an entry trigger)
Research only. All guard rails apply. No new spend: use the NQ MBO history
already bought and the free 1-s / 1-min history for other markets; quote
anything else, buy nothing. Exact engine, JN05W2, all layers ON, every
signal gated (taken and replacement), per book x session, windows L3M L6M
HOLD GAP PRE X' measured from today, drawdown first, FIRST PASS labels,
nonsense bar per cell, placebos (shift 11/23/37), matched-count subsets,
engine random skip at the same keep share, planted-edge check on each new
library before any result is read. Priority: directly after the bracket
grid and LR windows; ahead of all chart-indicator work.

PART A - WIDE ORDER-BY-ORDER LIBRARY (target several thousand conditions)
The only family with a real effect so far is c_H2_arrival_imb60_lo. Search
its neighbourhood as widely as the chart indicators were searched.
Windows 1, 5, 15, 30, 60, 120, 300 s before the entry second. Each reading
as own side, other side, and the difference; raw and as a percentile of
the prior 20 days at the same time of day; levels 1, 1-3, 1-10.
 1. Arrivals: order adds by count and by size, by side.
 2. Cancels: count, size, cancel-to-add ratio; cancels at the touch vs deep;
    cancels on the side price is moving toward (liquidity pulling).
 3. Trades: aggressor imbalance, trade size distribution, large prints,
    runs of same-side aggressors, speed (trades per second).
 4. Sweeps: one aggressor clearing 2+ levels; count, size, side; time for
    the swept level to refill to half and to full; refill failed.
 5. Hidden size: prints at a price exceeding displayed size (iceberg);
    repeated refresh at the same price; side; distance from entry.
 6. Absorption: heavy aggressor volume into a level with price not moving.
 7. Queue: depth ahead at the entry price, order age at the touch, share of
    touch depth that is under 1 s old (fleeting), top-of-book flicker.
 8. Order size mix: share of 1-lots vs 10+ lots in adds and in trades.
 9. Price impact: ticks moved per 100 contracts traded, by side; change in
    that reading over the window.
10. Stop-run signature: sweep through a prior swing or session level
    followed by refill and reversal inside N seconds (N = 5, 15, 60).
11. State of the book at D7's own stop and target prices at entry: resting
    size there, and whether it has been building or pulling.
Latency: score every item at 0, 1, 2, 5 s delay. Drop items that need
under 1 s.
Report per item: $/trade and R/trade vs cell, both percentiles, by year,
cluster membership. Then engine: SKIP, HALF, x1.5, x2, WAIT (up to 30, 60,
120 s for the state to turn favourable, then take or drop).

PART B - OTHER MARKETS AS A CONDITION ON D7 ENTRIES (no extra cost: D7 is
already paying to trade)
Use the T-ALPHA forecasts and their inputs, causal at the entry second:
 1. The combined multi-market forecast for NQ at 5, 15, 60 min: sign and
    strength relative to the trade side.
 2. Single leaders: ES, RTY, YM, ZN/ZB, DX or 6E, VX, GC, CL: return over
    the last 10 s, 1, 5, 15 min relative to trade side; NQ-minus-ES gap
    opening or closing; NQ leading or lagging ES.
 3. Agreement count across markets (how many point with the trade).
Same scoring and the same four engine actions as Part A. Report whether
each can be computed live from feeds D7 already has (CQG via NT8) or needs
a new subscription.

PART C - CONTINUOUS SCORE, NOT YES/NO
For the items passing A or B in a cell: fit one score per cell on the
trailing 26 weeks (frozen and 2-week refit both, per T-RECENTS finding),
walk forward, size by score quintile (half / x1 / x1 / x1.5 / x2, capped at
the book's live cap). Compare with the same procedure on nonsense items
and with a random size ladder of the same lot distribution.

PART D - FLOW AS THE ENTRY, NOT A FILTER (new shadow books)
Take the best Part A events as triggers by themselves, at levels a trader
would care about (session high/low, prior day high/low, overnight range
edges, VWAP bands, D7's own zones):
 1. Stop-run reversal: sweep through the level, refill, enter against.
 2. Absorption at the level: enter with the absorbing side.
 3. Liquidity pull ahead of price at the level: enter with the move.
 4. Arrival imbalance low on one side at the level: enter per the sign the
    filter result implies.
Brackets 40/40, 40/60, 58/60 and time stop 5/15/30 min. Costs at $4.84 and
measured slippage at 1 s latency. Per session. Report standalone AND added
to the D7 stack (drawdown, overlap with existing books, correlation).
Register survivors as shadow books only.

REPORT: DS3_FLOW.md. Lead with what passed in recent windows, then older,
then failures. For each survivor: can D7 compute it today, or does it need
the live L3 feed plus a sidecar on the VPS. Keep the hourly line current.
