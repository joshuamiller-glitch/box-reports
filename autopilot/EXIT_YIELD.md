# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-19 00:32Z

STATUS: 117 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 6%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 3,056 | 5 | 15 | 20 | 15 | 5 | 1.0 | 6.0 | 6.0 | 0.20 | 0.40 | 0.40 | 2 |
| London | 4,349 | 4 | 8 | 12 | 8 | 4 | 4.0 | 5.0 | 5.0 | 1.00 | 0.62 | 0.62 | 1 |
| NYAM | 5,463 | 21 | 64 | 84 | 63 | 20 | 5.0 | 19.5 | 19.5 | 0.24 | 0.30 | 0.31 | 14 |
| NYPM | 5,450 | 1 | 14 | 15 | 14 | 1 | 2.5 | 3.5 | 3.5 | 2.50 | 0.25 | 0.25 | 4 |
| ALL | 18,318 | 31 | 101 | 131 | 100 | | 12.5 | 34.0 | 34.0 | 0.40 | 0.34 | 0.34 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 43 | 43 | 8.5 | +34.5 | 17 | 8.0 |
| order flow | 0 | 0 | 1.0 | -1.0 | 0 | 1.0 |
| staged | 22 | 22 | 3.0 | +19.0 | 8 | 2.0 |
| stop-and-reverse | 7 | 7 | 4.0 | +3.0 | 5 | 3.5 |
| structure stop | 6 | 6 | 1.0 | +5.0 | 0 | 0.5 |
| time / behaviour | 45 | 44 | 8.5 | +35.5 | 13 | 6.5 |
| trailing | 44 | 44 | 11.5 | +32.5 | 17 | 10.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | latch=(0.85, 3.0, 20.0)|stop=('vol', 1.5)|target=('R', 2.0) | 19 | 19 | 1.0 | +18.0 |
| 2 | stop=('vol', 1.5)|target=('R', 2.0) | 15 | 15 | 0.5 | +14.5 |
| 3 | stop=('vol', 1.5)|trail=('chand', 3.0) | 14 | 14 | 1.0 | +13.0 |
| 4 | latch=(0.95, 0.0, 30.0)|stop=('vol', 1.5)|target=('R', 2.0) | 12 | 12 | 0.5 | +11.5 |
| 5 | minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27) | 12 | 12 | 1.5 | +10.5 |
| 6 | stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0) | 11 | 11 | 1.0 | +10.0 |
| 7 | be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0) | 9 | 9 | 1.5 | +7.5 |
| 8 | noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0) | 9 | 9 | 1.5 | +7.5 |
| 9 | stop=('swing', 8)|trail=('chand', 3.0) | 8 | 8 | 1.5 | +6.5 |
| 10 | stop=('swing', 8)|target=('R', 2.0) | 7 | 7 | 0.5 | +6.5 |
| 11 | stop=('vol', 2.5)|trail=('chand', 3.0) | 7 | 7 | 1.0 | +6.0 |
| 12 | stop=('swing', 4)|target=('R', 2.0) | 7 | 7 | 1.5 | +5.5 |
| 13 | stop=('swing', 4)|trail=('chand', 3.0) | 7 | 7 | 1.5 | +5.5 |
| 14 | stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0) | 5 | 5 | 0.0 | +5.0 |
| 15 | stop=('vol', 2.5)|trail=('chand', 2.0) | 7 | 7 | 2.0 | +5.0 |
| 16 | opp_exit=True|stop=('vol', 1.5) | 6 | 6 | 1.0 | +5.0 |
| 17 | stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0) | 5 | 5 | 1.0 | +4.0 |
| 18 | stop=('vol', 2.5)|target=('R', 2.0) | 7 | 7 | 3.0 | +4.0 |
| 19 | minrr=1.5|stop=('vol', 2.5)|target=('mm', 1.27) | 6 | 6 | 2.0 | +4.0 |
| 20 | stage=([1.0, 2.0], [0.34, 0.33], True)|stop=('vol', 1.5)|target=('R', 2.0) | 4 | 4 | 0.5 | +3.5 |

Recipes with NEW real minus null <= 0 in this sample: 24 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('line', 2); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('line', 2); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); minrr=2.0|stop=('vol', 2.5)|target=('opp',); stop=('vol', 2.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('line', 2); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('line', 2); stop=('vol', 2.5)|trail=('bricks', 1); flow=1|stop=('vol', 1.5)|trail=('chand', 3.0); flow=2|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 1,887 |
| fixed brackets (7), real entries: s per pair / per param | 28 / 1.8 |
| ALL 68 exit recipes, real entries: s per pair / per param | 1308 / 81.1 |
| the same on 2 null draws: s per pair (brackets + exits) | 2262 |

CAUTION on the cost numbers: they are wall seconds of one worker at nice 8-15 on hosts running at load 175-300 on 128 threads (about 2x oversubscribed), so they overstate the true CPU cost by up to ~2x; the per-recipe sweep (single-spec calls, 158 core-s per param for all 68) is NOT comparable with the batch run (68 recipes in one call, 81 core-s per param): use the batch figure for full-run cost and the sweep only for the share of the best recipes.

| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 14,939 / 156 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 25,824 / 269 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 14,939 / 57 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 25,824 / 99 h |

Per-recipe cost (measured separately on 2 pair(s)): all 68 = 158.5 core-s per param; best 20 recipes by NEW-over-null = 72.1 (45%); best 10 = 36.4 (23%). Full-grid core-hours scale by the same fractions.

PRELIMINARY (117 pairs < 150): RECOMMENDATION: FULL RUN of all 68 recipes: new passers are 2.9x rarer in the null (null/real NEW = 0.34) and 6 of 7 families contribute.

### core-hours of a FULL exit run (coarse params, all pairs of the grid, real entries only; the null would add 2x the brackets+exits null cost)

| scope | share of simulated trades | core-hours, all 68 recipes | core-hours, best 20 recipes | hours on the pool (262 core-eq) |
|---|---|---|---|---|
| NY AM + Asia only | 54% | 8,077 | 3,673 | 31 |
| all four sessions | 100% | 14,939 | 6,793 | 57 |
(session shares: Asia 11%, London 15%, NY AM 43%, NY PM 31% of simulated trades; the sessions are post-hoc axes of one simulation, so a session-only run saves only the signals outside those sessions.)
