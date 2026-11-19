# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T07:55:01Z | CORES reading: 2026-11-19 07:50Z | guard sample: 2026-11-19T07:50:01Z
Lead: last LEAD NOTE 13 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 07:40Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T07:54Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 73.67 | 28 | 182 | 36 | 1080 | n/a | n/a | 297 | 61.1 (0.034 GB/h, n/a h) |
| server2 | 100 | 64 | 113.39 | 27 | 1491 | 36 | 175 | 121937 | 40.9 h | 26819 | 407.5 (0.023 GB/h, n/a h) |
| serverA | 100 | 128 | 229.14 | 61 (grid) + 96 (engine) | 307 | 0 | 388 | 82128 | 133.8 h | 6294 | 829.9 (0.015 GB/h, n/a h) |
| serverB | 100 | 128 | 204.2 | 37 (grid) + 92 (engine) | 176 | 0 | 451 | 76185 | 216.4 h | 6265 | 412.2 (0.017 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 131348 lines pending; fleet rate 2160 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 60.8 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 98 min ago (06:17Z) | 1 of 143 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 20 min ago (07:35Z) | 1 of 143 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 106 of 143 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 8 min ago (07:47Z) | 16 of 143 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 25 min ago (07:30Z) | 0 of 143 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 455 min ago (00:20Z) | 0 of 143 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 327 min ago (02:28Z) | 0 of 143 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 98 min ago (06:17Z) | 0 of 143 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
