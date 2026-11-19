# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T16:30:02Z | CORES reading: 2026-11-19 16:25Z | guard sample: 2026-11-19T16:20:01Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 16:22Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T16:29Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.36 | 33 | 51 | 70 | 2423 | n/a | n/a | 292 | 59.7 (0.224 GB/h, 266.4 h) |
| server2 | ? | 64 | ? | ? | 2544 | 70 | 488 | 107289 | 21.1 h | 26514 | 407.3 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 254.03 | 105 (grid) + 100 (engine) | 494 | 0 | 997 | 75057 | 76.0 h | 6255 | 829.7 (0.017 GB/h, n/a h) |
| serverB | 100 | 128 | 220.97 | 105 (grid) + 99 (engine) | 776 | 0 | 1089 | 60753 | 39.1 h | 6201 | 412.0 (0.022 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 34/36 (94%); server2 25/28 (89%); serverA 100/102 (98%); serverB 101/102 (99%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T16:25Z): box1 22/28 (79%); Dallas 25/25 (100%); Frankfurt 101/101 (100%); Singapore 93/93 (100%); fleet 98%; exact-path kinds: TL3_CMB_MN 6

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 3 gr3 procs, 1170 XC records, B-C tasks 576/576 done (0 left); serverA: 3 gr3 procs, 1389 XC records, B-C tasks 0/0 done (0 left); serverB: 17 gr3 procs, 1328 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 74660 lines pending; fleet rate 4846 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 15.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-ASIA has no line for 100 min, G:agent W-GRIDOPS has no line for 182 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 0 min ago, agent line 21 min ago (16:09Z) | 1 of 147 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 24 min ago, agent line 110 min ago (14:40Z) | 1 of 147 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 56 min ago (15:34Z) [cron-owned: exempt] | 105 of 147 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 25 min ago, agent line 3.2 h ago (13:18Z) | 22 of 147 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 30 min ago, agent line 67 min ago (15:23Z) | 0 of 147 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 16.2 h ago (00:20Z) | 0 of 147 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 77 min ago (15:13Z) | 0 of 147 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 6.6 h ago, agent line 81 min ago (15:09Z) | 0 of 147 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 15 min ago, agent line 56 min ago (15:34Z) | 0 of 147 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 5 min ago, agent line 74 min ago (15:16Z) [cron-owned: exempt] | 0 of 147 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 70 min ago, agent line 15 min ago (16:15Z) [cron-owned: exempt] | 0 of 147 entries | fl_status.py cron; no supervised loops |
Alert G now: agent W-ASIA has no line for 110 min; agent W-GRIDOPS has no line for 192 min; agent W-SHORT has no line for 67 min
G: agent W-ASIA has no line for 100 min UNANSWERED since 16:20Z
