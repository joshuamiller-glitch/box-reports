# SELECTION_RULE_BAKEOFF - walk five selection rules forward through history (W-BAKEOFF, 2026-11-25 21:33Z)

## Answer first

- WINNER OVERALL (drawdown first, 2-week steps, whole out-of-sample Oct 2023 - Oct 2026): **R1 CURRENT** for both summed calendars (SUM-A ulcer 38,072 vs bare 45,001; SUM-B 25,345 vs bare 42,048) and for NY AM nine, NY AM eight and London individually. It also wins the summed calendars at 4-week and 6-week steps. No filtered/blended/ensemble rule beat it on the summed curve.
- WINNER PER SESSION (whole OOS, 2-week): Asia = R2 filter-then-rank (ulcer 6,637 vs R1 7,609, -13%); NY AM = R1 (nine and eight); NY PM = mixed, no clear winner (primary STKd8w42pm R4 blend 38,853 vs R1 43,126; all-history R3 24m; equal R4; delivered four R3 12m; bare is already within 1% of the best on the all-history stack); London = R1 (23,788 vs R2/R4/R5 about 32,600-34,100 and R3 3m 28,495).
- RECENT (last 6 and 3 months of the OOS curve): the filter rules look better than R1 on the summed curve (SUM-A L6M ulcer R2 10,047 / R4 9,132 vs R1 13,938; L3M R1 6,009 beats R2 12,286). That is mostly because after a prior-year filter very few combos survive, so R2..R5 sit on the same one combo or on bare (in London and NY PM the filtered rules equal bare for the whole last 6 months; pick = bare 14-36% of steps). The L6M window is also the window the candidate menu was built on (look-ahead, see below), so recent columns favour any rule that parks on the L6M-fitted combo.
- THE FILTER DOES NOT BUY WHAT IT WAS MEANT TO: whole-OOS the filtered rules (R2..R5) mostly have a HIGHER ulcer and deeper max DD than R1 (e.g. NY AM eight R1 36,854 vs R3 12m/R3 24m/R4 about 59,000-68,000 at 4-6 week steps; London R1 23,788 vs R2 32,634). They pick less often changed (R2 about 10-16% vs R1 36-38% of steps), but a stable pick is not a better pick here.
- INCOME AT EQUAL RISK: every drawdown-first rule, R1 included, pays for the lower drawdown with income. At the risk (ulcer) of bare, R1 earns $9,641/wk on NY AM nine vs bare $18,973, $11,480 vs 18,858 (eight), $18,042 vs $39,693 summed (SUM-A), $23,360 vs $31,560 (SUM-B), London $1,955 vs $3,298, NY PM primary $5,262 vs $12,258. Only Asia (R2 $3,962 equal-risk vs bare $5,164) and NY PM all-history (R1 $798 vs bare $1,107, where bare is already near the best ulcer) come relatively close; NY PM equal is worse ($480 vs $1,284). So against bare the picks cut DD by 35-45% but not at a better return per unit of risk in this out-of-sample walk; this is before the look-ahead flatters the menu.
- NOISE: LUCK-COMPATIBLE everywhere. Block bootstrap over the steps (reality-check style, paying for the best of 7 rows): p(best of 7 beats R1 on ulcer) is 0.15-0.98 for every stack and sum (smallest: NY PM equal 0.15, Asia 0.47); the one clearly separated pair is SUM-B, where R1 beats every other rule (P(rule lower ulcer than R1) 0.00-0.02) and NY AM eight (R4/R3 24m worse than R1 in 97-99% of draws). R1 being best is therefore the one statement the data support; any claim that R2..R5 beat R1 is inside noise. With 80 two-week steps, 7 rule rows and a menu built on the last 6 months, treat differences under about 20% on ulcer as not distinguishable.
- RECOMMENDATION TO THE LEAD (no gate changes made): the walk-forward does not support replacing R1 with a prior-year filter, window change, blend or ensemble as a SELECTION rule on this data; keep R1 and use the prior-year band as a visible flag (it is the rule Josh set, but as a hard filter it removed the best OOS combos). The honest limitation is the menu look-ahead: a clean test needs menus built only from data before each date (new engine runs; see the mix/menu section).

## What the OOS windows cannot tell
- The first three months (Oct-Dec 2023) have no prior calendar year: filter inactive. 2024 uses only 2023 (Apr-Dec). So the filter is a 2024-onwards effect and has seen only 1-3 prior years.
- Every candidate menu was ranked on L6M (May-Oct 2026): per-factor top-2 levels, OA over them. A rule that picks the L6M-best combo in 2024 is picking from a menu that already knows 2026. That affects R1..R5 alike.


Order: Josh 25 Nov 21:03Z / 21:18Z (option A), DIRECTIVE_20261125_2120Z_SELECTION_RULE_BAKEOFF.md. Research only; nothing live changes from this page. Read-only computation on stored month rows (no new engine runs). Does not duplicate PICKS_PRIOR_YEAR_FILTERED.md.

## Method and handling (read first)

- Data: the engine month dirs hold DAILY results (date x p484), so the finest honest step is one trading day; the steps tested are 2 weeks (primary), 4 and 6 weeks. 42 months per stack: 202304..202610 with 202511 absent for every stack (no data that month). All eight joints are complete (no missing month). Daily P&L is zero-filled on the weekdays of the existing months; ulcer, max DD, worst week (ISO week) use the same definitions as wf_gate / P.stats (RMS drawdown of cumulative daily P&L).
- Steps: first pick date 2023-10-02 (6 months of history exist), then every 2 / 4 / 6 weeks to 2026-10-30: 80 / 40 / 27 steps. Each rule picks with ONLY days before the date, and the pick is scored on the NEXT step; next-step results are chained into one out-of-sample curve per rule (about 3.1 years).
- Candidate pool = the landed joint of the stack: 80 combos + bare (Asia and NY PM four: the R200 joint at the 2-lot basis the fits use; NY AM nine and eight: all 242 combos, plus the first-80 OA subset JT1..JT80 shown as a check; NY PM and London: the 80 at 1 lot). Bare = the truly bare base of the stack at that basis (it is always a legal pick: the fallback).
- R1: best L6M by ulcer (drawdown first) among combos inside the page guard (ulcer below bare, worst week and max DD each not more than 15% worse than bare), else bare. R2: R1 after dropping every combo that lost money OR was RED (equal-risk $/wk shortfall vs bare > 30%, wf_gate year_band) in any calendar year fully before the date. R3: R2 with lookback 3, 12, 24 months (windows truncated to the available data early on). R4: R2 filter, score = 0.5 x last 6 months + 0.5 x all older months (ulcer, max DD, worst week and $/wk each blended; guard on the blended numbers; blend = 6M only while fewer than 20 older days exist). R5: R2 filter + guard, top 10 by L6M ulcer, per-factor most common level (ties to the milder: level 0 = bare setting, then 1, then 2), exact combo if run, else the NEAREST run combo (fewest factors different, ties lower L6M ulcer) among the filter-passing combos. R5 exact-match rate is reported per stack.
- HANDLING OF EARLY DATES (one choice): at a date with no calendar year fully before it (2023-10 to 2023-12) the prior-year filter is INACTIVE, so R2..R5 behave as R1 with their own window/blend/ensemble (they are not dropped from the score; the whole window is common to all rules). From 2024-01 the filter uses 2023 (Apr-Dec, partial), from 2025-01 2023-2024, from 2026-01 2023-2025. The by-year rows show what each rule did once the filter was live.
- Reference rows: bare, and the FIXED PICK (the combo each page shows as the best joint today: AS JT210, NY9 JT91, NY8 JT154, NP JT19, NPB JT19, NPE JT9, NP4 JT209, LO JT4) held through all of history. The fixed pick was chosen with L6M knowledge, so it is a hindsight row, not a rule.
- LOOK-AHEAD WARNING (applies to all rules): the 80 / 242 combos are built from the top-2 settings per factor ranked on L6M (May-Oct 2026), so every candidate menu already contains knowledge of the last six months. Earlier steps are therefore flattered or distorted for every rule alike; the comparison between rules is fair, the absolute $ and ulcer levels are optimistic. Only the L6M/L3M columns are fully in the fit window for the menu (and they are scored out-of-sample for the pick, but not for the menu).
- Dollars: whole-stack dollars at the stack basis the engine ran (1-lot units for the NY PM / London / NY AM joints as the pages show them, 2-lot basis for Asia and NY PM four). The summed calendar adds the four live-session stacks as they stand in the pool (Asia + NY AM nine + NY PM primary + London = SUM-A; alt SUM-B = Asia + NY AM eight + NY PM four + London); different bases are added as-is, so the sum is dominated by the largest-dollar stack (NY AM). Each session's rule is applied separately, then the out-of-sample curves are added.


## Winner table (2-week steps, drawdown first = lowest whole-OOS ulcer among the 7 rule rows)

| stack | whole-OOS winner | its ulcer / DD / $/wk | R1 ulcer / DD / $/wk | bare ulcer / DD / $/wk | winner on L6M | winner on L3M | equal-risk $/wk: winner / R1 (at bare ulcer) |
|---|---|---|---|---|---|---|---|
| Asia STKd8da2eb47b (2-lot basis, joint JT201..280 = R200 refit) | R2 filter->rank | 6637 / -23563 / 2256 | 7609 / -23298 / 2391 | 11655 / -59220 / 5164 | R2 filter->rank | R2 filter->rank | 3962 / 3662 |
| NY AM nine STKd8cd0279ff (1 lot basis, all 242 combos) | R1 current | 34727 / -121005 / 6673 | 34727 / -121005 / 6673 | 50169 / -188315 / 18973 | R3 lookback 3m | R4 recency blend | 9641 / 9641 |
| NY AM eight STKd8w42 (all 242 combos) | R1 current | 36854 / -126661 / 8196 | 36854 / -126661 / 8196 | 51620 / -193440 / 18858 | R1 current | R1 current | 11480 / 11480 |
| NY PM primary STKd8w42pm | R4 recency blend | 38853 / -180947 / 6955 | 43126 / -149191 / 4923 | 46100 / -180947 / 12258 | R1 current | R1 current | 8252 / 5262 |
| NY PM all-history STKd8w42pmb | R3 lookback 24m | 7370 / -18748 / 786 | 7932 / -23561 / 865 | 7318 / -23907 / 1107 | R3 lookback 3m | R3 lookback 3m | 780 / 798 |
| NY PM equal STKd8w42pme | R4 recency blend | 7116 / -19413 / 789 | 11402 / -30955 / 699 | 7831 / -25100 / 1284 | R3 lookback 3m | R3 lookback 24m | 868 / 480 |
| NY PM delivered four STKd893133bd8 (2-lot basis, R200 joint) | R3 lookback 12m | 13796 / -49009 / 2467 | 15402 / -43528 / 2217 | 17582 / -58752 / 4240 | R3 lookback 12m | R2 filter->rank | 3144 / 2530 |
| London STKd8w42lo | R1 current | 23788 / -63690 / 1278 | 23788 / -63690 / 1278 | 36407 / -107674 / 3298 | R1 current | R1 current | 1955 / 1955 |
| SUM-A (AS + NY9 + NP + LO) | R1 current | 38072 / -158309 / 15264 | 38072 / -158309 / 15264 | 45001 / -244753 / 39693 | R4 recency blend | R1 current | 18042 / 18042 |
| SUM-B (AS + NY8 + NP4 + LO) | R1 current | 25345 / -104228 / 14081 | 25345 / -104228 / 14081 | 42048 / -170907 / 31560 | R1 current | R1 current | 23360 / 23360 |

