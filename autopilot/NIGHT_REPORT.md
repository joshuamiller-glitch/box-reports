# NIGHT REPORT (generated 01:14Z by code/th_proof/night_report.py; window 2026-11-19T23:00Z .. 2026-11-20T12:00Z)

## Hours at >= 90% of cap per host (5-min samples of the HEALTH Engine slots line)

| host | samples | hours >= 90% | hours >= 50% | mean % of cap | min % |
|---|---|---|---|---|---|
| box1 | 26 | 0.1 | 1.5 | 61 | 33 |
| server2 | 26 | 1.5 | 2.2 | 95 | 79 |
| serverA | 26 | 2.2 | 2.2 | 99 | 97 |
| serverB | 26 | 1.8 | 2.2 | 95 | 80 |
| serverC | 26 | 2.0 | 2.0 | 90 | 0 |
| serverD | 26 | 1.8 | 2.2 | 94 | 78 |

## Drops (host below 90% of cap for >= 10 min)

- box1 23:05Z-01:05Z (120 min, low 33% of cap). Log lines around it (cause / healed by):
    - 23:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 5809 (real 1904), pass 2 571 (total results 6380); todo pass 1 105697 (ETA 18.2 h at this rate), pass 2 23750 (ETA 41.6 h);
    - 23:32Z LEAD NOTE: W-SHORT pseudo-real extension (appended to SURVIVOR_COUNTS.md): scoring random draws that pass R0 as if they were real cells: NY AM (80 sampled cells,
    - 23:42Z LEAD NOTE: HEALTH.md 23:40Z: all four machines 100% busy (Rule A OK). Engine queue 39,688 lines = 27.0 h at 1,468 set-months/h (>= 12 h target met: ladder cells 
    - 00:02Z LEAD NOTE (00:00Z engine queue report, order 2236Z item 2): engine queue 44,445 lines pending (box 1 44,079 / server 2 44,990 eligible) = 30.7 h at the fleet rat
    - 00:05Z W-PLAN DATED ESTIMATES (order 2236Z item 3; in ENGINE_PLAN.md section 11 + SEARCH_STATUS.md mirror): real pass 1 end Nov 19 ~03:00-08:00Z (1,904 real jobs/h meas
    - 00:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 8142 (real 3311), pass 2 959 (total results 9101); todo pass 1 100278 (ETA 12.3 h at this rate), pass 2 23162 (ETA 24.2 h);
- serverD 23:05Z-23:15Z (10 min, low 78% of cap). Log lines around it (cause / healed by):
    - 23:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 5809 (real 1904), pass 2 571 (total results 6380); todo pass 1 105697 (ETA 18.2 h at this rate), pass 2 23750 (ETA 41.6 h);
    - 22:57Z LEAD NOTE (W-GRIDOPS staleness fix #2, remote set JSON; autopilot/STALE_PULLBACK_EXPOSURE.md): CAUSE: the dispatchers pushed a set JSON only when the LOCAL file 
    - 22:58Z LEAD NOTE (W-GRIDOPS scoped exposure list, autopilot/STALE_PULLBACK_EXPOSURE_LIST.csv): every set-month launched before a later edit of its set JSON, no signatur
    - 22:59Z INBOX 20261119_2300Z_Singapore-slots-base-for-followups-wire-all-layers.md received: (1) URGENT engine slots (HEALTH 22:55Z): Singapore 24 of 102, box 1 17/36 (a
    - 23:01Z INBOX 20261119_2305Z_NIGHT-PROOF-six-machines-no-halt.md received: Josh 22:59Z: goes to bed in ~4-6 h (03:00-05:00Z), cannot monitor; six rented machines: 'tight
    - 23:02Z LEAD NOTE (NIGHT-PROOF started): W-PROOF (new) owns autopilot/NIGHT_PROOF.md + drills D1-D5 + CHANGE_FREEZE_0200_1400Z.md + the 12:00Z night-report generator; W-
- serverC 23:15Z-23:25Z (10 min, low 0% of cap). Log lines around it (cause / healed by):
    - 23:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 5809 (real 1904), pass 2 571 (total results 6380); todo pass 1 105697 (ETA 18.2 h at this rate), pass 2 23750 (ETA 41.6 h);
    - 23:32Z LEAD NOTE: W-SHORT pseudo-real extension (appended to SURVIVOR_COUNTS.md): scoring random draws that pass R0 as if they were real cells: NY AM (80 sampled cells,
    - 23:05Z W-PROOF feeder_rerun: layer_cron file state.json is 40 min old (limit 30): re-running its cron command -> rc 1, file age now 40 min
    - 23:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 2401 (real 11), pass 2 849 (total results 3250); todo pass 1 11 (ETA 0.0 h at this rate), pass 2 10239 (ETA 12.1 h); server
    - 23:06Z W-PROOF box1_guard: MemAvailable 47.2 GB < 48 GB: pausing side jobs first (cold copy, pushes, builders/London shards, pass-2 screens, calibration); engine, dispa
    - 23:06Z W-PROOF box1_guard: paused 18 side jobs (mem 47.2 GB, disk 283 GB): builders/London shards, calibration, pass-2 screens
- server2 00:05Z-00:15Z (10 min, low 89% of cap). Log lines around it (cause / healed by):
    - 00:02Z LEAD NOTE (00:00Z engine queue report, order 2236Z item 2): engine queue 44,445 lines pending (box 1 44,079 / server 2 44,990 eligible) = 30.7 h at the fleet rat
    - 00:05Z W-PLAN DATED ESTIMATES (order 2236Z item 3; in ENGINE_PLAN.md section 11 + SEARCH_STATUS.md mirror): real pass 1 end Nov 19 ~03:00-08:00Z (1,904 real jobs/h meas
    - 00:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 8142 (real 3311), pass 2 959 (total results 9101); todo pass 1 100278 (ETA 12.3 h at this rate), pass 2 23162 (ETA 24.2 h);
    - 00:10Z SUPERVISOR restarted 13 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/pyth
    - 00:16Z INBOX 20261119_0017Z_exit-yield-to-150-pairs-oversubscription-dallas-queue.md received (accepted, research ops only; the FULL exit run does not start without Jos
    - 00:16Z LEAD NOTE (W-GRIDOPS, late 23:30Z report + queue + void pairs, lead 00:05Z): (A) ROOT CAUSE OF THE REAL-RATE COLLAPSE IS BIGGER THAN NICE: the W-NIGHT supervisor
- server2 00:22Z-00:45Z (23 min, low 79% of cap). Log lines around it (cause / healed by):
    - 00:16Z INBOX 20261119_0017Z_exit-yield-to-150-pairs-oversubscription-dallas-queue.md received (accepted, research ops only; the FULL exit run does not start without Jos
    - 00:16Z LEAD NOTE (W-GRIDOPS, late 23:30Z report + queue + void pairs, lead 00:05Z): (A) ROOT CAUSE OF THE REAL-RATE COLLAPSE IS BIGGER THAN NICE: the W-NIGHT supervisor
    - 00:18Z W-GRIDOPS (lead order 0017Z items 1-3): (1) W-EXITYIELD asked for and set its 24 ey_job.py workers per host (A, B) to nice 8 at 00:17Z (equal to pass 2, above nu
    - 00:19Z W-NIGHT (per W-GRIDOPS 0017Z item 3): HEALTH.md / guard.py now sum grid todo over ALL four loops per host (real pass 1, _p2, _null, _n12). 00:19Z: Dallas 95.6k j
    - 00:20Z SUPERVISOR restarted 2 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/pytho
    - 00:20Z W-GRIDOPS: W-NIGHT's corrected HEALTH.md shows Dallas grid queue 9.3 h (< 12 h; A 71 h, B 72 h): Dallas re-partitioned again 00:22Z to rows 0,1,4,5,6,9,10,11 of 
- serverB 00:35Z-00:55Z (20 min, low 80% of cap). Log lines around it (cause / healed by):
    - 00:32Z W-EXITYIELD (order 0017Z item 1): reniced my 48 ey_job.py workers (24 on A, 24 on B) from nice 15 to nice 8 at 00:16Z (explicit pids, sudo renice; W-GRIDOPS told
    - 00:47Z W-GRIDOPS (A/B oversubscription test): PHASE 1 (00:17-00:47 UTC, A 96 grid workers, B 98 control): A engine 93 months, real-cell results 657, null-1/2 results 87
    - 00:47Z W-GRIDOPS (A/B oversubscription test): PHASE 1 (00:17-00:47 UTC, A 96 grid workers, B 98 control): A engine 94 months, real-cell results 658, null-1/2 results 87
    - 00:48Z LEAD NOTE: HEALTH.md 00:45Z: all four machines 100% busy (Rule A OK; guard alerts none): box 1 load 74, 28-30 engine, engine 490 set-months/30 min, MemAvail 53 G
    - 01:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 7298 (real 3232), pass 2 359 (total results 7657); todo pass 1 13553 (ETA 1.9 h at this rate), pass 2 22407 (ETA 62.4 h); s
    - 00:44Z LEAD NOTE (W-GRIDOPS: STALE-PULLBACK G1+G3 OLD-VS-NEW, autopilot/STALE_PULLBACK_G13_COMPARISON.txt): compared trade for trade (book, entry and exit time and pric
- serverD 00:35Z-00:45Z (10 min, low 86% of cap). Log lines around it (cause / healed by):
    - 00:32Z W-EXITYIELD (order 0017Z item 1): reniced my 48 ey_job.py workers (24 on A, 24 on B) from nice 15 to nice 8 at 00:16Z (explicit pids, sudo renice; W-GRIDOPS told
    - 00:47Z W-GRIDOPS (A/B oversubscription test): PHASE 1 (00:17-00:47 UTC, A 96 grid workers, B 98 control): A engine 93 months, real-cell results 657, null-1/2 results 87
    - 00:47Z W-GRIDOPS (A/B oversubscription test): PHASE 1 (00:17-00:47 UTC, A 96 grid workers, B 98 control): A engine 94 months, real-cell results 658, null-1/2 results 87
    - 00:48Z LEAD NOTE: HEALTH.md 00:45Z: all four machines 100% busy (Rule A OK; guard alerts none): box 1 load 74, 28-30 engine, engine 490 set-months/30 min, MemAvail 53 G
    - 00:44Z LEAD NOTE (W-GRIDOPS: STALE-PULLBACK G1+G3 OLD-VS-NEW, autopilot/STALE_PULLBACK_G13_COMPARISON.txt): compared trade for trade (book, entry and exit time and pric
    - 00:44Z W-BEST stale list update (G1+G3 comparison): cleared 38 of the 40 G1/G3 cells (every compared set-month IDENTICAL; applies at the next refresh :07/:37); still st

## Real firings overnight (automatic actions, from MORNING.md in the window; lines marked DRILL were forced tests)

- 23:00Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'NYE': 1})
- 23:05Z | feeder_rerun | host: - | - 23:05Z W-PROOF feeder_rerun: layer_cron file state.json is 40 min old (limit 30): re-running its cron command -> rc 1, file age now 40 min
- 23:06Z | box1_guard | host: box1 | - 23:06Z W-PROOF box1_guard: MemAvailable 47.2 GB < 48 GB: pausing side jobs first (cold copy, pushes, builders/London shards, pass-2 screens, calibration); engine, dispatchers, pullers untouched
- 23:06Z | box1_guard | host: box1 | - 23:06Z W-PROOF box1_guard: paused 18 side jobs (mem 47.2 GB, disk 283 GB): builders/London shards, calibration, pass-2 screens
- 23:08Z | box1_guard | host: box1 | - 23:08Z W-PROOF box1_guard: MemAvailable 46.6 GB: pause level group 1 (1 shards+calibration, 2 +pass-2 screens/builders, 3 +cold copy/pushes); engine, dispatchers, pullers untouched
- 23:09Z | box1_guard | host: box1 | - 23:09Z W-PROOF box1_guard: MemAvailable 45.3 GB: pause level group 2 (1 shards+calibration, 2 +pass-2 screens/builders, 3 +cold copy/pushes); engine, dispatchers, pullers untouched
- 23:09Z | box1_guard | host: box1 | - 23:09Z W-PROOF box1_guard: paused 7 side jobs (mem 45.3 GB, disk 283 GB): ny_bothside/London shards, other builders, pass-2 screens/loop
- 23:09Z | box1_guard | host: box1 | - 23:09Z W-PROOF box1_guard: trickle: MemAvailable 45.3 GB >= 45 GB, resumed paused pass-2 screens/loop pid 1875852 (rss 7.9 GB), immune 10 min so paused jobs still make progress
- 23:10Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'NYE': 1})
- 23:13Z | supervisor | host: box1 | - 23:13Z SUPERVISOR restarted 1 dead loop(s): box1: START_DISPATCH 67.213.127.157 C
- 23:19Z | box1_guard | host: box1 | - 23:19Z W-PROOF box1_guard: paused 1 side jobs (mem 49.0 GB, disk 283 GB): ny_bothside/London shards, other builders, pass-2 screens/loop
- 23:19Z | box1_guard | host: box1 | - 23:19Z W-PROOF box1_guard: trickle: MemAvailable 49.0 GB >= 45 GB, resumed paused pass-2 screens/loop pid 4028985 (rss 0.0 GB), immune 10 min so paused jobs still make progress
- 23:20Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'EXE': 1})
- 23:20Z | supervisor | host: box1 | - 23:20Z SUPERVISOR restarted 1 dead loop(s): box1: START_DISPATCH 67.213.127.157 C
- 23:25Z | supervisor | host: box1 | - 23:25Z SUPERVISOR restarted 1 dead loop(s): box1: START_DISPATCH 72.46.85.15 D
- 23:27Z | box1_guard | host: box1 | - 23:27Z W-PROOF box1_guard: paused 1 side jobs (mem 48.5 GB, disk 283 GB): ny_bothside/London shards, other builders, pass-2 screens/loop
- 23:29Z | box1_guard | host: box1 | - 23:29Z W-PROOF box1_guard: paused 1 side jobs (mem 48.4 GB, disk 283 GB): ny_bothside/London shards, other builders, pass-2 screens/loop
- 23:29Z | box1_guard | host: box1 | - 23:29Z W-PROOF box1_guard: trickle: MemAvailable 48.4 GB >= 45 GB, resumed paused other builders pid 2230004 (rss 0.9 GB), immune 10 min so paused jobs still make progress
- 23:30Z | lease_sweep | host: any (holder gone) | moved 11 stale leases to leases_stale_* ({'ASI': 5, 'NYE': 6})
- 23:30Z | mux_watch | host: /tmp/mux_pull_72_46_85_15_2 | - 23:30Z W-PROOF mux_watch: pull socket /tmp/mux_pull_72_46_85_15_2 (72.46.85.15) bad: probe through master TIMED OUT (hung master) (master pid 2246725 killed) -> master torn down by explicit socket, next pull rebuilds it
- 23:30Z | mux_watch | host: /tmp/mux_pull_72_46_85_15_2 | - 23:30Z W-PROOF mux_watch: pull socket /tmp/mux_pull_72_46_85_15_2 (72.46.85.15) bad: probe through master TIMED OUT (hung master) (master pid 978311 killed) -> master torn down by explicit socket, next pull rebuilds it
- 23:32Z | feeder_rerun | host: - | - 23:32Z W-PROOF feeder_rerun: ex_ownmerit file om_state.json is 22 (FORCED DRILL) min old (limit 90): re-running its cron command -> rc 0, file age now 22 min   [DRILL/forced]
- 23:34Z | box1_guard | host: box1 | - 23:34Z W-PROOF box1_guard: trickle: MemAvailable 50.2 GB >= 45 GB, resumed paused other builders pid 2060734 (rss 1.3 GB), immune 10 min so paused jobs still make progress
- 23:34Z | box1_guard | host: box1 | - 23:34Z W-PROOF box1_guard: trickle: MemAvailable 50.2 GB >= 45 GB, resumed paused other builders pid 2060741 (rss 1.4 GB), immune 10 min so paused jobs still make progress
- 23:34Z | box1_guard | host: box1 | - 23:34Z W-PROOF box1_guard: trickle: MemAvailable 50.2 GB >= 45 GB, resumed paused pass-2 screens/loop pid 4028985 (rss 0.0 GB), immune 10 min so paused jobs still make progress
- 23:34Z | slot_heal | host: serverB | 23:34Z W-GRIDOPS SELF-HEAL: serverB engine slots 99 of 102 (or dispatcher log silent) for >=10 min with runnable lines: killing dispatcher pid(s) 1954478, supervisor restarts it (once per 30 min per host)
- 23:35Z | feeder_rerun | host: - | - 23:35Z W-PROOF feeder_rerun: layer_cron file state.json is 70 min old (limit 30): re-running its cron command -> rc 1, file age now 70 min
- 23:35Z | supervisor | host: box1 | - 23:35Z SUPERVISOR restarted 1 dead loop(s): box1: START_DISPATCH 206.223.224.21 B
- 23:36Z | box1_guard | host: box1 | - 23:36Z W-PROOF box1_guard: /mnt/l2 free 283 GB < 400 GB: pausing writers first (cold copy, pushes, builders/London shards, pass-2 screens); engine, dispatchers, pullers untouched
- 23:38Z | box1_guard | host: box1 | - 23:38Z W-PROOF box1_guard: MemAvailable 41.4 GB: pause level group 3 (1 shards+calibration, 2 +pass-2 screens/builders, 3 +cold copy/pushes); engine, dispatchers, pullers untouched
- 23:40Z | box1_guard | host: box1 | - 23:40Z W-PROOF box1_guard: trickle: MemAvailable 48.0 GB >= 45 GB, resumed paused other builders pid 2060749 (rss 1.4 GB), immune 10 min so paused jobs still make progress
- 23:40Z | box1_guard | host: box1 | - 23:40Z W-PROOF box1_guard: trickle: MemAvailable 48.0 GB >= 45 GB, resumed paused other builders pid 2060763 (rss 1.5 GB), immune 10 min so paused jobs still make progress
- 23:40Z | lease_sweep | host: any (holder gone) | moved 2 stale leases to leases_stale_* ({'ASI': 1, 'NYE': 1})
- 23:46Z | box1_guard | host: box1 | - 23:46Z W-PROOF box1_guard: trickle: MemAvailable 46.4 GB >= 45 GB, resumed paused other builders pid 2060742 (rss 2.3 GB), immune 10 min so paused jobs still make progress
- 23:50Z | box1_guard | host: box1 | - 23:50Z W-PROOF box1_guard: MemAvailable 40.5 GB < 41 GB: SIGTERM ny_bothside/London shards pid 1058935 (rss 4.6 GB, re-runnable) 
- 23:51Z | box1_guard | host: box1 | - 23:51Z W-PROOF box1_guard: trickle: MemAvailable 46.0 GB >= 45 GB, resumed paused other builders pid 2060747 (rss 2.7 GB), immune 10 min so paused jobs still make progress
- 23:53Z | box1_guard | host: box1 | - 23:53Z W-PROOF box1_guard: MemAvailable 38.4 GB < 41 GB: SIGTERM ny_bothside/London shards pid 1058927 (rss 4.0 GB, re-runnable) 
- 23:54Z | box1_guard | host: box1 | - 23:54Z W-PROOF box1_guard: MemAvailable 39.2 GB < 41 GB: SIGTERM ny_bothside/London shards pid 1058932 (rss 3.3 GB, re-runnable) 
- 23:55Z | box1_guard | host: box1 | - 23:55Z W-PROOF box1_guard: MemAvailable 53.4 GB, /mnt/l2 282 GB free: back above the resume levels, resumed 10 paused side jobs
- 23:58Z | box1_guard | host: box1 | - 23:58Z W-PROOF box1_guard: MemAvailable 49.5 GB: pause level group 1 (1 shards+calibration, 2 +pass-2 screens/builders, 3 +cold copy/pushes); engine, dispatchers, pullers untouched
- 00:00Z | lease_sweep | host: any (holder gone) | moved 2 stale leases to leases_stale_* ({'NYE': 2})
- 00:06Z | box1_guard | host: box1 | - 00:06Z W-PROOF box1_guard: MemAvailable 46.3 GB: pause level group 1 (1 shards+calibration, 2 +pass-2 screens/builders, 3 +cold copy/pushes); engine, dispatchers, pullers untouched
- 00:10Z | supervisor | host: server2, serverA | - 00:10Z SUPERVISOR restarted 13 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.ve
- 00:20Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'ALN': 1})
- 00:20Z | supervisor | host: server2 | - 00:20Z SUPERVISOR restarted 2 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/python3 -I code/th_gr
- 00:50Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'ALN': 1})
- 01:00Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'ALN': 1})
- 01:10Z | lease_sweep | host: any (holder gone) | moved 2 stale leases to leases_stale_* ({'ALN': 1, 'NYE': 1})
- 01:10Z | ny_refill | host: queue | queue 12.0 h -> 14.0 h: ranked_follow beyond rank 50: asked 28982 set-months, queued 29126

## Set-months landed in the window (DONE files in the box-1 result tree), per programme prefix

| programme | set-months |
|---|---|
| TL3_ALN | 16922 |
| TL3_NYE | 7446 |
| TL3_ASI | 3855 |
| TL3_EXE | 136 |
| TL3_LON | 123 |
| TL3_STK | 60 |
| TL3_NYL | 12 |
| TL3_LYR | 9 |
| TOTAL | 28563 |
