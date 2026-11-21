# Order 1558Z Sat Nov 21 — Josh's words quoted; the rest written by the relay (Claude)

Josh's words (15:50Z-15:52Z): "If a bracket size works better recently, we should use that- why would we not pick the bracket size that's been working recently?" / "right it's worse over the whole history, but is it a disaster?" / "how can we expect one bracket size to constantly work with all these changing markets that's why we're re-fitting"

Information only, from the bracket walk-forward series already landed (576 per book). No engine runs, no gate change. W-BRKT, one block + page autopilot/BRACKET_REFIT_SERIES.md, within 30 minutes; partial first.

Josh's method is ADAPTIVE: pick the bracket on recent data, refit every 2 weeks. So the question is not "is today's pick good over the whole history as a frozen shape" but "what would the REFIT PROCESS have earned". Report that:

1. For each of the 43 pool books: the ROLLING-REFIT series (every 14 days pick the shape on the trailing 6 months at equal ulcer, trade it the next 14 days; what would actually have been traded) versus the book's OWN fixed bracket, side by side, at equal risk: $/wk, ulcer, max DD, worst week for L6M, L3M, 2023, 2024, 2025 and the whole walk-forward span; share of periods the refit beat own; how many times the picked shape changed; the list of shapes picked through time (e.g. P60 x 12, P45 x 9, F40_80 x 6).
2. Say plainly which prior-year band the bracket verdicts used: the band of the FROZEN current pick over 2023/24/25, or the band of the rolling-refit series. If frozen: recompute the band on the rolling-refit series (arithmetic) and show both; say how many books change verdict (walk-forward >= 0.58 and refit-series years inside the 15-30% band, null as landed).
3. The same rolling-refit series with a trailing 3-month pick window beside the 6-month one (Josh's standing rule says last 3-6 months), if the landed series allow it by arithmetic; if it needs engine runs give the cost only.
4. The 13 books whose shape won in both recent windows: one line each: own shape, today's pick, walk-forward share, refit-series $/wk and ulcer by year vs own, and which gate stopped it.
5. The 15% max-DD / worst-week guard that removed 10 of 23 books before the walk-forward: who added it and is it one of Josh's approved gates (18:10Z Nov 20: recent pick, walk-forward >= 58%, prior-year band, null >= 4/5)? If it is not his, show the 10 books' walk-forward results without it.
