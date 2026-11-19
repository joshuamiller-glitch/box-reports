# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T17:58:29Z | CORES reading: 2026-11-19 17:55Z | guard sample: 2026-11-19T17:50:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 16:44Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T17:58Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 79.5 | 33 | 271 | 79 | 1953 | n/a | n/a | 291 | 59.2 (0.328 GB/h, 180.5 h) |
| server2 | ? | 64 | ? | ? | 2269 | 63 | 493 | 102782 | 22.6 h | 26406 | 407.2 (0.028 GB/h, n/a h) |
| serverA | 100 | 128 | 234.19 | 105 (grid) + 96 (engine) | 566 | 0 | 976 | 73807 | 65.2 h | 6251 | 829.7 (0.017 GB/h, n/a h) |
| serverB | 100 | 128 | 182.19 | 105 (grid) + 18 (engine) | 1214 | 0 | 1011 | 57726 | 23.8 h | 6190 | 411.9 (0.019 GB/h, n/a h) |

questions for Josh: 8 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 33/36 (92%); server2 28/28 (100%); serverA 102/102 (100%); serverB 98/102 (96%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T17:55Z): box1 25/32 (78%); Dallas 20/20 (100%); Frankfurt 84/98 (86%); Singapore 19/19 (100%); fleet 88%; exact-path kinds: TL3_EXE_L<h>_ref_v15_t2_RP7_DC 6, TL3_EXE_L<h>_bricks3_v25_RP7_DC 6, TL3_LON_LA1_ALL 4, TL3_EXE_L<h>_bricks3_v25_RM7_DC 2, TL3_EXE_L<h>_neutral_v25_FLOWN_IDN 1

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 14 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 44 gr3 procs, 1487 XC records, B-C tasks 20/20 done (0 left); serverB: 26 gr3 procs, 1400 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 77478 lines pending; fleet rate 3906 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 19.8 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-ASIA has no line for 64 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 8 min ago, agent line 2 min ago (17:56Z) | 1 of 146 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 23 min ago, agent line 6 min ago (17:52Z) | 1 of 146 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 54 min ago (17:04Z) [cron-owned: exempt] | 104 of 146 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 53 min ago, agent line 11 min ago (17:47Z) | 22 of 146 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 28 min ago, agent line 41 min ago (17:17Z) | 0 of 146 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 17.6 h ago (00:20Z) | 0 of 146 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 32 min ago (17:26Z) | 0 of 146 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 8.0 h ago, agent line 2.8 h ago (15:09Z) | 0 of 146 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 13 min ago, agent line 6 min ago (17:52Z) | 0 of 146 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 3 min ago, agent line 2.7 h ago (15:16Z) [cron-owned: exempt] | 0 of 146 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 8 min ago, agent line 103 min ago (16:15Z) [cron-owned: exempt] | 0 of 146 entries | fl_status.py cron; no supervised loops |
Alert G now: none
