## NY AM ONE DATE LINE (order 1750Z, restated 1900Z: 4,557-cell ladder, other-book rows parked, id-duplicate first-look lines parked: first looks + ranked follow-ups)

**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 5530 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 03:55Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-20 03:55Z** (low case 2026-11-20 07:25Z); follow-ups of strict passers end 2026-11-20 07:13Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-20 07:19Z** (12 h); combination stage: W-COMBO; LONG POLE: follow-ups.**

| part (NY AM) | set-months left | measured last 60 min |
|---|---|---|
| first looks: stage A REPLACE-K7 lines (ladder = 4557 DISTINCT cells, all built; 976 first-looked; the 2588 old-seed-only ids are duplicate ids of built cells; duplicate-side lines of identical-stream pairs parked) | 20100 | 1856 /h |
| other-book REPLACE rows P7/M7/H7 (0 queued + ~0 to be appended as first looks finish: 3350 cells x 78% non-negative x 18) | 0 | 123 /h |
| stage B/C of the strict passers (prior years 37 + controls 526 left for the 8 strict sets in 5 cells) | 563 | 187 /h |
| layers (10524 queued, W-LAYERS + 1388 to be created for the 4 new passer cells) | 11912 | 788 /h |
| exit pairs (8 queued) + exit rows for the 5 passer cells (309 each, families unbuilt until builders W-XB1/XB2 ~21:00Z) | 1553 | 63 /h |
| follow-ups of FUTURE strict passers (about 17 more cells x 873 set-months each, at the measured passer rate 5 of 976) | 14982 | 0 /h |

Other streams in the mix: Asia first looks 9297, follow-ups total 39143 (NY AM 29010 + Asia 10133).

| fleet rate | Asia first looks end | NY AM first looks end | NY AM stream (first looks + other-book rows) ends | follow-ups end | **ALL (stage 1)** |
|---|---|---|---|---|---|
| 5076 /h | 2026-11-19 23:13Z | 2026-11-20 04:43Z | 2026-11-20 04:43Z | 2026-11-20 08:19Z | **2026-11-20 08:25Z** (14 h) |
| 5530 /h | 2026-11-19 22:49Z | 2026-11-20 03:55Z | 2026-11-20 03:55Z | 2026-11-20 07:13Z | **2026-11-20 07:19Z** (12 h) |
| 4000 /h | 2026-11-20 00:25Z | 2026-11-20 07:25Z | 2026-11-20 07:25Z | 2026-11-20 11:55Z | **2026-11-20 12:01Z** (17 h) |

OWN-MERIT FOLLOW-UPS (order 1806Z: ranked, no cap): follow-ups for the top-N ranked cells per session = N x 873 set-months (prior years 37 + 30 controls 180 + layers 347 + exit rows 309); fleet 5530 /h; the stage-1 date depends on N:

| N cells per session (NY AM and Asia each) | extra follow-up set-months | ALL stage 1 ends | hours |
|---|---|---|---|
| 50 | 87300 | 2026-11-20 23:07Z | 28 |
| 100 | 174600 | 2026-11-21 14:55Z | 44 |
| 200 | 349200 | 2026-11-22 22:25Z | 76 |
| 500 | 873000 | 2026-11-26 21:13Z | 170 |

Assumptions: weights Asia first looks 41.3%% / NY AM stream 28.7%% / follow-ups 30%% with the share of an EMPTY stream handed to the others (ny_mix3.py); the other-book rows are modelled as available from the start (they are appended as first looks complete, so this is the optimistic end); strict-passer follow-ups as in the part table (8 sets in 5 cells + extrapolated future passers). The mix is applied on the dispatchers (the lead measures it).
