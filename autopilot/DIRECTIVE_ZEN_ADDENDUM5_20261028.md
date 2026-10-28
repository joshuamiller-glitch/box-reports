T-ZEN ADDENDUM 5 — what the first four files missed (2026-10-28)

Same rules as T-ZEN. Items are grouped by what they change; each is small and attaches to the top cells unless it says "all touches".

M1. Points are not constant — the stop and target must also be tested in volatility units (all cells)

NQ went from ~12,000 to ~30,000 across the sample; a 15-pt stop in 2023 is a different trade from 15 pt in 2026. Run every bracket in BOTH units: fixed points (as the model states) and volatility-scaled (1-min ATR14 x 0.75 / 1.0 / 1.5 for the stop; percent of price 0.05% / 0.075%), and report by year which unit is stable. If the fixed-point version only works in one price regime, say so in the verdict.

M2. Entry mechanics (the model does not say how the order is placed)

Three entry types on the same signal: (a) resting limit at the line (filled during the touch, before the hold candle is known), (b) market on the hold candle's close, (c) stop-entry 1 tick above the hold candle's high (confirmation entry); plus (d) limit at the zone midpoint for FVG/OB entries. Report fill rate, average entry vs the line, and pts/trade for each. Also the hold-candle anatomy as features (all touches): wick penetration through the line in ticks (0-2, 3-8, 9+), body size, close location in the bar, bar volume.

M3. Stop placement variants (not only distance)

Below the wick low +1/+2 ticks; below the line; below the hold candle's low; below the last 1-min swing low; fixed 10/15/20; ATR-scaled (M1). Each paired on identical entries; report the realised stop distance distribution for the structure variants (the model's "if it needs more than 20 the timing was wrong" becomes a skip rule: cell that skips entries whose structure stop exceeds 20 pt).

M4. Session definition of the lines (a 1-min EMA200 spans ~3.3 hours, so at 10:00 it is mostly pre-market)

Lines computed on (a) continuous 24-h bars (default), (b) RTH-only bars (reset at 09:30), (c) anchored at 09:30 (VWAP-style anchoring for the averages too). Report the three on the top cells; the model's charts are usually (a), traders argue about it, the data decides.

M5. Long vs short, and higher-timeframe alignment

Every table split long / short (NQ drifts up; the short side of a pullback model often has a different win rate). Higher-timeframe context as features and gates: price vs daily 20/50 EMA, prior-day direction, overnight gap direction and size, weekly open side, distance to the nearest 4-hour FVG and to prior-day high/low in the trade direction (room), first pullback after the 5-min EMA200 cross (reversal-day entry) vs later pullbacks. Long-only and short-only versions of the top cells.

M6. Re-entry and attempt count

After a stopped touch: re-enter on the next hold candle at the same line (second attempt), or not; max 1 / 2 / 3 attempts per level per session; "once failed, done for the day" vs unlimited. After a win: pyramid on the next touch in the same trend (add 50%) vs no adds. Minimum spacing between trades (5 / 15 min). Max trades per day 2 / 3 / 5 and "first trade of the day only" (the model's own fatigue rule).

M7. Exits the model does not name

Time stop (flat after 10 / 20 / 30 min if neither level hit), exit on a 1-min close back below the line, exit at the 1-min EMA20 touch from above (for longs: when price crosses back below the 20 after the bounce), exit at VWAP / opposite VWAP band, exit at the session's prior high. All as bracket cells paired against the structure target. Time-to-resolution of winners and losers as a feature (minutes), to size the time stop from data not guesswork.

M8. The counts the model's claims depend on

How many ZM2 / ZM3 / ZM4 setups actually occur per week in 10:00-14:00 under strict definitions (stack within 5 pt, fresh FVG, OB at the level)? If ZM4 is 1-2 per month, say so: a tier with n < 100 trades in the whole sample gets a count, not a verdict. Report the frequency table before any tier P&L.

M9. Replication on ES, RTY, YM (the model claims "any liquid market")

The top 10 cells overall, constants scaled by the warm-up range ratio (as D3CX / CONFIRM A), 1-min bars, conservative fills, one holdout look. Replication on >= 2 of 3 is the strongest evidence available against best-of-N; NQ-only = lucky fit (the CONFIRM A rule).

M10. The learned gate (the firm way), once, with discipline

On all touches, PRE only: gradient-boosted model on the Addendum 4 features + M2 anatomy + M5 context, nested cross-validation, feature importance; report out-of-fold AUC and the top 10 features. Then ONE pre-registered gate cell from it (top-tercile score) to the holdout, counted in best-of-N. If AUC < 0.55 out of fold, say "nothing about the touch is predictable" and stop.

M11. Sizing by tier (the model's rule: ZM1 minimum, ZM4 full)

If tiers have different win rates (Addendum 1 Z3), the lot map 1 / 2 / 3 / 4 x by tier vs flat sizing, lot-matched; and the model's "range day = reduce size / after a 300-pt day reduce size / before FOMC reduce size" as sizing cells. Live-eligible once scored only if the underlying book passes.

M12. NT8 execution feasibility for small stops (write this into any spec)

The P9 slicing (1 lot per 2 s) takes 28 s for 14 lots; with a 15-pt stop the last slices can fill after the trade has already moved 5-10 pt. The spec must state the entry mechanism for small-stop books (single market order, or resting limit, or 2-3 slices max), the stop as a native stop-market with the measured slippage, and the lot size at which this book is executable at all. Addendum 3 B2 measures it; this item makes the spec say it.

M13. Decay and crowding

By-year tables already exist; add by-half-year and the plain sentence on whether the effect is shrinking (the model is popular 2023-2026); and the time-of-day drift of the effect (does the 10:00-11:00 edge move later or vanish).

Reporting

DS3_ZEN_M.md with one block per item (M1-M13), each ending in a one-line plain finding; everything folded into DS3_ZEN_FINAL.md. The FINAL's last section is the single honest paragraph: what ZEN is (a trend-regime bracket, or a real level effect), at what stop unit, which line pair, which window, which confirmation, with what fills, how many trades a week, and what it adds to the stack net of PE — or that it adds nothing, with the numbers.
