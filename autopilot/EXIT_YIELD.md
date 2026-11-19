# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-19 02:39Z

STATUS: 189 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 10%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 5,545 | 11 | 28 | 39 | 28 | 11 | 5.5 | 13.0 | 13.0 | 0.50 | 0.46 | 0.46 | 6 |
| London | 7,487 | 9 | 13 | 22 | 13 | 9 | 6.0 | 8.0 | 8.0 | 0.67 | 0.62 | 0.62 | 5 |
| NYAM | 9,116 | 31 | 81 | 110 | 79 | 29 | 7.0 | 26.0 | 25.5 | 0.23 | 0.32 | 0.32 | 25 |
| NYPM | 9,132 | 1 | 14 | 15 | 14 | 1 | 4.5 | 5.5 | 5.5 | 4.50 | 0.39 | 0.39 | 6 |
| ALL | 31,280 | 52 | 136 | 186 | 134 | | 23.0 | 52.5 | 52.0 | 0.44 | 0.39 | 0.39 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 52 | 52 | 14.0 | +38.0 | 26 | 13.0 |
| order flow | 1 | 1 | 1.5 | -0.5 | 1 | 1.5 |
| staged | 29 | 28 | 8.5 | +19.5 | 14 | 6.0 |
| stop-and-reverse | 9 | 8 | 4.5 | +3.5 | 6 | 4.0 |
| structure stop | 7 | 7 | 1.0 | +6.0 | 1 | 0.5 |
| time / behaviour | 48 | 46 | 11.5 | +34.5 | 15 | 9.0 |
| trailing | 59 | 58 | 17.0 | +41.0 | 31 | 14.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | latch=(0.85, 3.0, 20.0)|stop=('vol', 1.5)|target=('R', 2.0) | 20 | 20 | 1.0 | +19.0 |
| 2 | stop=('vol', 1.5)|trail=('chand', 3.0) | 15 | 15 | 1.0 | +14.0 |
| 3 | stop=('vol', 1.5)|target=('R', 2.0) | 15 | 15 | 1.0 | +14.0 |
| 4 | stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0) | 14 | 13 | 2.0 | +11.0 |
| 5 | latch=(0.95, 0.0, 30.0)|stop=('vol', 1.5)|target=('R', 2.0) | 12 | 12 | 1.0 | +11.0 |
| 6 | stop=('swing', 8)|target=('R', 2.0) | 11 | 11 | 1.0 | +10.0 |
| 7 | minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27) | 12 | 12 | 2.5 | +9.5 |
| 8 | stop=('swing', 4)|target=('R', 2.0) | 10 | 10 | 2.0 | +8.0 |
| 9 | stop=('swing', 8)|trail=('chand', 3.0) | 11 | 10 | 3.0 | +7.0 |
| 10 | noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0) | 9 | 9 | 2.0 | +7.0 |
| 11 | be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0) | 9 | 9 | 2.5 | +6.5 |
| 12 | stop=('vol', 2.5)|trail=('chand', 3.0) | 9 | 9 | 2.5 | +6.5 |
| 13 | stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0) | 8 | 7 | 1.0 | +6.0 |
| 14 | stop=('vol', 2.5)|trail=('bricks', 3) | 7 | 7 | 1.0 | +6.0 |
| 15 | opp_exit=True|stop=('vol', 1.5) | 7 | 7 | 1.0 | +6.0 |
| 16 | stop=('swing', 4)|trail=('chand', 3.0) | 10 | 9 | 3.5 | +5.5 |
| 17 | stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0) | 9 | 8 | 2.5 | +5.5 |
| 18 | stop=('vol', 2.5)|target=('R', 2.0) | 9 | 9 | 4.0 | +5.0 |
| 19 | stop=('vol', 2.5)|trail=('chand', 2.0) | 8 | 8 | 3.5 | +4.5 |
| 20 | stop=('vol', 2.5)|trail=('bricks', 1) | 4 | 4 | 0.0 | +4.0 |

Recipes with NEW real minus null <= 0 in this sample: 25 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('line', 2); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('line', 2); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0); stop=('vol', 2.5)|trail=('swing', 1); stop=('vol', 2.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('line', 2); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('line', 2); maxhold=900.0|stop=('vol', 1.5)|target=('R', 2.0); flow=1|stop=('vol', 1.5)|trail=('chand', 3.0); flow=2|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 3,138 |
| fixed brackets (7), real entries: s per pair / per param | 63 / 3.8 |
| ALL 68 exit recipes, real entries: s per pair / per param | 1472 / 88.7 |
| the same on 2 null draws: s per pair (brackets + exits) | 2711 |

CAUTION on the cost numbers: they are wall seconds of one worker at nice 8-15 on hosts running at load 175-300 on 128 threads (about 2x oversubscribed), so they overstate the true CPU cost by up to ~2x; the per-recipe sweep (single-spec calls, 158 core-s per param for all 68) is NOT comparable with the batch run (68 recipes in one call, 81 core-s per param): use the batch figure for full-run cost and the sweep only for the share of the best recipes.

| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 16,810 / 175 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 30,949 / 322 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 16,810 / 64 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 30,949 / 118 h |

Per-recipe cost (measured separately on 2 pair(s)): all 68 = 158.5 core-s per param; best 20 recipes by NEW-over-null = 73.9 (47%); best 10 = 35.9 (23%). Full-grid core-hours scale by the same fractions.

RECOMMENDATION: FULL RUN of all 68 recipes: new passers are 2.6x rarer in the null (null/real NEW = 0.39) and 6 of 7 families contribute.

### core-hours of a FULL exit run (coarse params, all pairs of the grid, real entries only; the null would add 2x the brackets+exits null cost)

| scope | share of simulated trades | core-hours, all 68 recipes | core-hours, best 20 recipes | hours on the pool (262 core-eq) |
|---|---|---|---|---|
| NY AM + Asia only | 55% | 9,269 | 4,323 | 35 |
| all four sessions | 100% | 16,810 | 7,841 | 64 |
(session shares: Asia 11%, London 15%, NY AM 44%, NY PM 30% of simulated trades; the sessions are post-hoc axes of one simulation, so a session-only run saves only the signals outside those sessions.)
