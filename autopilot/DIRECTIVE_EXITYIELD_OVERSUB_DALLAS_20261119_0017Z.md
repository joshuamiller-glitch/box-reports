# ORDER 20261119_0017Z: exit-yield sample to 150 pairs; A / B oversubscription; Dallas grid queue

Research ops only.

1. EXIT YIELD: 88 pairs at 00:10Z (74 at 23:03Z = ~14 pairs/h at nice 15). Josh's decision on a full exit run
   waits for the >= 150-pair read. Give W-EXITYIELD enough share (e.g. nice 8, same level as pass 2 + exits,
   or 16 dedicated cores on Dallas) to reach 150 pairs by ~02:30Z, then put it back to nice 15. Post the
   section-a table and the recommendation line in one LEAD NOTE when 150 is reached, per session, with the
   null/real ratios, and the core-hours of a full exit run for (i) NY AM + Asia only, (ii) all four sessions.
   The FULL run still does not start without Josh.
2. FRANKFURT / SINGAPORE run at load 280-325 on 128 threads; Frankfurt's engine does 57-69 set-months / 30 min
   against Singapore's 125-132 with the same 57 workers. Test for 30 min whether fewer grid workers on
   Frankfurt (e.g. 189 -> 120) raises TOTAL useful output (engine set-months + grid results weighted by your
   priority order); keep whichever setting produces more; log the two measurements.
3. DALLAS grid queue is 3.0-3.6 h on HEALTH.md for the last hour (rule: >= 12 h). Either refill it or, if
   HEALTH.md counts only "own rows" and the real depth is > 12 h, fix the HEALTH.md figure so the page is true.
4. W-NT2 near-target controls landed 0 set-months between 22:22Z and 23:24Z. Starved by priorities? Keep it
   moving enough to hold its 06:00Z (K7 table) and 12:00Z (controls) targets, or state the new times.
