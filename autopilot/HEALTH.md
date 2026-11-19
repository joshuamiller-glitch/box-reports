# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T18:40:01Z | CORES reading: 2026-11-19 18:35Z | guard sample: 2026-11-19T18:30:01Z
Lead: last LEAD NOTE 4 min ago | last transcript activity 7 min ago | last watchdog line: 2026-11-19 18:38Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T18:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.19 | 31 | 447 | 85 | 2253 | n/a | n/a | 290 | 59.0 (0.332 GB/h, 177.5 h) |
| server2 | 100 | 64 | 161.13 | 28 | 3108 | 83 | 490 | 101972 | 16.4 h | 26374 | 407.2 (0.028 GB/h, n/a h) |
| serverA | 100 | 128 | 236.26 | 105 (grid) + 101 (engine) | 465 | 0 | 932 | 73134 | 78.6 h | 6249 | 829.7 (0.019 GB/h, n/a h) |
| serverB | 100 | 128 | 224.08 | 105 (grid) + 100 (engine) | 1251 | 0 | 1006 | 56558 | 22.6 h | 6185 | 411.9 (0.023 GB/h, n/a h) |

questions for Josh: 9 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 31/36 (86%); server2 28/28 (100%); serverA 99/102 (97%); serverB 97/102 (95%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T18:35Z): box1 21/31 (68%); Dallas 28/28 (100%); Frankfurt 100/100 (100%); Singapore 102/102 (100%); fleet 96%; exact-path kinds: TL3_LON_WL9_RKN 3, TL3_LON_WL7_RMN 2, TL3_EXE_L<h>_sar_v60_ADD_IDN 1, TL3_EXE_L<h>_neutral_v25_PLAIN_IDN 1, TL3_EXE_L<h>_neutral_v25_SARN_IDN 1

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 65530 lines pending; fleet rate 4506 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 14.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 10 min ago, agent line 4 min ago (18:36Z) | 1 of 146 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 4 min ago, agent line 2 min ago (18:38Z) | 1 of 146 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 96 min ago (17:04Z) [cron-owned: exempt] | 104 of 146 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 35 min ago, agent line 0 min ago (18:40Z) | 22 of 146 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 10 min ago, agent line 83 min ago (17:17Z) | 0 of 146 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 18.3 h ago (00:20Z) | 0 of 146 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 74 min ago (17:26Z) | 0 of 146 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 8.7 h ago, agent line 3.5 h ago (15:09Z) | 0 of 146 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 25 min ago, agent line 48 min ago (17:52Z) | 0 of 146 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 15 min ago, agent line 25 min ago (18:15Z) [cron-owned: exempt] | 0 of 146 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 20 min ago, agent line 2.4 h ago (16:15Z) [cron-owned: exempt] | 0 of 146 entries | fl_status.py cron; no supervised loops |
Alert G now: agent W-SHORT has no line for 83 min
G: agent W-SHORT has no line for 73 min UNANSWERED since 18:20Z
