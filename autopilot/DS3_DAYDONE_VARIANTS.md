# DS3_DAYDONE_VARIANTS - DAY-DONE settings on the exact engine (W-DD, order 11-17 13:31Z)
VERDICT (data ends 2026-10-31; FIRST PASS 2026-11-17 16:49Z; OFF landed 12 of 43 months; ulcer index primary; tiers use the calibrated cut-offs): no variant has a scored tier yet (controls or windows missing = NOT FINISHED, never passing). No removal of the live rule is implied; this is a search for a better SETTING of the same layer.

> VALIDATION (desk standard, W-DD, FIRST PASS, 2026-11-17 16:49Z): trials counted = 37 settings on JL3 (7 named variants LATCH BE BT C D2 D4 F + 30 grid cells = closes {18,22,26,30} x live loss {3,000 4,200 6,000 8,000} for the eval form and for the session-boundary form, minus the two cells that equal REF and C), plus the references REF / OFF and JL2 OFF; controls = 6 families x 30 persistent random-day-halt draws (A day-reset, B open-P&L, C session, D2, D4, F per-book); correction = percentile among the controls of the matching family on the calibrated tiers, and over the 37 settings White RC / Hansen SPA / DSR / BH on weekly P&L deltas vs REF (mean) plus a block-bootstrap reality check on the ulcer statistic and PBO (CSCV, weekly P&L of the 37 + REF); in-sample on the 43 months (no fitted choice; recent windows L6M/L3M and older HOLD/GAP/PRE/X' are the walk-forward-style split); FIRST PASS, shown only for what landed.

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
- JL3 months landed (of 43): REF 43; LATCH 12; BE 12; BT 12; C 12; D2 12; D4 12; F 12; OFF 12; grid cells: 0 of 30 with all 43 months, 1 with any month. Inert-month copies written by the prefilter: 0 (a month in which the rule condition never holds on the OFF trade list cannot change anything; verification runs: see section 9).
- Controls: not built yet: the controls are calibrated on the OFF path once all 43 OFF months have landed (analytic halted-share match; sets pre-listed in the queue). A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Rule as implemented (code/th_dd/dd_hooks.py): the live C22 gate = stack closes today >= n AND stack day P&L (net of fees, engine BASE lots) <= thr, day = 17:00 ET roll, checked at every entry attempt (not latched). Live $4,200 = 2,400 base (x1.75). Variants replace the gate (OFF + hook). The engine's gate is NOT latched; the live rule may latch at the trip (variant a2).

## Table 1 - JL3: ulcer change / mean change vs OFF per window (engine base lots; ulcer + = lower than OFF); the reference row REF is the live setting itself
Ulcer = RMS of daily drawdown on cumulative P&L. P(lower) = week-clustered bootstrap (2,000) that the variant ulcer < OFF ulcer. Percentiles: Table 2. Days halted = label days with a trip on the cell's own closed-trade list (open-P&L cells approximate).

| setting | months | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | halted days L6M / pooled | halted share of sessions | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 43 | +30.5% / +1,687 | +0.4% / +992 | n/l | n/l | n/l | n/l | 0.96 / 0.81 / n/l | 50 / 160 | 0.096 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| a2. live rule latched at the 22nd close, until reset | 12 | +32.1% / +1,594 | +0.4% / +940 | n/l | n/l | n/l | n/l | 0.97 / 0.81 / n/l | 50 / n/l | 0.220 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| b1. open P&L counted, checked at entry, until reset | 12 | +30.6% / +1,705 | +0.3% / +921 | n/l | n/l | n/l | n/l | 0.96 / 0.81 / n/l | 50 / n/l | 0.218 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| b2. open P&L counted, checked at each close, latched to reset | 12 | +32.6% / +1,483 | +0.1% / +801 | n/l | n/l | n/l | n/l | 0.97 / 0.80 / n/l | 49 / n/l | 0.217 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| c. halt to next session boundary (22 / -4,200) | 12 | +25.6% / +1,641 | -5.2% / +281 | n/l | n/l | n/l | n/l | 0.84 / 0.68 / n/l | 50 / n/l | 0.185 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| d. halt 2 h | 12 | +18.1% / +2,542 | -13.9% / -253 | n/l | n/l | n/l | n/l | 0.73 / 0.54 / n/l | 50 / n/l | 0.209 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| d. halt 4 h | 12 | +26.2% / +1,919 | -9.9% / +411 | n/l | n/l | n/l | n/l | 0.96 / 0.67 / n/l | 50 / n/l | 0.215 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| f. per-book (books net negative on the day stop) | 12 | +15.5% / -42 | -0.1% / +969 | n/l | n/l | n/l | n/l | 0.36 / 0.84 / n/l | 50 / n/l | 0.126 | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |

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
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | A | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| a2. live rule latched at the 22nd close, until reset | A | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| b1. open P&L counted, checked at entry, until reset | B | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| b2. open P&L counted, checked at each close, latched to reset | B | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| c. halt to next session boundary (22 / -4,200) | C | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| d. halt 2 h | D2 | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| d. halt 4 h | D4 | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| f. per-book (books net negative on the day stop) | F | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |
| G_18_3000 | A | n/l | 0 | n/a / n/a / n/a | n/a / n/a / n/a | n/a | n/a | n/a / n/a / n/a | n/a | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) | NO MATCHED CONTROLS (grid cell: ulcer/mean only, no tier) |

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
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | n/l | | | | |
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

## Table 5 - threshold grid (JL3): ulcer change vs OFF % / mean change $/wk base; rows = closes, columns = live day loss

