T-ZEN ADDENDUM 8 — the setup on every bar type, lines and all (2026-10-28)

Same rules as T-ZEN. Bar types already in: time 15-s / 30-s / 1 / 2 / 3-min (entry), 5-60-min and 4-h (regime), 500 / 1000-tick, Renko-4. This addendum completes the set and, more importantly, computes the LINES on each bar type (an EMA200 on volume bars is a different line from an EMA200 on minutes), not only the trigger candle.

K1. Bar types (NT8-native where they exist; the library's own builder otherwise, cited from T-PBX B2 for the ones already built)

Time: as above. Tick: 250 / 500 / 1000 / 2000. Volume: sized so the median bar lasts ~30 s / 1 min / 3 min of RTH (state the contract counts). Dollar / notional: same sizing rule in $ traded. Range: 5 / 10 / 20 ticks (NT8 Range), and the price-accurate range bars from the custom-bars work if present. Renko: 4 / 8 / 16 ticks (NT8 Renko and the price-accurate UniRenko/grid-Renko variants if present, labelled). Imbalance / run bars (tick-rule signed volume imbalance threshold, the library's builder). Line break (3-line), Kagi (reversal 8 / 16 ticks). Heikin-Ashi (entries on the HA close are NOT allowed to use the HA open; fills at the real price). Session-anchored time bars (reset at 09:30) vs continuous. Equal-activity calibration: for every non-time type, the size parameter is chosen on the warm-up window so its bars average ~1 minute of RTH activity (and a ~3-min variant), so "bar type" is compared at equal resolution, not confounded with speed.

K2. What is computed on each bar type

(a) the entry line (EMA200 and the top 3 lines from Addendum 2) on that bar type; (b) the hold candle and the Addendum 1 reaction triggers on that bar type; (c) the regime line stays on 5-min time (control) and, separately, on the same bar type at ~5x its size. Brackets as the model (15-pt stop, structure target) and the 60-pt comparator; windows as T-ZEN section 5.

K3. Scoring

Screen on PRE per bar type for the top 5 entry cells; top 30 overall to holdout; best-of-N over all bar types x cells. Report a bar-type table: pts/trade, win rate vs break-even, trades/wk, effect vs random-in-regime (random entries on the SAME bar type), by window. Plain line: does any bar type beat 1-minute time bars on identical signals by more than the MDE, and is the ordering stable across years.

K4. Bar-type-specific effects to report (descriptive)

Renko/range: the lag of the line and the "phantom" moves (bars that print with no trade at that price in the 1-s tape) — count them; a trigger that fires on a phantom bar is a fill that does not exist. Volume/dollar bars: how many bars print in the first 30 minutes vs lunch (they compress time; the 10:00-14:00 window becomes a bar count, state it). Heikin-Ashi: the fill-price gap between the HA close and the real price at the signal.

K5. Execution note for the spec

Any bar type that passes must be one NT8 can build live identically (tick/volume/range/Renko on a Rithmic feed can differ from the historical build); the spec states the bar type, its parameter, and the identity check between the library build and NT8's build on the overlap window.

Reporting

DS3_ZEN_BARS.md: the bar-type table, K4 counts, by window; folded into DS3_ZEN_FINAL.md with the line "best bar type for the ZEN entry: X (or: 1-minute time bars, nothing beats them)".
