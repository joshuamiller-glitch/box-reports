# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T09:05:01Z | CORES reading: 2026-11-19 09:00Z | guard sample: 2026-11-19T09:00:01Z
Lead: last LEAD NOTE 15 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-19 07:40Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T09:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 68.1 | 27 | 429 | 9 | 1122 | n/a | n/a | 296 | 61.0 (0.03 GB/h, n/a h) |
| server2 | 100 | 64 | 106.35 | 29 | 2181 | 9 | 208 | 120459 | 27.6 h | 26791 | 407.5 (0.021 GB/h, n/a h) |
| serverA | 100 | 128 | 205.78 | 37 (grid) + 100 (engine) | 286 | 0 | 403 | 81562 | 142.6 h | 6289 | 829.9 (0.016 GB/h, n/a h) |
| serverB | 100 | 128 | 207.89 | 37 (grid) + 100 (engine) | 406 | 0 | 458 | 75318 | 92.8 h | 6258 | 412.1 (0.02 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 128477 lines pending; fleet rate 2244 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 57.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 168 min ago (06:17Z) | 1 of 143 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 16 min ago (08:49Z) | 1 of 143 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 106 of 143 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 60 min ago (08:05Z) | 16 of 143 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 5 min ago (09:00Z) | 0 of 143 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 525 min ago (00:20Z) | 0 of 143 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 397 min ago (02:28Z) | 0 of 143 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 168 min ago (06:17Z) | 0 of 143 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
