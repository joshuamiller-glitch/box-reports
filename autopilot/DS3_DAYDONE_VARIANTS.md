# DS3_DAYDONE_VARIANTS - DAY-DONE settings on the exact engine (W-DD, order 11-17 13:31Z)
VERDICT (data ends 2026-10-31; FIRST PASS 2026-11-24 21:14Z; OFF landed 43 of 43 months; ulcer index primary; tiers use the calibrated cut-offs): no variant has a scored tier yet (controls or windows missing = NOT FINISHED, never passing). No removal of the live rule is implied; this is a search for a better SETTING of the same layer.

> VALIDATION (desk standard, W-DD, FIRST PASS, 2026-11-24 21:14Z): trials counted = 37 settings on JL3 (7 named variants LATCH BE BT C D2 D4 F + 30 grid cells = closes {18,22,26,30} x live loss {3,000 4,200 6,000 8,000} for the eval form and for the session-boundary form, minus the two cells that equal REF and C), plus the references REF / OFF and JL2 OFF; controls = 6 families x 30 persistent random-day-halt draws (A day-reset, B open-P&L, C session, D2, D4, F per-book); correction = percentile among the controls of the matching family on the calibrated tiers, and over the 37 settings White RC / Hansen SPA / DSR / BH on weekly P&L deltas vs REF (mean) plus a block-bootstrap reality check on the ulcer statistic and PBO (CSCV, weekly P&L of the 37 + REF); in-sample on the 43 months (no fitted choice; recent windows L6M/L3M and older HOLD/GAP/PRE/X' are the walk-forward-style split); FIRST PASS, shown only for what landed.

## Status (what has landed)
- IDENTITY gate (inert / re-implemented cell = TL3_EV_JL3 trade for trade on 202610 and 202504): PASS
  - TL3_DD_JL3_ID 202504: 637 trades net 41239.76 vs reference 637 net 41239.76 -> IDENTICAL
  - TL3_DD_JL3_ID 202610: 691 trades net 37159.82 vs reference 691 net 37159.82 -> IDENTICAL
  - TL3_DD_JL3_REF_O 202504: 637 trades net 41239.76 vs reference 637 net 41239.76 -> IDENTICAL
  - TL3_DD_JL3_REF_O 202610: 691 trades net 37159.82 vs reference 691 net 37159.82 -> IDENTICAL
  - TL3_DD_JL3_REF_P 202504: 637 trades net 41239.76 vs reference 637 net 41239.76 -> IDENTICAL
  - TL3_DD_JL3_REF_P 202610: 691 trades net 37159.82 vs reference 691 net 37159.82 -> IDENTICAL
  - TL3_DD_JL2_ID 202610: 642 trades net 27487.58 vs reference 642 net 27487.58 -> IDENTICAL
  - TL3_DD_JL2_REF_O 202610: 642 trades net 27487.58 vs reference 642 net 27487.58 -> IDENTICAL
- JL3 months landed (of 43): REF 44; LATCH 23; BE 19; BT 19; C 23; D2 23; D4 23; F 23; OFF 43; grid cells: 0 of 30 with all 43 months, 30 with any month. Inert-month copies written by the prefilter: 439 (a month in which the rule condition never holds on the OFF trade list cannot change anything; verification runs: see section 9).
- Controls: A 12 draws landed (target halted share 0.098, p 0.177, tol 0.024, 30 seeds chosen ex ante); B 0 draws landed (target halted share 0.098, p 0.177, tol 0.024, 30 seeds chosen ex ante); C 0 draws landed (target halted share 0.085, p 0.383, tol 0.021, 30 seeds chosen ex ante); D2 0 draws landed (target halted share 0.092, p 0.278, tol 0.023, 30 seeds chosen ex ante); D4 0 draws landed (target halted share 0.094, p 0.230, tol 0.023, 30 seeds chosen ex ante); F 0 draws landed (target halted share 0.055, p 0.099, tol 0.014, 30 seeds chosen ex ante); X_R3_1000 0 draws landed (target halted share 0.098, p 0.189, tol 0.024, 30 seeds chosen ex ante); X_R3_2000 0 draws landed (target halted share 0.098, p 0.189, tol 0.024, 30 seeds chosen ex ante); X_R3_3000 0 draws landed (target halted share 0.098, p 0.189, tol 0.024, 30 seeds chosen ex ante). A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Rule as implemented (code/th_dd/dd_hooks.py): the live C22 gate = stack closes today >= n AND stack day P&L (net of fees, engine BASE lots) <= thr, day = 17:00 ET roll, checked at every entry attempt (not latched). Live $4,200 = 2,400 base (x1.75). Variants replace the gate (OFF + hook). The engine's gate is NOT latched; the live rule may latch at the trip (variant a2).

## Table 1 - JL3: ulcer change / mean change vs OFF per window (engine base lots; ulcer + = lower than OFF); the reference row REF is the live setting itself
Ulcer = RMS of daily drawdown on cumulative P&L. P(lower) = week-clustered bootstrap (2,000) that the variant ulcer < OFF ulcer. Percentiles: Table 2. Days halted = label days with a trip on the cell's own closed-trade list (open-P&L cells approximate).

| setting | months | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | halted days L6M / pooled | halted share of sessions | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 44 | +30.5% / +1,687 | +0.4% / +992 | +0.1% / -166 | +0.7% / +347 | +1.3% / -104 | +1.6% / +393 | 0.96 / 0.81 / 0.75 | 50 / 160 | 0.096 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| a2. live rule latched at the 22nd close, until reset | 23 | +32.1% / +1,594 | +0.4% / +940 | n/l | n/l | n/l | n/l | 0.97 / 0.81 / n/l | 50 / n/l | 0.115 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| b1. open P&L counted, checked at entry, until reset | 19 | +30.6% / +1,705 | +0.3% / +921 | n/l | n/l | n/l | n/l | 0.96 / 0.81 / n/l | 50 / n/l | 0.138 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| b2. open P&L counted, checked at each close, latched to reset | 19 | +32.6% / +1,483 | +0.1% / +801 | n/l | n/l | n/l | n/l | 0.97 / 0.80 / n/l | 49 / n/l | 0.137 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| c. halt to next session boundary (22 / -4,200) | 23 | +25.6% / +1,641 | -5.2% / +281 | n/l | n/l | n/l | n/l | 0.84 / 0.68 / n/l | 50 / n/l | 0.096 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| d. halt 2 h | 23 | +18.1% / +2,542 | -13.9% / -253 | n/l | n/l | n/l | n/l | 0.73 / 0.54 / n/l | 50 / n/l | 0.109 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| d. halt 4 h | 23 | +26.2% / +1,919 | -9.9% / +411 | n/l | n/l | n/l | n/l | 0.96 / 0.67 / n/l | 50 / n/l | 0.112 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| f. per-book (books net negative on the day stop) | 23 | +15.5% / -42 | -0.1% / +969 | n/l | n/l | n/l | n/l | 0.36 / 0.84 / n/l | 50 / n/l | 0.066 | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |

Same, vs REF (the live setting; ulcer + = lower than live):

| setting | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|
| a2. live rule latched at the 22nd close, until reset | +2.2% / -93 | -0.0% / -52 | n/l | n/l | n/l | n/l |
| b1. open P&L counted, checked at entry, until reset | +0.1% / +18 | -0.0% / -71 | n/l | n/l | n/l | n/l |
| b2. open P&L counted, checked at each close, latched to reset | +3.0% / -204 | -0.3% / -191 | n/l | n/l | n/l | n/l |
| c. halt to next session boundary (22 / -4,200) | -7.0% / -46 | -5.6% / -710 | n/l | n/l | n/l | n/l |
| d. halt 2 h | -17.9% / +856 | -14.3% / -1,244 | n/l | n/l | n/l | n/l |
| d. halt 4 h | -6.3% / +232 | -10.3% / -581 | n/l | n/l | n/l | n/l |
| f. per-book (books net negative on the day stop) | -21.6% / -1,729 | -0.4% / -23 | n/l | n/l | n/l | n/l |

## Table 2 - percentile among the controls of the matching family (JL3; real vs OFF + random halts of the same halted share), three price/size columns
pct = share of valid controls the setting beats (ulcer: lower is better; mean). Columns: base lots $1.18 RT | $4.84 RT | x1.75 live lots (live lots = max(1, floor(1.75 x base + 0.5))). Halted share check: cell share vs the family target.

| setting | family | halted share cell / ctrl target | valid ctrl L6M | pct ulcer L6M base / 4.84 / live | pct mean L6M base / 4.84 / live | pct ulcer L3M | pct ulcer HOLD | pct ulcer GAP / PRE / X' | pct ulcer pooled | tier | tier W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | A | 0.096 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| a2. live rule latched at the 22nd close, until reset | A | 0.115 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| b1. open P&L counted, checked at entry, until reset | B | 0.138 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| b2. open P&L counted, checked at each close, latched to reset | B | 0.137 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| c. halt to next session boundary (22 / -4,200) | C | 0.096 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| d. halt 2 h | D2 | 0.109 / 0.092 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| d. halt 4 h | D4 | 0.112 / 0.094 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| f. per-book (books net negative on the day stop) | F | 0.066 / 0.055 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_18_3000 | A | 0.231 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.231 vs controls 0.098, tol 0.024 x2): not passing | INVALID CONTROLS (halted share cell 0.231 vs controls 0.098, tol 0.024 x2): not passing |
| G_18_4200 | A | 0.220 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.220 vs controls 0.098, tol 0.024 x2): not passing | INVALID CONTROLS (halted share cell 0.220 vs controls 0.098, tol 0.024 x2): not passing |
| G_18_6000 | A | 0.180 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.180 vs controls 0.098, tol 0.024 x2): not passing | INVALID CONTROLS (halted share cell 0.180 vs controls 0.098, tol 0.024 x2): not passing |
| G_18_8000 | A | 0.145 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_22_3000 | A | 0.122 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_22_6000 | A | 0.104 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_22_8000 | A | 0.095 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_26_3000 | A | 0.086 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_26_4200 | A | 0.083 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_26_6000 | A | 0.074 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_26_8000 | A | 0.068 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_30_3000 | A | 0.057 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_30_4200 | A | 0.054 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| G_30_6000 | A | 0.047 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.047 vs controls 0.098, tol 0.024 x2): not passing | INVALID CONTROLS (halted share cell 0.047 vs controls 0.098, tol 0.024 x2): not passing |
| G_30_8000 | A | 0.041 / 0.098 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.041 vs controls 0.098, tol 0.024 x2): not passing | INVALID CONTROLS (halted share cell 0.041 vs controls 0.098, tol 0.024 x2): not passing |
| GC_18_3000 | C | 0.199 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.199 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.199 vs controls 0.085, tol 0.021 x2): not passing |
| GC_18_4200 | C | 0.189 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.189 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.189 vs controls 0.085, tol 0.021 x2): not passing |
| GC_18_6000 | C | 0.157 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.157 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.157 vs controls 0.085, tol 0.021 x2): not passing |
| GC_18_8000 | C | 0.128 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.128 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.128 vs controls 0.085, tol 0.021 x2): not passing |
| GC_22_3000 | C | 0.107 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_22_6000 | C | 0.091 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_22_8000 | C | 0.082 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_26_3000 | C | 0.076 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_26_4200 | C | 0.072 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_26_6000 | C | 0.065 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_26_8000 | C | 0.057 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_30_3000 | C | 0.049 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_30_4200 | C | 0.047 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) | NOT FINISHED |
| GC_30_6000 | C | 0.042 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.042 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.042 vs controls 0.085, tol 0.021 x2): not passing |
| GC_30_8000 | C | 0.036 / 0.085 | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | INVALID CONTROLS (halted share cell 0.036 vs controls 0.085, tol 0.021 x2): not passing | INVALID CONTROLS (halted share cell 0.036 vs controls 0.085, tol 0.021 x2): not passing |

