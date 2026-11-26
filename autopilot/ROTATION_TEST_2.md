# ROTATION TEST 2: qualify on history, one pick per family, switch on by recent results (W-ROT2)

**QUICK SCREEN label on every number below** unless it says EXACT: grid weekly arrays (th_grid/gcore2 tape walk, not the exact engine, not calibrated against it), 1 NQ lot per book at $20/point, grid cost in, no stack rules, no account layers, no depth fills. The exact re-score of the picked books is in the last section (filled when the sets land). Order: Josh 17:06Z / 17:09Z (autopilot/DIRECTIVE_ROTATION_TEST_2_1711Z.md), followed word for word, 108 versions per session, none added. Written 2026-11-26 by W-ROT2.

## ANSWER FIRST (QUICK SCREEN)

1. **FAIL against zero in all four sessions and in the four-session sum.** After the best-of-108 luck penalty the best version is below zero in every case (Asia -30, London -8, NY AM -8, NY PM -55, four summed -17 $/lot/wk) and the reality-check p-values are 0.56 to 0.95. Only 2 of 108 NY PM versions, 23 of 108 four-session versions, 28 of 108 London, 52 of 108 Asia and 70 of 108 NY AM versions are above zero at all, and the median version is at or below zero in every scope except NY AM (+18).
2. **FAIL against the equal-weight basket in all five scopes.** London (+37 after haircut, p 0.23) and NY PM (+33, p 0.27) look better than equal-weight, but only because their equal-weight basket (all qualified families held, no ranking) loses money (London -46, NY PM -84 $/lot/wk); that is not different from luck at p below 0.10 and it is still below zero. In Asia the equal-weight basket itself earns +108 $/lot/wk (bootstrap 90% interval +11 to +204) and **no ranked version gets close** (best 30, 0 of 108 above equal-weight). Ranking by income per drawdown on top of the qualification does not help; the qualification (>=30 trades, profitable in every past half-year, >=half of the family profitable) is where whatever edge exists comes from, and only Asia shows it.
3. **Recency adds in the last months, not over the three years.** Median change in $/lot/wk versus the 100%-history twin (same size, refit, on/off), 50/50 and 100% trailing: Asia -17 / -16, London +68 / +59, NY AM -10 / -11, NY PM -5 / -4, four summed +11 / +6, so over the whole OOS it helps in London and slightly in the sum and hurts elsewhere. In the last 6 months the picture is clear: median L6M $/lot/wk of the 100%-history versions is Asia -82, London -341, NY AM -210, four summed -145 (NY PM +78), against 50/50 and 100% trailing at Asia +50 / +66, London -7, NY AM -108 / -117, four summed +14. History-only picks bleed recently; blends stop the bleeding but earn little. The best versions are mostly 50/50 with the 4-month window, which is the best-of-108 choice and carries the luck haircut.
4. **Quick screen size of money.** Every number here is per lot of a median cell of a family, not of a best cell. Four sessions summed, best version: 21 $/lot/wk, max drawdown 1,904 $/lot, worst week -901 $/lot, L6M +46, L3M +70. The fixed live mixes (hindsight) earned 529 $/lot/wk on the same weeks in stage A. This test does not beat them and does not claim to; its purpose is whether qualifying plus rotating works with no hindsight, and the answer from the quick screen is no (FAIL vs zero).
5. **Turnover and book count (the cost of running it).** Turnover per refit 0.23 to 0.90 of the slots replaced over the 108 versions (best versions 0.37 to 0.61). Different books the last 6 months would have needed: best versions Asia 66, London 44, NY AM 54, NY PM 11, four-session best 253 (median version 170); fewest 71, most 439 for the four-session sum. Eligible families per date: 4,100 to 17,400 per session (table per session). A live file cannot hold that many books; this is a research test, not a build.
6. **Honest reading of the luck penalty.** 108 versions, but the 100%-history rows are duplicates between the 3M and 4M window (18 of the 108 rows are the same series as another row), so the true count of distinct tries is 90; the penalty is applied to all 108 as ordered. A best-of-108 haircut is 38 to 91 $/lot/wk (block bootstrap, 2,000 draws, block 4 weeks, White reality check). Nothing survives it.

