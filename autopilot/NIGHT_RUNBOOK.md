# NIGHT RUNBOOK (W-NIGHT, order 2052Z): what keeps the fleet working for 10 h with NO lead
Machines: box 1 (London, 32 threads, runs every supervisor/cron below), Dallas server 2 (64 threads, SMT off, no crontab binary), A Frankfurt (128 threads), B Singapore (128 threads). Reached only from box 1 by ssh key; nothing with keys or credentials lives on A/B/server 2.
Everything below runs outside Claude Code. A dead lead does NOT stop any of it. A restarted lead loses its subagents (they live inside the lead process); the loops below keep going.

## 1. Watchdog levels (box 1 cron) - bring a dead lead back
| level | script | when | action |
|---|---|---|---|
| L1 | lead_watchdog/wake_watchdog.py (cron */2) | trigger A new inbox file newer than the last LEAD NOTE; B a machine < 85% busy 3 readings with work pending; C no LEAD NOTE for 40 min; D admission lock saturated (> 150 blocked or a live-tag waiter > 6 h); E a host has workers but produces < 20% of its usual results / error stubs outgrow results / 0 engine set-months with >= 10 workers / host unreachable; F < 100 GB free on /mnt/l2 | types the wake line into tmux b5, max 1 per 10 min, logs 'WATCHDOG fired' (MORNING.md, WATCHDOG_LOG.md) |
| L2 | th_night/wd_levels.py (cron */2) | 15 min after the first unanswered wake (no transcript write and no new LEAD NOTE since) | if Claude Code runs in b5: Escape + the wake line again; logs 'WATCHDOG L2' |
| L3 | th_night/wd_levels.py | 30 min unanswered, OR no Claude Code process in b5 for >= 4 min, OR tmux session b5 gone, OR a file RESTART_LEAD_<YYYYMMDD_HHMMZ>.md appears in ~/inbox (direct or github relay; once per file name; the file is never opened) | Ctrl-C twice, wait 60 s, SIGTERM the explicit pid (only a `claude` whose parent is the b5 pane shell), recreate session b5 if needed with a NEW LOGIN shell (`bash -l -i`: the shell start-up files export the token; the token is never read/printed/stored), start `claude --resume 286aaa96-d728-4f6b-a187-ef8d7a22e202` (fallback plain `claude`), wait, type the restart message (read CLAUDE.md, ~/NIGHT_STANDING_ORDERS.md, last 150 lines of MORNING.md, SEARCH_STATUS.md, QUESTIONS_FOR_JOSH.md, ~/inbox; log a LEAD NOTE first). Max one per 45 min (a RESTART_LEAD request ignores the 45 min rule but not a 3 min loop guard). Logs 'WATCHDOG L3' / 'L3 by request'. |
Test tools: `python3 th_night/wd_levels.py --dry-run` (prints, touches nothing); `--test` reads <tmp> (session, cwd, start_cmd, fallback_cmd, l2_min, l3_min, dead_min, state, inbox, fake_incident_start, force_level) - cron runs never read it; a test that targets the REAL session b5 with test thresholds only runs if <tmp> exists (created by the lead). Tests done 20:50-20:58Z in a throwaway tmux session b5test (below).
Caveat: a restarted session comes up in the default permission mode of a fresh session (it showed 'auto mode on'), not necessarily the mode the old lead had set by hand.

