# AGENTS_LIVE (written by the lead on every change; last write 04:33Z 2026-11-19)
name | owns | stage-1? | state | supervised loops / what stops with the agent
W-NYENG (a2ac20ed36cb00e42) | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min
W-ASIA (a2cf9d86c085a4f9f) | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | running (resumed ~10:0xZ; posts own lines, e.g. 10:09Z) | asia ladder loop supervised; crons asia_note.py :05/:35, reorder_pending.py, lx_cron.sh 10 min; the crons keep running without the agent
W-D8EXIT (a6473a449fa968cf4) | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; workers + d8_cycle.sh supervised, no agent turn needed) | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ)
W-GRIDOPS (aafc0a5dadae3a88b) | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent
W-SHORT (a4b931c164d0337bb) | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | gr3 shards box 1 (<=3) may not be supervised
W-NIGHT (id not in lead list) | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons keep running) | crons guard/health/wd continue
W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh keep running | no | gone |
W-NIGHT2 (fork of lead) | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | guard/health crons (th_night); agent only edits
asia crons (W-ASIA, lead-reviewed 0620Z): asia_note.py :05/:35 (asked for by the lead), reorder_pending.py :10/:25/:40/:55 (ladder lines ahead of older lines; locked, atomic, multiset-checked; backup deletion removed by lead).
# required 30-min MORNING.md cron lines (agent_line_cron.py): W-NYENG (added 09:56Z, cron */30)
W-EXITENG (exit-recipe engine families, builder; started 09:57Z) | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes | running | agent lines 'W-EXITENG STATUS n'; cron status line from its state file; ex_* code is edit-only (nothing supervised)
W-LAYERS (automatic layer-set builder for D8 candidates; started 09:57Z) | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py :25/:55) | layer_cron.py every 30 min writes '(auto)' lines; agent posts real lines when it works
W-NYENG update 09:57Z: cron ny_note.py :20/:50 now writes its line
W-FASTLADDER (fast-ladder identity test builder) | fl_status.py cron :20/:50 writes '(auto)' lines to MORNING.md, autopilot/FAST_LADDER.md | yes | cron-owned (agent resumable; nothing switched in any queue) | fl_status.py cron; no supervised loops
W-BEST (own-merit scorecards; started 18:08Z; id a591575ee08a10e3b) | owns code/th_best/best_books.py, BEST_BOOKS_ASIA/NYAM.md, _split/best_books_*.csv | yes | cron-owned (:07/:37) | agent lines 'W-BEST' + cron refresh lines
W-XB1 (staged + swing/line-trail exit builder; started 17:50Z; id a3a5e0b878203671b) | code/th_exiteng/xb_*.py | yes | running | agent lines 'W-XB1 STATUS n'
W-XB2 (stop-and-reverse, opposite-signal, order-flow exit builder; started 17:50Z; id ae43b5553cf4572f1) | code/th_exiteng/xb2_*.py | yes | finished 23:00Z (work complete; frozen hooks)
W-COVER (SEARCH_COVERAGE.md reporter; finished 18:26Z; id a8ef9f74b2c04b356) | autopilot/SEARCH_COVERAGE.md | no | finished
W-P2A (pass-2 generic combiner builder; started 18:50Z; id a818dd3f13812f3e3) | code/th_pass2/combiner.py, PASS2_COMBINER.md | yes | running | agent lines 'W-P2A'
W-P2B (pass-2 engine hooks builder; started 18:50Z; id adf0eb373bc00bff2) | code/th_pass2 hooks, PASS2_HOOKS.md | yes | running | agent lines 'W-P2B'
W-P2P (pass-2 prereg/cost/plan; finished first delivery 18:55Z; id afe6fc591ea2b51c5) | PREREG_PASS2.md, PASS2_COST.md, PASS2_PLAN.md | yes | cron-owned (pass2_status.py :17 hourly) | cron lines
W-SRVC (server C Amsterdam 67.213.127.157 setup; started 18:58Z; id ac7f16d38fb025b22) | compute-pool setup | yes | finished 23:00Z (work complete; servers registered by W-GRIDOPS)
W-SRVD (server D new Dallas 72.46.85.15 setup; started 18:58Z; id a855ef1f755bfdcc0) | compute-pool setup | yes | finished 23:00Z (work complete; servers registered by W-GRIDOPS)
