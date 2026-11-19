# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T16:15:01Z | CORES reading: 2026-11-19 16:10Z | guard sample: 2026-11-19T16:10:01Z
Lead: last LEAD NOTE 9 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 15:58Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T16:14Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 84.43 | 31 | 56 | 33 | 2430 | n/a | n/a | 292 | 59.8 (0.201 GB/h, 297.2 h) |
| server2 | ? | 64 | ? | ? | 1646 | 33 | 474 | 108495 | 33.0 h | 26518 | 407.3 (0.034 GB/h, n/a h) |
| serverA | 100 | 128 | 253.18 | 105 (grid) + 102 (engine) | 360 | 0 | 998 | 75060 | 104.2 h | 6255 | 829.8 (0.015 GB/h, n/a h) |
| serverB | 100 | 128 | 227.0 | 105 (grid) + 99 (engine) | 148 | 0 | 1074 | 60808 | 205.4 h | 6203 | 412.0 (0.022 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 31/36 (86%); server2 28/28 (100%); serverA 98/102 (96%); serverB 94/102 (92%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T16:10Z): box1 23/29 (79%); Dallas 28/28 (100%); Frankfurt 98/98 (100%); Singapore 101/101 (100%); fleet 98%; exact-path kinds: TL3_CMB_MN 6

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 15 gr3 procs, 1161 XC records, B-C tasks 567/576 done (9 left); serverA: 17 gr3 procs, 1389 XC records, B-C tasks 952/1133 done (181 left); serverB: 31 gr3 procs, 1320 XC records, B-C tasks 759/1290 done (531 left)

Engine queue (shared by box 1, server 2, A, B): 73413 lines pending; fleet rate 4860 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 15.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 15 min ago, agent line 6 min ago (16:09Z) | 1 of 147 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 9 min ago, agent line 95 min ago (14:40Z) | 1 of 147 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 41 min ago (15:34Z) [cron-owned: exempt] | 105 of 147 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 10 min ago, agent line 3.0 h ago (13:18Z) | 22 of 147 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 15 min ago, agent line 52 min ago (15:23Z) | 0 of 147 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 15.9 h ago (00:20Z) | 0 of 147 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 62 min ago (15:13Z) | 0 of 147 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 6.3 h ago, agent line 66 min ago (15:09Z) | 0 of 147 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 30 min ago, agent line 41 min ago (15:34Z) | 0 of 147 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 20 min ago, agent line 59 min ago (15:16Z) [cron-owned: exempt] | 0 of 147 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 55 min ago, agent line 6 min ago (16:09Z) [cron-owned: exempt] | 0 of 147 entries | fl_status.py cron; no supervised loops |
Alert G now: agent W-ASIA has no line for 95 min
