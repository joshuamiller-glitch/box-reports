-ZEN ADDENDUM 2 — the ZEN premise with every line type, not only EMAs (2026-10-28)

Same rules as T-ZEN and Addendum 1. The premise under test is: a higher-timeframe line gives the side, price pulls back to a lower-timeframe line, a reaction candle at the line is the entry, stop 10-20 pt, target structure. EMA 200/200 is one choice of lines among many; nothing in the model shows it is the best. This addendum makes the LINE a search axis for both roles (regime line and entry line), separately, with the same screen-then-holdout discipline and the random-in-regime placebo on every row.

L1. Line families (each with its own lookback grid; both roles)

Averages: SMA, EMA, WMA, DEMA, TEMA, HMA (Hull), ZLEMA, T3, KAMA (Kaufman adaptive), FRAMA, VIDYA, ALMA, LSMA (linear regression), TMA (triangular), SMMA/RMA (Wilder), McGinley Dynamic, Ehlers MAMA/FAMA (the DS4 MA engine, exact recursion), Ehlers instantaneous trendline, Jurik-style (if a public definition exists; else skip and say so), volume-weighted MA, VWAP (session, and anchored to 09:30 / to the day's high and low / to the week), rolling VWAP (N-bar), Ichimoku Kijun/Tenkan, SuperTrend line (the band itself), Keltner mid/bands, Bollinger mid/bands, Donchian mid, parabolic SAR, pivot points (classic/Camarilla, daily), prior-day/overnight H/L/C and VA/POC as fixed lines (comparator: a line that does not move). Lookbacks per average: 9, 20, 21, 34, 50, 55, 89, 100, 144, 200, 233, 377 (a spread, not a tuning); price input close / hl2 / hlc3. Timeframes: regime line on 5-min (primary), 3-min, 10-min, 15-min, 30-min, 1-hour, 4-hour; entry line on 1-min (primary), 30-s, 15-s, 2-min, 3-min, 500-tick, 1000-tick. The screened N will be large; state it per family in DS3_ZEN_0_PLAN.md and use it in best-of-N. Equivalence check first: cluster lines whose paths are near-identical on NQ (corr of the line series > 0.995 and median distance < 2 pt) and score one representative per cluster, listing the members, so the grid is not inflated by duplicates.

L2. Regime-line search (the side)

With the entry fixed at the model's ZM1 (touch of the entry line + hold candle, 15-pt stop, nearest-swing target, 10:00-14:00), vary only the regime line across L1. Report the top 10 regime lines by effect vs random-in-regime and by win rate above break-even, and whether any beats the 5-min EMA200 paired on the same weeks by more than the MDE. Also regime by SLOPE of the line (rising/falling over N bars) and by price-distance from the line, as alternatives to side-of-line.

L3. Entry-line search (the level)

With the regime fixed at the 5-min EMA200 (and separately at the best line from L2), vary the entry line across L1 on the entry timeframes. Same reporting. Include the "stack" variant: two lines within 3-5 pt of each other (any pair from the top 10), the model's ZM2 generalised.

L4. Joint top set

The top 10 regime lines x top 10 entry lines (100 cells) to the direct replay and one holdout look, best-of-N over the full screened count. The verdict line: the best line pair, its effect vs random-in-regime with MDE, its win rate vs break-even at the 15-pt stop, and the plain sentence on whether the EMA200/EMA200 pair is anywhere near the top or just one ordinary member of the family.

L5. Adaptive and non-price lines (the "similar chart lines")

Lines that are not averages: VWAP ±1/2σ bands as the entry line in a trend (with-trend side); Keltner/Bollinger lower band in an uptrend; the SuperTrend line itself; parabolic SAR; the 1-min swing-low ladder (structure); the 5-min FVG midpoint; the overnight VWAP; the previous-day close; the opening-range edges; Fibonacci 50/61.8 of the last impulse. Each as the entry line with the model's reaction candle and bracket, same windows.

L6. Robustness of whatever wins

Neighbour stability (the lookbacks either side must not flip sign), by year, by window, 2x cost, mirror, and the overlap with PE and with the trend books (shared entry minutes ±5) — the stack-add is net of them.

Reporting

DS3_ZEN_LINES_A.md (clusters and screened N), _B (regime search), _C (entry search), _D (joint + L5), folded into DS3_ZEN_FINAL.md with one extra verdict line: "best regime line / best entry line / EMA200 rank among N / effect vs random with MDE."
