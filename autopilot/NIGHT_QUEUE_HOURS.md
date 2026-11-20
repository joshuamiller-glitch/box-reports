# NIGHT QUEUE HOURS (generated Fri 02:00Z by code/th_proof/queue_hours_table.py)

Fleet rate used: MEASURED 12718 set-months/h = DONE files of the last 60 min (HEALTH.md says 12672). Needed to reach 16:00Z: 14.0 h = 178047 set-months; with the 2 h margin (18:00Z): 16.0 h = 203483.

## Lines in queue files now (unstarted, undone, unleased), by class

| class | lines | hours at rate |
|---|---|---|
| RK7CT controls (30 date-shift) | 92978 | 7.3 |
| ALN book-alone follow-ups (prior years, L6M) | 78158 | 6.1 |
| NY AM first looks / REPLACE-K7 / prior years (TL3_NYE) | 62041 | 4.9 |
| London first looks (TL3_LON) | 2565 | 0.2 |
| exit batches by cron (TL3_EXE, ex_ownmerit) | 107 | 0.0 |
| TOTAL | 235849 | 18.5 |

## Per queue file

- _split/pending_mix3.txt: 233200
- _lon/pending.txt: 2565
- _exiteng/pending.txt: 52
- _split/pending_rerun_bg.txt: 29
- _split/pending_rerun.txt: 3

## Coverage

Queue alone runs until Fri 20:32Z at 12718/h (18.5 h). Needed: 16:00Z Nov 20. COVERED with 4.5 h margin before 16:00Z (covers 16:00Z + 2 h = 18:00Z), no decision from anyone.
At 120% of the measured rate (15262/h, e.g. a fast stretch) the queue alone lasts 15.5 h (to Fri 17:27Z): still covers 16:00Z; the refill (target = hours to 16:00Z + 1.5 h) tops it up every 10 min.

## Automatic sources that ADD to the queue with no decision (state now)

- REFILL TARGET now 16.0 h (refill_target.py: hours to 16:00Z + 1.5 h, between 12 and 18 h); queue is 18.5 h, so the refill is idle
- ny_refill (cron */10): last run 2026-11-20T02:00Z, queue 18.6 h, actions ['FORCED TARGET 16.0 h']. Rule: under 12 h it extends ranked follow-ups beyond rank 50 (217 set-months per ranked NY AM cell), then writes refill_request.txt, under 8 h switches London first looks on.
- Asia stage-A lines (asia pending): 0 lines in file now
- London first looks (_lon/pending.txt, ladder cells 808 in _lon/ladder_cells.json): 2565 lines in file now
- NY AM both-side first looks (ny_bothside shards then ny_ladder): 233193 lines in file now
- exit batches by cron: {"released": 10, "t": 1795129802.7101383, "note": "replan 22:32Z against refreshed best_books: positions re-based; DONE lines are skipped by release()"}
- London switch: london_on False, london_pin False

Not counted (needs a decision or a cleared hook): pass-2 joint runs (hooks W-P2B), exit own-merit starts on live-book bases (88 lines held by lead order 2330Z), anything in PARKED queue files.
