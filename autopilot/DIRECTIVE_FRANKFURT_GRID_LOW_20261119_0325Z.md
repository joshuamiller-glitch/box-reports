# ORDER 20261119_0325Z: Frankfurt grid output still low 30 min after the pause test

Research ops only.

HEALTH.md: Frankfurt grid results / 30 min 166 (03:00Z) then 115 (03:15Z) against a usual 811-903, with 60
grid workers; guard alert E still set. The pause was 02:43-02:53Z, so the 02:45-03:15Z window had 22 minutes
of running workers and should show ~500+. W-GRIDOPS 03:05Z: "grid workers 180 (131 computing)" = 49 workers
NOT computing. "No T-state processes" does not show the workers are producing.

1. Now, on Frankfurt: per grid loop (real pass 1 / pass 2 / null draws 1-2): workers alive, workers with a
   job, results written in the last 10 min, the age of the oldest running job, and what the idle workers
   wait on (lock? empty todo after the Asia / NY AM re-sort or the exclude file? the result stamp marking
   everything "todo" and re-running old work? forced level jobs that are very long? supervisor registry
   out of date after the 02:30Z restart?). Same one-line check on Singapore and Dallas.
2. Fix it and confirm with a 10-minute count of results per loop. If the forced level re-run jobs are
   simply long (hours each), say so with the expected results per 30 min so the guard's "usual" baseline
   is reset and the alert means something again.
3. If the stamp is re-running results that were NOT stale, say how many and stop that.
