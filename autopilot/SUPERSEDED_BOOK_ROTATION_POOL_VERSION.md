**SUPERSEDED by Josh order 1432Z (pool = today survivors; rotation must pick from the entire candidate set). Kept for reference only, not the answer.**

# Book rotation walk-forward: walk-forward analysis (Pardo) applied to BOOK SELECTION, i.e. strategy / book rotation (dynamic strategy selection, rolling re-selection)

Updated 2026-11-26 14:27Z. W-ROT, order from Josh (DIRECTIVE_20261126_1425Z_BOOK_ROTATION_WALKFORWARD.md). LIGHT version, STORED truly-bare R0 daily rows only, no engine run, nothing live changes.

## ANSWER FIRST

- **Rotation does NOT clearly win in this light test.** Out of sample (2-week steps, 80 steps, 2023-10-02 to 2026-10-30, every pick made only from days before the date) the typical rotation row earns $/wk per unit of ulcer of about 0.57 on the four sessions summed, against 0.78 for the fixed mixes held throughout (18 books, $11,477/wk, ulcer 14,778) and 0.59 for all pool books equal weight (87 books). The best single summed rotation row (lookback 5 months, N index 2, rank ulcer, py) reaches 0.91, but it pays for the best of 60 rows tried: the reality-check bootstrap gives p = 0.58 against the all-pool reference and p = 0.82 against the fixed mixes, i.e. **inside noise**.
- **Per session the fixed mix wins or ties in Asia and NY AM** (no rotation row beats the fixed mix on return per unit ulcer in either session: 0 of 60 rows), NY PM and London have a few rows above the fixed mix (NY PM 44 of 60, London 16 of 60) but p = 0.30 and 0.41 after paying for the best row: noise. Caution on the fixed mixes: they were picked with the last 6 months in view (hindsight), so beating them is a hard bar and losing to them is not proof that rotation is worse than a fairly chosen mix; the fair no-hindsight benchmark is the all-pool row, and rotation does not clearly beat that either.
- **Best lookback (median over N x rank x variant of $/wk per unit ulcer, 2-week steps, the six lookbacks 1/3/4/5/6/12 listed in the table below):** Asia 6 months, NY AM 3 (3 and 12 within 0.01), NY PM flat (all lookbacks 0.36-0.36: the pool is 7 books, N=7 is all of them), London 5 (flat, 0.10-0.11), four summed **6 months** (0.64 vs 0.54 for 1 month). The ordering of lookbacks is weak and not stable across sessions; 6 months is the standing rule and is as good as any.
- Longer N (more books) is better than short N on every session: median return per ulcer rises from N small to N large (Asia 0.12 to 0.20, NY AM 0.10 to 0.22, summed 0.40 to 0.66), i.e. the more the pick looks like the whole pool, the better. That says diversification, not selection, is doing the work. Ranking on $/wk only is as good as ranking on ulcer (Asia 0.17 vs 0.16, NY AM 0.17 vs 0.17, summed 0.51 vs 0.61 in favour of ulcer); the prior-year filter helps in NY PM, London and the sum (0.65 vs 0.43 summed) but not in Asia.
- **Recent first** (out-of-sample curve, last 6 and 3 months; tables below): rotation earns well in absolute terms but the fixed mixes (picked on exactly this period) are far ahead: summed L6M fixed 5.64 per unit ulcer vs rotation medians 2.9-3.9; L3M fixed 3.94 vs 2.3-3.7. The lookbacks 5-6 months and 12 are best in the last 6 months; the 1-month lookback is worst in the last 3 months for NY AM (0.33) and the sum (2.27).
- **Turnover:** the share of the N slots replaced at each 2-week step is 60-80% at a 1-month lookback in Asia/NY AM, 25-45% at 3-4 months, 17-25% at 6 months, 5-17% at 12 months (tables below). Beating the fixed mix step by step: the rotation row wins only 34-46% of steps in Asia, NY AM and the sum (per held lot), 45-55% in NY PM and London.
- Not done / skipped: variant (c), the weighted mix by the stack loop add rule, is NOT computed: that rule judges stack-level results (shared caps, stack rules, scaling to the current ulcer) that only the engine produces; adding stored 1-lot rows would not be the rule. HEAVY version: not started, waits for Josh yes (section at the end).

- **Practical line (how many different books would the live file have needed over the last 6 months if rotation won):** across the 60 two-week rotation rows the live file would have needed a median of **33 different books** over 2026-05..2026-10 (range 17 to 71), against 20 books in the fixed mixes today (Asia 4, NY AM 9, NY PM 4, London 3); for the best summed row (lookback 5, N index 2, ulcer, py) it is 32 (Asia 12, NY AM 10, NY PM 7, London 3); the 6-month lookback, ulcer ranking, plain: 25 / 31 / 40 books for the three N sizes. Of the pool, only the books with R0 rows were available to the walk (Asia 45 of 87, NY AM 31 of 42), so the real count is a floor.

## What was done and what it ignores (read first)

- Data: stored DAILY P&L of the truly bare R0 run (own bracket, 1 lot, fees in, TL3_ALN_<S>_<id>_R0*) from /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/ via combo_score.series (the loader the W-COMBO pages use; same trade-date convention, ulcer = RMS of drawdown of cumulative daily P&L, max DD, worst ISO week). 41 months 202304-202610 (202511 absent for every set, tape hole), 915 weekdays per book, zero-filled on weekdays without trades.
- Pools are the pool keys of the current reselect files (reselect_<session>_own_d8_nol3_recent.json): Asia 87, NY AM 42, NY PM 7, London 4. **Only books with a stored R0 set with all 41 months landed are included; the others are EXCLUDED** (their judgment sets are R1 wrapper / _CANC / _BASE / pass-2 runs with account layers on, not bare):

| session | pool | books with stored R0 daily rows (included) | daily rows | no R0 set (excluded) | fixed mix today | fixed mix members with R0 (used as reference) |
|---|---|---|---|---|---|---|
| Asia | 87 | **45** | 41,175 | 42 | 4 | 3 (missing: L385f4f2e_CX502) |
| NY AM | 42 | **31** | 28,365 | 11 | 9 | 8 (missing: B7bfd33b7) |
| NY PM | 7 | **7** | 6,405 | 0 | 4 | 4 (all) |
| London | 4 | **4** | 3,660 | 0 | 3 | 3 (all) |

