# EXIT_YIELD - what do the 68 exit recipes add on EVERY cell? (W-EXITYIELD, order 2024Z), refreshed 2026-11-18 23:03Z

STATUS: 74 pairs finished of the ordered stratified sample (5% = 1,801 pairs of 36,026; the sample list leaves out Dallas row groups 0-1, 2 of 12). Fraction of the 5% target: 4%. Any prefix of the ordered list is a proportional stratified random sample, so partial numbers are unbiased but noisier.
WHAT IS RUN: per pair, the COARSE params of the module (first / middle / last per variant = the SAME coverage as the real pass-1 search, because all params cost 1-3 core-hours per pair: see c.), all modes: 68 exit recipes on the REAL entries; the 7 fixed brackets on all params but scored on the same coarse set; and the same on 2 random-entry null draws (same count and side mix, null_audit rules). Cell = (pair, param, mode, session). Survivor rule = R0 thresholds on SURVIVOR_COUNTS.md (L6M>0, >=100 trades in L6M, L3M>0, persistence>0.60, no RED prior year), scale-free so no stop is needed. Bracket passer = any of the 7 brackets passes; exit passer = any of the 68 recipes passes; NEW = exit passer that is not a bracket passer.
NOT DONE (labelled): (1) own-stop version of the EXITS (needs per-trade records inside the path simulator; not built: the own-stop result below is for the FIXED BRACKETS only, N=2 stops); (2) the stack mask (account rules) version; (3) pairs of Dallas row groups 0-1.

## a. cells passing the survivor rule, per session (real vs null)

| session | cells (with trades) | bracket passers real | exit passers real | either | NEW (exit only) | LOST (bracket only) | bracket passers null (mean of 2) | exit passers null | NEW null | ratio null/real bracket | ratio null/real exit | ratio null/real NEW | brackets own-stop 2 stops passers real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | 1,774 | 4 | 8 | 12 | 8 | 4 | 0.5 | 2.5 | 2.5 | 0.12 | 0.31 | 0.31 | 1 |
| London | 2,376 | 2 | 5 | 7 | 5 | 2 | 2.0 | 4.0 | 4.0 | 1.00 | 0.80 | 0.80 | 1 |
| NYAM | 3,399 | 10 | 31 | 41 | 31 | 10 | 1.5 | 10.5 | 10.5 | 0.15 | 0.34 | 0.34 | 5 |
| NYPM | 3,380 | 0 | 1 | 1 | 1 | 0 | 1.0 | 2.0 | 2.0 | n/a | 2.00 | 2.00 | 2 |
| ALL | 10,929 | 16 | 45 | 61 | 45 | | 5.0 | 19.0 | 19.0 | 0.31 | 0.42 | 0.42 | |

READING: ratio null/real = how often noise passes the same rule relative to the real search (1.00 = the rule cannot tell real from random entries; lower = more real). If the exit-passer ratio is HIGHER than the bracket-passer ratio, an exit passer is LESS likely to be real than a bracket passer (best-of-68 on noise inflates). NEW passers with a null/real ratio near 1 are mostly selection.

## b. which exit FAMILIES produce the new passers

| family | passers real (all sessions) | NEW passers real | NEW null (mean of 2) | NEW real minus null | NEW where this family is the ONLY one that passes (real) | same null |
|---|---|---|---|---|---|---|
| market target | 23 | 23 | 5.0 | +18.0 | 12 | 4.5 |
| order flow | 0 | 0 | 0.0 | +0.0 | 0 | 0.0 |
| staged | 9 | 9 | 1.5 | +7.5 | 3 | 0.5 |
| stop-and-reverse | 3 | 3 | 2.0 | +1.0 | 2 | 1.5 |
| structure stop | 1 | 1 | 0.0 | +1.0 | 0 | 0.0 |
| time / behaviour | 17 | 17 | 5.0 | +12.0 | 6 | 3.5 |
| trailing | 15 | 15 | 8.5 | +6.5 | 8 | 7.0 |

### recipes ranked by NEW passers real minus null (top 20; the rest add nothing beyond noise or less)