Whole-OOS winner count over the eight stacks: R1 current 3, R2 filter->rank 1, R3 lookback 12m 1, R3 lookback 24m 1, R4 recency blend 2. Rows with identical ulcer to bare mean the rule sat in bare for the whole stretch (see "pick = bare" shares).

## Noise check (block bootstrap of the steps, 1000 draws, blocks of 3 steps; reality-check style on ulcer)

p(best of 7) = probability that the BEST of the 7 rule rows would beat the benchmark by at least the observed margin on ulcer if no rule had an edge (differences re-centred at zero over the 7 rows, so it already pays for choosing the best of 7). P(rule < R1) = share of bootstrap curves where that rule has lower ulcer than R1. Label: LUCK-COMPATIBLE if p(best of 7) > 0.10, WEAK if 0.05-0.10, LIKELY REAL if < 0.05.

| stack / sum | best row (ulcer) | its ulcer vs R1 | p(best of 7) vs R1 | best row vs bare | p(best of 7) vs bare | label vs R1 |
|---|---|---|---|---|---|---|
| Asia STKd8da2eb47b | R2 filter->rank (6637) | -13% | 0.47 | R2 filter->rank (6637 vs bare 11655) | 0.18 | LUCK-COMPATIBLE |
| NY AM nine STKd8cd0279ff | R2 filter->rank (35414) | +2% | 0.79 | R1 current (34727 vs bare 50169) | 0.35 | LUCK-COMPATIBLE |
| NY AM eight STKd8w42 | R5 ensemble (42665) | +16% | 0.90 | R1 current (36854 vs bare 51620) | 0.40 | LUCK-COMPATIBLE |
| NY PM primary STKd8w42pm | R4 recency blend (38853) | -10% | 0.29 | R4 recency blend (38853 vs bare 46100) | 0.56 | LUCK-COMPATIBLE |
| NY PM all-history STKd8w42pmb | R3 lookback 24m (7370) | -7% | 0.72 | R3 lookback 24m (7370 vs bare 7318) | 0.67 | LUCK-COMPATIBLE |
| NY PM equal STKd8w42pme | R4 recency blend (7116) | -38% | 0.15 | R4 recency blend (7116 vs bare 7831) | 0.92 | LUCK-COMPATIBLE |
| NY PM delivered four STKd893133bd8 | R3 lookback 12m (13796) | -10% | 0.48 | R3 lookback 12m (13796 vs bare 17582) | 0.34 | LUCK-COMPATIBLE |
| London STKd8w42lo | R3 lookback 3m (28495) | +20% | 0.88 | R1 current (23788 vs bare 36407) | 0.12 | LUCK-COMPATIBLE |
| SUM-A | R3 lookback 12m (39794) | +5% | 0.74 | R1 current (38072 vs bare 45001) | 0.73 | LUCK-COMPATIBLE |
| SUM-B | R5 ensemble (36701) | +45% | 0.98 | R1 current (25345 vs bare 42048) | 0.15 | LUCK-COMPATIBLE |

Per-rule P(ulcer lower than R1) in the bootstrap, by stack: 

| stack | R2 filter->rank | R3 lookback 3m | R3 lookback 12m | R3 lookback 24m | R4 recency blend | R5 ensemble |
|---|---|---|---|---|---|---|
| Asia STKd8da2eb47b | 0.56 | 0.40 | 0.51 | 0.39 | 0.59 | 0.45 |
| NY AM nine STKd8cd0279ff | 0.46 | 0.34 | 0.48 | 0.46 | 0.32 | 0.10 |
| NY AM eight STKd8w42 | 0.19 | 0.15 | 0.03 | 0.01 | 0.01 | 0.17 |
| NY PM primary STKd8w42pm | 0.35 | 0.29 | 0.46 | 0.40 | 0.49 | 0.38 |
| NY PM all-history STKd8w42pmb | 0.64 | 0.53 | 0.42 | 0.72 | 0.50 | 0.61 |
| NY PM equal STKd8w42pme | 0.85 | 0.78 | 0.78 | 0.59 | 0.89 | 0.89 |
| NY PM delivered four STKd893133bd8 | 0.36 | 0.59 | 0.63 | 0.53 | 0.46 | 0.50 |
| London STKd8w42lo | 0.09 | 0.14 | 0.09 | 0.07 | 0.07 | 0.08 |
| SUM-A | 0.32 | 0.23 | 0.38 | 0.32 | 0.26 | 0.07 |
| SUM-B | 0.01 | 0.01 | 0.00 | 0.00 | 0.00 | 0.02 |

## Four sessions summed on one calendar

### SUM-A: Asia STKd8da2eb47b + NY AM nine STKd8cd0279ff + NY PM primary STKd8w42pm + London STKd8w42lo

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 19672 / -71054 / -11515 / -70152 / 82388 | 17030 / -75220 / -11515 / -75220 / 104657 | 45001 / -244753 / -113844 / -92741 / 39693 | 64185 / -244753 / -98796 / -75220 / 69500 | 38865 / -170066 / -113844 / -92741 / 35947 | 31412 / -96166 / -78557 / -50510 / 19851 | 19132 / -52326 / -41347 / -33421 / 34051 |
| fixed pick today (ref, hindsight) | 6379 / -19784 / -4440 / -17290 / 38700 | 8988 / -33067 / -10588 / -27633 / 45444 | 24920 / -93526 / -69571 / -41707 / 15699 | 24436 / -93526 / -41631 / -27633 / 31323 | 25970 / -90602 / -69571 / -41707 / 10465 | 18458 / -61368 / -35954 / -31219 / 10207 | 32274 / -54926 / -35389 / -22545 / 5083 |
| R1 current **(winner whole OOS)** | 6009 / -31264 / -2690 / -22416 / 38155 | 13938 / -53008 / -14567 / -31981 / 35880 | 38072 / -158309 / -50777 / -46676 / 15264 | 51304 / -158309 / -42048 / -31981 / 23153 | 26790 / -96559 / -43611 / -42628 / 14787 | 25939 / -101921 / -50777 / -46676 / 9494 | 15204 / -35451 / -22557 / -25569 / 13953 |
| R2 filter->rank | 12286 / -40928 / -8470 / -40928 / 65190 | 10047 / -40928 / -8470 / -40928 / 82298 | 40915 / -199918 / -63830 / -57520 / 23431 | 60022 / -199918 / -54279 / -57520 / 51127 | 26980 / -115611 / -63830 / -44204 / 16018 | 28400 / -105908 / -57627 / -37713 / 9662 | 15204 / -35451 / -22557 / -25569 / 13953 |
| R3 lookback 3m | 12612 / -40928 / -8470 / -40928 / 64657 | 12895 / -61125 / -8470 / -44653 / 82207 | 55402 / -281801 / -76760 / -52801 / 23997 | 94852 / -281801 / -76760 / -50272 / 48772 | 24716 / -95744 / -59283 / -52801 / 18399 | 29730 / -102847 / -59531 / -40614 / 10854 | 16655 / -40965 / -30980 / -15173 / 15020 |
| R3 lookback 12m | 12286 / -40928 / -8470 / -40928 / 65190 | 10047 / -40928 / -8470 / -40928 / 82298 | 39794 / -199918 / -67751 / -57520 / 23097 | 60546 / -199918 / -54279 / -57520 / 49152 | 28661 / -114313 / -67751 / -48487 / 18779 | 22320 / -75399 / -55098 / -36027 / 7361 | 12503 / -29250 / -22452 / -21044 / 15551 |
| R3 lookback 24m | 12286 / -40928 / -8470 / -40928 / 65190 | 10047 / -40928 / -8470 / -40928 / 82298 | 48625 / -255512 / -71990 / -50272 / 22130 | 82256 / -255512 / -71990 / -50272 / 47968 | 22044 / -74177 / -61821 / -44428 / 14893 | 23454 / -75399 / -55098 / -36027 / 9018 | 12503 / -29250 / -22452 / -21044 / 15551 |
| R4 recency blend | 10750 / -40928 / -8470 / -40928 / 67904 | 9132 / -40928 / -8470 / -40928 / 83645 | 50258 / -259388 / -76760 / -50272 / 21914 | 84184 / -259388 / -76760 / -50272 / 48692 | 22211 / -71910 / -69324 / -45268 / 14976 | 28827 / -99147 / -55098 / -36027 / 8347 | 12391 / -31006 / -15449 / -22978 / 12921 |
| R5 ensemble | 12286 / -40928 / -8470 / -40928 / 65190 | 10047 / -40928 / -8470 / -40928 / 82298 | 54985 / -255152 / -97088 / -61837 / 23711 | 82672 / -255152 / -76760 / -57520 / 49275 | 42303 / -127509 / -97088 / -61837 / 16759 | 36271 / -133685 / -63885 / -43973 / 12637 | 27170 / -60962 / -25583 / -23104 / 8773 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 76% ($ 26%) | 0% ($ 0%) | 36% | 0% |
| R2 filter->rank | 69% ($ 21%) | 31% ($ 54%) | 16% | 16% |
| R3 lookback 3m | 71% ($ 28%) | 36% ($ 59%) | 31% | 20% |
| R3 lookback 12m | 74% ($ 24%) | 39% ($ 56%) | 9% | 14% |
| R3 lookback 24m | 71% ($ 21%) | 35% ($ 54%) | 6% | 14% |
| R4 recency blend | 69% ($ 22%) | 38% ($ 51%) | 16% | 15% |
| R5 ensemble | 59% ($ 20%) | 25% ($ 61%) | 16% | 16% |
| fixed pick (ref) | 82% ($ 19%) | 57% ($ 49%) | - | - |

