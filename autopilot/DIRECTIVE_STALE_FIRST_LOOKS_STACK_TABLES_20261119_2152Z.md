# ORDER 20261119_2152Z: first looks run on old event files + stack tables + box 1

## 1. First looks that ran BEFORE their events file was rewritten (W-EXITENG status 35, W-GRIDOPS 21:41Z)
Facts as posted: 2,324 NY AM RK7 and 4,930 Asia RA7 set-months started before the mtime of the events file their set loads now (1,198 sets). Of 20 re-run so far, 6 differed (two NY AM cells, Lef8bf664 and L773badc8; events rewritten with the mode filter at 17:03Z). The scorecards (BEST_BOOKS_ASIA / NYAM), the ranked follow-ups, the stack dry runs and the pass-2 lists all read these first looks.
- Run the CONTENT test on ALL 1,198 sets now (signals in the old month's MF1 trades vs the current events file). It is cheap and needs no engine slots. Post: sets identical in content / sets changed, per session.
- Every changed set-month: park (move, never delete), re-run for real, compare. Order of re-runs: scorecard rank order (top books first), both sessions.
- Until a changed cell is re-run, mark it "(STALE-PENDING RE-RUN)" on the scorecards (W-BEST already has the column) and keep it OUT of: the frozen pass-2 lists, stack building, the exit stage and the ranked follow-up queue. If a cell already in PASS2_LIST_ASIA / NYAM or in a stack dry run is changed, say which and redo that part after the re-run.
- For each changed cell say WHICH book the result now describes (side: long / short / both) so the "what it is" column matches the trades. Josh's rule: D8 codes each book exactly as tested.
- Same content test for prior-year, control and layer set-months of those cells.
- One line when done: how many of the current top 50 per session changed, and whether any top-5 book changed.

## 2. Stack-building tables (W-COMBO)
The stack queue emptied at 20:46Z (927 set-months done) and no result line has been posted since 19:48Z. Post the tables: Asia prior years + last-3-months + persistence for the four moves (swap U7 -> Ldcdb0b6e, swap A7 -> Lc4e74264, add Ldcdb0b6e, add L5c9e11b3); combinations AC1-AC5; NY AM variants NV1-NV4 (persistence vs the 0.58 gate); wave-2 triples and drop-one results. Drawdown first. All still DRY RUN labels. If any stack used a cell that item 1 marks changed, flag the row.

## 3. Box 1 engine slots 17-20 of 36 for 45+ minutes while busy 100%
One line on HEALTH: what holds the other cores (pulls for five hosts, pass-2 screens, hook identity, London build shards, pushes to D, cold copy) and whether box 1 is the hub on purpose now. If yes, lower its engine cap to what it can really run so the slot line is honest, and confirm result pull-back lag per host stays under 2 minutes with six machines.

## 4. London, when the refill turns it on
The London ladder is "REPLACE-only vs M7" as the first-look vehicle. Fine as a vehicle. But London books are scored on their OWN merit exactly like Asia and NY AM (order 1806Z): BEST_BOOKS_LONDON.md with the same columns, live London books as ordinary rows. No "beats M7" verdicts as the test.

Answer in MORNING.md.