### Verdicts (PASS = best version after the best-of-108 haircut is above the benchmark AND the reality-check p is 0.10 or lower; else FAIL)

| session | best version (by $/wk per unit max DD) | $/lot/wk | best-of-108 haircut | after haircut vs zero | RC p vs zero | vs zero | after haircut vs EW | RC p vs EW | vs EW |
|---|---|---|---|---|---|---|---|---|---|
| Asia | 50/50 w4M N12 r2w always | 20 | 60 | -30 | 0.83 | **FAIL** | -134 | 1.00 | **FAIL** |
| London | 50/50 w4M N5 r1w gate | 52 | 60 | -8 | 0.59 | **FAIL** | 37 | 0.23 | **FAIL** |
| NY AM | 50/50 w4M N8 r1w always | 83 | 91 | -8 | 0.56 | **FAIL** | -35 | 0.68 | **FAIL** |
| NY PM | 100% hist w3M N5 r2w always | 19 | 74 | -55 | 0.95 | **FAIL** | 33 | 0.27 | **FAIL** |
| Four sessions summed | 50/50 w4M N8 r1w always | 21 | 38 | -17 | 0.81 | **FAIL** | -18 | 0.72 | **FAIL** |

Equal-weight basket against zero (no ranking, family median cells, refit 1 week; bootstrap 90% interval of the weekly mean): Asia +108 $/lot/wk [+11, +204] (PASS vs zero on its own: only session where the qualification alone earns money out of sample), London -46 [-140, +40], NY AM +27 [-108, +154], NY PM -84 [-128, -41] (loses), four summed +1 [-52, +55].

| equal-weight basket (refit 1w) | L3M | L6M | $/lot/wk | max DD $/lot | worst wk | 2023 Q4 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|
| Asia | 57 | 112 | 108 | 4,436 | -2,578 | -15 | 105 | 131 | 121 |
| London | -244 | -113 | -46 | 8,999 | -3,733 | -100 | -1 | -73 | -52 |
| NY AM | 142 | -177 | 27 | 14,948 | -3,547 | 10 | 86 | 84 | -113 |
| NY PM | -89 | -42 | -84 | 14,232 | -1,191 | -26 | -108 | -97 | -57 |
| four summed (per lot) | -34 | -55 | 1 | 3,757 | -2,266 | -33 | 21 | 11 | -25 |

## Rules as run (exactly the order; choices where the order is silent are marked)

