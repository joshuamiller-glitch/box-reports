T-ZEN ADDENDUM 6 — the full structural stop x target grid (2026-10-28)

Same rules as T-ZEN. Applies to the top entry cells of every family. Structural brackets are entry x bracket combinations here (exits-on-existing-books are dead and not re-tested). Every cell reports the realised stop distance distribution (median, p90) and the realised reward:risk, because structure stops vary trade by trade; plus the cost-adjusted break-even win rate for the realised ratio. Pairs that make no sense (target closer than 1 tick, stop > 60 pt) are skipped and counted.

S1. Stop sources (for a long; mirror for shorts) — each with buffer 0 / 2 / 5 ticks

Candle: low of the hold candle; low of the previous 1-min candle; lowest low of the last 2 / 3 candles. Line: 1 tick below the entry line; below the regime line (wide); below the zone (FVG far edge, OB far edge). Swing (per timeframe 1-min, 3-min, 5-min, 15-min; strength 2 and 3): the last swing low; the last HIGHER low (structure point); the swing low that started the impulse leg. Range: the pullback low (lowest low since the leg's high); the session low; the opening-range low (09:30-09:45 / 09:30-10:00); the previous hour's low; the overnight low; the previous day's low; the lowest low of the last N 1-min bars (N = 10, 20, 50, Donchian-style). Levels: the nearest round number below (x00 / x50); the nearest prior-day/overnight level below; VWAP −1σ. Skip rules: skip the entry when the chosen stop exceeds 15 / 20 / 30 pt (the model's timing rule), and the ATR-cap variant (stop > 1.5x 1-min ATR14 -> skip).

S2. Target sources — each as single target and as the first of two

Swing (per timeframe 1-min, 3-min, 5-min, 15-min): the nearest swing high; the last LOWER high (for a reversal); the impulse leg's high; equal highs (two highs within 2 pt). Range: the session high; the opening-range high; the previous hour's high; the overnight high; the previous day's high; the previous day's close; the highest high of the last N bars (N = 20, 50, 100). Levels: the next round number above; VWAP / VWAP +1σ / +2σ; the 5-min EMA20 (for a reversal from below); the nearest 4-hour FVG edge; the nearest 1-hour / 4-hour swing high; the daily pivot R1 / R2; the SD extension −1.5 / −2.25 of the impulse leg (Addendum 1 Z5). Multiples of the structure stop: 1R, 1.5R, 2R, 3R of the realised stop distance; and "whichever is nearer of 2R and the next structure". Fixed: 20 / 30 / 40 pt (the comparator).

S3. The grid

Primary: every S1 stop x every S2 target on the top 5 entry cells, screened on PRE, ranked by effect vs random-in-regime with the SAME bracket pair (the random entries get the same structural stop/target logic applied at their random minute), top 30 to holdout. Report the grid as a heat table (stop source rows x target source columns) of PRE pts/trade and win rate vs break-even, so the shape of what works is visible even where nothing passes.

S4. Trailing on structure (as bracket shapes, paired against the fixed version)

Move the stop to each new 1-min higher low (strength 2 / 3); to each new 3-min / 5-min higher low; to the previous candle's low after +X pt; to the entry after +1R / after the first scale; Chandelier (highest high − 2 / 3 x ATR14); the 5-min candle-low trail from Addendum 1; exit on a close below the 1-min EMA20 after +1R. Each with and without a first scale at the nearest structure.

S5. Multi-target scaling

First target = nearest structure (S2) for 50% / 75%, second = the next structure up / 2R / the previous-day high / the 4-hour FVG, stop to entry after the first fill (and NOT to entry, as the control: the dead-BE finding from CRT should be re-checked here on a 15-pt stop, where BE means something different). Three-target ladders (25/25/50) on the top 3 cells only.

S6. The ladder of highs and lows as a map (descriptive, all touches)

For every touch: the distance to each S2 target above and each S1 stop below at the moment of entry (pts and ATR), and which level price reached first. A table of "probability of reaching the nearest swing high before the hold-candle low is broken" by level type and by window: the structural odds, independent of any bracket choice. This is the number that tells you whether structure targets are reachable at all from a 1-min EMA200 touch.

Reporting

DS3_ZEN_STRUCT.md: the S6 map first, then the S3 heat table, trailing (S4) and scaling (S5) paired results, the realised stop/target distributions, and the plain line: "the best structural pair is stop X / target Y, realised R:R Z, win rate W vs break-even B, effect vs random V with MDE" or "no structural pair beats the fixed bracket". Folded into DS3_ZEN_FINAL.md.
