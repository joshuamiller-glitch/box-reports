# Asia: every handoff from "a book passes its checks" to "stack FINAL posted" (lead, 18:00Z, Josh's order item 4)

Plain words. "Who notices" is who WOULD see it if the step did not happen, as of now. Where the answer is "nobody",
that is a gap and is listed under **Gaps** with the fix. Heartbeat lines (HB, every 30 min per loop) and the lead's
stall check (code/lead_watchdog/stall_check.py, run every lead cycle) are the new net.

## The path

| # | Handoff | Who does it | How | Who notices if it does NOT happen (today) |
|---|---|---|---|---|
| 1 | A cell is on the first-look list (old-split rank, positive in L6M and L3M) | W-D8SPEC builds bars, events and set JSONs | `pending_canc_fl_N.txt` files in `/mnt/l2/l2vast/_d8spec/` | W-D8SPEC's own build log; nobody else |
| 2 | New queue file becomes a queue line | W-GRIDOPS, BY HAND (the automatic editor was denied) | a read-only watch tells it a new `_d8spec/pending*.txt` exists; it adds a QUEUES.txt line with a backup; 5-minute audit of files vs QUEUES.txt | its own audit (posts when it finds an unwired file); this was missed for 15-45 min twice (fl_6..16, ct files) |
| 3 | Set JSONs + events reach the hosts | automatic prepush (`d8_prepush.py`, every 40 s) | globs `pending_canc_*.txt` | W-GRIDOPS slot split ("on-host" counts); a missing push shows as 0 slots for D8 (this stalled D8 for ~1 h at 16:30-17:15Z and was found by the hourly slot split, not by an alarm) |
| 4 | Dispatchers launch the line | dispatchers (first runnable line in queue order) | QUEUES.txt order; stage-1 rows and bulk files sit ahead | slot split by class; the lead reading it |
| 5 | Result lands and is pulled back | pullers (s2_pull / s3_pull) | DONE + trades on box 1 | stale-results check (signature), lease sweep; a lease marked failed with a finished result on the host sat 12 h once (L0fcc21c7 202608) |
| 6 | First-look result passes L6M and L3M > 0 -> prior-year lines | W-D8SPEC `canc_auto.py` (every 10 min) | writes `pending_canc_py_N.txt` | its heartbeat (new); W-GRIDOPS must then wire the file by hand (handoff 2 again) |
| 7 | Prior years pass gate b -> 30 luck controls | W-D8SPEC `canc_auto.py` | writes `pending_canc_ct_N.txt` | same as 6 |
| 8 | Controls land -> the book counts as an own-checks passer (a+b+c+d) | W-COMBO's gate/pool code (reads `aln_state.json`, classifier) | recomputed every minute | W-COMBO's Asia COUNTDOWN line ("passed a+b+c waiting for controls n"); if n never falls nobody sees it today except the lead |
| 9 | Pool lists reach the other agents | each agent re-reads W-COMBO's pool: W-P2A (20 min), W-LAYERS (30 min), W-BRKT (by hand / by cycle), W-EXITENG (cron :12/:42) | file reads, no push | each agent's own heartbeat; a book that joins the pool but is never picked up is invisible unless the lead compares lists |
| 10 | Per-book fits (layers, brackets, pass 2, exits) are run | W-LAYERS pool driver, W-BRKT driver, W-P2A loop, W-EXITENG cron | their own queue files, wired by W-GRIDOPS by hand or already in QUEUES.txt | HB lines (new) |
| 11 | Fitted picks reach stage 2 | W-BRKT `fitted_proposal.json`; W-LAYERS picks; W-COMBO `_combo/fitted_books.json` | file formats agreed by message only; NOT wired automatically | **nobody** (see gaps) |
| 12 | Stage-2 re-pick runs on fitted books | W-COMBO FIT=1 loop | needs `fitted_books.json` | W-COMBO's HB (new) |
| 13 | Stack FINAL posted, stack controls run | W-COMBO final phase | control lines re-queued at the front by its reassert() | stall twice already (loop crash 05:30Z, reassert bug 08:59Z-11:23Z); now HB |
| 14 | Stack read by the lead and posted to Josh | lead | MORNING.md line | the lead's stall check; Josh reading the page |

## Gaps (who would NOT notice), and the fix
1. **Handoff 11 (fitted picks -> `fitted_books.json`) is manual.** Fix: W-COMBO's heartbeat must show "fitted_books.json books n, last updated"; the lead's check treats a pool book with a PASSED stage-2 pick but no entry in `fitted_books.json` after 30 minutes as a stall. Owner: W-COMBO + lead.
2. **Handoff 8: a controls shortfall is invisible.** 87 books were "waiting for controls" at 17:52Z; nothing says how many of those 87 have their 30 control sets queued. Fix: W-COMBO's heartbeat prints "waiting_on n sets | queued_or_running m" for exactly this (the check that caught the 05:30Z and 11:23Z failures). Owner: W-COMBO.
3. **Handoff 2 (manual wiring)**: depends on one agent noticing. Fix in place: its 5-minute audit posts a line; the lead's stall check reads "queue" heartbeats. Not fixed: an automatic editor was denied by the harness and is NOT proposed again without an explicit OK covering the block.
4. **Handoff 3 (prepush) failing silently** (one-hour stall at 16:30Z): Fix: W-GRIDOPS's heartbeat shows "waiting_on = sets not on hosts".
5. **Handoff 5 (failed lease with a finished result)**: stale-results check does not catch it; W-GRIDOPS's slot split and lease audit do, by hand. Open item for 14:00Z-style cleanup (puller DONE-check race).
6. **Handoff 9 (pool list propagation)**: no one compares lists. Fix: the lead's stall check prints each agent's last-read pool count (from HB lines) next to W-COMBO's pool size.

## What the lead checks every cycle (new)
`python3 -I code/lead_watchdog/stall_check.py`: a heartbeat missing for 45 min, or "waiting_on > 0 with queued_or_running 0" on two heartbeats in a row = DOWN: find out why, fix it, write what happened (MORNING.md line, "LEAD STALL FIX ...").
Expected heartbeat names: asia-own, asia-stay, ny-own, widening, layer-fit, layer-null, pass2, brackets, exits, canc-auto, canc-bulk, queue.
