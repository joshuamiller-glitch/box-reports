# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T09:25:01Z | CORES reading: 2026-11-19 09:20Z | guard sample: 2026-11-19T09:20:01Z
Lead: last LEAD NOTE 17 min ago | last transcript activity 7 min ago | last watchdog line: 2026-11-19 09:22Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T09:24Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 75.89 | 28 | 560 | 10 | 1225 | n/a | n/a | 296 | 61.0 (0.03 GB/h, n/a h) |
| server2 | 100 | 64 | 105.62 | 30 | 2034 | 10 | 236 | 119039 | 29.3 h | 26779 | 407.5 (0.021 GB/h, n/a h) |
| serverA | 100 | 128 | 200.49 | 37 (grid) + 101 (engine) | 227 | 0 | 437 | 81356 | 179.2 h | 6288 | 829.9 (0.018 GB/h, n/a h) |
| serverB | 100 | 128 | 209.32 | 37 (grid) + 101 (engine) | 236 | 0 | 495 | 75086 | 159.1 h | 6257 | 412.1 (0.02 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 132910 lines pending; fleet rate 2450 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 54.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-NYENG has no line for 183 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 188 min ago (06:17Z) | 1 of 143 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 20 min ago (09:05Z) | 1 of 143 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 106 of 143 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 20 min ago (09:05Z) | 16 of 143 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 25 min ago (09:00Z) | 0 of 143 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 545 min ago (00:20Z) | 0 of 143 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 417 min ago (02:28Z) | 0 of 143 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 188 min ago (06:17Z) | 0 of 143 entries | guard/health crons (th_night); agent only edits |
Alert G now: agent W-NYENG has no line for 188 min
G: agent W-NYENG has no line for 183 min UNANSWERED since 09:20Z
