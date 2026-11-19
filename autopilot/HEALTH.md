# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T22:45:01Z | CORES reading: 2026-11-19 22:40Z | guard sample: 2026-11-19T22:40:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 22:44Z WATCHDOG L1 fired: E/G
github relay last pull OK at 2026-11-19T22:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 86.58 | 17 | 27 | 126 | 4576 | n/a | n/a | 285 | 58.2 (0.172 GB/h, 339.5 h) |
| server2 | 100 | 64 | 131.97 | 20 | 1385 | 126 | 464 | 92747 | 33.5 h | 26170 | 407.1 (0.016 GB/h, n/a h) |
| serverA | 100 | 128 | 218.66 | 105 (grid) + 100 (engine) | 1013 | 0 | 862 | 66204 | 32.7 h | 6222 | 829.7 (0.0 GB/h, n/a h) |
| serverB | 100 | 128 | 176.82 | 105 (grid) + 23 (engine) | 389 | 0 | 957 | 51933 | 66.8 h | 6162 | 411.9 (0.006 GB/h, n/a h) |
| serverC | 74 | 128 | 96.42 | 1 (grid) + 98 (engine) | 0 | 0 | 1049 | 0 | n/a | 27694 | 411.4 (0.0 GB/h, n/a h) |
| serverD | 85 | 64 | 55.07 | 1 (grid) + 52 (engine) | 0 | 0 | 940 | 0 | n/a | 27760 | 411.4 (0.001 GB/h, n/a h) |

questions for Josh: 13 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: serverC 74%, serverD 85%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 17/36 (47%); server2 22/28 (79%); serverA 101/102 (99%); serverB 24/102 (24%); serverC 99/100 (99%); serverD 52/64 (81%)
Stale-result detector (ex_pullback_scan, every 30 min): 586 results older than their lease launch, 0 of them with code/data edited after the old result (stale_vs_code); the pullers now reject a DONE older than the launch and park results whose code signature changed
Feeders (age min / max min): W-BEST rank Asia 9/90; W-BEST rank NY AM 9/90; ny_mix3 ranked stream 0/5; ny_refill 0/20; layer_cron 15/30; ex_ownmerit batch release 16/90; pass2_status 23/90
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T22:40Z): box1 13/15 (87%); Dallas 21/21 (100%); Frankfurt 91/101 (90%); Singapore 24/24 (100%); C Amsterdam 87/97 (90%); D Dallas-2 50/55 (91%); fleet 91%; exact-path kinds: TL3_STK_ZA_da899c7b_72eN 2, TL3_STK_ZA_c9c33df5_c4eN 2, TL3_STK_ZA_47096851_7eaN 2, TL3_EXE_P2_L<h>_FLIP_P2VN 1, TL3_EXE_P2_L<h>_SPLIT_P2VN 1. Identity sets (_IDN) excluded from the share; kinds still waiting for their fast identity: 27 slots (TL3_STK_ZA_da899c7b_72eN 2, TL3_STK_ZA_c9c33df5_c4eN 2, TL3_STK_ZA_47096851_7eaN 2, TL3_EXE_P2_L<h>_FLIP_P2VN 1)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); serverD: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 113106 lines pending; fleet rate 9152 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 12.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): E:box1:E-ENGINE host box1 slots 17/36

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 9 min ago, agent line 9 min ago (22:36Z) | 1 of 148 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 9 min ago, agent line 7 min ago (22:38Z) | 1 of 148 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 16 min ago (22:29Z) [cron-owned: exempt] | 104 of 148 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 40 min ago, agent line 53 min ago (21:52Z) | 22 of 148 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 15 min ago, agent line 21 min ago (22:24Z) | 0 of 148 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line -3 min ago (22:48Z) | 0 of 148 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line -1 min ago (22:46Z) | 0 of 148 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 12.8 h ago, agent line 7.6 h ago (15:09Z) | 0 of 148 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 0 min ago, agent line 16 min ago (22:29Z) | 0 of 148 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 20 min ago, agent line 8 min ago (22:37Z) [cron-owned: exempt] | 0 of 148 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 25 min ago, agent line 47 min ago (21:58Z) [cron-owned: exempt] | 0 of 148 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 14 min ago (22:31Z) [cron-owned: exempt] | 0 of 148 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | running | no cron line, agent line 25 min ago (22:20Z) | 0 of 148 entries | agent lines 'W-XB1 STATUS n' |
| W-XB2 | code/th_exiteng/xb2_*.py | yes | running | no cron line, agent line 93 min ago (21:12Z) | 0 of 148 entries | agent lines 'W-XB2 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 3.4 h ago, agent line 42 min ago (22:03Z) | 0 of 148 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | no cron line, agent line 12 min ago (22:33Z) | 0 of 148 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 28 min ago, agent line 3.4 h ago (19:22Z) [cron-owned: exempt] | 0 of 148 entries | cron lines |
| W-SRVC | compute-pool setup | yes | running | no cron line, agent line 101 min ago (21:04Z) | 0 of 148 entries | agent lines 'W-SRVC' |
| W-SRVD | compute-pool setup | yes | running | no cron line, agent line 60 min ago (21:45Z) | 0 of 148 entries | agent lines 'W-SRVD' |
Alert G now: agent W-XB2 has no line for 93 min; agent W-SRVC has no line for 101 min; agent W-SRVD has no line for 60 min
G: agent W-SRVC has no line for 96 min UNANSWERED since 22:10Z
G: agent W-XB2 has no line for 88 min UNANSWERED since 22:20Z
