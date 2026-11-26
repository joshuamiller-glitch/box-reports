# SERVER REPORT for Josh (W-ROTS, read-only, measured 26 Nov 2026 15:55-16:10Z)

Nothing was changed: no queue edit, no kill, no restart. Only ps, df, free, vmstat, file counts and log reads. You pay $240/day per server, $1,440/day for six.

## ANSWER FIRST

1. **Today the fleet is mostly idle for exact replays, and the cause is feed, not hardware.** At 15:50Z engine slots in use were 45 of 464 (10%). Server D has been 100% idle and C about 85% idle. A, B and server 2 are busy, but on quick-screen grid jobs and D8 exit jobs, not on exact replays. Measured exact-engine rate over the last 6 h and last 12 h is **1,260 set-months/h for the whole fleet**.
2. **The 763/h and the 5,800/h are both real, but stale or conditional.**
   - 763/h is an old snapshot (box 1 450 + Dallas 313, written when A and B had no engine yet; SURVIVOR_COUNTS.md line 9). It is not two servers today.
   - 5,800/h is what the six servers deliver when the queue is full. From 12 h to 24 h ago they averaged **7,600/h**, with hours up to 10,079/h.
   - Around 03:30Z the rate fell about 6x. The wired queue ran dry: of 63,487 distinct rows in the live queue files, 62,549 are DONE and **only 52 are runnable**. The dispatchers now launch a small wave about every 15 min and then sit idle.
3. **Minimum for the rotation routine going forward: 1 server** of the 128-thread class (A, B or C), for both the weekly and the two-weekly refit. Estimated 0.5 to 3 h per weekly refit on one server. A second server is only a convenience. Two servers help for the first full run today. One part cannot be sized from measurements: scoring each new week for the whole quick-screen grid (section 3).
4. **Engine spec:** 1 core per slot, about 1.0 GB RAM per slot, about 300 GB local data, light disk and network. Details in section 4. A single 32 to 64 core machine with 128 to 256 GB RAM and a 1 TB NVMe disk would do the routine work, but see the caveat on page cache.
5. **Candidate backlog:** the legacy file `_nye/pending_r5.txt` holds **508,500** unleased, not-yet-run set-months (the "508,620 lines pending" in HEALTH.md). It is not wired into the dispatchers' queue list, so nothing is feeding it. Hours: **about 170 h on 1 server (7 days), about 85 h on 2, about 67 h on all 6** (a 42 to 88 h range). 78% of these rows are date-shift controls, and an earlier characterization (Nov 24) called about 28% of the file obsolete. See section 5.

**Two warnings that matter more than the server count**
- **Box 1's data disk /mnt/l2 is 99% full: 60 GB free of 3.5 TB.** HEALTH.md shows "?" for it (the box 1 probe timed out). Stage A reads about 95 GB of stored grid arrays and every replay writes results here. Make room before a big run. Moving or deleting data is not my call, and I did nothing.
- The 1520Z order says "use all six". Right now A, B and server 2 CPUs are taken by the grid pool (gjob2, 86 to 92 workers each, 183 h of grid todo on A and B) and the D8 exit screen (ey_job2, 24 workers each on A and B). The rotation gets them only if the lead pauses those jobs. Idle today without touching anything: D fully, C about 85%.

## 1. What each server is doing now

Threads, RAM and disk come from ssh `nproc`, `free` and `df` at about 15:59Z. Rates come from the DONE files in box 1's result tree (`_th_sz/ijk/exact/runs_rf/*/*/DONE`, mtime), matched to the lease file for the host, covering the last 24 h (107,236 DONE). The "box 1 / server 2" row is one combined figure because box 1's own runs and server 2's runs carry the same lease type with no host field. W-SHORT's ENGINE_RATE line puts server 2 at about 84/h, so box 1 itself is about 400/h.

