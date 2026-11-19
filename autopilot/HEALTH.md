# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T06:10:01Z | CORES reading: 2026-11-19 06:05Z | guard sample: 2026-11-19T06:00:01Z
Lead: last LEAD NOTE 20 min ago | last transcript activity 9 min ago | last watchdog line: 2026-11-19 05:42Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T06:09Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 58.79 | 10 | 194 | 19 | 724 | n/a | n/a | 297 | 61.1 (-0.168 GB/h, n/a h) |
| server2 | 100 | 64 | 104.1 | 12 | 2248 | 0 | 85 | 125209 | 27.8 h | 26867 | 407.5 (0.026 GB/h, n/a h) |
| serverA | 100 | 128 | 199.84 | 61 (grid) + 66 (engine) | 640 | 0 | 256 | 83100 | 64.9 h | 6299 | 829.9 (0.011 GB/h, n/a h) |
| serverB | 100 | 128 | 193.9 | 61 (grid) + 69 (engine) | 343 | 0 | 296 | 76933 | 112.1 h | 6274 | 412.2 (0.013 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 189973 lines pending; fleet rate 2722 set-months/h => 69.8 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 220 min ago (02:30Z) | 1 of 144 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 66 min ago (05:04Z) | 1 of 144 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 107 of 144 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 5 min ago (06:05Z) | 16 of 144 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 91 min ago (04:39Z) | 0 of 144 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 350 min ago (00:20Z) | 0 of 144 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 222 min ago (02:28Z) | 0 of 144 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 95 min ago (04:35Z) | 0 of 144 entries | guard/health crons (th_night); agent only edits |
Alert G now: agent W-NYENG has no line for 220 min; agent W-SHORT has no line for 91 min
