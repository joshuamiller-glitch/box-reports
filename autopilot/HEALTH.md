# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:50:01Z | CORES reading: 2026-11-19 04:45Z | guard sample: 2026-11-19T04:40:01Z
Lead: last LEAD NOTE 9 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-19 04:22Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T04:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.44 | 24 | 66 | 9 | 486 | n/a | n/a | 298 | 61.2 (-0.165 GB/h, n/a h) |
| server2 | 100 | 64 | 105.81 | 13 | 3150 | 9 | 82 | 136225 | 21.6 h | 26918 | 407.6 (0.025 GB/h, n/a h) |
| serverA | 100 | 128 | 178.78 | 61 (grid) + 73 (engine) | 313 | 0 | 136 | 85098 | 135.9 h | 6305 | 829.9 (0.009 GB/h, n/a h) |
| serverB | 100 | 128 | 166.38 | 61 (grid) + 69 (engine) | 1456 | 0 | 175 | 79335 | 27.2 h | 6283 | 412.2 (0.013 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 163382 lines pending; fleet rate 1758 set-months/h => 92.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 140 min ago (02:30Z) | 1 of 145 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 42 min ago (04:08Z) | 1 of 145 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 108 of 145 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 42 min ago (04:08Z) | 16 of 145 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 11 min ago (04:39Z) | 0 of 145 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 270 min ago (00:20Z) | 0 of 145 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 142 min ago (02:28Z) | 0 of 145 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 15 min ago (04:35Z) | 0 of 145 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