## Table 3 - what the halt skipped (JL3 cell vs OFF; trades present in OFF and absent in the cell = skipped, trades only in the cell = gained after the freed room; base-lot dollars, OFF lots)
Positive $ on the skipped trades = the skipped sessions were winners on average (the halt cost money); negative = losers (the halt saved money). Common-trade change = path effect on trades both runs share.

Window L6M
| setting | skipped n / $ / $ per trade | gained n / $ | common-trade change $ (n) | net change $ | skipped were |
|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 682 / -41,362 / -61 | 1 / +1,199 | +1,778 (1) | +44,339 | LOSERS (halt saves money) |
| a2. live rule latched at the 22nd close, until reset | 746 / -41,893 / -56 | 0 / +0 | +0 (0) | +41,893 | LOSERS (halt saves money) |
| b1. open P&L counted, checked at entry, until reset | 689 / -45,730 / -66 | 1 / -915 | +0 (0) | +44,815 | LOSERS (halt saves money) |
| b2. open P&L counted, checked at each close, latched to reset | 736 / -38,988 / -53 | 0 / +0 | +0 (0) | +38,988 | LOSERS (halt saves money) |
| c. halt to next session boundary (22 / -4,200) | 623 / -50,480 / -81 | 19 / -6,639 | -717 (1) | +43,124 | LOSERS (halt saves money) |
| d. halt 2 h | 558 / -50,844 / -91 | 57 / +17,327 | -1,342 (2) | +66,829 | LOSERS (halt saves money) |
| d. halt 4 h | 671 / -57,483 / -86 | 43 / -7,043 | +0 (0) | +50,439 | LOSERS (halt saves money) |
| f. per-book (books net negative on the day stop) | 557 / +2,704 / +5 | 2 / -176 | +1,778 (1) | -1,101 | WINNERS (halt costs money) |

