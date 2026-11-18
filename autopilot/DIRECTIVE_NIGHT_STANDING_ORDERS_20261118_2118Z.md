# 2118Z — NIGHT STANDING ORDERS: what to do with NO new order arriving (the order path depends on Josh's Mac; assume it can go dark)

From: Josh's chat assistant (relay). Research only; no spend; nothing touches the execution server, a live chart or credentials. Save this as ~/NIGHT_STANDING_ORDERS.md and make the level-3 restart line (order 2052Z) tell a restarted lead to read it. It stays in force every night until Josh replaces it. GitHub relay (2103Z): build the box side when convenient, but it is NOT available (the chat cannot write to GitHub from this session); do not wait for it.

IF NO ORDER ARRIVES FOR HOURS, THAT IS NORMAL. Keep going in this order, deciding yourself, logging each decision in MORNING.md with the reason:

A. KEEP ALL FOUR MACHINES ABOVE 90% of real threads. A machine idle with work existing anywhere is the one thing never acceptable. If a queue empties, pull from the next item below; never wait for an instruction.

B. THE PLAN (unchanged; details in the orders of 11-18: 1722Z, 1731Z, 1845Z, 1932Z, 2013Z, 2042Z):
   1. Phase 1: finish pass 1, pass 2 and the exit recipes for all four sessions, with the own-stop and current-stack-mask versions.
   2. Ladder, no cap, a cell leaves only by failing: R0 bare rule -> R1 own-stop rule -> R2 trust + look-ahead -> R3 per-cell random-entry p-values (30 -> 200 -> 1,000 draws) with Benjamini-Hochberg per session at q = 10% -> R5 engine staged (last 6 + 3 months add / replace -> prior years -> 30 date-shift controls). Whole-search null: 5 draws at about 25% of A and B, as a check.
   3. Phase 3 for every book that clears R5: its own layers (fast replay to narrow settings, exact engine for every verdict), then jointly; sessions DECIDED in clock order Asia -> London -> NY AM -> NY PM, day-state rebuilt after each; Asia can be replaced, with the higher bar.
   4. Phase 4: autopilot/D8_BUILD_SPEC.md, one block per book that is BUILD-READY, updated whenever a book qualifies. Target: a first complete spec for whatever has qualified by Saturday 11-21 12:00Z.
   5. Side jobs at low priority: exit-yield sample (EXIT_YIELD.md; do NOT start a full exit run - Josh decides), near-target K7 lock controls, ORB controls.

C. WHEN SOMETHING BREAKS: fix it and log cause and fix. If a fix needs a restart of a loop or a host process, do it (explicit pids). Do NOT: reboot a server, delete data (beyond what Josh already approved), rent or release anything, change any standard, or touch anything outside research.

D. WHEN A DECISION IS REALLY JOSH'S (spend, a full exit run, dropping a standard, deleting data): do not stop the fleet for it. Write the question at the top of autopilot/QUESTIONS_FOR_JOSH.md with your recommended default, apply the safe default (the one that keeps every standard and spends nothing), and carry on.

E. EVERY HOUR: one LEAD NOTE: machines busy %, what each is running, what landed, what is next, queue hours left per machine. Every morning by 12:30Z: autopilot/MORNING_SUMMARY.md in plain words: what was found overnight, what failed and why, the ladder counts per session, the D8 spec status, and the questions for Josh.
