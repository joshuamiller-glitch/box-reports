# BLIND_DEFECTS_ZL2 - live fills and data vs the engine assumptions (ZL-2, 2026-11-06; input: data/live/StratTrades_DS7_<acct>.csv sha256 d918fee4..., 187 trades, and the P2 1-s tables)
Reads only the live trade csv (seal 1ffc16d5 predates the file: logged 2026-11-06T00:50:57Z; the user delivered the file 15:59Z) and the P2 tables NQ/1s/2026-11__ext_20261101_20261105. Variant runs only; no sealed file touched. Code l2vast/ds3/code/blind/zl2_fills.py and zl2_fills_report.py. Times: live csv is ET wall clock (EST, DST ended 2026-11-01 02:00 ET, every trade is after it), converted with the tz database; table ts is the 1-s bin END, so the bin [x, x+1) carries ts x+1, and the book state at second x is row ts = x.
**Caveat on the live csv:** entryTime is a bar-aligned time for 149 of 187 trades (seconds = 00, the 1-min close); 38 have a true second (late slices / adds). pnlNet / (points x $20) equals qty on 177 trades; on 10 the P&L implies a different lot count than qty (see section 5). entryPx is the average over slices (decimals like .42/.63/.88).

## 1. Headline (what fills and data explain)
* Live net on the csv: $104,095 on 187 trades; sealed prediction +$34,879 on 182. P7 live +$86,010 on 53 vs predicted +$2,404 on 43 (BASE-4 leads that ranking). **Costs measured live are worse than the engine assumptions, not better**, so fills do not explain the positive gap; they make it larger:
  * ENTRY: on 120 live trades matched to a sealed trade (same book, side, entry within 3 s) the live average entry is 3.52 pt WORSE than the engine entry price (median 3.50), about $76 per lot, $19,780 on the matched trades, about $32,057 extrapolated to all 423 live lots. The cause is visible on the tape: engine entry prices are 3.4-5.3 pt BETTER than the touch at the engine entry second for K6/H6/M6/P6/U6 (A6 0.9, X-books 0), and the tape trades at/through the engine entry price only after a median 9 s (mean 50 s; K6 50 s, P6 50 s, U6 97 s) after entry_ts; the live first slice fills at the touch within the first second (114 of 136 timed fills), at the first print of the second on average (mean difference -0.01 pt).
  * CUT exits (ThL2Cut, PolicyCut, ThL2Trail, PolicyTake, BookLock; 99 exits, 212 lots): cost vs the mid at the cut second 1.18 pt (median 0.88) against the engine market-exit 0.80 pt: $1,926 adverse in total. Against the opposite touch the fill is only 0.57 pt worse; the rest is the half spread (0.61 pt).
  * STOPS: only 2 live stops (K7, M7) vs 7 sealed: K7 -83.00 pt, M7 -80.75 pt from entry. With a nominal 75-pt stop (the engine X3/X4 stop distance, 75 + 2.45 = 77.45; the nominal is INFERRED, not in the csv) the slippage is 8.0 pt (K7, JoinThenMarket 3 s) and 5.75 pt (M7) against 2.45: +$177 adverse. Tape check K7: price crossed 28147 about 6 s before the exit second and the fill was 28155.00 (the exit second's range 28149.75-28155.50): join phase did not fill in a rising market, then market. n = 2, no inference.
  * TARGETS fill at nominal: all 86 target exits are at entry +/- nominal (60.00 pt for A/H/K/M/P/U within 0.12, 90 for O7, 50.12 X3, 40 X4; mean deviation from the assumed nominal 0.00 pt); of the 85 with a printed exit second, 73 had the tape trade strictly through the level in that second, 12 only touched it. The engine assumption (targets resting at nominal) holds on the live fills.
  * Net: the fill-side differences are adverse (entry about -$32k extrapolated, cuts -$1.9k, stops -$0.2k), so the live P7 excess (+$86k vs +$2.4k) comes from trade selection / lots / exit mix, not from better fills (see the exit-mix table in section 4).

## 2. Entries (per book; minute-aligned entries, slippage > 0 = worse)
| book | n | lots | vs touch at the close second (pt) | vs mid (pt) | vs first print of next second (pt) | mean spread (pt) | share filled in the first second |
|--|--|--|--|--|--|--|--|
| A7 | 18 | 18 | +0.40 | +1.15 | +1.18 | 1.49 | 1.00 |
| H7 | 3 | 4 | -0.46 | -0.16 | +0.04 | 0.58 | 0.67 |
| K7 | 56 | 68 | -0.51 | +0.12 | +0.19 | 1.25 | 0.94 |
| M7 | 27 | 35 | -0.87 | -0.36 | -0.40 | 1.03 | 0.84 |
| O7 | 3 | 3 | -0.08 | +0.29 | +0.00 | 0.75 | 1.00 |
| P7 | 34 | 166 | -1.71 | -0.99 | -0.68 | 1.43 | 0.54 |
| U7 | 6 | 19 | -0.62 | -0.12 | +0.17 | 1.00 | 0.67 |
| X5 | 2 | 4 | +0.25 | +0.62 | -0.12 | 0.75 | 1.00 |
All minute-aligned entries (149): vs touch -0.72 pt (sd 2.26), vs mid -0.10, vs first print -0.01; timed first fill: second 0 114, second 1 11, later 11, not resolved 13 (average prices of multi-slice entries often lie inside no single second). The 38 entries with a true second in the csv: P7 19, K7 8, A7 5, X3 3, X4 2, M7 1 (late slices / adds).

### Engine vs live entry price, matched trades (live minus engine, adverse > 0)
| book | matched n | mean (pt) | median | $ per lot | $ total |
|--|--|--|--|--|--|
| A7 | 15 | +1.20 | +0.75 | 24 | 360 |
| K7 | 48 | +3.93 | +4.12 | 75 | 4,070 |
| M7 | 20 | +3.69 | +3.75 | 62 | 1,603 |
| P7 | 32 | +3.69 | +2.81 | 81 | 12,007 |
| U7 | 5 | +4.70 | +4.00 | 102 | 1,741 |
| all | 120 | +3.52 | +3.50 | 76 | 19,780 |
Engine side (sealed csv, 182 trades): entry price relative to the touch at the engine entry second (> 0 worse): A6 -0.90, H6 -4.37, K6 -3.40, M6 -4.70, P6 -5.32, U6 -5.04, X3 +0.12, X4 -0.38, X5 -0.25 pt. Matching rule is mine (book letter, side, entry within 3 s, one-to-one); BASE-4's per-trade match is the reference.

## 3. Exits by type (live; pt; cost vs mid = side x (mid at the exit second - fill), > 0 worse)
| exit type | n | lots | live $ | cost vs mid (pt) | vs opposite touch (pt) | spread at exit (pt) | engine assumption |
|--|--|--|--|--|--|--|--|
| BookLock | 3 | 7 | -1,340 | +0.88 | +0.42 | 0.92 | market 0.80 pt |
| PolicyCut | 39 | 96 | -66,880 | +1.40 | +0.71 | 1.38 | market 0.80 pt |
| PolicyTake | 2 | 3 | 2,605 | +1.12 | +0.75 | 0.75 | market 0.80 pt |
| Stop | 2 | 2 | -3,275 | +2.31 | +1.88 | 0.88 | nominal + 2.45 pt |
| Target | 86 | 209 | 245,410 | +nan | +nan | 1.09 | resting at nominal (0) |
| ThL2Cut | 53 | 104 | -73,470 | +1.05 | +0.48 | 1.14 | market 0.80 pt |
| ThL2Trail | 2 | 2 | 1,045 | +0.88 | +0.50 | 0.75 | market 0.80 pt |
(Target rows: cost vs mid is not meaningful, the order rests at nominal; fills at nominal on all 86.)

Cut cost by book (cost vs mid, pt; $ vs the 0.80 assumption):
| book | n | lots | cost vs mid | $ vs 0.80 |
|--|--|--|--|--|
| A7 | 16 | 16 | +1.16 | 114 |
| H7 | 2 | 3 | +0.06 | -33 |
| K7 | 32 | 39 | +1.13 | 356 |
| M7 | 14 | 19 | +1.04 | 61 |
| O7 | 2 | 2 | +5.00 | 168 |
| P7 | 25 | 111 | +1.27 | 1,206 |
| U7 | 3 | 12 | +1.25 | 148 |
| X3 | 2 | 4 | -0.44 | -99 |
| X4 | 1 | 2 | +1.88 | 43 |
| X5 | 2 | 4 | +0.31 | -39 |
| all | 99 | 212 | +1.18 | 1,926 |
Reading: cuts cost 1.18 pt on average against the mid (spread 1.21 pt, so about the touch +0.5 pt), versus 0.80 assumed: PolicyCut 1.40, ThL2Cut 1.05, ThL2Trail 0.88, PolicyTake 1.12, BookLock 0.88. The O7 cuts (2) cost 5.00 pt (thin). No cut exit filled better than the touch on average.

## 4. Exit mix, live vs sealed engine, by book (counts)
| book | live n | live target | live cuts (ThL2+Policy) | live stop/lock/other | live lots | live $ | sealed n | sealed target | sealed cuts | sealed stop/lock/other |
|--|--|--|--|--|--|--|--|--|--|--|
| P7 | 53 | 28 | 24 | 1 | 247 | 86,010 | 43 | 16 | 27 | 0 |
| K7 | 64 | 31 | 30 | 3 | 76 | 16,065 | 61 | 30 | 29 | 2 |
| M7 | 28 | 13 | 13 | 2 | 37 | 6,015 | 29 | 12 | 17 | 0 |
| A7 | 23 | 7 | 14 | 2 | 23 | -1,415 | 18 | 12 | 0 | 6 |
| H7 | 3 | 1 | 2 | 0 | 4 | -770 | 19 | 8 | 9 | 2 |
| U7 | 6 | 3 | 3 | 0 | 19 | -1,755 | 7 | 4 | 3 | 0 |
| X3 | 3 | 1 | 2 | 0 | 6 | -905 | 2 | 0 | 0 | 2 |
| X4 | 2 | 1 | 1 | 0 | 4 | -170 | 2 | 1 | 0 | 1 |
| X5 | 2 | 0 | 1 | 1 | 4 | 360 | 1 | 1 | 0 | 0 |
| O7 | 3 | 1 | 2 | 0 | 3 | 660 | 0 | 0 | 0 | 0 |
Target points per trade: live 60.00 for all books but O7/X3/X4; sealed engine target exits average A6 60.0, H6 62.4, K6 60.5, M6 61.8, P6 62.7, U6 63.6, X4 40.0, X5 60.0 pt (engine entry prices are better than the touch, so its target points exceed the 60-pt nominal).

## 5. Lots (qty) vs the engine
Matched trades: qty differs from the engine lots on 7 of 120 (mean -0.07); P7 matched lots 149 live vs 152 engine. Live total 423 lots on 187 trades (P7 247 on 53 = 4.66 avg; the engine P6 uses 3.0-5.0). **qty vs P&L inconsistency in the live csv: 10 trades whose pnlNet implies a different lot count than qty** (pnlNet / (points x $20)): K7 11-02 13:33 qty 1 implies 2.00 (Target); P7 11-03 10:46 qty 4 implies 3.00 (Target); P7 11-03 18:56 qty 4 implies 1.99 (PolicyCut); U7 11-04 00:00 qty 4 implies 2.00 (Target); P7 11-04 00:30 qty 7 implies 6.00 (Target); P7 11-04 00:53 qty 7 implies 4.92 (PolicyCut); M7 11-04 06:00 qty 1 implies 2.00 (ThL2Cut); P7 11-04 07:25 qty 5 implies 1.90 (BookLock); P7 11-05 02:53 qty 7 implies 6.00 (Target); P7 11-05 08:09 qty 4 implies 3.00 (PolicyCut). These look like partially filled or split slices (the average entryPx carries the slice mix); P&L, not qty, is the reliable figure. Net effect on the implied lot sum: K7 and M7 one lot above qty, P7 about 12 below (P7 qty 247, implied 235.2).

## 6. Data integrity flags (P2 tables, 2026-11-01T23:00Z -> 11-05T16:05Z)
| ET day | 1-s rows | book age median (s) | p95 | share age > 5 s |
|--|--|--|--|--|
| 11-01 | 21484 | 0.062 | 0.43 | 0.0000 |
| 11-02 | 83028 | 0.028 | 0.33 | 0.0000 |
| 11-03 | 82773 | 0.020 | 0.24 | 0.0000 |
| 11-04 | 82608 | 0.017 | 0.21 | 0.0000 |
| 11-05 | 39876 | 0.023 | 0.24 | 0.0000 |
* Book age at every live entry and exit second is below 2 s (0 of 187 entries, 0 of 187 exits stale); no live trade second is missing from the table (1 exit second row has no quote). 641 gaps > 1 s in the table, longest 2700 s (Monday 11-02 evening from about 17:45 ET; no live trade second falls inside a gap).
* 11-01 (Sunday evening): 8 minute-aligned entries; the first-second fill share is 0.38 against 0.57-0.86 on the other days (late fills on the thin Sunday open) and the exit costs vs mid that day are not representative (7 exits). The table itself is not degraded on 11-01 by age or record counts (age p95 0.44 s, nrec > 0 every second); whether the live MBP stream was degraded on 11-01 cannot be told from this table (it records the vendor stream, not the NT8 feed): the lead's degraded-stream flag stays unconfirmed by me.
* DST: ended 2026-11-01 02:00 ET; all live and table times are after it, EST (UTC-5) used throughout, no ambiguous or skipped hour in the sample; the engine label-day axis is unaffected. Instrument: one id in the table (NQZ6), no roll in the span.
* Time stamps: live entryTime is bar-aligned (the 1-min close), exitTime has the true second; the table bin end convention (+1 s) matters for every second-level comparison above (offset of +1 found by matching live prices to the bin prints: 80 of 187 first match at offset +1).

## 7. Limits (what this does not show)
* The nominal stop distance (75 pt) is inferred. The engine entry model details (70/30 split, OTE-62 resting add, 45-s PE confirmation) are in the config freeze; I compare average prices, not slice by slice, and the matching to sealed trades is mine. n = 2 for stops. The entry difference (3.5 pt) is a measured fact on 120 matched trades; its cause (engine limit-style average vs live market first slice) is read from the tape-wait numbers, not from the engine code.
