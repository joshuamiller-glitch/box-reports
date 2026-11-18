# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-18 22:03Z

STATUS: 35 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 2%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 435 | 1 | 1 | 2 | 1 | 1 | 0.0 | 0.0 | 0.0 | 0.00 | 0.00 | 0.00 | 0 |
| London | 703 | 0 | 1 | 1 | 1 | 0 | 1.0 | 0.5 | 0.5 | n/a | 0.50 | 0.50 | 0 |
| NYAM | 1,427 | 2 | 7 | 9 | 7 | 2 | 0.5 | 4.5 | 4.5 | 0.25 | 0.64 | 0.64 | 1 |
| NYPM | 1,395 | 0 | 0 | 0 | 0 | 0 | 0.5 | 1.5 | 1.5 | n/a | n/a | n/a | 1 |
| ALL | 3,960 | 3 | 9 | 12 | 9 | | 2.0 | 6.5 | 6.5 | 0.67 | 0.72 | 0.72 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 4 | 4 | 1.5 | +2.5 | 3 | 1.5 |
| order flow | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| staged | 1 | 1 | 0.0 | +1.0 | 1 | 0.0 |
| stop-and-reverse | 1 | 1 | 1.0 | +0.0 | 0 | 0.5 |
| structure stop | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| time / behaviour | 3 | 3 | 1.5 | +1.5 | 1 | 1.0 |
| trailing | 2 | 2 | 3.0 | -1.0 | 2 | 3.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | stop=('swing', 4)|trail=('chand', 3.0) | 1 | 1 | 0.0 | +1.0 |
| 2 | noprog=(4, 0.5)|stop=('inval', 2)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 3 | stop=('inval', 2)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 4 | latch=(0.95, 0.0, 30.0)|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 5 | latch=(0.85, 3.0, 20.0)|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 6 | stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0) | 1 | 1 | 0.0 | +1.0 |
| 7 | maxhold=900.0|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 8 | stop=('swing', 8)|target=('R', 2.0) | 1 | 1 | 0.5 | +0.5 |
| 9 | stop=('vol', 2.5)|trail=('chand', 2.0) | 1 | 1 | 0.5 | +0.5 |
| 10 | stop=('swing', 4)|target=('R', 2.0) | 1 | 1 | 0.5 | +0.5 |
| 11 | minrr=2.0|stop=('swing', 8)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |
| 12 | stop=('swing', 8)|trail=('swing', 1) | 0 | 0 | 0.0 | +0.0 |
| 13 | stop=('swing', 4)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 14 | stop=('swing', 4)|trail=('swing', 1) | 0 | 0 | 0.0 | +0.0 |
| 15 | stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 16 | minrr=1.5|stop=('swing', 8)|target=('mm', 1.27) | 0 | 0 | 0.0 | +0.0 |
| 17 | stop=('vol', 2.5)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 18 | stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 19 | stop=('vol', 1.5)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 20 | minrr=2.0|stop=('vol', 1.5)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |

Recipes with NEW real minus null <= 0 in this sample: 58 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('chand', 2.0); stop=('swing', 4)|trail=('swing', 1); stop=('swing', 4)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('chand', 2.0); stop=('swing', 8)|trail=('chand', 3.0); stop=('swing', 8)|trail=('swing', 1); stop=('swing', 8)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 8)|target=('R', 2.0); minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27); stop=('vol', 1.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 1.5)|target=('opp',); stop=('vol', 1.5)|trail=('chand', 2.0); stop=('vol', 1.5)|trail=('chand', 3.0); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('vol', 1.5)|target=('R', 2.0); minrr=1.5|stop=('vol', 2.5)|target=('mm', 1.27); stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 2.5)|target=('opp',); stop=('vol', 2.5)|trail=('chand', 3.0); stop=('vol', 2.5)|trail=('swing', 1); stop=('vol', 2.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=1.5|stop=('inval', 2)|target=('mm', 1.27); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('swing', 1); stop=('inval', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('inval', 2)|target=('R', 3.0)|trail=('chand', 3.0); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('swing', 1); stop=('wall', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('wall', 2)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('wall', 2)|target=('R', 2.0); stop=('vol', 2.5)|trail=('bricks', 1); stop=('vol', 2.5)|trail=('bricks', 2); stop=('vol', 2.5)|trail=('bricks', 3); be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0); be=(0.5, 0)|stop=('vol', 1.5)|target=('R', 2.0); stage=([1.0, 2.0], [0.34, 0.33], True)|stop=('vol', 1.5)|target=('R', 2.0); opp_exit=True|stop=('vol', 1.5); clock=('0825', '0955', '1155')|stop=('vol', 1.5); sar=True|stop=('vol', 2.5); flow=1|stop=('vol', 1.5)|trail=('chand', 3.0); flow=2|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 508 |
| fixed brackets (7), real entries: s per pair / per param | 17 / 1.2 |
| ALL 68 exit recipes, real entries: s per pair / per param | 904 / 62.3 |
| the same on 2 null draws: s per pair (brackets + exits) | 1451 |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 10,316 / 107 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 16,565 / 173 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 10,316 / 39 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 16,565 / 63 h |

Per-recipe cost (measured separately on 2 pair(s)): all 68 = 158.5 core-s per param; best 20 recipes by NEW-over-null = 53.0 (33%); best 10 = 32.7 (21%). Full-grid core-hours scale by the same fractions.

RECOMMENDATION (one line, filled when >= 150 pairs are finished): not enough pairs yet.
