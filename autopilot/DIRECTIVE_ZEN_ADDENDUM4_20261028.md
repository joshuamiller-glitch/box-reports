T-ZEN ADDENDUM 4 — trend strength BEFORE the pullback, as a feature search (2026-10-28)

Same rules as T-ZEN. Every candidate touch (any family, any line pair) gets a vector of pre-touch trend-strength features measured at the moment of the touch, using only data before it. The question: which features separate touches that bounce from touches that fail, and does gating on them beat random-in-regime (with the SAME gate applied to the random entries, so the feature is credited only for what it adds beyond "strong trend + bracket"). This is a feature study first (descriptive, all touches, no selection), then a small set of pre-registered gate cells.

F1. Features (computed at the touch; T = time since the regime began, i.e. since price last crossed the regime line)

Time / distance:

Bars (1-min) since price last touched / closed below the entry line (the "stayed above" count); same for the 20 and 50 lines; bars since the regime line was crossed.
Max distance of price from the entry line during the leg (pts and in ATR units); distance at the touch of the regime line from the entry line (the two lines' spread, the model's "separation").
Number of prior touches of the entry line in this regime (first touch, second, third+); outcome of the previous touch (bounced / failed).
Height of the leg (impulse from the last swing low to the swing high before the pullback) in pts and ATR; depth of the pullback as a fraction of the leg (0.3 / 0.5 / 0.618 / 0.786); pullback duration in bars; pullback speed (pts per bar) vs the impulse speed. Structure:
Count of higher highs and higher lows (1-min swings, strength 2 and 3) since the regime began; whether the pullback broke the last higher low (structure intact or not); number of 5-min closes above the 5-min 20 line in a row. Slope / momentum:
Slope of the entry line and the regime line over 5 / 20 bars (pts/bar and normalised by ATR); 1-min and 5-min ADX14, DI+/DI-; RSI14 on 5-min at the touch; the 1-min 20-line vs 200-line spread and its 5-bar change (the model's "20 curling"); 5-min Supertrend age. Volatility / participation:
1-min ATR14 at the touch vs its 20-day median (quiet vs wide); realised range of the leg vs the day's median range; volume of the impulse leg vs the pullback's volume (impulse/pullback volume ratio); cumulative delta over the leg and over the pullback (with the tape); number of 1-min bars in the pullback with volume > 2x median. Context:
Minutes since 09:30; minutes since the last scheduled release; day type ex-ante (first-hour range vs median); overnight direction agrees with the regime; ES and RTY on the same side of their own regime lines (cross-index agreement); VWAP on the trend side; distance to the nearest 4-hour FVG / prior-day high-low in the trade direction (room to run). Derived:
Interactions that the model implies: "held above for >= N bars AND first touch", "leg >= 2 ATR AND pullback <= 0.5 of leg", "20-line curling AND structure intact".

F2. Descriptive pass (all touches, no selection, PRE window only)

For each feature: bounce rate (reaches +1x stop before -1x stop at the 15-pt and 60-pt stops), mean pts/trade at the model's bracket, by decile / by bucket, with n and CI; a one-line ranking of features by the spread between their best and worst bucket (information, not a verdict). Also a simple regularised model (logistic on standardised features, PRE only, 5-fold) and its out-of-fold AUC, so we know whether ANY combination carries information before gating cells are written. Report the top 10 features and the AUC plainly.

F3. Gate cells (pre-registered after F2, on PRE only; <= 20 cells; holdout once)

The top features as gates on the top entry cells from T-ZEN / Addendum 1-2: e.g. "stayed above the entry line >= 30 / 60 / 120 bars", "first touch only", "leg >= 1.5 / 2 ATR", "pullback <= 0.5 of leg", "structure intact", "20-line curling", "impulse/pullback volume >= 2", and the model-score top tercile from F2. Each paired on the ungated base and vs random-in-regime with the same gate. Verdict per gate: effect in pts/trade with MDE, trades kept (%), win rate vs break-even at the 15-pt stop, by window, by year.

F4. The opposite question

Does trend strength predict FAILURE of the pullback instead (over-extended legs: distance from the regime line > 3 ATR, RSI > 75, 5+ higher highs without a 20-line touch)? The same gates inverted as a "skip" filter, and as the reversal-entry condition for T-ZEN section 6.

Reporting

DS3_ZEN_STRENGTH.md: feature table (F2), AUC, gate results (F3), inverse (F4), and the plain sentence: "the pre-touch feature that matters most is X; gating on it changes pts/trade by Y with MDE Z; or: nothing about the trend before the touch predicts the bounce." Folded into DS3_ZEN_FINAL.md.
