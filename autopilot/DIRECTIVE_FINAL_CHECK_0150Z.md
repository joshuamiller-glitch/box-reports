# Order 0150Z Sun Nov 22 — FINAL CHECK before the relay drops — written by the relay (Claude), not typed by Josh
Information and plumbing only. No new test, no gate change. The relay loses its order channel at about 03:00Z and can only READ the mirror after that. Josh reads the relay's summaries on his phone through the night. Everything below must run with nobody sending orders.

1. NY AM POOL PICK-UP (W-COMBO). 10 NY AM books have passed (d) at new brackets (W-BRKT lines 23:48Z-01:34Z), but the 01:35Z chain status still says "NY: pool 9 (new-pool members 1), step-2 chosen 10". Asia shows 24 new-pool members of 33 passes. Say why NY AM passes are not entering the NY pool (gate a/b/c re-check in your gate? lag? a bug?) and fix it so they enter automatically like Asia. Same check for London and NY PM before their first passes arrive.

2. LOOP RESTARTS ON POOL CHANGE (W-COMBO). The pool grows every few minutes (47 -> 54 -> 59) and each change re-runs the loops. Confirm in one line each:
   a. a running pass is allowed to FINISH and post its FINAL before the re-run (equal AND weighted loops);
   b. the WEIGHTED loops (asia-own-w, asia-stay-w, started 23:29Z): which step are they on, which pool size, and when is the first weighted FINAL expected? "weighted 2" in the status line: 2 loops or 2 FINALs?
   c. post each FINAL reached on a not-yet-complete pool with the word PROVISIONAL and the pool size, so Josh has a number tonight; the last one on the complete pool is the real one.
   d. if re-running on every new book would keep a weighted pass from ever finishing before Asia wave 1 is empty (~03:30Z), re-run the weighted loops at most once an hour, or once when wave 1 is empty. Your call; say which.

3. FITS (W-LAYERS). The stack-rule + daily-stop fit registered the J502-alone FINAL at 01:02Z. Confirm it registers every later new-pool FINAL (equal and weighted, all four sessions) by itself, and that a PROVISIONAL final being replaced does not strand engine rows (stop feeding the replaced one; do not delete results).

4. SHARES (LEAD). Keep managing them by your own judgment all night: Asia pool first, NY AM second, then London, then NY PM. Old Dallas is at 68% and server D at 84% at 01:45Z: refill.

5. LIVENESS. Hourly LEAD NOTE, cron LEAD AUTO HOURLY, dead-daemon checks and the wake watchdog keep running. If a driver dies, restart it and post one line. If something cannot be fixed without Josh, post "LEAD TO JOSH: BLOCKED ..." with the one decision needed.

6. EVERY "LEAD TO JOSH" RESULT LINE TONIGHT, and the 13:00Z MORNING PAGE, in this plain form:
   a. passes per session (count, and a table: book, trigger, bar, bracket, L6M and L3M $/wk, max drawdown, 2023/2024/2025 $/wk, controls beaten). W-BRKT: the Asia pass lines print "maxDD None"; fill the real number.
   b. each stack FINAL per session, equal weight and weighted (members, sizes, L6M and L3M $/wk, ulcer, max drawdown, worst week, prior years, stack controls), BESIDE the truly bare D7 row for that session from BARE_D7_YARDSTICK.md, and scaled to the same max drawdown. Bare beside bare only: never fitted D7 beside bare D8.
   c. the fit verdicts so far (stack rules, daily profit/loss stop), with the truly bare reference row.
   d. state on every stack number whether it is truly bare (R0) or carries today's wrapper (R1), and whether it is 1-lot or the x4-lot weighted run.
   e. a short list of anything that stalled, died, or was re-run overnight, and what it cost.
   f. what is still running and when it lands.

7. Reply to this order with one line per item (1-6) so the relay can tell Josh it is all in place before the channel drops.
