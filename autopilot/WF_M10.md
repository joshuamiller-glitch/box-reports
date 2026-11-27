# WF_M10: M10 LOSS-STREAK GOVERNOR (W-WF12, 2026-11-27)

## ANSWER FIRST

**0 of 32 primary cells (4 sessions x 2 subjects x 4 steps) PASS.** Chained out-of-sample max DD is shallower than untouched in 24 of 32 cells but income falls by more than 10% in 21 of 32; the permutation null (same number of half-size blocks, shuffled) shows the timing carries no information in nearly every cell (plain p in tables). Nothing is called works. Which step is best: see per-method note at the end. The 2-week step (Josh refit rhythm) is shown first.

## Method

Trailing 4-week P&L of the untreated session mix below X = min(20th percentile of all past rolling 4-week results, 0) (needs 8 past results) turns half size on; it stays on until the untreated equity closes the last week above the highest of the four week-ends before it (new 4-week high). Step 2 / 4 / 13 weeks (state frozen over the step) and weekly.

Subjects. S1 = four live session mixes with live layers, per-trade exact engine P&L (book column) of sets TL3_SR_*; halving is applied to each trade P&L post-hoc: **post-hoc approx** (stack caps, daily-loss halts, 3-lot books -> 1.5 not modelled). 0 engine rows needed. S2 = equal-weight basket (per lot, $20/pt grid) of Test 5 primary held cells (walk5 pkl), quick screen only: exact S2 impossible for M1 because cell history before the hold is not in engine sets. Forward span weeks 26-181 (2023-10-02 to 2026-09-27) minus the four Nov-2025 weeks; periods = decision blocks (step 2: 77 periods, 4: 39, 13: 12, weekly: 152). Max DD per period on daily P&L (S1) or weekly points (S2) starting at zero each period; the chained curve joins all forward weeks into one curve. PASS at step 13: shallower DD in >= 8/12 and income not lower by > 10%, or income higher in >= 8/12 with DD not deeper. PASS at step 1/2/4: better (shallower DD, or higher income with no deeper DD) in >= 2/3 of periods and income not lower by > 10% (or the income-higher branch). Periods where the rule leaves full size are ties and count as not better. Plain p = permutation null (200 draws shuffling the decision-block scales across blocks), share of draws with at least as many better periods.

## S1 live mixes (exact per-trade, post-hoc size): primary, steps side by side (drawdown first)

#### Asia, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -67,941 -> -71,631 | -15,764 -> -13,254 | -4,735 -> -3,871 | 5,537 -> 5,044 (-8.9%) | 21 / 21 / 9 | **FAIL** | 1.00 |
| 4 | 39 | -67,941 -> -70,713 | -23,319 -> -20,189 | -11,711 -> -9,817 | 5,388 -> 4,849 (-10.0%) | 10 / 10 / 2 | **FAIL** | 1.00 |
| 13 | 12 | -67,941 -> -64,207 | -38,271 -> -35,440 | -21,617 -> -20,089 | 5,513 -> 5,180 (-6.0%) | 1 / 1 / 0 | **FAIL** | 1.00 |
| weekly | 152 | -67,941 -> -75,362 | -9,924 -> -8,536 | 5,593 -> 4,508 | 5,593 -> 4,508 (-19.4%) | 41 / 41 / 15 | **FAIL** | 0.87 |

#### NY AM, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -200,647 -> -174,622 | -43,982 -> -39,982 | -9,582 -> -9,374 | 19,825 -> 17,442 (-12.0%) | 18 / 18 / 6 | **FAIL** | 1.00 |
| 4 | 39 | -200,647 -> -173,715 | -62,580 -> -56,993 | -30,566 -> -28,188 | 19,562 -> 16,793 (-14.2%) | 9 / 9 / 3 | **FAIL** | 1.00 |
| 13 | 12 | -200,647 -> -184,763 | -101,653 -> -95,460 | -58,514 -> -53,890 | 20,215 -> 18,040 (-10.8%) | 2 / 2 / 0 | **FAIL** | 1.00 |
| weekly | 152 | -200,647 -> -174,622 | -28,369 -> -25,752 | 20,408 -> 18,028 | 20,408 -> 18,028 (-11.7%) | 32 / 32 / 10 | **FAIL** | 0.55 |