### SUM-B: Asia + NY AM eight STKd8w42 + NY PM four STKd893133bd8 + London

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 17669 / -80374 / -5031 / -77666 / 65776 | 16809 / -80374 / -5031 / -77666 / 88057 | 42048 / -170907 / -128156 / -90782 / 31560 | 43406 / -164958 / -87630 / -77666 / 61768 | 47965 / -160314 / -128156 / -90782 / 24183 | 33603 / -89947 / -74466 / -51347 / 15373 | 13335 / -35986 / -24703 / -33669 / 23303 |
| fixed pick today (ref, hindsight) | 6616 / -19604 / 1775 / -18865 / 33318 | 8531 / -32516 / -2360 / -18865 / 39616 | 29401 / -93281 / -55421 / -25314 / 12167 | 22857 / -77797 / -33868 / -21319 / 25759 | 25678 / -80349 / -55421 / -25314 / 8860 | 33380 / -89960 / -33962 / -24664 / 6248 | 15192 / -33105 / -18354 / -18838 / 2911 |
| R1 current **(winner whole OOS)** | 7641 / -24464 / 602 / -16481 / 30932 | 9734 / -30769 / -17828 / -21973 / 34435 | 25345 / -104228 / -50627 / -33868 / 14081 | 31158 / -101664 / -33181 / -28038 / 24480 | 22180 / -71359 / -50627 / -33232 / 12454 | 15632 / -49116 / -43594 / -33868 / 9320 | 35452 / -67665 / -28533 / -27712 / 4587 |
| R2 filter->rank | 18502 / -68029 / -2388 / -68029 / 57775 | 18576 / -72445 / -8720 / -72445 / 74731 | 37142 / -125605 / -96728 / -72445 / 24321 | 37551 / -122013 / -96728 / -72445 / 51014 | 41309 / -125605 / -75675 / -52689 / 16792 | 28921 / -84812 / -48711 / -43113 / 14034 | 35452 / -67665 / -28533 / -27712 / 4587 |
| R3 lookback 3m | 19292 / -74840 / -5992 / -74354 / 55824 | 19241 / -74840 / -8720 / -74354 / 71724 | 40497 / -170663 / -119517 / -74354 / 23342 | 40058 / -137343 / -103547 / -74354 / 48697 | 52846 / -170663 / -119517 / -65208 / 17211 | 27615 / -105398 / -81654 / -41282 / 12439 | 17368 / -41417 / -17710 / -24847 / 5372 |
| R3 lookback 12m | 18307 / -67320 / -2388 / -67320 / 57372 | 18357 / -71862 / -8720 / -71862 / 76460 | 52386 / -238397 / -74377 / -71862 / 22037 | 81689 / -238397 / -51233 / -71862 / 45440 | 45166 / -141726 / -74377 / -51875 / 16057 | 23780 / -75984 / -50910 / -43906 / 11324 | 14380 / -38552 / -14349 / -27288 / 9256 |
| R3 lookback 24m | 24537 / -86724 / -6467 / -74549 / 55416 | 22082 / -86724 / -7424 / -74549 / 74806 | 53038 / -230546 / -80013 / -74549 / 20232 | 80650 / -230546 / -51233 / -74549 / 44620 | 42609 / -130165 / -80013 / -51875 / 16084 | 34258 / -117090 / -46690 / -37261 / 6572 | 14380 / -38552 / -14349 / -27288 / 9256 |
| R4 recency blend | 21419 / -78165 / -2863 / -67515 / 56579 | 20067 / -78165 / -8720 / -72445 / 74147 | 51927 / -217982 / -75675 / -72445 / 20759 | 78050 / -217982 / -51233 / -72445 / 44399 | 41890 / -118749 / -75675 / -52689 / 16309 | 32938 / -104672 / -45995 / -44348 / 8868 | 22969 / -46050 / -21385 / -22309 / 6262 |
| R5 ensemble | 22396 / -78643 / -2863 / -67515 / 56734 | 20609 / -78643 / -9814 / -71477 / 75153 | 36701 / -151267 / -103078 / -71477 / 23954 | 36479 / -104468 / -103078 / -71477 / 50820 | 43436 / -151267 / -86148 / -51170 / 16098 | 28605 / -101767 / -87495 / -39722 / 12936 | 28742 / -57489 / -31352 / -24139 / 7797 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 74% ($ 26%) | 0% ($ 0%) | 38% | 0% |
| R2 filter->rank | 55% ($ 29%) | 16% ($ 57%) | 19% | 9% |
| R3 lookback 3m | 59% ($ 26%) | 22% ($ 61%) | 33% | 13% |
| R3 lookback 12m | 50% ($ 26%) | 16% ($ 61%) | 7% | 7% |
| R3 lookback 24m | 50% ($ 25%) | 16% ($ 56%) | 6% | 7% |
| R4 recency blend | 50% ($ 26%) | 19% ($ 55%) | 19% | 8% |
| R5 ensemble | 56% ($ 24%) | 24% ($ 65%) | 26% | 9% |
| fixed pick (ref) | 78% ($ 26%) | 48% ($ 48%) | - | - |

## Per stack, 2-week steps

### Asia STKd8da2eb47b (2-lot basis, joint JT201..280 = R200 refit)

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 6940 / -21112 / 911 / -13716 / 12075 | 5887 / -21112 / -10222 / -13716 / 14875 | 11655 / -59220 / -40559 / -18132 / 5164 | 12064 / -59220 / -40559 / -18132 / 11846 | 12510 / -32197 / -21095 / -14380 / 2613 | 11626 / -31565 / -14687 / -10781 / 2402 | 1646 / -5547 / -7272 / -4894 / 3450 |
| fixed pick today (ref, hindsight) | 1986 / -6473 / 505 / -4444 / 6033 | 2000 / -7552 / -4497 / -4501 / 7796 | 6503 / -23697 / -18200 / -9031 / 2398 | 5856 / -20289 / -9004 / -7477 / 5440 | 6521 / -23697 / -18200 / -9031 / 1124 | 7624 / -20744 / -9182 / -5528 / 1364 | 1571 / -3640 / -2167 / -2369 / 1137 |
| R1 current | 4527 / -14329 / -2900 / -7137 / 5774 | 3792 / -14329 / -4136 / -7137 / 6782 | 7609 / -23298 / -19654 / -8719 / 2391 | 5132 / -18719 / -8786 / -7613 / 5323 | 7052 / -21398 / -19654 / -7525 / 1078 | 10094 / -23298 / -11441 / -8719 / 1288 | 630 / -1822 / -1630 / -1819 / 1913 |
| R2 filter->rank **(winner whole OOS)** | 3151 / -10523 / -5182 / -4595 / 5656 | 2886 / -10523 / -5182 / -5585 / 7539 | 6637 / -23563 / -17511 / -9758 / 2256 | 4998 / -17567 / -7945 / -7531 / 5255 | 8059 / -23563 / -17511 / -6427 / 740 | 7068 / -19093 / -11782 / -9758 / 1252 | 630 / -1822 / -1630 / -1819 / 1913 |
| R3 lookback 3m | 3318 / -10523 / -5182 / -6706 / 5124 | 3849 / -17409 / -5182 / -12260 / 7949 | 7080 / -23563 / -17511 / -12260 / 2466 | 5376 / -17567 / -7945 / -12260 / 5502 | 7362 / -23563 / -17511 / -6438 / 1075 | 8647 / -20581 / -11782 / -9758 / 1499 | 815 / -1950 / -1230 / -1819 / 1380 |
| R3 lookback 12m | 3151 / -10523 / -5182 / -4595 / 5656 | 2886 / -10523 / -5182 / -5585 / 7539 | 7638 / -22841 / -16966 / -9758 / 2237 | 4998 / -17567 / -7945 / -7531 / 5277 | 7815 / -22808 / -16966 / -7199 / 828 | 9088 / -22020 / -11782 / -9758 / 1049 | 576 / -1822 / -1630 / -1819 / 2096 |
| R3 lookback 24m | 3151 / -10523 / -5182 / -4595 / 5656 | 2886 / -10523 / -5182 / -5585 / 7539 | 8731 / -25063 / -16966 / -9758 / 2198 | 4998 / -17567 / -7945 / -7531 / 5255 | 8443 / -21169 / -16966 / -7873 / 721 | 10405 / -24241 / -11782 / -9758 / 1049 | 576 / -1822 / -1630 / -1819 / 2096 |
| R4 recency blend | 3151 / -10523 / -5182 / -4595 / 5656 | 2886 / -10523 / -5182 / -5585 / 7539 | 6838 / -22107 / -17511 / -9758 / 2269 | 4998 / -17567 / -7945 / -7531 / 5255 | 8552 / -22107 / -17511 / -6756 / 621 | 7112 / -18097 / -11782 / -9758 / 1359 | 575 / -1822 / -1630 / -1819 / 2084 |
| R5 ensemble | 3151 / -10523 / -5182 / -4595 / 5656 | 2886 / -10523 / -5182 / -5585 / 7539 | 7698 / -27935 / -18299 / -9758 / 2291 | 4998 / -17567 / -7945 / -7531 / 5288 | 9291 / -27935 / -18299 / -8151 / 1056 | 8694 / -22546 / -11782 / -9758 / 1173 | 1021 / -3036 / -2790 / -2788 / 1368 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 88% ($ 30%) | 0% ($ 0%) | 38% | 0% |
| R2 filter->rank | 91% ($ 29%) | 49% ($ 42%) | 19% | 0% |
| R3 lookback 3m | 82% ($ 26%) | 51% ($ 50%) | 30% | 5% |
| R3 lookback 12m | 89% ($ 28%) | 49% ($ 52%) | 10% | 0% |
| R3 lookback 24m | 89% ($ 25%) | 44% ($ 52%) | 8% | 0% |
| R4 recency blend | 90% ($ 28%) | 50% ($ 50%) | 23% | 0% |
| R5 ensemble | 85% ($ 29%) | 48% ($ 46%) | 14% | 0% |
| fixed pick (ref) | 84% ($ 30%) | 52% ($ 50%) | - | - |

