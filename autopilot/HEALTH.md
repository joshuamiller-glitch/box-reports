# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-27T09:35:01Z | CORES reading: 2026-11-27 09:30Z | guard sample: 2026-11-27T09:30:01Z
Lead: last LEAD NOTE 29 min ago | last transcript activity 54 min ago | last watchdog line: 2026-11-27 09:24Z WATCHDOG L1 fired: A/F/G
github relay last pull OK at 2026-11-27T09:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 57.27 | 14 | ? | ? | ? | n/a | n/a | ? | ? |
| server2 | 97 | 64 | 85.61 | 28 | 411 | 28 | 401 | 23268 | 28.3 h | 25759 | 406.1 (0.002 GB/h, n/a h) |
| serverA | 100 | 128 | 181.23 | 105 (grid) + 101 (engine) | 153 | 0 | 772 | 53954 | 176.3 h | 5782 | 829.4 (0.002 GB/h, n/a h) |
| serverB | 100 | 128 | 171.75 | 105 (grid) + 101 (engine) | 140 | 0 | 880 | 51277 | 183.1 h | 5636 | 411.4 (0.0 GB/h, n/a h) |
| serverC | 100 | 128 | 136.95 | 1 (grid) + 138 (engine) | 0 | 0 | 1139 | 0 | n/a | 27335 | 411.2 (0.002 GB/h, n/a h) |
| serverD | 97 | 64 | 63.39 | 1 (grid) + 64 (engine) | 0 | 0 | 990 | 0 | n/a | 27710 | 411.3 (0.0 GB/h, n/a h) |

questions for Josh: 37 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 14/24 (58%) (15 min old); server2 28/28 (100%); serverA 100/102 (98%); serverB 102/102 (100%); serverC 136/140 (97%); serverD 66/68 (97%)
Box 1 = hub (pulls, dispatch, builders, grid pool, side jobs): engine cap 24 by lead order 2350Z (p90 of running engine jobs was 30, median 20); E-ENGINE and slot_heal use this cap (slot_heal does not watch box 1)
Stale-result detector (ex_pullback_scan, every 30 min): 478 results older than their lease launch, 0 of them with code/data edited after the old result (stale_vs_code); the pullers now reject a DONE older than the launch and park results whose code signature changed
Feeders (age min / max min): W-BEST rank Asia 16/90; W-BEST rank NY AM 16/90; ny_mix3 ranked stream -2/5; ny_refill 0/20; ex_aln_feed (all-new-base exit feed, W-EXITENG) 8/30; pass2_status 13/90
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-27T09:30Z): box1 12/12 (100%); Dallas 0/28 (0%); Frankfurt 0/97 (0%); Singapore 0/102 (0%); C Amsterdam 0/136 (0%); D Dallas-2 0/64 (0%); fleet 3%; exact-path kinds: TL3_DX_NP_MF2_ch2_N 42, TL3_DX_NP_MF2_ch3t_A 42, TL3_DX_NP_MF2_ch3_M 42, TL3_DX_NP_MF2_ch3t_M 42, TL3_DX_NP_MF2_ch3_N 42. Identity sets (_IDN) excluded from the share; kinds still waiting for their fast identity: 0 slots (none)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): server2: 3 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 3 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 3 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); serverD: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 504809 lines pending; fleet rate 0 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => n/a of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): E:box1:unreachable (TimeoutExpired(['bash', '-c', 'G=/mnt/l2/l2vast/_grid/res; R=/mnt/l2/l2vast/_th_), F:exit queue:708 all-new-base exit lines (TL3_ALN_*_EX*) undone but no ALN EX lease changed for 705 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 5 min ago, no agent line found | 1 of 167 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished 01:50Z (work complete; Asia fir | cron line 29 min ago, no agent line found | 1 of 167 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, no agent line found [cron-owned: exempt] | 122 of 167 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 30 min ago, agent line 24 min ago (09:11Z) | 22 of 167 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | resumable (idle-by-design; job finished, | cron line 5 min ago, no agent line found | 0 of 167 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, no agent line found | 0 of 167 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, no agent line found | 0 of 167 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | no cron line, no agent line found | 0 of 167 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 20 min ago, agent line 27 min ago (09:08Z) | 0 of 167 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | no cron line, no agent line found [cron-owned: exempt] | 0 of 167 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 15 min ago, no agent line found [cron-owned: exempt] | 0 of 167 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 22 min ago (09:13Z) [cron-owned: exempt] | 0 of 167 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | finished 03:5xZ | no cron line, no agent line found | 0 of 167 entries | agent lines 'W-XB1 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | no cron line, agent line 36 min ago (08:59Z) | 0 of 167 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | finished 00:20Z (hooks built + frozen v1 | no cron line, no agent line found | 0 of 167 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 18 min ago, no agent line found [cron-owned: exempt] | 0 of 167 entries | cron lines |
Alert G now: agent W-NYENG has no line in the log; agent W-SHORT has no line in the log
G: agent W-NYENG has no line in the log UNANSWERED since 20:20Z
G: agent W-SHORT has no line in the log UNANSWERED since 12:00Z
