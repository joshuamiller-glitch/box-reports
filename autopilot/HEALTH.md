# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T20:20:02Z | CORES reading: 2026-11-19 20:15Z | guard sample: 2026-11-19T20:10:01Z
Lead: last LEAD NOTE 5 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-19 20:12Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-19T20:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 75.37 | 26 | 25 | 62 | 2642 | n/a | n/a | 288 | 58.6 (0.301 GB/h, 194.3 h) |
| server2 | 100 | 64 | 131.86 | 28 | 1762 | 62 | 451 | 97972 | 27.8 h | 26298 | 407.2 (0.026 GB/h, n/a h) |
| serverA | 100 | 128 | 236.78 | 105 (grid) + 99 (engine) | 908 | 0 | 840 | 70899 | 39.0 h | 6240 | 829.7 (0.011 GB/h, n/a h) |
| serverB | 100 | 128 | 218.09 | 105 (grid) + 101 (engine) | 124 | 0 | 950 | 54857 | 221.2 h | 6178 | 411.9 (0.014 GB/h, n/a h) |
| serverC | 2 | 128 | 2.96 | 1 (grid) + 3 (engine) | 0 | 0 | 3 | 0 | n/a | 27738 | 411.4 (None GB/h, n/a h) |

questions for Josh: 12 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: serverC 2%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 22/36 (61%); server2 27/28 (96%); serverA 101/102 (99%); serverB 99/102 (97%); serverC 3/3 (100%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T20:15Z): box1 18/18 (100%); Dallas 26/28 (93%); Frankfurt 74/99 (75%); Singapore 79/101 (78%); C Amsterdam 3/3 (100%); fleet 80%; exact-path kinds: TL3_STK_NV4_noHN 6, TL3_STK_NV1_noLbN 6, TL3_STK_NV2_noLb44_L2bN 5, TL3_STK_NV3_SEL_L2bN 5, TL3_ASI_AX1_RHN 5. STK (multi-book stack sets) not fast-eligible, IDN identity sets excluded: not a fault (STK capped at 10%% of each remote host slots by the dispatchers)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 56544 lines pending; fleet rate 5284 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 10.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-ASIA has no line for 62 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 20 min ago, agent line 5 min ago (20:15Z) | 1 of 145 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 14 min ago, agent line 6 min ago (20:14Z) | 1 of 145 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 48 min ago (19:32Z) [cron-owned: exempt] | 104 of 145 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 15 min ago, agent line -5 min ago (20:25Z) | 22 of 145 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 20 min ago, agent line -2 min ago (20:22Z) | 0 of 145 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 20.0 h ago (00:20Z) | 0 of 145 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 2 min ago (20:18Z) | 0 of 145 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 10.4 h ago, agent line 5.2 h ago (15:09Z) | 0 of 145 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 5 min ago, agent line 8 min ago (20:12Z) | 0 of 145 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 25 min ago, agent line 2.1 h ago (18:15Z) [cron-owned: exempt] | 0 of 145 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 30 min ago, agent line 7 min ago (20:13Z) [cron-owned: exempt] | 0 of 145 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 79 min ago (19:01Z) [cron-owned: exempt] | 0 of 145 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | running | no cron line, agent line 48 min ago (19:32Z) | 0 of 145 entries | agent lines 'W-XB1 STATUS n' |
| W-XB2 | code/th_exiteng/xb2_*.py | yes | running | no cron line, agent line 8 min ago (20:12Z) | 0 of 145 entries | agent lines 'W-XB2 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 57 min ago, agent line 17 min ago (20:03Z) | 0 of 145 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | no cron line, agent line 34 min ago (19:46Z) | 0 of 145 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 3 min ago, agent line 58 min ago (19:22Z) [cron-owned: exempt] | 0 of 145 entries | cron lines |
| W-SRVC | compute-pool setup | yes | running | no cron line, agent line 22 min ago (19:58Z) | 0 of 145 entries | agent lines 'W-SRVC' |
| W-SRVD | compute-pool setup | yes | running | no cron line, agent line 44 min ago (19:36Z) | 0 of 145 entries | agent lines 'W-SRVD' |
Alert G now: none
