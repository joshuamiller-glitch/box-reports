# NIGHT REPORT (generated 23:49Z by code/th_proof/night_report.py; window 2026-11-19T23:00Z .. 2026-11-20T12:00Z)

## Hours at >= 90% of cap per host (5-min samples of the HEALTH Engine slots line)

| host | samples | hours >= 90% | hours >= 50% | mean % of cap | min % |
|---|---|---|---|---|---|
| box1 | 9 | 0.0 | 0.2 | 49 | 42 |
| server2 | 9 | 0.8 | 0.8 | 100 | 100 |
| serverA | 9 | 0.8 | 0.8 | 99 | 98 |
| serverB | 9 | 0.8 | 0.8 | 97 | 95 |
| serverC | 9 | 0.6 | 0.6 | 76 | 0 |
| serverD | 9 | 0.5 | 0.8 | 91 | 78 |

## Drops (host below 90% of cap for >= 10 min)

- box1 23:05Z-23:45Z (40 min, low 42% of cap). Log lines around it (cause / healed by):
    - 23:05Z W-GRIDOPS: jobs/h last 60 min: pass 1 5809 (real 1904), pass 2 571 (total results 6380); todo pass 1 105697 (ETA 18.2 h at this rate), pass 2 23750 (ETA 41.6 h);
    - 23:32Z LEAD NOTE: W-SHORT pseudo-real extension (appended to SURVIVOR_COUNTS.md): scoring random draws that pass R0 as if they were real cells: NY AM (80 sampled cells,
    - 23:42Z LEAD NOTE: HEALTH.md 23:40Z: all four machines 100% busy (Rule A OK). Engine queue 39,688 lines = 27.0 h at 1,468 set-months/h (>= 12 h target met: ladder cells 
    - 22:57Z LEAD NOTE (W-GRIDOPS staleness fix #2, remote set JSON; autopilot/STALE_PULLBACK_EXPOSURE.md): CAUSE: the dispatchers pushed a set JSON only when the LOCAL file 
    - 22:58Z LEAD NOTE (W-GRIDOPS scoped exposure list, autopilot/STALE_PULLBACK_EXPOSURE_LIST.csv): every set-month launched before a later edit of its set JSON, no signatur
    - 22:59Z INBOX 20261119_2300Z_Singapore-slots-base-for-followups-wire-all-layers.md received: (1) URGENT engine slots (HEALTH 22:55Z): Singapore 24 of 102, box 1 17/36 (a
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
- 23:17Z | slot_heal share | host: server2, serverA, serverB, serverC, serverD | 23:17Z W-GRIDOPS ORDER 2318Z DONE (items 1-3): (1) LONDON PIN removed: _split/london_pin and london_on moved to .off_2325 (not deleted); London comes back only by ny_refill rule (queue < 8 h) or BY RIGHT via code/lead_watchdog/lon
- 23:19Z | box1_guard | host: box1 | - 23:19Z W-PROOF box1_guard: paused 1 side jobs (mem 49.0 GB, disk 283 GB): ny_bothside/London shards, other builders, pass-2 screens/loop
- 23:19Z | box1_guard | host: box1 | - 23:19Z W-PROOF box1_guard: trickle: MemAvailable 49.0 GB >= 45 GB, resumed paused pass-2 screens/loop pid 4028985 (rss 0.0 GB), immune 10 min so paused jobs still make progress
- 23:20Z | lease_sweep | host: any (holder gone) | moved 1 stale leases to leases_stale_* ({'EXE': 1})
- 23:20Z | slot_heal share | host: - | 23:20Z W-GRIDOPS share_ctl: ALN leased last 30 min 337 (>=300 = all-new base flowing): FOLLOWUP_FIRST back ON for C; FOLLOWUP_FIRST back ON for D
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
- 00:10Z | supervisor | host: server2, serverA | - 00:10Z SUPERVISOR restarted 13 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.ve
- 00:20Z | supervisor | host: server2 | - 00:20Z SUPERVISOR restarted 2 dead loop(s): server2: <repo>/.venv/bin/python3 -I code/th_gr; server2: <repo>/.venv/bin/python3 -I code/th_gr

## Set-months landed in the window (DONE files in the box-1 result tree), per programme prefix

| programme | set-months |
|---|---|
| TL3_ALN | 3740 |
| TL3_NYE | 2680 |
| TL3_ASI | 2114 |
| TL3_EXE | 136 |
| TL3_STK | 60 |
| TL3_LON | 33 |
| TL3_LYR | 9 |
| TOTAL | 8772 |