#### NY PM, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -134,363 -> -97,424 | -20,215 -> -17,635 | -4,074 -> -3,073 | 5,954 -> 5,639 (-5.3%) | 20 / 20 / 7 | **FAIL** | 0.72 |
| 4 | 39 | -134,363 -> -112,825 | -29,172 -> -25,806 | -12,522 -> -10,712 | 5,181 -> 5,050 (-2.5%) | 10 / 10 / 3 | **FAIL** | 1.00 |
| 13 | 12 | -134,363 -> -134,363 | -49,090 -> -43,980 | -26,113 -> -22,937 | 5,843 -> 4,455 (-23.8%) | 3 / 3 / 0 | **FAIL** | 1.00 |
| weekly | 152 | -134,363 -> -75,564 | -12,797 -> -10,967 | 6,189 -> 5,854 | 6,189 -> 5,854 (-5.4%) | 40 / 40 / 18 | **FAIL** | 0.52 |

#### London, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -224,333 -> -232,222 | -24,151 -> -20,607 | -5,234 -> -4,744 | 5,188 -> 4,130 (-20.4%) | 21 / 21 / 6 | **FAIL** | 1.00 |
| 4 | 39 | -224,333 -> -150,993 | -37,290 -> -31,367 | -17,080 -> -13,947 | 5,393 -> 4,812 (-10.8%) | 10 / 10 / 3 | **FAIL** | 1.00 |
| 13 | 12 | -224,333 -> -156,282 | -65,753 -> -55,112 | -35,181 -> -28,010 | 5,430 -> 5,734 (+5.6%) | 2 / 2 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -224,333 -> -213,492 | -14,777 -> -12,565 | 5,164 -> 4,286 | 5,164 -> 4,286 (-17.0%) | 41 / 41 / 15 | **FAIL** | 0.24 |

### L3M and L6M (primary)

| session | step | L3M max DD U -> T | L3M worst wk | L3M $/wk | L6M max DD U -> T | L6M worst wk | L6M $/wk |
|---|---|---|---|---|---|---|---|
| Asia | 2 | -23,953 -> -23,953 | -8,395 -> -8,395 | 10,371 -> 10,371 | -37,750 -> -34,639 | -33,859 -> -33,859 | 15,460 -> 14,908 |
| Asia | 13 | -23,953 -> -23,953 | -8,395 -> -8,395 | 10,371 -> 10,371 | -37,750 -> -37,750 | -33,859 -> -33,859 | 15,460 -> 15,460 |
| NY AM | 2 | -69,974 -> -69,974 | -35,029 -> -35,029 | 60,454 -> 60,454 | -69,974 -> -69,974 | -59,414 -> -37,621 | 53,912 -> 51,914 |
| NY AM | 13 | -69,974 -> -69,974 | -35,029 -> -35,029 | 60,454 -> 60,454 | -69,974 -> -69,974 | -59,414 -> -35,029 | 53,912 -> 42,070 |
| NY PM | 2 | -26,269 -> -26,269 | -18,119 -> -18,119 | 12,337 -> 12,337 | -30,613 -> -30,613 | -23,047 -> -23,047 | 12,962 -> 12,247 |
| NY PM | 13 | -26,269 -> -26,269 | -18,119 -> -18,119 | 12,337 -> 12,337 | -30,613 -> -26,269 | -23,047 -> -18,119 | 12,962 -> 9,565 |
| London | 2 | -39,760 -> -39,760 | -20,172 -> -20,172 | 18,416 -> 18,416 | -39,760 -> -39,760 | -20,695 -> -20,695 | 17,963 -> 17,107 |
| London | 13 | -39,760 -> -39,760 | -20,172 -> -20,172 | 18,416 -> 18,416 | -39,760 -> -39,760 | -20,695 -> -20,695 | 17,963 -> 17,963 |

### Reference versions (not primaries)

| version (reference) | Asia: chain DD chg / income chg / verdict | NY AM: chain DD chg / income chg / verdict | NY PM: chain DD chg / income chg / verdict | London: chain DD chg / income chg / verdict |
|---|---|---|---|---|
| ref:p10, step 2 | -3,689 / -8% / FAIL | 26,025 / -10% / FAIL | 36,939 / -1% / FAIL | 4,239 / -12% / FAIL |
| ref:p10, step 13 | 0 / +0% / FAIL | 15,884 / -1% / FAIL | 0 / -14% / FAIL | 31,009 / +4% / FAIL |
| ref:p30, step 2 | -3,689 / -10% / FAIL | 49,658 / -12% / FAIL | 36,939 / -5% / FAIL | -12,884 / -21% / FAIL |
| ref:p30, step 13 | 3,734 / -6% / FAIL | 15,884 / -12% / FAIL | 0 / -24% / FAIL | 68,051 / +6% / FAIL |
| ref:release_r4pos, step 2 | 3,908 / -6% / FAIL | 423 / -8% / FAIL | 36,939 / -3% / FAIL | -11,187 / -19% / FAIL |
| ref:release_r4pos, step 13 | 3,734 / -6% / FAIL | 15,884 / -11% / FAIL | 0 / -24% / FAIL | 68,051 / +6% / FAIL |
| ref:unclipped, step 2 | -3,689 / -9% / FAIL | 26,025 / -12% / FAIL | 36,939 / -5% / FAIL | -7,890 / -20% / FAIL |
| ref:unclipped, step 13 | 3,734 / -6% / FAIL | 15,884 / -11% / FAIL | 0 / -24% / FAIL | 68,051 / +6% / FAIL |

