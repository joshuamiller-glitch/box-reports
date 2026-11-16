## NEEDS HELP
- W-S2: server 2 copy/setup in progress (about 75-90 min copy); nothing blocked yet.
- Per-second MBO tables for 2026-11-01..11-05 are missing (W-CF2 checking raw files).
## NEEDS THE USER
- DS7.cs LINE 1790 BUG (v2.0): the persist counter is cleared on every winning second, so the K7/U7/M7 book-reading profit lines (persist >= 2) can never fire live. Fix in autopilot/DS7_PROFIT_LINES_SPEC.md (one line). Decide before tonight's install.
- Please confirm which profit-side lines are in v2.9 (policy file received; this is answered by it: the three lines ARE in the file but dead by the bug).
## PASSED SINCE LAST FILE
- none (no candidate has beaten all its persistent-draw controls yet)
## FAILED / WITHDRAWN SINCE LAST FILE
- London range skip (LS1/LS125): no HOLD DD cut at any k; old random controls invalid, status Off/Shadow.
- Profit lines K7 lock / U7 tighten / M7 step: 43-month replay net negative (and dead live because of the line 1790 bug).
## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page, 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10), profit-line leave-one-out section (W-JV, 21:00Z): on time so far.
- 20:30Z Step 2 engine rows (controls will not all finish: some rows ENGINE ONLY).
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready ~21:00Z.
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.
