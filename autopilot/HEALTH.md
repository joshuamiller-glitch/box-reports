# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T14:40:01Z | CORES reading: 2026-11-19 14:35Z | guard sample: 2026-11-19T14:30:02Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 14:24Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T14:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 86.71 | 33 | 41 | 33 | 886 | n/a | n/a | 293 | 60.3 (0.088 GB/h, 688.6 h) |
| server2 | 100 | 64 | 131.41 | 30 | 842 | 29 | 127 | 113935 | 67.7 h | 26583 | 407.3 (0.027 GB/h, n/a h) |
| serverA | 100 | 128 | 238.06 | 105 (grid) + 102 (engine) | 451 | 0 | 403 | 76205 | 84.5 h | 6259 | 829.8 (0.02 GB/h, n/a h) |
| serverB | 100 | 128 | 235.21 | 105 (grid) + 99 (engine) | 2964 | 0 | 320 | 61220 | 10.3 h | 6209 | 412.0 (0.022 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 74390 lines pending; fleet rate 1772 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 42.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 10 min ago, agent line 2 min ago (14:38Z) | 1 of 128 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 4 min ago, agent line 27 min ago (14:13Z) | 1 of 128 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 86 of 128 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 35 min ago, agent line 82 min ago (13:18Z) | 22 of 128 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 10 min ago, agent line 10 min ago (14:30Z) | 0 of 128 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 14.3 h ago (00:20Z) | 0 of 128 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 12.2 h ago (02:28Z) | 0 of 128 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 4.7 h ago, agent line 4.4 h ago (10:15Z) | 0 of 128 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 25 min ago, agent line 33 min ago (14:07Z) | 0 of 128 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 15 min ago, agent line 25 min ago (14:15Z) [cron-owned: exempt] | 0 of 128 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 20 min ago, agent line 1 min ago (14:39Z) [cron-owned: exempt] | 0 of 128 entries | fl_status.py cron; no supervised loops |
Alert G now: none
