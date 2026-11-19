# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T09:40:02Z | CORES reading: 2026-11-19 09:35Z | guard sample: 2026-11-19T09:30:01Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 09:22Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T09:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 77.25 | 26 | 449 | 10 | 1187 | n/a | n/a | 296 | 61.0 (0.03 GB/h, n/a h) |
| server2 | 100 | 64 | 125.13 | 28 | 1823 | 10 | 227 | 119092 | 32.7 h | 26776 | 407.5 (0.018 GB/h, n/a h) |
| serverA | 100 | 128 | 197.06 | 37 (grid) + 98 (engine) | 259 | 0 | 442 | 81356 | 157.1 h | 6287 | 829.9 (0.018 GB/h, n/a h) |
| serverB | 100 | 128 | 206.3 | 37 (grid) + 93 (engine) | 197 | 0 | 484 | 75086 | 190.6 h | 6257 | 412.1 (0.02 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 133541 lines pending; fleet rate 2374 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 56.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 203 min ago (06:17Z) | 1 of 144 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 5 min ago (09:35Z) | 1 of 144 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 106 of 144 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 35 min ago (09:05Z) | 17 of 144 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 10 min ago (09:30Z) | 0 of 144 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 560 min ago (00:20Z) | 0 of 144 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 432 min ago (02:28Z) | 0 of 144 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 203 min ago (06:17Z) | 0 of 144 entries | guard/health crons (th_night); agent only edits |
Alert G now: agent W-NYENG has no line for 203 min
G: agent W-NYENG has no line for 193 min UNANSWERED since 09:20Z
