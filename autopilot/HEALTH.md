# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T13:45:01Z | CORES reading: 2026-11-19 13:40Z | guard sample: 2026-11-19T13:40:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 13:42Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T13:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 88.52 | 31 | 107 | 24 | 1786 | n/a | n/a | 293 | 60.4 (0.076 GB/h, 798.3 h) |
| server2 | 100 | 64 | 146.57 | 30 | 781 | 5 | 329 | 114632 | 73.4 h | 26629 | 407.4 (0.021 GB/h, n/a h) |
| serverA | 100 | 128 | 265.57 | 105 (grid) + 116 (engine) | 513 | 0 | 629 | 76720 | 74.8 h | 6266 | 829.8 (0.022 GB/h, n/a h) |
| serverB | 100 | 128 | 196.4 | 105 (grid) + 55 (engine) | 1360 | 0 | 750 | 65064 | 23.9 h | 6218 | 412.0 (0.027 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 173351 lines pending; fleet rate 3572 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 48.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-EXITENG has no line for 68 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 15 min ago, agent line 4 min ago (13:41Z) | 1 of 148 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 9 min ago, agent line 9 min ago (13:36Z) | 1 of 148 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 106 of 148 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 40 min ago, agent line 27 min ago (13:18Z) | 22 of 148 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 15 min ago, agent line 27 min ago (13:18Z) | 0 of 148 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 13.4 h ago (00:20Z) | 0 of 148 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 11.3 h ago (02:28Z) | 0 of 148 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 3.8 h ago, agent line 3.5 h ago (10:15Z) | 0 of 148 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 30 min ago, agent line 73 min ago (12:32Z) | 0 of 148 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 9 min ago, agent line 9 min ago (13:36Z) [cron-owned: exempt] | 0 of 148 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 25 min ago, agent line 7 min ago (13:38Z) [cron-owned: exempt] | 0 of 148 entries | fl_status.py cron; no supervised loops |
Alert G now: agent W-EXITENG has no line for 73 min
G: agent W-EXITENG has no line for 68 min UNANSWERED since 13:40Z
