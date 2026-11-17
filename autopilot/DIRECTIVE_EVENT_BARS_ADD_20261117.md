RESEARCH ORDER (relay, 11-17 18:02Z): addendum to 1758Z (new books on event bars). The user wants the full range of sampling schemes covered, and treats the earlier alt-bar study as not valid (old base, one-layer-at-a-time): do NOT rely on DS3_BARS_* / ENGINES_ON_BARS conclusions; cite them only as history. Any bar type can be built for NinjaTrader 8 (custom BarsType), so NT8 availability is not a constraint: just say per survivor whether it is native or custom.

Add these to the bar types in 1758Z (all from the NQ tick tape / MBO history on the box; trailing-only thresholds):
 g. QUOTE / MID-PRICE bars: a bar per N mid-price changes, and microprice bars (size-weighted mid), from top of book;
 h. ORDER-BOOK EVENT clock: a bar per N book messages (adds + cancels + trades), i.e. activity time rather than trade time;
 i. DIRECTIONAL-CHANGE / intrinsic-time events: a new event each time price reverses by a threshold (8 / 16 / 24 / 40 ticks, and ATR-scaled), with the overshoot measured after each change; and CUSUM-filter events (sample when the cumulative move since the last sample exceeds a volatility-scaled threshold);
 j. REVERSAL CHARTS: point-and-figure (box x reversal), Kagi, three-line break;
 k. PROFILE PERIODS: 30-minute TPO brackets and volume-profile periods per session (value area, POC, single prints, poor highs/lows, initial balance and its extensions) as the event grid for entries;
 l. FOOTPRINT / CLUSTER bars: bid-volume and ask-volume per price inside each volume or range bar (stacked imbalances, unfinished auctions, delta divergence at the bar extreme, absorption);
 m. ANCHORED bars: bars and VWAPs anchored at the session open, the 08:30 release, the 09:30 open, the prior day's high-volume node; equal-volume buckets counted from the anchor;
 n. Heikin-Ashi and other smoothing transforms ONLY as a transform applied on top of the event bars above (not on minute candles).

For each bar type report first a plain property table per session (London, NY AM, NY PM): bars per session, serial correlation of bar returns, how close bar returns are to normal, and whether a simple momentum or reversal rule on that bar has any sign stability by year: this tells us which clocks carry structure in which session before any book is fitted. Then the book families of 1758Z on the types that show structure, and the seven live book definitions on each.

Coverage table on the page: 20 rows (time; tick; volume; dollar; volume-clock; tick-imbalance; volume/dollar-imbalance; run; range; Renko/UniRenko; delta; volatility-normalised; quote/mid; book-event clock; directional-change/CUSUM; point-and-figure/Kagi/line-break; profile periods; footprint; anchored; smoothing transforms) with status built / scored / survivor.

Same judging rules, same priority as 1758Z. Research only. No spend.