Window HOLD
| setting | skipped n / $ / $ per trade | gained n / $ | common-trade change $ (n) | net change $ | skipped were |
|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 372 / -22,679 / -61 | 4 / +2,969 | +0 (0) | +25,649 | LOSERS (halt saves money) |
| a2. live rule latched at the 22nd close, until reset | 385 / -24,294 / -63 | 0 / +0 | +0 (0) | +24,294 | LOSERS (halt saves money) |
| b1. open P&L counted, checked at entry, until reset | 370 / -23,819 / -64 | 0 / +0 | +0 (0) | +23,819 | LOSERS (halt saves money) |
| b2. open P&L counted, checked at each close, latched to reset | 385 / -20,709 / -54 | 0 / +0 | +0 (0) | +20,709 | LOSERS (halt saves money) |
| c. halt to next session boundary (22 / -4,200) | 319 / -12,745 / -40 | 5 / -4,901 | -567 (1) | +7,277 | LOSERS (halt saves money) |
| d. halt 2 h | 311 / +4,453 / +14 | 31 / -2,077 | +0 (0) | -6,530 | WINNERS (halt costs money) |
| d. halt 4 h | 346 / -13,741 / -40 | 9 / -2,492 | -610 (2) | +10,638 | LOSERS (halt saves money) |
| f. per-book (books net negative on the day stop) | 298 / -20,882 / -70 | 5 / +4,168 | +0 (0) | +25,051 | LOSERS (halt saves money) |

