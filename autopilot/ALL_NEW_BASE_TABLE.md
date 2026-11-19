# WHICH BASE DOES EACH PROGRAMME RUN ON? (W-NYENG, 2026-11-19 23:0xZ, order 2300Z item 2)
Principle (Josh): every number used for a DECISION is taken on the ALL-NEW base (the book alone: all four live NY AM books K7/P7/M7/H7 off, account layers ON, all other sessions' books keep trading as the account); the RANKING screen keeps the current vehicle (REPLACE-K7 / REPLACE-A7). Measured: ADD vs REPLACE-K7 changes the book's own MF1 trade list in 64% of 120 cell-months (mean |net| difference $1,667/month vs ~$5.4k book result), so the live-book base moves a book ~30%.
Cost of the all-new base (set TL3_NYE_<id>_ALN, 4 live books off): 6 test set-months on server C: 225-298 s (mean 270 s) vs 195 s mean for REPLACE-K7 first looks on all hosts (host-confounded): same order, NO new engine cost class; trades per month ~ the same. In 3 of the 6 test months the MF1 trade list is IDENTICAL to REPLACE-K7's, in the other 3 it differs (e.g. L01811caa 202608: 54 vs 52 trades, net 1,441 vs 659).
| programme | base now | lines queued (23:00Z) | decision | cost of moving | share already spent (DONE) |
|---|---|---|---|---|---|
| NY AM first looks (REPLACE-K7) + the one-side re-runs | live stack minus K7 | 18,867 | KEEP (ranking screen) | - | 15.7k set-months |
| B-id both-side first looks | live minus K7 | 7,050 | KEEP (ranking screen) | - | just started (88+ of 1,469 books built) |
| Asia / London first looks | live minus A7 / M7 | 1,807 Asia (+ London flag) | KEEP | - | - |
| ranked prior years (RK7 sets, months outside 202605-202610) | live minus K7 | 28,395 queued at 22:55Z | **MOVED at 23:0xZ**: those lines PARKED (parked_rk7py_2300.txt, rollback ny_aln_convert.py --rollback), the same 771 cells' L6M + prior years queued on the ALL-NEW base TL3_NYE_<id>_ALN = 33,153 set-months (+6 L6M months per cell, +17%); ranked_follow()/refill now queue ALN sets for new cells (flag _nye/use_aln) | builder done (ny_alone.py, 771 set JSONs, minutes); +17% set-months; engine seconds per set-month ~ +0 to +40% (not separable from host mix); FAST path: NOT eligible until identity pairs (3 identical vs full engine) exist | 901 RK7 prior-year set-months done (all kept, not used for decisions) |
| 30 date-shift controls (RK7CT sets) | live minus K7 | 47,705 | KEEP for ranking-level evidence: real RK7 vs shifted RK7 copies are compared LIKE WITH LIKE on the same base, the base moves both, so the pass/fail of 'beats its own controls' is not distorted; for cells that become all-new STACK candidates the controls are re-run on the ALN base (180 set-months per survivor, function ensure_aln_controls) | 0 now; 180 per survivor later | 5,717 done |
| exit own-merit batches (TL3_EXE_*_RK7/_RA7 _OM, W-EXITENG) | live minus K7/A7 | 83 (+ more released later) | STOP STARTING new ones on the live base once W-EXITENG's generator can add the 4-book-off hooks (ALN construction); the 83 queued are small | one builder change (the swb_inject2 off-list), small; FAST path kind (^TL3_EXE_L.._bricks3_v25_RK7_OM$) is tied to the RK7 base and needs new identity pairs for ALN | 761 set-months done (kept) |
| pass-2 hook runs (W-P2B sets) | not mine: base unknown to me | ? | W-P2B to answer (I did not read their sets) | - | - |
| layer programmes (W-LAYERS; most parked) | REPLACE-K7 set JSON as the base | 12 (rest parked) | KEEP PARKED; rebuild on the ALN base (W-LAYERS' builder reads the base set: switch to TL3_NYE_<id>_ALN) | builder parameter | 17,143 set-months done on the old base (kept, not used for decisions) |
| STK / all-new stack sets (W-COMBO, combo_build3) | empty session (book(s) alone) by design | 1 queued | KEEP: this IS the all-new base | - | 1,635 done |
| the all-new base for the RANKED cells' first looks (decision numbers) | n/a | included in the 33,153 | the ALN L6M months of each ranked cell run with the prior years | see above | - |

## Design of the all-new-base set generator (with W-COMBO)
- Construction (code/th_nyeng/ny_alone.py): JL3 hooklist + mf_inject (the book's own events file, tag MF1, 1 base lot) + swb_inject2 in swap mode with an EMPTY event file for each of K7, P7, M7, H7 in session 3 (NY AM signals of all four live books suppressed; everything else - Asia/London/NY PM books, DAY-DONE, stack rule, caps, locks - unchanged). This is the 'empty session' base of combo_build3 for a single book; W-COMBO's multi-book stack uses mf_multi (one tag per book).
- Naming: TL3_NYE_<id>_ALN (L6M + prior years), TL3_NYE_<id>_ALNCT<k><p|m> controls, B ids the same (TL3_NYE_B<hex>_ALN); tests used TL3_NYE_<id>_ALONE (same construction).
- Cost per set-month: 225-298 s measured (mean 270 s), i.e. the same class as 195 s; the whole month's tape is replayed whatever trades.
- FAST path: only for kinds with identity pairs (W-FASTLADDER); ALN has none yet: 3 identical pairs (ALN vs the full engine on a cell-month where the tape-level result is known) are needed; until then ALN runs on the full engine.
- The builder was ready within ~20 minutes (generator + conversion script); the fleet stays full meanwhile: first looks (NY AM re-runs, B books, Asia remaining), London flag, ranked controls.

## UPDATE 23:3xZ (lead order 2310Z): W-GRIDOPS numbers vs mine
Their 34.5k prior-year lines on the live-book base were BEFORE my move: at 23:0xZ 28,395 RK7 prior-year lines were parked and 33,153 ALN lines (L6M + prior years, all-new base) queued; the move cost ~4 h of fleet time is what those ALN lines are (they are the same months, base changed). Controls 47.8k: keep. Exits ~100: hold new starts (the 83-112 queued ones are tiny). First looks stay.
## D4: ny_refill.py ACTED ONCE FOR REAL (--target=17 --london, new flags added, backup .bak_force_2310)
- Queue before 12.1 h (112,215 lines at 9,294/h) -> 17.6 h (166,413 lines at 9,468/h) after the extension: +69,059 lines in pending_r5.txt (RK7CT controls 37,440, ALN prior-year/L6M 31,433, RK7 210). Multiset check: 0 duplicates, only 8 lines removed from the file by the ladder advance (DONE ones), additions all in the ranked order, new lines of 2023/24/25/26 months 6.6k/8.8k/8.8k/45k. Mix rebuilt: ALN and RK7 lines now first among the follow-ups; first looks/re-runs keep their 70% share (weights unchanged).
- BUG FOUND by the drill: the London step crashed at its report line (literal '15%' in a % format string; never reached before). Fixed ('15%%'). The shards had already started and the flag london_on is written.
- London first looks ON (flag london_on): 6 shards started, memory guard added: 1 shard if MemAvailable <48 GB, 3 if <55 GB or load>90 (code ny_refill.py). 
- Memory: ny_bothside shards 0-5 and London shards were found STOPPED (state T, not by me) by the memory guard at ~48 GB; my SIGTERMs to bothside 3,4,5 and London 3,4,5 will take effect when they resume (they die; 0-2 continue). ny_bothside.py is now gated (shard 0 only <48 GB, shards 0-2 <55 GB, all above, checked before each cell; unregistered half-built events are rebuilt). B-set builds are at 1,377 of ~1,469 books: nearly done, so no move to C/D is needed (bars/events need box-1 data).

## (c/4) QUEUE FOR THE WHOLE NIGHT (23:4xZ, rate 8,900 sm/h, no decision needed)
Unstarted/unfinished/unleased lines in all QUEUES.txt files: 186,106 = 20.9 h -> covers to ~20:20Z Nov 20 (need >= 16:00Z = ~17 h = 150k).
| source | lines | hours | automatic? |
|---|---|---|---|
| date-shift controls (RK7CT) | 81,873 | 9.2 | queued (refill added 37k) |
| ALN prior years + L6M (all-new base) | 64,562 | 7.3 | queued (refill added 31k) |
| B-id / one-side first looks, re-runs, RK7 | 29,373 | 3.3 | queued; B builds 1,377/1,469 done, rest auto |
| Asia first/ranked (RA7 L/M, AX) | ~3,600 | 0.4 | queued |
| all-new NY/AS base (W-COMBO allnew_pending) | 5,040 | 0.6 | queued |
| London first looks (london_on, 3 shards) | 78 now, 808 cells coming | ~0.1 now, ~2-3 h when built | automatic, memory-gated |
| exit batches (W-EXITENG) | ~100 | 0 | by cron, small |
| pass-2 joint runs | 0 | - | MISSING until hooks cleared (W-P2B) |
Missing: nothing for the queue to 16:00Z (+4.3 h margin). Fixes automatic: ny_refill (cron */10) adds ranked follow-ups below 12 h (now cron-safe: crash fixed). Risk: the memory guard stops builders (London shards); controls/ALN are enough to keep slots full without them. Follow-up share cut to 10% (GRIDOPS) lengthens the follow-up tail, not the first-look end (~02:30Z).
