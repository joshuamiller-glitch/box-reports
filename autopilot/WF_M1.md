# WF_M1: M1 BOOK SWITCH ON ITS OWN CURVE (W-WF12, 2026-11-27)

## ANSWER FIRST

**2 of 32 primary cells (4 sessions x 2 subjects x 4 steps) PASS: NY AM S1 step 4, NY AM S2 step 4.** Chained out-of-sample max DD is shallower than untouched in 28 of 32 cells but income falls by more than 10% in 13 of 32; the permutation null (same number of half-size blocks, shuffled) shows the timing carries no information in nearly every cell (plain p in tables). Nothing is called works. Which step is best: see per-method note at the end. The 2-week step (Josh refit rhythm) is shown first.

## Method

Each book full size while its own trailing 13-week P&L (untreated, valid weeks before the decision) is above zero, else half size. Decision step 2 / 4 / 13 weeks (scale frozen over the step, set from data before the step) and weekly (state rule). Books with fewer than 13 prior valid weeks: full size.

Subjects. S1 = four live session mixes with live layers, per-trade exact engine P&L (book column) of sets TL3_SR_*; halving is applied to each trade P&L post-hoc: **post-hoc approx** (stack caps, daily-loss halts, 3-lot books -> 1.5 not modelled). 0 engine rows needed. S2 = equal-weight basket (per lot, $20/pt grid) of Test 5 primary held cells (walk5 pkl), quick screen only: exact S2 impossible for M1 because cell history before the hold is not in engine sets. Forward span weeks 26-181 (2023-10-02 to 2026-09-27) minus the four Nov-2025 weeks; periods = decision blocks (step 2: 77 periods, 4: 39, 13: 12, weekly: 152). Max DD per period on daily P&L (S1) or weekly points (S2) starting at zero each period; the chained curve joins all forward weeks into one curve. PASS at step 13: shallower DD in >= 8/12 and income not lower by > 10%, or income higher in >= 8/12 with DD not deeper. PASS at step 1/2/4: better (shallower DD, or higher income with no deeper DD) in >= 2/3 of periods and income not lower by > 10% (or the income-higher branch). Periods where the rule leaves full size are ties and count as not better. Plain p = permutation null (200 draws shuffling the decision-block scales across blocks), share of draws with at least as many better periods.

## S1 live mixes (exact per-trade, post-hoc size): primary, steps side by side (drawdown first)

#### Asia, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -67,941 -> -74,831 | -15,764 -> -14,844 | -4,735 -> -4,812 | 5,537 -> 4,549 (-17.8%) | 43 / 46 / 23 | **FAIL** | 0.83 |
| 4 | 39 | -67,941 -> -68,950 | -23,319 -> -21,957 | -11,711 -> -10,876 | 5,388 -> 4,690 (-13.0%) | 20 / 21 / 9 | **FAIL** | 0.99 |
| 13 | 12 | -67,941 -> -63,577 | -38,271 -> -36,138 | -21,617 -> -18,317 | 5,513 -> 4,940 (-10.4%) | 7 / 7 / 2 | **FAIL** | 0.80 |
| weekly | 152 | -67,941 -> -71,713 | -9,924 -> -9,156 | 5,593 -> 4,813 | 5,593 -> 4,813 (-14.0%) | 76 / 83 / 54 | **FAIL** | 0.56 |

#### NY AM, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -200,647 -> -157,041 | -43,982 -> -38,552 | -9,582 -> -8,280 | 19,825 -> 18,596 (-6.2%) | 44 / 44 / 25 | **FAIL** | 1.00 |
| 4 | 39 | -200,647 -> -175,216 | -62,580 -> -54,739 | -30,566 -> -26,273 | 19,562 -> 17,902 (-8.5%) | 26 / 26 / 13 | **PASS** | 0.67 |
| 13 | 12 | -200,647 -> -162,225 | -101,653 -> -88,330 | -58,514 -> -50,953 | 20,215 -> 16,761 (-17.1%) | 11 / 11 / 3 | **FAIL** | 0.35 |
| weekly | 152 | -200,647 -> -157,041 | -28,369 -> -25,164 | 20,408 -> 18,411 | 20,408 -> 18,411 (-9.8%) | 83 / 84 / 56 | **FAIL** | 0.97 |