Window pooled
| setting | skipped n / $ / $ per trade | gained n / $ | common-trade change $ (n) | net change $ | skipped were |
|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 1526 / -69,606 / -46 | 7 / +2,234 | +1,778 (1) | +73,618 | LOSERS (halt saves money) |
| a2. live rule latched at the 22nd close, until reset | n/l | | | | |
| b1. open P&L counted, checked at entry, until reset | n/l | | | | |
| b2. open P&L counted, checked at each close, latched to reset | n/l | | | | |
| c. halt to next session boundary (22 / -4,200) | n/l | | | | |
| d. halt 2 h | n/l | | | | |
| d. halt 4 h | n/l | | | | |
| f. per-book (books net negative on the day stop) | n/l | | | | |

## Table 4 - absolute risk metrics (JL3, base lots): ulcer index (RMS daily DD), mean $/wk, max DD, worst week

Window L6M
| setting | ulcer | mean $/wk | max DD | worst week | x1.75 live: ulcer / mean / max DD |
|--|--|--|--|--|--|
| OFF (layer removed) | 13,206 | +18,422 | -43,429 | -20,041 | 28,657 / +34,222 / -96,394 |
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 9,176 | +20,109 | -30,189 | -15,066 | 18,465 / +37,463 / -60,591 |
| a2. live rule latched at the 22nd close, until reset | 8,973 | +20,015 | -30,189 | -15,066 | 17,874 / +37,254 / -59,569 |
| b1. open P&L counted, checked at entry, until reset | 9,165 | +20,127 | -30,189 | -15,066 | 18,270 / +37,499 / -59,569 |
| b2. open P&L counted, checked at each close, latched to reset | 8,903 | +19,905 | -29,642 | -14,518 | 17,731 / +37,056 / -58,475 |
| c. halt to next session boundary (22 / -4,200) | 9,820 | +20,062 | -34,248 | -16,876 | 19,558 / +37,347 / -67,900 |
| d. halt 2 h | 10,818 | +20,964 | -41,418 | -23,213 | 23,131 / +39,275 / -89,596 |
| d. halt 4 h | 9,750 | +20,341 | -33,154 | -17,087 | 21,736 / +37,904 / -76,837 |
| f. per-book (books net negative on the day stop) | 11,158 | +18,380 | -34,956 | -21,261 | 24,467 / +34,052 / -80,441 |

