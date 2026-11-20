# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-20T16:35:01Z | CORES reading: 2026-11-20 16:30Z | guard sample: 2026-11-20T16:30:01Z
Lead: last LEAD NOTE 17 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-20 16:32Z WATCHDOG L1 fired: G
github relay last pull OK at 2026-11-20T16:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min (host-local, do not add up) | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 64.75 | 17 | 46 | 46 | 7248 | n/a | n/a | 256 | 57.4 (0.214 GB/h, 268.8 h) |
| server2 | 99 | 64 | 96.84 | 21 | 457 | 46 | 689 | 66089 | 72.3 h | 25933 | 406.9 (0.011 GB/h, n/a h) |
| serverA | 100 | 128 | 188.89 | 105 (grid) + 101 (engine) | 144 | 0 | 1322 | 53957 | 187.4 h | 6157 | 829.7 (0.002 GB/h, n/a h) |
| serverB | 100 | 128 | 176.05 | 105 (grid) + 90 (engine) | 140 | 0 | 1452 | 51280 | 183.1 h | 6107 | 411.8 (0.004 GB/h, n/a h) |
| serverC | 53 | 128 | 78.23 | 1 (grid) + 100 (engine) | 0 | 0 | 1786 | 0 | n/a | 27684 | 411.4 (0.0 GB/h, n/a h) |
| serverD | 94 | 64 | 64.23 | 1 (grid) + 67 (engine) | 0 | 0 | 1702 | 0 | n/a | 27750 | 411.4 (0.002 GB/h, n/a h) |

questions for Josh: 24 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: serverC 53%


Engine slots (running engine JOBS / cap; a job = a tp_launch.py wrapper and its child; caps from the cap files; every 5 min): box1 15/24 (62%); server2 21/28 (75%); serverA 101/102 (99%); serverB 99/102 (97%); serverC 97/100 (97%); serverD 71/76 (93%)
Box 1 = hub (pulls, dispatch, builders, grid pool, side jobs): engine cap 24 by lead order 2350Z (p90 of running engine jobs was 30, median 20); E-ENGINE and slot_heal use this cap (slot_heal does not watch box 1)
Stale-result detector (ex_pullback_scan, every 30 min): 478 results older than their lease launch, 0 of them with code/data edited after the old result (stale_vs_code); the pullers now reject a DONE older than the launch and park results whose code signature changed
Feeders (age min / max min): W-BEST rank Asia 17/90; W-BEST rank NY AM 17/90; ny_mix3 ranked stream 0/5; ny_refill 0/20; ex_aln_feed (all-new-base exit feed, W-EXITENG) 6/30; pass2_status 13/90
Fast share (running engine jobs whose set kind is in FAST_KINDS.txt, as of 2026-11-20T16:30Z): box1 14/14 (100%); Dallas 13/21 (62%); Frankfurt 26/100 (26%); Singapore 26/96 (27%); C Amsterdam 36/97 (37%); D Dallas-2 38/71 (54%); fleet 38%; exact-path kinds: TL3_ALN_AS_L<h>_BRPN 21, TL3_ALN_AS_L<h>_BRP30_CTN 19, TL3_ALN_AS_STKD84c5d6aN 13, TL3_ALN_AS_STKD0eb58dN 12, TL3_ALN_AS_STKDba276fN 11. Identity sets (_IDN) excluded from the share; kinds still waiting for their fast identity: 0 slots (none)

Calibration pools (W-SHORT gr3, stage-1 judge work; records done/left per host, every 5-10 min): box1: 5 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); server2: 11 gr3 procs, 1304 XC records, B-C tasks 18/18 done (0 left); serverA: 21 gr3 procs, 1494 XC records, B-C tasks 1/1 done (0 left); serverB: 17 gr3 procs, 1413 XC records, B-C tasks 1/1 done (0 left); serverC: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left); serverD: 3 gr3 procs, 0 XC records, B-C tasks 0/0 done (0 left)

Engine queue (shared by box 1, server 2, A, B): 256355 lines pending; fleet rate 14496 set-months/h (method: DONE files in the box-1 result tree in the last 30 min x 2; box 1 holds the results pulled back from Dallas, A and B; the per-host columns above are host-local and must not be summed) => 17.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB, G = stage-1 agent gone or silent): G:agent W-SHORT has no line for 67 min

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).

## Live agents (from autopilot/AGENTS_LIVE.md + last MORNING.md line per agent; guard alert G = stage-1 owner gone or silent > 60 min)
| agent | owns | stage-1 | state | last MORNING.md lines (cron vs agent) | supervised loops (registry) | what stops with the agent |
|---|---|---|---|---|---|---|
| W-NYENG | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | cron line 5 min ago, agent line 2 min ago (16:33Z) | 1 of 167 entries | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min |
| W-ASIA | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished 01:50Z (work complete; Asia fir | cron line 0 min ago, agent line 115 min ago (14:40Z) | 1 of 167 entries | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep |
| W-D8EXIT | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; worke | no cron line, agent line 61 min ago (15:34Z) [cron-owned: exempt] | 122 of 167 entries | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ) |
| W-GRIDOPS | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | cron line 30 min ago, agent line 2.6 h ago (14:01Z) | 22 of 167 entries | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent |
| W-SHORT | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | cron line 5 min ago, agent line 72 min ago (15:23Z) | 0 of 167 entries | gr3 shards box 1 (<=3) may not be supervised |
| W-NIGHT | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons | no cron line, agent line 16.3 h ago (00:20Z) | 0 of 167 entries | crons guard/health/wd continue |
| W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh k | no | gone | no cron line, agent line 82 min ago (15:13Z) | 0 of 167 entries |  |
| W-NIGHT2 | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | cron line 6.6 h ago, agent line 86 min ago (15:09Z) | 0 of 167 entries | guard/health crons (th_night); agent only edits |
| W-EXITENG | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | cron line 20 min ago, agent line 25 min ago (16:10Z) | 0 of 167 entries | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing superv |
| W-LAYERS | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py  | cron line 10 min ago, agent line 26 min ago (16:09Z) [cron-owned: exempt] | 0 of 167 entries | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works |
| W-FASTLADDER | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopil | yes | cron-owned (agent resumable; nothing swi | cron line 15 min ago, agent line 20 min ago (16:15Z) [cron-owned: exempt] | 0 of 167 entries | fl_status.py cron; no supervised loops |
| W-BEST | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_ | yes | cron-owned (:07/:37) | no cron line, agent line 22 min ago (16:13Z) [cron-owned: exempt] | 0 of 167 entries | agent lines 'W-BEST' + cron refresh lines |
| W-XB1 | code/th_exiteng/xb_*.py | yes | finished 03:5xZ | no cron line, agent line 12.6 h ago (03:57Z) | 0 of 167 entries | agent lines 'W-XB1 STATUS n' |
| W-P2A | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | cron line 3.1 h ago, agent line 16 min ago (16:19Z) | 0 of 167 entries | agent lines 'W-P2A' |
| W-P2B | code/th_pass2 hooks, PASS2_HOOKS.md | yes | finished 00:20Z (hooks built + frozen v1 | no cron line, agent line 16.3 h ago (00:20Z) | 0 of 167 entries | agent lines 'W-P2B' |
| W-P2P | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron line 18 min ago, agent line 21.2 h ago (19:22Z) [cron-owned: exempt] | 0 of 167 entries | cron lines |
Alert G now: agent W-SHORT has no line for 72 min
G: agent W-SHORT has no line for 67 min UNANSWERED since 16:30Z
