# Order 2005Z Sat Nov 21 — STANDING ORDER FOR TONIGHT. Josh's words quoted; the plan is written by the relay (Claude)

## Why
Josh is travelling. From about 03:00Z Sunday (8-9pm Mountain) the Mac relay is offline, so the relay can READ the mirror but can send NO orders, possibly until Sunday. Everything below must run by itself. Nobody waits for Josh or for the relay.

## Josh's words (verbatim, 19:55Z-19:58Z)
- "Great, around eight or 9 PM mountain time tonight. You will lose connection to the MacBook Pro as I'm traveling, but will check in once I get to the airport and throughout the night."
- "yes, but why are you waiting to do the fitting once we have all the top candidates?"
- "I meant once the top candidates come back you will start the fitting automatically correct?"
His "yes" answers the relay's request for three small runs: (1) a bare second look at the candidates rejected under the old setup, (2) the 1,168 Asia candidates that were never run, at all shapes from the start, (3) the D7 yardstick re-run truly bare.
Earlier today, still in force: "we cant fit until the brackets are set" (17:29Z); "great same with NY and london" (17:13Z); "whole fleet" bracket first look (16:28Z); truly bare first looks (16:31Z); "ii" stack-rule + daily-stop fit (15:08Z); "yes both" weights (14:13Z).

RELAY'S READING: fitting is not to wait for anyone. The moment a session's candidates have their brackets set and have passed the checks, the stacks are built and the fitting starts AUTOMATICALLY. Details below are the relay's; correct what is wrong for the code, say so on MORNING.md, and carry on.

## THE CHAIN, PER SESSION, FULLY AUTOMATIC (Asia first, then NY AM, then London, then NY PM)
1. Brackets: step 2a (bare first look at best shape) -> stage B (prior years) -> stage C (luck controls in waves with exact early stop; twins collapsed). No cap on survivors. A book that passes a+b+c+d on bare (R0) results at its shape is a POOL member at that shape.
2. Stacks, as soon as a session's stage C has finished for the books queued so far (do not wait for stragglers: re-run when later books pass): the loops on the new pool: equal-weight loops as reference rows AND the weighted loops (asia-own-w, asia-stay-w, ny-own-w; sizes 0.25 / 0.5 / 1 / 2; order 1416Z/1419Z) as the default. W-COMBO starts the -w loops itself when the first new-pool FINAL exists; no further word needed. Post each FINAL with weights, window table, persistence, controls, and BARE D7 at the same drawdown.
3. Fits, as soon as a stack FINAL exists on the new pool (lift the holds yourselves at that moment; this order is the word):
   a. The stack-rule + daily-stop fit (order 1510Z: StackCut, BookLock, per-book daily caps, whole-stack daily profit/loss stops, sizer, entry-gate rows; R0 and R1 reference rows; lot-neutral; joint stage; Josh's four gates; lot check) on every distinct stack FINAL of the session (weighted final first, then equal-weight / stay variants).
   b. Per-book fits (layers, exits, pass 2; the bracket is already set by step 2) through the pool watchers: release books with combo_fithold.release in THIS ORDER so fleet time goes where it matters: members of any stack FINAL first, then pool books that were tried in an add round, then the rest of the pool by L6M $/wk per unit of ulcer. This is ordering, not a cap: everything gets fitted eventually.
   c. Stage 2 / stage 3 of the three-stage fit as already defined (re-pick, joint), per stack.
4. When a session's chain completes, W-D8SPEC writes/refreshes D8_BUILD_SPEC.md for that session: the stack options with weights, each book's bar / trigger / bracket, the fitted stack rules and daily stops in lot-neutral form, NT8 computability and open items. Nothing is frozen without Josh: options are kept side by side.

## THE THREE RUNS JOSH APPROVED ("yes")
5. Truly bare D7 yardstick (~3,774 set-months): run now, head of queue; BARE_D7_YARDSTICK.md gets R0 rows beside today's; every D8 vs D7 line from now on uses truly bare vs truly bare.
6. The 1,168 Asia cells that never had a new-book base: 17-shape grid first look (grid hosts' spare share; do NOT pause the engine fleet for it), then the bare engine chain (steps 1-3 above) for the positives. Queue position: right after Asia stage C, ahead of London.
7. Bare second look at candidates rejected under the old wrapper (1,173 with a landed first look): only for cells NOT already re-looked bare by step 2 at a new shape (say how many remain); 6 months bare at their old bracket and at their best grid shape; passers join the chain. Behind item 6.

## RULES FOR THE NIGHT
8. No gate, rule or definition changes. No caps on survivors. No data deleted (move/park only). Nothing on the execution server or any live chart. No spend, no new machines. Paste-only items stay parked for Josh.
9. Where a choice is needed and no order covers it: take the option that caps nothing, re-runs nothing already valid and wastes the least fleet time; write one line "LEAD DECISION (night): ..." on MORNING.md and add it to QUESTIONS_FOR_JOSH.md. Do not stop the chain to ask.
10. Machines full at all times. Queue priority: Asia chain > NY AM chain > London chain > NY PM chain > items 6-7 (as placed above) > NY D8 tail > everything else. If the head of the queue is empty, the next class runs at once.
11. Self-recovery as already drilled (NIGHT_PROOF.md). The lead wakes the specialists (they are idle until messaged): at least every 30 minutes check every step-2 daemon, loop and watcher by explicit pid and restart any that died; no pattern kills. Do not edit mf_multi.py or other engine files while lin-mode / R0 rows are in flight unless a result would otherwise be wrong; if you must, say what was re-run.
12. REPORTING (the relay reads only the mirror tonight): keep the mirror pushing every 5 minutes; post "LEAD TO JOSH" lines in plain words at each milestone: session pool complete (count, top 10 with bar / trigger / shape / L6M and L3M $/wk / ulcer / max DD / prior years / controls); each new stack FINAL; each fit verdict; anything that failed and what was done. One hourly LEAD NOTE with: stage per session, set-months left per stage, expected finish times, fleet rate, anything stalled. A morning page at 13:00Z Sunday.
13. First thing now: post the plan for tonight in 8 lines (stage, owner, set-months, finish time per session) and name anything in this order that cannot run automatically, so it can be fixed while the relay can still send orders (until about 02:30Z).
