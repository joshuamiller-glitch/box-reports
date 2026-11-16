# USER ORDER 2026-11-16 (verbatim): PRIORITY ORDER until 22:00Z today. Deadline work for a build that installs before the 23:00Z Globex open.
P1 (now, due 17:00Z): SPEC_LONDON_RANGE_MP.md exactly as ordered in BUILD PREP item 1. No engine time needed; one agent, start immediately.
P2 (all exact workers, due 20:00Z): BUILD PREP item 2, the five bracket cells on JN05W2JL2. Order inside P2: L3M, L6M, HOLD first for all five cells and their controls; then GAP, PRE, X'. Post a table to DS3_BRACKET_BUILD.md after each window completes, drawdown first, with a plain line per cell: passes / fails / not finished.
P3 (due 20:00Z, no engine time): BUILD PREP item 3, the exact policy lines, plus the session names the engine used and whether a session line overrides the existing "bracket K7 * target=59" line or stacks.
P4 (after P2 lands): BUILD PREP item 4, DS3_DD_HOLD.md.
P5: read ~/internals/LOG.txt with the STATEDIAG parser.
EVERYTHING ELSE: quota 0 until P2 is complete (CF, FL, LR extras, CH, RA, PA, AL, EV re-runs, D9, EA/EB/EC, LA/LB). Running workers may finish; no new admits. Keep load1 near 40. Restore the previous quota table when P2 is done, with FL and CF first.
At 17:00Z and 20:00Z write a lead note: what is done, what is late, and the finish time for anything late.
