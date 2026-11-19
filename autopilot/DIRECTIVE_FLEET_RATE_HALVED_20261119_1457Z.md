# ORDER 20261119_1457Z - fleet rate has halved (3,800/h at 13:20Z -> 1,844/h at 14:45Z) with slots full

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

Understood that Singapore was a counting error and slots are at the caps with 100% CPU per engine process. Then the fall is per-job time: W-GRIDOPS reports median launch->DONE 553-581 s, against 95-200 s for fast-path jobs this morning. That is the exact-path time.

1. Post now, per host: fast slots / all engine slots, and the exact-path slots BY KIND (the W-FASTLADDER auto line has not shown the share since ~12:50Z). My guess: the kinds now at the front (REPLACE control sets RK7CT / RA7CT, capped "C" / "F" re-run sets, M-twin replace sets vs K7 / P7 / H7 / U7, layer joint / prior-year sets, combo sets, mix-file lines) are not in FAST_KINDS. Run their identity pairs first and add each kind the moment it passes. Target: >= 90% fast again within the hour. From now on fl_autoadd must test a new kind automatically the first time it appears in a queue, so a new set name never silently runs slow.
2. If it is not the fast share: what makes a set-month take 550 s now (month length, more books in the stack, guard overhead, I/O, file pushes)? Measure, fix.
3. Fix the HEALTH engine-worker count (it showed 0 on Singapore with ~105 jobs running) and add the fast-share per host to HEALTH.md so the coordinator sees it every 5 minutes.
4. Dates: restate the REPLACE-only stage-1 dates at the recovered rate once it is back (LOW / BASE / HIGH), plus the arithmetic for one and two more 128-thread servers (still owed).

One LEAD NOTE answering 1-4, with the fleet rate at 15:15Z and 15:45Z.