| server | where / chip | threads | RAM | disk (root / data) | engine cap (slots) | doing now (CPU view) | exact replays/h last 6 h | last 12 h | 12-24 h ago | last 24 h total |
|---|---|---|---|---|---|---|---|---|---|---|
| box 1 (hub, this machine) | London, 32 | 32 | 187 GB (14 free, 59 available) | root 44 GB free; **data 60 GB free (99%)** | 24 | 29 tp_launch engine procs, 16 grid procs, the pullers, dispatchers, builders and W-agents; load 64, 94% busy | in the combined row | in the combined row | in the combined row | in the combined row |
| server 2 (old Dallas 207.188.7.103) | EPYC 9554P, no SMT | 64 | 1.5 TB | root 407 GB free; data 26 TB free | 28 | 86 gjob2 grid workers plus 4 gscore; 0 engine procs; 73% busy | **489 (box 1 + server 2 together)** | 490 | 1,140 | 19,536 |
| A (Frankfurt 109.94.96.39) | EPYC 9554P, 2 threads/core | 128 | 1.5 TB | root 830 GB free; data 5.7 TB free of 7 TB | 102 | 92 gjob2 plus 24 ey_job2 (D8 exit); 0 engine procs; vmstat idle 59% | 161 | 220 | 1,290 | 18,165 |
| B (Singapore 206.223.224.21) | same | 128 | 1.5 TB | root 412 GB free; data 5.6 TB free | 102 | 92 gjob2 plus 24 ey_job2; 0 engine procs; idle 50%; load 100 | 233 | 208 | 1,480 | 20,295 |
| C (Amsterdam 67.213.127.157) | same | 128 | 1.5 TB (1,018 GB free) | root 412 GB free; data 27 TB free | 140 | 122 engine slots in a wave, each about 90% of a core, then idle; 15% busy | 218 | 151 | 1,950 | 25,231 |
| D (new Dallas 72.46.85.15) | EPYC 9554P, no SMT | 64 | 1.5 TB | root 412 GB free; data 28 TB free | 68 | nothing: 0% CPU, load 0.08 | 159 | 192 | 1,760 | 23,383 |
| **fleet** | | 544 | | | 464 | 42% of threads busy overall, 7% on exact replays | **1,260/h** | **1,260/h** | **7,600/h** | 106,610 |

The "sixth" server is box 1 itself. The six are box 1, server 2, A, B, C and D, from `guard.py` HOSTS plus the extra_servers registry and the `start_dispatch.sh` lines.

AGENTS_LIVE.md is stale (last write Nov 19) and has no server list. The server list comes from the code and the running processes.

Slots in use at 15:50Z (HEALTH.md): box 1 16 of 24, server 2 0 of 28, A 0 of 102, B 0 of 102, C 29 of 140, D 0 of 68.

## 2. Why 763/h measured versus 5,800/h quoted

| claim | what it really is | evidence |
|---|---|---|
| 763/h "on two servers" | An old figure from the ENGINE_PLAN / SURVIVOR_COUNTS era (Nov 19), with A and B "no engine runs yet". | SURVIVOR_COUNTS.md line 9: "measured 763 (box 1 450 + Dallas 313; A and B have no engine runs yet), projected 2894 with A and B engine-ready". |
| 5,800/h fleet | The six-server rate when the queue is full. | DONE files 12-24 h ago averaged 7,600/h (hourly 2,962, 5,851, 10,079, 9,287, 6,023, 6,306, 9,100, 6,051, 10,045, 7,173, 9,258, 9,987). 24 h per host: C 25.2k, D 23.4k, B 20.3k, A 18.2k, box 1 + server 2 19.5k. |
| 1,260/h now | The measured rate in the last 6 and 12 h. | Hourly DONE counts since 04:00Z are about 1,000 to 1,450. HEALTH.md shows "fleet rate 0" only because the box 1 probe timed out. That number is not real. |

Why the rate fell from about 7,600/h to 1,260/h (evidence, strongest first):

