# Josh-nypm-book-specs-for-D8 (information / plumbing, 2026-11-23 ~17:05Z)

Josh's words, verbatim (10:03 Mountain time = 17:03Z, 23 Nov):

> "we have no NY PM yet to code?"

Everything below is the relay's reading (relay = Claude, not typed by Josh). Information / plumbing only: no new tests, no gate or rule change. Same request as order 0212Z was for London and 2200Z for NY AM.

Context: the NY PM stack FINAL (equal weight, complete pool of 6) is L52359bf4.BRP30 + L8e0bf58c.BRS8U + L4bdd521a.BRF80_40 + L2c6916a5.BRP60. D8_BUILD_SPEC.md has only GENERIC AUTO blocks for them. The D8 NinjaTrader file now runs Asia (5 books + layers), NY AM (5 books + the 2-lot layer pick) and London (1 book); NY PM (12:00-16:00 ET) is the empty part of the day.

Please, with a small agent (almost no compute):

1. A hand-written AUTO:BOOK block for each of the four books: the BAR rule in full (kernel, threshold and its daily scale, reset rules, known time, part bars, which sessions the series is built for, whether the D8 _CANC print rule matters), the TRIGGER in full (every series, window, threshold, sign convention, edge rule, sides traded; for L8e0bf58c the anch_PDN_B25 anchor definition and the BRS8U bracket = what "S8U" means in points and how the unit is computed per day), the bracket in points (or the unit rule), the entry rule (order time, one position), the NY PM window and its session-end exit time, and any data beyond NQ trades (other symbols, depth, quotes) with how a live feed must supply it.
2. An independent re-implementation check per book against the engine events (matched / only-engine / only-mine).
3. Parity pages D8_PARITY_<book>_<td>.md for td 20261109 and 20261110 (Josh's NinjaTrader NQ tick export covers those two days; if a book has no signal on one of them, add the nearest earlier day with at least 2 signals): bars, signals, trades, INPUTS, per-day thresholds.
4. Say per book whether it can be reproduced from a NinjaTrader feed (NQ ticks with bid/ask, level-2 depth, 1-minute bars of other futures) or needs something NinjaTrader does not give (10-level cancel tape, MBO), so the port can ship a book OFF if it cannot be matched.
5. Dates: NY PM exit verdicts per book (queued 16:14Z), the NY PM bare all-layers joint and its keys / defaults pages (D8_LAYER_KEYS_NYPM.md, D8_LAYER_DEFAULTS_NYPM.md with the recommended basis for 2 lots per book), and the bare D7 NY PM yardstick rows.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
