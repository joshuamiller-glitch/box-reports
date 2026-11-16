# USER ORDER 2026-11-16 (verbatim): T-REBUILD
(server 2, after T-JOINT-EXIT is queued; this box keeps deadline work). Research only, guard rails apply. Exact engine, windows measured from today, recents first, drawdown first, persistent-draw controls, walk-forward for every fitted choice (trailing 26 weeks -> next 2 weeks), planted-edge check before any result is read.

STAGE 0 RAW BASE: each book (K7 M7 U7 P7 H7 A7 O7) alone with NO layers: no sizers, no cuts, no caps, no governors, no stack rules, fixed 60 stop, exits recorded as full 1-s paths (MFE, MAE, time). Per book x session: trades, mean, DD, worst week. This is the reference for everything below.

STAGE 1 CONDITIONS ON RAW TRADES: every condition family already built (L3 arrival, squeeze/volatility state, day direction, range used, other markets, time of day, re-entry context) scored against the RAW trade per book x session: effect on mean R, on MAE, on MFE. Nonsense bar per cell.

STAGE 2 ONE SCORE PER BOOK: combine Stage 1 survivors into one score per book (regularised linear first, then gradient-boosted as a check), walked forward. Size by score quintile. Compare with the same procedure on nonsense conditions and on shuffled outcomes.

STAGE 3 EXITS JOINTLY with Stage 2 sizing: target rule, loss cut (book and flat), profit lock/take, give-back, partials. Choose together per book; report the interaction table.

STAGE 4 STACK RULES LAST: daily caps, DAY-DONE, governor, blackout, stack cut, stack cap, M7 London cap: add one at a time to the Stage 3 stack; keep a rule only if drawdown improves beyond its controls.

STAGE 5 AUDIT TODAY'S STACK (JL2): leave-one-out for every live layer (reference rows only; nothing is removed from live without a tested replacement). Table: layer, what it is worth in mean, DD, worst week, per window, and which other layer it overlaps with.

STAGE 6 HEAD TO HEAD: rebuilt stack vs JL2, all windows, HOLD path 2025-11-17..12-10 separately, W44-removed, $4.84 column, x1.75 lots.

Pages DS3_REBUILD_S0.md .. S6.md. Stage 0 and Stage 5 first (they need no fitting and tell the user today what each layer is worth). Lead note every 6 hours with what has landed.

# ADDENDUM to T-REBUILD (user 11-16, verbatim): Stage 1 must include EVERY family already built, scored against the RAW trade per book x session.
Nothing is excluded because it failed on top of the old stack; that failure is what this order re-examines. Checklist (tick each in DS3_REBUILD_S1.md, with the count of conditions scored):
 1. Full confluence library: the ~21,000 conditions + ~26,000 alt-bar conditions (oscillators, trend, SMC, named systems incl. the Simpler Trading set, squeeze, MACD, CCI, RSI, volume profile, session levels)
 2. Candle-counting families, ICT 7-13-21 count, IRL/ERL sweeps
 3. Zones: the zone layer and every zone definition tested
 4. Range: range-used-up, HAR realised-range forecast, CME NQ options range, UW range forecast, forecast remaining range
 5. Order flow: L3 arrival imbalance and the T-FLOW Part A library, L2 imbalance, walls, the L2 entry gate
 6. Other markets: T-ALPHA forecasts, ES/RTY/YM/ZN/NKD leaders, breadth
 7. Options and positioning: UW exposure/levels/tide/flow, QQQ gamma
 8. Day and regime: day direction vote, chop call, trend-day call, volatility state (atr_rel), event calendar, time of day
 9. Trade context: fresh vs rechase, same-side losers, gap since last close, trades this session, signal quality (SIGQ dA), ER trend sizer
10. Internals: TICK
Stage 2 draws its inputs from all ten. Stage 3 and 4 include every existing exit and stack rule: brackets by forecast, NKD take, stack cut, stack cap, NTZ, breadth skip, blackout, governor, ATR skip, LOT/SIGQ/REG. Stage 0 also runs the borderline and shadow books raw: S7, O7, X1-X8. Conditions that need a feed D7 does not have live (L3, UW, options) are flagged, not dropped.