#### NY PM, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -134,363 -> -119,239 | -20,215 -> -17,778 | -4,074 -> -3,278 | 5,954 -> 5,346 (-10.2%) | 41 / 41 / 22 | **FAIL** | 0.90 |
| 4 | 39 | -134,363 -> -128,411 | -29,172 -> -26,384 | -12,522 -> -10,719 | 5,181 -> 4,725 (-8.8%) | 21 / 21 / 11 | **FAIL** | 0.92 |
| 13 | 12 | -134,363 -> -130,279 | -49,090 -> -44,088 | -26,113 -> -21,703 | 5,843 -> 4,971 (-14.9%) | 8 / 8 / 1 | **FAIL** | 0.72 |
| weekly | 152 | -134,363 -> -119,084 | -12,797 -> -11,259 | 6,189 -> 5,443 | 6,189 -> 5,443 (-12.1%) | 75 / 75 / 45 | **FAIL** | 0.98 |

#### London, S1

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -224,333 -> -208,547 | -24,151 -> -21,280 | -5,234 -> -5,221 | 5,188 -> 3,863 (-25.5%) | 33 / 33 / 14 | **FAIL** | 0.78 |
| 4 | 39 | -224,333 -> -170,046 | -37,290 -> -31,568 | -17,080 -> -14,218 | 5,393 -> 4,576 (-15.1%) | 17 / 17 / 6 | **FAIL** | 0.84 |
| 13 | 12 | -224,333 -> -174,724 | -65,753 -> -54,861 | -35,181 -> -28,777 | 5,430 -> 4,533 (-16.5%) | 7 / 7 / 3 | **FAIL** | 0.88 |
| weekly | 152 | -224,333 -> -221,199 | -14,777 -> -12,965 | 5,164 -> 3,739 | 5,164 -> 3,739 (-27.6%) | 58 / 58 / 25 | **FAIL** | 0.94 |

### L3M and L6M (primary)

| session | step | L3M max DD U -> T | L3M worst wk | L3M $/wk | L6M max DD U -> T | L6M worst wk | L6M $/wk |
|---|---|---|---|---|---|---|---|
| Asia | 2 | -23,953 -> -22,498 | -8,395 -> -6,953 | 10,371 -> 9,699 | -37,750 -> -53,949 | -33,859 -> -31,840 | 15,460 -> 13,457 |
| Asia | 13 | -23,953 -> -22,498 | -8,395 -> -6,953 | 10,371 -> 9,366 | -37,750 -> -45,328 | -33,859 -> -31,840 | 15,460 -> 13,786 |
| NY AM | 2 | -69,974 -> -69,974 | -35,029 -> -35,029 | 60,454 -> 59,454 | -69,974 -> -69,974 | -59,414 -> -52,486 | 53,912 -> 51,144 |
| NY AM | 13 | -69,974 -> -68,232 | -35,029 -> -31,270 | 60,454 -> 59,528 | -69,974 -> -69,723 | -59,414 -> -52,486 | 53,912 -> 48,232 |
| NY PM | 2 | -26,269 -> -26,269 | -18,119 -> -18,119 | 12,337 -> 11,900 | -30,613 -> -28,796 | -23,047 -> -23,047 | 12,962 -> 12,042 |
| NY PM | 13 | -26,269 -> -26,269 | -18,119 -> -18,119 | 12,337 -> 12,337 | -30,613 -> -28,796 | -23,047 -> -18,119 | 12,962 -> 12,676 |
| London | 2 | -39,760 -> -39,760 | -20,172 -> -20,172 | 18,416 -> 17,809 | -39,760 -> -39,760 | -20,695 -> -20,695 | 17,963 -> 15,161 |
| London | 13 | -39,760 -> -36,518 | -20,172 -> -18,372 | 18,416 -> 17,192 | -39,760 -> -36,518 | -20,695 -> -18,372 | 17,963 -> 14,941 |

### Reference versions (not primaries)

