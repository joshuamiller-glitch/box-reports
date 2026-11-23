# Bug report: D8_TIME_WINDOWS.md, Asia windows after midnight ET
**Written by the relay (Claude), not typed by Josh. Plumbing only: no new test, no gate or rule change.**

On the Asia tables (unit ALL and per book) the four windows after midnight ET remove almost the whole session instead of 30 minutes:
- 00:00-00:30 removes 2,230 trades of the L6M (all of them: $/wk 0, maxDD 0), verdict printed PASS;
- 00:30-01:00 removes 2,016, 01:00-01:30 removes 1,888, 01:30-02:00 removes 1,741.
The evening windows remove 50-140 each, which is the plausible size. So the block test for windows on the far side of midnight looks wrong (wrap of the ET minute-of-day, or a state that never clears once set), and a "PASS" on a row that removed every trade must not be read as a result.

Please (W-TW):
1. Find and fix it (say what it was), re-run those four windows for Asia (stack + per book, L6M and prior years), and check no other session's rows are affected.
2. Add a guard to the scorer: a window that removes more than, say, 40% of the trades of a 30-minute block is flagged CHECK, never PASS.
3. Mark the four rows "BROKEN, re-running" on the page until fixed.
4. Note on the page that the NY PM tables are on the bare base and will be re-scored on BF2_JT209.

The relay has told Josh the after-midnight Asia rows are not to be trusted and has relayed only the other rows.
