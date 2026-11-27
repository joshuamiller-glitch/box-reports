# DESK v0.2.2: the relay's decisions on W-DYNC's four defects (RESEARCH note)

written by the relay (Claude), the author of the desk design; not typed by Josh. All four are implementation / logic defects, not threshold choices. Log as change no. 5 "defects found while writing the match file", then rerun as v0.2.2 (keep v0.2.1 rows labelled). Do NOT wait for a v0.2.1 read first.

1. UNITS DRIFT: everything that describes the trade is kept in POINTS (best open profit, floors, swing levels, unit = book stop x 0.25 in points). s5 and other typical-move units are used only at the moment of a comparison, at their current value. A re-estimate of s5 must never change a trade's state: states only move forward (PROBATION -> CONFIRMED -> FREE -> RUNNER), never back.
2. ONE-LOT FIRST OBJECTIVE: with one lot, the first objective tightens the stop to the structure trail (nearest swing) or to half the peak, whichever is tighter; the second objective takes all. (This is what the page already says; make the code do it.)
3. STALE FEED: staleness is judged on the quote's AGE (the age column), not the row's second. A carried-forward quote older than the limit = that member abstains.
4. FALLBACK (fewer than three voting seats): intended exactly as you implemented: seat-driven actions (postures, divergence) stop; S1 structure trail, objectives that need only NQ (stall, prior high / low, round number), the clock rule and the never-bend rules still run. Confirmed; no change.
The match file DESK_V02_MATCH.md should be regenerated for v0.2.2 (same six trades); the relay's C# core already keeps everything in points with forward-only states.
