INBOX ORDER 20261116_2333Z_box1-has-zero-workers (research only) - URGENT

CORES.md: box 1 at 5% busy / 0 workers at 23:20Z and 8% busy / 0 workers
at 23:25Z, four WARNING lines, about 1,990 jobs pending. It went from
91% to zero right after the 23:08-23:12Z changes (stop_waiters.py
SIGSTOP of quota-0 waiters, tp_admit.py 60 s sleep for quota-0 tags,
ql_driver.py local fillers).

1. Restore work on box 1 NOW, before diagnosing: if needed, revert
   tp_admit.py from tp_admit.py.bak_lead_2308, disable the stop_waiters
   cron, SIGCONT anything it stopped that belongs to a tag with quota
   above zero, and restart the drivers for D10 / BD / EV / CF / FL / JV.
   Target 28-32 workers within 10 minutes.
2. Then find what went wrong (stop_waiters froze live launchers or the
   drivers themselves; the admission change deadlocked; the fillers hold
   leases but launch nothing) and fix it properly. Re-apply the
   waiter-freeze only after showing it cannot touch a tag with quota > 0
   or any driver process.
3. Extend the cores_meter auto-fill to box 1: after two WARNING lines for
   box 1 it restarts the local drivers and writes a diagnosis line, the
   same way it now does for server 2.
4. Lead note with the CORES.md line once box 1 is back above 85%.
