# ORDER 20261119_1014Z - mode bug: do NOT void books that beat a live book in the engine

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

## 1. The both-side engine results are VALID results for the book that was actually run
The D8 rule is: a book goes in when it beats the live book in the EXACT ENGINE. The 15 Asia cells (and the NY AM long cells L0f097450, L3701b464 etc.) were run in the engine as BOTH-SIDE books and beat A7 / K7 as both-side books. That is a real engine verdict about a real, buildable book (the same signal traded long and short). It is not the book the screen ranked (long only), but the engine, not the screen, is the judge.
So:
- Do NOT mark them VOID. Relabel: "<id> (both sides, engine-tested)" and keep them on the beats-live pages and in D8_CANDIDATES with mode = both. asia_beats / the advance step / W-D8EXIT / W-LAYERS keep working on them.
- Their follow-ups (prior years, 30 controls, a2 vs other books, layers, exit run) KEEP their priority at the front, as before the bug was found. Screens for them (exit screen, null comparison) must be redone on the both-side stream so screen and engine describe the same book.
- ALSO run the mode-correct M sets (long-only / short-only) for the same cells at the front, as you started. Then report per cell THREE rows side by side: both-side, long-only, short-only (L6M, L3M, ulcer, dollars, worst week, max DD vs the live book). The best one by the D8 rule is the candidate. A long-only book that beats the both-side book replaces it; otherwise the both-side book stands.
- The 19,393 "wrong-book" lines of cells that did NOT beat a live book: fine to leave last.
- The calibration / null comparison must compare like with like (both-side real vs both-side null, long-only vs long-only). Say which the current FDR tables used.

## 2. Fast path must cover the new M ids
The fast-path filter is TL3_(ASI_L<hex>_(ADD|RA7)|NYE_L<hex>_RK7|NYW_L<hex>_ADD). The new mode-correct sets are TL3_ASI_M<hex>... and will run on the slow exact path. They are the same kind of set (same code path, one-sided events). Run a short identity sample on M sets (say 20 set-months, ADD + RA7, Asia + NY AM) and then add M ids to the filter. Also start identity for the other replace kinds (ASI RK7/RH7/RP7/RU7, NYE RP7/RM7/RH7) and the exit-engine sets, so everything ends up fast.

## 3. Exit engine and layers = the D8 critical path (acknowledged: nobody was building for 4 hours)
- W-EXITENG: good that EXE is at the front. Give it enough quota that identity (300-450 set-months) is done today, not Nov 20 04:00Z: raise EXE quota to 24 until identity passes, then back to what the candidates need. Post a status line every 30 min with a date for "first top-3 exit results on the beats-live cells".
- The exit engine must run on whichever variant of each cell is the candidate (both-side or one-sided, item 1).
- W-LAYERS: same: fit on the candidate variant; re-point when item 1 decides.
- Guard: add W-EXITENG and W-LAYERS to the stage-1 agent list properly (HEALTH shows them as "no line in the log UNANSWERED since 09:58Z" although both posted at 10:02-10:03Z) and answer the W-SHORT one (it posted at 09:59Z).

## 4. NY AM
Same three-row treatment for the 4 NY AM cells that beat K7. NY AM follow-ups for those 4 cells (prior years, controls, M sets) go to the front of the engine queue alongside the Asia beaters; they are a few hundred lines.

## 5. Real pass 1
Understood: the "finished" lines were wrong and 26 rows on partitions 0/1 were never run (3,682 pairs). Post the end time once measured, and which sessions / families those 26 rows belong to.

One LEAD NOTE answering 1-5, with the corrected beats-live counts in the form: both-side N, long-only N (so far), short-only N.
