## NY AM ONE DATE LINE (order 1750Z, restated 1806Z after PARKING the other-book rows: first looks + ranked follow-ups only)

**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 4499 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 07:47Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 07:47Z** (low case 2026-11-20 09:23Z); follow-ups of strict passers end 2026-11-20 10:53Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 10:59Z** (17 h); combination stage: W-COMBO; LONG POLE: follow-ups.**

| part (NY AM) | set-months left | measured last 60 min |
|---|---|---|
| first looks: stage A REPLACE-K7 lines (current list 6493 cells, all built; 979 of 6493 cells first-looked; 2588 old-seed-only cells never built, not counted) | 24697 | 1462 /h |
| other-book REPLACE rows P7/M7/H7 (0 queued + ~0 to be appended as first looks finish: 4116 cells x 85% non-negative x 18) | 0 | 114 /h |
| stage B/C of the strict passers (prior years 37 + controls 526 left for the 8 strict sets in 5 cells) | 563 | 163 /h |
| layers (8309 queued, W-LAYERS + 1388 to be created for the 4 new passer cells) | 9697 | 1097 /h |
| exit pairs (17 queued) + exit rows for the 5 passer cells (309 each, families unbuilt until builders W-XB1/XB2 ~21:00Z) | 1562 | 35 /h |
| follow-ups of FUTURE strict passers (about 21 more cells x 873 set-months each, at the measured passer rate 5 of 979) | 18352 | 0 /h |

Other streams in the mix: Asia first looks 11025, follow-ups total 39906 (NY AM 30174 + Asia 9732).

| fleet rate | Asia first looks end | NY AM first looks end | NY AM stream (first looks + other-book rows) ends | follow-ups end | **ALL (stage 1)** |
|---|---|---|---|---|---|
| 5076 /h | 2026-11-19 23:17Z | 2026-11-20 06:11Z | 2026-11-20 06:11Z | 2026-11-20 08:59Z | **2026-11-20 09:05Z** (15 h) |
| 4499 /h | 2026-11-19 23:59Z | 2026-11-20 07:47Z | 2026-11-20 07:47Z | 2026-11-20 10:53Z | **2026-11-20 10:59Z** (17 h) |
| 4000 /h | 2026-11-20 00:41Z | 2026-11-20 09:23Z | 2026-11-20 09:23Z | 2026-11-20 12:59Z | **2026-11-20 13:05Z** (19 h) |

OWN-MERIT FOLLOW-UPS (order 1806Z: ranked, no cap): follow-ups for the top-N ranked cells per session = N x 873 set-months (prior years 37 + 30 controls 180 + layers 347 + exit rows 309); fleet 4499 /h; the stage-1 date depends on N:

| N cells per session (NY AM and Asia each) | extra follow-up set-months | ALL stage 1 ends | hours |
|---|---|---|---|
| 50 | 87300 | 2026-11-21 06:23Z | 36 |
| 100 | 174600 | 2026-11-22 01:47Z | 56 |
| 200 | 349200 | 2026-11-23 16:41Z | 95 |
| 500 | 873000 | 2026-11-28 13:05Z | 211 |

Assumptions: weights Asia first looks 41.3%% / NY AM stream 28.7%% / follow-ups 30%% with the share of an EMPTY stream handed to the others (ny_mix3.py); the other-book rows are modelled as available from the start (they are appended as first looks complete, so this is the optimistic end); strict-passer follow-ups as in the part table (8 sets in 5 cells + extrapolated future passers). The mix is applied on the dispatchers (the lead measures it).