R5: exact combo existed on 22 of 80 steps where it picked (rest = nearest run combo; 0 steps had no candidate and fell to bare).

### NY AM nine STKd8cd0279ff (1 lot basis, all 242 combos)

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 29290 / -99970 / -16356 / -77369 / 36277 | 28581 / -99970 / -20048 / -83394 / 52932 | 50169 / -188315 / -117277 / -83394 / 18973 | 40180 / -131451 / -90354 / -83394 / 37130 | 60116 / -188315 / -117277 / -82641 / 16374 | 41131 / -109316 / -87056 / -58165 / 7944 | 29125 / -61918 / -35275 / -34788 / 12456 |
| fixed pick today (ref, hindsight) | 8365 / -21737 / -1575 / -11284 / 10992 | 9465 / -25973 / -7960 / -15186 / 17919 | 31127 / -101447 / -38918 / -20923 / 7196 | 25797 / -79990 / -38918 / -16978 / 12159 | 22514 / -65610 / -27725 / -20923 / 6716 | 12376 / -44894 / -32282 / -18514 / 6083 | 60030 / -93616 / -19952 / -14683 / -3101 |
| R1 current **(winner whole OOS)** | 15022 / -36606 / -33040 / -31929 / 11327 | 45427 / -110427 / -48374 / -31929 / 12194 | 34727 / -121005 / -48374 / -39909 / 6673 | 53390 / -121005 / -48374 / -31929 / 8394 | 21481 / -64948 / -34113 / -24457 / 8440 | 20643 / -64979 / -36359 / -39909 / 3948 | 23644 / -49709 / -28498 / -27291 / 5365 |
| R2 filter->rank | 13086 / -46899 / -8939 / -36137 / 25497 | 14679 / -52244 / -17099 / -40178 / 37909 | 35414 / -112525 / -73410 / -40178 / 11686 | 30993 / -112525 / -73410 / -40178 / 25389 | 30594 / -102072 / -47358 / -36267 / 9627 | 39887 / -105525 / -43407 / -29923 / 3799 | 23644 / -49709 / -28498 / -27291 / 5365 |
| R3 lookback 3m | 13086 / -46899 / -8939 / -36137 / 25497 | 12723 / -46899 / -8939 / -40178 / 37408 | 44299 / -175141 / -47358 / -40178 / 11189 | 54526 / -175141 / -38424 / -40178 / 22795 | 32144 / -111607 / -47358 / -36267 / 11125 | 45889 / -126965 / -43407 / -27701 / 3463 | 22991 / -37624 / -24393 / -14848 / 3814 |
| R3 lookback 12m | 13086 / -46899 / -8939 / -36137 / 25497 | 14679 / -52244 / -17099 / -40178 / 37909 | 38162 / -124388 / -73410 / -40178 / 11793 | 35433 / -112525 / -73410 / -40178 / 23408 | 31374 / -99731 / -47358 / -37985 / 12612 | 41226 / -124388 / -43407 / -34521 / 2865 | 23503 / -49709 / -28498 / -27291 / 5970 |
| R3 lookback 24m | 13086 / -46899 / -8939 / -36137 / 25497 | 14679 / -52244 / -17099 / -40178 / 37909 | 35684 / -163076 / -52147 / -40178 / 11026 | 49999 / -163076 / -52147 / -40178 / 22247 | 28082 / -97504 / -46962 / -37985 / 8832 | 22891 / -75148 / -43407 / -34521 / 5005 | 23503 / -49709 / -28498 / -27291 / 5970 |
| R4 recency blend | 7966 / -32899 / -8939 / -32899 / 28212 | 12728 / -52244 / -17099 / -40178 / 39256 | 42023 / -166953 / -52147 / -40178 / 10647 | 51512 / -166953 / -52147 / -40178 / 22971 | 28082 / -97504 / -46962 / -37985 / 8832 | 34129 / -94933 / -43407 / -34521 / 3860 | 32233 / -63235 / -28498 / -27291 / 3594 |
| R5 ensemble | 13086 / -46899 / -8939 / -36137 / 25497 | 14679 / -52244 / -17099 / -40178 / 37909 | 57041 / -166953 / -73410 / -46948 / 11169 | 50961 / -166953 / -73410 / -40178 / 23663 | 58452 / -163118 / -67724 / -46948 / 10101 | 38991 / -107383 / -57357 / -35150 / 4302 | 38826 / -86432 / -26356 / -15760 / 1105 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 78% ($ 36%) | 0% ($ 0%) | 35% | 0% |
| R2 filter->rank | 85% ($ 34%) | 34% ($ 50%) | 19% | 0% |
| R3 lookback 3m | 84% ($ 32%) | 44% ($ 56%) | 35% | 2% |
| R3 lookback 12m | 88% ($ 31%) | 41% ($ 57%) | 11% | 0% |
| R3 lookback 24m | 84% ($ 30%) | 42% ($ 54%) | 3% | 0% |
| R4 recency blend | 84% ($ 29%) | 40% ($ 51%) | 13% | 0% |
| R5 ensemble | 76% ($ 30%) | 31% ($ 54%) | 15% | 0% |
| fixed pick (ref) | 84% ($ 34%) | 56% ($ 50%) | - | - |

R5: exact combo existed on 26 of 80 steps where it picked (rest = nearest run combo; 0 steps had no candidate and fell to bare).

Check, first-80 OA subset (JT1..JT80) only, 2-week steps, whole OOS: 

| rule | whole OOS ulcer / DD / worst wk / worst day / $/wk | L6M |
|---|---|---|
| bare (ref) | 50169 / -188315 / -117277 / -83394 / 18973 | 28581 / -99970 / -20048 / -83394 / 52932 |
| R1 current | 30560 / -84674 / -57083 / -39909 / 7428 | 23361 / -59143 / -29013 / -17816 / 15725 |
| R2 filter->rank | 36502 / -175061 / -90354 / -83394 / 15292 | 21335 / -93632 / -20048 / -83394 / 53762 |
| R3 lookback 3m | 44555 / -193700 / -51401 / -83394 / 13009 | 23627 / -99970 / -16356 / -83394 / 47166 |
| R3 lookback 12m | 47187 / -195007 / -51401 / -83394 / 13461 | 28581 / -99970 / -20048 / -83394 / 52932 |
| R3 lookback 24m | 44304 / -195007 / -56853 / -33250 / 7301 | 22589 / -71858 / -56853 / -26151 / 16814 |
| R4 recency blend | 45526 / -195007 / -56853 / -83394 / 12393 | 23294 / -93632 / -56853 / -83394 / 48890 |
| R5 ensemble | 68685 / -204230 / -90354 / -83394 / 12420 | 21335 / -93632 / -20048 / -83394 / 53762 |

### NY AM eight STKd8w42 (all 242 combos)

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 28739 / -97355 / -9208 / -80574 / 35029 | 27178 / -97355 / -15764 / -81333 / 53077 | 51620 / -193440 / -125371 / -81333 / 18858 | 38506 / -124946 / -112083 / -81333 / 37139 | 60579 / -193440 / -125371 / -80761 / 16238 | 48642 / -127211 / -87760 / -65939 / 7863 | 29116 / -62879 / -30511 / -29510 / 11859 |
| fixed pick today (ref, hindsight) | 10716 / -32268 / -17735 / -18671 / 13631 | 14720 / -46473 / -17735 / -18671 / 19744 | 43561 / -124226 / -44902 / -23422 / 5262 | 46798 / -124226 / -44902 / -23422 / 10757 | 25794 / -77811 / -37592 / -18317 / 5819 | 38006 / -99980 / -40524 / -20340 / 2261 | 43239 / -65542 / -27013 / -15305 / -3058 |
| R1 current **(winner whole OOS)** | 12781 / -35319 / -24092 / -21129 / 13204 | 16456 / -53952 / -24092 / -21129 / 18675 | 36854 / -126661 / -45410 / -30519 / 8196 | 39856 / -126661 / -45410 / -23863 / 12879 | 27437 / -81575 / -37960 / -24948 / 8610 | 18123 / -50445 / -40959 / -30519 / 6095 | 60800 / -105988 / -29167 / -27686 / -503 |
| R2 filter->rank | 28171 / -97163 / -12054 / -73539 / 36045 | 26874 / -97163 / -18155 / -81333 / 52043 | 47321 / -129614 / -117036 / -81333 / 17631 | 36365 / -119285 / -117036 / -81333 / 36423 | 45490 / -129614 / -68757 / -46422 / 13075 | 34147 / -90289 / -52725 / -41122 / 10758 | 60800 / -105988 / -29167 / -27686 / -503 |
| R3 lookback 3m | 28739 / -97355 / -9208 / -80574 / 35029 | 28009 / -97355 / -18155 / -81333 / 48065 | 45387 / -182357 / -117036 / -81333 / 16321 | 38283 / -119285 / -117036 / -81333 / 33628 | 57971 / -182357 / -112628 / -56910 / 13076 | 31386 / -108833 / -88384 / -42229 / 8882 | 41722 / -75598 / -15674 / -27846 / 562 |
| R3 lookback 12m | 28171 / -97163 / -12054 / -73539 / 36045 | 26874 / -97163 / -18155 / -81333 / 52043 | 54971 / -236694 / -70371 / -81333 / 15283 | 79000 / -236694 / -70371 / -81333 / 30049 | 45907 / -137292 / -68757 / -44102 / 13042 | 38849 / -111059 / -52725 / -41122 / 7905 | 24373 / -56144 / -19627 / -27686 / 4033 |
| R3 lookback 24m | 31937 / -105722 / -20693 / -80574 / 35274 | 29332 / -105722 / -20693 / -81333 / 51968 | 59036 / -236694 / -70371 / -81333 / 13942 | 79136 / -236694 / -70371 / -81333 / 30116 | 45907 / -137292 / -68757 / -44102 / 13042 | 53665 / -146876 / -52725 / -38814 / 3832 | 24373 / -56144 / -19627 / -27686 / 4033 |
| R4 recency blend | 28171 / -97163 / -12054 / -73539 / 36045 | 26874 / -97163 / -18155 / -81333 / 52043 | 66062 / -224130 / -70371 / -81333 / 14383 | 76111 / -224130 / -70371 / -81333 / 30338 | 47827 / -137292 / -68757 / -46422 / 12878 | 59611 / -133507 / -52725 / -41122 / 5763 | 45940 / -81061 / -21676 / -23481 / 1441 |
| R5 ensemble | 28171 / -97163 / -12054 / -73539 / 36045 | 26874 / -97163 / -18155 / -81333 / 52043 | 42665 / -153389 / -117036 / -81333 / 17199 | 39085 / -119285 / -117036 / -81333 / 36197 | 48682 / -153389 / -75063 / -46422 / 12128 | 30916 / -99756 / -88384 / -42229 / 9793 | 48192 / -71279 / -31478 / -27033 / 2426 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 79% ($ 31%) | 0% ($ 0%) | 39% | 0% |
| R2 filter->rank | 60% ($ 38%) | 20% ($ 59%) | 19% | 0% |
| R3 lookback 3m | 55% ($ 34%) | 30% ($ 65%) | 33% | 10% |
| R3 lookback 12m | 56% ($ 39%) | 18% ($ 55%) | 6% | 0% |
| R3 lookback 24m | 52% ($ 34%) | 19% ($ 51%) | 9% | 0% |
| R4 recency blend | 56% ($ 38%) | 21% ($ 55%) | 18% | 0% |
| R5 ensemble | 55% ($ 38%) | 24% ($ 65%) | 28% | 0% |
| fixed pick (ref) | 81% ($ 30%) | 48% ($ 42%) | - | - |

