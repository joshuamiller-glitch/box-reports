# AGENTS_LIVE (written by the lead on every change; last write 04:33Z 2026-11-19)
name | owns | stage-1? | state | supervised loops / what stops with the agent
W-NYENG (a2ac20ed36cb00e42) | NY AM + NY PM ladder/engine queues, D8_SPEC_STATUS, D8_CANDIDATES (NY) | yes | resumable on demand | ny_ladder_loop.sh supervised (registry fixed 04:10Z); 15-min cron re-order; pages cron 30 min
W-ASIA (a2cf9d86c085a4f9f) | Asia engine/ladder, NEW_BOOK_BEATS_LIVE_ASIA | yes | finished first pass 04:06Z | asia ladder loop supervised; progress cron lx_cron.sh 10 min; asia_cron.sh 30 min
W-D8EXIT (a6473a449fa968cf4) | D8-candidate exit screen + broad exit run | yes | cron-owned (agent finished 03:2xZ; workers + d8_cycle.sh supervised, no agent turn needed) | d8_cycle.sh cron 15 min and worker pools supervised (registered 03:2xZ)
W-GRIDOPS (aafc0a5dadae3a88b) | grid ops, result stamp, nice ladder, ag_nice | yes | resumable | ag_nice_ctl.sh cron, supervise.py; loops continue without the agent
W-SHORT (a4b931c164d0337bb) | R3, calibration by family, staleness knock-on | yes | running (resumed 04:5xZ) | gr3 shards box 1 (<=3) may not be supervised
W-NIGHT (id not in lead list) | guard.py, health.py, wd_levels | yes | gone (replaced by W-NIGHT2 04:41Z; crons keep running) | crons guard/health/wd continue
W-LONENG | gone (replaced by W-ASIA); crons lon_cron.sh/asia_cron.sh/lx_cron.sh keep running | no | gone |
W-NIGHT2 (fork of lead) | guard.py/health.py/agents_live.py, alert G, HEALTH live-agent section | yes | finished 04:4xZ | guard/health crons (th_night); agent only edits
asia crons (W-ASIA, lead-reviewed 0620Z): asia_note.py :05/:35 (asked for by the lead), reorder_pending.py :10/:25/:40/:55 (ladder lines ahead of older lines; locked, atomic, multiset-checked; backup deletion removed by lead).
# required 30-min MORNING.md cron lines (agent_line_cron.py): W-NYENG (added 09:56Z, cron */30)
W-EXITENG (exit-recipe engine families, builder; started 09:57Z) | owns D8_EXIT_ENGINE_SUPPORT build, D8_EXIT_ENGINE_RESULTS.md | yes (exit run) | running | cron status line from its state file
W-LAYERS (automatic layer-set builder for D8 candidates; started 09:57Z) | owns code/th_layers, TL3_NYL layer programme for beats-live cells | yes | cron-owned (built 10:0xZ; layer_cron.py :25/:55) | cron every 30 min
W-NYENG update 09:57Z: cron ny_note.py :20/:50 now writes its line
