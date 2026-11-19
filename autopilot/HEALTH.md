# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T15:00:00Z | CORES reading: 2026-11-19 14:55Z | guard sample: 2026-11-19T14:50:01Z
Lead: last LEAD NOTE 1 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 14:24Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T14:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 77.61 | 30 | 59 | 15 | 1202 | n/a | n/a | 293 | 60.2 (0.113 GB/h, 531.4 h) |
| server2 | ? | 64 | ? | ? | 2638 | 15 | 204 | 112229 | 21.3 h | 26571 | 407.3 (0.029 GB/h, n/a h) |
| serverA | 100 | 128 | 234.02 | 105 (grid) + 99 (engine) | 519 | 0 | 561 | 76192 | 73.4 h | 6258 | 829.8 (0.02 GB/h, n/a h) |
| serverB | 100 | 128 | 237.83 | 105 (grid) + 101 (engine) | 1088 | 0 | 480 | 61161 | 28.1 h | 6208 | 412.0 (0.021 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 34/36 (94%); server2 28/28 (100%); serverA 108/102 (106%); serverB 85/102 (83%)

Engine queue (shared by box 1, server 2, A, B): 75201 lines pending; fleet rate 2404 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 31.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 0 min ago, agent line -5 min ago (15:05Z) | 1 of 128 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 24 min ago, agent line 20 min ago (14:40Z) | 1 of 128 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 86 of 128 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 55 min ago, agent line 102 min ago (13:18Z) | 22 of 128 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 30 min ago, agent line 30 min ago (14:30Z) | 0 of 128 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 14.7 h ago (00:20Z) | 0 of 128 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 7 min ago (14:53Z) | 0 of 128 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 5.1 h ago, agent line 19 min ago (14:41Z) | 0 of 128 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 15 min ago, agent line 53 min ago (14:07Z) | 0 of 128 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 5 min ago, agent line 45 min ago (14:15Z) [cron-owned: exempt] | 0 of 128 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 5 min ago, agent line 1 min ago (14:59Z) [cron-owned: exempt] | 0 of 128 entries | fl_status.py cron; no supervised loops |
Alert G now: none