- Walk: weekly dates 2023-10-01 to 2026-10-25 (weeks 26 to 185 of the grid, 160 weeks, OOS), ranking at date w uses weeks before w only. Refit 1, 2 and 4 weeks, all chains start at the same week. The 2025-11 tape hole is a zero week for every cell alike.
- Candidate set (same as stage A, QUICK SCREEN): every grid cell (file x param x bracket x mode both/long/short) with at least 5 trades over the whole 3.6 years, from bfl17 + real + p1real: Asia 14,501,940; London 16,818,394; NY AM 17,767,116; NY PM 17,777,269 cells.
- Families: the stage-A family rule, same bar type, same module and variant, all adjacent bar sizes, params, brackets and sides (the grid neighbour-graph components collapse to these groups): 22,981 (Asia), 37,656 (London), 40,022 (NY AM), 39,949 (NY PM) families exist in the stored set; 4,100 to 17,400 of them are eligible at a date.
- QUALIFY at each date, data before it only: (a) at least 30 trades to date; (b) profitable (sum above zero) in every fully-past calendar half-year (**choice**: 2023 H1 is not a full half-year in the data, which starts 2023-04-02, so it is not counted; the first counted one is 2023 H2, which becomes past on 2024-01-01; before that the half-year test passes everything, so Oct-Dec 2023 is only gated by (a) and (c); a half-year with no trades is not profitable); (c) at least half of the stored cells of its own family are profitable over all history to date.
- ONE PICK PER FAMILY: family score = median of its eligible cells' scores, the pick is the median cell (**choice**: lower median when the count is even).
- SCORE (**choice**: "income per unit of drawdown" = mean weekly points / max(max drawdown in points of the cumulative curve over the window, 2.5 points)); history = all weeks before the date, trailing = 13 weeks (3 months) or 17 weeks (4 months). Blend 100% history, 50/50, 100% trailing. The 100%-history rows do not depend on the window, so they repeat for 3M and 4M (kept, 108 rows as ordered).
- BASKET top 5, 8, 12 families, equal weight, 1 lot each; "per lot" divides by the basket size (an empty slot is cash). Refit 1, 2 and 4 weeks.
- ON/OFF: always on; or gate: a book trades the next period only if its own trailing 3-month (13-week) quick-screen result at the refit date is above zero (off = flat, per lot still divided by the basket size).
- Comparators with no hindsight: zero; equal-weight of all eligible families (one median cell per family by the 100%-history score, no ranking, same refit); equal-weight of all eligible cells (second row, refit 1 week); the 100%-history version (same size, refit, on/off).
- Metrics from weekly $: income per lot per week, max drawdown (per lot, of the cumulative weekly curve), worst week, L6M = last 26 weeks, L3M = last 13 weeks, by year (2023 = Oct-Dec only), share of refit blocks beating the equal-weight basket (same refit step, per lot), turnover = share of slots replaced per refit, distinct books over the refits whose period touches the last 26 weeks.
- Best-of-rows penalty: block bootstrap over the 160 weeks (block 4, 2,000 draws), White reality check over the 108 rows, per lot, versus zero and versus the equal-weight basket of the same refit step.
- "Best version" per session = highest income per unit of max drawdown among the 108 (drawdown first). The same table is in the parquet with every version (autopilot/ROTATION_TEST_2_ROWS.parquet, 540 rows = 108 x 5 scopes).

## Hindsight and survivor effects (read before trusting any row)

- The candidate set is the stored grid: cells with fewer than 5 trades over the whole 3.6 years were removed, a filter that looks at the full span (small and dwarfed by the 66.9 M cells, but it is not zero look-ahead).
- Modules, brackets and bar types in the grid were chosen by people who saw earlier data; 13 of 17 level modules had stale pre-06:00Z grid results (UNVERIFIED until re-stamped), as flagged in stage A.
- The quick screen is a tape walk, not the engine; stage B showed in test 1 how far apart the two can be, so the exact section matters more than these rows.
- Weekly bins; the weekly drawdown is coarser than the daily one; the first three months of OOS (Oct-Dec 2023) have no half-year test.
- The best-of-108 row is selected on the same weeks it is reported on; the haircut above is the correction. The equal-weight comparison has no selection and is therefore the more honest read.

# Per session tables (QUICK SCREEN, recent first: L3M, L6M, then all, then years)