1. **Queue starvation.** I read all 1,190 files in `_s2/QUEUES.txt`. They hold 63,487 distinct set-month rows: 62,549 DONE, 838 leased and not done, 48 with no set file, **52 runnable**, and 49 of those 52 are exit rows in `_exiteng/pending.txt`. A queue that is 99.9% done cannot feed 464 slots. The dispatch logs match: every host launches in waves (for example 15:08, 15:24, 15:38 and 15:54Z), always with "remote running 0". Wave sizes were 14 to 102. Jobs finish in about 100 s and then the slots idle for about 13 min.
2. **The big queue is not wired in.** The 508,500-row backlog sits in `_nye/pending_r5.txt`, which is not listed in QUEUES.txt. The dispatchers cannot see it. The 1520Z order now says to stop feeding it.
3. **Slots are idle, not slow.** At 15:50Z engine slots were 45 of 464. The CPU view shows C 85% idle and D 100% idle. A, B and server 2 are busy, but with the grid pool, not replays (gjob2 workers: 86, 92 and 92).
4. **Per-run cost is not the problem now.** Launch to DONE medians in the last 5 h: D 76 s, C 93 s, A 118 s, B 120 s, box 1 / server 2 123 s (p90 107 to 169 s). That is the fast path. The 550 s per run seen on Nov 19 (DIRECTIVE_FLEET_RATE_HALVED) is not present now (the fast share is 100% on box 1 and C).
5. **Disk, data and network are not limiting.** Every remote has more than 5 TB free on /mnt/l2 and more than 400 GB free on root. C shows `bi` 0 in vmstat, so the month cache is served from RAM. Box 1 is the exception: /mnt/l2 is at 99% (60 GB free).
6. **Guards and caps.** Caps are 24, 28, 102, 102, 140 and 68 (464). Server 2 is capped at 28 slots on 64 cores and box 1 at 24 slots on 32 threads, by lead decision. The "bad set json TL3_ALN_NY_L59efe6b3_R0 FileNotFoundError" line repeats every 15 s on all six dispatch logs (about 9,350 lines each). It is harmless to dispatch but is a missing set file at the queue head, and it fills the logs. At 15:32Z SLOT_HEAL killed and restarted the server 2 dispatcher after 10 min of 0 slots. All dispatchers were restarted at 15:35Z.

Theoretical ceiling for comparison: slots times 3600 divided by measured seconds per run gives box 1 about 580, server 2 about 840, A about 3,100, B about 3,000, C about 5,400 and D about 3,100, so about 16,000/h if every slot were full. The best measured hour was 10,079. So 5,800 to 7,600 is a fair planning figure for six servers when fed, and it is conservative.

## 3. Minimum servers for the rotation routine

**Definitions.** Stage A is the quick-screen walk on the whole stored set (44.03 M cells with weekly arrays, about 95 GB of npz on box 1, no replays). Stage B (the "fit of picked mixes") is the exact re-score of the picked books plus their mix fits. The numbers come from ROTATION_FULL_SET_AUDIT.md (W-ROT 14:34Z), SURVIVOR_COUNTS.md and ENGINE_PLAN.md, scaled to the 1502Z and 1506Z design. All hours below are **planning estimates, not measurements**.

**Planning rates (assumptions).** One 128-thread server (A, B or C class) sustains about 3,000 set-months/h of exact engine. That is measured per-run time, with slots at about 80% of the 4,200 to 5,400/h theoretical. One 64-core server (D or server 2 class) sustains about 2,000/h. Box 1 is not counted because it is the hub. No grid pool is running on the servers used.

**Today's one-off test (first full run).**
- **Stage A:** the audit estimated 2 to 6 h on 1 server for 5 lookbacks and 80 dates. The 1502Z/1506Z design has 7 lookbacks, weekly dates, 4 refit steps, and 11 prior-year levels with two baselines. That is about 4 to 6 times more work, **a guess of 6 to 24 h on 1 server**. It splits cleanly by session (4 ways), and the guess for 2 and 3 servers is below. The lead's own ETA is 2 to 4 h on six servers after the build. That ETA is consistent with this guess if the grid pool is paused.
- **Stage B:** the audit's 8,000 to 29,000 set-months were for the old, smaller design. With 7 lookbacks, 4 steps and the best 3 levels per session plus no filter, I guess **25,000 to 90,000**. This is the least certain number in the report.