live form (eval at entry, until reset) - window L6M
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | +18.2% / +1,094 | n/l | n/l | n/l |
| 22 | n/l | +30.5% / +1,687 | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

live form (eval at entry, until reset) - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | +0.4% / +992 | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

live form (eval at entry, until reset) - window pooled
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | n/l | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

halt only to the next session boundary - window L6M
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | +25.6% / +1,641 | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

halt only to the next session boundary - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | -5.2% / +281 | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

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

## Table 7 - selection statistics over the 37 settings (needs all 37 with all 43 months)
NOT FINISHED: 0 of 37 settings have all 43 months. RC / SPA / DSR / PBO are not issued until then.

## 8. Controls
| family | stands for | target halted share (cell on OFF path) | p per day | tol | seeds chosen ex ante | landed |
|--|--|--|--|--|--|--|

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
| R1_N2 | 0 | not landed | | | | | | | | | |
| R1_N3 | 0 | not landed | | | | | | | | | |
| R1_N4 | 0 | not landed | | | | | | | | | |
| R1_X1000 | 0 | not landed | | | | | | | | | |
| R1_X2000 | 0 | not landed | | | | | | | | | |
| R1_X3000 | 0 | not landed | | | | | | | | | |
| R2_13 | 0 | not landed | | | | | | | | | |
| R2_16 | 0 | not landed | | | | | | | | | |
| R3_1000 | 0 | not landed | | | | | | | | | |
| R3_2000 | 0 | not landed | | | | | | | | | |
| R3_3000 | 0 | not landed | | | | | | | | | |
| R4 | 0 | not landed | | | | | | | | | |
| R5 | 0 | not landed | | | | | | | | | |
| R6 | 0 | not landed | | | | | | | | | |
| R_BEST2 | 0 | not landed | | | | | | | | | |

Same, ulcer / mean vs REF (the live rule, + = better than live):
| resume rule | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|

Walk-forward pick (SEL = 2023-04..2025-10 ulcer vs OFF; tested on the untouched L6M and HOLD): NOT FINISHED (needs all SEL months of every cell of the group; older months are queued as the OFF months land)

## 12. What the halt cost or saved: shadow P&L of the skipped sessions after every trip (JL3; shadow trades = the OFF run's trades entered after the trip of that label day, base lots, net of fees; x1.75 = live lots approx.)
Tripped days: 89 (months with OFF landed: 12). Format: days with >= 1 shadow trade in the session | mean $ per tripped day | share of those days positive | worst day | sum.

pooled (all OFF months landed): 89 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 3 | -1,962 | -3,433 | 0.00 | -2,914 | -5,885 |
| London | 52 | +193 | +338 | 0.58 | -9,902 | +10,043 |
| NY AM | 82 | -479 | -839 | 0.44 | -5,935 | -39,298 |
| NY PM | 62 | -501 | -876 | 0.37 | -4,327 | -31,046 |
| total | 86 | -770 | -1,347 | 0.41 | -14,094 | -66,187 |

L6M + HOLD (2025-11..2026-10): 89 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 3 | -1,962 | -3,433 | 0.00 | -2,914 | -5,885 |
| London | 52 | +193 | +338 | 0.58 | -9,902 | +10,043 |
| NY AM | 82 | -479 | -839 | 0.44 | -5,935 | -39,298 |
| NY PM | 62 | -501 | -876 | 0.37 | -4,327 | -31,046 |
| total | 86 | -770 | -1,347 | 0.41 | -14,094 | -66,187 |

older (before 2025-11): 0 tripped days
| session skipped | days with trades | mean $/day base | mean x1.75 | share positive | worst day | sum $ |
|--|--|--|--|--|--|--|
| Asia | 0 | | | | | |
| London | 0 | | | | | |
| NY AM | 0 | | | | | |
| NY PM | 0 | | | | | |
| total | 0 | | | | | |

Negative mean = the skipped sessions were net losers (the halt saved money); positive = winners (the halt cost money).

## 13. DS7 needs for a resume rule
- DAY-DONE today needs only Book.TradesToday and Book.DayPnl (exist). R3 needs the stack open P&L at the check (ComboDayPnl(px) exists, line 4251). R4/R6 need a per-day state flag plus a half-lot multiplier at entry (lots go through Jn04Size/V9Gate: a day-scoped multiplier is new code). R5 needs net P&L by side for the day (new counter). R1 and R2 need SHADOW trade bookkeeping that the existing Shadow modes do not provide for skipped signals: the Shadow modes log what a feature WOULD have done but do not simulate the skipped entry through brackets, cuts and exits; a shadow-trade ledger (virtual entry at the signal, virtual stop/target/cut exits, virtual P&L per book and day) is missing and is new code; R2 also needs atr_rel at the session open (jnAtr exists).

## Notes and limits
- Everything is FIRST PASS and in-sample on 43 months; a window is shown only when every month of it landed for the cell and OFF. n/l = not landed; missing controls = NOT FINISHED, never passing.
- Live-vs-engine: the live night of 11-16 (22 closes, -9,660 live, halt 01:26 ET to the 18:00 reset, day -5,450) is one event; the engine day-figure counts realised closes only. Variants b1/b2 test whether open profits would have kept the halt from tripping.
- The engine's gate is evaluated at entry attempts and is not latched; a2 latches it at the trip close. c/d are trip-form: the halt starts at the closing trade that satisfies the condition, ends at the boundary / after N hours, and any later close that still satisfies the condition re-trips it.
- Inert-month copies: for settings with n >= 26 the condition rarely holds on a month's OFF trades, so those months are copies of OFF (hook cannot act). The tier percentiles use only landed, validated months.
