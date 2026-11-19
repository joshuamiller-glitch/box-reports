# D8_EXIT_SCREEN - 68 exit recipes on the D8 candidates (W-D8EXIT, orders 0213Z / 0220Z / 0224Z), refreshed 2026-11-19 02:27Z
Research only. Screen = points per lot (base lots), 68 recipes (7 families) on the candidate cell's OWN entries, run on real entries and on 2 random-entry draws (same count / side mix). Pick rule (PREREG_D8EXIT.md sha in DECISIONS.md): eligible = L6M>0, L3M>0, trades L6M>=20, no prior year (2023-25) >30% worse; best = lowest ulcer then highest L6M. A cell BEATS-NULL when its best eligible recipe L6M exceeds the best eligible recipe of BOTH null draws (2 draws = screen only; finalists get more draws). Data week index 189 (as EXIT_YIELD). Fixed reference = best fixed bracket of the cell from pass-1 (p1real).
Engine support per family and build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md. Until a family is built, a recipe of that family cannot be the best TESTED exit in the D8 spec (screen result stands).

## a. progress per session (order: Asia, NY AM, London, NY PM)

| session | candidate cells | screened | pending | with an eligible exit (real) | BEATS-NULL | beat fixed ref too | ETA |
|---|---|---|---|---|---|---|---|
| Asia | 0 | 0 | 0 | 0 | 0 | 0 | done |
| NY AM | 3557 | 5 | 3552 | 1 | 1 | 1 | about 296.0 h after the sessions above (fleet 12 cells/h) |
| London | 0 | 0 | 0 | 0 | 0 | 0 | done |
| NY PM | 391 | 0 | 391 | 0 | 0 | 0 | about 328.6 h after the sessions above (fleet 12 cells/h) |

Asia and London candidates appear here when W-LONENG's engine rows land in D8_CANDIDATES (0 now = none listed yet, not "none exist").

## b. candidates with an eligible exit that beats both null draws (best first by ulcer)

| session | live book | cell id | cell | fixed ref (bracket L6M / ulcer) | best exit (family) | L6M | L3M | ulcer | persist | y23 / y24 / y25 / y26 | win / avg win / avg loss / hold min | trades L6M | null best eligible L6M (a / b) | top 2-3 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NY AM | K7 | L41bfa428 | NYAM/drb_2000/trig_book_ofi/follow_sm/{"L": 100, "z": 1.5, "sm": 3}/sym15u/both | n/a on this host | stop=('vol', 2.5) target=('R', 2.0) (market target) | +1282 | +937 | 675 | 0.60 | +1816 / +4433 / +4465 / +239 | 43% / +124.3 / -84.5 / 45 | 264 | - / - |  |

## c. what the screen has found per exit family (best eligible exit of each screened cell, real vs null)

| family | cells where it is the best eligible exit (real) | same on null (mean of 2 draws) |
|---|---|---|
| market target | 1 | 0.5 |

Screened cells with an eligible exit: real 1 of 5 (20%), null 0.5 of 5 (10%). Null/real ratio is the false-positive reading for "best of 68": a cell that clears its own nulls and sits in a session where this ratio is low is the one to take to the engine.

## d. machines, workers, measured speed

| machine | D8-exit-screen workers (nice 7) | rows owned (crc32(row)%12) | note |
|---|---|---|---|
| A Frankfurt | 24 | 2-6 | started 02:24Z beside 36+24 grid workers and 24 EXIT_YIELD workers (nice 15) |
| B Singapore | 24 | 7-11 | same |
| server 2 Dallas | 8 | 0-1 | same |
| box 1 | 0 | - | memory guard (MemAvail > 40 GB) |


Measured: 2 groups finished, 2 cells, mean 117 s per cell (3 tags: real + 2 null) per worker.

## e. BROAD exit run (order 0224Z) - status at 02:30Z (measured, not yet re-ordered)
What runs today: EXIT_YIELD workers (ey_job.py, 24 per A / B, nice 15) already walk the whole ordered pair list (36,026 pairs A+B, any prefix a stratified sample) - 68 recipes on the COARSE params + 7 brackets, real + 2 null draws. That IS the broad run's coarse stage; it was capped at a 5% target by reporting, not by the code.
Measured cost (205 finished pairs): mean 3,792 core-s per pair (median 3,157, p90 7,319) = 37,950 core-hours for all 36,026 A+B pairs, ~+7,600 core-hours for the Dallas row groups 0-1 (about 45,500 core-hours in all, coarse params only).
ETA at today's allocation (24 workers per A / B, ~34 pairs/h in the last hour): about 1,060 h. With all 256 threads of A + B on it: ~150 h (6.2 days); with all four machines: ~110 h (4.6 days). It sits below the D8 path, real pass 1, R3 / pass 2 and null 1-2 (ladder g), so it WILL starve for more than 12 h: LEAD NOTE required (Josh decides on machines / waiting).
NOT built yet (needed before the broad numbers are final): (1) session ordering - pairs cannot be split by session (one simulation serves all four), so the list must be re-ordered by Asia / NY AM screen value (best pass-1 L6M of the pair in those sessions); needs a new claims namespace and a worker restart (not done: it would reset W-EXITYIELD chunk claims); (2) fine params on cells alive on any recipe; (3) own-stop version of the exits (per-trade records in the path simulator, EXIT_YIELD NOT-DONE item 1); (4) faster simulator: per-spec cost ~0.25-0.5 s per param per spec, 68 specs x (real + 2 null); candidates: reuse of the entry/context build across the 3 tags (context is rebuilt per tag now), RAM-cached stores, compiled path loop - each needs an identity test (trade for trade vs the current simulator) before any number is used.