- **Ignores:** books summed as independent 1-lot streams. No stack rules, no same-side cap, no stack locks, no day caps, no size-dependent fills or slippage, no account layers (those are exactly what R0 removes). A real stack of the picked books would trade less than the sum shows. Dollars scale with the number of books held (lots column): compare rows across N or against the references on **$/wk per unit ulcer** and per-lot step results, not on raw dollars.
- **Look-ahead in the menu (applies to every rotation row):** the pools are the books that passed the W-COMBO gates, which used data up to 2026-10, and the 42 and 11 books without R0 rows are not in the menu: the menu is survivor-biased toward the books that did well in the last 6 months. Rotation rows are flattered in the early steps; the fixed mixes are flattered even more (picked on the last 6 months). The comparison among lookbacks, N, ranks is fair; absolute levels are optimistic.
- Walk: step dates every 2 weeks (and 4 weeks beside) from Monday 2023-10-02 (6 months of history exist from 2023-04-03; the 12-month reference starts 2024-04-03) to 2026-10-30; at each date, per session, books ranked on the trailing LOOKBACK months using ONLY days before the date; top N at equal weight (each held book 1 lot, P&L summed); held until the next date; step results chained into one out-of-sample curve (80 steps at 2 weeks, 40 at 4). N = 3 / 5 / 8 (London 1 / 2 / 3; NY PM has only 7 books, so N=8 means all 7 and equals the all-pool row). The summed calendar adds the four session curves with N index aligned (3/3/3/1, 5/5/5/2, 8/8/all7/3).
- RANK drawdown first = ulcer ascending, $/wk descending as tie-break; second run on $/wk only. A book needs activity in the window (non-zero P&L on at least max(3, 20%) of the window days) to be ranked ahead of an inactive one, otherwise a book that did not trade would rank first on ulcer (one choice, stated). Variant (b) prior-year filter: drop a book that lost money in, or was RED (ulcer > 1.3 x pool median or max DD more than 30% deeper than the pool median) in, any calendar year fully before the date (inactive until 2024-01-01; 2023 is Apr-Dec); if fewer than N books pass, the remaining slots are filled in rank order. 2023-10 to 2023-12 therefore behaves like plain.
- Columns: $/wk, max DD, ulcer, worst week: of the out-of-sample curve over the window named; per-ulcer = $/wk / ulcer; "beat" = share of steps where the rotation P&L per held lot beat the fixed mix P&L per member (per-lot, because the fixed mixes hold 3/8/4/3 books); turnover = share of slots replaced at a step (mean). Full rows (all windows, 2 and 4 weeks, all variants): BOOK_ROTATION_WALKFORWARD_ROWS.csv.

## 1. Whole out-of-sample (2-week steps, rank = ulcer, variant (a) plain), every LOOKBACK x N

### Asia

| lookback (months) | N | lots | $/wk | max DD | ulcer | worst week | $/wk per ulcer | beats fixed (steps) | turnover |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 3 | 3 | 1,288 | -45,113 | 17,321 | -10,590 | 0.07 | 38% | 80% |
| 1 | 5 | 5 | 2,394 | -62,542 | 18,782 | -23,957 | 0.13 | 40% | 70% |
| 1 | 8 | 8 | 4,224 | -65,969 | 21,767 | -32,427 | 0.19 | 45% | 60% |
| 3 | 3 | 3 | 1,059 | -49,333 | 23,698 | -17,417 | 0.04 | 41% | 43% |
| 3 | 5 | 5 | 2,097 | -46,415 | 16,417 | -40,979 | 0.13 | 40% | 35% |
| 3 | 8 | 8 | 3,690 | -69,154 | 22,729 | -55,326 | 0.16 | 40% | 30% |
| 4 | 3 | 3 | 1,441 | -36,730 | 11,013 | -19,809 | 0.13 | 41% | 36% |
| 4 | 5 | 5 | 2,447 | -45,934 | 11,416 | -40,512 | 0.21 | 38% | 30% |
| 4 | 8 | 8 | 4,064 | -58,969 | 16,190 | -47,959 | 0.25 | 34% | 25% |
| 5 | 3 | 3 | 1,670 | -22,367 | 6,618 | -9,926 | 0.25 | 44% | 24% |
| 5 | 5 | 5 | 2,261 | -29,566 | 10,934 | -18,256 | 0.21 | 38% | 24% |
| 5 | 8 | 8 | 3,906 | -44,506 | 16,693 | -21,660 | 0.23 | 34% | 20% |
| 6 | 3 | 3 | 1,389 | -24,548 | 6,223 | -14,892 | 0.22 | 39% | 25% |
| 6 | 5 | 5 | 2,410 | -29,837 | 9,391 | -20,527 | 0.26 | 34% | 21% |
| 6 | 8 | 8 | 3,864 | -51,723 | 17,204 | -21,660 | 0.22 | 36% | 17% |
| 12 (ref, starts 2024-04) | 3 | 3 | 1,053 | -34,204 | 12,447 | -10,477 | 0.08 | 42% | 17% |
| 12 (ref, starts 2024-04) | 5 | 5 | 1,704 | -39,664 | 12,718 | -12,425 | 0.13 | 32% | 16% |
| 12 (ref, starts 2024-04) | 8 | 8 | 3,247 | -49,093 | 19,491 | -30,579 | 0.17 | 39% | 11% |
| **FIXED mix held throughout (bare)** | | 3 | 1,991 | -23,767 | 4,797 | -15,068 | 0.42 | | |
| **ALL pool books equal weight (held throughout)** | | 45 | 25,821 | -329,709 | 93,402 | -236,600 | 0.28 | | |

### NY AM

| lookback (months) | N | lots | $/wk | max DD | ulcer | worst week | $/wk per ulcer | beats fixed (steps) | turnover |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 3 | 3 | 1,310 | -36,541 | 12,228 | -25,340 | 0.11 | 36% | 64% |
| 1 | 5 | 5 | 2,339 | -47,371 | 15,315 | -28,733 | 0.15 | 35% | 56% |
| 1 | 8 | 8 | 3,942 | -76,052 | 23,374 | -38,219 | 0.17 | 42% | 49% |
| 3 | 3 | 3 | 892 | -45,542 | 12,135 | -16,050 | 0.07 | 39% | 34% |
| 3 | 5 | 5 | 2,261 | -34,086 | 11,929 | -28,613 | 0.19 | 36% | 28% |
| 3 | 8 | 8 | 3,389 | -66,101 | 19,052 | -30,738 | 0.18 | 39% | 21% |
| 4 | 3 | 3 | 1,331 | -30,842 | 8,010 | -16,050 | 0.17 | 39% | 28% |
| 4 | 5 | 5 | 2,328 | -49,878 | 14,007 | -23,723 | 0.17 | 45% | 22% |
| 4 | 8 | 8 | 3,798 | -66,421 | 20,408 | -25,879 | 0.19 | 41% | 18% |
| 5 | 3 | 3 | 937 | -35,878 | 11,589 | -14,504 | 0.08 | 40% | 20% |
| 5 | 5 | 5 | 2,034 | -60,917 | 16,335 | -19,230 | 0.12 | 41% | 16% |
| 5 | 8 | 8 | 3,420 | -70,458 | 20,194 | -28,964 | 0.17 | 38% | 13% |
| 6 | 3 | 3 | 1,034 | -37,459 | 14,021 | -8,781 | 0.07 | 41% | 18% |
| 6 | 5 | 5 | 1,852 | -73,652 | 19,756 | -19,870 | 0.09 | 39% | 13% |
| 6 | 8 | 8 | 3,595 | -59,375 | 16,907 | -23,290 | 0.21 | 44% | 10% |
| 12 (ref, starts 2024-04) | 3 | 3 | 705 | -35,214 | 14,335 | -12,162 | 0.05 | 30% | 12% |
| 12 (ref, starts 2024-04) | 5 | 5 | 2,064 | -45,407 | 14,255 | -17,824 | 0.14 | 41% | 10% |
| 12 (ref, starts 2024-04) | 8 | 8 | 4,206 | -66,478 | 19,465 | -23,290 | 0.22 | 39% | 5% |
| **FIXED mix held throughout (bare)** | | 8 | 5,899 | -56,611 | 12,921 | -41,128 | 0.46 | | |
| **ALL pool books equal weight (held throughout)** | | 31 | 22,231 | -264,872 | 59,749 | -141,138 | 0.37 | | |

