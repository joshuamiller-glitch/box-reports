# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-18 20:53Z

STATUS: 1 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 0%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 | 0.0 | 0.0 | n/a | n/a | n/a | 0 |
| London | 0 | 0 | 0 | 0 | 0 | 0 | 0.0 | 0.0 | 0.0 | n/a | n/a | n/a | 0 |
| NYAM | 9 | 0 | 0 | 0 | 0 | 0 | 0.0 | 0.0 | 0.0 | n/a | n/a | n/a | 0 |
| NYPM | 9 | 0 | 0 | 0 | 0 | 0 | 0.0 | 0.0 | 0.0 | n/a | n/a | n/a | 0 |
| ALL | 18 | 0 | 0 | 0 | 0 | | 0.0 | 0.0 | 0.0 | 0.00 | 0.00 | 0.00 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| order flow | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| staged | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| stop-and-reverse | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| structure stop | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| time / behaviour | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| trailing | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | minrr=1.5|stop=('swing', 4)|target=('mm', 1.27) | 0 | 0 | 0.0 | +0.0 |
| 2 | stop=('swing', 4)|target=('R', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 3 | minrr=2.0|stop=('swing', 4)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |
| 4 | stop=('swing', 4)|trail=('chand', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 5 | stop=('swing', 4)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 6 | stop=('swing', 4)|trail=('swing', 1) | 0 | 0 | 0.0 | +0.0 |
| 7 | stop=('swing', 4)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 8 | stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 9 | noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 10 | minrr=1.5|stop=('swing', 8)|target=('mm', 1.27) | 0 | 0 | 0.0 | +0.0 |
| 11 | stop=('swing', 8)|target=('R', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 12 | minrr=2.0|stop=('swing', 8)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |
| 13 | stop=('swing', 8)|trail=('chand', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 14 | stop=('swing', 8)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 15 | stop=('swing', 8)|trail=('swing', 1) | 0 | 0 | 0.0 | +0.0 |
| 16 | stop=('swing', 8)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 17 | stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0) | 0 | 0 | 0.0 | +0.0 |
| 18 | noprog=(4, 0.5)|stop=('swing', 8)|target=('R', 2.0) | 0 | 0 | 0.0 | +0.0 |
| 19 | minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27) | 0 | 0 | 0.0 | +0.0 |
| 20 | stop=('vol', 1.5)|target=('R', 2.0) | 0 | 0 | 0.0 | +0.0 |

Recipes with NEW real minus null <= 0 in this sample: 68 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); stop=('swing', 4)|target=('R', 2.0); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('chand', 2.0); stop=('swing', 4)|trail=('chand', 3.0); stop=('swing', 4)|trail=('swing', 1); stop=('swing', 4)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); stop=('swing', 8)|target=('R', 2.0); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('chand', 2.0); stop=('swing', 8)|trail=('chand', 3.0); stop=('swing', 8)|trail=('swing', 1); stop=('swing', 8)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 8)|target=('R', 2.0); minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27); stop=('vol', 1.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 1.5)|target=('opp',); stop=('vol', 1.5)|trail=('chand', 2.0); stop=('vol', 1.5)|trail=('chand', 3.0); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('vol', 1.5)|target=('R', 2.0); minrr=1.5|stop=('vol', 2.5)|target=('mm', 1.27); stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 2.5)|target=('opp',); stop=('vol', 2.5)|trail=('chand', 2.0); stop=('vol', 2.5)|trail=('chand', 3.0); stop=('vol', 2.5)|trail=('swing', 1); stop=('vol', 2.5)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=1.5|stop=('inval', 2)|target=('mm', 1.27); stop=('inval', 2)|target=('R', 2.0); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('swing', 1); stop=('inval', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('inval', 2)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('inval', 2)|target=('R', 2.0); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('swing', 1); stop=('wall', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('wall', 2)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('wall', 2)|target=('R', 2.0); stop=('vol', 2.5)|trail=('bricks', 1); stop=('vol', 2.5)|trail=('bricks', 2); stop=('vol', 2.5)|trail=('bricks', 3); be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0); be=(0.5, 0)|stop=('vol', 1.5)|target=('R', 2.0); stage=([1.0, 2.0], [0.34, 0.33], True)|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 3 |
| fixed brackets (7), real entries: s per pair / per param | 2 / 0.6 |
| ALL 68 exit recipes, real entries: s per pair / per param | 80 / 26.8 |
| the same on 2 null draws: s per pair (brackets + exits) | 143 |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 917 / 10 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 1,630 / 17 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 917 / 4 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 1,630 / 6 h |

RECOMMENDATION (one line, filled when >= 150 pairs are finished): not enough pairs yet.
