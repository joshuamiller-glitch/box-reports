# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T05:15:01Z | CORES reading: 2026-11-19 05:10Z | guard sample: 2026-11-19T05:10:01Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 04:22Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T05:14Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.23 | 27 | 110 | 10 | 460 | n/a | n/a | 298 | 61.1 (-0.163 GB/h, n/a h) |
| server2 | 100 | 64 | 72.69 | 13 | 5347 | 10 | 82 | 131371 | 12.3 h | 26892 | 407.5 (0.026 GB/h, n/a h) |
| serverA | 100 | 128 | 190.99 | 61 (grid) + 51 (engine) | 837 | 0 | 142 | 84676 | 50.6 h | 6302 | 829.9 (0.009 GB/h, n/a h) |
| serverB | 100 | 128 | 184.29 | 61 (grid) + 48 (engine) | 897 | 0 | 154 | 77988 | 43.5 h | 6280 | 412.2 (0.015 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 170930 lines pending; fleet rate 1676 set-months/h => 102.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md line | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | 165 min ago (02:30Z) | 1 of 144 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | 11 min ago (05:04Z) | 1 of 144 entries | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | finished 03:2xZ (workers + cron keep run | no line found | 107 of 144 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | 8 min ago (05:07Z) | 16 of 144 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | 36 min ago (04:39Z) | 0 of 144 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | 295 min ago (00:20Z) | 0 of 144 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | 167 min ago (02:28Z) | 0 of 144 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | 40 min ago (04:35Z) | 0 of 144 entries | guard/health crons (th_night); agent only edits |
Alert G now: none