Window HOLD
| setting | ulcer | mean $/wk | max DD | worst week | x1.75 live: ulcer / mean / max DD |
|--|--|--|--|--|--|
| OFF (layer removed) | 27,971 | +9,004 | -87,011 | -35,337 | 52,512 / +17,293 / -170,319 |
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 27,872 | +9,996 | -82,017 | -36,787 | 51,886 / +19,402 / -152,332 |
| a2. live rule latched at the 22nd close, until reset | 27,872 | +9,944 | -82,017 | -36,787 | 51,887 / +19,297 / -152,332 |
| b1. open P&L counted, checked at entry, until reset | 27,874 | +9,926 | -82,017 | -36,787 | 51,888 / +19,214 / -152,332 |
| b2. open P&L counted, checked at each close, latched to reset | 27,942 | +9,805 | -82,017 | -36,787 | 52,035 / +19,020 / -152,332 |
| c. halt to next session boundary (22 / -4,200) | 29,435 | +9,286 | -84,718 | -39,373 | 55,121 / +17,981 / -157,734 |
| d. halt 2 h | 31,872 | +8,752 | -85,403 | -38,704 | 60,173 / +16,913 / -159,104 |
| d. halt 4 h | 30,747 | +9,416 | -87,467 | -37,098 | 57,617 / +18,241 / -163,233 |
| f. per-book (books net negative on the day stop) | 27,994 | +9,973 | -83,310 | -36,787 | 51,909 / +19,356 / -154,918 |

Window pooled
| setting | ulcer | mean $/wk | max DD | worst week | x1.75 live: ulcer / mean / max DD |
|--|--|--|--|--|--|
| OFF (layer removed) | 24,741 | +7,629 | -87,011 | -38,734 | 47,540 / +14,351 / -170,319 |
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 24,344 | +8,022 | -88,502 | -38,412 | 46,574 / +15,137 / -172,602 |

## Table 5 - threshold grid (JL3): ulcer change vs OFF % / mean change $/wk base; rows = closes, columns = live day loss

live form (eval at entry, until reset) - window L6M
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | +18.2% / +1,094 | +16.3% / +1,065 | +9.7% / +699 | +13.4% / +1,041 |
| 22 | +31.6% / +1,715 | +30.5% / +1,687 | +30.0% / +1,581 | +25.3% / +1,362 |
| 26 | +28.9% / +836 | +28.2% / +554 | +29.5% / +628 | +24.4% / +557 |
| 30 | +15.7% / -20 | +11.9% / -203 | +5.3% / -167 | +6.5% / -39 |

live form (eval at entry, until reset) - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | +16.8% / +2,070 | +0.8% / +1,464 | -2.0% / +1,513 | -1.0% / +974 |
| 22 | +6.6% / +1,223 | +0.4% / +992 | -5.0% / +757 | -7.9% / +406 |
| 26 | +10.8% / +1,192 | +3.9% / +859 | -3.1% / +535 | -4.7% / +405 |
| 30 | +6.8% / +998 | +8.4% / +992 | +6.8% / +773 | +4.8% / +719 |

live form (eval at entry, until reset) - window pooled
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | +1.6% / +393 | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

halt only to the next session boundary - window L6M
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | +20.5% / +723 | +19.0% / +497 | +8.8% / +360 | +8.4% / +413 |
| 22 | +23.3% / +1,023 | +25.6% / +1,641 | +21.9% / +834 | +16.9% / +870 |
| 26 | +22.6% / +556 | +22.3% / +509 | +24.1% / +350 | +19.6% / +631 |
| 30 | +9.6% / +173 | +8.7% / +166 | -1.5% / +179 | +2.4% / +176 |

halt only to the next session boundary - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | +7.5% / +1,383 | -1.3% / +819 | -7.6% / +931 | -11.7% / +393 |
| 22 | +2.0% / +569 | -5.2% / +281 | -11.1% / +165 | -16.9% / -131 |
| 26 | +5.2% / +678 | -1.4% / +409 | -2.7% / +365 | -10.2% / +88 |
| 30 | +5.1% / +583 | +7.5% / +629 | +3.0% / +403 | -2.8% / +295 |

halt only to the next session boundary - window pooled
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | n/l | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

