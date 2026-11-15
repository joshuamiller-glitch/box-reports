## LAYERS: live loss-layer settings, overlap and best setting per layer (for W-CF3 BASIC_TESTS 2c/2d; W-LA, FIRST PASS 2026-11-15 ~19:00Z)
**One line: from the L3M and L6M cells done so far, the K7 state cut is the only loss layer where a different setting beats the live one in both windows (K7 arm +5 = 50: L3M +$2,354/wk, L6M +$344/wk at the $4.84 column, max DD -23.7% both windows, -9.1% with W44 removed); every other layer's live setting is not beaten yet, and the K7 gain is largely the one W44 week. FIRST PASS: only L3M+L6M, no older windows, no placebos, 13 and 26 weeks.**
Basis: JN05W2 at base lots (live x1.75), dollars per week, engine fee $1.18 (d_mean_484 repriced at $4.84), reference = JN05W2 (598 trades / 25,943.82 on 202610). Windows L3M = 13 weeks (mean 16,015/wk), L6M = 26 weeks.

### UPDATE 2026-11-15 ~20:00Z: K7 candidates under weekly-cluster test (L6M, 26 weeks; older windows queued, 37 more months each)
**The K7 arm-50 / persist-5 / state-cut-off gain is NOT distinguishable from noise: weekly-cluster t = 0.26 / 0.34 / 0.22, sign-flip p = 0.81 / 0.75 / 0.85, and with W44 removed the mean change is negative for arm 50 (-$177/wk) and off (-$81/wk); only persist 5 stays +$100/wk. Rank of the three among the 14 K7 grid cells (the placebo null = other K7 settings): arm 50 is #2 on mean, #1 on W44-removed DD; that rank is what a grid search of 14 settings gives by chance. Treat as NOT a lead.**
Which K7 setting the live port actually runs: the live K7 state line is persist 3 (pct <= -0.75 = 45 pts, pulled_mult >= 10, win 2, armlots v2) and it stayed SILENT live (open W-LB2 bug); the K7 flat -45 line (persist 1) fires. So live K7 protection behaves like the engine cell S_K7_NOCUT (flat -45 only), not like the engine base (state cut + flat). NOCUT vs engine base: +$1,319/wk L3M, +$308/wk L6M, but weekly t 0.22. Whichever the live bug turns out to be, the engine says the K7 state line adds nothing measurable beyond flat -45; fixing the live K7 persist is not where the value is.
File: /mnt/l2/l2vast/_deepen_la/a/k7_test.csv (code/th_deepen_la/la_k7_test.py).

### Live setting in JN05W2 (exact, from sets/JN05W2.json)
| layer | exact setting |
|--|--|
| state cut K7 | arm 45 pts, var 2 (arm x sqrt(lots/4), clip 15..50), mult 10, win 2 s, persist 3, newmae 0, all six sessions |
| state cut M7 | arm 30, var 0, mult 10, win 2, persist 2 |
| state cut U7 / A7 | U7 arm 30 var 2 mult 60 win 15 persist 5; A7 arm 30 var 0 mult 60 win 15 persist 3 |
| state cut H7 / O7 | H7 arm 15 mult 30 win 10 persist 2 newmae 1 var 1 (session 3: arm 35 mult 20 win 2 persist 1 var 2); O7 arm 25 mult 20 win 10 persist 10 |
| context cut (F3), P7 only | fresh 45 / 5x / win 5 / persist 10; rechase 30 / 10x / win 5 / persist 2 (replaces the P7 by-unit line); fresh = entry no. <= 2, not chasing (chase_k <= 1), >= 30 min since the book's last exit |
| flat cut | K7 only, -45 pts (mid, decision second r, exit mid(r+1) - 0.8) |
| WL_E1 | P7 only, sessions asia/london/nyam/nypm (0,1,3,4): skip the signal when same-side losers since last winner >= 2 and no new session extreme (noevid = 1) |
| C22 | stack-wide, all sessions: skip any new entry once day closes >= 22 AND day P&L <= -2 R (R = $1,200, i.e. -$2,400); label day, 17:00 ET roll |

### Overlap found (from my cells)
- K7 state cut vs K7 flat -45: they overlap. Removing the K7 state cut (S_K7_NOCUT) changes 11 cuts/week (52.5 -> 41.2 StateCut/wk) and is better in L3M (+$1,319/wk, DD -17.6%) and L6M (+$308/wk); with W44 removed DD changes only 1.8%. So the K7 state cut mostly duplicates flat -45 and costs a little; K7 persistence P1 -$1,220, P2 -$1,090 (worse), P3 base, P5 +$1,632 (L3M): the less often it fires, the better.
- WL_E1: raising to 3 losers (G3) cuts DD 16% but dd44 = 0 (the whole cut is the W44 week) but costs $609-989/wk; 1 loser (G1) is clearly worse (-$2,927/wk, DD +26%). Sessions: E1 in London only (SESS1) is nearly as good as base on mean (+$522 L3M, -$36 L6M) and keeps the same W44-only 16% DD cut (dd44 0); E1 in asia only is worse. Removing the noevid condition (NOEV0) is worse for DD (+23.7% worse with W44 out).
- C22: n=18 (+$994 L3M, +$203 L6M, DD cut 7.2%) and counting entries (C_ENT +$530/+$596, DD cut 6.1%) beat n=22 on mean but lose 10-12% DD with W44 removed; n=14, 26, 30 and per-session versions are worse; pnl_r -1.0..-1.5 do nothing for DD, -2.5..-3 neutral.
- Flat cuts at -40 per session: K7 asia (+$556/+$431, DD cut 21.5%, dd44 +6.5%) and K7 london (+$852/+$437, DD 11.9%, dd44 +12.6%) are the only positive ones; P7 and M7 flat -40 lose money. K7 NY PM flat -40 loses.
- Context cut / P7: NOCUT of the P7 state cut changes L3M by -$53 with DD +11% worse: the context cut earns its place at its current setting; none of the P7 arm/mult variants run so far beat it (see page sections 3-4 for rows as they land).
- Book-reading cut: detector identity PROVEN (XA_K7/P7/M7/U7_ANDID: net and drawdown identical to the engine cut, exits named LaXcut), so the XA book-reading and two-stage cells measure the condition, not the port.

### Best setting per layer so far (replacement, never empty)
| layer | best so far | status |
|--|--|--|
| K7 state cut | arm 45 -> 50 (S_K7_Ap5), else persist 5 (S_K7_P5) | candidate, W44-driven, needs HOLD/PRE/X' and placebo |
| K7 flat | -45 (live) stays; add session flat -40 in asia and london only if state cut is kept | open |
| other books' state cut | live | grid still running (P7, M7, U7, A7, H7 in the queue) |
| context cut (F3) | live | no variant yet beats it |
| WL_E1 | live (G2 + noevid); London-only is the cheaper fallback | open |
| C22 | live n=22 / -2R; n=18 is the only candidate | W44 says no |
Persistence-risk: K7 variants that need persist <= 2 are the worst ones (P1/P2 lose money in the engine), so no state-cut variant here depends on the persist=3-silent live fault; the best variants are LESS sensitive to the live persist problem than the live line.
Weekly delta series for W-RE: /mnt/l2/l2vast/_deepen_la/a/weekly_delta.csv (cell, win, week_id, net, ref, delta).
