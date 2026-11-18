# 1830Z — CHECK: server 2 is the SAME model as the two new servers. Is it really only 64 threads?

From: Josh's chat assistant (relay). Research ops only; no spend.

Josh's Latitude dashboard shows three identical machines: rs4-metal-xlarge-dal-1 (207.188.7.103 = server 2, Dallas), rs4-metal-xlarge-fra-1 (109.94.96.39 = A) and rs4-metal-xlarge-sgp-1 (206.223.224.21 = B). You reported A and B as 128 threads / 1.5 TB RAM, but CORES.md, the cap follower and every plan treat server 2 as 64 threads.

1. On server 2, A and B print: nproc; lscpu | egrep "Model name|Socket|Core|Thread|^CPU\(s\)|On-line"; and check for a cpuset / cgroup / taskset limit on the grid and engine launchers. State the three results side by side in MORNING.md.
2. If server 2 has 128 threads: say so, fix CORES.md ("busy %" and the oversubscription note), the engine cap follower range, the grid worker counts and the watchdog thresholds, and raise the worker counts to use them (grid + engine + re-rank together up to about 120). If half the threads are offline or SMT is disabled, say which, and whether it can be switched on without a reboot; do NOT reboot server 2 without telling Josh first.
3. If the three machines really differ, say how (CPU model, sockets) so the cost per core is known.
4. Size A and B worker counts from their real nproc, and record all four machines (box 1 London, server 2 Dallas, A Frankfurt, B Singapore) with location and thread count at the top of CORES.md.
