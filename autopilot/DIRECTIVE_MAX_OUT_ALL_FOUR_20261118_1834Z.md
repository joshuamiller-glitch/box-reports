# 1834Z — MAX OUT ALL FOUR MACHINES (Josh: "make sure they are MAXED out")

From: Josh's chat assistant (relay). Research ops only; no spend.

Josh's own facts from the Latitude dashboard: London box = 16 cores; Dallas (server 2) = 64 cores; Frankfurt (A) = 64 cores; Singapore (B) = 64 cores. 64 physical cores with hyper-threading = 128 threads on each of the three rs4 machines (you measured 128 on A and B). Server 2 has been run as "64 threads" since it was rented.

1. Confirm nproc on all four and write the real thread counts at the top of CORES.md (order 1830Z). CORES.md "busy %" must be measured against the REAL thread count of each machine (mpstat / /proc/stat idle), not against an assumed 64.
2. TARGET for every machine, around the clock: CPU busy >= 90% of ALL its threads (server 2, A, B: about 115-125 runnable workers each; box 1: its 32 threads), limited only by memory (keep the 40 GB floor on box 1). If hyper-threads give less than proportional speed, measure it once (jobs/hour at 64 vs 96 vs 120 workers on one machine) and run the count that gives the most jobs/hour, and say which.
3. Server 2 NOW: raise grid + engine + re-rank workers to its real capacity; update the cap follower range and the watchdog (trigger B = below 85% of REAL threads for 3 readings).
4. A and B: start partial work as soon as any usable slice of data has arrived (do not wait for the full 65-70 GB): copy the bar rows / feature stores in job order and release each row to the workers when it lands; report minutes-to-first-job for each. Use many parallel streams; B from whichever source measures fastest.
5. Box 1: as the parked engine queues drain, give its free cores to the grid (W-GRIDOPS 19:00Z proposal: do it).
6. Hourly line in MORNING.md and SEARCH_STATUS.md: per machine: threads, busy %, workers by type, jobs/hour; total jobs/hour; phase-1 ETA. Any machine below 85% for 3 readings with work pending = explain in one line and fix.
