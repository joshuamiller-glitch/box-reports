# ORDER 20261119_0432Z: Dallas guard alert E + a live-agent list on HEALTH.md

Research ops only.

1. DALLAS. HEALTH.md 04:25Z: guard alert "E:server2:unreachable (IndexError('list index out of range'))",
   the Dallas row shows "?" for grid results / stubs / engine / todo, while CORES still reads busy 100%,
   load 91, 11 workers; the watchdog fired E at 04:22Z; fleet engine rate fell 1,944 -> 1,674 set-months/h.
   a. Is Dallas reachable and producing (ssh, grid results and engine set-months in the last 10 min)?
   b. If it is fine, the guard probe has a bug (IndexError): fix the probe so a parsing error is reported
      as "probe error", never as "unreachable", and say what changed on Dallas at ~04:15Z that broke it
      (the re-partition? a loop restart? a file the probe reads being empty?).
   c. If Dallas really lost work (loops down, dispatcher stopped), restart per NIGHT_RUNBOOK.md and say
      how many minutes were lost.
2. LIVE AGENTS. W-LONENG disappeared tonight and Asia sat unowned for hours. Add to HEALTH.md (cron, not
   the lead's memory): one line per agent that owns work: name, what it owns (stage-1 item or other),
   time of its last MORNING.md line, state (running / finished / gone). Sources: the lead's agent list
   written to a file on every change + the last line per W-name in MORNING.md.
   Guard alert G: an agent that owns a STAGE-1 item (Asia engine, NY AM engine, D8 exit screen, grid ops,
   calibration, night safety) has no line for 60 min, or is gone: wake the lead, which restarts or
   replaces it and writes one line saying so. Its unattended loops (cron / supervised) keep running anyway:
   list for each agent which of its loops are supervised and which would stop with it.
3. NIGHT_STANDING_ORDERS.md: add the stage sequence (Asia + NY AM fully first, then London, then NY PM),
   the D8 inclusion rule, the exit-run rule and the priority fix (ag_nice cron must stay on), so a lead
   restarted overnight by level 3 starts from tonight's rules, not yesterday's.