### NY PM

| lookback (months) | N | lots | $/wk | max DD | ulcer | worst week | $/wk per ulcer | beats fixed (steps) | turnover |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 3 | 3 | 1,850 | -14,683 | 5,546 | -12,069 | 0.33 | 54% | 40% |
| 1 | 5 | 5 | 2,686 | -30,688 | 8,334 | -14,544 | 0.32 | 48% | 21% |
| 1 | all 7 | 7 | 3,949 | -40,096 | 10,972 | -15,276 | 0.36 | 51% | 0% |
| 3 | 3 | 3 | 1,749 | -42,399 | 12,588 | -16,428 | 0.14 | 46% | 15% |
| 3 | 5 | 5 | 2,785 | -35,308 | 11,055 | -12,645 | 0.25 | 48% | 8% |
| 3 | all 7 | 7 | 3,949 | -40,096 | 10,972 | -15,276 | 0.36 | 51% | 0% |
| 4 | 3 | 3 | 1,681 | -44,546 | 11,271 | -16,428 | 0.15 | 46% | 15% |
| 4 | 5 | 5 | 2,735 | -30,766 | 10,697 | -13,119 | 0.26 | 51% | 6% |
| 4 | all 7 | 7 | 3,949 | -40,096 | 10,972 | -15,276 | 0.36 | 51% | 0% |
| 5 | 3 | 3 | 2,055 | -41,134 | 10,523 | -16,428 | 0.20 | 52% | 13% |
| 5 | 5 | 5 | 2,540 | -32,131 | 11,586 | -13,574 | 0.22 | 48% | 6% |
| 5 | all 7 | 7 | 3,949 | -40,096 | 10,972 | -15,276 | 0.36 | 51% | 0% |
| 6 | 3 | 3 | 1,767 | -43,691 | 10,827 | -16,428 | 0.16 | 52% | 10% |
| 6 | 5 | 5 | 2,605 | -37,426 | 13,654 | -15,792 | 0.19 | 51% | 6% |
| 6 | all 7 | 7 | 3,949 | -40,096 | 10,972 | -15,276 | 0.36 | 51% | 0% |
| 12 (ref, starts 2024-04) | 3 | 3 | 1,714 | -39,770 | 11,851 | -15,714 | 0.14 | 47% | 5% |
| 12 (ref, starts 2024-04) | 5 | 5 | 2,893 | -38,643 | 12,878 | -14,992 | 0.22 | 45% | 4% |
| 12 (ref, starts 2024-04) | all 7 | 7 | 4,149 | -40,096 | 11,646 | -15,276 | 0.36 | 55% | 0% |
| **FIXED mix held throughout (bare)** | | 4 | 2,103 | -29,188 | 8,160 | -11,409 | 0.26 | | |
| **ALL pool books equal weight (held throughout)** | | 7 | 3,607 | -40,096 | 10,830 | -15,276 | 0.33 | | |

### London

| lookback (months) | N | lots | $/wk | max DD | ulcer | worst week | $/wk per ulcer | beats fixed (steps) | turnover |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | 1 | 402 | -29,404 | 10,580 | -7,286 | 0.04 | 45% | 57% |
| 1 | 2 | 2 | 674 | -38,611 | 13,149 | -11,757 | 0.05 | 42% | 30% |
| 1 | 3 | 3 | 1,482 | -44,382 | 12,204 | -15,568 | 0.12 | 40% | 14% |
| 3 | 1 | 1 | 468 | -20,640 | 10,259 | -6,591 | 0.05 | 50% | 30% |
| 3 | 2 | 2 | 973 | -40,150 | 15,541 | -14,242 | 0.06 | 49% | 18% |
| 3 | 3 | 3 | 1,683 | -46,587 | 11,398 | -15,568 | 0.15 | 45% | 7% |
| 4 | 1 | 1 | 318 | -40,341 | 19,196 | -11,320 | 0.02 | 49% | 22% |
| 4 | 2 | 2 | 834 | -45,693 | 19,481 | -12,568 | 0.04 | 50% | 15% |
| 4 | 3 | 3 | 1,699 | -46,810 | 11,898 | -15,568 | 0.14 | 46% | 6% |
| 5 | 1 | 1 | 167 | -46,073 | 25,393 | -11,320 | 0.01 | 42% | 22% |
| 5 | 2 | 2 | 645 | -47,615 | 22,854 | -12,568 | 0.03 | 42% | 13% |
| 5 | 3 | 3 | 1,568 | -46,810 | 12,003 | -15,568 | 0.13 | 48% | 5% |
| 6 | 1 | 1 | 317 | -25,242 | 11,979 | -11,320 | 0.03 | 46% | 19% |
| 6 | 2 | 2 | 932 | -33,488 | 11,678 | -12,568 | 0.08 | 48% | 9% |
| 6 | 3 | 3 | 1,625 | -46,810 | 12,026 | -15,568 | 0.14 | 48% | 3% |
| 12 (ref, starts 2024-04) | 1 | 1 | 459 | -21,998 | 10,727 | -11,320 | 0.04 | 48% | 9% |
| 12 (ref, starts 2024-04) | 2 | 2 | 1,051 | -30,866 | 11,650 | -12,588 | 0.09 | 48% | 4% |
| 12 (ref, starts 2024-04) | 3 | 3 | 1,563 | -46,103 | 14,023 | -21,682 | 0.11 | 47% | 3% |
| **FIXED mix held throughout (bare)** | | 3 | 1,484 | -45,648 | 13,578 | -25,126 | 0.11 | | |
| **ALL pool books equal weight (held throughout)** | | 4 | 1,924 | -56,031 | 16,483 | -28,968 | 0.12 | | |

### Four sessions summed

