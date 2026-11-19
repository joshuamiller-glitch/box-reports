# ORDER 20261119_2305Z: NIGHT-PROOF. Six rented machines must not halt while Josh sleeps.

Josh, 22:59Z: he goes to bed in about 4-6 hours (roughly 03:00-05:00Z) and cannot monitor. Six machines are rented by the hour. "tighten up everything so that things can't halt overnight - the whole point of expanding servers is to plow through this not wake up and say we've been down for 7 hours".

Everything below must be DONE and PROVEN by 02:00Z, while he is still awake. Proven = a real drill with the result posted, not "tested on copies". This order outranks new research features until it is closed. First looks and follow-ups keep running throughout.

## 1. Every way the fleet can stop, with its automatic recovery
Post autopilot/NIGHT_PROOF.md: one row per failure, columns: failure / what detects it / how fast / what heals it WITHOUT the lead and without an order / drilled yes-no with time and result. Rows at least:
a) A dispatcher or puller dies on any host (box 1, old Dallas, A, B, C, D). C and D were registered today: confirm they are in the supervisor WATCH list (s2_pull was noted as NOT in it at 19:02Z: fix that).
b) A host's engine slots fall far under its cap while lines are queued (tonight: Singapore 24 of 102 at 22:55Z; Dallas 0 on Nov 19 morning). Rule: slots < 80% of cap for 10 minutes with queued work = automatic restart of that host's dispatcher + alert E. No reserved share (re-run 75%, stack 20%, first-look 70%) may ever leave a slot empty: unused share falls through to the next class in the same dispatcher round.
c) The shared queue runs low: refill fires by itself (ranked follow-ups beyond rank 50, then London first looks). The refill has never acted for real: drill it now by letting ny_refill act once on the real queue (it adds useful lines, nothing is wasted).
d) A feeder cron fails silently (best_books failed 19:07-21:27Z unnoticed): feeder-age alerts exist: add an automatic re-run of the failed feeder and confirm every cron uses the venv python.
e) Results stop coming back to box 1 (pull lag, ssh mux socket dead, box-1 disk or inode full): detection + automatic socket rebuild; disk guard thresholds; what is paused FIRST if box-1 /mnt/l2 falls under 150 GB (name it: not the engine).
f) Box 1 memory: MemAvailable guard that pauses side jobs (pass-2 screens, builders, London shards, cold copy) BEFORE the engine or the pullers are hurt.
g) A remote host becomes unreachable or reboots: its leases are released and re-run elsewhere automatically; on return it rejoins without the lead (services start on boot? say yes / no per host and fix).
h) THE LEAD (tmux b5 on box 1) dies, hangs, hits a usage / context limit, or box 1 reboots. State exactly what keeps running with the lead gone (dispatchers, pullers, supervisor, refill, crons: all must), what restarts the lead, and how the restarted lead recovers its state (which file it reads first). If a lead restart has never been drilled, say so plainly: Josh will decide in the next hours whether to drill it while he is awake.
i) The watchdog itself and the supervisor die: who watches them (systemd / cron respawn)? Show it.
j) inbox_watch / the relay: orders from the chat assistant arrive by the Mac outbox AND by the GitHub relay (order 2103Z Nov 18). Confirm BOTH paths are alive now (post the time of the last successful GitHub pull and the polling interval) because the Mac may sleep.
k) A code edit by an agent breaks a dispatcher (several of today's drops followed restarts or edits). See item 2.

## 2. CHANGE FREEZE on fleet plumbing from 02:00Z to 14:00Z
No edits and no restarts of dispatchers, pullers, supervisor, guard, mix / refill scripts, cap files, QUEUES.txt order or share files during the freeze, EXCEPT to fix a failure that is stopping work, and then: backup, one change, verify slots on all six hosts within 10 minutes, one MORNING.md line. Planned changes go in before 02:00Z or wait. Research agents (stack, pass 2, exits, layers) keep working: they append lines to their own queue files only.

## 3. Drills to run now (one at a time, each a few minutes, post the line)
D1 kill the dispatcher on ONE host (use C): it must be restarted by the supervisor and slots back at cap within 10 minutes with no one touching it.
D2 kill a puller on one host (use D): same.
D3 stale ssh mux socket on one host: pulls recover by themselves.
D4 the refill acting on the real queue (item 1c).
D5 guard alert -> automatic action for "slots < 80% of cap for 10 min" (item 1b), on Singapore's real case from tonight.
Anything that fails a drill gets fixed and re-drilled before 02:00Z.

## 4. Enough work for the whole night, queued in files, not waiting on an agent's decision
Post at 02:00Z: queue hours at the six-machine rate, and the hours each automatic source adds (Asia stage-A lines, NY AM both-side first looks, ranked follow-ups extension, exit batches by cron, pass-2 joint runs when hooks are cleared, London first looks). The total must cover at least until 16:00Z Nov 20 with no decision from anyone. If it does not, say now what is missing.

## 5. Night report for the morning
One block in MORNING.md at 12:00Z: hours each host ran at >= 90% of cap, any drop (start, end, cause, what healed it), set-months landed overnight per programme.

Answer: NIGHT_PROOF.md + one MORNING.md line per drill. Items 1-3 before 02:00Z.
