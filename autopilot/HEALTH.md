# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:40:01Z | CORES reading: 2026-11-19 04:35Z | guard sample: 2026-11-19T04:34:52Z
Lead: last LEAD NOTE 1 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-19 04:22Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T04:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 77.87 | 27 | 92 | 9 | 489 | n/a | n/a | 298 | 61.2 (-0.16 GB/h, n/a h) |
| server2 | 100 | 64 | 101.18 | 14 | 3194 | 9 | 80 | 136225 | 21.3 h | 26919 | 407.6 (0.028 GB/h, n/a h) |
| serverA | 100 | 128 | 171.63 | 61 (grid) + 75 (engine) | 261 | 0 | 134 | 85098 | 163.0 h | 6306 | 829.9 (0.009 GB/h, n/a h) |
| serverB | 100 | 128 | 156.97 | 61 (grid) + 67 (engine) | 1345 | 0 | 178 | 79335 | 29.5 h | 6284 | 412.2 (0.011 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 156690 lines pending; fleet rate 1762 set-months/h => 88.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 130 min ago (02:30Z) | 1 of 145 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 32 min ago (04:08Z) | 1 of 145 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 108 of 145 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 32 min ago (04:08Z) | 16 of 145 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 1 min ago (04:39Z) | 0 of 145 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 260 min ago (00:20Z) | 0 of 145 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 132 min ago (02:28Z) | 0 of 145 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 5 min ago (04:35Z) | 0 of 145 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
