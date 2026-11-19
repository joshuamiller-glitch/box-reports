# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T10:05:01Z | CORES reading: 2026-11-19 10:00Z | guard sample: 2026-11-19T10:00:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 09:56Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T10:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 71.57 | 23 | 265 | 26 | 1250 | n/a | n/a | 295 | 60.7 (0.105 GB/h, 576.3 h) |
| server2 | 100 | 64 | 121.32 | 29 | 3673 | 26 | 231 | 119465 | 16.3 h | 26756 | 407.4 (0.021 GB/h, n/a h) |
| serverA | 100 | 128 | 240.6 | 77 (grid) + 97 (engine) | 829 | 0 | 447 | 79796 | 48.1 h | 6284 | 829.9 (0.015 GB/h, n/a h) |
| serverB | 100 | 128 | 245.99 | 77 (grid) + 100 (engine) | 447 | 0 | 512 | 73954 | 82.7 h | 6255 | 412.1 (0.018 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 133090 lines pending; fleet rate 2500 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 53.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 5 min ago, agent line 8 min ago (09:57Z) | 1 of 144 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | cron line 30 min ago, agent line 76 min ago (08:49Z) | 1 of 144 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 106 of 144 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 60 min ago, agent line 21 min ago (09:44Z) | 17 of 144 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 5 min ago, agent line 6 min ago (09:59Z) | 0 of 144 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 9.8 h ago (00:20Z) | 0 of 144 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 7.6 h ago (02:28Z) | 0 of 144 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 8 min ago, agent line 7 min ago (09:58Z) | 0 of 144 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | no cron line, agent line 2 min ago (10:03Z) | 0 of 144 entries | cron status line from its state file |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 4 min ago, agent line 3 min ago (10:02Z) [cron-owned: exempt] | 0 of 144 entries | cron every 30 min |
Alert G now: none
G: agent W-SHORT has no line for 223 min UNANSWERED since 09:58Z
G: agent W-EXITENG has no line in the log UNANSWERED since 09:58Z
G: agent W-LAYERS has no line in the log UNANSWERED since 09:58Z
