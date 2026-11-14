ADDENDUM (user) to T-CHOP — CLOSE THE GAPS IN THE CHOP INPUTS. 2026-11-14. Research only. Save verbatim, log within 15 minutes. Runs under T-CHOP's share; these inputs join STEP 2, same label, same benchmark, same placebos, session by session.

ADD, all causal, all from data on the box:
1. STANDARD GAUGES on 1 / 3 / 5 / 15-min bars: ADX and DI spread, Choppiness Index, Bollinger and Keltner band width and squeeze, variance ratio, Hurst exponent, lag-1 return autocorrelation, fractal efficiency; rolling 30 / 60 / 120 min and since the session start.
2. HIGHER-TIMEFRAME CONTEXT at the session start: inside day, NR4 / NR7, position inside the 3- / 5- / 10-day range and inside the multi-day value area, daily and 4-hour trend strength, days since the last 2-ATR day.
3. DEVELOPING PROFILE through the session: single vs double distribution, value-area width vs normal, migration of the point of control (points and direction per 30 min), time spent within the value area, number of rotations.
4. EFFORT VS RESULT: volume and absolute cumulative delta per point of net progress over 15 / 30 / 60 min; delta flips per hour; share of volume at the session's extremes that failed to extend.
5. CLOCK: time-of-day and day-of-week chop rates (lunch 12:00-14:00 ET, Friday afternoon, holiday weeks, month-end), per session.
6. DEALER GAMMA AS AN INPUT (UW data already pulled): gamma sign and size, distance to the flip, 0DTE share, as inputs to the combination, not as a standalone forecast.
7. SECTOR SPREAD from the UW 1-minute ETF prices on the current plan (QQQ, SPY, IWM, XLK, SMH and whichever sector ETFs the plan returns; pull them, no spend): dispersion of sector returns, share of sectors moving with the index, leadership flips.
8. COMBINATION MODELS, walk-forward: (a) logistic / gradient-boosted model on all inputs for "rest of session is chop", at the session start and re-scored every 15 minutes; (b) a regime model on NQ returns and volatility (2 and 3 states), giving the probability of the choppy state each minute. Report the gain of the combination over the best single input, and the top 10 inputs by contribution so D7 can compute a small version itself.

QUOTE ONLY, do not buy: ZN and DX (or 6E) 1-minute history from 2023-04 on Databento, to test bond / dollar inactivity as a chop input; a headline-count history from a news API (Benzinga or similar). State the cost and what the free calendar and VIX inputs already capture of the same thing.

FOR THE LIVE BUILD: for the best chop call, say exactly which inputs D7 can compute from its own bars and book at the signal second, and how much is lost if the call is restricted to those.

REPORT in DS3_CHOP.md: one table, every input, forecasts chop yes / no, gain over the benchmark, per session; then the combination; then the actions from STEP 3 driven by the best causal call. First table within 3 hours.
