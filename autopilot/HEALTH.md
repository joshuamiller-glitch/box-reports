# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T10:00:01Z | CORES reading: 2026-11-19 09:55Z | guard sample: 2026-11-19T09:58:42Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 09:56Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T09:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 77.02 | 25 | 253 | 26 | 1221 | n/a | n/a | 295 | 60.7 (0.104 GB/h, 582.8 h) |
| server2 | 100 | 64 | 115.86 | 27 | 3629 | 26 | 232 | 119465 | 16.5 h | 26756 | 407.4 (0.02 GB/h, n/a h) |
| serverA | 100 | 128 | 242.14 | 77 (grid) + 101 (engine) | 804 | 0 | 448 | 79796 | 49.6 h | 6284 | 829.9 (0.013 GB/h, n/a h) |
| serverB | 100 | 128 | 245.93 | 77 (grid) + 96 (engine) | 430 | 0 | 520 | 73954 | 86.0 h | 6256 | 412.1 (0.017 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 133703 lines pending; fleet rate 2442 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 54.8 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-SHORT has no line for 223 min, G:agent W-EXITENG has no line in the log, G:agent W-LAYERS has no line in the log

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 0 min ago, agent line 3 min ago (09:57Z) | 1 of 142 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | cron line 25 min ago, agent line 71 min ago (08:49Z) | 1 of 142 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 106 of 142 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 55 min ago, agent line 16 min ago (09:44Z) | 15 of 142 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 30 min ago, agent line 1 min ago (09:59Z) | 0 of 142 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 9.7 h ago (00:20Z) | 0 of 142 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 7.5 h ago (02:28Z) | 0 of 142 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 3 min ago, agent line 2 min ago (09:58Z) | 0 of 142 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | no cron line, no agent line found | 0 of 142 entries | cron status line from its state file |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | running | no cron line, no agent line found | 0 of 142 entries | cron every 30 min |
Alert G now: agent W-EXITENG has no line in the log; agent W-LAYERS has no line in the log
G: agent W-SHORT has no line for 223 min UNANSWERED since 09:58Z
G: agent W-EXITENG has no line in the log UNANSWERED since 09:58Z
G: agent W-LAYERS has no line in the log UNANSWERED since 09:58Z
