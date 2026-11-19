# ORDER 20261119_0143Z: stale results: check EVERY module family, and stamp results so it cannot recur

Research only. Good catch on the level modules (01:26Z). Two gaps remain.

1. ALL MODULES, not only trig_levels_*: for each of the 145 trigger modules take one result file written
   in each distinct code era of that module (use the module file's change history / mtimes; at least the
   oldest result on disk and one written before 2026-11-18 06:00Z), re-run it fresh, compare arrays.
   Table on SEARCH_STATUS.md: module, oldest result time, last code change time, identical? / differs.
   Do the same once for the shared pieces every module depends on (bar builders per bar row, feature
   stores, the path simulator, the R0 scorer): a change there makes results of ALL modules on that row stale.
   Any module or row that differs gets the same forced re-run as the levels (GL_FORCE_BEFORE per module),
   real cells first, then null draws 1-2, then pass 2.
2. STAMP: every result file (real, null, pass 2, exit-yield, R3 draws) carries a hash of the module code +
   shared code + bar/feature store version it was computed with; the loop treats a hash mismatch as
   "todo"; the rule / R3 / calibration scripts refuse to mix hashes and print the count of excluded files.
   Until the stamp exists, say on SURVIVOR_COUNTS.md and the CALIBRATION section which rows rest on
   unverified (pre-fix) results.
3. KNOCK-ON: say plainly, in one LEAD NOTE, what already-published numbers used stale level results and will
   be redone: R0 survivor counts per session, the R3 stage-A counts, the 01:16Z calibration table (real AND
   null side), the exit-yield sample (were its level-module pairs computed with fixed code?), the screen-rank
   lists feeding the engine (cells already in the engine queue from stale ranks stay queued; new rank after
   the re-run), and the new end times for real pass 1, null draws 1-2 and the first trustworthy calibration.
4. Engine rows are computed from fresh signal code: confirm that with one check (a level cell: engine entry
   list vs fresh grid entry list, same month), so Josh knows the engine results he has seen stand.