| lookback (months) | N | lots | $/wk | max DD | ulcer | worst week | $/wk per ulcer | beats fixed (steps) | turnover |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 3/3/3/1 | 10 | 4,848 | -46,445 | 13,565 | -40,131 | 0.36 | 38% | 61% |
| 1 | 5/5/5/2 | 17 | 8,092 | -82,789 | 18,077 | -59,021 | 0.45 | 40% | 47% |
| 1 | 8/8/all7/3 | 26 | 13,597 | -112,692 | 22,318 | -81,884 | 0.61 | 40% | 35% |
| 3 | 3/3/3/1 | 10 | 4,168 | -47,961 | 14,830 | -23,327 | 0.28 | 35% | 31% |
| 3 | 5/5/5/2 | 17 | 8,116 | -102,172 | 16,204 | -73,116 | 0.50 | 39% | 23% |
| 3 | 8/8/all7/3 | 26 | 12,712 | -128,916 | 21,388 | -91,341 | 0.59 | 41% | 16% |
| 4 | 3/3/3/1 | 10 | 4,770 | -61,524 | 11,973 | -45,064 | 0.40 | 40% | 26% |
| 4 | 5/5/5/2 | 17 | 8,344 | -95,847 | 17,660 | -70,975 | 0.47 | 45% | 19% |
| 4 | 8/8/all7/3 | 26 | 13,510 | -114,782 | 19,463 | -74,812 | 0.69 | 44% | 14% |
| 5 | 3/3/3/1 | 10 | 4,829 | -48,706 | 12,214 | -22,576 | 0.40 | 46% | 19% |
| 5 | 5/5/5/2 | 17 | 7,480 | -72,481 | 14,536 | -41,952 | 0.51 | 42% | 15% |
| 5 | 8/8/all7/3 | 26 | 12,843 | -87,558 | 18,326 | -46,639 | 0.70 | 44% | 11% |
| 6 | 3/3/3/1 | 10 | 4,507 | -75,324 | 18,902 | -22,229 | 0.24 | 36% | 18% |
| 6 | 5/5/5/2 | 17 | 7,799 | -71,414 | 15,136 | -37,614 | 0.52 | 39% | 13% |
| 6 | 8/8/all7/3 | 26 | 13,033 | -91,984 | 16,215 | -57,900 | 0.80 | 42% | 9% |
| 12 (ref, starts 2024-04) | 3/3/3/1 | 10 | 3,931 | -57,063 | 18,097 | -22,195 | 0.22 | 27% | 11% |
| 12 (ref, starts 2024-04) | 5/5/5/2 | 17 | 7,711 | -54,534 | 15,600 | -33,190 | 0.49 | 35% | 9% |
| 12 (ref, starts 2024-04) | 8/8/all7/3 | 26 | 13,165 | -91,904 | 20,965 | -53,037 | 0.63 | 35% | 5% |
| **FIXED mix held throughout (bare)** | | 18 | 11,477 | -93,135 | 14,778 | -46,951 | 0.78 | | |
| **ALL pool books equal weight (held throughout)** | | 87 | 53,583 | -568,240 | 91,178 | -366,637 | 0.59 | | |

## 2. Variants and ranks: median $/wk per unit ulcer over the other settings (2-week | 4-week steps, whole OOS)

| session | lookback | 1 | 3 | 4 | 5 | 6 | 12 (ref) |
|---|---|---|---|---|---|---|---|
| Asia | median of 12 rows (3 N x 2 ranks x 2 variants), 2w / 4w | 0.18 / 0.20 | 0.11 / 0.16 | 0.19 / 0.19 | 0.19 / 0.20 | 0.21 / 0.23 | 0.14 / 0.15 |
| NY AM | median of 12 rows (3 N x 2 ranks x 2 variants), 2w / 4w | 0.15 / 0.18 | 0.19 / 0.19 | 0.17 / 0.18 | 0.16 / 0.17 | 0.18 / 0.18 | 0.19 / 0.21 |
| NY PM | median of 12 rows (3 N x 2 ranks x 2 variants), 2w / 4w | 0.36 / 0.36 | 0.36 / 0.36 | 0.36 / 0.35 | 0.36 / 0.35 | 0.36 / 0.36 | 0.36 / 0.36 |
| London | median of 12 rows (3 N x 2 ranks x 2 variants), 2w / 4w | 0.10 / 0.09 | 0.10 / 0.10 | 0.11 / 0.11 | 0.11 / 0.11 | 0.11 / 0.10 | 0.10 / 0.08 |
| Four sessions summed | median of 12 rows (3 N x 2 ranks x 2 variants), 2w / 4w | 0.54 / 0.63 | 0.55 / 0.58 | 0.50 / 0.59 | 0.60 / 0.61 | 0.64 / 0.69 | 0.53 / 0.57 |

| session | plain / prior-year filter (2w) | rank ulcer / rank $/wk (2w) | fixed mix | all pool | best single row (2w, N index, rank, variant) |
|---|---|---|---|---|---|
| Asia | 0.18 / 0.17 | 0.18 / 0.17 | 0.42 | 0.28 | 0.26 (lookback 6, N 5, ulcer, plain; $/wk 2,410, ulcer 9,391) |
| NY AM | 0.16 / 0.19 | 0.17 / 0.17 | 0.46 | 0.37 | 0.30 (lookback 3, N 8, wk, py; $/wk 4,979, ulcer 16,755) |
| NY PM | 0.25 / 0.36 | 0.36 / 0.36 | 0.26 | 0.33 | 0.53 (lookback 3, N 3, wk, py; $/wk 2,219, ulcer 4,174) |
| London | 0.06 / 0.11 | 0.11 / 0.10 | 0.11 | 0.12 | 0.20 (lookback 1, N 3, wk, py; $/wk 1,738, ulcer 8,798) |
| Four sessions summed | 0.43 / 0.65 | 0.60 / 0.52 | 0.78 | 0.59 | 0.91 (lookback 5, N 8/8/all7/3, ulcer, py; $/wk 13,785, ulcer 15,195) |

## 3. Recent first: last 6 months and last 3 months of the out-of-sample curve (2-week steps, rank ulcer, plain; cell = $/wk | ulcer)

### last 6 months (2026-05..2026-10)

**Asia**

| lookback | N=3 | N=5 | N=8 |
|---|---|---|---|
| 1 | 3,684 / 3,960 (worst wk -7,114, DD -10,761) | 5,521 / 5,072 (worst wk -8,735, DD -13,639) | 9,665 / 8,173 (worst wk -12,649, DD -23,115) |
| 3 | 3,211 / 6,395 (worst wk -6,295, DD -19,335) | 5,922 / 7,822 (worst wk -8,978, DD -23,868) | 8,219 / 8,664 (worst wk -11,595, DD -28,042) |
| 4 | 4,003 / 6,727 (worst wk -6,295, DD -20,452) | 5,635 / 8,075 (worst wk -8,978, DD -24,407) | 8,333 / 11,027 (worst wk -14,813, DD -31,470) |
| 5 | 3,211 / 4,264 (worst wk -5,067, DD -10,995) | 5,081 / 6,135 (worst wk -11,413, DD -13,190) | 7,517 / 9,990 (worst wk -14,920, DD -24,728) |
| 6 | 2,955 / 3,401 (worst wk -5,067, DD -9,461) | 5,568 / 5,582 (worst wk -8,480, DD -14,708) | 8,151 / 7,325 (worst wk -13,107, DD -21,094) |
| 12 | 3,314 / 3,786 (worst wk -5,067, DD -10,591) | 5,624 / 3,966 (worst wk -7,447, DD -14,326) | 9,388 / 4,765 (worst wk -6,677, DD -14,093) |
| fixed mix (3 books) | 5,346 / 3,011 (worst wk -3,479, DD -8,558) | | |
| all pool (45 books) | 68,890 / 45,877 (worst wk -62,227, DD -127,807) | | |

