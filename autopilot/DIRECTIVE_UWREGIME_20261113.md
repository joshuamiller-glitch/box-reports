DIRECTIVE (user) — T-UWREGIME: UNUSUAL WHALES AS A DAY-TYPE AND RANGE TOOL. Research only; nothing on the execution server or any live chart changes. No new spend. Runs beside T-UWBOOKS and W-UW2, does not replace them. The user does not accept "UW is worthless" on the tests so far: direction was tested, range and day type were not.

1. FORECAST TEST FIRST (no trading). Does UW forecast, out of sample: (a) the session's range and realized vol, (b) trend day vs chop day (efficiency ratio, close location in range, number of mean crossings), (c) pinning near the largest gamma strike into the close, (d) time of day of the high/low? Inputs: gamma level and sign (SPX, NDX, QQQ, SPY), distance of price to the flip level and to the walls, vanna/charm, IV level, IV minus realized, IV term slope, implied move vs actual move so far, 0DTE share of volume, Tide level. Readings as of prior close, 08:30, 09:30, 10:00 ET. Benchmark every forecast against the no-UW version (yesterday's range, ATR, VIX alone). Report the gain OVER that benchmark, session by session.

2. IF IT FORECASTS, USE IT ON D7's EXISTING DIALS (exact engine, JN05W2 base, all layers ON):
- target and stop width per book by forecast range (wide on big-range days, tight on pin days);
- which books run: mean-reversion books (K7) favoured in positive gamma, trend/pullback books (P7, U7) in negative gamma; test size x0.5 / x1 / x1.5 by book, not on/off;
- cut and lock settings by day type (hold longer on trend days, take earlier on pin days);
- the day-done and stack caps by forecast range;
- the last 90 minutes: fade moves away from the largest gamma strike when gamma is positive.

3. STILL UNTESTED INPUTS — screen all of them in both uses (direction and day type): IV stats, dark-pool levels, the full options tape by DTE bucket and >= $100k trades, megacap exposure and flow, IWM, DIA, opex week and opex day, month-end and quarter-end.

4. RULES. Session by session; L3M and L6M from today first, then HOLD and PREUW; tolerant gate; drawdown first (worst week, max DD, full stops/wk), then mean; measured fills; walk-forward every 2 weeks; family null and placebo beside every number; each value used only as of when it was available. "Nothing" is not a deliverable: deliver the best setting per dial with its evidence and say how strong it is.

5. REPORT. DS3_UWREGIME.md, first page within 3 hours (the forecast test), update every 3 hours. Say plainly for each input: forecasts range yes/no, forecasts day type yes/no, and by how much over the no-UW benchmark.