## Asia (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023(Q4) | 2024 | 2025 | 2026 | beat EW | turnover | books L6M | L6M DD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST1: 50/50 w4M N12 r2w always | 122 | 52 | 20 | 2,549 | -1,266 | 44 | -17 | -20 | 109 | 41% | 0.61 | 66 | 1,383 |
| BEST2: 50/50 w4M N12 r2w gate | 122 | 52 | 19 | 2,563 | -1,266 | 44 | -17 | -20 | 106 | 41% | 0.61 | 66 | 1,383 |
| BEST3: 100% trail w4M N8 r1w always | 69 | 63 | 29 | 4,461 | -1,299 | 82 | 38 | -53 | 105 | 49% | 0.44 | 62 | 1,296 |
| BEST4: 100% trail w4M N8 r1w gate | 69 | 63 | 29 | 4,485 | -1,299 | 82 | 38 | -53 | 105 | 49% | 0.44 | 62 | 1,296 |
| BEST5: 50/50 w4M N8 r1w always | 60 | 47 | 24 | 3,752 | -1,299 | 67 | 30 | -48 | 95 | 48% | 0.44 | 63 | 1,296 |
| 100%-HISTORY best: 100% hist w3M N12 r4w always | -172 | -75 | 30 | 5,434 | -3,126 | 84 | 118 | -10 | -47 | 35% | 0.68 | 44 | 5,434 |
| EQUAL-WEIGHT family medians, refit 1w | 57 | 112 | 108 | 4,436 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 2w | 49 | 107 | 105 | 4,543 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 4w | 55 | 110 | 103 | 4,559 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT all eligible cells, refit 1w | - | - | 140 | - | - | - | - | - | - | - | - | - | - |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | - | 0 |

Per-version summary over all 108: positive $/lot/wk 52 of 108; median -1; best 30; worst -59. Versions beating zero in both L6M and L3M: 62. Versions with $/lot/wk above equal-weight: 0.
Median $/lot/wk by blend (does recency add): 100% history 4, 50/50 -8, 100% trailing -3. By on/off: always 0, gate -3. By basket size: 5 -> -8, 8 -> 1, 12 -> 9. By refit: 1w -7, 2w -1, 4w 3.
Recency vs 100%-history twin (same N, refit, on/off): median change $/lot/wk, 50/50 -17, 100% trailing -16.
Best-of-rows penalty (108 versions, block bootstrap 2,000 draws, block 4 weeks, White reality check): vs zero best-by-mean row 30 $/lot/wk, luck haircut 60, after -30, RC p 0.83, versions positive 52 of 108; vs equal-weight best row -74, haircut 60, after -134, RC p 1.00.
Eligible families per date (cells in brackets): 2023-10-01 5509 (2,447,888), 2023-12-31 7436 (2,927,289), 2024-06-30 10150 (2,909,642), 2024-12-29 9500 (1,895,740), 2025-06-29 10577 (1,456,472), 2025-12-28 9811 (1,381,822), 2026-06-28 10436 (671,210), 2026-10-18 9777 (642,375); min 4862, median 9893, max 11521.
Different books the last 6 months needed (best version): 66; median over 108 versions 47; fewest 20, most 118.

## London (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023(Q4) | 2024 | 2025 | 2026 | beat EW | turnover | books L6M | L6M DD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST1: 50/50 w4M N5 r1w gate | 33 | -13 | 52 | 3,694 | -1,776 | -68 | 89 | 5 | 101 | 56% | 0.41 | 44 | 2,592 |
| BEST2: 50/50 w4M N5 r1w always | 33 | -13 | 52 | 3,694 | -1,776 | -68 | 89 | 5 | 101 | 56% | 0.41 | 44 | 2,592 |
| BEST3: 100% trail w4M N5 r1w gate | -4 | -32 | 45 | 3,659 | -1,776 | -106 | 77 | 16 | 89 | 54% | 0.41 | 45 | 2,592 |
| BEST4: 100% trail w4M N5 r1w always | -4 | -32 | 45 | 3,659 | -1,776 | -106 | 77 | 16 | 89 | 54% | 0.41 | 45 | 2,592 |
| BEST5: 50/50 w4M N12 r4w always | -3 | 21 | 18 | 2,074 | -1,528 | -56 | -8 | 25 | 65 | 62% | 0.77 | 56 | 1,480 |
| 100%-HISTORY best: 100% hist w3M N5 r4w always | -412 | -295 | -22 | 11,423 | -1,708 | 222 | 45 | -56 | -140 | 57% | 0.48 | 20 | 8,195 |
| EQUAL-WEIGHT family medians, refit 1w | -244 | -113 | -46 | 8,999 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 2w | -251 | -128 | -46 | 8,904 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 4w | -249 | -122 | -43 | 8,772 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT all eligible cells, refit 1w | - | - | -47 | - | - | - | - | - | - | - | - | - | - |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | - | 0 |

