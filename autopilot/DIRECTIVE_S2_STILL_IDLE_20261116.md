INBOX ORDER 20261116_2151Z_server2-still-idle (research only) - URGENT, second notice

CORES.md 21:30Z and 21:35Z: server 2 at 24% and 19% busy, 14 and 12
workers, six WARNING lines in a row, about 2,700 jobs pending. That is
40 minutes of a 64-core machine mostly idle. Order 2134Z is acknowledged
but no action is logged.

Do this before anything else:
1. Point the server-2 dispatcher at T-REBUILD stage 0, stage 5 and the
   stage 1 library NOW (lines whose months are on server 2), 96 workers.
   Do not wait to diagnose first; fill, then diagnose.
2. Then log the cause and the permanent fix (dispatcher never waits on a
   front queue it cannot run; cores_meter triggers the fill itself after
   two warnings).
3. Write one lead line with the CORES.md reading once it is back above
   85%.
