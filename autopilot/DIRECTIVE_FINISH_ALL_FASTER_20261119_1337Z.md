# ORDER 20261119_1337Z - Josh: finish ALL of Asia + NY AM before any build; make it faster

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend (no new machines: only Josh can order those, by pasting to the lead). Delete nothing.

Josh's words (13:33Z): "i want it all done before building or we will be building so many versions - with only 2% we already have 2-3 books - imagine how many more! - also what can we do to get this part done faster?"

## 1. Decision: NO D8 build spec until the Asia AND NY AM ladders are complete
Complete = every ladder cell has its first look, and every cell that beats a live book has prior years, controls, layers, exit run, and the today / REPLACE / ADD pick. No "first wave". The picks posted so far are provisional. D8_SPEC_STATUS: replace the wave dates with ONE date for "stage 1 complete", stated with its rate and its assumptions, plus a breakdown of the remaining set-months by part (Asia first looks, NY AM first looks, follow-ups by type).

## 2. Speed, part A (now, no spend): more engine slots from the machines we have
The engine is the bottleneck; the search (grid) side on Frankfurt / Singapore / Dallas runs ~93 + 93 + ~28 workers of lower-stage work at low priority. Measure and then raise engine caps as far as memory and cores allow (cap_steps, mem_guard stay in force): target Frankfurt and Singapore ~120 engine slots each, Dallas ~56, box 1 as high as its memory allows, with search workers reduced to what stage 1 needs (calibration deeper rungs, level re-run, beats-live exit screen) plus whatever fits strictly below the engine. Report slots before / after and the fleet rate after 30 minutes. London / NY PM search work waits; it is stage 2 / 3.

## 3. Speed, part B (start today, in parallel): compiled inner loop for the engine
The per-print loop is pure Python (on_print ~75% of the time). The fast path gave 2x. A compiled inner loop (Cython / Numba / C extension for the per-print book and fill logic, same code path semantics) is the one lever that can give another large factor. Start a dedicated builder now (W-COMPILED): design note today (what is compiled, what stays Python, expected factor from a profile of one Asia and one NY AM month), then build behind the same opt-in launcher switch as the fast path, with the SAME identity standard (trade for trade to 1e-9 on the 217-case sample plus the newer kinds, 2% exact re-check forever, automatic fallback). Nothing switches until identity passes. Post a status line every hour with the measured factor.

## 4. Speed, part C: balance and waste
a) NY AM is 9,081 cells and gets ~120 set-months/h while Asia gets the rest. Both must finish. Split engine slots so that both ladders end at about the same time (state the split and the two end dates); follow-ups of gate-pass candidates stay first.
b) Duplicate streams: several cells are the same event stream under different ids (e.g. two 240-second cells, two 4-minute cells, two NY AM cells). Detect identical event files by hash BEFORE launching and run each stream once; copy the result to its twins. Report how many set-months this removes from the queue.
c) Any cell already "out" at an early rung must not have later-rung lines still queued. Count and remove from the active queue (move to a parked file, do not delete).

## 5. Ask for Josh (he decides spend): post in one line what ONE more 128-thread server would do to the "stage 1 complete" date, and what two would do, at today's measured per-slot rate. No purchase, no quote request: just the arithmetic.

One LEAD NOTE answering 1-5, with the single "stage 1 complete" date.