| rank | recipe | passers real | NEW real | NEW null | real minus null |
|---|---|---|---|---|---|
| 1 | stop=('vol', 1.5)|target=('R', 2.0) | 6 | 6 | 0.5 | +5.5 |
| 2 | latch=(0.95, 0.0, 30.0)|stop=('vol', 1.5)|target=('R', 2.0) | 6 | 6 | 0.5 | +5.5 |
| 3 | stop=('swing', 8)|target=('R', 2.0) | 5 | 5 | 0.5 | +4.5 |
| 4 | be=(1.0, 0)|stop=('vol', 1.5)|trail=('chand', 3.0) | 5 | 5 | 1.5 | +3.5 |
| 5 | minrr=1.5|stop=('vol', 2.5)|target=('mm', 1.27) | 4 | 4 | 1.0 | +3.0 |
| 6 | stop=('inval', 2)|target=('R', 2.0) | 3 | 3 | 0.0 | +3.0 |
| 7 | stop=('vol', 1.5)|trail=('chand', 3.0) | 4 | 4 | 1.0 | +3.0 |
| 8 | stop=('swing', 4)|target=('R', 2.0) | 4 | 4 | 1.0 | +3.0 |
| 9 | noprog=(4, 0.5)|stop=('inval', 2)|target=('R', 2.0) | 3 | 3 | 0.0 | +3.0 |
| 10 | clock=('0825', '0955', '1155')|stop=('vol', 1.5) | 3 | 3 | 0.0 | +3.0 |
| 11 | stage=([1.0, 2.0], [0.34, 0.33], True)|stop=('vol', 1.5)|target=('R', 2.0) | 3 | 3 | 0.5 | +2.5 |
| 12 | latch=(0.85, 3.0, 20.0)|stop=('vol', 1.5)|target=('R', 2.0) | 3 | 3 | 0.5 | +2.5 |
| 13 | stop=('vol', 2.5)|trail=('chand', 2.0) | 4 | 4 | 1.5 | +2.5 |
| 14 | minrr=1.5|stop=('vol', 1.5)|target=('mm', 1.27) | 3 | 3 | 0.5 | +2.5 |
| 15 | stage=([1.0], [0.5], True)|stop=('vol', 2.5)|target=('R', 3.0)|trail=('chand', 3.0) | 3 | 3 | 1.0 | +2.0 |
| 16 | stage=([1.0], [0.5], True)|stop=('vol', 1.5)|target=('R', 3.0)|trail=('chand', 3.0) | 2 | 2 | 0.5 | +1.5 |
| 17 | stop=('vol', 1.5)|trail=('chand', 2.0) | 3 | 3 | 1.5 | +1.5 |
| 18 | stop=('vol', 2.5)|trail=('chand', 3.0) | 2 | 2 | 1.0 | +1.0 |
| 19 | stop=('vol', 2.5)|trail=('bricks', 3) | 2 | 2 | 1.0 | +1.0 |
| 20 | stage=([1.0], [0.5], True)|stop=('inval', 2)|target=('R', 3.0)|trail=('chand', 3.0) | 1 | 1 | 0.0 | +1.0 |

Recipes with NEW real minus null <= 0 in this sample: 41 of 68 (candidates to DROP from a full run): minrr=1.5|stop=('swing', 4)|target=('mm', 1.27); minrr=2.0|stop=('swing', 4)|target=('opp',); stop=('swing', 4)|trail=('chand', 2.0); stop=('swing', 4)|trail=('swing', 1); stop=('swing', 4)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 4)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 4)|target=('R', 2.0); minrr=1.5|stop=('swing', 8)|target=('mm', 1.27); minrr=2.0|stop=('swing', 8)|target=('opp',); stop=('swing', 8)|trail=('chand', 2.0); stop=('swing', 8)|trail=('chand', 3.0); stop=('swing', 8)|trail=('swing', 1); stop=('swing', 8)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('swing', 8)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('swing', 8)|target=('R', 2.0); minrr=2.0|stop=('vol', 1.5)|target=('opp',); stop=('vol', 1.5)|trail=('swing', 1); stop=('vol', 1.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 1.5)|target=('R', 2.0); stop=('vol', 2.5)|target=('R', 2.0); minrr=2.0|stop=('vol', 2.5)|target=('opp',); stop=('vol', 2.5)|trail=('swing', 1); stop=('vol', 2.5)|trail=('line', 2); noprog=(4, 0.5)|stop=('vol', 2.5)|target=('R', 2.0); minrr=1.5|stop=('inval', 2)|target=('mm', 1.27); minrr=2.0|stop=('inval', 2)|target=('opp',); stop=('inval', 2)|trail=('chand', 2.0); stop=('inval', 2)|trail=('chand', 3.0); stop=('inval', 2)|trail=('line', 2); minrr=1.5|stop=('wall', 2)|target=('mm', 1.27); stop=('wall', 2)|target=('R', 2.0); minrr=2.0|stop=('wall', 2)|target=('opp',); stop=('wall', 2)|trail=('chand', 2.0); stop=('wall', 2)|trail=('chand', 3.0); stop=('wall', 2)|trail=('swing', 1); stop=('wall', 2)|trail=('line', 2); stage=([1.0], [0.5], True)|stop=('wall', 2)|target=('R', 3.0)|trail=('chand', 3.0); noprog=(4, 0.5)|stop=('wall', 2)|target=('R', 2.0); stop=('vol', 2.5)|trail=('bricks', 1); flow=1|stop=('vol', 1.5)|trail=('chand', 3.0); flow=2|stop=('vol', 1.5)|target=('R', 2.0)

## c. cost (core-seconds measured on the rented 128-thread hosts, nice 12, engine and grid running beside it; SMT shares cores so these are hyper-thread-seconds)

| item | value |
|---|---|
| params finished (sum over finished pairs) | 1,175 |
| fixed brackets (7), real entries: s per pair / per param | 28 / 1.8 |
| ALL 68 exit recipes, real entries: s per pair / per param | 1230 / 77.5 |
| the same on 2 null draws: s per pair (brackets + exits) | 1948 |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 14,045 / 146 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on current fleet (box 1 + Dallas, 96 core-equivalents) | 22,235 / 232 h |
| FULL GRID (41,102 pairs): exits, real: core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 14,045 / 54 h |
| extra for the exit NULL (2 draws, brackets+exits): core-hours / hours on pool (4 machines, 262 core-equivalents, HT factor assumed) | 22,235 / 85 h |

Per-recipe cost (measured separately on 2 pair(s)): all 68 = 158.5 core-s per param; best 20 recipes by NEW-over-null = 64.9 (41%); best 10 = 29.6 (19%). Full-grid core-hours scale by the same fractions.

RECOMMENDATION (one line, filled when >= 150 pairs are finished): not enough pairs yet.