## Table 6 - JL2 for comparison (REF vs OFF; top variants when queued)
| setting | months | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|--|
| JL2 a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 44 | +33.8% / +2,555 | n/l | n/l | n/l | n/l | n/l |

## Table 7 - selection statistics over the 37 settings (needs all 37 with all 43 months)
NOT FINISHED: 0 of 37 settings have all 43 months. RC / SPA / DSR / PBO are not issued until then.

## 8. Controls
| family | stands for | target halted share (cell on OFF path) | p per day | tol | seeds chosen ex ante | landed |
|--|--|--|--|--|--|--|
| A | REF, LATCH, live-form grid | 0.0976 | 0.1772 | 0.0244 | 30 | 12 |
| B | BE, BT | 0.0976 | 0.1772 | 0.0244 | 30 | 0 |
| C | C, session-boundary grid | 0.0847 | 0.3833 | 0.0212 | 30 | 0 |
| D2 | D2 | 0.0920 | 0.2784 | 0.0230 | 30 | 0 |
| D4 | D4 | 0.0936 | 0.2299 | 0.0234 | 30 | 0 |
| F | F (per book) | 0.0553 | 0.0992 | 0.0138 | 30 | 0 |
| X_R3_1000 | resume-rule controls X_R3_1000 | 0.0976 | 0.1886 | 0.0244 | 30 | 0 |
| X_R3_2000 | resume-rule controls X_R3_2000 | 0.0976 | 0.1886 | 0.0244 | 30 | 0 |
| X_R3_3000 | resume-rule controls X_R3_3000 | 0.0976 | 0.1886 | 0.0244 | 30 | 0 |

Control design: persistent draw, one uniform per (seed, label day [, book]) < p starts a halt at the 17:00 ET roll + a start drawn from the 163 real trip times of the live rule on the JL3 path (so halts start when the real ones do), lasting per the family (day-reset, next session boundary, 2 h, 4 h). Nothing about trading enters the draw. Because the draw is independent of the trading path, the halted share of sessions (label days x sessions asia, london, nyam, nypm; a session counts when a halt intersects it) is computed analytically over the 927 calendar days and the 30 seeds per family are the first whose share is within max(min(0.05, 0.25 x target), 0.002) of the target, chosen BEFORE any result (not by pilot runs as in W-CELL: the share does not depend on the path). The cell's own halted share is measured from its trade list and checked against the target (within 2 x tol, else INVALID, never passing).

## 9. Identity, prefilter, verification
Verification runs of the inert-month copies vs OFF: queued, not landed
## 10. LATCH: what the live DS7 v2.0 code does (read from /mnt/l2/l2vast/_ds7v20/DS7.cs, V9Gate, the DAY-DONE block, lines 2279-2300)
- Live is NOT latched. V9Gate re-evaluates the condition at EVERY entry attempt: closes = sum over books of Book.TradesToday, day = sum over books of Book.DayPnl; it skips the entry when closes >= DayDoneCloses (22) AND day <= -DayDoneLossDollars (4,200). If the day figure climbs back above -4,200 the gate lets entries through again; on the night of 11-16 the day finished at -5,450 (still under the line), so every signal stayed skipped.
- What counts: Book.DayPnl = Realized - SessionBase + CarryDay = REALISED closed-trade P&L only (no open P&L). TradesToday is incremented once per full trade close (ClosePosition path, lines 3978 and 4000); partial exits are not counted until the trade is closed. Counters reset at the session roll; a restart zeroes them (the v2.0 header notes the restart bug and fix).
- So the engine gate (eval form at entry attempts, realised closes, closed trades) is the same rule as live: the reference row REF is the live rule. The latched form (a2, LATCH) and the open-P&L forms (b1, b2) are VARIANTS, not the live behaviour; both forms are run.