## S2 Test 5 basket (quick): primary, steps side by side (drawdown first)

#### Asia, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -7,083 -> -5,934 | -717 -> -572 | -413 -> -317 | 199 -> 181 (-9.0%) | 21 / 21 / 13 | **FAIL** | 0.44 |
| 4 | 39 | -7,083 -> -6,662 | -1,332 -> -1,109 | -984 -> -824 | 216 -> 170 (-21.0%) | 14 / 14 / 4 | **FAIL** | 0.81 |
| 13 | 12 | -7,083 -> -7,083 | -2,934 -> -2,426 | -1,883 -> -1,536 | 206 -> 95 (-53.7%) | 5 / 5 / 0 | **FAIL** | 1.00 |
| weekly | 152 | -7,083 -> -6,487 | -363 -> -293 | 201 -> 161 | 201 -> 161 (-19.8%) | 25 / 25 / 25 | **FAIL** | 0.81 |

#### NY AM, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -22,269 -> -15,132 | -1,069 -> -834 | -713 -> -562 | 135 -> 84 (-37.5%) | 21 / 21 / 13 | **FAIL** | 0.73 |
| 4 | 39 | -22,269 -> -15,099 | -1,970 -> -1,496 | -1,395 -> -1,070 | 134 -> 132 (-1.2%) | 13 / 13 / 5 | **FAIL** | 0.40 |
| 13 | 12 | -22,269 -> -18,063 | -4,381 -> -3,361 | -2,487 -> -1,942 | 139 -> 70 (-49.7%) | 7 / 7 / 1 | **FAIL** | 1.00 |
| weekly | 152 | -22,269 -> -14,146 | -542 -> -416 | 134 -> 78 | 134 -> 78 (-41.3%) | 27 / 27 / 27 | **FAIL** | 0.81 |

#### NY PM, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -23,091 -> -14,751 | -1,218 -> -968 | -756 -> -582 | 127 -> 109 (-14.7%) | 23 / 23 / 14 | **FAIL** | 0.83 |
| 4 | 39 | -23,091 -> -15,978 | -2,275 -> -1,866 | -1,581 -> -1,291 | 140 -> 106 (-23.8%) | 13 / 13 / 5 | **FAIL** | 0.98 |
| 13 | 12 | -23,091 -> -12,942 | -5,448 -> -4,300 | -2,791 -> -2,374 | 135 -> 150 (+11.1%) | 3 / 3 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -23,091 -> -14,023 | -617 -> -494 | 133 -> 101 | 133 -> 101 (-24.3%) | 29 / 29 / 29 | **FAIL** | 0.93 |

#### London, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -13,451 -> -14,315 | -807 -> -678 | -567 -> -492 | -64 -> -81 (-26.3%) | 28 / 28 / 21 | **FAIL** | 0.69 |
| 4 | 39 | -13,451 -> -11,866 | -1,496 -> -1,211 | -1,135 -> -916 | -67 -> -70 (-4.6%) | 15 / 15 / 7 | **FAIL** | 0.97 |
| 13 | 12 | -13,451 -> -9,906 | -3,813 -> -3,032 | -2,251 -> -1,800 | -60 -> -42 (+29.1%) | 5 / 5 / 3 | **FAIL** | 1.00 |
| weekly | 152 | -13,451 -> -13,765 | -409 -> -346 | -56 -> -69 | -56 -> -69 (-23.7%) | 36 / 36 / 36 | **FAIL** | 0.59 |

### L3M and L6M (primary)