| first full run (today) | stage A (guess) | stage B, 25k to 90k set-months (guess) | total |
|---|---|---|---|
| 1 server (128-thread) | 6-24 h | 8-30 h | 14-54 h |
| 2 servers | 3-12 h | 4-15 h | 7-27 h |
| 3 servers | 2-8 h | 3-10 h | 5-18 h |
| 6 servers (measured 7,600/h when fed) | 1-4 h | 3-12 h | 4-16 h |

**Going forward (after the first run).** Stage A is incremental: only the newest date has to be ranked for each of 7 lookbacks and 11 levels. That is minutes on one server and not the bottleneck. Two things are not measured:
- **The new week's quick-screen scoring** for all 44 M cells (the grid pool). I cannot size it from anything on disk. Grid throughput today is only 140 to 380 result rows per 30 min per server, with 183 h of todo on A and B. I **guess 1 to 6 h on one server**, and it needs to be measured once.
- **The size of the fit.** I used two cases, each in set-months per refit:
  - Light: about 3,000. That is 10 to 30 new books entering the picks at 41 months each, plus about 2,200 shared whole-session and mixed sets (ENGINE_PLAN section 2).
  - Heavy: about 9,000. That adds 30 date-shift controls times 6 months (180 rows) per new pick.

| refit (stage B only; add the stage A and grid-week times above) | set-months | 1 server (3,000/h) | 2 servers | 3 servers |
|---|---|---|---|---|
| weekly, light | 3,000 | 1.0 h | 0.5 h | 0.35 h |
| weekly, heavy | 9,000 | 3.0 h | 1.5 h | 1.0 h |
| every 2 weeks, light (more turnover, assume 1.6x) | 4,800 | 1.6 h | 0.8 h | 0.5 h |
| every 2 weeks, heavy | 14,400 | 4.8 h | 2.4 h | 1.6 h |

A 64-core server (about 2,000/h) takes 1.5x these times; the weekly heavy case is then 4.5 h. **Minimum = 1 server.** Weekly or two-weekly, the routine fits in a working day on one 128-thread server. Keep a second server only if you want the weekly job done in under 2 h, or as insurance against a host failing. The six-server fleet is not needed for steady state. It was built for the 44 M-cell search and the backlog.

## 4. What the engine really needs (to price cheaper machines)

All figures are measured on this fleet unless marked a guess.

| item | measured | basis |
|---|---|---|
| CPU | **1 core per slot**, one single-thread Python process at 87 to 93% of a core (OMP, NUMBA and OPENBLAS threads all set to 1). Per set-month: about 78 s on a real core (D, 64 cores, no SMT), 93 to 120 s on a hyper-thread (A, B, C, box 1). That is about 80 to 120 core-seconds per set-month. All six are AMD EPYC 9554P (Zen 4), except box 1, whose chip I did not read. Chip class matters; slower cores scale the rate down. | `ps` and `top` on C; lease-to-DONE medians |
| RAM per slot | about **1.0 GB resident** (C processes show 0.98 to 1.1 GB; ENGINE_PLAN: 0.74 to 1.0 GB). The launcher waits when free RAM is below 20 GB (TP_WAIT_GB=20) and the dispatcher uses 1.0 GB per worker. | `top` on C; s2_remote_run.sh; CAPS.txt |
| shared cache | The month cache is **223 GB** (about 2.5 GB per month; `_th_tp/cache`). On the 1.5 TB machines it sits entirely in the page cache (C: 470 GB cache, `bi` 0). **Guess:** if RAM is below about 300 GB, jobs read the cache from the NVMe disk, and I do not know how much that slows them. Test it before buying small-RAM boxes. | du; vmstat |
| data to keep local per engine server | cache 223 GB + `_hist_replica` 35 to 43 GB + `_th_sz` 14 GB + `_exiteng` 7 GB + `_s2` 9 GB + code 2.3 GB = **about 300 to 320 GB** before results. Results are small: `runs_rf` is 73 GB for about 190k set dirs (about 0.4 MB per set-month, so about 4 GB per 10,000 set-months). | du on D and box 1 |
| disk I/O | light: `bo` about 0 to 1 MB/s on C; bursts of reads when a month cache is first touched. Any 1 TB NVMe will do, if the RAM is large. Remote servers use 1 to 4 NVMe disks in RAID0. | vmstat |
| network | small per job (set JSON plus `rsync` of changed dependencies, results pulled by `s3_pull.py`). Link speeds measured in ENGINE_PLAN: 127 to 470 MB/s between servers. The one-time engine copy is about 60 GB of data plus the 223 GB cache. ENGINE_PLAN assumed 20 to 40 min plus 30 to 60 min per server (an assumption, not a measurement). | ENGINE_PLAN section 1 |
| stage A extra | reads about 95 GB of stored grid arrays (`_grid/res`, on box 1). Wants those 95 GB local to wherever it runs, plus RAM for the working set. **I did not measure this; guess 64 to 128 GB RAM.** | du |