## 2. Status for the outside (cron, not the lead)
- th_night/health.py (*/5) -> autopilot/HEALTH.md: UTC time, per machine busy %, workers, results / error stubs / engine set-months in 30 min, grid queue hours, disk; engine queue hours; minutes since last LEAD NOTE and last lead activity; last watchdog line; github relay line; 'questions for Josh: N open'; rule A (all four >= 90%).
- th_night/guard.py (*/10) -> <tmp> + 'HOST x PRODUCING NOTHING' lines in CORES.md: silent-failure guard (E) and disk (F).
- lead_watchdog/cores_meter.py (*/5) -> CORES.md (busy % vs real threads for all four machines).
- box-reports mirror (cron */5): autopilot/*.md incl. HEALTH.md and WATCHDOG_LOG.md are staged, redacted, scanned (HEALTH.md passes the scan) and pushed.
- lead_watchdog/gh_pull.py (cron every minute): public-repo relay of orders (writes autopilot/gh_relay_last_ok.txt; its line is in HEALTH.md).

## 3. Supervisors: loops restarted automatically
th_night/supervise.py (box 1 cron */5, flock) restarts any loop recorded in th_night/registry.json that is no longer running (same cmdline + same GL_/QL_/S3_ env, nice, stdout file), max 3 restarts/hour per loop (else ALERT in th_night/supervise.log), never if <tmp> exists, the loop's own STOP file exists (_grid/STOP, _s2/QL_STOP_<TAG>, _s3_<X>/STOP) or enabled=false. After an INTENTIONAL change of the loop set run `python3 th_night/supervise.py --record` (otherwise a loop stopped on purpose is restarted). Check: `python3 th_night/supervise.py --dry-run` says 'all supervised loops alive'.
| host | loop | what it does | healthy when |
|---|---|---|---|
| box 1 | s2_dispatch.py, s2_pull.py (th_s2) | dispatch engine set-months from _s2/QUEUES.txt to Dallas, pull results back | CORES 'dispatcher alive'; _s2/dispatch.out grows |
| box 1 | start_dispatch.sh A 32 / B 28 -> s3_dispatch.py + s3_pull.py (th_s3; state _s3_A, _s3_B) | same for Frankfurt / Singapore (only after IDENTITY_PASS) | HEALTH engine set-months for the host > 0 |
| box 1 | ql_driver.py fillers, tags NT (3), NYL (2), NYF, NYE, NYW, LON, ASI, FR, ORB | engine chains on box 1 pulling their queue files | tp_launch workers on box 1; queue lines shrink |
| box 1 | results_sync_loop.sh (th_s3) | copies A/B grid results into server 2's res/ every ~5 min | HEALTH grid results on server 2; log in /tmp |
| box 1 | s2_sync_grid.sh (th_grid), ghourly_loop.sh | code/manifest/results pull-push with server 2; hourly grid status lines | files fresh |
| box 1 | inbox_watch.sh (lead_watchdog) | acks inbox files, writes ~/inbox/.pending | <tmp> fresh |
| server 2 | gloop.py real pass 1 (rows 0,1/12), pass 2 + exits (GL_SUF=_p2), null (GL_SUF=_null); gcycle.py (score + pages, nice 5); /tmp/nullloop.sh (null-draw audit) | the grid on Dallas | HEALTH grid results/30 min ~1,000+ |
| A, B | gloop.py real pass 1, pass 2 (_p2), null (_null) for their row partitions (A rows 2-6, B 7-11) | the grid on the rented servers | HEALTH grid results/30 min |
Cron-driven (already supervised by cron, box 1): filler_ctl.sh (*/5, grid filler on A/B sized to 128 - engine busy), s2_cap_follow.py, s2_grid_watch.py (restarts server-2 grid loops when idle), stop_waiters.py (*/1), backfill.py, gtop_pull.sh, plan_refresh.py (hourly), th_gridops status crons, ny_cron/lon_cron/asia_cron page builders, ny_fit.py, lx_cron.sh, ey_cycle.sh, daymask_cycle.sh, th_short pull_short.sh (R3 pages).
Transient jobs (not supervised, re-issued by their drivers): R3 runners (/tmp/r3run.sh, /tmp/r3one.sh -> th_short/gr3.py), exit-yield jobs.

## 4. Queue depth (hours of work per machine that needs no decision), 20:50Z numbers, live values in HEALTH.md
- Grid (own rows, jobs / measured jobs per hour): server 2 ~15 h, Frankfurt ~60 h, Singapore ~31 h (pass 1 + pass 2 + null): OK (>= 12 h each).
- ENGINE queue (shared by all four): 4,502 lines = ~3.3 h at the fleet rate of ~1,400 set-months/h: SHORT. Before 02:00Z the engine needs >= 12 h = ~16,600 set-months queued that need no decision. Who adds: W-NYENG (XA3 layer programme joint stage + prior years; ladder R5 set builder once W-SHORT writes _nye/ladder_cells.json), W-LONENG (London/Asia lead sets stages 2-3), W-NT2 (near-target controls), W-SHORT (R3 stages B-D are screen jobs on the grid, not engine). Parked queues (S3, DD, EV, P7L, MF, SWB ...) can be un-parked by removing '# PARKED 1858Z' in _s2/QUEUES.txt and resetting their quota in PRIORITY.txt if the lead decides.

## 5. What could still stop the fleet with no human awake
1. Box 1 itself (it runs every cron, dispatcher and the ssh key): a reboot/crash stops dispatch to all hosts (their already-running workers finish; grid loops on A/B/server 2 keep running as they are self-contained). No remote watchdog exists; Josh's check of HEALTH.md (box-1 mirror stops updating) is the alarm.
2. Disk: box 1 /mnt/l2 ~350 GB free (engine cache + results grow); box 1 root filesystem ~9 GB free (98%): the repo, MORNING.md and logs live there.
3. The Claude Code token / account limits: if the token expires or usage is exhausted, L3 restarts a session that cannot work; HEALTH.md shows 'minutes since last LEAD NOTE' growing and watchdog lines repeating.
4. Engine queue empty in ~3 h (section 4) unless the ladder R5 builder and the layer programme keep refilling it; the grid still fills the CPU (rule A holds) but R5 evidence stalls.
5. Admission-lock saturation by stale waiters (trigger D wakes the lead; the fix is by hand).
6. ssh connectivity from London to Singapore (156 ms) / Frankfurt: supervise.py logs ALERT 'host unreachable' and guard.py raises E.
