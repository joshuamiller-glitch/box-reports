# QUEUE HOURS, REFILL AND WHAT QUEUES ONLY ON COMPLETION (W-NYENG, 2026-11-19 21:25Z, order 2117Z item 1)
Fleet rate used: 7,900 set-months/h (HEALTH 8,100 at 21:10Z, tp_admit 7,825; incl. Server C at cap ~100; D (+~1,000) not counted).

## (a) Queue hours now by source (unstarted, unfinished, unleased lines in pending_mix3.txt after the refill below ran at 21:19Z)
| source / group | lines | hours at 7,900/h |
|---|---|---|
| controls (30 date-shift, ranked cells: 59,949; top-50 NY AM 7,900 + Asia 694 of them) | 59,949 | 7.6 |
| NY AM first looks (REPLACE-K7) | 19,396 | 2.5 |
| prior years (ranked cells) | 17,574 | 2.2 |
| layers (W-LAYERS) | 11,524 | 1.5 |
| Asia first looks | 4,215 | 0.5 |
| exit | 2 | 0.0 |
| **mix3 total** (+ _lon/pending.txt 315 lines) | **112,660** | **14.3 h** |
Before the refill the queue was 54.8k lines = 6.8 h (HEALTH 21:10Z: 52.3k = 6.7 h).
Expected hours at fixed rate 7,900/h, no further additions (lines left = 112.7k - 7.9k x t): 00:00Z (t = 2.6 h) 92k = 11.6 h; 04:00Z (t = 6.6 h) 60k = 7.6 h; 08:00Z (t = 10.6 h) 29k = 3.7 h. With D (+1,000/h) each figure is ~12% lower. Additions that are NOT in these figures: ~30.7k Asia stage-A lines appended by W-ASIA as cells pass stage A, W-LAYERS' cron, W-EXITENG's batch release, and the automatic refill below.

## (b) The ~81k top-50-per-session follow-up set-months: in a queue file NOW vs waiting on scripts
| part | in a queue file now | waits on |
|---|---|---|
| NY AM top 50: prior years + 30 controls | 1,629 + 7,900 = 9,529 of 10.2k remaining (all 50 cells queued by ranked_follow at 21:1xZ: 26 cells whose first look was complete had not been queued because the 15-min advance step had stalled 12 min on slow stats; fixed) | nothing |
| NY AM top 50: layers | 1,114 of 16.9k | W-LAYERS cron (reads its pass list, not the ranked list): ~15.8k not queued |
| NY AM top 50: exit rows | 0 of 15.4k | W-EXITENG batch release (after the both-side screen ~22:00Z) |
| Asia top 50: prior years + controls | 829 + 694 of 9.1k | W-ASIA's gate / its ~30.7k stage-A appends |
| Asia top 50: layers | 2,817 of 14.4k | W-LAYERS cron |
| Asia top 50: exit rows | 0 of 15.3k | W-EXITENG |
So of 81.4k: ~14.9k are in a queue file now (18%); ~66k (82%) wait on W-LAYERS' cron (~30k), W-EXITENG's release (~30.7k: my 309 per cell is a ceiling; W-EXITENG's measured exit pairs are 12 set-months each, 36 per 3 slots, so the real figure may be far lower), and W-ASIA's gate (~8k). Beyond rank 50 the refill queues prior years + controls for 272 more ranked cells now.

## (c) Exit stage after the both-side screen (~22:00Z) and pass 2 (Asia after first looks ~23:20Z)
Not mine and not queued yet (0 exit lines in the queue; STK 0). Their cost is unknown to me beyond the measured 12 set-months per exit pair; assuming 4 pairs per candidate x 100 candidates = ~5k set-months (<1 h at 7,900/h) versus my 30.7k ceiling. Pass 2 (grid) runs on the grid cores, not in the engine queue. Both arrive AFTER the 22:00-23:20Z window, so tonight's queue hours must not depend on them: the refill covers that.

## (d) AUTOMATIC REFILL (code/th_nyeng/ny_refill.py, cron every 10 min, flock; `ny_refill.py --check` prints hours and exits 2 when < 6 h for the W-GRIDOPS guard)
- hours = unstarted lines of every QUEUES.txt file / fleet rate (HEALTH, else tp_admit). Target 12 h (refills to 14 h).
- < 12 h: extends the ranked follow-ups DOWN the own-merit list beyond rank 50 (prior years 37 + 30 controls = 217 per cell, REPLACE-K7 set, first look complete, parked twins skipped, rank order, no cap on survivors). First run 21:19Z: asked 58.6k, queued 58.8k set-months (271 cells). Capacity left: 472 ranked cells with a complete first look not yet queued = ~102k set-months (13 h at 7,900/h), growing as first looks finish.
- when that runs out: writes the next 100 ranked cells to /mnt/l2/l2vast/_split/refill_request.txt (for W-LAYERS layer sets and W-EXITENG exit rows to consume).
- < 8 h: London first looks (stage order): London ladder builder code/th_loneng/lon_ladder.py does NOT exist (the London list has 808 cells in _lon/ladder_cells.json; asia_ladder.py is the template): flag LONDON_BUILDER_MISSING in /mnt/l2/l2vast/_split/refill_state.json; needs W-LONENG.
- first looks keep their 70% share of the mix; refill only adds follow-up lines.
