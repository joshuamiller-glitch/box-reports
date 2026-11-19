## NY AM ONE DATE LINE (order 1750Z, corrected 1830Z: simulated mix)

**NY AM STAGE 1 ONE DATE LINE (simulated mix with handoff of empty streams, fleet 4401 /h measured / 5076 /h lead / 4000 low): NY AM first looks end 2026-11-20 09:24Z; NY AM stream incl. other-book REPLACE rows ends **2026-11-21 06:48Z** (low case 2026-11-21 10:24Z); follow-ups of strict passers end 2026-11-20 16:42Z (exit rows also wait for the unbuilt exit families ~21:00Z); FLEET-WIDE stage 1 (Asia + NY AM) ends **2026-11-21 06:54Z** (37 h); combination stage: W-COMBO; LONG POLE: NY AM stream: the other-book REPLACE rows (77397 set-months after the first looks).**

| part (NY AM) | set-months left | measured last 60 min |
|---|---|---|
| first looks: stage A REPLACE-K7 lines (current list 6493 cells, all built; 878 of 6493 cells first-looked; 2588 old-seed-only cells never built, not counted) | 25065 | 1217 /h |
| other-book REPLACE rows P7/M7/H7 (13145 queued + ~64252 to be appended as first looks finish: 4178 cells x 85% non-negative x 18) | 77397 | 148 /h |
| stage B/C of the strict passers (prior years 37 + controls 526 left for the 8 strict sets in 5 cells) | 563 | 119 /h |
| layers (8145 queued, W-LAYERS + 1388 to be created for the 4 new passer cells) | 9533 | 1201 /h |
| exit pairs (54 queued) + exit rows for the 5 passer cells (309 each, families unbuilt until builders W-XB1/XB2 ~21:00Z) | 1599 | 0 /h |
| follow-ups of FUTURE strict passers (about 24 more cells x 873 set-months each, at the measured passer rate 5 of 878) | 20768 | 0 /h |

Other streams in the mix: Asia first looks 17120, follow-ups total 42521 (NY AM 32463 + Asia 10058).

| fleet rate | Asia first looks end | NY AM first looks end | NY AM stream (first looks + other-book rows) ends | follow-ups end | **ALL (stage 1)** |
|---|---|---|---|---|---|
| 5076 /h | 2026-11-20 02:00Z | 2026-11-20 07:18Z | 2026-11-21 01:48Z | 2026-11-20 13:36Z | **2026-11-21 01:54Z** (32 h) |
| 4401 /h | 2026-11-20 03:18Z | 2026-11-20 09:24Z | 2026-11-21 06:48Z | 2026-11-20 16:42Z | **2026-11-21 06:54Z** (37 h) |
| 4000 /h | 2026-11-20 04:12Z | 2026-11-20 11:00Z | 2026-11-21 10:24Z | 2026-11-20 18:54Z | **2026-11-21 10:30Z** (41 h) |

PROPOSAL (NOT applied, for Josh): other-book rows only for cells whose K7 first look has L6M ulcer lower (1.5% of first looks = ~1,132 rows) + a 100-cell validation sample (1,800 rows): ALL ends 2026-11-20 13:54Z (20 h) at 4401 /h instead of 2026-11-21 06:54Z.

Assumptions: weights Asia first looks 41.3%% / NY AM stream 28.7%% / follow-ups 30%% with the share of an EMPTY stream handed to the others (ny_mix3.py); the other-book rows are modelled as available from the start (they are appended as first looks complete, so this is the optimistic end); strict-passer follow-ups as in the part table (8 sets in 5 cells + extrapolated future passers). The mix is applied on the dispatchers (the lead measures it).
