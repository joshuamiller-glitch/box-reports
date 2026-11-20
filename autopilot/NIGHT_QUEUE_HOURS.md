# NIGHT QUEUE HOURS (generated Fri 03:30Z by code/th_proof/queue_hours_table.py)

Fleet rate used: MEASURED 11942 set-months/h = DONE files of the last 60 min (HEALTH.md says 11568). Needed to reach 16:00Z: 12.5 h = 149270 set-months; with the 2 h margin (18:00Z): 14.5 h = 173154.

## Lines in queue files now (unstarted, undone, unleased), by class

| class | lines | hours at rate |
|---|---|---|
| RK7CT controls (30 date-shift) | 90045 | 7.5 |
| ALN book-alone follow-ups (prior years, L6M) | 78632 | 6.6 |
| NY AM first looks / REPLACE-K7 / prior years (TL3_NYE) | 56359 | 4.7 |
| London first looks (TL3_LON) | 2449 | 0.2 |
| exit batches by cron (TL3_EXE, ex_ownmerit) | 107 | 0.0 |
| TOTAL | 227592 | 19.1 |

## Per queue file

- _split/pending_mix3.txt: 225061
- _lon/pending.txt: 2449
- _exiteng/pending.txt: 52
- _split/pending_rerun_bg.txt: 27
- _split/pending_rerun.txt: 3

## Coverage

Queue alone runs until Fri 22:33Z at 11942/h (19.1 h). Needed: 16:00Z Nov 20. COVERED with 6.6 h margin before 16:00Z (covers 16:00Z + 2 h = 18:00Z), no decision from anyone.
At 120% of the measured rate (14330/h, e.g. a fast stretch) the queue alone lasts 15.9 h (to Fri 19:22Z): still covers 16:00Z; the refill (target = hours to 16:00Z + 1.5 h) tops it up every 10 min.

## Automatic sources that ADD to the queue with no decision (state now)

- REFILL TARGET now 14.5 h (refill_target.py: hours to 16:00Z + 1.5 h, between 12 and 18 h); queue is 19.1 h, so the refill is idle
- ny_refill (cron */10): last run 2026-11-20T03:30Z, queue 19.7 h, actions ['FORCED TARGET 14.5 h']. Rule: under 12 h it extends ranked follow-ups beyond rank 50 (217 set-months per ranked NY AM cell), then writes refill_request.txt, under 8 h switches London first looks on.
- Asia stage-A lines (asia pending): 0 lines in file now
- London first looks (_lon/pending.txt, ladder cells 808 in _lon/ladder_cells.json): 2449 lines in file now
- NY AM both-side first looks (ny_bothside shards then ny_ladder): 225053 lines in file now
- exit batches by cron: {"released": 10, "t": 1795129802.7101383, "note": "replan 22:32Z against refreshed best_books: positions re-based; DONE lines are skipped by release()"}
- London switch: london_on False, london_pin False

Not counted (needs a decision or a cleared hook): pass-2 joint runs (hooks W-P2B), exit own-merit starts on live-book bases (88 lines held by lead order 2330Z), anything in PARKED queue files.