## 11. CONDITIONAL RESUME after a DAY-DONE trip (order 15:09Z): R1 shadow recovery, R2 new session + health, R3 day P&L recovery, R4 probation size, R5 side-specific, R6 book-specific
Cells TL3_DD_JL3_<R code> = OFF + hook code/th_dd/dd_resume.py: trip as live (22 closes, live -4,200 = -2,400 base); after the trip entries stay skipped until the resume condition holds; after a resume the gate is off for the day unless 2 consecutive losing closes follow (then halted to the 17:00 ET roll). Shadow trades for R1/R2 = the OFF run's trades entered after the trip (the engine path equals the OFF path up to the trip and nothing is entered between trip and resume, so they are the exact shadow trades with the same brackets, cuts, lots and stack state; after a first resume the paths differ, and the re-halt rule is then live in the hook). R1: N = last N shadow trades net positive (2,3,4) or shadow P&L since the halt >= +X base (1,000 / 2,000 / 3,000); R2: at the next session open 02:00 / 09:30 / 12:00 ET if atr_rel at the open < 1.3 (R2_13) or < 1.6 (R2_16), else when the first shadow trade of the new session closes a winner; R3: realised + open day P&L >= trip level + 1,000 / 2,000 / 3,000 live (571 / 1,143 / 1,714 base); R4: resume at the next session boundary at half lots, full after 2 winning closes; R5: only the side with the net day loss stays halted (no resume); R6: books net negative on the day halted, they resume at the next session boundary at half size (R4 mechanics per book), books net positive keep trading.

| resume rule | months | L6M | HOLD | GAP | PRE | X' | pooled | halted share (designed) | halted days L6M / pooled | pct ulcer L6M / HOLD (family controls) | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| R1_N2 | 12 | +7.8% / -663 | +12.2% / +1,534 | n/l | n/l | n/l | n/l | 0.057 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R1_N3 | 12 | +21.6% / +1,078 | -2.6% / +522 | n/l | n/l | n/l | n/l | 0.065 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R1_N4 | 12 | +22.1% / +1,191 | -7.1% / +679 | n/l | n/l | n/l | n/l | 0.067 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R1_X1000 | 12 | +24.1% / +538 | -10.8% / -6 | n/l | n/l | n/l | n/l | 0.067 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R1_X2000 | 12 | +26.6% / +995 | -3.8% / +586 | n/l | n/l | n/l | n/l | 0.077 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R1_X3000 | 12 | +28.5% / +1,428 | -4.4% / +458 | n/l | n/l | n/l | n/l | 0.082 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R2_13 | 12 | +29.1% / +834 | -17.5% / +69 | n/l | n/l | n/l | n/l | 0.086 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R2_16 | 12 | +27.4% / +589 | -17.5% / +69 | n/l | n/l | n/l | n/l | 0.084 | 50 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R3_1000 | 12 | +32.0% / +1,599 | +0.0% / +1,050 | n/l | n/l | n/l | n/l | 0.098 | 50 / n/l | n/a / n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| R3_2000 | 12 | +32.4% / +1,513 | +0.4% / +1,120 | n/l | n/l | n/l | n/l | 0.098 | 50 / n/l | n/a / n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| R3_3000 | 12 | +32.4% / +1,513 | +0.4% / +940 | n/l | n/l | n/l | n/l | 0.098 | 50 / n/l | n/a / n/a | NOT FINISHED (fewer than 10 valid controls in L6M/L3M or windows missing) |
| R4 | 12 | +21.4% / +362 | -8.5% / +49 | n/l | n/l | n/l | n/l | 0.039 | 51 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R5 | 12 | +15.6% / +2,038 | +3.1% / +560 | n/l | n/l | n/l | n/l | 0.049 | 51 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R6 | 12 | +6.8% / +468 | -17.1% / -385 | n/l | n/l | n/l | n/l | 0.039 | 51 / n/l | n/a / n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| R_BEST2 | 0 | not landed | | | | | | | | | |

Same, ulcer / mean vs REF (the live rule, + = better than live):
| resume rule | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|
| R1_N2 | -32.7% / -2,350 | +11.8% / +543 | n/l | n/l | n/l | n/l |
| R1_N3 | -12.8% / -608 | -3.0% / -470 | n/l | n/l | n/l | n/l |
| R1_N4 | -12.0% / -496 | -7.5% / -313 | n/l | n/l | n/l | n/l |
| R1_X1000 | -9.2% / -1,149 | -11.2% / -998 | n/l | n/l | n/l | n/l |
| R1_X2000 | -5.6% / -692 | -4.1% / -406 | n/l | n/l | n/l | n/l |
| R1_X3000 | -2.9% / -259 | -4.7% / -534 | n/l | n/l | n/l | n/l |
| R2_13 | -2.1% / -853 | -17.9% / -923 | n/l | n/l | n/l | n/l |
| R2_16 | -4.5% / -1,097 | -17.9% / -923 | n/l | n/l | n/l | n/l |
| R3_1000 | +2.1% / -88 | -0.4% / +58 | n/l | n/l | n/l | n/l |
| R3_2000 | +2.7% / -173 | +0.0% / +128 | n/l | n/l | n/l | n/l |
| R3_3000 | +2.7% / -173 | -0.0% / -52 | n/l | n/l | n/l | n/l |
| R4 | -13.2% / -1,324 | -8.8% / -943 | n/l | n/l | n/l | n/l |
| R5 | -21.5% / +351 | +2.8% / -432 | n/l | n/l | n/l | n/l |
| R6 | -34.2% / -1,219 | -17.5% / -1,377 | n/l | n/l | n/l | n/l |

