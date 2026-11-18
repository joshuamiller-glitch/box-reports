# 2042Z — LUCK TESTING: spend the budget on per-cell p-values with FDR control; cut the whole-search null to 5 draws; give the search its cores back

From: Josh's chat assistant (relay). Research only; no spend. This changes HOW the luck test is done, not whether: the standard gets stricter, the cost gets smaller. Josh can overrule.

WHY:
(a) 20 full null draws = 1.2 M jobs = 11 days at the 50% split, and the 50% split has pushed real pass 2 + exits from ~28 h to ~49 h. The null is starving the search it is meant to check.
(b) R3 as ordered (beat >= 27 of 30) is too weak on its own: a pure-noise cell passes it about 13% of the time (4 of 31 ranks), 24 of 30 about 23%, 29 of 30 about 6%. First Asia numbers (97 family-bests): 32% at 24, 9% at 27, 0% at 29 = at or below what noise gives at 27 and 29. With thousands of families a 13% noise pass rate lets hundreds of lucky cells through to the engine.

DO:
1. WHOLE-SEARCH NULL: target 5 complete draws, not 20 (draws 1-2 inside the real loops plus 3-5). Put the null loops back to about 25% of A and B; restore the real pass-1 / pass-2 / exit loops to the rest so phase 1 finishes on its earlier ~18-28 h. The 5 draws are a CALIBRATION CHECK of item 2 (do null cells pushed through the same ladder come out at the false-discovery rate the ladder claims?), plus the best-pick comparison. Publish both ETAs after the change.
2. R3 BECOMES A PER-CELL P-VALUE WITH FALSE-DISCOVERY CONTROL (adaptive, cheap):
   - stage A: 30 same-bracket random draws for every family-best (as now).
   - stage B: every cell that beats >= 24 of 30 gets 200 draws.
   - stage C: every cell with p <= 0.02 after 200 gets 1,000 draws (cost about 15-47 CPU-s per 30 draws, so about 10-25 CPU-min per cell).
   - p = (1 + number of random draws that do at least as well as the real cell) / (1 + draws), on the last-6-month equal-risk result AND separately on the weakest prior year (report both; the pass uses the L6M p-value, the prior-year p is shown).
   - Per session apply Benjamini-Hochberg across ALL family-bests of that session at q = 10% (also show the count at q = 5% and 20%). PASS R3 = inside the BH set. Say how many pass per session and the expected number of false ones (q x passes).
   - Neighbours in a family are tested after their best member, same procedure; a family whose best member passes but whose neighbours all fail is flagged "isolated".
3. Because BH needs small p-values, the minimum draws for a pass is large: say on the page the smallest p reachable at each stage and that a cell cannot pass on 30 draws alone.
4. Keep everything else: own-stop rule (R1), trust + look-ahead (R2), engine with 30 date-shift controls and prior years (R5), layers, clock order. Nothing is capped; cells leave only by failing.
5. Update SURVIVOR_COUNTS.md, ENGINE_PLAN.md and SEARCH_STATUS.md: the new R3 / R4 definitions, counts in and out per stage per session, core-hours, and the dated estimates again (phase 1 end, R3 end per session, engine hours for the BH passers at q = 10%, D8 spec date).
6. XA3 through the same stage B / C now (it beat 25 of 30): report its p at 200 and 1,000 draws.
