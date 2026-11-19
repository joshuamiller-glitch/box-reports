# CHANGE FREEZE on fleet plumbing: 02:00Z Nov 20 to 14:00Z Nov 20 (order 20261119_2305Z item 2; text by W-PROOF)

Why: Josh sleeps from about 03:00-05:00Z and cannot monitor six rented machines. Tonight's drops followed restarts and edits. Everything that keeps the fleet fed has been drilled (autopilot/NIGHT_PROOF.md); from 02:00Z it must not be changed without cause.

## FROZEN (no edit, no restart, no kill, no new cron line, no re-ordering)
1. Dispatchers and pullers: `code/th_s3/s3_dispatch.py`, `s3_pull.py`, `start_dispatch.sh`, `code/th_s2/s2_dispatch.py`, `s2_pull.py`, `ql_driver.py`, `pc_pull.py`, `results_sync*.sh`, and the running processes `S3_TAG_A..D s3_dispatch|s3_pull`, `python3 s2_dispatch.py`, `python3 s2_pull.py`.
2. Supervisor and registry: `code/th_night/supervise.py`, `registry.json` (no `--record`), `<tmp>` must not be created.
3. Guard and self-heal: `code/th_night/guard.py`, `health.py`, `wd_levels.py`, `agents_live.py`, `code/lead_watchdog/*` (slot_heal, lease_sweep, wake_watchdog, gh_pull, london_switch), `code/th_gridops/mem_guard.py`, `share_ctl.py`, `ag_nice_ctl.sh`, `code/th_proof/*` (box1_guard, mux_watch, feeder_rerun, slot_log, night_report).
4. Mix and refill: `code/th_nyeng/ny_mix3.py`, `ny_refill.py`, `ny_london_next.py`, `rerun_gen.py`, `fl_autoadd.py`, `fl_autonew.py`, `fl_share.py`.
5. Cap and share files and queue order: `_s3_*/CAP.txt`, `_th_tp/CAPS.txt`, `_th_tp/PRIORITY.txt`, `_s2/FU_SHARE.txt` and every share/flag file (`FOLLOWUP_FIRST*`, `DENY_KINDS.txt`, `london_on`), `_s2/QUEUES.txt` order and its PARKED markers.
6. The crontab of box 1 (backups: autopilot/crontab.bak_proof_2304).
7. Remote hosts: no package changes, no reboots, no mount changes, no process on a remote host other than engine workers/grid loops started by the box-1 dispatchers.

## STILL ALLOWED (research keeps working)
Research agents (stack, pass 2, exits, layers, first looks) keep working and may APPEND lines to their OWN queue files (`pending_*.txt` of their programme) and write their own result pages. No change of an existing line, no re-ordering, no new queue file in QUEUES.txt. Reading anything is always allowed.

## THE EXCEPTION RULE
Only a failure that is STOPPING WORK may be fixed (a host below 90% of cap that the automatic heal has not repaired within 15 min; a loop dead beyond the supervisor's 3-restarts-per-hour limit; results no longer landing; box-1 memory or disk at the floor). Then, in this order:
1. Back up the file or state first (`cp file file.bak_<owner>_<HHMM>`).
2. ONE change. Explicit pids only (never `pkill -f`). No credentials, no reboot, no deletion, no spend.
3. Verify the engine slots on ALL SIX hosts (HEALTH.md 'Engine slots' line) within 10 minutes; if a host is below 90% of its cap, say so in the line.
4. ONE MORNING.md line: `- HH:MMZ <agent> FREEZE EXCEPTION: <failure>; backup <file>; change <one change>; slots after <A n/cap, B n/cap, C n/cap, D n/cap, Dallas n/cap, box1 n/cap>`.
No second change without a new failure. If in doubt, do nothing and write the question at the top of autopilot/QUESTIONS_FOR_JOSH.md.

## WHO IS BOUND (the lead broadcasts this file to every agent at 02:00Z)
W-GRIDOPS (aafc0a5dadae3a88b): owns dispatchers/pullers/supervisor/guard/slot_heal/lease_sweep, may act only under the exception rule.
W-NYENG (a2ac20ed36cb00e42): ny_mix3, ny_refill, ladder builders; appends to its pending files only.
W-BEST (a591575ee08a10e3b): best_books feeders (code frozen, cron wrapper run_best.sh stays).
W-FASTLADDER (a3b8e54a46c26d0b7): fast-path crons (fl_*), frozen; may append lines to its own queue files.
W-PROOF (this agent): th_proof/*; may re-run drills read-only; exception rule applies to it too.
W-ASIA (a2cf9d86c085a4f9f), W-EXITENG, W-XB1, W-LAYERS, W-COMBO, W-SHORT (a4b931c164d0337bb), W-P2A (a818dd3f13812f3e3), W-P2B (adf0eb373bc00bff2), W-P2P (afe6fc591ea2b51c5), W-D8EXIT, W-NIGHT/W-NIGHT2 (gone; crons stay), W-LONENG (gone): research appends only; nothing in sections FROZEN.
The lead (Claude Code, tmux b5): bound like everyone; the lead and its watchdog levels decide nothing in the frozen list except under the exception rule. A real lead restart (flag <tmp>) needs Josh's agreement and is not part of the freeze.

## What heals things during the freeze with nobody touching anything
supervise.py (cron */5) restarts dead dispatchers/pullers/loops; slot_heal.py (cron */2) restarts a dispatcher of a host under 80% of cap for 10 min with runnable lines; mux_watch.py (cron */2) repairs hung ssh pull masters; box1_guard.py (cron */1) pauses side jobs at MemAvailable 50/46/43 GB and writers at /mnt/l2 < 150 GB; feeder_rerun.py (cron */5) re-runs a stale feeder; ny_refill.py (cron */10) refills the queue under 12 h; lease_sweep.py (cron */10) frees leases of dead holders and of a host unreadable for 30 min; wd_levels.py brings the lead back. Night report at 12:00Z: autopilot/NIGHT_REPORT.md + one MORNING.md block.
