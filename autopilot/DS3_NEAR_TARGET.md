# DS3_NEAR_TARGET - near-target take, profit side, all books (user order 17:25Z)
Generated 2026-11-24 07:39Z. 184 cells scored (family PHI_NT, U2, live-week gated, null_ver 2). PRE-PROOF. First-order screen; exact (ExhCut) results in the Stage 2 section.

Cells: (1) NT_take: market take (decision at k, execute k+1 at mid -+0.80 pt) once the favourable extreme (print high/low, or mid) is within k ticks of the target (k 1-10) and the extreme is >= s seconds old (s 0-30); policy line `profit <book> * pct>=P secs_ext>=s take`, P = 1 - k*0.25/target (target 60 pt; O7 90). (2) NT_retarget: nominal limit at target -+ k ticks (k 1-8). (3) NT_queue_wall / NT_queue_book: within kt ticks of the target and the target-level wall (>= X x MedLevel) or the ahead_rel / tot_rel book ratio >= thr: market take. The stop-side mirror is not in the grid. Equal lots, no trade removed; reference row = never-cut hold-to-bracket (60/60), not a candidate.

Execution cost: every take that would have filled anyway at the target pays (target - exit price) + 0.80 pt slippage; the net-gain table below shows whether the rescued misses pay for that.

## Frozen live week: targets missed by <= k ticks
186 frozen live trades; the 60-pt (O7 90) target price was touched on the path before the live exit for 9; never touched for 177. Missed by 0 < m <= k ticks (live pnl = what the trade actually earned at its live exit): 
- k=1: 11 trades (P7 5, K7 5, M7 1), live pnl of those 43165 USD, a fill exactly at the target would add 2251 USD over what they earned
- k=2: 25 trades (K7 12, P7 7, M7 3, A7 2, U7 1), live pnl of those 68820 USD, a fill exactly at the target would add 2890 USD over what they earned
- k=3: 32 trades (K7 18, P7 7, M7 4, A7 2, U7 1), live pnl of those 78420 USD, a fill exactly at the target would add 2851 USD over what they earned
- k=5: 42 trades (K7 22, P7 11, M7 6, A7 2, U7 1), live pnl of those 110815 USD, a fill exactly at the target would add 3920 USD over what they earned
- k=8: 54 trades (K7 26, P7 15, M7 7, A7 3, X5 1, H7 1, U7 1), live pnl of those 135235 USD, a fill exactly at the target would add 6989 USD over what they earned
- k=10: 58 trades (K7 26, P7 15, M7 8, A7 6, X5 1, H7 1, U7 1), live pnl of those 136285 USD, a fill exactly at the target would add 10720 USD over what they earned
Note: most of the missed trades already earned at or above target pnl at their live exit, so the live miss gain is small; the live M7 example of today (long 27933.75, target 27993.75, high 27993.50, missed by 1 tick) is outside the frozen file and is quoted from the user only.

### K7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=4 | +870 / +872 / +496 / +415 / +212 / -8 / +147 / -28 | 15455 / 20902 | 23127 / 26707 | 1718 | 0.154 | -375 | CANDIDATE-DD |
| NT_take | k=7 s=30 trigger=mid | -455 / +155 / -29 / +92 / -24 / -323 / -86 / -142 | 15919 / 20902 | 23463 / 26707 | 437 | 0.231 | +1476 | CANDIDATE-DD |
| NT_retarget | k=5 | +632 / +1001 / +538 / +644 / +318 / -111 / +102 / +34 | 15935 / 20902 | 23727 / 26707 | 1957 | 0.108 | -495 | CANDIDATE-DD |
| NT_take | k=8 s=30 trigger=mid | -639 / +236 / +16 / +18 / -52 / -154 / -162 / -95 | 16020 / 20902 | 24054 / 26707 | 534 | 0.169 | +504 | CANDIDATE-DD |
| NT_take | k=7 s=20 trigger=mid | -527 / +116 / -69 / +68 / -49 / -344 / -93 / -147 | 16039 / 20902 | 23623 / 26707 | 514 | 0.385 | +1354 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 1718 fired; 1688 would have filled at the target anyway (cost -38720 USD total, -22.9 per take); 30 rescued misses (gain vs their hold-to-bracket exit 71959 USD).

