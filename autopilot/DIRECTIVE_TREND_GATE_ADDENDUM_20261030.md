# T-TREND-GATE ADDENDUM — institutional regime measures — user directive pasted 2026-10-30 (verbatim)

T-TREND-GATE ADDENDUM — the institutional regime measures (statistical, cross-asset, options-implied, flow) added to the catalogue (user, 2026-10-30)

Applies to T-TREND-GATE sections A-E in full: every item below is a catalogue measure (continuous + buckets), appears in the trend map, the gates / sizers / brackets, the combinations and the learned gate, with the same controls and the same recent-first reporting.

1. Statistical regime (what a desk computes before it looks at a chart)
Time-series momentum at multiple horizons: the sign and magnitude of the return over the last 15 m / 1 h / 4 h / 1 d / 5 d / 20 d (and vol-scaled: return / realised vol, the Moskowitz-Ooi-Pedersen form); the count of horizons agreeing with the signal; the momentum "ladder" (short- and long-horizon momentum agree vs conflict).
Autocorrelation of returns at 1 / 5 / 15 / 60-min lags over rolling windows (positive = trending, negative = mean-reverting); the variance-ratio test (Lo-MacKinlay) at 2 / 5 / 10 / 30 horizons; the rolling Hurst exponent by R/S and by DFA (detrended fluctuation); fractal dimension (Katz / Higuchi); the entropy of the return-sign sequence; the run-length distribution of return signs vs its random expectation.
Hidden Markov / Markov-switching models on 1-min and 5-min returns (2 and 3 states: trend-up / trend-down / chop; and vol-high / vol-low), fitted walk-forward, the filtered state probability at the signal second as the measure; Kalman trend filter (local linear trend) slope and its variance; Bayesian online changepoint probability (a regime just changed = do not trust the trend yet); the Ehlers / Hilbert-transform cycle-vs-trend mode and dominant cycle period.
Realised vs implied: realised vol (1 / 5 / 30 min, 1 day) vs the 20-day median and vs implied (VIX level; VX front-month and the VIX term-structure slope — backwardation vs contango; the VIX-of-VIX if available); the variance risk premium sign; "vol expanding with the move" (trend) vs "vol expanding against it".
Return distribution shape over the last 1 / 5 days: skew, kurtosis, the share of range covered by the largest bar (impulse vs grind).

2. Cross-asset and market-structure regime
ES / RTY / YM agreement with NQ at every horizon (the three-index count); the NQ-ES spread trend; sector / factor proxies where on disk (ES vs NQ as the growth-vs-broad proxy); bonds (ZN / ZB direction and its agreement with the equity move — risk-on / risk-off), the dollar (DX / 6E), gold, crude where on disk; the "everything moving together" score (the first principal component's share of variance over the last hour) — high = macro-driven trend day.
Breadth proxies that can be built from what is on disk (ES-NQ-RTY agreement as the only proxy; note $TICK / $ADD are NOT available on the box — name the gap, do not fabricate).
Options positioning as a daily file if the user supplies one (dealer gamma sign / level, the gamma flip level, the largest strikes): negative-gamma days trend, positive-gamma days pin; scored only if the file exists; otherwise named as the gap.
Calendar regime: the day's scheduled releases (FOMC, CPI, NFP, earnings night), opex / quad witching, month-end, the first / last trading day, holiday-adjacent — as a regime tag on every gate.

3. Flow regime (from the tape and the book already built)
Order-sign persistence: the Hurst / autocorrelation of aggressor signs (LMF long memory) over 15 / 60 min; VPIN level and trend; the share of volume from large prints and its direction bias; the book's persistent lean (imb10 sign run length); OFI trend; CVD slope and CVD-price agreement; absorption-vs-exhaustion counts over the last 15 / 60 min; the sweep count and direction; the iceberg count by side; the queue-refill ratio trend (refilling bids = supported trend).
The "trend quality" composite: the walk-forward-weighted combination of 1-3 (the learned gate of section C already does this; here also as a transparent z-score average with the weights printed).

4. Reporting
These enter DS3_TREND_MAP.md and DS3_TREND_GATE.md as their own family ("STAT", "CROSS", "FLOW"); the final adds the plain sentence "the statistical regime measures (HMM state / variance ratio / horizon momentum) add X pts per contract over the chart measures (MA separation / ADX) in the last 6 months, or do not"; and the gaps list (what an institution would use that the box cannot compute: breadth, options positioning unless supplied, intraday implied vol).
