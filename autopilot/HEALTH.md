# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T21:40:01Z | CORES reading: 2026-11-19 21:35Z | guard sample: 2026-11-19T21:31:33Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 21:16Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T21:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 80.8 | 23 | 14 | 113 | 4164 | n/a | n/a | 286 | 58.3 (0.242 GB/h, 240.6 h) |
| server2 | 100 | 64 | 155.2 | 26 | 1968 | 109 | 472 | 95216 | 24.2 h | 26226 | 407.2 (0.023 GB/h, n/a h) |
| serverA | 100 | 128 | 216.19 | 105 (grid) + 102 (engine) | 1369 | 0 | 973 | 69448 | 25.4 h | 6229 | 829.7 (0.002 GB/h, n/a h) |
| serverB | 100 | 128 | 202.97 | 105 (grid) + 101 (engine) | 891 | 0 | 1036 | 53005 | 29.7 h | 6167 | 411.9 (0.009 GB/h, n/a h) |
| serverC | 74 | 128 | 94.63 | 1 (grid) + 96 (engine) | 0 | 0 | 1243 | 0 | n/a | 27707 | 411.4 (0.0 GB/h, n/a h) |

questions for Josh: 12 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: serverC 74%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 20/36 (56%); server2 28/28 (100%); serverA 100/102 (98%); serverB 99/102 (97%); serverC 100/100 (100%)
Stale-result detector (ex_pullback_scan, every 30 min): 633 results older than their lease launch, 20 of them with code/data edited after the old result (stale_vs_code); the pullers now reject a DONE older than the launch and park results whose code signature changed
Feeders (age min / max min): W-BEST rank Asia 4/90; W-BEST rank NY AM 4/90; ny_mix3 ranked stream -1/5; ny_refill 2/20; layer_cron 6/30; ex_ownmerit batch release 10/90; pass2_status 15/90
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T21:35Z): box1 18/21 (86%); Dallas 26/26 (100%); Frankfurt 102/102 (100%); Singapore 101/101 (100%); C Amsterdam 97/97 (100%); fleet 99%; exact-path kinds: TL3_EXE_P2_L<h>_IT1_P2VN 1, TL3_EXE_P2_L<h>_LIM1_P2VN 1, TL3_EXE_P2_L<h>_FC_P2VN 1. Identity sets (_IDN) excluded from the share; kinds still waiting for their fast identity: 3 slots (TL3_EXE_P2_L<h>_IT1_P2VN 1, TL3_EXE_P2_L<h>_LIM1_P2VN 1, TL3_EXE_P2_L<h>_FC_P2VN 1)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 11 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 22 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 112145 lines pending; fleet rate 8328 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 13.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 10 min ago, agent line 15 min ago (21:25Z) | 1 of 146 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 4 min ago, agent line 2 min ago (21:38Z) | 1 of 146 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 71 min ago (20:29Z) [cron-owned: exempt] | 104 of 146 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 35 min ago, agent line 2 min ago (21:38Z) | 22 of 146 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 10 min ago, agent line 28 min ago (21:12Z) | 0 of 146 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 40 min ago (21:00Z) | 0 of 146 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 17 min ago (21:23Z) | 0 of 146 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 11.7 h ago, agent line 6.5 h ago (15:09Z) | 0 of 146 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 25 min ago, agent line 1 min ago (21:39Z) | 0 of 146 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 4 min ago, agent line 3.4 h ago (18:15Z) [cron-owned: exempt] | 0 of 146 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 20 min ago, agent line 1 min ago (21:39Z) [cron-owned: exempt] | 0 of 146 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 2 min ago (21:38Z) [cron-owned: exempt] | 0 of 146 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | running | no cron line, agent line 3 min ago (21:37Z) | 0 of 146 entries | agent lines 'W-XB1 STATUS n' |
| W-XB2 | code/th_exiteng/xb2_*.py | yes | running | no cron line, agent line 28 min ago (21:12Z) | 0 of 146 entries | agent lines 'W-XB2 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 2.3 h ago, agent line 11 min ago (21:29Z) | 0 of 146 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | no cron line, agent line 27 min ago (21:13Z) | 0 of 146 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 23 min ago, agent line 2.3 h ago (19:22Z) [cron-owned: exempt] | 0 of 146 entries | cron lines |
| W-SRVC | compute-pool setup | yes | running | no cron line, agent line 36 min ago (21:04Z) | 0 of 146 entries | agent lines 'W-SRVC' |
| W-SRVD | compute-pool setup | yes | running | no cron line, agent line 28 min ago (21:12Z) | 0 of 146 entries | agent lines 'W-SRVD' |
Alert G now: none
