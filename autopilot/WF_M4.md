# WF M4: volatility regime size filter (W-WF49, 2026-11-27)

## ANSWER FIRST
**FAIL for all four sessions, both subjects, all three steps (2, 4, 13 weeks). No primary passes.** The drawdown falls (Asia and London S1 chained max DD roughly halves) but only because the filter sits at half size almost all the time: forward income falls by about the same fraction (Asia S1 $5,537 -> $2,876 per week at the 2-week step), so the income rule fails and income per unit of chained drawdown is unchanged (Asia S1 12.5 -> 13.0, London 3.5 -> 2.9). That is a uniform half-size, not a regime signal. Reason: NQ's trailing 20-day median range kept rising (about 195-240 points at the early dates, 300-650 in 2026), so the past-data tercile the rule picks (mostly the LOW tercile) is rarely met in the forward period; full size applied on only 5-7% of Asia/London trades at 13 weeks. NY AM is the only session where the rule is not a plain halving (it picks the high band): NY AM S1 chained DD -200.6k -> -163.6k, income 19.8k -> 15.7k per week at 2 weeks, income per DD 15.5 -> 15.0, FAIL.
Reference rows (marked reference, 6 variants including a price-normalised range band 'pct_range') produced only 5 reference passes, all S2 and mostly London S2 where the untouched basket itself has negative income; they are not credited. Nothing goes to the forward register.
Faster steps: no help. 2-week and 4-week rows look the same as 13-week; the band choice is stable, so refitting faster changes nothing.

