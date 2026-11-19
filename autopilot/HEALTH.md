# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T23:50:01Z | CORES reading: 2026-11-19 23:45Z | guard sample: 2026-11-19T23:40:01Z
Lead: last LEAD NOTE 4 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 23:42Z WATCHDOG L1 fired: E/F/G
github relay last pull OK at 2026-11-19T23:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 54.75 | 12 | 27 | 49 | 5551 | n/a | n/a | 283 | 58.2 (0.108 GB/h, 538.9 h) |
| server2 | 100 | 64 | 110.84 | 25 | 3218 | 49 | 537 | 91067 | 14.1 h | 26117 | 407.1 (0.018 GB/h, n/a h) |
| serverA | 100 | 128 | 219.19 | 105 (grid) + 102 (engine) | 885 | 0 | 1056 | 64131 | 36.2 h | 6216 | 829.7 (0.001 GB/h, n/a h) |
| serverB | 100 | 128 | 211.62 | 105 (grid) + 99 (engine) | 178 | 0 | 1058 | 51747 | 145.4 h | 6157 | 411.9 (0.006 GB/h, n/a h) |
| serverC | 70 | 128 | 94.44 | 1 (grid) + 97 (engine) | 0 | 0 | 1175 | 0 | n/a | 27693 | 411.4 (0.0 GB/h, n/a h) |
| serverD | 76 | 64 | 53.84 | 1 (grid) + 60 (engine) | 0 | 0 | 1441 | 0 | n/a | 27759 | 411.4 (0.001 GB/h, n/a h) |

questions for Josh: 14 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: serverC 70%, serverD 76%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 12/36 (33%); server2 28/28 (100%); serverA 102/102 (100%); serverB 101/102 (99%); serverC 98/100 (98%); serverD 60/64 (94%)
Box 1 = hub (pulls, dispatch, builders, grid pool, side jobs): engine cap 24 by lead order 2350Z (p90 of running engine jobs was 30, median 20); E-ENGINE and slot_heal use this cap (slot_heal does not watch box 1)
Stale-result detector (ex_pullback_scan, every 30 min): 478 results older than their lease launch, 0 of them with code/data edited after the old result (stale_vs_code); the pullers now reject a DONE older than the launch and park results whose code signature changed
Feeders (age min / max min): W-BEST rank Asia 28/90; W-BEST rank NY AM 28/90; ny_mix3 ranked stream 0/5; ny_refill 0/20; layer_cron 75/30 STALE; ex_ownmerit batch release 30/90; pass2_status 23/90
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-19T23:45Z): box1 12/12 (100%); Dallas 17/25 (68%); Frankfurt 72/102 (71%); Singapore 69/97 (71%); C Amsterdam 53/97 (55%); D Dallas-2 0/62 (0%); fleet 56%; exact-path kinds: TL3_ALN_AS_L<h>_BASE 73, TL3_ALN_NY_L<h>_BASE 68, TL3_NYE_L<h>_ALN 21, TL3_ALN_AS_M<h>_BASE 7, TL3_ALN_AS_L<h>_CTN 2. Identity sets (_IDN) excluded from the share; kinds still waiting for their fast identity: 0 slots (none)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 6 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 11 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 3 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); serverD: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 185516 lines pending; fleet rate 11102 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 16.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): E:box1:E-ENGINE host box1 slots 12/36, F:feeders:layer_cron file state.json is 75 min old (max 30 min): its cron may have failed silently, E:SLOT_HEAL:23:34Z W-GRIDOPS SELF-HEAL: serverB engine slots 99 of 102 (or dispatcher log silent) for >=10 min with runnable lines: killing dispatcher pid(s) 1954478, supervisor restarts it (once per 30 min per h

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 20 min ago, agent line 33 min ago (23:17Z) | 1 of 167 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own line | cron line 13 min ago, agent line 47 min ago (23:03Z) | 1 of 167 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 81 min ago (22:29Z) [cron-owned: exempt] | 122 of 167 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 45 min ago, agent line 17 min ago (23:33Z) | 22 of 167 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 20 min ago, agent line 18 min ago (23:32Z) | 0 of 167 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 62 min ago (22:48Z) | 0 of 167 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 64 min ago (22:46Z) | 0 of 167 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 13.9 h ago, agent line 8.7 h ago (15:09Z) | 0 of 167 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 5 min ago, agent line 48 min ago (23:02Z) | 0 of 167 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 85 min ago, agent line 5 min ago (23:45Z) [cron-owned: exempt] | 0 of 167 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 30 min ago, agent line 40 min ago (23:10Z) [cron-owned: exempt] | 0 of 167 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 7 min ago (23:43Z) [cron-owned: exempt] | 0 of 167 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | running | no cron line, agent line 49 min ago (23:01Z) | 0 of 167 entries | agent lines 'W-XB1 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 49 min ago, agent line 51 min ago (22:59Z) | 0 of 167 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | no cron line, agent line 44 min ago (23:06Z) | 0 of 167 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 33 min ago, agent line 4.5 h ago (19:22Z) [cron-owned: exempt] | 0 of 167 entries | cron lines |
Alert G now: none
G: agent W-SRVD has no line for 65 min UNANSWERED since 22:50Z
