# ORDER 20261119_0613Z: engine cap beyond 70; restated dates; guard alert G for W-NYENG / W-SHORT

Research ops only.

1. ENGINE CAP. 38 -> 54 -> 70 gave A + B 644 -> 924 -> 1,108 set-months/h with 1.2 TB free on both hosts.
   Real pass 1 is nearly drained (2,075 jobs at 06:05Z). Continue the measured steps: 70 -> 86 -> 102 on
   Frankfurt and Singapore (same script, 5 min ramp + 15 min measure, fixed memory guard, keep the best,
   stop below +5%). Then the same question for Dallas (cap 12 of 64 threads; 1 TB free): step 12 -> 20 -> 28
   and for box 1 within its memory floor. Stage-1 engine is priority a; the work it displaces (D8 exit
   screen, R3, pass 2, null draws, broad exits) keeps its order below it. Log one table: host, cap, engine
   set-months/h, per-worker rate, grid results / 30 min, D8-screen progress.
2. RESTATED DATES at the new fleet rate (2,722 set-months/h at 06:05Z and after step 1): Asia ladder stage 1,
   NY AM ladder, the combined Asia + NY AM engine end, the first date a candidate can be through everything
   (prior years, 30 controls, layers, exit-recipe engine rows), and the D8 spec date for (i) "first wave"
   = candidates through everything by then and (ii) the whole ladder. Put them on SEARCH_STATUS.md and in
   QUESTIONS_FOR_JOSH.md item 16.
3. GUARD ALERT G fired for W-NYENG (no line since 02:30Z) and W-SHORT (61 min at 05:40Z); the alert has
   cleared from HEALTH.md but no line says what was done. One line each: resumed / replaced / loops running
   without it, and whether D8_SPEC_STATUS.md, the NY AM beats page and the CALIBRATION deeper rungs are
   still being refreshed (time of last refresh). An alert that clears by its own rate limit without an
   answer is a hole: make G stay on HEALTH.md until the lead writes the answer line.
4. First Asia ladder verdicts: one line when the first REPLACE rows finish (how many beat A7 / K7 / P7 / H7 / U7
   under the Asia rule, best five rows with drawdown and dollars), even if the number is zero.