R5: exact combo existed on 25 of 80 steps where it picked (rest = nearest run combo; 0 steps had no candidate and fell to bare).

Check, first-80 OA subset (JT1..JT80) only, 2-week steps, whole OOS: 

| rule | whole OOS ulcer / DD / worst wk / worst day / $/wk | L6M |
|---|---|---|
| bare (ref) | 51620 / -193440 / -125371 / -81333 / 18858 | 27178 / -97355 / -15764 / -81333 / 53077 |
| R1 current | 35397 / -121813 / -45410 / -32865 / 7869 | 17284 / -54232 / -35702 / -16866 / 16352 |
| R2 filter->rank | 55775 / -249256 / -112083 / -81333 / 17101 | 27178 / -97355 / -15764 / -81333 / 53077 |
| R3 lookback 3m | 49157 / -165925 / -112083 / -81333 / 16252 | 27968 / -97355 / -15764 / -81333 / 49194 |
| R3 lookback 12m | 53432 / -241320 / -70371 / -81333 / 15727 | 27178 / -97355 / -15764 / -81333 / 53077 |
| R3 lookback 24m | 61385 / -282249 / -70371 / -81333 / 14121 | 27178 / -97355 / -15764 / -81333 / 53077 |
| R4 recency blend | 55108 / -241320 / -70371 / -81333 / 15522 | 20056 / -87187 / -15764 / -81333 / 54028 |
| R5 ensemble | 57558 / -249256 / -112083 / -81333 / 14861 | 27178 / -97355 / -15764 / -81333 / 53077 |

### NY PM primary STKd8w42pm

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 46100 / -180947 / -61893 / -57520 / 12258 | 68381 / -180947 / -39779 / -41896 / 13877 | 25381 / -89607 / -61893 / -57520 / 15922 | 42410 / -130798 / -44940 / -37479 / 6942 | 17735 / -47876 / -27041 / -27941 / 14697 |
| fixed pick today (ref, hindsight) | 3912 / -12874 / -6184 / -11618 / 14084 | 5536 / -18074 / -17369 / -16450 / 13704 | 37044 / -101174 / -39678 / -30295 / 4780 | 31924 / -91090 / -25239 / -17343 / 8713 | 40185 / -101174 / -39678 / -30295 / 3873 | 29184 / -82569 / -23339 / -22926 / 2224 | 8697 / -26360 / -16178 / -12913 / 5315 |
| R1 current | 4186 / -13514 / -8023 / -11618 / 14047 | 8223 / -22533 / -8023 / -19332 / 12987 | 43126 / -149191 / -37600 / -25940 / 4923 | 46563 / -123043 / -36567 / -25940 / 6215 | 42524 / -114938 / -32146 / -24097 / 5109 | 17253 / -73750 / -37600 / -24626 / 3599 | 11466 / -25538 / -15724 / -13155 / 5250 |
| R2 filter->rank | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 41590 / -180947 / -39779 / -41896 / 7173 | 68394 / -180947 / -39779 / -41896 / 13835 | 27695 / -68503 / -21776 / -25008 / 5342 | 20367 / -92208 / -28595 / -27644 / 3816 | 11466 / -25538 / -15724 / -13155 / 5250 |
| R3 lookback 3m | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 43967 / -180947 / -39779 / -41896 / 7895 | 68397 / -180947 / -39779 / -41896 / 13827 | 35812 / -83344 / -31654 / -25008 / 5795 | 21708 / -92208 / -28595 / -31654 / 4808 | 8703 / -21392 / -10759 / -15781 / 8328 |
| R3 lookback 12m | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 39532 / -180947 / -39779 / -41896 / 7017 | 68394 / -180947 / -39779 / -41896 / 13835 | 21566 / -62882 / -31654 / -26351 / 5916 | 15802 / -65519 / -22611 / -25233 / 2641 | 10678 / -26573 / -15724 / -13155 / 5975 |
| R3 lookback 24m | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 41799 / -180947 / -39779 / -41896 / 6976 | 68394 / -180947 / -39779 / -41896 / 13835 | 32219 / -77529 / -31654 / -26351 / 5784 | 15802 / -65519 / -22611 / -25233 / 2641 | 10678 / -26573 / -15724 / -13155 / 5975 |
| R4 recency blend **(winner whole OOS)** | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 38853 / -180947 / -39779 / -41896 / 6955 | 68394 / -180947 / -39779 / -41896 / 13835 | 18890 / -50340 / -21776 / -24097 / 5556 | 14548 / -62349 / -22611 / -25233 / 2751 | 8973 / -22580 / -15724 / -13155 / 6123 |
| R5 ensemble | 10508 / -35805 / -7770 / -33004 / 24083 | 11696 / -55861 / -18817 / -41896 / 25748 | 40113 / -180947 / -40496 / -41896 / 7892 | 68459 / -180947 / -39779 / -41896 / 13677 | 18378 / -50340 / -31543 / -26538 / 5306 | 23828 / -90810 / -40496 / -31429 / 6352 | 14283 / -29903 / -17693 / -14716 / 4376 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 79% ($ 34%) | 0% ($ 0%) | 34% | 0% |
| R2 filter->rank | 54% ($ 28%) | 28% ($ 42%) | 14% | 28% |
| R3 lookback 3m | 50% ($ 24%) | 34% ($ 55%) | 28% | 34% |
| R3 lookback 12m | 54% ($ 24%) | 32% ($ 50%) | 9% | 28% |
| R3 lookback 24m | 56% ($ 24%) | 36% ($ 51%) | 9% | 28% |
| R4 recency blend | 56% ($ 24%) | 32% ($ 48%) | 8% | 28% |
| R5 ensemble | 52% ($ 25%) | 22% ($ 49%) | 13% | 28% |
| fixed pick (ref) | 86% ($ 36%) | 50% ($ 50%) | - | - |

R5: exact combo existed on 1 of 58 steps where it picked (rest = nearest run combo; 22 steps had no candidate and fell to bare).

### NY PM all-history STKd8w42pmb

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 2069 / -5597 / -1082 / -4324 / 2334 | 2409 / -6224 / -1285 / -4324 / 2359 | 7318 / -23907 / -10012 / -7119 / 1107 | 4388 / -13264 / -8957 / -4799 / 1412 | 6154 / -15632 / -5902 / -7119 / 1217 | 7825 / -23907 / -10012 / -6564 / 658 | 2605 / -5857 / -4122 / -3624 / 1491 |
| fixed pick today (ref, hindsight) | 1816 / -4853 / -1218 / -3884 / 2356 | 2085 / -6479 / -1405 / -6042 / 2537 | 8624 / -26399 / -8227 / -6042 / 862 | 4837 / -12808 / -7926 / -6042 / 1380 | 7567 / -17898 / -7353 / -5248 / 581 | 7532 / -25684 / -8227 / -3604 / 669 | 2520 / -6380 / -5572 / -2450 / 955 |
| R1 current | 2930 / -7755 / -2462 / -4799 / 2093 | 2755 / -7755 / -2661 / -6559 / 2051 | 7932 / -23561 / -9886 / -6559 / 865 | 7860 / -21760 / -9886 / -6559 / 1039 | 6122 / -16531 / -5727 / -5508 / 1105 | 7631 / -23561 / -8328 / -3929 / 364 | 3010 / -7915 / -3422 / -2344 / 1416 |
| R2 filter->rank | 2959 / -7364 / -2572 / -5999 / 1828 | 3152 / -8733 / -2572 / -5999 / 1994 | 7796 / -23561 / -12271 / -5999 / 888 | 7708 / -20868 / -12271 / -5999 / 1025 | 6122 / -16531 / -5727 / -5508 / 1105 | 7460 / -23561 / -8328 / -3929 / 445 | 3010 / -7915 / -3422 / -2344 / 1416 |
| R3 lookback 3m | 2259 / -6792 / -1167 / -4324 / 2242 | 2672 / -7786 / -1300 / -5434 / 2315 | 8444 / -28506 / -12271 / -6673 / 905 | 7651 / -21983 / -12271 / -5594 / 1217 | 6479 / -16826 / -5902 / -6673 / 1102 | 8640 / -28506 / -11327 / -3929 / 439 | 2789 / -7665 / -4347 / -2589 / 1007 |
| R3 lookback 12m | 2626 / -7659 / -2957 / -4829 / 2164 | 2834 / -7659 / -2957 / -4829 / 2258 | 8104 / -19828 / -9656 / -6673 / 778 | 6523 / -18137 / -9656 / -4829 / 1220 | 7643 / -19285 / -7827 / -6673 / 644 | 7175 / -18940 / -8232 / -3929 / 378 | 3010 / -7915 / -3422 / -2344 / 1416 |
| R3 lookback 24m **(winner whole OOS)** | 2568 / -7217 / -3452 / -4829 / 1868 | 2921 / -8228 / -3452 / -5469 / 2105 | 7370 / -18748 / -9656 / -6673 / 786 | 6712 / -18748 / -9656 / -5469 / 1141 | 7409 / -16686 / -5562 / -6673 / 773 | 7182 / -17455 / -9262 / -5144 / 347 | 3010 / -7915 / -3422 / -2344 / 1416 |
| R4 recency blend | 2651 / -7364 / -2572 / -5999 / 2256 | 3011 / -8733 / -2572 / -5999 / 2079 | 7971 / -22126 / -12271 / -6673 / 797 | 7471 / -19762 / -12271 / -5999 / 1195 | 6508 / -16686 / -5562 / -6673 / 807 | 7855 / -22126 / -8232 / -3929 / 304 | 3010 / -7915 / -3422 / -2344 / 1416 |
| R5 ensemble | 2945 / -7364 / -2572 / -5999 / 1921 | 3145 / -8733 / -2572 / -5999 / 2040 | 7741 / -23908 / -10449 / -6673 / 938 | 6406 / -17441 / -10449 / -5999 / 1137 | 5673 / -16556 / -5562 / -6673 / 1349 | 8217 / -23908 / -8328 / -3929 / 392 | 3702 / -7915 / -3422 / -2834 / 948 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 52% ($ 44%) | 0% ($ 0%) | 35% | 0% |
| R2 filter->rank | 55% ($ 44%) | 19% ($ 22%) | 25% | 1% |
| R3 lookback 3m | 49% ($ 39%) | 42% ($ 48%) | 57% | 6% |
| R3 lookback 12m | 52% ($ 40%) | 45% ($ 40%) | 20% | 0% |
| R3 lookback 24m | 54% ($ 41%) | 49% ($ 48%) | 11% | 0% |
| R4 recency blend | 54% ($ 42%) | 45% ($ 45%) | 28% | 0% |
| R5 ensemble | 52% ($ 40%) | 49% ($ 50%) | 51% | 4% |
| fixed pick (ref) | 50% ($ 40%) | 51% ($ 57%) | - | - |

