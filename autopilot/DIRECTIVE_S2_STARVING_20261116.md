INBOX ORDER 20261116_2134Z_server2-is-starving (research only) - URGENT

CORES.md shows server 2 underused for 20+ minutes with about 2,800 jobs
pending, at $5.44/hour:
 21:10Z-21:15Z 41% busy, 71 workers
 21:20Z        65% busy,  9 workers
 21:25Z        30% busy, 34 workers   (WARNING x4)
It was at 100% / 96-98 workers until 21:05Z, so something changed at the
21:00Z quota switch or when pc_front was put first.

1. Find the cause now and write it in the lead log: the server-2
   dispatcher starved by a queue whose lines are not eligible there
   (months or extended-store sets not on server 2, e.g. 202611+ or
   ev_store_launch sets), a queue that ran dry at the front, the puller
   or dispatcher stalled, or pc_front waiting on calibration.
2. Fix: the server-2 dispatcher must NEVER wait on an ineligible or empty
   front queue. If the front queue has no line it can run right now, it
   takes from the next queue in the standing order immediately, and keeps
   96 workers busy. T-REBUILD stage 0 / stage 5 and the stage 1 library
   are the bottomless fill: thousands of eligible lines.
3. Copy to server 2 whatever is missing for the queues that matter
   (extended store for 202511..202611, ev_store_launch inputs, JL2
   reference sets), so JOINT-EXIT, FLAT vs BOOK and the pass-rule draws
   can run there.
4. Add to cores_meter.py: when the server-2 WARNING fires twice in a row,
   run the fill-from-next-queue step automatically and log it. The lead
   should not be needed for this.
5. Report in the lead log: cause, fix, and the CORES.md line showing
   server 2 back at 85%+ with 96 workers.
