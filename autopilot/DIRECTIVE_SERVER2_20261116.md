# USER ORDER 2026-11-16 (verbatim): SECOND SERVER
compute pool only, rs4.metal.xlarge, 64 cores / 128 threads / 1,536 GB RAM, 4 x 8 TB NVMe, Dallas, $5.44/hr. Reachable from this box as: ssh ubuntu@207.188.7.103
No Claude Code, no vendor key, no credentials of any kind go on it. Never copy /etc/trading or any key file. Research data and code only.
1. Write SETUP_SERVER2.md, then do it: mount the 8 TB disks, rsync code and /mnt/l2 data (state size and time estimate first), build the python environment, run the identity check there (JL2 202610 = 642 trades, net 27,487.58).
2. One queue on this box, two worker pools. Server 2 workers are launched over ssh; results are written back here. Measure server 2's knee (do not assume 128) and set its cap from that.
3. This box keeps the deadline work until 21:00Z. Server 2 takes T-JOINT-EXIT first, then whatever is queued behind it. If server 2 is ready before 21:00Z, give it the Step 2 engine cells that have not started.
4. Hourly block: server 2 workers running, and cell-months per hour on each machine.
5. It bills by the hour. If it sits idle for more than 30 minutes, say so in a lead note.