**NY AM**

| lookback | N=3 | N=5 | N=8 |
|---|---|---|---|
| 1 | 2,099 / 5,361 (worst wk -6,647, DD -14,101) | 3,578 / 6,094 (worst wk -6,321, DD -15,157) | 7,693 / 5,535 (worst wk -13,176, DD -20,337) |
| 3 | 1,021 / 5,746 (worst wk -4,521, DD -16,473) | 3,121 / 5,462 (worst wk -8,455, DD -16,255) | 5,995 / 6,447 (worst wk -13,492, DD -24,159) |
| 4 | 2,176 / 5,993 (worst wk -6,368, DD -15,597) | 4,350 / 3,971 (worst wk -7,907, DD -12,540) | 7,117 / 6,150 (worst wk -13,492, DD -20,374) |
| 5 | 1,724 / 2,622 (worst wk -5,518, DD -8,205) | 3,290 / 3,865 (worst wk -6,667, DD -11,131) | 6,346 / 6,234 (worst wk -13,492, DD -16,262) |
| 6 | 1,730 / 3,266 (worst wk -4,308, DD -8,505) | 3,322 / 3,626 (worst wk -4,092, DD -10,253) | 6,513 / 5,391 (worst wk -5,783, DD -16,630) |
| 12 | 1,763 / 3,844 (worst wk -5,268, DD -9,469) | 4,373 / 3,718 (worst wk -7,861, DD -12,477) | 8,652 / 5,087 (worst wk -8,228, DD -16,791) |
| fixed mix (8 books) | 15,643 / 8,082 (worst wk -11,608, DD -27,540) | | |
| all pool (31 books) | 46,875 / 32,157 (worst wk -34,903, DD -103,799) | | |

**NY PM**

| lookback | N=3 | N=5 | N=all 7 |
|---|---|---|---|
| 1 | 2,982 / 3,863 (worst wk -6,306, DD -12,890) | 4,847 / 4,935 (worst wk -6,588, DD -14,901) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| 3 | 3,013 / 4,427 (worst wk -6,595, DD -13,210) | 5,763 / 4,794 (worst wk -7,811, DD -14,053) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| 4 | 3,580 / 4,407 (worst wk -8,361, DD -15,616) | 6,055 / 4,767 (worst wk -4,476, DD -15,353) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| 5 | 4,367 / 5,122 (worst wk -8,361, DD -19,577) | 5,818 / 5,524 (worst wk -7,491, DD -21,337) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| 6 | 3,708 / 5,813 (worst wk -3,707, DD -19,577) | 6,185 / 5,573 (worst wk -4,476, DD -21,337) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| 12 | 3,231 / 3,359 (worst wk -3,707, DD -11,684) | 5,800 / 3,600 (worst wk -6,152, DD -13,720) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) |
| fixed mix (4 books) | 4,629 / 2,723 (worst wk -4,238, DD -12,121) | | |
| all pool (7 books) | 8,367 / 4,439 (worst wk -7,058, DD -14,808) | | |

**London**

| lookback | N=1 | N=2 | N=3 |
|---|---|---|---|
| 1 | 1,310 / 1,635 (worst wk -3,052, DD -4,842) | 2,047 / 2,825 (worst wk -5,346, DD -7,638) | 4,174 / 3,681 (worst wk -8,547, DD -13,295) |
| 3 | 1,680 / 1,294 (worst wk -2,673, DD -3,809) | 3,431 / 2,616 (worst wk -5,346, DD -7,638) | 4,847 / 2,915 (worst wk -5,503, DD -8,575) |
| 4 | 1,768 / 1,273 (worst wk -2,673, DD -3,809) | 3,431 / 2,616 (worst wk -5,346, DD -7,638) | 4,847 / 2,915 (worst wk -5,503, DD -8,575) |
| 5 | 1,768 / 1,273 (worst wk -2,673, DD -3,809) | 3,431 / 2,616 (worst wk -5,346, DD -7,638) | 4,847 / 2,915 (worst wk -5,503, DD -8,575) |
| 6 | 1,768 / 1,273 (worst wk -2,673, DD -3,809) | 3,431 / 2,616 (worst wk -5,346, DD -7,638) | 4,847 / 2,915 (worst wk -5,503, DD -8,575) |
| 12 | 1,751 / 1,349 (worst wk -2,673, DD -3,829) | 3,431 / 2,616 (worst wk -5,346, DD -7,638) | 4,847 / 2,915 (worst wk -5,503, DD -8,575) |
| fixed mix (3 books) | 4,768 / 4,241 (worst wk -8,344, DD -12,149) | | |
| all pool (4 books) | 6,431 / 4,680 (worst wk -7,768, DD -15,392) | | |

**Four sessions summed**

| lookback | N=3/3/3/1 | N=5/5/5/2 | N=8/8/all7/3 |
|---|---|---|---|
| 1 | 10,075 / 5,392 (worst wk -8,469, DD -19,842) | 15,992 / 5,851 (worst wk -11,337, DD -17,764) | 29,898 / 7,201 (worst wk -13,171, DD -23,596) |
| 3 | 8,925 / 5,762 (worst wk -4,672, DD -17,753) | 18,237 / 5,622 (worst wk -8,905, DD -19,187) | 27,428 / 7,950 (worst wk -21,200, DD -34,764) |
| 4 | 11,526 / 5,660 (worst wk -11,398, DD -19,564) | 19,471 / 5,929 (worst wk -10,002, DD -21,079) | 28,664 / 7,957 (worst wk -18,416, DD -28,113) |
| 5 | 11,070 / 3,523 (worst wk -6,101, DD -12,871) | 17,620 / 4,287 (worst wk -12,136, DD -15,717) | 27,077 / 8,232 (worst wk -18,598, DD -30,278) |
| 6 | 10,161 / 4,616 (worst wk -9,346, DD -14,397) | 18,507 / 4,954 (worst wk -13,281, DD -16,709) | 27,877 / 7,106 (worst wk -11,183, DD -25,501) |
| 12 | 10,058 / 3,820 (worst wk -6,724, DD -14,498) | 19,228 / 4,191 (worst wk -1,607, DD -15,161) | 31,253 / 4,775 (worst wk -2,894, DD -22,176) |
| fixed mix (18 books) | 30,385 / 5,387 (worst wk -7,727, DD -28,599) | | |
| all pool (87 books) | 130,563 / 40,926 (worst wk -54,308, DD -136,258) | | |

