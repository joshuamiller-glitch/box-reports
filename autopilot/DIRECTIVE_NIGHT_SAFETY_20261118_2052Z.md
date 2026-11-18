# 2052Z — NIGHT SAFETY: no repeat of the 05:35Z-13:03Z stall. Build and TEST these before 02:00Z, while Josh is awake.

From: Josh's chat assistant (relay). Research ops only; no spend; nothing touches the execution server, a live chart or credentials.

Last night two things failed together: the lead stopped taking turns, and the grid was failing silently on server 2. Tonight there are four machines. The rule: THE MACHINES MUST KEEP WORKING FOR 10 HOURS WITH NO LEAD AT ALL, and a dead lead must come back by itself.

1. DEAD-MAN RESTART (new, in the watchdog, cron every 2 min, outside Claude Code): 
   a. LEVEL 1 (exists): type the wake line into tmux b5 on triggers A / B / C / D.
   b. LEVEL 2 (new): if 15 minutes after a wake line there is still no new real LEAD NOTE in MORNING.md, check the pane: if a Claude Code process is running in b5 send Escape then the wake line again; log "WATCHDOG L2".
   c. LEVEL 3 (new): if 30 minutes after the first wake there is still no lead note, or no Claude Code process exists in b5, or the tmux session is gone: recreate the session if needed and START Claude Code in b5 with the same working directory and the same flags it runs with now, then type: "WATCHDOG L3 restart: read CLAUDE.md, the last 150 lines of MORNING.md, autopilot/SEARCH_STATUS.md and ~/inbox; resume the standing plan; log a LEAD NOTE first." Log "WATCHDOG L3" with the time. At most one L3 per 45 minutes. Record the exact start command in the script from the running process now (do not guess it later).
   d. Every level writes a line to MORNING.md and to autopilot/WATCHDOG_LOG.md so the chat assistant sees it on its 15-minute check.
   e. TEST tonight with Josh awake: (i) L1 by dropping a test file in ~/inbox; (ii) L2 and L3 in a DRY-RUN mode that prints what it would do; (iii) one REAL L3 test at a moment you choose between tasks (finish your turn, let the watchdog find no lead note for 30 minutes with a short test threshold, confirm it restarts and the new session resumes). Report each result. Do not run /restart for the pending Claude Code update except as part of this tested restart.

2. THE WORK MUST NOT DEPEND ON THE LEAD:
   a. Every loop that feeds a machine (grid real / null / filler loops, engine dispatchers on all four, results merge, R3 runner, page builders) runs under cron or a supervisor that restarts it if it dies, on each host. List them in autopilot/NIGHT_RUNBOOK.md with: what it does, how it is restarted, how to tell it is healthy.
   b. QUEUE DEPTH: before 02:00Z make sure every machine has at least 12 hours of queued work that needs no decision: grid pass 1 / pass 2 / exits, null draws, R3 stages A-C for all four sessions, the XA3 layer programme through its joint stage and prior years, London / Asia lead sets, near-target controls. Write the hours of queue per machine on the runbook.
   c. SILENT FAILURE GUARD (this is what really cost the night): per host, every 10 minutes compare results written in the last 30 minutes with workers running; if a host has workers but writes fewer than 20% of its usual results, or error stubs grow faster than results, that is trigger E: wake the lead, and write "HOST x PRODUCING NOTHING" in CORES.md.
   d. Disk: trigger F at < 100 GB free on any data volume.
   
3. STATUS FOR THE OUTSIDE: one small file autopilot/HEALTH.md rewritten every 5 minutes by cron (not by the lead): UTC time; per machine busy %, workers, results in the last 30 minutes, engine set-months in the last 30 minutes, queue hours left; minutes since the last real lead note; last watchdog level fired. The chat assistant reads this file every 15 minutes and alerts Josh from it.

4. Reply in MORNING.md by 22:30Z: what is built, each test result, the hours of queue per machine for tonight, and anything that could still stop the fleet with no human awake.
