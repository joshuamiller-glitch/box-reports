# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T15:08:57Z | CORES reading: 2026-11-19 15:05Z | guard sample: 2026-11-19T15:08:39Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 15:02Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T15:08Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 96.43 | 31 | 49 | 10 | 1787 | n/a | n/a | 293 | 60.1 (0.131 GB/h, 458.4 h) |
| server2 | ? | 64 | ? | ? | 2212 | 10 | 366 | 112229 | 25.4 h | 26562 | 407.3 (0.028 GB/h, n/a h) |
| serverA | 100 | 128 | 254.89 | 105 (grid) + 100 (engine) | 553 | 0 | 732 | 75624 | 68.4 h | 6258 | 829.8 (0.018 GB/h, n/a h) |
| serverB | 100 | 128 | 216.34 | 105 (grid) + 102 (engine) | 158 | 0 | 722 | 61006 | 193.1 h | 6207 | 412.0 (0.022 GB/h, n/a h) |

questions for Josh: 7 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 31/36 (86%); server2 24/28 (86%); serverA 102/102 (100%); serverB 101/102 (99%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T15:05Z): box1 18/22 (82%); Dallas 1/22 (5%); Frankfurt 50/100 (50%); Singapore 50/102 (49%); fleet 48%; exact-path kinds: TL3_NYE_L<h>_RM7CTN 70, TL3_NYE_L<h>_RH7CTN 35, TL3_NYE_L<h>_RP7CTN 18, TL3_CMB_IDN 2, TL3_CMB_S_L<h>_RPN 2

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 8 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 15 gr3 procs, 1027 XC records, B-C tasks 433/576 done (143 left); serverA: 17 gr3 procs, 1142 XC records, B-C tasks 705/1133 done (428 left); serverB: 31 gr3 procs, 1128 XC records, B-C tasks 567/1290 done (723 left)

Engine queue (shared by box 1, server 2, A, B): 75046 lines pending; fleet rate 3574 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 21.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-EXITENG has no line for 61 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 9 min ago, agent line -4 min ago (15:13Z) | 1 of 128 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 3 min ago, agent line 29 min ago (14:40Z) | 1 of 128 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 86 of 128 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 4 min ago, agent line 111 min ago (13:18Z) | 22 of 128 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 9 min ago, agent line 39 min ago (14:30Z) | 0 of 128 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 14.8 h ago (00:20Z) | 0 of 128 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line -4 min ago (15:13Z) | 0 of 128 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 5.2 h ago, agent line 28 min ago (14:41Z) | 0 of 128 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 24 min ago, agent line 62 min ago (14:07Z) | 0 of 128 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 14 min ago, agent line 54 min ago (14:15Z) [cron-owned: exempt] | 0 of 128 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 14 min ago, agent line 9 min ago (15:00Z) [cron-owned: exempt] | 0 of 128 entries | fl_status.py cron; no supervised loops |
Alert G now: agent W-EXITENG has no line for 61 min
G: agent W-EXITENG has no line for 61 min UNANSWERED since 15:08Z