Per-version summary over all 108: positive $/lot/wk 28 of 108; median -26; best 52; worst -112. Versions beating zero in both L6M and L3M: 14. Versions with $/lot/wk above equal-weight: 74.
Median $/lot/wk by blend (does recency add): 100% history -70, 50/50 -6, 100% trailing -8. By on/off: always -24, gate -29. By basket size: 5 -> -31, 8 -> -22, 12 -> -29. By refit: 1w -13, 2w -29, 4w -38.
Recency vs 100%-history twin (same N, refit, on/off): median change $/lot/wk, 50/50 68, 100% trailing 59.
Best-of-rows penalty (108 versions, block bootstrap 2,000 draws, block 4 weeks, White reality check): vs zero best-by-mean row 52 $/lot/wk, luck haircut 60, after -8, RC p 0.59, versions positive 28 of 108; vs equal-weight best row 98, haircut 61, after 37, RC p 0.23.
Eligible families per date (cells in brackets): 2023-10-01 17632 (7,725,161), 2023-12-31 14856 (4,284,661), 2024-06-30 10493 (1,399,354), 2024-12-29 9679 (716,562), 2025-06-29 7655 (256,947), 2025-12-28 7565 (238,418), 2026-06-28 4813 (73,622), 2026-10-18 4841 (69,631); min 4510, median 9160, max 17632.
Different books the last 6 months needed (best version): 44; median over 108 versions 44; fewest 20, most 101.

## NY AM (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023(Q4) | 2024 | 2025 | 2026 | beat EW | turnover | books L6M | L6M DD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST1: 50/50 w4M N8 r1w always | 46 | 32 | 83 | 2,214 | -1,449 | -40 | 63 | 200 | -2 | 51% | 0.39 | 54 | 1,260 |
| BEST2: 50/50 w4M N8 r1w gate | 46 | 32 | 76 | 2,214 | -1,449 | -40 | 58 | 183 | -2 | 51% | 0.39 | 54 | 1,260 |
| BEST3: 50/50 w4M N12 r1w always | 94 | 78 | 67 | 2,256 | -1,400 | 21 | 44 | 132 | 27 | 52% | 0.39 | 70 | 840 |
| BEST4: 100% trail w4M N8 r1w always | 46 | 32 | 78 | 2,710 | -2,047 | 42 | 35 | 193 | -2 | 52% | 0.39 | 55 | 1,260 |
| BEST5: 50/50 w4M N12 r1w gate | 81 | 72 | 62 | 2,256 | -1,400 | 21 | 43 | 121 | 23 | 51% | 0.39 | 70 | 840 |
| 100%-HISTORY best: 100% hist w3M N12 r4w gate | -37 | -108 | 52 | 7,590 | -4,966 | -134 | 110 | 144 | -78 | 52% | 0.50 | 30 | 4,412 |
| EQUAL-WEIGHT family medians, refit 1w | 142 | -177 | 27 | 14,948 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 2w | 142 | -191 | 18 | 15,271 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 4w | 148 | -187 | 17 | 15,222 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT all eligible cells, refit 1w | - | - | 66 | - | - | - | - | - | - | - | - | - | - |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | - | 0 |

