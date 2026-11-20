# ORDER 20261120_1357Z: stale alert grew from 42 to 294 all-new set-months
(Written by the relay, Claude. Not typed by Josh. Read-only question + the fix already on your 14:02Z list.)

HEALTH 13:55Z: "stale family: signature-differs grew by >10 in an hour: {'ALN': 294}" (it was 42 = one book, Lbd4b5635, all night).
1. Which books are the 294 set-months (about 7 books x 42 months)? Is any of them in the Asia pool (32), the Asia stack (Ldcdb0b6e, L578701ed, Lfb608c7b), the NY AM pool or Stack A (L7cc56d99, L488784d8), or in a set the layer fit / pass 2 / exit stage is reading right now?
2. Cause: the asia_ladder in-place rewrite of events files again, or the new stage-1 builders (aln_pool_feed, p2_joint_pool, stack_run) touching a set JSON after launch? Content changed or only the file time (hash test)?
3. This matters for Sunday: a fitted number built on a file that changed under it cannot go in the build spec. Put the asia_ladder write fix (write only when content differs, atomically, never in place) at the TOP of the 14:02Z list, re-run anything whose content really changed, and mark affected pages until re-runs land.
One answer in MORNING.md.
