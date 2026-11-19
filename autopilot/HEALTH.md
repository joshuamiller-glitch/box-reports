# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T06:20:01Z | CORES reading: 2026-11-19 06:15Z | guard sample: 2026-11-19T06:17:34Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 05:42Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T06:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.0 | 19 | 257 | 19 | 699 | n/a | n/a | 297 | 61.1 (-0.192 GB/h, n/a h) |
| server2 | 100 | 64 | 101.52 | 7 | 1720 | 19 | 82 | 124075 | 36.1 h | 26860 | 407.5 (0.025 GB/h, n/a h) |
| serverA | 100 | 128 | 190.76 | 61 (grid) + 52 (engine) | 292 | 0 | 262 | 82806 | 141.8 h | 6298 | 829.9 (0.015 GB/h, n/a h) |
| serverB | 100 | 128 | 174.71 | 61 (grid) + 41 (engine) | 373 | 0 | 292 | 76673 | 102.8 h | 6272 | 412.2 (0.019 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 194594 lines pending; fleet rate 1398 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 139.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 3 min ago (06:17Z) | 1 of 144 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 8 min ago (06:12Z) | 1 of 144 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 107 of 144 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 6 min ago (06:14Z) | 16 of 144 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 5 min ago (06:15Z) | 0 of 144 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 360 min ago (00:20Z) | 0 of 144 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 232 min ago (02:28Z) | 0 of 144 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 3 min ago (06:17Z) | 0 of 144 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
