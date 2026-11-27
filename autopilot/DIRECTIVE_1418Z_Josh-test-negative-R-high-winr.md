# Test the NEGATIVE-R, high-win-rate profile: small target, wide safety stop, active management (order from Josh, relayed)

Josh, 27 Nov 14:18Z, verbatim: "also neg R trades - super high winrate - like 10 pt target with 60-90 stops A but active management"

(relay) My reading and design. Research only. Third profile beside the big-target books and the order-book scalps (14:14Z). It fits the algo design directly: wide back-up stop, small objective, the management loop is what stops a loser becoming a full stop.

1. FIRST, THE PLAIN FACTS FROM DATA ALREADY ON HAND (hours, server C, no engine): for every live book's entries (and the Test 5 qualifier cells as the non-hindsight sample), from the 1-second paths: the share of trades that reach +5, +8, +10, +15, +20 points BEFORE going -30, -45, -60, -90 against; median time to reach it; what the losers looked like on the way (how far under water, how long) before the wide stop. Per book, session, year, L3M and L6M first. Break-even win rate for each target/stop pair at real costs is shown beside the actual win rate. This table alone says whether the profile is even possible on these entries.
2. THEN THE PROFILE ON THE EXACT ENGINE (MBO book, real costs: fee label $4.84 per lot round trip and the engine's own; pessimistic stop-fill label, which matters most here because the losses are the wide stops):
 a. plain: target 8 / 10 / 15 points, safety stop 60 / 90, no management (reference: shows the raw tail);
 b. with the management loop (loop A as it stands, then later versions): the loop's whole job is to get out of the trades that are not going to make the small target, well before the wide stop: time under water, failure to progress, book and flow turning, ES/leaders against;
 c. target as a resting LIMIT with honest queue position versus market-on-touch (at 10 points the fill method matters);
 d. re-entry rows L0-L3 (14:11Z), since a 10-point winner frees the book quickly: "compounded" winners is the intended behaviour, but only while the book's signal state persists;
 e. scale: 1, 2, 4, 6 lots.
3. JUDGING, DRAWDOWN FIRST AND THE TAIL IN FRONT: win rate; average win and average loss in points; the worst day, worst week, max DD and the largest single loss; longest losing run; income; how many full safety stops per month and what each cost; L3M and L6M first, by year; versus the same book with its live bracket + Trade Health. Random-entry null with the same exits (a 10-point target with a 75-point stop wins most of the time on ANY entry: the question is whether the books' entries beat random ones net of the tail). Say plainly whether the high win rate survives its own losers.
4. ORDER: item 1 now on server C for Asia and NY AM books first; item 2 behind the first loop-A replays on the exact engine. Second track; the algo build keeps its agents.
Post the item-1 table in a LEAD TO JOSH line as soon as it exists.