**Cheaper machines, rule of thumb:** engine rate per server is about threads x 3,600 / 110 x 0.8. That gives about 32 threads, 64 GB: 900/h (box 1 sits there, but it is also the hub); 64 real cores, 256 GB: 2,000 to 2,500/h; 128 threads, 512 GB or more: 3,000 to 3,500/h. If the routine is 3,000 to 9,000 set-months per refit, a 64-core, 256 GB, 1 TB NVMe machine is enough, and you would not need the 1.5 TB RAM and 28 TB of disk you pay for now. Cost per set-month at $240/day on a 128-thread server fully used is about $0.0033, so the 508k backlog is about $1,700 of server time if the servers are kept full.

## 5. Candidate backlog (rows counted first)

- **Wired queue files** (QUEUES.txt, 1,190 files): 63,487 distinct rows, 62,549 DONE, **52 runnable**, 838 leased and not DONE. About 300 of those leases are in flight (C 122, B 102, D 16, server 2 26, box 1 about 15) and the rest are stale leases (my inference; the reaper `leases_stale_*` runs about every 10 min).
- **Legacy `_nye/pending_r5.txt`:** 663,083 distinct rows: 154,527 DONE, 56 leased, **508,500 unleased**. By kind: `TL3_NYE_L*_ALNCT` 231,388 and `TL3_NYE_B*_ALNCT` 164,340 (date-shift controls, 395,728, 78%); `_ALN` (all-new base) 73,368 and 39,404 (112,772, 22%). Months 202304 to 202610, about 68,600 rows each for the recent months. The 18:50Z Nov 24 characterization: 1,373 cells (266k rows) were out at first look with L6M negative and so obsolete work. I did not re-check that. If it still holds, up to about half of this backlog could be dropped. Only the lead can decide to prune.

Hours for 508,500 rows (assumptions: 3,000/h per 128-thread server, 2,000/h per 64-core server; the 6-server column uses the measured 5,800 to 7,600/h):

| servers | rate | hours | days |
|---|---|---|---|
| 1 (128-thread) | 3,000/h | 170 | 7.1 |
| 1 (64-core) | 2,000/h | 254 | 10.6 |
| 2 (128-thread) | 6,000/h | 85 | 3.5 |
| 6 (measured fleet when fed) | 5,800 to 7,600/h | 67 to 88 | 2.8 to 3.7 |
| 6 (theoretical ceiling) | about 12,000/h | 42 | 1.8 |

Note: every row of the backlog is a replay, so the server count scales the time almost linearly (no shared bottleneck below about 10,000/h except the box 1 puller and disk).

## What I could not verify (honest list)

- Box 1's chip and the per-run time of box 1 slots. The lease record has no host for box 1 and server 2 rows, so they are combined.
- Stage A time on the new design and the size of stage B. These are scaled guesses from the audit and have not been run.
- The cost of scoring one new week for the whole grid (the largest unknown for the routine).
- Whether small-RAM machines slow the engine (page cache).
- The 508,500 count came from `os.path.exists` on DONE and lease files. Rows whose DONE is stale (older than the lease, 478 per the stale detector) count as done here.
