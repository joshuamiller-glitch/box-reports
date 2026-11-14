ADDENDUM (user) to T-CHOP / dial 9 — MAKE THE BRACKET SCALING BITE. 2026-11-14. Research only. Save verbatim, log within 15 minutes. Runs under tag D9 with its quota raised to 15% of cores (taken from item 8 leftovers first, then evenly from items 5-7). The first dial 9 read: smooth scaling with all point levels scaled is +0.6k to +0.8k/wk and DD 3-8% lower in L3M; the tercile steps lose. Build on the smooth version. Exact engine, JN05W2, all layers ON, live caps.

1. TRADE-HORIZON FORECAST, AT ENTRY (the main change). For each book and session measure the median and 75th-percentile holding time. Forecast the expected NQ move over THAT horizon at the signal second from: realized range / realized vol of the last 15, 30, 60 and 120 minutes; the same clock's normal level (time-of-day seasonality); the session forecast from T-RANGE2 (HAR, HAR + CME implied move); range used so far vs the session forecast; calendar flags. Walk-forward. Report how well it predicts the realized move over the horizon (R2 and rank accuracy, per session), against the session-start forecast used in the first dial 9. Then W = k x expected move, set per trade at entry, k fitted per book.

2. PER BOOK AND PER SESSION. Fit the scaling separately for K7, M7, U7, P7, H7, A7 in each session. Report which books gain and which do not; a book that is better left at its fixed bracket stays fixed. No pooled verdict only.

3. GEARING AND BAND. W = base x ratio^g with g = 0.5 / 1 / 1.5 / 2; clip 30..100, 25..120 and 20..150; a dead band (no change when the ratio is within +/-10% and +/-20% of normal) so small forecast noise does nothing.

4. LOTS. Constant dollars at the stop, increase capped at x1.5 / x2 / x3; and the version where lots follow only half the change in W (so narrow brackets carry somewhat less dollar risk and wide ones somewhat more).

5. TARGET-TO-STOP RATIO. Besides the book's own ratio: target = 0.8 / 1.0 / 1.2 / 1.5 x W; and the ratio itself moving with the forecast (nearer target relative to the stop when the expected move is small, further when large).

6. EVERYTHING IN POINTS SCALES WITH W, as in version A: state-cut and context-cut arms, flat cuts, lock levels, add distances, time stops in proportion. Also fix the one level that could not be scaled (the hard-coded 30-point profit-side tighten threshold in sim.py) through the hook, and say what it changes.

7. COMBINED WITH THE CHOP CALL. Narrow bracket only when BOTH the expected move is small AND the chop inputs say chop; wide only when the trend-day inputs agree. Compare with each alone.

8. NARROW-ONLY AND WIDE-ONLY halves for every finalist, to see which side carries the gain.

RULES. Session by session; L3M and L6M from today first, then HOLD, PRE, X', GAP (the trade-horizon forecast needs only our own bars, so it can be scored on all 43 months: do that); tolerant gate; a lead must hold in recent AND older windows; drawdown first (max DD, worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing), then mean; fees and measured slippage at the real lot count; exact placebos (forecast shifted 11 / 23 / 37 days, and expected move taken from the same clock on another day); drawdown also with week 2026-W44 removed; walk-forward every 2 weeks. "Nothing" is not a deliverable: best setting per book and session with its evidence.

FOR THE LIVE BUILD. For every finalist state exactly what D7 would need at the signal second and whether D7 can compute it itself from its own bars (preferred) or needs a file from the box. A version D7 can compute alone ranks above an equal version that needs a file.

REPORT. DS3_RANGEUSE.md, section "Dial 10: trade-horizon bracket", plain one-line verdict. Forecast quality table within 3 hours; first exact cells within 6 hours.
