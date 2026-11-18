# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-18 22:32Z

STATUS: 52 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 3%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,051 | 2 | 4 | 6 | 4 | 2 | 0.0 | 1.5 | 1.5 | 0.00 | 0.38 | 0.38 | 0 |
| London | 1,431 | 0 | 3 | 3 | 3 | 0 | 2.0 | 2.5 | 2.5 | n/a | 0.83 | 0.83 | 0 |
| NYAM | 2,300 | 2 | 15 | 17 | 15 | 2 | 0.5 | 8.5 | 8.5 | 0.25 | 0.57 | 0.57 | 4 |
| NYPM | 2,277 | 0 | 0 | 0 | 0 | 0 | 1.0 | 2.0 | 2.0 | n/a | n/a | n/a | 1 |
| ALL | 7,059 | 4 | 22 | 26 | 22 | | 3.5 | 14.5 | 14.5 | 0.88 | 0.66 | 0.66 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 12 | 12 | 4.5 | +7.5 | 8 | 4.0 |
| order flow | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| staged | 2 | 2 | 1.0 | +1.0 | 2 | 0.5 |
| stop-and-reverse | 1 | 1 | 1.0 | +0.0 | 0 | 0.5 |
| structure stop | 1 | 1 | 0.0 | +1.0 | 0 | 0.0 |
| time / behaviour | 5 | 5 | 3.5 | +1.5 | 1 | 2.5 |
| trailing | 7 | 7 | 6.5 | +0.5 | 6 | 6.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | noprog=(4, 0.5)|stop=('inval', 2)|target=('R', 2.0) | 3 | 3 | 0.0 | +3.0 |
| 2 | stop=('inval', 2)|target=('R', 2.0) | 3 | 3 | 0.0 | +3.0 |
| 3 | stop=('vol', 1.5)|target=('R', 2.0) | 3 | 3 | 0.5 | +2.5 |
| 4 | stop=('vol', 2.5)|trail=('bricks', 3) | 2 | 2 | 0.0 | +2.0 |
| 5 | stop=('vol', 2.5)|trail=('bricks', 2) | 2 | 2 | 0.0 | +2.0 |
| 6 | stop=('swing', 8)|target=('R', 2.0) | 2 | 2 | 0.5 | +1.5 |
| 7 | stop=('swing', 4)|target=('R', 2.0) | 2 | 2 | 1.0 | +1.0 |
| 8 | stage=([1.0], [0.5], True)|stop=('inval', 2)|target=('R', 3.0)|trail=('chand', 3.0) | 1 | 1 | 0.0 | +1.0 |
| 9 | opp_exit=True|stop=('vol', 1.5) | 1 | 1 | 0.0 | +1.0 |
| 10 | maxhold=900.0|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.0 | +1.0 |
| 11 | stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0) | 1 | 1 | 0.5 | +0.5 |
| 12 | latch=(0.85, 3.0, 20.0)|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.5 | +0.5 |
| 13 | stop=('vol', 2.5)|trail=('chand', 3.0) | 1 | 1 | 0.5 | +0.5 |
| 14 | latch=(0.95, 0.0, 30.0)|stop=('vol', 1.5)|target=('R', 2.0) | 1 | 1 | 0.5 | +0.5 |
| 15 | stop=('swing', 4)|trail=('chand', 3.0) | 2 | 2 | 1.5 | +0.5 |
| 16 | stop=('swing', 4)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 17 | stop=('vol', 1.5)|trail=('line', 2) | 0 | 0 | 0.0 | +0.0 |
| 18 | minrr=2.0|stop=('vol', 2.5)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |
| 19 | minrr=1.5|stop=('inval', 2)|target=('mm', 1.27) | 0 | 0 | 0.0 | +0.0 |
| 20 | minrr=2.0|stop=('inval', 2)|target=('opp',) | 0 | 0 | 0.0 | +0.0 |

Recipes with NEW real minus null <= 0 in this sample: 53 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('chand', 2.0); stop=('swing', 4)|trail=('swing', 1); stop=('swing', 4)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('chand', 2.0); stop=('swing', 8)|trail=('chand', 3.0); stop=('swing', 8)|trail=('swing', 1); stop=('swing', 8)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 8)|target=('R', 2.0); minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27); minrr=2.0|stop=('vol', 1.5)|target=('opp',); stop=('vol', 1.5)|trail=('chand', 2.0); stop=('vol', 1.5)|trail=('chand', 3.0); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('vol', 1.5)|target=('R', 2.0); minrr=1.5|stop=('vol', 2.5)|target=('mm', 1.27); stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 2.5)|target=('opp',); stop=('vol', 2.5)|trail=('chand', 2.0); stop=('vol', 2.5)|trail=('swing', 1); stop=('vol', 2.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=1.5|stop=('inval', 2)|target=('mm', 1.27); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('swing', 1); stop=('inval', 2)|trail=('line', 2); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('swing', 1); stop=('wall', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('wall', 2)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('wall', 2)|target=('R', 2.0); stop=('vol', 2.5)|trail=('bricks', 1); be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0); be=(0.5, 0)|stop=('vol', 1.5)|target=('R', 2.0); stage=([1.0, 2.0], [0.34, 0.33], True)|stop=('vol', 1.5)|target=('R', 2.0); clock=('0825', '0955', '1155')|stop=('vol', 1.5); sar=True|stop=('vol', 2.5); flow=1|stop=('vol', 1.5)|trail=('chand', 3.0); flow=2|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 804 |
| fixed brackets (7), real entries: s per pair / per param | 21 / 1.4 |
| ALL 68 exit recipes, real entries: s per pair / per param | 1103 / 71.4 |
| the same on 2 null draws: s per pair (brackets + exits) | 1724 |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 12,596 / 131 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 19,679 / 205 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 12,596 / 48 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 19,679 / 75 h |

Per-recipe cost (measured separately on 2 pair(s)): all 68 = 158.5 core-s per param; best 20 recipes by NEW-over-null = 50.8 (32%); best 10 = 28.3 (18%). Full-grid core-hours scale by the same fractions.

RECOMMENDATION (one line, filled when >= 150 pairs are finished): not enough pairs yet.
