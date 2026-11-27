# DESK MANAGER v0.2: a professional retail desk's trade management, written down (RESEARCH order)

Josh, typed 20:22Z 27 Nov, verbatim:

> lets wait for saturday/ come
> up with a retail professional desk management system

(relay) "wait for saturday" = his decision on which books to cut waits for Saturday's page. The design below is written by the relay (Claude), not typed by Josh; he is reading it now and may mark it up (v0.3). It REPLACES playbook v0.1 as the fourth design. v0.1 rows already finished stay, labelled v0.1; unstarted v0.1 rows are voided and requeued as v0.2 (log it as a design change made before any v0.1 result was read by the relay: none has been reported). Replay ONCE as written; same test method as the 17:23Z order (replay, same trade two ways, tape review, scorecard). Where a number is not given, choose ONE sensible value in the book's or instrument's own units, write it in PLAYBOOK.md, never vary it.

## 1. What today's findings changed
- Outside markets rarely LEAD NQ (WHAT_MOVES_NQ): so screens are used for CONFIRMATION and DIVERGENCE (is the rest of the market agreeing with this move or refusing it), never as a prediction of the next tick.
- NQ's own book turns first in Asia / London: it gets the first vote there.
- Blind protection rules lose because the slot refills: STAND-DOWN after an exit is part of the system, not an add-on.

## 2. The desk: six seats, each gives WITH / AGAINST / NOTHING on the open trade
S1 PRICE: NQ's own structure (swing highs / lows since entry, VWAP, session levels) and pace.
S2 TAPE: NQ book and tape (absorption, pulled size, imbalance flip, liquidity wall ahead). First vote in Asia / London.
S3 INDEX COMPLEX: ES, RTY, YM (+ NKD overnight), cash ^NDX; NY hours add breadth: ^TICK, ^TICKQ, ^ADD, ^UVOL vs ^DVOL.
S4 LEADERS: the eight megacaps, QQQ, SPY (NY hours only).
S5 MACRO / FEAR: ZN, ZB, 6J, 6E, CL, GC; ^VIX, ^PCR.
S6 OPTIONS / CLOCK: option walls and flow; the calendar; minutes to the bell.
Seats with no data in a session or period ABSTAIN (say which). A stale feed abstains. If fewer than three seats can vote, the manager falls back to S1 + the never-bend rules only.
CONVICTION = seats WITH minus seats AGAINST. Four postures: PRESS (>= +2), NORMAL (-1..+1), DEFEND (<= -2), ABORT (all voting seats AGAINST, or S1 and S2 both AGAINST with nobody WITH).

## 3. The trade's states
ENTRY GATE (before the order): (a) time left to the bell must exceed this book's median winner holding time, else skip (late-entry rule, already positive on the exact engine); (b) no entry inside the calendar blackout around a top-tier release; (c) STAND-DOWN: after any exit of this book that was not a full target-style win, no new same-direction entry until price trades back through the exit level or 15 minutes pass.
PROBATION (from fill until up one unit; unit = the book's own stop distance x 0.25): safety stop at the broker (book stop x 1.5). DEFEND -> take half. ABORT -> out. A dip with NORMAL or PRESS -> hold.
FREE TRADE (up 2 units): stop to entry. From here it cannot lose.
RUNNER (after FREE TRADE): no target. Trail by STRUCTURE: behind the last confirmed swing against the trade (S1), never looser than giving back half of the peak. PRESS -> trail stays on structure and may skip one swing. NORMAL -> structure. DEFEND -> take a third (once), trail to the nearest swing. ABORT or DIVERGENCE (NQ makes a new best while S3 breadth and S4 leaders do not) -> take all.
OBJECTIVES (any state, in profit): stall (no new best for 3x the time the last unit took) / prior high-low / round number / option wall or liquidity wall just ahead (S2, S6) / session range used up -> take half at the first objective, all at the second, all at once if posture is DEFEND.
CLOCK: if the distance still wanted exceeds what NQ normally covers in the minutes left -> take it now; never carry open profit into a forced close; tighten to structure 2 minutes before a top-tier release.

## 4. Never bend
(i) a trade that reached the old target distance x 0.9 never becomes a loss; (ii) never give back more than half of a peak of 2 units or more; (iii) broker safety stop always live; (iv) the manager can only reduce risk: it never adds size and never widens the safety stop.

## 5. The desk's risk seat (above the trader)
Per book per session: after two managed exits at a loss in a row, that book stands down for the session. Per session: existing daily caps unchanged. Report these two as separate rows (with / without) so their effect is visible.

## 6. Deliverables
PLAYBOOK.md updated to v0.2 with every chosen number; replays (NY AM and Asia edge books first; then the exact-confirmed replacement books for NY PM / Asia); same-trade-two-ways counts incl. slot effects; scorecard; MGMT_TAPE_REVIEW.md showing the state, posture and seat votes at every decision. Shadow-log line: time, book, state, posture, votes S1..S6, action, price.