### last 3 months (2026-08..2026-10)

**Asia**

| lookback | N=3 | N=5 | N=8 |
|---|---|---|---|
| 1 | 3,458 / 4,399 (worst wk -5,815, DD -10,761) | 5,057 / 5,117 (worst wk -8,735, DD -13,639) | 6,906 / 9,097 (worst wk -12,388, DD -23,115) |
| 3 | 1,673 / 8,773 (worst wk -6,295, DD -19,335) | 3,743 / 10,409 (worst wk -8,978, DD -23,868) | 6,536 / 10,566 (worst wk -11,595, DD -28,042) |
| 4 | 1,823 / 9,384 (worst wk -6,295, DD -20,452) | 3,362 / 11,235 (worst wk -8,978, DD -24,407) | 5,640 / 14,707 (worst wk -14,813, DD -31,470) |
| 5 | 2,220 / 5,525 (worst wk -4,946, DD -10,986) | 3,239 / 7,373 (worst wk -7,699, DD -12,516) | 5,588 / 12,398 (worst wk -11,981, DD -24,728) |
| 6 | 1,665 / 4,412 (worst wk -4,946, DD -9,452) | 3,653 / 6,567 (worst wk -7,699, DD -14,396) | 4,688 / 8,764 (worst wk -12,068, DD -21,094) |
| 12 | 2,662 / 4,955 (worst wk -4,946, DD -10,582) | 3,966 / 4,330 (worst wk -3,802, DD -10,751) | 7,757 / 4,954 (worst wk -6,159, DD -11,550) |
| fixed mix (3 books) | 3,826 / 3,348 (worst wk -959, DD -8,549) | | |
| all pool (45 books) | 56,201 / 54,684 (worst wk -61,042, DD -127,807) | | |

**NY AM**

| lookback | N=3 | N=5 | N=8 |
|---|---|---|---|
| 1 | -338 / 6,896 (worst wk -6,647, DD -14,101) | 355 / 8,148 (worst wk -6,321, DD -15,157) | 4,076 / 7,118 (worst wk -13,176, DD -20,337) |
| 3 | 1,380 / 3,475 (worst wk -3,438, DD -7,611) | 2,918 / 4,140 (worst wk -7,796, DD -11,682) | 6,549 / 5,259 (worst wk -13,492, DD -15,546) |
| 4 | 1,602 / 8,202 (worst wk -6,368, DD -15,597) | 3,094 / 4,233 (worst wk -7,907, DD -12,540) | 5,463 / 5,451 (worst wk -13,492, DD -15,546) |
| 5 | 2,297 / 2,228 (worst wk -5,518, DD -6,623) | 3,507 / 3,312 (worst wk -6,667, DD -8,326) | 5,973 / 5,940 (worst wk -13,492, DD -16,232) |
| 6 | 850 / 4,053 (worst wk -4,308, DD -8,505) | 3,643 / 2,956 (worst wk -3,240, DD -9,201) | 6,024 / 4,933 (worst wk -5,783, DD -16,630) |
| 12 | 909 / 4,608 (worst wk -5,268, DD -9,332) | 3,475 / 2,917 (worst wk -7,861, DD -10,450) | 5,165 / 5,255 (worst wk -8,228, DD -16,080) |
| fixed mix (8 books) | 11,150 / 8,125 (worst wk -3,993, DD -27,540) | | |
| all pool (31 books) | 35,406 / 36,124 (worst wk -34,903, DD -93,552) | | |

**NY PM**

| lookback | N=3 | N=5 | N=all 7 |
|---|---|---|---|
| 1 | 2,060 / 4,296 (worst wk -5,546, DD -12,890) | 4,263 / 4,037 (worst wk -6,588, DD -11,166) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| 3 | 3,112 / 1,458 (worst wk -223, DD -5,102) | 5,295 / 2,702 (worst wk -1,913, DD -7,730) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| 4 | 2,617 / 1,904 (worst wk -8,361, DD -8,585) | 5,289 / 2,638 (worst wk -1,913, DD -7,730) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| 5 | 3,252 / 2,188 (worst wk -8,361, DD -8,585) | 5,357 / 3,126 (worst wk -7,491, DD -8,258) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| 6 | 2,991 / 4,627 (worst wk -3,707, DD -12,430) | 6,119 / 3,350 (worst wk -3,616, DD -9,368) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| 12 | 2,771 / 4,101 (worst wk -3,707, DD -11,684) | 5,427 / 3,413 (worst wk -4,787, DD -9,024) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) |
| fixed mix (4 books) | 4,340 / 2,089 (worst wk -4,238, DD -7,269) | | |
| all pool (7 books) | 7,806 / 3,459 (worst wk -5,363, DD -12,720) | | |

**London**

| lookback | N=1 | N=2 | N=3 |
|---|---|---|---|
| 1 | 732 / 2,023 (worst wk -3,052, DD -4,842) | 1,924 / 2,934 (worst wk -4,898, DD -6,749) | 3,682 / 4,557 (worst wk -8,547, DD -13,295) |
| 3 | 1,461 / 1,444 (worst wk -2,449, DD -3,402) | 3,107 / 2,816 (worst wk -4,898, DD -6,749) | 4,455 / 3,196 (worst wk -3,949, DD -8,358) |
| 4 | 1,643 / 1,406 (worst wk -2,449, DD -3,402) | 3,107 / 2,816 (worst wk -4,898, DD -6,749) | 4,455 / 3,196 (worst wk -3,949, DD -8,358) |
| 5 | 1,643 / 1,406 (worst wk -2,449, DD -3,402) | 3,107 / 2,816 (worst wk -4,898, DD -6,749) | 4,455 / 3,196 (worst wk -3,949, DD -8,358) |
| 6 | 1,643 / 1,406 (worst wk -2,449, DD -3,402) | 3,107 / 2,816 (worst wk -4,898, DD -6,749) | 4,455 / 3,196 (worst wk -3,949, DD -8,358) |
| 12 | 1,644 / 1,405 (worst wk -2,449, DD -3,402) | 3,107 / 2,816 (worst wk -4,898, DD -6,749) | 4,455 / 3,196 (worst wk -3,949, DD -8,358) |
| fixed mix (3 books) | 5,135 / 4,020 (worst wk -6,556, DD -11,529) | | |
| all pool (4 books) | 6,599 / 4,596 (worst wk -7,485, DD -13,648) | | |

**Four sessions summed**