Per-version summary over all 108: positive $/lot/wk 70 of 108; median 18; best 83; worst -66. Versions beating zero in both L6M and L3M: 24. Versions with $/lot/wk above equal-weight: 48.
Median $/lot/wk by blend (does recency add): 100% history 25, 50/50 5, 100% trailing 6. By on/off: always 12, gate 23. By basket size: 5 -> 16, 8 -> -9, 12 -> 24. By refit: 1w 28, 2w 17, 4w 5.
Recency vs 100%-history twin (same N, refit, on/off): median change $/lot/wk, 50/50 -10, 100% trailing -11.
Best-of-rows penalty (108 versions, block bootstrap 2,000 draws, block 4 weeks, White reality check): vs zero best-by-mean row 83 $/lot/wk, luck haircut 91, after -8, RC p 0.56, versions positive 70 of 108; vs equal-weight best row 56, haircut 91, after -35, RC p 0.68.
Eligible families per date (cells in brackets): 2023-10-01 15659 (7,391,090), 2023-12-31 15295 (4,672,125), 2024-06-30 12723 (1,742,325), 2024-12-29 16154 (1,574,772), 2025-06-29 14940 (893,843), 2025-12-28 16055 (928,930), 2026-06-28 10840 (234,714), 2026-10-18 9591 (216,853); min 9419, median 15298, max 17397.
Different books the last 6 months needed (best version): 54; median over 108 versions 42; fewest 18, most 120.

## NY PM (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023(Q4) | 2024 | 2025 | 2026 | beat EW | turnover | books L6M | L6M DD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST1: 100% hist w3M N5 r2w always | 190 | 182 | 19 | 12,534 | -2,117 | -91 | 107 | -86 | 78 | 65% | 0.37 | 11 | 991 |
| BEST2: 100% hist w4M N5 r2w always | 190 | 182 | 19 | 12,534 | -2,117 | -91 | 107 | -86 | 78 | 65% | 0.37 | 11 | 991 |
| BEST3: 50/50 w4M N5 r1w gate | 335 | 224 | -4 | 10,834 | -2,460 | 165 | -70 | -79 | 119 | 55% | 0.42 | 42 | 1,351 |
| BEST4: 50/50 w4M N5 r1w always | 335 | 224 | -4 | 10,834 | -2,460 | 165 | -70 | -79 | 119 | 55% | 0.42 | 42 | 1,351 |
| BEST5: 100% trail w3M N8 r4w always | 127 | 155 | -6 | 8,244 | -2,660 | 10 | -120 | 19 | 100 | 52% | 0.83 | 44 | 1,879 |
| 100%-HISTORY best: 100% hist w3M N5 r2w always | 190 | 182 | 19 | 12,534 | -2,117 | -91 | 107 | -86 | 78 | 65% | 0.37 | 11 | 991 |
| EQUAL-WEIGHT family medians, refit 1w | -89 | -42 | -84 | 14,232 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 2w | -72 | -33 | -87 | 14,725 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 4w | -72 | -39 | -95 | 16,088 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT all eligible cells, refit 1w | - | - | -70 | - | - | - | - | - | - | - | - | - | - |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | - | 0 |

Per-version summary over all 108: positive $/lot/wk 2 of 108; median -43; best 19; worst -115. Versions beating zero in both L6M and L3M: 95. Versions with $/lot/wk above equal-weight: 100.
Median $/lot/wk by blend (does recency add): 100% history -39, 50/50 -40, 100% trailing -55. By on/off: always -39, gate -45. By basket size: 5 -> -44, 8 -> -46, 12 -> -40. By refit: 1w -37, 2w -50, 4w -42.
Recency vs 100%-history twin (same N, refit, on/off): median change $/lot/wk, 50/50 -5, 100% trailing -4.
Best-of-rows penalty (108 versions, block bootstrap 2,000 draws, block 4 weeks, White reality check): vs zero best-by-mean row 19 $/lot/wk, luck haircut 74, after -55, RC p 0.95, versions positive 2 of 108; vs equal-weight best row 106, haircut 73, after 33, RC p 0.27.
Eligible families per date (cells in brackets): 2023-10-01 10825 (3,833,980), 2023-12-31 11119 (2,400,259), 2024-06-30 14873 (1,874,930), 2024-12-29 9847 (531,890), 2025-06-29 7035 (224,320), 2025-12-28 6885 (215,002), 2026-06-28 4550 (49,542), 2026-10-18 4126 (46,258); min 4126, median 8722, max 15175.
Different books the last 6 months needed (best version): 11; median over 108 versions 42; fewest 11, most 101.

