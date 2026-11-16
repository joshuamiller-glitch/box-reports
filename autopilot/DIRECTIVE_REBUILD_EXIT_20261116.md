INBOX ORDER 20261116_2017Z_rebuild-addendum3-exit-confluence (research only)
ADDENDUM 3 to T-REBUILD: EXIT CONFLUENCE. Server 2. Same validation
standard as orders 1954Z and 2000Z (trial ledger, percentile controls,
PBO for anything fitted, resampled drawdown).

So far every condition in the library was read ONCE, at the entry second.
Exits were tested only as single fixed rules (give-back, partial, trail,
target change). Nothing has asked: while a trade is open, do several
things lining up say "get out" or "stay in"? Build that.

A. IN-TRADE STATE, once per closed minute (and per 5 s for flow items) for
   every trade of every book on the RAW base (stage 0) and on JL2:
   1. trade path: open profit in points and in R, best so far, worst so
      far, give-back from best, minutes in trade, minutes since the best,
      distance to stop / target / nearest structure level
   2. the same readings used at entry, RE-READ now, signed with the trade:
      day-direction vote, session VWAP side, squeeze state and whether it
      fired with or against, atr_rel, range used vs forecast, RSI/CCI
      zone relative to the trade, MACD histogram sign and slope
   3. flow: aggressor delta against the trade, own-side support pulled,
      wall ahead, tape speed and acceleration, L3 arrival imbalance
   4. other markets: ES / RTY / NKD / ZN move over 1, 5, 15 min relative
      to the trade; the T-ALPHA forecast sign and strength now
   5. what changed since entry: each entry reading that has FLIPPED
      against the trade (count of flips = the exit confluence count)

B. LABEL: at each in-trade minute, the remaining result of the trade from
   that minute to its real exit (points and R), and whether exiting now
   would have been better. No look-ahead in the features.

C. THREE TESTS, per book x session and per book:
   1. single in-trade conditions: effect on remaining R, vs nonsense and
      shifted-label controls;
   2. EXIT CONFLUENCE COUNT: remaining R by the number of independent
      clusters now against the trade (0, 1, 2, 3, 4+), with the same
      count built from nonsense items beside it. Is it a staircase?
   3. ONE EXIT SCORE per book (regularised linear, then boosted as a
      check), walk-forward (trailing 26 weeks -> next 2), predicting
      remaining R. Actions by score: hold / tighten stop to breakeven or
      to a trail / take half / exit. Separate thresholds for a trade in
      profit and a trade in loss.

D. ENGINE VERDICT: the best exit score per book on the exact engine, all
   windows, against (a) JL2 as is, (b) a random-exit control with the
   same share of early exits and the same minutes-since-entry and open-
   profit distribution, (c) the simple give-back rule. Then jointly with
   the stage 2 entry score and the loss cuts (stage 3).

E. Report separately for winners that gave it back, losers that never
   went green, and trades cut by the current loss lines: which group the
   score helps. Also the HOLD path 2025-11-17..12-10 alone.

Page DS3_REBUILD_EXIT.md. Build A and B first (they feed everything
else); C1 and C2 table by 12:00Z 11-17.
