# 1932Z — THOUSANDS OF CELLS PASS THE BARE RULE: run the tests cheapest-first (no cap, no cell dropped without failing a test)

From: Josh's chat assistant (relay). Research only; no spend.

FACT (SURVIVOR_COUNTS.md 19:08Z, bare, provisional): Asia 2,992 cells / 1,890 families; London 1,035 / 808; NY AM 9,504 / 4,556; NY PM 531 / 396. At 7.8 core-h per cell for 30 date-shift ENGINE controls, NY AM family-best members alone are ~35,000 core-h. Josh's rule stands: no top-N cap. The answer is ORDER OF TESTS BY COST: every passing cell meets every test; a cell leaves only by FAILING one; the expensive engine work is spent on cells that have already survived the cheap ones.

LADDER (per session; publish the count entering and leaving every rung on SURVIVOR_COUNTS.md):
R0  bare rule (done).
R1  OWN-STOP rule (the ranking that carries the shortlist, addendum 1731Z): same thresholds applied to the own-stop result (2 stops; 1.5 / 3 shown). Costs nothing extra once phase 1 results carry it. Cells that pass bare but fail own-stop are kept and labelled "depends on today's stack" (they can still be tested later as add-to-today's-stack, after the own-stop passers).
R2  Trust audit + look-ahead gate (0.001-0.005 core-h per cell): every R1 cell.
R3  Same-bracket random entries, 30 draws, screen level (0.24-0.39 core-h per cell): every R2 family (best member first, then the neighbours). PASS = beats at least 27 of 30 (state the threshold used and show the count at 24 / 27 / 29 so Josh can see how sensitive it is). Today's example: XA3 beats 25/30, WP10 15/30.
R4  Selection-corrected null of the whole search (20 full null draws, ~6,300 core-h, shared by all four sessions): START IT NOW in the background at a fixed share of the grid fleet (about 25% of A + B) so it is finished when phase 1 is; it must run with the same own-stop flags as the real search. Report: how many cells per session pass R0-R3 in each null draw versus in the real search (that ratio is the false-discovery rate) and the best-pick comparison.
R5  ENGINE, staged: last 6 + 3 months as ADD and as replacement for the weakest live book of the session (about 0.3 core-h per set-month): every R3 family-best, in rank order; rows that are not negative go on to prior years; then 30 date-shift controls (7.8 core-h) for rows still alive; then the layer programme (phase 3) in clock order.
At every rung state: cells / families in, out, core-hours spent, core-hours the next rung needs, and hours on the current fleet. If a rung still needs more than ~48 h of the fleet, say so with the number: Josh decides between more machines and waiting. Do NOT trim to fit.

ALSO:
1. WP10 (NY PM money flow): per PHASE2_TOOLING_TEST.md it is NOT distinguishable from random entries on its own wide bracket (15/30) and its best date-shift control came within $135 of it; own-stop weak. Relabel it honestly on the pages (lead for "add to today's stack" at most; not a rebuilt-stack candidate) and do not spend more engine on it ahead of R3 passers.
2. XA3 (NY AM VWAP retest, 5000-tick): beats 25/30 random and 30/30 date-shift (+$54,428 vs best control +$24,259): keep it at the front; report its own-stop result, prior years and the K7 / P7 / M7 swaps.
3. Grid / engine split on A and B: the engine was starved on A (1,072 s per month vs ~160 s on Dallas). Set an explicit split per phase and state it: while phase 1 runs, grid gets most cores but the lead / R5 engine sets get a guaranteed share (say 24-32 engine workers on A at normal priority); measure set-months/h on A and put it in ENGINE_PLAN.md.
4. The admission-lock finding (219 stale waiters throttling box-1 engine admissions for days): add a check to the watchdog (waiters on the lock > 150, or any waiter older than 6 h = wake the lead) so it cannot recur.
