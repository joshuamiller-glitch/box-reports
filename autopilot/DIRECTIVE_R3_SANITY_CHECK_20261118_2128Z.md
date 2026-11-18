# ORDER 20261118_2128Z: R3 sanity check: NY AM stage A is BELOW the chance rate

Research only. Small job for W-SHORT; do not stop stage A for it.

## What I see (SURVIVOR_COUNTS.md, 21:25Z)
Under a pure-noise null a cell beats >= 24 of 30 draws 22.6% of the time (7/31), >= 27 12.9%, >= 29 6.5%.
- Asia, 472 family-bests: 30% / 10.6% / 1.5%.
- NY AM, 522 family-bests: 13% / 4.6% / 1.0%.
These cells were SELECTED for L6M > 0, and the null mean is negative (XA3: -6.8 R). They should sit well
ABOVE chance at >= 24, yet NY AM is at about half of chance and both sessions are far below chance at >= 29.
Either the table counts something other than what its label says, or the random draws are not a fair match.

## Check and report (one LEAD NOTE + a short section on SURVIVOR_COUNTS.md)
1. Which statistic do the "beat >= 24 / 27 / 29 on L6M" columns count, exactly (L6M sum of R, strict > or >=, ties)?
   Show the full histogram of beats (0..30) per session for the cells tested so far, beside the uniform expectation.
2. Is each draw a fair twin of the real cell: same costs / fill basis, same number of trades, same side mix,
   same session window and days, same one-position-at-a-time rule, same bracket AND the same stop clip in points?
   Does a draw get more market exposure than the real cell (e.g. the real trigger clusters trades, draws spread them)?
3. Real statistic and draw statistic computed by the same code path on the same data end date (the real R0 number
   comes from the grid; the draws from gr3bh.py): re-score 20 real cells through the draw code path and compare.
4. Order effects: are tested cells a random sample of family-bests or rank-ordered (which end first)?
5. If a mismatch is found: fix, say which results are void, re-run them. If none: say so plainly and explain
   why selected cells can sit below chance (state it as measured, not as a guess).
No pass set (SET 1 or SET 2) is to be called final until this check is logged.
