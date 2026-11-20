# NIGHT QUEUE HOURS (generated Fri 01:14Z by code/th_proof/queue_hours_table.py)

Fleet rate used: MEASURED 14100 set-months/h = DONE files of the last 60 min (HEALTH.md says 14294). Needed to reach 16:00Z: 14.8 h = 208187 set-months; with the 2 h margin (18:00Z): 16.8 h = 236387.

## Lines in queue files now (unstarted, undone, unleased), by class

| class | lines | hours at rate |
|---|---|---|
| RK7CT controls (30 date-shift) | 94545 | 6.7 |
| ALN book-alone follow-ups (prior years, L6M) | 77744 | 5.5 |
| NY AM first looks / REPLACE-K7 / prior years (TL3_NYE) | 24890 | 1.8 |
| London first looks (TL3_LON) | 2637 | 0.2 |
| exit batches by cron (TL3_EXE, ex_ownmerit) | 107 | 0.0 |
| TOTAL | 199923 | 14.2 |

## Per queue file

- _split/pending_mix3.txt: 195115
- _lon/pending.txt: 2637
- _combo/allnew_pending.txt: 1441
- _exiteng/pending.txt: 608
- _split/pending_stack_urgent.txt: 90
- _split/pending_rerun_bg.txt: 29
- _split/pending_rerun.txt: 3

## Coverage

Queue alone runs until Fri 15:24Z at 14100/h (14.2 h). Needed: 16:00Z Nov 20. NOT COVERED: short by 0.6 h (8264 set-months).
At 120% of the measured rate (16920/h, e.g. a fast stretch) the queue alone lasts 11.8 h (to Fri 13:03Z): does NOT cover 16:00Z by itself; the refill (target = hours to 16:00Z + 1.5 h) tops it up every 10 min.

## Automatic sources that ADD to the queue with no decision (state now)

- REFILL TARGET now 16.3 h (refill_target.py: hours to 16:00Z + 1.5 h, between 12 and 18 h); queue is 14.2 h, so the refill will act on its next */10 tick
- ny_refill (cron */10): last run 2026-11-20T01:10Z, queue 12.0 h, actions ['ranked_follow beyond rank 50: asked 28982 set-months, queued 29126']. Rule: under 12 h it extends ranked follow-ups beyond rank 50 (217 set-months per ranked NY AM cell), then writes refill_request.txt, under 8 h switches London first looks on.
- Asia stage-A lines (asia pending): 0 lines in file now
- London first looks (_lon/pending.txt, ladder cells 808 in _lon/ladder_cells.json): 2637 lines in file now
- NY AM both-side first looks (ny_bothside shards then ny_ladder): 207848 lines in file now
- exit batches by cron: {"released": 10, "t": 1795129802.7101383, "note": "replan 22:32Z against refreshed best_books: positions re-based; DONE lines are skipped by release()"}
- London switch: london_on False, london_pin False

Not counted (needs a decision or a cleared hook): pass-2 joint runs (hooks W-P2B), exit own-merit starts on live-book bases (88 lines held by lead order 2330Z), anything in PARKED queue files.