| lookback | N=3/3/3/1 | N=5/5/5/2 | N=8/8/all7/3 |
|---|---|---|---|
| 1 | 5,912 / 5,776 (worst wk -8,469, DD -15,168) | 11,600 / 6,675 (worst wk -11,337, DD -17,044) | 22,471 / 8,474 (worst wk -13,171, DD -23,596) |
| 3 | 7,625 / 5,281 (worst wk -4,672, DD -15,350) | 15,064 / 5,567 (worst wk -8,321, DD -18,151) | 25,347 / 8,741 (worst wk -21,200, DD -27,475) |
| 4 | 7,684 / 7,638 (worst wk -11,398, DD -19,564) | 14,851 / 7,518 (worst wk -10,002, DD -21,079) | 23,365 / 9,206 (worst wk -18,416, DD -28,113) |
| 5 | 9,412 / 3,336 (worst wk -6,101, DD -12,871) | 15,210 / 3,432 (worst wk -12,136, DD -12,136) | 23,822 / 9,331 (worst wk -18,598, DD -30,278) |
| 6 | 7,150 / 5,214 (worst wk -9,346, DD -14,397) | 16,522 / 4,853 (worst wk -13,281, DD -16,709) | 22,974 / 7,371 (worst wk -8,499, DD -23,670) |
| 12 | 7,986 / 4,953 (worst wk -6,724, DD -14,498) | 15,975 / 4,002 (worst wk -1,607, DD -12,054) | 25,183 / 4,701 (worst wk -1,069, DD -12,492) |
| fixed mix (18 books) | 24,452 / 6,212 (worst wk -7,727, DD -28,599) | | |
| all pool (87 books) | 106,012 / 49,244 (worst wk -54,308, DD -136,258) | | |

## 4. By year (2-week steps, rank ulcer, plain, N = middle size; cell = $/wk | ulcer | max DD)

**Asia, N = 5**

| lookback | 2023 (Oct-Dec) | 2024 | 2025 | 2026 (Jan-Oct) |
|---|---|---|---|---|
| 1 | 2,738 / 2,471 / -6,565 | 1,430 / 14,813 / -36,873 | 973 / 27,884 / -62,542 | 4,927 / 8,956 / -29,171 |
| 3 | 2,429 / 1,189 / -3,565 | 2,259 / 6,974 / -18,486 | -502 / 25,608 / -46,415 | 4,601 / 12,341 / -30,455 |
| 4 | 1,850 / 1,323 / -4,149 | 1,309 / 11,618 / -25,582 | 1,786 / 10,617 / -45,934 | 4,619 / 12,263 / -30,186 |
| 5 | 2,203 / 1,431 / -3,600 | 1,409 / 9,071 / -24,925 | 794 / 15,639 / -29,566 | 4,837 / 7,132 / -19,174 |
| 6 | 2,718 / 1,079 / -3,697 | 1,880 / 8,970 / -29,837 | 486 / 11,882 / -28,364 | 4,992 / 7,791 / -22,405 |
| 12 | n/a | 302 / 10,406 / -22,796 | -48 / 14,631 / -39,664 | 4,789 / 9,442 / -31,446 |
| fixed mix | 891 / 2,475 / -5,698 | 1,017 / 5,369 / -12,877 | 1,261 / 5,348 / -12,823 | 4,860 / 4,834 / -23,767 |
| all pool | 9,443 / 72,220 / -174,130 | 17,344 / 91,030 / -232,908 | 14,523 / 117,099 / -263,901 | 61,959 / 77,651 / -329,709 |

**NY AM, N = 5**

| lookback | 2023 (Oct-Dec) | 2024 | 2025 | 2026 (Jan-Oct) |
|---|---|---|---|---|
| 1 | 3,179 / 4,876 / -11,878 | 1,918 / 13,855 / -38,586 | 2,354 / 14,564 / -38,332 | 2,475 / 17,583 / -47,371 |
| 3 | -1,186 / 15,746 / -25,717 | 2,375 / 7,846 / -29,424 | 2,372 / 13,968 / -34,086 | 2,916 / 10,876 / -28,644 |
| 4 | 2,106 / 3,886 / -10,745 | 2,439 / 9,877 / -30,010 | 1,431 / 14,815 / -49,878 | 3,152 / 14,010 / -37,837 |
| 5 | 2,172 / 3,612 / -7,808 | 1,961 / 12,961 / -34,798 | 2,506 / 9,593 / -30,811 | 1,462 / 25,414 / -60,917 |
| 6 | 2,766 / 3,716 / -7,808 | 1,246 / 15,605 / -38,645 | 2,888 / 8,353 / -30,811 | 1,074 / 31,970 / -73,652 |
| 12 | n/a | 1,618 / 10,820 / -29,296 | 1,530 / 14,639 / -45,407 | 2,948 / 8,775 / -29,303 |
| fixed mix | 3,434 / 10,836 / -28,844 | 3,214 / 10,433 / -33,058 | 5,488 / 13,047 / -43,938 | 11,508 / 14,639 / -56,611 |
| all pool | 14,487 / 39,511 / -124,950 | 17,844 / 32,361 / -109,449 | 20,819 / 74,197 / -264,872 | 34,941 / 78,342 / -261,601 |

**NY PM, N = 5**

| lookback | 2023 (Oct-Dec) | 2024 | 2025 | 2026 (Jan-Oct) |
|---|---|---|---|---|
| 1 | 3,020 / 4,945 / -12,327 | 1,673 / 10,549 / -28,135 | 2,415 / 7,889 / -30,688 | 3,986 / 5,013 / -14,901 |
| 3 | 3,087 / 4,608 / -12,327 | 2,557 / 13,154 / -35,308 | 1,799 / 9,021 / -27,167 | 3,943 / 8,676 / -26,160 |
| 4 | 2,947 / 4,687 / -12,327 | 2,442 / 11,402 / -30,766 | 1,753 / 11,228 / -27,654 | 3,996 / 9,176 / -28,151 |
| 5 | 2,494 / 4,690 / -12,327 | 2,079 / 11,482 / -29,113 | 1,790 / 10,688 / -27,167 | 3,828 / 8,747 / -26,662 |
| 6 | 2,494 / 4,690 / -12,327 | 2,119 / 14,621 / -37,426 | 1,753 / 11,599 / -27,654 | 4,053 / 8,766 / -26,662 |
| 12 | n/a | 1,448 / 13,939 / -38,643 | 3,258 / 6,162 / -19,666 | 3,602 / 8,767 / -26,587 |
| fixed mix | 1,725 / 4,061 / -15,835 | 1,325 / 10,467 / -29,188 | 2,157 / 5,998 / -17,976 | 3,220 / 4,570 / -14,826 |
| all pool | 2,418 / 8,488 / -24,356 | 2,662 / 13,806 / -40,096 | 3,611 / 8,707 / -35,977 | 5,629 / 6,985 / -24,765 |

**London, N = 2**

