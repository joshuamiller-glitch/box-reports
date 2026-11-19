# ORDER 20261119_2025Z: stale exit results + three short checks

## 1. Exit-stage results produced while the exit hooks were being edited (W-FASTLADDER 20:13Z)
W-FASTLADDER found that the stored own-merit exit results (TL3_EXE_*_OM, DONE 19:49-19:51Z) do not match an exact re-run with the current code (row counts 886 vs 923, 899 vs 909, 608 vs 620, 728 vs 721), because xb_inject.py / ex_events.py / ex_ownmerit.py / xb2_flow.py were edited between 19:33Z and 19:53Z while those sets ran.
- List EVERY exit-stage result (any TL3_EXE_ set, any host) whose run started before the last edit of any hook file it loads. Do not rely on the 8 that were noticed.
- PARK those results (move, never delete) and re-run them on the frozen code. No number from a parked result may appear in D8_EXIT_SCREEN.md, engine_gain.csv, BEST_BOOKS or any verdict.
- Say whether the L01811caa result of 19:32Z ("fixed bracket has the lowest ulcer in every slot K7/P7/M7/H7") is affected. If yes, mark it withdrawn until re-run.
- Rule from now on: the exit hook files are FROZEN while exit sets are queued or running. A change = new file version + hash in DECISIONS.md + identity re-run before any production set uses it. Record the code hash in each result's metadata so a stale result can be detected by machine.
- Same check for the pass-2 hooks (p2_inject.py and friends) before any pass-2 production set runs.

## 2. Per-book exit picks (standing rule: nothing goes into D8 without the non-fixed exit run)
The own-merit exit stage runs two generic recipes per book because the screen pick was usable for 0 of 40 books (23 both-side books were screened long-only). Two generic recipes are not "the exit run" for a book.
- When does the both-side exit screen land? Give a time.
- Then every top-ranked book gets its OWN screened best exits run in the engine, across ALL built families (per-entry stops/targets, chandelier, bricks, swing/line trails, staged, time/latch, opposite-signal, order flow, stop-and-reverse), not only the two generic ones. State the recipes per book and the cost.
- Drawdown first when judging an exit; a fixed bracket winning is a valid result and is reported as such.

## 3. Box 1 engine slots 18/36 (20:00Z) and 22/36 (20:20Z) while busy = 100%
One line: what is using the other cores (pass-2 screens, hook identity runs, pushes to C/D, pulls)? Is box 1's own engine work or the result pull-back for the fleet slowed? Fleet rate went 5,588 (18:50Z) -> 5,284 (20:15Z). If box-1 side jobs are the cause, say what ends when; first looks must not slow.

## 4. Ranked follow-ups (W-ASIA 20:14Z: only 11 prior years + 1 control landed in an hour)
The weighted interleave (60% ranked / 20% exit / 20% stack) was applied 20:15Z. Report the measured landed rate per group for the first full hour, and the restated date for "top 50 per session have prior years + controls" with Server C at full cap and Server D joined. Servers C and D were rented for exactly this work.

Answer in MORNING.md. No change to first looks.
