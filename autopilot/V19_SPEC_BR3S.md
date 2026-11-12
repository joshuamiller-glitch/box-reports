# V19_SPEC_BR3S - code-level definition of WI_J_BR3S (breadth_ext15==3 skip) AS SCORED, and the difference to the user's v1.9 reading (W-I, 2026-11-12; Shadow only, no PASS)
Code: code/th_works_i/i_feat.py (functions ext_within = as scored, ext_strict = user reading), gate i_mixin.py (IGateMixin.trend_size). Sets: WI_J_BR3S (JN04RM base), WIL_J_BR3S (+ parts _A.._D, live panel base), WI_N_BR3S / WI_G_BR3S (stacked); user variants WIL_BR3S_V19 (all books) and WIL_BR3S_V19P (P7 only) on the live panel base.

## As scored, element by element
1. Books: P7 ONLY. The gate rule is {"books": ["P7"], "conds": [["breadth_ext15", "==", 3]], "act": "skip"}; K7, U7, M7, H7, A7, O7 are untouched. (User reading: all books: DIFFERENT.)
2. When it is evaluated: at the P7 signal second (inside trend_size, i.e. when the book is about to size an entry), from the last COMPLETED 1-min bar whose end (open + 60 s) is <= the signal second and not older than 15 minutes. If the signal side is unknown or no bar is usable the gate does not fire.
3. Price series and bar basis: 1-min OHLC bars of the continuous front contract of NQ, ES and RTY (bars1m files to 2026-10-16 plus the Databento ohlcv-1m extension to 2026-11-10, the stored continuous series (already roll-adjusted; my jump check found no further roll jump)). BAR based, not tick based: the session high (long) or low (short) is the running maximum of the bar HIGHS (minimum of the bar LOWS), not of prints and not of the current price. The current price / the forming bar is not included.
4. Session definition (the clock): six ET sessions on the bar OPEN time: Asia 18:00-02:00, London 02:00-08:30, pre 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00, close 15:00-18:00 (hm = HHMM in America/New_York); the session key = trading day (ET time + 6 h, so 18:00 ET starts the next trading day) x session index. A session starts at its first bar that exists in the data.
5. "New extreme" (as scored): the bar that holds the session's running high (low) -- the LATEST bar among ties -- ended within 15 minutes before the last completed bar (end[last] - end[extreme bar] <= 900 s). This includes (a) the FIRST bar of the session (if the session high is still the first bar's high it counts as the extreme), (b) ties (a bar that only equals the earlier high counts), (c) the last completed bar itself. In the first 15 minutes of a session the flag is therefore true almost by construction. In the 3,000 latest P7 signals 16 percent of the breadth-3 signals fall in the first 15 bars of their session.
6. Breadth: the count of {NQ, ES, RTY} for which (5) holds, in the trade direction (long = session high, short = session low); the gate skips the P7 signal when the count is 3. Skip = lots 0 (no order); no half variant was scored for BR3S, no change of bracket.
7. Not used: tick data, L2, other books' signals, ZN/6E/6J.

## The user's reading (V19) and what is the same or different
| element | user reading | as scored | same / different | change |
|--|--|--|--|--|
| each of NQ, ES, RTY | yes | yes | same | none |
| 1-min bar exceeds the earlier session high (long) / low (short) | strictly exceeds | running max including ties and the first bar | DIFFERENT | ext_strict: the last bar of the session whose high strictly exceeds every earlier bar of the session, within 15 min |
| within 15 minutes | yes | extreme bar ends within 900 s of the last completed bar | same | none |
| first bar of the session not counted | not counted | counted | DIFFERENT | ext_strict never counts bar 0 of the session |
| session clock | six-session clock | six-session clock (same) | same | none |
| session extreme includes current price | "plus the current price" | bars only | DIFFERENT (small) | not coded in V19; the 1-min bar boundary is the live decision granularity, price within the forming bar is ignored in both |
| books | all books | P7 only | DIFFERENT | V19 = all books; V19P = the user's strict reading on P7 only, to separate the two differences |
Agreement on the 3,000 latest P7 signals (breadth under each reading): scored 3 -> V19 3 in 892 of 1,003 (89 percent); 111 signals scored-3 are V19 < 3 (26 drop to 0, 28 to 1, 57 to 2); V19 never exceeds the scored value.

## Five worked rows (real P7 signals; N/E/R = NQ/ES/RTY flag; scored breadth | V19 breadth)
1. 2025-03-06 09:12Z short, London (session start 07:00Z, bar 131): scored 1/1/1 = 3, V19 1/1/1 = 3 -> both skip (actual P7 trade +$3,591, a winner removed).
2. 2025-03-20 23:28Z short, Asia (start 22:00Z, bar 87): scored 1/1/1 = 3, V19 1/1/0 = 2 -> scored skips, V19 trades (actual -$6,045).
3. 2025-07-14 22:16Z short, Asia (start 22:00Z, bar 15): scored 1/1/1 = 3, V19 0/1/1 = 2 -> scored skips (the NQ session low is the opening bar's), V19 trades (actual -$3,292).
4. 2025-03-14 11:04Z long, London (start 06:00Z, bar 303): scored 1/1/0 = 2, V19 1/1/0 = 2 -> both trade (actual +$2,403).
5. 2025-03-07 00:06Z long, Asia (start 2025-03-06 23:00Z, bar 65): scored 0/0/0 = 0, V19 0 -> both trade (actual -$3,289).
The frozen live week rows are in DS3_WORKS_I.md (5 real rows with the scored definition).

## V19 exact results (live panel base, vs LPB_BASE; L6M, HOLD)
To be filled by the exact runs WIL_BR3S_V19 (all books) and WIL_BR3S_V19P (P7 only); see the end of this file when written.
