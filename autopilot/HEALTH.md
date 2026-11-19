# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T19:40:01Z | CORES reading: 2026-11-19 19:35Z | guard sample: 2026-11-19T19:30:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 19:32Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T19:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 108.76 | 22 | 133 | 38 | 2750 | n/a | n/a | 289 | 58.7 (0.324 GB/h, 181.2 h) |
| server2 | 100 | 64 | 153.34 | 25 | 2135 | 38 | 462 | 99824 | 23.4 h | 26330 | 407.2 (0.03 GB/h, n/a h) |
| serverA | 100 | 128 | 241.9 | 105 (grid) + 98 (engine) | 313 | 0 | 850 | 72215 | 115.4 h | 6245 | 829.7 (0.017 GB/h, n/a h) |
| serverB | 100 | 128 | 209.24 | 105 (grid) + 99 (engine) | 248 | 0 | 970 | 55106 | 111.1 h | 6181 | 411.9 (0.018 GB/h, n/a h) |

questions for Josh: 12 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 33/36 (92%); server2 27/28 (96%); serverA 101/102 (99%); serverB 100/102 (98%)
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T19:35Z): box1 15/15 (100%); Dallas 23/25 (92%); Frankfurt 82/99 (83%); Singapore 77/100 (77%); fleet 82%; exact-path kinds: TL3_ASI_AX17_RHN 6, TL3_ASI_AX17_RAN 6, TL3_STK_AT_P7_L5c_Lc4e 3, TL3_STK_AD_PN 3, TL3_STK_AT_P7_L867_Lc4e 2. STK (multi-book stack sets) not fast-eligible, IDN identity sets excluded: not a fault (STK capped at 10%% of each remote host slots by the dispatchers)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 58676 lines pending; fleet rate 5500 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 10.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 10 min ago, agent line 5 min ago (19:35Z) | 1 of 145 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 4 min ago, agent line 32 min ago (19:08Z) | 1 of 145 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 8 min ago (19:32Z) [cron-owned: exempt] | 104 of 145 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 35 min ago, agent line -2 min ago (19:42Z) | 22 of 145 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 10 min ago, agent line -2 min ago (19:42Z) | 0 of 145 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 19.3 h ago (00:20Z) | 0 of 145 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 2.2 h ago (17:26Z) | 0 of 145 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 9.7 h ago, agent line 4.5 h ago (15:09Z) | 0 of 145 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 25 min ago, agent line 6 min ago (19:34Z) | 0 of 145 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 15 min ago, agent line 85 min ago (18:15Z) [cron-owned: exempt] | 0 of 145 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 20 min ago, agent line 3.4 h ago (16:15Z) [cron-owned: exempt] | 0 of 145 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 39 min ago (19:01Z) [cron-owned: exempt] | 0 of 145 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | running | no cron line, agent line 8 min ago (19:32Z) | 0 of 145 entries | agent lines 'W-XB1 STATUS n' |
| W-XB2 | code/th_exiteng/xb2_*.py | yes | running | no cron line, agent line 48 min ago (18:52Z) | 0 of 145 entries | agent lines 'W-XB2 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 17 min ago, agent line 11 min ago (19:29Z) | 0 of 145 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | no cron line, agent line 10 min ago (19:30Z) | 0 of 145 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 23 min ago, agent line 18 min ago (19:22Z) [cron-owned: exempt] | 0 of 145 entries | cron lines |
| W-SRVC | compute-pool setup | yes | running | no cron line, agent line 3 min ago (19:37Z) | 0 of 145 entries | agent lines 'W-SRVC' |
| W-SRVD | compute-pool setup | yes | running | no cron line, agent line 4 min ago (19:36Z) | 0 of 145 entries | agent lines 'W-SRVD' |
Alert G now: none
