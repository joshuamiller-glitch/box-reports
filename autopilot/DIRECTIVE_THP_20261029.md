T-TH-PROFIT — the profit-side Trade Health search: every technology, every book, in-sample and out (2026-10-29)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Redact account ids. Run 4-8 hours minimum on all cores (replay memory-aware; CPU work on the existing 1-s/L2 trade paths needs no new replay). Session rule in force (score by entry session as a column everywhere). Fill basis: MEASURED for every exit (market exit on the 1-s path +1 tick; stop-market with the measured walk; limit targets at touch with the correction); CONSERVATIVE as a label.

The question

The live profit-side Trade Health (JADE: min profit 20 pts, 3 of 4 conditions, 8-pt trail) is a fixed rule. The user wants the best possible rule for "when a trade is in profit, hold / tighten / take it", found with every tool available, across EVERY book and set (ST, HM, WT, KB, SM, PE, PB, DN, MV, MA, CR, the basket legs; the DS3/DS5/DS6 session cells; the D6 O6 cell), and he will implement what comes out. Prior result to cite, not repeat: the exits program (246/246) found no exit rule that beats hold-to-bracket on average. This program is bigger in two ways: (1) it uses the trade's own path and the order book as features and lets a model decide, not a fixed trail; (2) it reports IN-SAMPLE results as first-class output beside the holdout (the user wants to see what the best possible policy looks like even where it does not generalise), with both clearly labelled.

A. The dataset (build first; one table, reused by everything)

Every trade of every book above on the 1-s path (library trade rows + the direct replays; stored where no replay exists, labelled), from the first second in profit to the exit. At every decision point (every 1 s while in profit; also every 1-min bar close) record:

Path: unrealised pts, MFE, MAE, drawdown from MFE (pts and % of MFE), seconds in trade, seconds since MFE, efficiency ratio (net move / path length) over 30 s / 2 min / 5 min, velocity (pts per 30 s), number of new highs in the last minute, stall seconds (no new MFE), distance to target and to stop (pts and % of R), the live rule's own C1-C4 conditions as booleans.
Order book (NQ mbp-10): depth imbalance 5/10 levels, size at the current best, size at the target level and at the stop level ("wall" ahead / behind), aggressor delta over 10 s / 60 s, trade intensity (prints per second vs the session median), large prints in the last 30 s, absorption at the current price, pulled size, spread.
Bars: 1-min ATR14 vs its 20-day median, distance to VWAP and the VWAP bands, distance to the session high/low, to the opening range, to the nearest 5-min swing, Supertrend 1m/5m/10m state, the 20-EMA slope, bar range of the last 1-min bar vs ATR.
Cross-asset: ES and RTY move since the entry (in their own ATR), ES-NQ divergence over 5 min.
Time: minute of day, session, minutes to the next scheduled release (clock proxy 08:30/10:00/14:00), day type ex-ante.
Stack: other books' positions (same side / opposite), the stack's day P&L.
Labels at the decision point: remaining P&L to the bracket exit (pts), whether the target is reached before the stop from here, time to resolution, max further drawdown from here. State the table size (trades, decision points) and the share with order-book features.
B. Rule grids (the classic layer; the baseline the models must beat)

On identical entries, paired vs hold-to-bracket: fixed trails (10/15/20/30 pts after +10/+20/+30), % give-back of MFE (25/33/50% after +15/+20/+30), ATR trails (1/1.5/2 x ATR 1-min and 5-min), step ladders, candle trails (1-min, 5-min low), EMA20 touch, time stops (10/20/30/60 min if not at +X), stall exits (no new MFE for N seconds), velocity/efficiency exits, the JADE rule itself and its parameter grid (min profit 10-40, required 2-4, trail 4-16), partial exits (50% at +20/+30/+40 then trail the rest), and the combinations. Report per book, per session, per year, in-sample AND holdout, with the give-back saved vs upside forfeited split.

C. Learned policies (the new layer)
Supervised: gradient boosting (and a logistic baseline) on the A features predicting (a) P(target before stop from here) and (b) expected remaining pts; nested cross-validation inside PRE (by day blocks), then one holdout look. Policy: exit at market when E[remaining pts] < 0 (and < -cost, and < -2 pts as sensitivity); tighten (stop to MFE - trail) when E[remaining] in a middle band. Report feature importance (top 15), calibration, and the P&L delta vs hold-to-bracket, in-sample (cross-validated) and holdout, per book and session.
Optimal stopping by dynamic programming: discretise the state (unrealised pts x seconds in trade x drawdown-from-MFE x one order-book imbalance bucket), estimate the transition structure on PRE, solve the value function (continue vs stop), and report the resulting policy as a table; test on holdout.
Survival / hazard model for time-to-target and time-to-stop as competing risks; exit when the hazard ratio turns adverse.
Changepoint detection on the trade's own path (CUSUM on 1-s returns, Bayesian online changepoint): exit on a detected regime break after +X; and an HMM on delta/imbalance (2-3 states) with "exit when the flow state flips against the position".
Quantile regression of the remaining P&L (10th/50th/90th): exit when the 10th percentile from here is worse than the stop would be anyway.
Sequence model on the last 120 s of the path and book (small GRU; only if the above is done within the time budget), same evaluation.
Per-book vs pooled: fit pooled across all books with the book as a feature, and per book; report which generalises. Every model's policy is also evaluated with a placebo (shuffled labels within day; random exits at the same exit rate) so the delta is credited beyond "exiting early reduces variance".
D. The distilled rule (what gets implemented)

For the best learned policy: distil it into something codeable in NT8 without a model file — a decision tree with <= 8 leaves, or a lookup table over <= 3 features, or a small set of IF rules — and report how much of the model's gain the distilled version keeps (target >= 80%). The spec: exact features (how computed live from 1-s ticks and the mbp-10 book as NT8 exposes it, or 1-min bars if the book is not needed), thresholds, the hold / tighten / exit actions, applicability per book, and the plain-English paragraph. Also the "simplest rule that gets most of it" line: if a 2-parameter trail captures 70% of the model's gain, say so.

E. Honest evaluation and the in-sample reporting the user asked for

Two tables everywhere: IN-SAMPLE (PRE, cross-validated where learned; raw in-sample for rule grids, labelled as such) and HOLDOUT (one look). Per book, per session, per year, 2023 span. Paired deltas vs hold-to-bracket in pts/trade and $/wk at the live lots, with MDE; win rate; give-back saved vs upside forfeited; number of exits added; cost of the added exits at MEASURED fills. Stack-level: the policy applied to every book at once, weekly series, SD, maxDD, worst-20-weeks, vs the stack as it is. The multiplicity statement (how many rules/policies were tried). Never-empty-handed: the top 10 by in-sample delta and the top 10 by holdout delta, regardless of verdict, with what killed each.

Reporting

DS3_THP_A_DATA.md (the table), DS3_THP_B_RULES.md, DS3_THP_C_<model>.md as each finishes, DS3_THP_D_SPEC.md (the distilled rule(s), codeable), MORNING.md every 2 h with "best in-sample policy / best holdout policy / distilled rule so far", DS3_THP_FINAL.md with one verdict line per book and the stack line. Use all cores; this outranks everything except an active replay wave already running.
