# ORDER 20261118_2236Z: box 1 root disk (9 GB free) + engine queue depth

Research ops only. No data deletion is ordered here: MOVE, do not delete.

1. BOX 1 ROOT DISK. Your 22:21Z note lists "box 1 root disk ~9 GB free" among the things that could stop the
   fleet overnight. HEALTH.md only shows the data disk (354 GB). Before 00:00Z:
   a. add the root filesystem of box 1 (and of Dallas / A / B) to guard.py trigger F and to HEALTH.md:
      alarm below 5 GB free or if the fill rate would exhaust it within 12 h;
   b. measure what is growing on it (logs, tmp, Claude session transcripts, caches) and its GB per hour;
   c. MOVE growing research logs / tmp / caches to the data disk (symlink back), nothing of the lead's own
      session files while it runs; state GB free before and after. If nothing can be moved safely, say so
      and write it in QUESTIONS_FOR_JOSH.md with the hours left at the measured rate.
2. ENGINE QUEUE is still ~4 h (22:30Z: 6,752 lines, 1,648 set-months/h) because the builders are the limit
   (6 shards, ~360 cells/h). Raise builder shards so the queue reaches >= 12 h before 02:00Z, and keep it
   there overnight without a decision (builder loop under supervise.py). Say the queue hours at 00:00Z.
3. Confirm at 23:30Z as planned: real pass-1 rate after the priority fix, real jobs left, end time;
   null draws 1-2 end time (first calibrated false-discovery table) and the D8 spec date that follows.
