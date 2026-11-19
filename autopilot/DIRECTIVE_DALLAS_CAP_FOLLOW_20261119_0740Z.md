# ORDER 20261119_0740Z: the Dallas cap-follower is undoing the engine cap

Research ops only.

S2-CAP-FOLLOW lowered the Dallas engine cap 28 -> 24 (07:10Z) -> 20 (07:25Z) because "grid results fell
while the host is busy". That rule predates tonight's priority order: stage-1 ENGINE is priority a and the
grid is below it, so grid results falling when the engine gets cores is the intended effect, not a reason
to give the cores back. Left alone it walks Dallas back to 12 and loses the measured +150% (180 -> 452
set-months/h at cap 28).

1. Set Dallas back to the measured best (28) and change the follower: it may lower the engine cap only on a
   SUCCESSFUL memory reading below the floor (same rule as mem_guard.py), never for grid throughput; it may
   raise it when memory allows. Same check for any other automatic rule that trades engine workers for grid
   results on box 1 / Frankfurt / Singapore.
2. So the grid cannot starve completely: give real pass 1 + the stale-family REAL re-run a small fixed core
   budget per host (e.g. 8-12 cores at high priority) until those two finish (2,074 real jobs were left at
   07:05Z and only 302 moved in an hour), then release it to the engine. Say when real pass 1 ends.
3. Same idea for the D8-candidate exit screen (1,859 of 4,557 NY AM cells at 06:54Z, ~30 cells per 20 min):
   screen FIRST the cells that already beat a live book (NY AM yes rows + the Asia cells beating A7) with a
   small fixed budget, so the first wave is not waiting on the screen; the rest follows in rank order.
4. One line with: caps per host now, engine set-months/h per host (lease-based), real pass 1 jobs left and
   end time, exit-screen cells done for the "beats live" set.
