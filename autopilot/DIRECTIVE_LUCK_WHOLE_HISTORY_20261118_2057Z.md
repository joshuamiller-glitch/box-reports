# ORDER 20261118_2057Z: luck test (R3): add a WHOLE-HISTORY p-value column beside the L6M one

Research only. Nothing here touches the execution server, a live chart, credentials, spend or data deletion.
This ADDS a column and widens who advances a stage. It removes nothing and stops nothing.

## Why
Josh asked whether the R3 pass rule is too strict. He has a point: the pass currently uses the p-value on the
last 6 months ALONE. With thousands of family-bests per session, Benjamini-Hochberg at q = 10% needs p near
0.0001-0.002, and 26 weeks of one cell's trades can rarely reach that even when the edge is real (XA3: L6M p 0.092,
weakest prior year p 0.002, 30/30 date-shift). His selection rule is "pick on recent data; prior years not a
disaster". It never said the recent window alone must be statistically significant. Proof of "not luck" can
use all the data; the PICK stays on recent.

## Do this
1. For every family-best, from the SAME random draws (no new null design), compute three p-values,
   p = (1 + k) / (1 + n), equal-risk sum of R:
   (a) p_L6M: last 26 weeks (as now);
   (b) p_ALL: whole history, first available month to today (L6M included);
   (c) p_PRIOR: weakest prior year (as now).
2. Stage advance (A 30 -> B 200 -> C 1,000 -> D 10,000) if EITHER the L6M statistic OR the whole-history
   statistic meets the stage rule. Cells already drawn: recompute (b) from stored draws; re-open cells
   that stopped at stage A on L6M but qualify on whole history. Cells parked from engine stage 3 for
   R3 < 24 on L6M: re-queue if they qualify on whole history (parked, not deleted, so reversible).
3. Report TWO pass sets per session, side by side, on SURVIVOR_COUNTS.md (counts at q = 5 / 10 / 20%):
   SET 1 (strict, current rule): inside BH on p_L6M.
   SET 2 (proposed): inside BH on p_ALL, AND the cell still passes R0 / R1 unchanged (L6M > 0, L3M > 0,
   >= 100 L6M trades, persistence > 0.60, no red prior year). So recent picks, whole history proves.
   For each set: count, expected false (q x count), engine core-hours, D8 spec date estimate.
   Flag cells in SET 2 whose p_L6M > 0.20 as "recent no better than random" (shown, not dropped).
4. Josh decides which set is the pass rule once both counts are on the page. Until then the engine takes
   SET 1 first, then SET 2 members, best p first. No cap on either.
5. XA3: publish p_ALL at 1,000 draws (and stage D if it is at the floor).
6. Log acceptance, the added core-hours, and any change to the dated estimates in MORNING.md.

Everything else in 2042Z stands (5 null draws as the calibration check; the null check is run against
whichever set Josh picks, both if cheap).