## Four sessions summed (QUICK SCREEN)

| version | L3M $/lot/wk | L6M $/lot/wk | $/lot/wk | max DD $/lot | worst wk $/lot | 2023(Q4) | 2024 | 2025 | 2026 | beat EW | turnover | books L6M | L6M DD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BEST1: 50/50 w4M N8 r1w always | 70 | 46 | 21 | 1,904 | -901 | -39 | 24 | 12 | 46 | 50% | 0.41 | 253 | 636 |
| BEST2: 50/50 w4M N5 r1w always | 114 | 52 | 20 | 1,955 | -726 | 24 | 15 | 10 | 38 | 54% | 0.43 | 170 | 1,020 |
| BEST3: 50/50 w4M N5 r1w gate | 114 | 52 | 20 | 1,955 | -726 | 24 | 15 | 10 | 38 | 54% | 0.43 | 170 | 1,020 |
| BEST4: 50/50 w4M N8 r1w gate | 70 | 46 | 19 | 2,060 | -901 | -39 | 23 | 9 | 46 | 49% | 0.41 | 253 | 636 |
| BEST5: 100% trail w4M N5 r1w gate | 105 | 42 | 17 | 1,867 | -732 | -27 | 16 | 14 | 35 | 53% | 0.43 | 170 | 1,102 |
| 100%-HISTORY best: 100% hist w3M N5 r2w always | -89 | -149 | -6 | 8,508 | -1,923 | 32 | 104 | -52 | -95 | 51% | 0.38 | 75 | 4,864 |
| EQUAL-WEIGHT family medians, refit 1w | -34 | -55 | 1 | 3,757 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 2w | -33 | -61 | -2 | 3,720 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT family medians, refit 4w | -30 | -59 | -4 | 4,062 | - | - | - | - | - | - | - | - | - |
| EQUAL-WEIGHT all eligible cells, refit 1w | - | - | 22 | - | - | - | - | - | - | - | - | - | - |
| ZERO | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | - | - | - | 0 |

Per-version summary over all 108: positive $/lot/wk 23 of 108; median -12; best 21; worst -62. Versions beating zero in both L6M and L3M: 46. Versions with $/lot/wk above equal-weight: 28.
Median $/lot/wk by blend (does recency add): 100% history -19, 50/50 -6, 100% trailing -8. By on/off: always -12, gate -13. By basket size: 5 -> -11, 8 -> -22, 12 -> -9. By refit: 1w -18, 2w -14, 4w -11.
Recency vs 100%-history twin (same N, refit, on/off): median change $/lot/wk, 50/50 11, 100% trailing 6.
Best-of-rows penalty (108 versions, block bootstrap 2,000 draws, block 4 weeks, White reality check): vs zero best-by-mean row 21 $/lot/wk, luck haircut 38, after -17, RC p 0.81, versions positive 23 of 108; vs equal-weight best row 20, haircut 38, after -18, RC p 0.72.
Different books the last 6 months needed (best version): 253; median over 108 versions 170; fewest 71, most 439.

## EXACT re-score of the picked books (best version per session + equal-weight sample)

PENDING. Sets TL3_ALN_<S>_W<hash>_R0RT (truly bare R0, 1 lot, own bracket, fees in), months held only, queued behind W-ROTA's stage B rows. Status in MORNING.md LEAD NOTEs.

Code: code/th_rot2/{walk,chain,metrics,resolve,build2}.py; data on server C /mnt/l2/l2vast/_rot2/{out2,stageb_picks.json}; build files /mnt/l2/l2vast/_rot2/ on box1 (small).
