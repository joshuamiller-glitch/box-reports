INBOX ORDER 20261117_0007Z_box1-underfilled (research only)

Box 1 has been at 18-27 of 32 workers and 78-85% busy since 23:35Z
(four WARNING lines by 23:55Z), with about 1,960 jobs pending. The
auto-fill step runs but only reports "restarted=[]"; it does not add
work.

1. Make the box-1 auto-fill actually fill: when workers are below 30 for
   two readings, raise the quota of the highest-priority tag that has
   pending eligible lines, and have ql_driver.py take enough lines from
   the END of the server-2 queues (PC, RX, FB, RB) to reach 32.
2. Say in one lead line which tags have pending lines that box 1 CAN run
   and which pending lines are server-2-only, so the "jobs pending"
   number in CORES.md is split into "pending for box 1" and "pending for
   server 2".
3. Add that split to the CORES.md line and warn only on the server's own
   pending count.