R5: exact combo existed on 1 of 79 steps where it picked (rest = nearest run combo; 1 steps had no candidate and fell to bare).

### NY PM equal STKd8w42pme

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 2037 / -5889 / -2342 / -4439 / 2204 | 2218 / -6395 / -5112 / -4439 / 2508 | 7831 / -25100 / -8162 / -6308 / 1284 | 8231 / -24292 / -7192 / -5184 / 1503 | 4264 / -16310 / -6186 / -6308 / 1442 | 10392 / -25100 / -8162 / -5135 / 955 | 3204 / -6265 / -3997 / -4439 / 1297 |
| fixed pick today (ref, hindsight) | 1890 / -5596 / -3704 / -4666 / 1540 | 1737 / -5596 / -3704 / -4666 / 2141 | 7489 / -24016 / -7833 / -4666 / 784 | 8982 / -23289 / -5193 / -4666 / 815 | 5085 / -16160 / -7833 / -4522 / 1071 | 8126 / -19088 / -4680 / -4579 / 540 | 3034 / -7285 / -4800 / -3479 / 599 |
| R1 current | 2020 / -5987 / -4095 / -4666 / 2452 | 2400 / -6931 / -4095 / -5258 / 2150 | 11402 / -30955 / -7987 / -6262 / 699 | 9051 / -22397 / -4402 / -5423 / 1040 | 6264 / -20104 / -7987 / -6262 / 957 | 16623 / -30955 / -6751 / -6230 / 270 | 5555 / -10453 / -5617 / -4119 / 330 |
| R2 filter->rank | 2167 / -5889 / -2342 / -4439 / 2386 | 3922 / -10772 / -8023 / -5258 / 1799 | 9699 / -28523 / -8023 / -6230 / 813 | 7465 / -17646 / -8023 / -5258 / 956 | 3875 / -16160 / -7833 / -6094 / 1372 | 14573 / -28523 / -6751 / -6230 / 300 | 5555 / -10453 / -5617 / -4119 / 330 |
| R3 lookback 3m | 1364 / -3604 / -1358 / -3604 / 2204 | 1852 / -5330 / -5112 / -3604 / 2284 | 10686 / -27171 / -7192 / -6160 / 873 | 10175 / -24631 / -7192 / -5184 / 1138 | 4292 / -17409 / -6434 / -6094 / 1426 | 15386 / -27171 / -6751 / -6160 / 102 | 2615 / -5896 / -3192 / -3161 / 1048 |
| R3 lookback 12m | 1519 / -5154 / -1738 / -3604 / 2105 | 3768 / -10772 / -8023 / -5258 / 1660 | 9074 / -24631 / -8023 / -6094 / 850 | 11984 / -24631 / -8023 / -5258 / 779 | 4867 / -16160 / -7833 / -6094 / 1373 | 9931 / -21591 / -4550 / -4579 / 501 | 5328 / -10453 / -5617 / -4119 / 558 |
| R3 lookback 24m | 1331 / -3604 / -1358 / -3604 / 2107 | 3648 / -10772 / -8023 / -5258 / 1673 | 9788 / -27045 / -8428 / -5258 / 679 | 13477 / -27045 / -8023 / -5258 / 502 | 5239 / -16755 / -8428 / -4688 / 1064 | 9931 / -21591 / -4550 / -4579 / 501 | 5328 / -10453 / -5617 / -4119 / 558 |
| R4 recency blend **(winner whole OOS)** | 2167 / -5889 / -2342 / -4439 / 2386 | 3922 / -10772 / -8023 / -5258 / 1799 | 7116 / -19413 / -8428 / -5258 / 789 | 7465 / -17646 / -8023 / -5258 / 956 | 5498 / -16755 / -8428 / -4688 / 999 | 8284 / -19413 / -4680 / -4579 / 548 | 5421 / -10453 / -5617 / -4119 / 422 |
| R5 ensemble | 2167 / -5889 / -2342 / -4439 / 2386 | 3922 / -10772 / -8023 / -5258 / 1799 | 7659 / -24597 / -8023 / -6094 / 842 | 7555 / -17646 / -8023 / -5258 / 918 | 3865 / -16160 / -7833 / -6094 / 1437 | 10481 / -24597 / -4908 / -4579 / 324 | 2962 / -5743 / -4323 / -3161 / 476 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 44% ($ 36%) | 0% ($ 0%) | 33% | 2% |
| R2 filter->rank | 31% ($ 25%) | 35% ($ 32%) | 22% | 10% |
| R3 lookback 3m | 34% ($ 29%) | 50% ($ 49%) | 37% | 22% |
| R3 lookback 12m | 36% ($ 29%) | 50% ($ 50%) | 9% | 0% |
| R3 lookback 24m | 45% ($ 36%) | 54% ($ 48%) | 10% | 5% |
| R4 recency blend | 44% ($ 38%) | 57% ($ 52%) | 13% | 6% |
| R5 ensemble | 34% ($ 28%) | 51% ($ 50%) | 30% | 10% |
| fixed pick (ref) | 54% ($ 45%) | 55% ($ 46%) | - | - |

R5: exact combo existed on 21 of 72 steps where it picked (rest = nearest run combo; 8 steps had no candidate and fell to bare).

### NY PM delivered four STKd893133bd8 (2-lot basis, R200 joint)

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 4143 / -14543 / -8566 / -8737 / 8718 | 5573 / -24257 / -8566 / -16735 / 9003 | 17582 / -58752 / -22882 / -26155 / 4240 | 8960 / -28568 / -11832 / -16735 / 6135 | 12184 / -35977 / -22882 / -25756 / 4293 | 21719 / -58752 / -21635 / -26155 / 2545 | 4875 / -16710 / -3732 / -7627 / 4545 |
| fixed pick today (ref, hindsight) | 1931 / -7740 / -7288 / -5329 / 6063 | 2894 / -9660 / -7288 / -6769 / 6050 | 9390 / -35972 / -14610 / -14872 / 3183 | 4355 / -13815 / -11250 / -7351 / 4550 | 6230 / -18848 / -13805 / -14872 / 3165 | 11262 / -35972 / -14610 / -11310 / 2087 | 3142 / -8659 / -3491 / -4248 / 3100 |
| R1 current | 2937 / -10940 / -7752 / -6910 / 4946 | 4587 / -14061 / -7752 / -10600 / 5061 | 15402 / -43528 / -22720 / -14473 / 2217 | 9738 / -24435 / -10737 / -10600 / 3058 | 7592 / -22161 / -14574 / -14473 / 2605 | 17304 / -43528 / -22720 / -12192 / 1278 | 4140 / -10396 / -4925 / -4148 / 1751 |
| R2 filter->rank | 2090 / -6041 / -5033 / -5233 / 6121 | 7262 / -23337 / -12877 / -12207 / 4048 | 14512 / -49009 / -22720 / -18769 / 2118 | 10836 / -25934 / -21578 / -18769 / 2689 | 5377 / -15333 / -12817 / -14473 / 2669 | 17516 / -49009 / -22720 / -12192 / 1229 | 4140 / -10396 / -4925 / -4148 / 1751 |
| R3 lookback 3m | 2114 / -6041 / -5033 / -4657 / 5718 | 5576 / -16700 / -8257 / -9660 / 4608 | 14566 / -41461 / -24492 / -14473 / 2107 | 9632 / -21550 / -13851 / -11356 / 2919 | 6971 / -20235 / -11632 / -14473 / 2656 | 15415 / -39999 / -24492 / -12734 / 974 | 3932 / -10297 / -2748 / -4335 / 1932 |
| R3 lookback 12m **(winner whole OOS)** | 2114 / -6041 / -5033 / -4657 / 5718 | 3173 / -10368 / -5033 / -6739 / 5777 | 13796 / -49009 / -15474 / -14473 / 2467 | 9177 / -23213 / -11969 / -10122 / 3483 | 5342 / -15333 / -12817 / -14473 / 2764 | 16349 / -49009 / -15474 / -8514 / 1564 | 4138 / -9706 / -5055 / -4168 / 1617 |
| R3 lookback 24m | 6155 / -17451 / -9287 / -5833 / 4532 | 6616 / -17451 / -9287 / -10777 / 4198 | 14126 / -49009 / -21476 / -14473 / 2163 | 9504 / -22550 / -11969 / -10777 / 2618 | 5342 / -15333 / -12817 / -14473 / 2764 | 17129 / -49009 / -21476 / -12724 / 1368 | 4138 / -9706 / -5055 / -4168 / 1617 |
| R4 recency blend | 5330 / -14133 / -9287 / -5833 / 4924 | 8036 / -23337 / -12877 / -12207 / 3464 | 14401 / -49009 / -21476 / -14473 / 2064 | 10151 / -23337 / -12877 / -12207 / 2175 | 5354 / -15333 / -12817 / -14473 / 2842 | 17129 / -49009 / -21476 / -12724 / 1368 | 4138 / -9706 / -5055 / -4168 / 1617 |
| R5 ensemble | 6589 / -21302 / -11558 / -7123 / 5080 | 6820 / -21302 / -11558 / -10777 / 4469 | 16216 / -49938 / -24492 / -14473 / 2106 | 12271 / -29613 / -13851 / -11356 / 2687 | 5625 / -15333 / -12817 / -14473 / 2617 | 19316 / -49938 / -24492 / -12734 / 1161 | 4760 / -10847 / -5135 / -4378 / 2078 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 89% ($ 38%) | 0% ($ 0%) | 35% | 0% |
| R2 filter->rank | 84% ($ 28%) | 28% ($ 29%) | 27% | 0% |
| R3 lookback 3m | 88% ($ 31%) | 46% ($ 39%) | 41% | 0% |
| R3 lookback 12m | 89% ($ 28%) | 38% ($ 44%) | 9% | 0% |
| R3 lookback 24m | 86% ($ 25%) | 40% ($ 41%) | 4% | 0% |
| R4 recency blend | 88% ($ 25%) | 41% ($ 41%) | 16% | 0% |
| R5 ensemble | 84% ($ 25%) | 36% ($ 41%) | 41% | 0% |
| fixed pick (ref) | 98% ($ 36%) | 44% ($ 49%) | - | - |

