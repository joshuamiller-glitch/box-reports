# NIGHT QUEUE HOURS (generated Thu 23:40Z by code/th_proof/queue_hours_table.py)

Fleet rate used: 10460 set-months/h (HEALTH.md: DONE files in 30 min x 2, six machines). Needed to reach 16:00Z Nov 20: 16.3 h = 170827 set-months.

## Lines in queue files now (unstarted, undone, unleased), by class

| class | lines | hours at rate |
|---|---|---|
| RK7CT controls (30 date-shift) | 80870 | 7.7 |
| ALN book-alone follow-ups (prior years, L6M) | 70597 | 6.7 |
| NY AM first looks / REPLACE-K7 / prior years (TL3_NYE) | 29654 | 2.8 |
| Asia stage A / follow-ups (TL3_ASI_) | 3828 | 0.4 |
| London first looks (TL3_LON) | 330 | 0.0 |
| exit batches by cron (TL3_EXE, ex_ownmerit) | 55 | 0.0 |
| layers (TL3_NYL) | 12 | 0.0 |
| TOTAL | 185346 | 17.7 |

## Per queue file

- _split/pending_mix3.txt: 176844
- _combo/allnew_pending.txt: 6135
- _split/pending_rerun_bg.txt: 2034
- _lon/pending.txt: 330
- _split/pending_rerun.txt: 3

## Coverage

Queue alone runs until Fri 17:23Z at 10460/h (17.7 h). Needed: 16:00Z Nov 20. COVERED with 1.4 h margin, no decision from anyone.
At 80% of the measured rate (8368/h) the queue lasts 22.1 h (to Fri 21:49Z): still covers 16:00Z.

## Automatic sources that ADD to the queue with no decision (state now)

- ny_refill (cron */10): last run 2026-11-19T23:40Z, queue 18.4 h, actions []. Rule: under 12 h it extends ranked follow-ups beyond rank 50 (217 set-months per ranked NY AM cell), then writes refill_request.txt, under 8 h switches London first looks on.
- Asia stage-A lines (asia pending): 3249 lines in file now
- London first looks (_lon/pending.txt, ladder cells 808 in _lon/ladder_cells.json): 330 lines in file now
- NY AM both-side first looks (ny_bothside shards then ny_ladder): 176843 lines in file now
- exit batches by cron: {"released": 10, "t": 1795129802.7101383, "note": "replan 22:32Z against refreshed best_books: positions re-based; DONE lines are skipped by release()"}
- London switch: london_on False, london_pin False

Not counted (needs a decision or a cleared hook): pass-2 joint runs (hooks W-P2B), exit own-merit starts on live-book bases (88 lines held by lead order 2330Z), anything in PARKED queue files.