| lookback | 2023 (Oct-Dec) | 2024 | 2025 | 2026 (Jan-Oct) |
|---|---|---|---|---|
| 1 | 1,475 / 1,646 / -4,298 | 364 / 6,914 / -18,785 | 334 / 11,908 / -30,280 | 1,157 / 11,022 / -26,233 |
| 3 | 1,004 / 3,257 / -6,490 | 718 / 11,009 / -28,664 | 166 / 16,996 / -32,459 | 2,125 / 6,846 / -18,888 |
| 4 | 1,004 / 3,257 / -6,490 | 330 / 11,486 / -28,664 | 140 / 24,528 / -37,631 | 2,125 / 6,846 / -18,888 |
| 5 | 1,004 / 3,257 / -6,490 | 86 / 12,826 / -30,837 | -202 / 31,785 / -43,980 | 2,125 / 6,846 / -18,888 |
| 6 | 1,004 / 3,257 / -6,490 | 481 / 8,070 / -22,517 | 290 / 17,935 / -33,488 | 2,125 / 6,846 / -18,888 |
| 12 | n/a | 610 / 9,307 / -23,569 | 308 / 15,933 / -30,866 | 2,210 / 6,403 / -18,593 |
| fixed mix | 586 / 10,035 / -22,915 | 1,468 / 3,608 / -12,817 | 779 / 22,474 / -45,648 | 3,016 / 10,223 / -26,693 |
| all pool | 858 / 9,524 / -24,583 | 1,741 / 4,924 / -19,880 | 947 / 27,873 / -56,031 | 4,089 / 12,560 / -33,927 |

**Four sessions summed, N = 5/5/5/2**

| lookback | 2023 (Oct-Dec) | 2024 | 2025 | 2026 (Jan-Oct) |
|---|---|---|---|---|
| 1 | 10,412 / 5,072 / -14,457 | 5,385 / 19,813 / -57,970 | 6,076 / 17,654 / -82,789 | 12,545 / 18,485 / -66,254 |
| 3 | 5,334 / 5,355 / -14,551 | 7,909 / 8,966 / -32,764 | 3,835 / 19,928 / -102,172 | 13,585 / 19,938 / -65,216 |
| 4 | 7,907 / 2,876 / -9,126 | 6,520 / 10,381 / -37,660 | 5,109 / 18,349 / -95,847 | 13,893 / 23,978 / -72,383 |
| 5 | 7,874 / 2,961 / -9,066 | 5,536 / 10,241 / -36,895 | 4,889 / 15,540 / -72,481 | 12,252 / 18,563 / -58,324 |
| 6 | 8,983 / 2,678 / -8,611 | 5,726 / 10,353 / -36,461 | 5,416 / 12,972 / -61,874 | 12,245 / 22,367 / -71,414 |
| 12 | n/a | 3,977 / 13,050 / -41,955 | 5,048 / 15,654 / -53,948 | 13,550 / 15,333 / -54,534 |
| fixed mix | 6,636 / 7,926 / -23,403 | 7,024 / 9,425 / -27,499 | 9,685 / 13,135 / -49,514 | 22,605 / 22,937 / -93,135 |
| all pool | 27,206 / 29,692 / -92,157 | 39,591 / 56,456 / -153,669 | 39,900 / 107,520 / -428,802 | 106,619 / 132,030 / -568,240 |

(2023 reference rows cover Apr-Dec; rotation rows cover only 2023-10 onward. 12-month rows have no 2023 steps.)

## 5. Is it inside noise? Block bootstrap over steps, paying for the best of the rows tried

White reality-check style: 60 rotation rows (5 lookbacks 1-6 x 3 N x 2 ranks x 2 variants, 2-week steps; the 12-month reference excluded), 80 steps, stationary block bootstrap (mean block 3 steps, 2,000 draws), the same resampled step sequence applied to every row and the reference. Statistic = $/wk per unit ulcer of the row minus the reference; p = share of centred draws whose best row gain is at least the observed best gain, i.e. the chance that the best of 60 looks this good by luck. Second line: ulcer per held lot (lower is better).

| session | reference | rows beating ref (of 60) | best row (lookback, N index, rank, variant) | best row per ulcer vs reference | p (paid for 60 rows) | rows lower ulcer per lot | p (ulcer per lot) |
|---|---|---|---|---|---|---|---|
| Asia | fixed mix | 0 | 6, 1, ulcer, plain | 0.26 vs 0.45 | **1.00** | 0 | 1.00 |
| Asia | all pool | 0 | 6, 1, ulcer, plain | 0.26 vs 0.32 | **1.00** | 5 | 1.00 |
| NY AM | fixed mix | 0 | 3, 2, wk, py | 0.30 vs 0.49 | **0.99** | 0 | 1.00 |
| NY AM | all pool | 0 | 3, 2, wk, py | 0.30 vs 0.38 | **0.94** | 2 | 1.00 |
| NY PM | fixed mix | 44 | 3, 0, wk, py | 0.53 vs 0.26 | **0.30** | 47 | 0.61 |
| NY PM | all pool | 17 | 3, 0, wk, py | 0.53 vs 0.36 | **0.55** | 13 | 0.94 |
| London | fixed mix | 16 | 1, 2, wk, py | 0.20 vs 0.12 | **0.41** | 29 | 0.99 |
| London | all pool | 16 | 1, 2, wk, py | 0.20 vs 0.13 | **0.37** | 17 | 0.99 |
| Four sessions summed | fixed mix | 5 | 5, 2, ulcer, py | 0.91 vs 0.81 | **0.82** | 21 | 0.94 |
| Four sessions summed | all pool | 24 | 5, 2, ulcer, py | 0.91 vs 0.62 | **0.58** | 37 | 0.82 |

Reading: no row separates from either reference at any usual level (smallest p 0.30). With 80 steps, 60 rows and a menu built on the last 6 months, treat differences under about 20% on return per ulcer as not distinguishable. The one statement the data does support is negative: in Asia and NY AM the fixed mix is better than every rotation row on return per unit ulcer (p near 1.0 that a rotation row only looks better by chance), and that comparison is biased in favour of the fixed mix.

## 6. HEAVY version (not started; waits for Josh yes)

The light test freezes each book at its stored bare setting and sums streams. The heavy version would re-fit settings and weights with the ENGINE at every step, in true walk-forward order, with the real stack rules, caps, locks and size-dependent fills: for each of the 80 two-week steps (a) rebuild the candidate menu using only data before the step, (b) re-run the stack and the leave-one-out / weight combos, (c) pick on the trailing lookback and score the next step. The earlier estimate is **131,796 month-runs** (3,138 sets = 9 x 242 + 4 x 80 + 5 x 80 + 3 x 80 leave-one-out combos, x 42 months; each extra weight level or lookback multiplies it; a menu rebuilt per step with a trailing-only fit multiplies it again). It would add: real stack rules and caps, size-dependent fills, a menu without the last-6-month look-ahead, weights by the stack add rule (variant c). **I wait for Josh yes; nothing started.** Given the light result (no row clearly beats the fixed mix or the pool, differences inside noise), the expected gain of the heavy run is small relative to its cost.

## 7. Files

- Page: autopilot/BOOK_ROTATION_WALKFORWARD.md; all rows: autopilot/BOOK_ROTATION_WALKFORWARD_ROWS.csv. Scripts (read-only, niced): load.py, walk.py, ana.py, boot.py, boot_all.py, gen.py under the agent scratchpad rot/ (reuse code/th_combo/combo_score.py loaders). No engine file, gate, rule, definition or live item touched. No new engine runs.