### P7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=8 | +2611 / -2261 / +535 / +1658 / +2001 / -1154 / -358 / -498 | 77449 / 133887 | 111128 / 109442 | 1857 | 0.031 | -3572 | CANDIDATE-DD |
| NT_retarget | k=7 | +3152 / -1728 / +1002 / +623 / +1576 / -1005 / -193 / -322 | 103032 / 133887 | 107618 / 109442 | 1751 | 0.077 | -2977 | CANDIDATE-DD |
| NT_retarget | k=5 | +4486 / -548 / +2034 / +1341 / +1066 / -1139 / -45 / -397 | 107577 / 133887 | 104313 / 109442 | 1483 | 0.077 | -1892 | CANDIDATE-DD |
| NT_retarget | k=6 | +3879 / -1103 / +1516 / +789 / +1144 / -1481 / -39 / -336 | 109867 / 133887 | 105618 / 109442 | 1627 | 0.200 | -2457 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_slow kt=5 thr=3.0 | -149 / -75 / +686 / +90 / +35 / -584 / -148 / -162 | 111908 / 133887 | 109442 / 109442 | 46 | 0.031 | +0 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 1857 fired; 1812 would have filled at the target anyway (cost -326120 USD total, -180.0 per take); 45 rescued misses (gain vs their hold-to-bracket exit 456629 USD).

### M7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=2 | -70 / -54 / -50 / +145 / +188 / -57 / -36 / -32 | 37775 / 44425 | 51471 / 50321 | 633 | 0.169 | +1930 | CANDIDATE-DD |
| NT_retarget | k=3 | +474 / +496 / +297 / +471 / +323 / -108 / +21 / -61 | 38495 / 44425 | 47811 / 50321 | 864 | 0.262 | +1920 | CANDIDATE-DD |
| NT_take | k=2 s=5 trigger=print | -284 / -135 / -97 / +32 / +16 / -323 / -122 / -89 | 39001 / 44425 | 54601 / 50321 | 243 | 0.046 | +1844 | no |
| NT_retarget | k=4 | +409 / +444 / +246 / +408 / +261 / -175 / +44 / -98 | 39265 / 44425 | 49026 / 50321 | 1039 | 0.262 | +1910 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_fast kt=2 thr=1.5 | +0 / -22 / -26 / +41 / -40 / -249 / -51 / -101 | 39468 / 44425 | 51771 / 50321 | 147 | 0.062 | +334 | CANDIDATE-DD |
Net gain per take (best cell, first order, all fired trades of the book): 633 fired; 627 would have filled at the target anyway (cost -7340 USD total, -11.7 per take); 6 rescued misses (gain vs their hold-to-bracket exit 19260 USD).

### U7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_queue_book | feat=ahead_rel_slow kt=5 thr=3.0 | +0 / +0 / +0 / +13 / -30 / -14 / -17 / -3 | 21561 / 21561 | 42226 / 42226 | 26 | 1.000 | +0 | no |
| NT_queue_book | feat=ahead_rel_fast kt=5 thr=3.0 | +0 / +0 / +0 / +34 / -2 / +0 / -47 / -3 | 21561 / 21561 | 43913 / 42226 | 27 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 26 fired; 24 would have filled at the target anyway (cost -8375 USD total, -349.0 per take); 2 rescued misses (gain vs their hold-to-bracket exit 1393 USD).

### A7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_queue_wall | feat=wall_med kt=1 thr=10 | +0 / +0 / +0 / +0 / -3 / +0 / -6 / -3 | 12461 / 12461 | 6089 / 6089 | 22 | 0.862 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 22 fired; 22 would have filled at the target anyway (cost -1044 USD total, -47.5 per take); 0 rescued misses (gain vs their hold-to-bracket exit 0 USD).

