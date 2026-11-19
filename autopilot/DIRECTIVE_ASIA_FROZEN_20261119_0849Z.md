# ORDER 20261119_0849Z: Asia cell counts frozen for 90 minutes; Frankfurt real pass-1 loop unconfirmed

Research ops only.

1. ASIA. The auto line shows "Asia cells with engine rows 212" at 07:35Z, 08:05Z AND 08:35Z, and REPLACE
   verdicts 95 -> 95 -> 100, while ~2,080 Asia set-months landed per hour (5,716 in 3 h). One ladder cell
   needs 12 stage-A lines, so 2,000 set-months/h should bring ~170 NEW cells per hour; 1,800 of 1,890 cells
   are still at stage A. Where are the Asia set-months going?
   a. Break the last 2 h of landed Asia set-months down by type: ladder stage A (new cells) / a2 REPLACE vs
      K7-P7-H7-U7 / stage B prior years / stage C controls / old AB-AX lines / anything else; and by cell
      (how many distinct cells).
   b. Is the 15-min reorder cron putting every appended a2 / prior-year / control line AHEAD of the stage-A
      lines of cells that have no verdict yet? The intended order (order 0400Z + 0633Z item 4): finish the
      follow-up rows of cells that already BEAT a live book first (few cells), then stage A for new cells
      in block-score / screen-rank order, then follow-ups of cells that are merely "not negative".
      Follow-ups of non-beating cells must not starve the first look at 1,800 untested cells.
   c. Or is it a counting bug in asia_beats.py (rows landed but not counted)? Count DONE stage-A cells
      directly: how many of the 1,890 have all 12 stage-A lines done.
   d. Fix, and write one line with the corrected counts and the new-cells-per-hour rate.
2. FRANKFURT REAL PASS 1. 07:44Z: "Frankfurt: no real pass-1 loop found ()"; no confirmation since; Frankfurt
   grid results 294-349 / 30 min; real pass-1 todo 2,315 at 08:05Z (2,074 at 07:05Z: not falling). Confirm
   the Frankfurt real loop runs with its 12-worker budget (pid, workers, real results in the last 10 min),
   real jobs left per host, the end time of real pass 1 and of the stale-family REAL re-run.
3. One LEAD NOTE answering 1 and 2.
