# NIGHT QUEUE HOURS (generated Thu 23:39Z by code/th_proof/queue_hours_table.py)

Fleet rate used: 9966 set-months/h (HEALTH.md: DONE files in 30 min x 2, six machines). Needed to reach 16:00Z Nov 20: 16.3 h = 162790 set-months.

## Lines in queue files now (unstarted, undone, unleased), by class

| class | lines | hours at rate |
|---|---|---|
| RK7CT controls (30 date-shift) | 80871 | 8.1 |
| ALN book-alone follow-ups (prior years, L6M) | 70640 | 7.1 |
| NY AM first looks / REPLACE-K7 / prior years (TL3_NYE) | 29657 | 3.0 |
| Asia stage A / follow-ups (TL3_ASI_) | 3833 | 0.4 |
| London first looks (TL3_LON) | 330 | 0.0 |
| exit batches by cron (TL3_EXE, ex_ownmerit) | 55 | 0.0 |
| layers (TL3_NYL) | 12 | 0.0 |
| TOTAL | 185398 | 18.6 |

## Per queue file

- _split/pending_mix3.txt: 176850
- _combo/allnew_pending.txt: 6178
- _split/pending_rerun_bg.txt: 2037
- _lon/pending.txt: 330
- _split/pending_rerun.txt: 3

## Coverage

Queue alone runs until Fri 18:16Z at 9966/h (18.6 h). Needed: 16:00Z Nov 20. COVERED with 2.3 h margin, no decision from anyone.
At 80% of the measured rate (7973/h) the queue lasts 23.3 h (to Fri 22:55Z): still covers 16:00Z.

## Automatic sources that ADD to the queue with no decision (state now)

- ny_refill (cron */10): last run 2026-11-19T23:30Z, queue 20.5 h, actions []. Rule: under 12 h it extends ranked follow-ups beyond rank 50 (217 set-months per ranked NY AM cell), then writes refill_request.txt, under 8 h switches London first looks on.
- Asia stage-A lines (asia pending): 3251 lines in file now
- London first looks (_lon/pending.txt, ladder cells 808 in _lon/ladder_cells.json): 330 lines in file now
- NY AM both-side first looks (ny_bothside shards then ny_ladder): 176847 lines in file now
- exit batches by cron: {"released": 10, "t": 1795129802.7101383, "note": "replan 22:32Z against refreshed best_books: positions re-based; DONE lines are skipped by release()"}
- London switch: london_on False, london_pin False

Not counted (needs a decision or a cleared hook): pass-2 joint runs (hooks W-P2B), exit own-merit starts on live-book bases (88 lines held by lead order 2330Z), anything in PARKED queue files.