R5: exact combo existed on 2 of 80 steps where it picked (rest = nearest run combo; 0 steps had no candidate and fell to bare).

### London STKd8w42lo

Cells = ulcer / max DD / worst week / worst day / $ per week of the chained out-of-sample curve (whole-stack dollars at the stack basis). Lower ulcer and shallower DD first.

| rule | last 3m (Aug-Oct 26) | last 6m (May-Oct 26) | whole OOS (Oct 23-Oct 26) | 2026 Jan-Oct | 2025 | 2024 | 2023 Oct-Dec |
|---|---|---|---|---|---|---|---|
| bare (ref) | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 36407 / -107674 / -52465 / -40029 / 3298 | 23903 / -60541 / -26431 / -21656 / 6648 | 60118 / -107674 / -52465 / -40029 / 1040 | 10839 / -41168 / -28939 / -19277 / 2564 | 2852 / -11367 / -3782 / -11367 / 3449 |
| fixed pick today (ref, hindsight) | 3253 / -8124 / -3461 / -6352 / 7590 | 3210 / -8124 / -6244 / -7522 / 6026 | 38383 / -83262 / -30322 / -20570 / 1324 | 5000 / -18377 / -8793 / -11212 / 5011 | 58454 / -83262 / -30322 / -20570 / -1247 | 11457 / -31437 / -19210 / -11242 / 535 | 2883 / -5876 / -3192 / -5037 / 1732 |
| R1 current **(winner whole OOS)** | 3341 / -11302 / -1870 / -11302 / 7007 | 4336 / -11302 / -7006 / -11302 / 3918 | 23788 / -63690 / -24957 / -22605 / 1278 | 10300 / -36887 / -14890 / -14052 / 3220 | 32837 / -55287 / -24957 / -22605 / 161 | 8971 / -26089 / -17501 / -9894 / 659 | 2532 / -6405 / -2508 / -5384 / 1426 |
| R2 filter->rank | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 32634 / -91380 / -26431 / -21656 / 2316 | 23903 / -60541 / -26431 / -21656 / 6648 | 53350 / -91380 / -14514 / -16320 / 308 | 8871 / -26089 / -19876 / -9894 / 795 | 2532 / -6405 / -2508 / -5384 / 1426 |
| R3 lookback 3m | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 28495 / -77946 / -26431 / -21656 / 2448 | 23903 / -60541 / -26431 / -21656 / 6648 | 45007 / -77946 / -15631 / -11598 / 404 | 8682 / -20882 / -18672 / -9964 / 1084 | 2715 / -6068 / -3741 / -5664 / 1498 |
| R3 lookback 12m | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 40128 / -94464 / -26431 / -21656 / 2050 | 23903 / -60541 / -26431 / -21656 / 6631 | 57932 / -91380 / -14514 / -11598 / -577 | 7909 / -22686 / -21251 / -10003 / 806 | 2523 / -6267 / -1838 / -6223 / 1510 |
| R3 lookback 24m | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 40213 / -94464 / -26431 / -21656 / 1930 | 23903 / -60541 / -26431 / -21656 / 6631 | 57927 / -91380 / -14514 / -11598 / -443 | 8898 / -26586 / -17031 / -10159 / 323 | 2523 / -6267 / -1838 / -6223 / 1510 |
| R4 recency blend | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 34116 / -91380 / -26431 / -21656 / 2042 | 23903 / -60541 / -26431 / -21656 / 6631 | 53826 / -91380 / -14514 / -16320 / -32 | 11170 / -27118 / -21251 / -13967 / 378 | 3234 / -7102 / -4745 / -5474 / 1121 |
| R5 ensemble | 7424 / -19383 / -9051 / -10341 / 9954 | 6305 / -19383 / -10078 / -12650 / 11102 | 32830 / -91380 / -26431 / -21656 / 2358 | 23903 / -60541 / -26431 / -21656 / 6648 | 53350 / -91380 / -14514 / -16320 / 296 | 10505 / -26703 / -18732 / -11408 / 809 | 3542 / -8169 / -3832 / -6064 / 1925 |

Step behaviour (share of steps; step = each pick scored on the next period): 
Beat = step drawdown not deeper than the comparator (ties: higher P&L), the wf_gate period rule used on the pages (drawdown first); the dollar share is in brackets.

| rule | beat bare | beat R1 | pick changed vs previous | pick = bare |
|---|---|---|---|---|
| R1 current | 79% ($ 32%) | 0% ($ 0%) | 38% | 0% |
| R2 filter->rank | 49% ($ 20%) | 22% ($ 44%) | 10% | 36% |
| R3 lookback 3m | 52% ($ 19%) | 30% ($ 57%) | 29% | 38% |
| R3 lookback 12m | 51% ($ 21%) | 40% ($ 55%) | 4% | 28% |
| R3 lookback 24m | 52% ($ 20%) | 39% ($ 51%) | 5% | 28% |
| R4 recency blend | 45% ($ 20%) | 32% ($ 50%) | 20% | 32% |
| R5 ensemble | 44% ($ 20%) | 30% ($ 56%) | 22% | 36% |
| fixed pick (ref) | 76% ($ 30%) | 44% ($ 45%) | - | - |

R5: exact combo existed on 0 of 51 steps where it picked (rest = nearest run combo; 29 steps had no candidate and fell to bare).

## 4-week steps, whole OOS and last 6 months (ulcer / DD / $ per week)

| stack | window | bare | R1 | R2 | R3 3m | R3 12m | R3 24m | R4 | R5 |
|---|---|---|---|---|---|---|---|---|---|
| AS | ALL | 11655 / -59220 / 5164 | 7736 / -24861 / 2371 | 6646 / -23563 / 2301 | 7738 / -23563 / 2213 | 6907 / -22808 / 2400 | 7996 / -24052 / 2188 | 6815 / -21169 / 2301 | 7759 / -27175 / 2241 |
| AS | L6M | 5887 / -21112 / 14875 | 3494 / -14329 / 6715 | 2886 / -10523 / 7539 | 2977 / -10523 / 7275 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 |
| NY9 | ALL | 50169 / -188315 / 18973 | 33144 / -127733 / 8219 | 32383 / -112525 / 11885 | 47643 / -151248 / 9979 | 37211 / -124388 / 11704 | 37055 / -163076 / 10802 | 37096 / -147941 / 10859 | 47274 / -163118 / 12245 |
| NY9 | L6M | 28581 / -99970 / 52932 | 33831 / -109669 / 17689 | 14679 / -52244 / 37909 | 17366 / -62559 / 32058 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 |
| NY8 | ALL | 51620 / -193440 / 18858 | 33821 / -119594 / 8516 | 43044 / -147082 / 17399 | 49298 / -190953 / 15935 | 58857 / -282249 / 15012 | 62802 / -282249 / 13593 | 64814 / -282249 / 14607 | 46014 / -151918 / 16882 |
| NY8 | L6M | 27178 / -97355 / 53077 | 16032 / -53952 / 18864 | 26874 / -97163 / 52043 | 27171 / -97355 / 51539 | 26874 / -97163 / 52043 | 28892 / -105722 / 51970 | 26874 / -97163 / 52043 | 26874 / -97163 / 52043 |
| NP | ALL | 46100 / -180947 / 12258 | 36733 / -148270 / 4795 | 41539 / -180947 / 7155 | 42001 / -180947 / 7758 | 42048 / -180947 / 6822 | 39074 / -180947 / 7100 | 38809 / -180947 / 6958 | 39998 / -180947 / 8033 |
| NP | L6M | 11696 / -55861 / 25748 | 8244 / -22533 / 12375 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 |
| NPB | ALL | 7318 / -23907 / 1107 | 8622 / -25977 / 807 | 8374 / -25977 / 852 | 8549 / -26821 / 850 | 8219 / -20339 / 751 | 7443 / -18748 / 770 | 7802 / -21052 / 768 | 7217 / -21803 / 1008 |
| NPB | L6M | 2409 / -6224 / 2359 | 2821 / -7700 / 1954 | 3089 / -8733 / 2039 | 2741 / -7786 / 2236 | 2831 / -7659 / 2158 | 2921 / -8228 / 2105 | 3011 / -8733 / 2079 | 3083 / -8733 / 2086 |
| NPE | ALL | 7831 / -25100 / 1284 | 8319 / -22764 / 758 | 7845 / -24025 / 876 | 9912 / -27379 / 901 | 9574 / -24631 / 834 | 9296 / -24292 / 708 | 8032 / -22467 / 752 | 9300 / -25096 / 798 |
| NPE | L6M | 2218 / -6395 / 2508 | 2405 / -6931 / 2091 | 3922 / -10772 / 1799 | 1852 / -5330 / 2284 | 3768 / -10772 / 1660 | 3647 / -10772 / 1581 | 3922 / -10772 / 1799 | 3922 / -10772 / 1799 |
| NP4 | ALL | 17582 / -58752 / 4240 | 15301 / -43444 / 2238 | 15438 / -48541 / 1894 | 18575 / -57858 / 2103 | 13533 / -48061 / 2405 | 14068 / -48061 / 2169 | 14582 / -48061 / 2021 | 17725 / -55632 / 2033 |
| NP4 | L6M | 5573 / -24257 / 9003 | 4386 / -14061 / 5132 | 8895 / -24786 / 3647 | 5485 / -16700 / 4880 | 3173 / -10368 / 5777 | 6616 / -17451 / 4198 | 9529 / -24786 / 3263 | 6869 / -21302 / 4256 |
| LO | ALL | 36407 / -107674 / 3298 | 33509 / -80370 / 1292 | 32709 / -91380 / 2322 | 29177 / -81984 / 2517 | 43899 / -112936 / 1934 | 43989 / -112936 / 1816 | 37043 / -91380 / 1950 | 32744 / -91380 / 2441 |
| LO | L6M | 6305 / -19383 / 11102 | 5278 / -13374 / 3803 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 |
| SUM-A | ALL | 45001 / -244753 / 39693 | 37683 / -175237 / 16677 | 40963 / -199918 / 23663 | 53447 / -281346 / 22467 | 39497 / -199918 / 22860 | 49046 / -255512 / 21907 | 46920 / -258933 / 22068 | 43351 / -203339 / 24959 |
| SUM-A | L6M | 17030 / -75220 / 104657 | 14389 / -55206 / 40583 | 10047 / -40928 / 82298 | 10872 / -40928 / 76183 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 |
| SUM-B | ALL | 42048 / -170907 / 31560 | 22459 / -103844 / 14416 | 36990 / -143353 / 23916 | 41854 / -182795 / 22769 | 57071 / -284397 / 21751 | 59241 / -286208 / 19766 | 57989 / -286208 / 20879 | 37985 / -147865 / 23597 |
| SUM-B | L6M | 16809 / -80374 / 88057 | 8937 / -26319 / 34514 | 18475 / -72445 / 74331 | 18894 / -74840 / 74795 | 18357 / -71862 / 76460 | 21802 / -86724 / 74808 | 20062 / -78165 / 73947 | 20599 / -78643 / 74939 |