| version (reference) | Asia: chain DD chg / income chg / verdict | NY AM: chain DD chg / income chg / verdict | NY PM: chain DD chg / income chg / verdict | London: chain DD chg / income chg / verdict |
|---|---|---|---|---|
| ref:n26, step 2 | -4,436 / -4% / FAIL | 14,088 / -13% / FAIL | 14,378 / -8% / FAIL | -5,178 / -19% / FAIL |
| ref:n26, step 13 | 3,749 / -7% / FAIL | 20,574 / -10% / FAIL | -0 / -12% / FAIL | 28,542 / -14% / FAIL |
| ref:n8, step 2 | -15,393 / -20% / FAIL | 42,322 / -13% / FAIL | 34,705 / -9% / FAIL | 20,022 / -23% / FAIL |
| ref:n8, step 13 | 6,447 / -24% / FAIL | 35,495 / -21% / FAIL | 4,084 / -21% / FAIL | 47,664 / -30% / FAIL |

## S2 Test 5 basket (quick): primary, steps side by side (drawdown first)

#### Asia, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -7,083 -> -6,820 | -717 -> -685 | -413 -> -391 | 199 -> 180 (-9.3%) | 28 / 32 / 27 | **FAIL** | 1.00 |
| 4 | 39 | -7,083 -> -6,801 | -1,332 -> -1,272 | -984 -> -933 | 216 -> 202 (-6.3%) | 20 / 20 / 12 | **FAIL** | 1.00 |
| 13 | 12 | -7,083 -> -6,959 | -2,934 -> -2,920 | -1,883 -> -1,870 | 206 -> 203 (-1.3%) | 4 / 4 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -7,083 -> -6,929 | -363 -> -344 | 201 -> 181 | 201 -> 181 (-10.0%) | 40 / 54 / 54 | **FAIL** | 0.99 |

#### NY AM, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -22,269 -> -19,349 | -1,069 -> -974 | -713 -> -646 | 135 -> 131 (-2.9%) | 39 / 42 / 30 | **FAIL** | 0.91 |
| 4 | 39 | -22,269 -> -19,996 | -1,970 -> -1,808 | -1,395 -> -1,273 | 134 -> 135 (+0.6%) | 27 / 28 / 15 | **PASS** | 0.51 |
| 13 | 12 | -22,269 -> -21,249 | -4,381 -> -4,261 | -2,487 -> -2,431 | 139 -> 137 (-1.2%) | 6 / 6 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -22,269 -> -19,116 | -542 -> -488 | 134 -> 131 | 134 -> 131 (-1.6%) | 53 / 64 / 64 | **FAIL** | 0.90 |

#### NY PM, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -23,091 -> -16,814 | -1,218 -> -1,073 | -756 -> -644 | 127 -> 132 (+3.2%) | 32 / 35 / 29 | **FAIL** | 0.70 |
| 4 | 39 | -23,091 -> -17,148 | -2,275 -> -2,028 | -1,581 -> -1,387 | 140 -> 143 (+2.7%) | 22 / 23 / 16 | **FAIL** | 0.56 |
| 13 | 12 | -23,091 -> -20,676 | -5,448 -> -5,208 | -2,791 -> -2,687 | 135 -> 109 (-19.3%) | 4 / 4 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -23,091 -> -16,888 | -617 -> -544 | 133 -> 138 | 133 -> 138 (+3.7%) | 41 / 58 / 58 | **FAIL** | 0.34 |

#### London, S2

| step (wk) | periods | chain max DD U -> T | mean per-period max DD U -> T | mean worst wk U -> T | $/wk U -> T (chg) | shallower / better / income-higher | verdict | plain p (perm.) |
|---|---|---|---|---|---|---|---|---|
| 2 | 77 | -13,451 -> -12,922 | -807 -> -730 | -567 -> -521 | -64 -> -64 (+0.6%) | 28 / 30 / 25 | **FAIL** | 0.81 |
| 4 | 39 | -13,451 -> -13,535 | -1,496 -> -1,386 | -1,135 -> -1,053 | -67 -> -67 (-1.1%) | 18 / 18 / 14 | **FAIL** | 0.74 |
| 13 | 12 | -13,451 -> -12,302 | -3,813 -> -3,676 | -2,251 -> -2,219 | -60 -> -49 (+17.8%) | 2 / 2 / 2 | **FAIL** | 1.00 |
| weekly | 152 | -13,451 -> -11,894 | -409 -> -360 | -56 -> -53 | -56 -> -53 (+5.1%) | 38 / 51 / 51 | **FAIL** | 0.45 |

### L3M and L6M (primary)