| session | step | L3M max DD U -> T | L3M worst wk | L3M $/wk | L6M max DD U -> T | L6M worst wk | L6M $/wk |
|---|---|---|---|---|---|---|---|
| Asia | 2 | -3,189 -> -2,796 | -1,920 -> -1,920 | 167 -> 126 | -3,999 -> -3,999 | -2,455 -> -2,455 | 618 -> 518 |
| Asia | 13 | -3,189 -> -3,189 | -1,920 -> -1,920 | 167 -> 167 | -3,999 -> -3,189 | -2,455 -> -1,920 | 618 -> 351 |
| NY AM | 2 | -4,696 -> -4,696 | -2,501 -> -2,501 | 235 -> -155 | -10,511 -> -7,440 | -3,134 -> -2,501 | -126 -> -200 |
| NY AM | 13 | -4,696 -> -2,348 | -2,501 -> -1,250 | 235 -> 118 | -10,511 -> -5,255 | -3,134 -> -1,567 | -126 -> -63 |
| NY PM | 2 | -5,097 -> -4,220 | -2,559 -> -1,996 | 271 -> 249 | -13,868 -> -6,934 | -4,339 -> -4,339 | 125 -> 271 |
| NY PM | 13 | -5,097 -> -5,097 | -2,559 -> -2,559 | 271 -> 271 | -13,868 -> -6,934 | -4,339 -> -2,559 | 125 -> 130 |
| London | 2 | -5,858 -> -5,858 | -3,458 -> -3,458 | 187 -> 129 | -5,858 -> -5,858 | -3,458 -> -3,458 | 126 -> 33 |
| London | 13 | -5,858 -> -5,858 | -3,458 -> -3,458 | 187 -> 187 | -5,858 -> -5,858 | -3,458 -> -3,458 | 126 -> 110 |

### Reference versions (not primaries)

| version (reference) | Asia: chain DD chg / income chg / verdict | NY AM: chain DD chg / income chg / verdict | NY PM: chain DD chg / income chg / verdict | London: chain DD chg / income chg / verdict |
|---|---|---|---|---|
| ref:p10, step 2 | 1,052 / -10% / FAIL | 2,021 / -50% / FAIL | 8,340 / +7% / FAIL | -84 / -18% / FAIL |
| ref:p10, step 13 | -0 / -49% / FAIL | 4,206 / -32% / FAIL | 10,149 / +11% / FAIL | 3,545 / +29% / FAIL |
| ref:p30, step 2 | 1,149 / -27% / FAIL | 7,170 / -38% / FAIL | 8,340 / -16% / FAIL | -1,826 / -36% / FAIL |
| ref:p30, step 13 | -0 / -54% / FAIL | 4,206 / -50% / FAIL | 10,149 / +6% / FAIL | 5,128 / +47% / FAIL |
| ref:release_r4pos, step 2 | 1,149 / -4% / FAIL | 7,137 / -38% / FAIL | 8,340 / +1% / FAIL | -1,784 / -36% / FAIL |
| ref:release_r4pos, step 13 | -0 / -46% / FAIL | 4,206 / -50% / FAIL | 10,149 / +16% / FAIL | 3,545 / +29% / FAIL |
| ref:unclipped, step 2 | 1,149 / -9% / FAIL | 7,137 / -38% / FAIL | 8,340 / -15% / FAIL | -864 / -26% / FAIL |
| ref:unclipped, step 13 | -0 / -54% / FAIL | 4,206 / -50% / FAIL | 10,149 / +11% / FAIL | 3,545 / +29% / FAIL |

## Caveats

- Live books were chosen on the same weeks (hindsight flatters the untreated subject); S2 qualifiers are in-sample at qualify date. Decisions use data before each step only; no parameter was tuned on forward weeks (one primary, <= 5 references).
- Halving always cuts income roughly in proportion to the half-size share (frac of time half: see scoreboard); a rule that only shrinks size at random does as well on drawdown per dollar, which is what the permutation p tests.
- Pessimistic-fill re-score (fee $4.84/lot, stop slippage): not run for the PASS cells above because their permutation p is not small; the post-hoc halving scales fees and slippage alike so it would not change the verdict.
- Scoreboard lines (step_weeks 1/2/4/13, all versions) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl. Code: outputs/code/wf_m1m10/ (wf12.py, run12b.py, pages.py); results pickle /mnt/l2/l2vast/_wf/m1m10/results_steps.pkl.


## Which step is best (added)

- step 2: chain DD shallower in 5/8, income within -10% in 3/8, both 2/8, PASS 0/8, permutation p<=0.05 in 0/8.
- step 4: chain DD shallower in 7/8, income within -10% in 3/8, both 3/8, PASS 0/8, permutation p<=0.05 in 0/8.
- step 13: chain DD shallower in 6/8, income within -10% in 4/8, both 4/8, PASS 0/8, permutation p<=0.05 in 0/8.
- step weekly: chain DD shallower in 6/8, income within -10% in 1/8, both 1/8, PASS 0/8, permutation p<=0.05 in 0/8.

Reading: faster steps do not help in a way the null cannot reproduce; the shallower chained drawdowns are mostly the arithmetic of running smaller size part of the time.