### H7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_take | k=3 s=30 trigger=print | -56 / -28 / -44 / +16 / -25 / -28 / -48 / -31 | 13974 / 15477 | 20829 / 20667 | 69 | 0.108 | +0 | CANDIDATE-DD |
| NT_take | k=4 s=30 trigger=print | -56 / -28 / -56 / +1 / -61 / -74 / -74 / -63 | 13974 / 15477 | 20829 / 20667 | 100 | 0.092 | +0 | CANDIDATE-DD |
| NT_take | k=1 s=30 trigger=print | +0 / +0 / +0 / +0 / -11 / -8 / -10 / -3 | 15477 / 15477 | 20829 / 20667 | 27 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 69 fired; 64 would have filled at the target anyway (cost -14396 USD total, -224.9 per take); 5 rescued misses (gain vs their hold-to-bracket exit 12947 USD).

### O7 - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_take | k=9 s=5 trigger=mid | +0 / +0 / +0 / +0 / -10 / -6 / -17 / -28 | 7469 / 7469 | 5102 / 5102 | 42 | 1.000 | +0 | no |
| NT_take | k=10 s=10 trigger=mid | +0 / +0 / +0 / +0 / -7 / +0 / -19 / -22 | 7469 / 7469 | 5102 / 5102 | 37 | 1.000 | +0 | no |
| NT_take | k=5 s=5 trigger=print | +0 / +0 / +0 / +0 / -15 / -24 / -15 / -19 | 7469 / 7469 | 5102 / 5102 | 44 | 1.000 | +0 | no |
| NT_take | k=5 s=30 trigger=print | +0 / +0 / +0 / +0 / -12 / -34 / -8 / -12 | 7469 / 7469 | 5102 / 5102 | 20 | 1.000 | +0 | no |
| NT_take | k=8 s=10 trigger=mid | +0 / +0 / +0 / +0 / -4 / +0 / -14 / -22 | 7469 / 7469 | 5102 / 5102 | 30 | 1.000 | +0 | no |
Net gain per take (best cell, first order, all fired trades of the book): 42 fired; 42 would have filled at the target anyway (cost -3954 USD total, -94.2 per take); 0 rescued misses (gain vs their hold-to-bracket exit 0 USD).

### ALL - pooled sessions, drawdown-first top 5
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | nfire | placebo p | live week | label |
|---|---|---|---|---|---|---|---|---|
| NT_retarget | k=5 | +5069 / +1862 / +3341 / +2517 / +1807 / -640 / +215 / -426 | 109631 / 121381 | 133965 / 152455 | 5901 | 0.169 | -588 | CANDIDATE-DD |
| NT_retarget | k=6 | +4055 / +943 / +2480 / +1657 / +1711 / -881 / +130 / -227 | 111081 / 121381 | 135360 / 152455 | 6443 | 0.262 | +1643 | CANDIDATE-DD |
| NT_retarget | k=7 | +2885 / -36 / +1619 / +1275 / +1897 / -707 / +84 / -353 | 112731 / 121381 | 124625 / 152455 | 6903 | 0.292 | +843 | CANDIDATE-DD |
| NT_retarget | k=8 | +1980 / -928 / +800 / +2204 / +2165 / -972 / -182 / -610 | 114131 / 121381 | 126165 / 152455 | 7294 | 0.385 | -62 | CANDIDATE-DD |
| NT_queue_book | feat=tot_rel_fast kt=1 thr=3.0 | -28 / +0 / -9 / +58 / -6 / -35 / -31 / -156 | 121381 / 121381 | 153084 / 152455 | 34 | 1.000 | +0 | no |