## Method (post-hoc, exact trades where S1)
- Band signal: median of NQ's daily range (all sessions, stored 15-s time bars, 934 trading days) over the 20 trading days strictly before the trade date. Past data only: at each decision date, tercile edges and the band with the best income per max drawdown are computed from past days (masked daily P&L, other days zero). Forward trades inside the chosen band keep size 1, outside 0.5. 'Unknown history' = full size.
- S1 = the four live set P&L per trade (exact engine, TRADES), trade P&L rescaled post-hoc by x1 / x0.5: **post-hoc approx** (stack caps and daily-loss halts not re-run; with halved lots the engine's integer lots and layers could differ). Decision steps 2, 4, 13 weeks over weeks 26..182 (77 / 39 / 12 forward periods; one all-Nov-2025 period dropped at step 2; Nov 2025 weeks excluded).
- S2 = equal-weight (per-lot) basket of the Test 5 primary qualifiers held at the latest 13-week re-qualify date (list does not refresh faster than 13 weeks; only the M4 band refreshes), weekly resolution, quick screen (grid points x $20, no account layers).
- PASS rule: step 13 as the common doc; steps 2/4: shallower DD, or higher income with no deeper DD, in >= 2/3 of the periods AND income not lower by more than 10%. Plain p = one-sided sign test on the period count. 168 scoreboard lines appended (7 versions x 4 sessions x 2 subjects x 3 steps).
- Caveats: live books chosen on the same weeks; S2 qualifiers in-sample; the 36 primary cells tried here add to the luck count.

## Tables (primary; drawdown first). good/n at step 13 = shallower-DD periods

**Step 2 wk, S1 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -67,941 | -33,971 | -14,759 | -7,531 | 5,537 | 2,876 | 12.51 | 13.00 | 75/77 | 0.000 | FAIL |
| NY AM | -200,647 | -163,622 | -40,083 | -31,852 | 19,825 | 15,685 | 15.46 | 14.99 | 37/77 | 0.676 | FAIL |
| NY PM | -134,363 | -77,909 | -19,166 | -12,685 | 5,954 | 3,726 | 7.00 | 7.67 | 58/77 | 0.000 | FAIL |
| London | -224,333 | -118,415 | -22,728 | -12,638 | 5,188 | 2,300 | 3.50 | 2.93 | 67/77 | 0.000 | FAIL |

**Step 2 wk, S2 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -7,630 | -7,619 | -347 | -262 | 189 | 98 | 3.79 | 1.96 | 26/77 | 0.999 | FAIL |
| NY AM | -20,874 | -12,250 | -584 | -357 | 140 | 94 | 1.01 | 1.14 | 33/77 | 0.914 | FAIL |
| NY PM | -22,899 | -14,473 | -621 | -336 | 131 | 64 | 0.91 | 0.70 | 40/77 | 0.410 | FAIL |
| London | -12,211 | -11,104 | -287 | -246 | -59 | -58 | -0.63 | -0.68 | 27/77 | 0.997 | FAIL |

**Step 4 wk, S1 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -67,941 | -33,971 | -22,942 | -11,793 | 5,388 | 2,762 | 12.51 | 12.83 | 39/39 | 0.000 | FAIL |
| NY AM | -200,647 | -163,622 | -59,991 | -47,403 | 19,562 | 15,215 | 15.46 | 14.90 | 21/39 | 0.375 | FAIL |
| NY PM | -134,363 | -67,181 | -28,820 | -19,725 | 5,181 | 3,213 | 7.00 | 9.43 | 29/39 | 0.002 | FAIL |
| London | -224,333 | -118,415 | -35,024 | -19,894 | 5,393 | 2,842 | 3.50 | 3.51 | 34/39 | 0.000 | FAIL |

**Step 4 wk, S2 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -7,083 | -6,560 | -968 | -716 | 223 | 145 | 4.48 | 2.98 | 19/39 | 0.625 | FAIL |
| NY AM | -21,801 | -12,714 | -1,644 | -956 | 131 | 92 | 0.91 | 1.08 | 26/39 | 0.027 | FAIL |
| NY PM | -22,405 | -14,226 | -1,800 | -1,049 | 94 | 32 | 0.58 | 0.30 | 29/39 | 0.002 | FAIL |
| London | -17,452 | -13,194 | -1,133 | -806 | -101 | -68 | -0.79 | -0.66 | 17/39 | 0.832 | FAIL |

**Step 13 wk, S1 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -67,941 | -35,511 | -38,040 | -20,425 | 5,513 | 2,787 | 12.51 | 12.10 | 11/12 | 0.003 | FAIL |
| NY AM | -200,647 | -163,622 | -100,401 | -81,359 | 20,215 | 18,142 | 15.46 | 17.07 | 6/12 | 0.613 | FAIL |
| NY PM | -134,363 | -78,363 | -48,887 | -32,560 | 5,843 | 3,189 | 7.00 | 6.63 | 9/12 | 0.073 | FAIL |
| London | -224,333 | -118,415 | -65,161 | -33,211 | 5,430 | 2,840 | 3.50 | 3.48 | 12/12 | 0.000 | FAIL |

**Step 13 wk, S2 (primary).** Chained OOS max DD U -> M4; mean per-period max DD U -> M4; $/wk U -> M4; chained income/|DD| U -> M4; periods good (shallower DD, or higher income w/o deeper DD; step 13: shallower only) / n; sign p; verdict

| session | chain DD U | chain DD M4 | mean period DD U | M4 | $/wk U | M4 | inc/DD U | M4 | good/n | p | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | -7,083 | -7,083 | -2,726 | -2,250 | 206 | 171 | 4.31 | 3.61 | 6/12 | 0.613 | FAIL |
| NY AM | -22,269 | -18,063 | -4,381 | -3,000 | 139 | 88 | 0.91 | 0.70 | 8/12 | 0.194 | FAIL |
| NY PM | -23,091 | -15,965 | -5,265 | -3,212 | 135 | 60 | 0.88 | 0.57 | 10/12 | 0.019 | FAIL |
| London | -11,940 | -12,209 | -3,517 | -3,115 | -60 | -50 | -0.71 | -0.56 | 6/12 | 0.613 | FAIL |
