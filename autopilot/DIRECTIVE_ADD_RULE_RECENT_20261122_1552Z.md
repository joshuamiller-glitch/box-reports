# Josh-add-rule-recent-basis (research order, relayed 2026-11-22 ~15:52Z)

Josh's words, verbatim (10:48 ET), in answer to the relay's question "re-run the stack search with adds judged on recent drawdown, prior years as the 15-30% band, for all sessions?":

> "yes recents should drive this"

Everything below is the relay's reading (relay = Claude, not typed by Josh).

1. (relay) ADD RULE BASIS. In the stack searches (equal-weight and weighted; adds, swaps and resizes), judge a candidate at EQUAL RECENT risk: the L6M basis of the standing selection rule (drawdown first: equal L6M ulcer, with the existing 15% L6M max-drawdown / worst-week guard), L3M shown beside. This replaces "equal worst-prior-year max drawdown" as the deciding basis. That prior-year basis came from the relay's 14:13Z weights order wording, not from Josh.

2. (relay) PRIOR YEARS = a check, not the picker. Apply them the way the standing rule already does for picks: each prior year not a disaster (the 15-30% band as you apply it elsewhere; say on the page exactly how you applied it and the numbers). A stack that fails the band is shown with its numbers, flagged, and not chosen. Controls (30 date-shift) reported as now.

3. (relay) SCOPE. Re-run on the COMPLETE pools: Asia now (80-book pool); NY AM on the same basis (provisional until its controls land, then final); London and NY PM use this basis from their first search. Keep the current-rule results on the pages as reference rows so the two bases can be read side by side.

4. (relay) WHAT DOES NOT CHANGE. Asia v1 build basis stays the pinned 5-book stack TL3_ALN_AS_STKd8106b26ef and its all-layers bare fit stays first in the queue. If the recent-basis search on the complete pool finds a stack that beats it (bare vs bare, drawdown first), report it with both side by side and start its bare all-layers fit as well; do not swap the pin without Josh. No gates for books change (a-d stay).

5. (relay) PLUMBING / INFORMATION for the D8 port (no new tests), as capacity allows and never ahead of items 1-4:
   a. Publish, daily in the mirror as .md, a start-up state seed per pinned book: the values the live code needs at session start to match your engine without replaying history (for example: daily scale factors s_vol / s_n / s_rng, pivot lines, trailing medians "u", EMA/vsig state for L92a90948, sd window for L578701ed, RSI state and the ES/YM z-score state for J502).
   b. L92a90948: state the minimum periods for vsig and the exact definition of the edge (fires on a state flip only, or also on first valid bar).
   c. L578701ed: how a book snapshot with bid == ask, crossed, or empty levels is handled.
   d. The bare-fit identity DIFF at 2 and 4 lots on the J502 stream: cause in one or two lines.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