Walk-forward pick (SEL = 2023-04..2025-10 ulcer vs OFF; tested on the untouched L6M and HOLD): NOT FINISHED (needs all SEL months of every cell of the group; older months are queued as the OFF months land)

## 12. What the halt cost or saved: shadow P&L of the skipped sessions after every trip (JL3; shadow trades = the OFF run's trades entered after the trip of that label day, base lots, net of fees; x1.75 = live lots approx.)
Tripped days: 163 (months with OFF landed: 32). Format: days with >= 1 shadow trade in the session | mean $ per tripped day | share of those days positive | worst day | sum.

pooled (all OFF months landed): 163 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 3 | -1,962 | -3,433 | 0.00 | -2,914 | -5,885 |
| London | 67 | +38 | +66 | 0.57 | -9,902 | +2,540 |
| NY AM | 129 | -289 | -505 | 0.47 | -6,161 | -37,240 |
| NY PM | 117 | -231 | -405 | 0.41 | -4,327 | -27,073 |
| total | 150 | -451 | -789 | 0.44 | -14,094 | -67,658 |

L6M + HOLD (2025-11..2026-10): 89 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 3 | -1,962 | -3,433 | 0.00 | -2,914 | -5,885 |
| London | 52 | +193 | +338 | 0.58 | -9,902 | +10,043 |
| NY AM | 82 | -479 | -839 | 0.44 | -5,935 | -39,298 |
| NY PM | 62 | -501 | -876 | 0.37 | -4,327 | -31,046 |
| total | 86 | -770 | -1,347 | 0.41 | -14,094 | -66,187 |

older (before 2025-11): 74 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 0 | | | | | |
| London | 15 | -500 | -875 | 0.53 | -5,913 | -7,503 |
| NY AM | 47 | +44 | +77 | 0.51 | -6,161 | +2,058 |
| NY PM | 55 | +72 | +126 | 0.45 | -3,084 | +3,973 |
| total | 64 | -23 | -40 | 0.48 | -7,646 | -1,471 |

Negative mean = the skipped sessions were net losers (the halt saved money); positive = winners (the halt cost money).

## 13. DS7 needs for a resume rule
- DAY-DONE today needs only Book.TradesToday and Book.DayPnl (exist). R3 needs the stack open P&L at the check (ComboDayPnl(px) exists, line 4251). R4/R6 need a per-day state flag plus a half-lot multiplier at entry (lots go through Jn04Size/V9Gate: a day-scoped multiplier is new code). R5 needs net P&L by side for the day (new counter). R1 and R2 need SHADOW trade bookkeeping that the existing Shadow modes do not provide for skipped signals: the Shadow modes log what a feature WOULD have done but do not simulate the skipped entry through brackets, cuts and exits; a shadow-trade ledger (virtual entry at the signal, virtual stop/target/cut exits, virtual P&L per book and day) is missing and is new code; R2 also needs atr_rel at the session open (jnAtr exists).

## Notes and limits
- Everything is FIRST PASS and in-sample on 43 months; a window is shown only when every month of it landed for the cell and OFF. n/l = not landed; missing controls = NOT FINISHED, never passing.
- Live-vs-engine: the live night of 11-16 (22 closes, -9,660 live, halt 01:26 ET to the 18:00 reset, day -5,450) is one event; the engine day-figure counts realised closes only. Variants b1/b2 test whether open profits would have kept the halt from tripping.
- The engine's gate is evaluated at entry attempts and is not latched; a2 latches it at the trip close. c/d are trip-form: the halt starts at the closing trade that satisfies the condition, ends at the boundary / after N hours, and any later close that still satisfies the condition re-trips it.
- Inert-month copies: for settings with n >= 26 the condition rarely holds on a month's OFF trades, so those months are copies of OFF (hook cannot act). The tier percentiles use only landed, validated months.
