# DS3_RECENT_PORTFOLIO - T-RECENT-EDGE section 3: how to run recent edges, and the walk-forward test of the approach (RE-2, 2026-10-31)

Prereg `l2vast/ds3/prereg/RE2_prereg.md` sha256 5eb81c3287b4f232f680f7651669585958440b8883d72cba4d002cd6ee702e9b. Code `l2vast/ds3/code/recentedge2/` (re2_portfolio, re2_portfolio_eval, re2_portfolio_latest, re2_mkportfolio). Outputs `l2vast/ds3/out/recentedge2/portfolio_*.csv|pkl`, `latest_*`. Masks capped 20260206; UNTOUCHED never read.

## PAGE 1 - the answer

**Units.** Everything is the lock-engine stack on the 70/30 split base (S73), basis N, **research lots**, $/week, as a delta against the same stack without the edges. Live lots A = research / 2.35 (divide by 2.35). Reference: the base stack itself earned 50.8k/wk (SD 138k, max drawdown 625k) over 2023-04..2026-02, so a delta of -10k/wk is about a fifth of it. The ledger is the 294 unique recoverable series of DS3_EDGE_MONITOR.md (STACK-2 cells and new row-multiplier rules); programs that stored only window aggregates are not in the walk-forward (they have no monthly series).