## Per-session best cell (drawdown-first, L6M mean >= never-cut, nfire >= 20)
- K7 session 1: NT_retarget k=7  L6M maxDD 11452 / 14952, L6M mean +181, PRE mean -5, nfire 538
- K7 session 3: NT_retarget k=5  L6M maxDD 19275 / 23185, L6M mean +43, PRE mean -27, nfire 453
- K7 session 4: NT_queue_wall feat=wall_med kt=5 thr=10  L6M maxDD 6369 / 6369, L6M mean +0, PRE mean -23, nfire 35
- P7 session 0: NT_retarget k=8  L6M maxDD 92850 / 116210, L6M mean +919, PRE mean -271, nfire 849
- P7 session 3: NT_take k=9 s=5 trigger=print  L6M maxDD 55529 / 86629, L6M mean +564, PRE mean -500, nfire 288
- M7 session 1: NT_retarget k=1  L6M maxDD 31193 / 38178, L6M mean +86, PRE mean -7, nfire 232
- M7 session 3: NT_queue_book feat=ahead_rel_fast kt=3 thr=3.0  L6M maxDD 11379 / 11667, L6M mean +11, PRE mean -1, nfire 20
- U7 session 0: NT_queue_wall feat=wall_med kt=2 thr=10  L6M maxDD 10073 / 9906, L6M mean +0, PRE mean -14, nfire 21
- U7 session 1: NT_take k=2 s=30 trigger=print  L6M maxDD 32749 / 32749, L6M mean +0, PRE mean -29, nfire 24
- A7 session 0: NT_queue_wall feat=wall_med kt=1 thr=10  L6M maxDD 12461 / 12461, L6M mean +0, PRE mean -6, nfire 22
- H7 session 0: NT_queue_wall feat=wall_med kt=3 thr=10  L6M maxDD 14606 / 14606, L6M mean +0, PRE mean -13, nfire 25
- H7 session 3: NT_take k=3 s=0 trigger=mid  L6M maxDD 3762 / 3762, L6M mean +0, PRE mean -5, nfire 26
- O7 session 3: NT_take k=9 s=5 trigger=mid  L6M maxDD 7469 / 7469, L6M mean +0, PRE mean -17, nfire 42

## Plain sentences per book (profit, near-target)
K7 profit (near-target): NT_retarget (k=4); L6M maxDD 20902 -> 15455, L6M mean +415 USD/wk, PRE maxDD 26707 -> 23127, PRE mean +147, placebo p 0.154, live week -375 USD (15 fired); CANDIDATE-DD.

P7 profit (near-target): NT_retarget (k=8); L6M maxDD 133887 -> 77449, L6M mean +1658 USD/wk, PRE maxDD 109442 -> 111128, PRE mean -358, placebo p 0.031, live week -3572 USD (19 fired); CANDIDATE-DD.

M7 profit (near-target): NT_retarget (k=2); L6M maxDD 44425 -> 37775, L6M mean +145 USD/wk, PRE maxDD 50321 -> 51471, PRE mean -36, placebo p 0.169, live week +1930 USD (2 fired); CANDIDATE-DD.

U7 profit (near-target): NT_queue_book (feat=ahead_rel_slow kt=5 thr=3.0); L6M maxDD 21561 -> 21561, L6M mean +13 USD/wk, PRE maxDD 42226 -> 42226, PRE mean -17, placebo p 1.000, live week +0 USD (0 fired); no.

A7 profit (near-target): NT_queue_wall (feat=wall_med kt=1 thr=10); L6M maxDD 12461 -> 12461, L6M mean +0 USD/wk, PRE maxDD 6089 -> 6089, PRE mean -6, placebo p 0.862, live week +0 USD (0 fired); no.

H7 profit (near-target): NT_take (k=3 s=30 trigger=print); L6M maxDD 15477 -> 13974, L6M mean +16 USD/wk, PRE maxDD 20667 -> 20829, PRE mean -48, placebo p 0.108, live week +0 USD (0 fired); CANDIDATE-DD.

O7 profit (near-target): NT_take (k=9 s=5 trigger=mid); L6M maxDD 7469 -> 7469, L6M mean +0 USD/wk, PRE maxDD 5102 -> 5102, PRE mean -17, placebo p 1.000, live week +0 USD (0 fired); no.

ALL profit (near-target): NT_retarget (k=5); L6M maxDD 121381 -> 109631, L6M mean +2517 USD/wk, PRE maxDD 152455 -> 133965, PRE mean +215, placebo p 0.169, live week -588 USD (37 fired); CANDIDATE-DD.

## Policy lines (D7 grammar, best cell per book; fields the grammar lacks marked)
- profit K7 * retarget -4 ticks
- profit P7 * retarget -8 ticks
- profit M7 * retarget -2 ticks
- profit U7 * within 5 ticks of target and ahead_rel_slow>=3.0 take at market   # needs: wall/ahead gate on take
- profit A7 * within 1 ticks of target and wall_med>=10 take at market   # needs: wall/ahead gate on take
- profit H7 * pct>=0.9875 secs_ext>=30 take   (k=3 ticks, print trigger)
- profit O7 * pct>=0.9750 secs_ext>=5 take   (k=9 ticks, mid trigger)