## 6-week steps, whole OOS and last 6 months (ulcer / DD / $ per week)

| stack | window | bare | R1 | R2 | R3 3m | R3 12m | R3 24m | R4 | R5 |
|---|---|---|---|---|---|---|---|---|---|
| AS | ALL | 11655 / -59220 / 5164 | 9217 / -30306 / 2299 | 6141 / -23563 / 2357 | 6533 / -23563 / 2391 | 6901 / -22808 / 2402 | 7996 / -24052 / 2177 | 6922 / -24423 / 2318 | 7645 / -27175 / 2307 |
| AS | L6M | 5887 / -21112 / 14875 | 3551 / -14329 / 7360 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 | 2886 / -10523 / 7539 |
| NY9 | ALL | 50169 / -188315 / 18973 | 37222 / -124122 / 6726 | 33143 / -113175 / 12751 | 48996 / -165612 / 9599 | 43963 / -148008 / 11118 | 38345 / -147941 / 10842 | 34479 / -147941 / 11049 | 51884 / -172624 / 11700 |
| NY9 | L6M | 28581 / -99970 / 52932 | 41396 / -100785 / 11527 | 14679 / -52244 / 37909 | 39873 / -116605 / 26046 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 | 14679 / -52244 / 37909 |
| NY8 | ALL | 51620 / -193440 / 18858 | 30429 / -117013 / 8016 | 38907 / -129614 / 17685 | 43319 / -182357 / 17298 | 59528 / -282249 / 15141 | 62336 / -282249 / 13891 | 67711 / -282249 / 14312 | 41328 / -149308 / 17035 |
| NY8 | L6M | 27178 / -97355 / 53077 | 17389 / -53952 / 16898 | 26874 / -97163 / 52043 | 27148 / -97355 / 51404 | 26874 / -97163 / 52043 | 29035 / -105722 / 51776 | 26874 / -97163 / 52043 | 26874 / -97163 / 52043 |
| NP | ALL | 46100 / -180947 / 12258 | 30278 / -124975 / 4755 | 41590 / -180947 / 7228 | 40379 / -180947 / 8279 | 38648 / -180947 / 7266 | 38179 / -180947 / 7285 | 38874 / -180947 / 6854 | 41199 / -180947 / 7851 |
| NP | L6M | 11696 / -55861 / 25748 | 8849 / -38234 / 12074 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 | 11696 / -55861 / 25748 |
| NPB | ALL | 7318 / -23907 / 1107 | 8324 / -22706 / 871 | 7855 / -22706 / 913 | 8066 / -25496 / 903 | 8332 / -20600 / 751 | 7375 / -18748 / 801 | 7558 / -21052 / 831 | 7603 / -21813 / 976 |
| NPB | L6M | 2409 / -6224 / 2359 | 2833 / -7700 / 1947 | 3089 / -8733 / 2039 | 2810 / -7786 / 2056 | 2813 / -7659 / 2119 | 2923 / -8228 / 2076 | 3076 / -8733 / 2059 | 3138 / -8733 / 1974 |
| NPE | ALL | 7831 / -25100 / 1284 | 9132 / -25717 / 733 | 8883 / -24692 / 691 | 11136 / -26604 / 684 | 8683 / -24292 / 831 | 8764 / -24292 / 729 | 7795 / -21591 / 742 | 9247 / -28250 / 731 |
| NPE | L6M | 2218 / -6395 / 2508 | 2316 / -6931 / 2248 | 3916 / -10772 / 1660 | 3654 / -10772 / 1720 | 3768 / -10772 / 1660 | 3648 / -10772 / 1673 | 3916 / -10772 / 1660 | 3916 / -10772 / 1660 |
| NP4 | ALL | 17582 / -58752 / 4240 | 16530 / -48573 / 2253 | 15035 / -45528 / 1922 | 16933 / -52430 / 2083 | 18002 / -57609 / 2360 | 13402 / -45528 / 2199 | 14052 / -45528 / 1985 | 16648 / -47598 / 1923 |
| NP4 | L6M | 5573 / -24257 / 9003 | 4437 / -14026 / 5090 | 8896 / -24786 / 3553 | 5492 / -16700 / 5007 | 3173 / -10368 / 5777 | 6616 / -17451 / 4198 | 9555 / -24786 / 3135 | 6869 / -21302 / 4460 |
| LO | ALL | 36407 / -107674 / 3298 | 21980 / -67318 / 1397 | 32559 / -91380 / 2303 | 33013 / -88706 / 2176 | 43899 / -112936 / 1934 | 43983 / -112936 / 1803 | 35840 / -91380 / 2056 | 32599 / -91380 / 2362 |
| LO | L6M | 6305 / -19383 / 11102 | 5279 / -12843 / 4788 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 | 6305 / -19383 / 11102 |
| SUM-A | ALL | 45001 / -244753 / 39693 | 40078 / -189224 / 15177 | 39690 / -199918 / 24639 | 49161 / -262934 / 22444 | 40203 / -199918 / 22720 | 48051 / -258933 / 22107 | 47044 / -258933 / 22277 | 51893 / -254697 / 24220 |
| SUM-A | L6M | 17030 / -75220 / 104657 | 13784 / -49119 / 35750 | 10047 / -40928 / 82298 | 13938 / -57531 / 70435 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 | 10047 / -40928 / 82298 |
| SUM-B | ALL | 42048 / -170907 / 31560 | 24552 / -112377 / 13965 | 35343 / -128934 / 24267 | 36472 / -168442 / 23948 | 57245 / -284397 / 21837 | 58645 / -286208 / 20070 | 57705 / -286208 / 20671 | 36068 / -147186 / 23627 |
| SUM-B | L6M | 16809 / -80374 / 88057 | 10143 / -37370 / 34136 | 18444 / -72445 / 74237 | 18763 / -74840 / 75051 | 18357 / -71862 / 76460 | 21875 / -86724 / 74614 | 20016 / -78165 / 73819 | 20584 / -78643 / 75143 |


## Second table: the MIX choice (which books, which weights) under R1 / R2 / R4 - NOT RUN, needs new engine runs (STOP: LEAD to decide)

The stored month rows hold trades per book (trades.parquet has a `book` column: NY AM nine 9 books, NY AM eight 8, NY PM primary 5, Asia 4, NY PM four 4, London 3) for each of the 80 / 242 combos, but a different mix of books or different weights changes the stack itself (shared daily-loss halts DLA/DLB/DLC, caps, stack locks and the smallest-lot rule act across books), so adding or re-scaling stored book P&L would be an approximation, not the engine's number. I did not do that. No book-weight variants of the joint combos exist in the month rows (only the 6/3/1 vs 6/3/2 file-size runs of the one NY AM nine pick).
Count to do it exactly: (a) minimum, leave-one-book-out of the CURRENT fixed pick of the four live stacks (NY AM nine 9 + Asia 4 + NY PM primary 5 + London 3 = 21 sets) x 42 months = 882 engine month-runs, which allows a fixed-pick mix test only; (b) a true walk-forward of the mix choice needs every leave-one-out for every candidate combo: 9 x 242 + 4 x 80 + 5 x 80 + 3 x 80 = 3,138 sets x 42 months = 131,796 month-runs, plus any weight levels (each extra weight level multiplies by the books). Not run; waiting for the LEAD.

## Files and reproduction
Candidate month rows read from /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/<set>/<month>/trades.parquet via pool_run.daily_safe (the BAREFIT loader) and the joint maps /mnt/l2/l2vast/_layers/barefitjoint_*.json (Asia and NY PM four: the _r200 files). Scripts (scratchpad, read-only, niced): load.py, bake.py, rep.py, gen.py under <tmp> No engine file, gate or live item touched.