| session | step | L3M max DD U -> T | L3M worst wk | L3M $/wk | L6M max DD U -> T | L6M worst wk | L6M $/wk |
|---|---|---|---|---|---|---|---|
| Asia | 2 | -3,189 -> -3,201 | -1,920 -> -1,913 | 167 -> 131 | -3,999 -> -3,929 | -2,455 -> -2,427 | 618 -> 564 |
| Asia | 13 | -3,189 -> -3,201 | -1,920 -> -1,913 | 167 -> 164 | -3,999 -> -3,974 | -2,455 -> -2,443 | 618 -> 613 |
| NY AM | 2 | -4,696 -> -4,315 | -2,501 -> -2,252 | 235 -> 153 | -10,511 -> -9,321 | -3,134 -> -2,951 | -126 -> -133 |
| NY AM | 13 | -4,696 -> -4,412 | -2,501 -> -2,341 | 235 -> 228 | -10,511 -> -9,904 | -3,134 -> -2,968 | -126 -> -126 |
| NY PM | 2 | -5,097 -> -5,321 | -2,559 -> -2,518 | 271 -> 243 | -13,868 -> -9,717 | -4,339 -> -4,273 | 125 -> 133 |
| NY PM | 13 | -5,097 -> -5,062 | -2,559 -> -2,458 | 271 -> 258 | -13,868 -> -11,703 | -4,339 -> -3,824 | 125 -> 10 |
| London | 2 | -5,858 -> -5,711 | -3,458 -> -3,300 | 187 -> 179 | -5,858 -> -5,711 | -3,458 -> -3,300 | 126 -> 89 |
| London | 13 | -5,858 -> -5,858 | -3,458 -> -3,458 | 187 -> 187 | -5,858 -> -5,858 | -3,458 -> -3,458 | 126 -> 126 |

### Reference versions (not primaries)

| version (reference) | Asia: chain DD chg / income chg / verdict | NY AM: chain DD chg / income chg / verdict | NY PM: chain DD chg / income chg / verdict | London: chain DD chg / income chg / verdict |
|---|---|---|---|---|
| ref:n26, step 2 | 186 / -1% / FAIL | 1,185 / +2% / FAIL | 757 / -34% / FAIL | -444 / +0% / FAIL |
| ref:n26, step 13 | 0 / +0% / FAIL | 132 / +0% / FAIL | 1,215 / -19% / FAIL | 0 / +0% / FAIL |
| ref:n8, step 2 | 758 / -13% / FAIL | 3,754 / -7% / FAIL | 5,649 / -24% / FAIL | 2,188 / +12% / FAIL |
| ref:n8, step 13 | 11 / -4% / FAIL | 1,371 / -5% / PASS | 2,442 / -11% / FAIL | 1,050 / +16% / FAIL |

## Caveats

- Live books were chosen on the same weeks (hindsight flatters the untreated subject); S2 qualifiers are in-sample at qualify date. Decisions use data before each step only; no parameter was tuned on forward weeks (one primary, <= 5 references).
- Halving always cuts income roughly in proportion to the half-size share (frac of time half: see scoreboard); a rule that only shrinks size at random does as well on drawdown per dollar, which is what the permutation p tests.
- Pessimistic-fill re-score (fee $4.84/lot, stop slippage): not run for the PASS cells above because their permutation p is not small; the post-hoc halving scales fees and slippage alike so it would not change the verdict.
- Scoreboard lines (step_weeks 1/2/4/13, all versions) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl. Code: outputs/code/wf_m1m10/ (wf12.py, run12b.py, pages.py); results pickle /mnt/l2/l2vast/_wf/m1m10/results_steps.pkl.


## Which step is best (added)

- step 2: chain DD shallower in 7/8, income within -10% in 5/8, both 5/8, PASS 0/8, permutation p<=0.05 in 0/8.
- step 4: chain DD shallower in 6/8, income within -10% in 6/8, both 5/8, PASS 2/8, permutation p<=0.05 in 0/8.
- step 13: chain DD shallower in 8/8, income within -10% in 3/8, both 3/8, PASS 0/8, permutation p<=0.05 in 0/8.
- step weekly: chain DD shallower in 7/8, income within -10% in 5/8, both 5/8, PASS 0/8, permutation p<=0.05 in 0/8.

Reading: faster steps do not help in a way the null cannot reproduce; the shallower chained drawdowns are mostly the arithmetic of running smaller size part of the time.
