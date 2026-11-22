# london-nypm-stack-loops-see-no-books (plumbing, 2026-11-22 ~22:05Z)

Written by the relay (Claude), not typed by Josh. Plumbing only: no new tests, no gate or rule change.

What the mirror shows at 22:00Z:
- W-BRKT has posted books passing a+b+c+d truly bare at a new bracket: London 4 (Lc78f2492, L19201dfc, L12842dde, L74274eca), NY PM 6 (first three: L8e0bf58c, L2c6916a5, L8dff280f); NY PM pool complete flag set 21:16Z; London stage C drained 19:10Z.
- But the stack loops report nothing to work on: "RESELECT-LONDON [london-own] COUNTDOWN: pool 0 books ... HB step done/0, queued_or_running 0, last_progress 10:42Z" and the same for nypm-own / london-stay / nypm-stay (last_progress 10:43Z). The lead's own 19:32Z note says "London pool 1 book so far: no stack (needs 2+)" while W-BRKT lists 4.

Please:
1. Find why the London and NY PM loops do not see the bracket passers (pool feed file r0br_chosen_london / nypm not written, a pool-complete flag missing for London, a different pass definition between W-BRKT's (d) line and the loop's pool, or the loops finished at 10:42Z on an empty pool and never re-read it) and fix the wiring so both sessions' stack searches run on the full bracket-passer pools, on the recent basis of orders 1552Z + 1612Z (equal L6M ulcer + 15% guard, blocked only on a negative prior year or persistence < 0.58), equal and weighted.
2. Post one line per session with the pool size the loop now sees, and the first FINAL with its bare numbers (L6M / L3M / prior years, truly bare) beside the truly bare D7 yardstick of that session.
3. Say when London and NY PM will each have: pool complete, stack FINAL, exit run on the members, bare all-layers fit. Order of work stays Josh's: Asia and NY AM fits first, then London, then NY PM.
4. Add this case to the hourly cron check: a session with >= 2 posted bracket passers and a stack loop showing pool 0 for more than 30 minutes is flagged as STALLED.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