1. **The plain sentence.** Each month from 2024-01 to 2026-01 the ledger was rebuilt from the information available at the month start (edges positive over the last 13 and 26 weeks, one representative per correlation cluster of weekly series) and run on the real lock engine for the next month. **Running them at full size would have made -9,598 $/wk over the 25 months (MDE 27,130; live A -4,084), 10 of 25 months positive; at half size -7,353 (MDE 20,567, 10 of 25); at the walk-forward shrunk size -5,531 (MDE 10,046, 2024 only: from 2025 the shrinkage factor measured on earlier months is below zero, so the size is 0); doing nothing earns 0.** The worst single month was -740,076 at full size (2024-07) and the maximum drawdown of the policy's own equity line 1,721,520 (the stack's own maximum drawdown is 625k).
2. **By year (full size, $/wk, research lots):** 2024 -3,253, 2025 -22,128, January 2026 59,813. The policy lost money in the 24 months before January 2026 and made it in the last month, which is exactly the pattern of a recent-regime edge being picked up after it turned on. Nothing earlier than 2025-10 predicted the January 2026 gain (persistence below).
3. **Screening by persistence did not help.** Edges whose noise-adjusted persistence score (first-pass walk-forward logistic, see section 1; RE-1's score replaces it when published) was >= 0.5 / 0.6 / 0.7: at shrunk size -5,462 / -6,209 / 213 $/wk; at full size -6,509 / -5,567 / -4,751 (MDE 21,870 / 14,614 / 12,701). The >= 0.7 policy is +213 $/wk but active in only 11 of 25 months and indistinguishable from zero (MDE 3,483). The local persistence score has no calibration (realised P(next quarter > 0) was 0.48 / 0.33 / 0.47 / 0.25 / 0.23 for score bins <0.4 / 0.4-0.5 / 0.5-0.6 / 0.6-0.7 / >0.7: if anything inverted).
4. **Is picking recently-positive edges better than picking at random?** Yes, slightly, and still negative. An equal-weight sleeve of every ON bank edge at full size (additive, not on the engine) made -1,581 $/wk (MDE 4,410; 10 of 25 months positive; on average 58 ON edges per month) against -6,869 +/- 695 $/wk for the same number of randomly chosen bank rules: recency selection removes about 5k/wk of the average rule's loss, it does not create a gain. Most rules in the bank are filters and cuts that remove profitable trades; the recent-edge question is whether the few that add value can be found in advance, and over 2024-26 they could not be found with this method.
5. **Sizing.** Kelly at the shrunk expectation is zero for the current ledger (the shrinkage factor, the ratio of next-13-week to trailing-13-week mean pooled over earlier months, is below zero for each group and is clipped at 0). Even at the generous bankroll W = 20 x the base stack's weekly SD the uncapped half-Kelly would be 0. So the only defensible size for a recent-only edge is the monitoring size: shadow, or a fixed small fraction chosen by the user. Section 3 shows what 50% and 100% of today's ledger would have done in the windows it was selected on.

## 1. Method

* Decision date D = first day of each month 2024-01..2026-01. Weeks fully before D only. Edge ON: trailing 13-week and 26-week mean > 0. Cluster representatives: edges sorted by 13-week mean, an edge is dropped if its weekly series correlates >= 0.8 (trailing 52 weeks) with an already-chosen one. S73-base rules only (the MKT-base twins are duplicates of the same effect).
* Persistence score: walk-forward logistic regression P(next 13-week mean > 0 | t13, t26, streak, 13/26 ratio, long-run mean) fitted on (rule, month) pairs whose outcome ended before D, then 'noise-adjusted' = 0.5 + score - baseline P for the same group measured on block-shuffled twins of the series (0.29 entry filter/regime, 0.41 sizing, 0.47 stack cut/cap). This is the first-pass the directive allows until RE-1's DS3_PERSISTENCE.md exists; RE-1's outputs were not published when this ran.
* Shrunk expectation = group keep-ratio (pooled next-13-week sum / trailing-13-week sum over earlier ON pairs, clipped to [0,1]) x the edge's trailing 13-week mean. Kelly: half-Kelly f = 0.5 mu_s W / sigma^2 with W = 20 x the base stack's weekly SD (a stated bankroll assumption; with W = 5 x SD the capped result is the same because mu_s = 0 now), capped at 1.0.
* Run: a real joint lock-engine run per decision with the cluster representatives together (s2_lib `T.run`): row-multiplier rules are multiplied (size f gives multiplier 1 + f (m - 1)), the first-stop cut with the highest 13-week mean is the one event rule (cut fraction P x f), a cap rule is added if f >= 0.5. Rules with f <= 0.01 are dropped. The month's delta = joint run minus the plain stack, summed over the days of the month. Doing nothing is 0. 'Everything positive at full size' = all cluster representatives at f = 1.
* Approximation: scaling a rule by f is linear for multipliers and cuts but not for the engine's day/week governors; the engine is re-run for every f so the nonlinearity is inside the numbers, only the rule's own parameters are scaled.

## 2. Walk-forward result, 2024-01..2026-01 (25 monthly decisions; research lots; $/wk)

| policy | mean $/wk | MDE | live A | active months | months + | months - | 2024 | 2025 | Jan 2026 | L6M | L3M | worst month $ | max DD $ | worst-20-week sum $ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| everything ON at full size | -9,598 | 27,130 | -4,084 | 25 | 10 | 15 | -3,253 | -22,128 | 59,813 | -5,839 | 3,213 | -740,076 | 1,721,520 | -2,941,233 |
| everything ON at 50% size | -7,353 | 20,567 | -3,129 | 25 | 10 | 15 | -9,537 | -9,299 | 39,360 | 7,084 | 13,118 | -552,829 | 1,110,261 | -2,437,136 |
| everything ON at shrunk Kelly size | -5,531 | 10,046 | -2,354 | 25 | 12 | 13 | -11,375 | 0 | 0 | 0 | 0 | -469,224 | 643,482 | -819,743 |
| persistence>=0.5, full | -6,509 | 21,870 | -2,770 | 23 | 12 | 11 | -10,132 | -4,743 | 15,787 | 773 | 2,060 | -740,076 | 1,293,596 | -2,634,140 |
| persistence>=0.5, shrunk | -5,462 | 9,826 | -2,324 | 23 | 11 | 12 | -11,234 | 0 | 0 | 0 | 0 | -469,224 | 636,022 | -788,997 |
| persistence>=0.6, full | -5,567 | 14,614 | -2,369 | 14 | 7 | 7 | -11,818 | -251 | 6,563 | 1,215 | 2,524 | -760,393 | 1,025,233 | -1,589,223 |
| persistence>=0.6, shrunk | -6,209 | 9,979 | -2,642 | 14 | 5 | 9 | -12,770 | 0 | 0 | 0 | 0 | -469,224 | 679,245 | -884,800 |
| persistence>=0.7, full | -4,751 | 12,701 | -2,022 | 11 | 5 | 6 | -9,778 | 7 | 0 | 0 | 0 | -734,161 | 919,530 | -1,319,960 |
| persistence>=0.7, shrunk | 213 | 3,483 | 91 | 11 | 7 | 4 | 439 | 0 | 0 | 0 | 0 | -0 | 119,141 | -112,017 |
| doing nothing | 0 | - | 0 | - | - | - | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| additive equal-weight sleeve of all ON edges, full | -1,581 | 4,410 | -673 | 25 | 10 | 15 | | | | | | | 407,965 | -478,337 |
| same, random bank rules (200 draws) | -6,869 | | | | | | | | | | | | | |

Monthly detail (delta in the month after the decision, $ at research lots, not per week; 'reps' = cluster representatives):

| decision month | ON edges | reps | everything, full | persistence>=0.5, shrunk | persistence>=0.5, full | persistence>=0.6, full |
|---|---|---|---|---|---|---|
| 2024-01 | 38 | 16 | 33,209 | 0 | 0 | 0 |
| 2024-02 | 38 | 13 | 20,930 | -0 | 35,288 | 42,725 |
| 2024-03 | 56 | 20 | -292,094 | -0 | -86,048 | -86,048 |
| 2024-04 | 68 | 21 | 301,640 | -0 | 227,568 | 2,615 |
| 2024-05 | 86 | 23 | 188,873 | 0 | 243,804 | 216,144 |
| 2024-06 | 127 | 31 | -62,810 | -116,783 | -73,833 | -73,833 |
| 2024-07 | 137 | 32 | -740,076 | -469,224 | -740,076 | -760,393 |
| 2024-08 | 61 | 16 | 243,660 | -9,398 | 243,660 | -642 |
| 2024-09 | 41 | 16 | 81,418 | 0 | 69,619 | 124,496 |
| 2024-10 | 61 | 23 | 316,844 | 0 | -108,263 | 36,553 |
| 2024-11 | 116 | 35 | -138,300 | -0 | -281,355 | -104,083 |
| 2024-12 | 76 | 23 | -125,722 | -0 | -67,345 | -23,867 |
| 2025-01 | 70 | 25 | -225,049 | 0 | -80,026 | -39,102 |
| 2025-02 | 22 | 11 | -4,766 | -0 | 12,022 | 25,807 |
| 2025-03 | 22 | 11 | -363,909 | 0 | -145,293 | 0 |
| 2025-04 | 18 | 8 | -68,492 | -0 | -55,614 | 0 |
| 2025-05 | 21 | 13 | 128,399 | -0 | 201 | 0 |
| 2025-06 | 24 | 11 | -148,569 | 0 | 75,362 | 0 |
| 2025-07 | 26 | 10 | -33,656 | 0 | 0 | 0 |
| 2025-08 | 26 | 13 | 8,513 | -0 | -14,396 | 0 |
| 2025-09 | 47 | 17 | -44,612 | 0 | 4,155 | 0 |
| 2025-10 | 42 | 12 | -175,676 | 0 | 3,672 | 0 |
| 2025-11 | 80 | 19 | -221,269 | 0 | -74,588 | 0 |
| 2025-12 | 54 | 10 | -23,682 | 0 | 23,103 | 0 |
| 2026-01 | 85 | 14 | 299,063 | 0 | 78,933 | 32,813 |

What the 'drawdown when a regime ends' looks like: the worst months at full size were 2024-07 (-740k: edges that had been ON from the April-May 2024 run reversed together), 2025-03 (-364k), 2024-03 (-292k), 2025-10 (-176k), 2025-11 (-221k). Each of these is a month in which many ON edges, chosen at the start of the month, stopped together; the per-edge STOPPED flag of the monitor arrives about 4 weeks after such a break (DS3_EDGE_MONITOR.md).

## 3. The ledger as of 2026-02-06 and how it would be run today

69 S73-base edges are ON (positive 13- and 26-week mean) at the last data week; 35 are cluster representatives. Their persistence (noise-adjusted first pass): >= 0.5: 7, >= 0.6: 1, >= 0.7: 0. Shrunk expectation and Kelly fraction are 0 for all of them (the earlier-month ratio forward/trailing is negative for each group). In-sample windows below: the ledger was chosen with the data it is scored on, so L3M and L6M are not out-of-sample; PRE and X' show what the same set did before it was chosen.

Joint lock-engine run of the representatives (delta vs the plain stack, research lots, $/wk; SD and drawdown of the weekly delta; w20 = sum of the 20 worst weeks of the window, so in L3M and L6M it is the sum of all negative-prone weeks of that window):

| set | size | window | mean $/wk | MDE | live A | SD | max DD $ | worst-20-week sum $ | weeks |
|---|---|---|---|---|---|---|---|---|---|
| all reps | full | L3M | 63,709 | 82,654 | 27,110 | 110,451 | 180,489 | 891,929 | 14 |
| all reps | full | L6M | 8,930 | 68,409 | 3,800 | 129,280 | 888,150 | -1,040,348 | 28 |
| all reps | full | PRE | -57,668 | 38,873 | -24,539 | 120,232 | 4,691,528 | -3,853,392 | 75 |
| all reps | full | X | -8,770 | 39,853 | -3,732 | 94,412 | 769,684 | -1,957,215 | 44 |
| all reps | full | ALL | -28,154 | 28,044 | -11,980 | 122,256 | 5,535,775 | -4,212,033 | 149 |
| all reps | half | L3M | 45,216 | 77,033 | 19,241 | 102,940 | 162,219 | 633,022 | 14 |
| all reps | half | L6M | 11,446 | 56,746 | 4,871 | 107,241 | 677,534 | -801,555 | 28 |
| all reps | half | PRE | -44,488 | 29,037 | -18,931 | 89,809 | 3,548,898 | -2,905,138 | 75 |
| all reps | half | X | -3,117 | 29,963 | -1,327 | 70,983 | 520,476 | -1,404,059 | 44 |
| all reps | half | ALL | -20,101 | 21,503 | -8,553 | 93,742 | 4,112,778 | -3,111,518 | 149 |
| padj>=0.5 | full | L3M | 19,112 | 73,611 | 8,133 | 98,367 | 327,700 | 267,574 | 14 |
| padj>=0.5 | full | L6M | 8,120 | 54,189 | 3,455 | 102,409 | 733,021 | -911,606 | 28 |
| padj>=0.5 | full | PRE | -31,028 | 26,507 | -13,203 | 81,984 | 2,416,554 | -2,483,246 | 75 |
| padj>=0.6 | full | L3M | 878 | 2,459 | 374 | 3,286 | 0 | 12,297 | 14 |
| padj>=0.6 | full | L6M | 447 | 1,258 | 190 | 2,378 | 1,765 | -1,765 | 28 |
| padj>=0.6 | full | PRE | 85 | 698 | 36 | 2,158 | 10,999 | -18,228 | 75 |

Reading: run in full, today's ledger would have added +64k/wk (MDE 83k) in L3M, +9k (68k) in L6M, and lost 58k/wk (MDE 39k) in PRE (2024-02..2025-06) and 9k/wk in X'. That is the recent-regime shape in one line. Half size halves the swings, not the sign.

### The independent effects behind the 35 representatives (the same regime in different clothes)

Weekly correlation of eight named edges (all 149 weeks above the diagonal, last 52 weeks below):

| | FS cut P50 | FS Asia | FS opp>=1 | ER sizer | skip 60min | skip after loser | pre cap 8 | SM x1.5 |
|---|---|---|---|---|---|---|---|---|
| FS cut P50 | 1 | 0.76 | 0.59 | 0.29 | 0.27 | 0.17 | 0.08 | 0.01 |
| FS Asia | 0.82 | 1 | 0.54 | 0.33 | 0.21 | 0.18 | 0.04 | 0.04 |
| FS opp>=1 | 0.47 | 0.42 | 1 | 0.14 | 0.17 | 0.02 | 0.07 | -0.06 |
| ER sizer | 0.39 | 0.36 | 0.08 | 1 | 0.37 | 0.22 | 0.32 | -0.05 |
| skip 60min | 0.22 | 0.27 | 0.08 | 0.42 | 1 | 0.22 | 0.36 | -0.10 |
| skip after loser | 0.04 | 0.09 | -0.15 | 0.26 | 0.21 | 1 | 0.03 | 0.02 |
| pre cap 8 | 0.04 | 0.02 | 0.02 | 0.33 | 0.36 | 0.08 | 1 | -0.08 |
| SM x1.5 | 0.18 | 0.19 | 0.12 | -0.03 | -0.05 | 0.00 | 0.05 | 1 |

Clusters found among the 69 ON edges (weekly correlation >= 0.8 over the last 52 weeks): about 3 effects. (i) **'Cut the other books when the first one stops'** - P25/P50/P75/P100, with or without a window since entry, rearm, block re-entry for the hour, stopped-session filters, ER/vol-tercile filters: about 25 of these variants correlate 0.7-0.84 over all weeks and are ONE effect with different gating; the Asia, opposite-books and ER>=0.4 gates are thinner versions of it. (ii) **'Pre-session same-side cap'** - ten cap variants and 'session pre OFF' are one effect. (iii) **'Trade less at the open / after losses'** - skip-first-30, skip-first-60, and the session first-hour skips are variants of one idea (0.81 weekly correlation between skip-30 and skip-60); the ER sizer is a separate effect (see the matrix for how weakly related). The 35-representative portfolio is therefore closer to 4 bets than 35.

## 4. Equal-risk frame (STRUCTURE)

STRUCTURE label: each representative is scaled to the median weekly SD of the set and the 35 are averaged (a pure re-weighting of the stored deltas, no engine run; it equalises the risk the variants contribute, it does not create information). The equal-risk sleeve earns 11,110 $/wk in L3M, 4,734 in L6M, -3,094 in PRE, -800 over all weeks (research-lot dollars of the median edge's risk; live A /2.35). It has the same sign pattern as the full-size run: positive only in the last two windows.

## 5. What the user can do with this

* The walk-forward test of 'find what works now, size it, drop it when it stops' says: with the discipline available on this box (positive 13/26 weeks, one per cluster, monitor), the approach lost money in 2024 and 2025 and gained in January 2026. The gain in the most recent window is real in the numbers but is the same on any ON edge; it is not evidence that the approach selects edges that will pay next.
* Prefer SHADOW for every recent-only edge, with the monitor's status as the dashboard. The one S2 edge that is positive in every window and every basis (first-stop cut when a book is open on the other side, LEAD) can run at a small fixed fraction; its numbers are in DS3_RECENT_EDGE_FINAL.md.
* Re-run: `python3 -I l2vast/ds3/code/recentedge2/re2_portfolio.py` (4 min, 3 workers) then re2_portfolio_eval.py, re2_portfolio_latest.py, re2_mkportfolio.py.