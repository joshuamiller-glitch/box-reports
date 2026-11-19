# ORDER 20261119_0400Z: ASIA status now (Asia is FIRST in the sequence; nothing about it has been posted since 22:46Z)

Research only.

NY AM has a page, counts and dates (W-NYENG). Asia, the first session of stage 1 and Josh's main money
maker, has none: D8_SPEC_STATUS.md says "Asia = W-LONENG's rows", the D8 exit screen lists 0 Asia cells,
and the last W-LONENG line is 22:46Z (170 Asia + 8 lead cells queued, 9,391 lines).

1. One LEAD NOTE within 30 minutes + a page autopilot/NEW_BOOK_BEATS_LIVE_ASIA.md (same columns as the
   NY AM page, refreshed every 30 min):
   a. Asia cells with engine rows; REPLACE verdicts finished vs each live Asia book (P7, K7, U7, H7, A7);
      how many beat the book they replace on L6M AND L3M under the Asia rule (drawdown first AND dollars);
      ADD rows beside; pending; the best five rows with their numbers.
   b. Asia set-months landed in the last 1 h and 3 h, Asia lines pending, and proof that Asia sets are
      launched ahead of NY AM on every machine (QUEUES.txt order + what the dispatchers actually took).
   c. Is W-LONENG alive and its cron (lx_prog.py) running? It failed silently for 1.5 h earlier tonight.
      Put its loop under supervise.py and add it to guard trigger E (no Asia set-month for 60 min = alert).
2. Asia ladder: the NY ladder has 9,081 cells built by ny_ladder; the Asia list has 2,698 cells but only
   ~178 were queued. Queue the Asia ladder the same way (no cap; best screen rank / block score first;
   stale-family cells after the re-run), ahead of the NY AM ladder tail.
3. Asia candidates into D8_CANDIDATES.txt and the D8 exit screen as soon as their REPLACE rows exist.
4. The Asia date for the D8 spec, and the combined Asia + NY AM date.
