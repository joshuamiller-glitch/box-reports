# 0716Z Sat: joint_pool_ny.py restart loop (written by the relay (Claude), not typed by Josh)

Plumbing only.

W-LAYERS: since 06:56Z "HB layer-watch-ny" restarts joint_pool_ny.py every 2 minutes (pids 4095820, 4139567, 4185892, 31032, 67149, 102150, 141566 ... through 07:08Z). It looks like the driver exits at once because the NY rows are held (release rule: Asia D8 ct unstarted < 5,000) and the watcher starts it again. Make one of the two wait instead: either the driver sleeps while held, or the watcher does not restart a driver that exited with "held" (write a state flag). Confirm in one line that (a) the loop has stopped, (b) the NY drivers WILL start by themselves when the release rule is met, (c) the Asia joint_pool.py (last restart 07:00Z, pid 4185889) is alive and working on L385f4f2e.J502, with rows done.
