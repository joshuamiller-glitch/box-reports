# The manager playbook (relay draft v0.1) and how it is tested (RESEARCH order)

Josh today, verbatim:
> (17:10Z) so having a million settings trying to work over long periods is not going to test well - the base books are what test well - it's hard to even find those - and then a smart trader is managing them in real time - this is what we don't have - i have no idea how the box is going to design the management system i'm asking for
> (17:12Z) but i wasn't looking at the 25 new indexs we just got or any stocks - that's what the manager will do - and other futures products - as if a retail trader had 8 screens like John Carter
> (17:14Z) and the issue is the box is backtesting - the backtesting has to be different somehow - we've already backtested and walked forward the entries - how do we do this?
> (17:15Z) we'll see about the shadow thing - code it so it can go shadow but i'll decide

Everything below is written by the relay (Claude), not typed by Josh. He has been shown the playbook draft and the test method and has NOT yet marked the playbook up; build the machinery now, expect a v0.2 with his edits. Your three designs (MGMT_DESIGN.md) keep running as the baseline.

## A. PLAYBOOK v0.1 (the fourth design; test it exactly as written)
EIGHT SCREENS, each gives one vote on the open trade: WITH / AGAINST / NOTHING. "Moved" = more than that instrument's own recent typical move (your 2-hour unit is fine).
1 NQ chart + clock. 2 NQ tape / book. 3 ES, RTY, YM. 4 ZN, ZB, 6E, 6J, CL, GC (+NKD overnight). 5 internals: ^TICK, ^TICKQ, ^ADD, ^UVOL vs ^DVOL. 6 ^VIX, ^PCR. 7 eight megacaps, QQQ, SPY, ^NDX. 8 options flow / walls + calendar.
A screen votes AGAINST when the majority of its members have moved against the trade (WITH likewise). Screens with no data in that session or period abstain; say which abstained.
LIFE OF A TRADE:
1. JUST IN: safety stop only. NQ dips and no other screen has moved -> hold. Most voting screens AGAINST before NQ follows -> take half; all voting screens AGAINST -> out.
2. WORKING (up one typical 5-minute NQ move x 2): stop to entry.
3. RUNNING: no target; trail behind best price. Screens WITH -> loose trail. Two screens AGAINST -> take a part (half) and tighten. Most screens AGAINST, or NQ makes a new best that internals AND leaders do not confirm -> take all.
4. AT AN OBJECTIVE: stall after most of the move (no new best for a time long relative to how fast it got there), or prior high / low, round number, option wall just ahead, or session range used up -> take it.
5. CLOCK: if the bell closes the trade in N minutes and the distance still wanted exceeds what NQ normally covers in N minutes -> take it now. Tighten or flat before a scheduled release.
6. AFTER EXIT: no re-entry of the same idea while the screens are still AGAINST it.
NEVER BEND: (i) a trade that got most of the way never becomes a full loss; (ii) never give back more than half of a meaningful peak; (iii) never carry open profit into a forced close.
Where a number is needed and not given above, choose ONE sensible value, write it in the page, and do not vary it.

## B. HOW IT IS TESTED (different from the entry search)
1. REPLAY, NOT SEARCH: one playbook, written first, run once over all 42 months on the exact engine. Nothing chosen from results, so the whole history is out of sample.
2. SAME TRADE TWO WAYS: every trade managed vs left on its own bracket. Report counts: big give-backs prevented, winners cut short, losers cut early, losers made worse, net $ and net by year; slot effects (extra entries after early exits) shown separately.
3. TAPE REVIEW (new deliverable, MGMT_TAPE_REVIEW.md): per session, the 20 worst give-backs, the 20 best runners, and 50 random trades: a short step-by-step of what the manager did, at what time, and which screens voted (one line per decision). Plain enough for Josh to read and say "a professional would / would not do that".
4. CHANGE DISCIPLINE: the playbook changes only when the tape review shows the LOGIC is wrong, never because another threshold scores better. Log every change with its reason.
5. Scorecard as in the 16:43Z order (smoothness first, income floors 10 / 20 / 30%).
6. SHADOW LOG: one line per decision in a fixed format; the relay codes Off / Shadow / Live per session in the next build and Josh decides which. Put the format in the page.
First: NY AM and Asia edge books. Say which screens have history on the box per session (abstainers).
