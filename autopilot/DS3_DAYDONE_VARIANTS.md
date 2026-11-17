# DS3_DAYDONE_VARIANTS - DAY-DONE settings on the exact engine (W-DD, order 11-17 13:31Z)
VERDICT (data ends 2026-10-31; FIRST PASS 2026-11-17 13:45Z; OFF landed 0 of 43 months; ulcer index primary; tiers use the calibrated cut-offs): no variant has a scored tier yet (controls or windows missing = NOT FINISHED, never passing). No removal of the live rule is implied; this is a search for a better SETTING of the same layer.

> VALIDATION (desk standard, W-DD, FIRST PASS, 2026-11-17 13:45Z): trials counted = 37 settings on JL3 (7 named variants LATCH BE BT C D2 D4 F + 30 grid cells = closes {18,22,26,30} x live loss {3,000 4,200 6,000 8,000} for the eval form and for the session-boundary form, minus the two cells that equal REF and C), plus the references REF / OFF and JL2 OFF; controls = 6 families x 30 persistent random-day-halt draws (A day-reset, B open-P&L, C session, D2, D4, F per-book); correction = percentile among the controls of the matching family on the calibrated tiers, and over the 37 settings White RC / Hansen SPA / DSR / BH on weekly P&L deltas vs REF (mean) plus a block-bootstrap reality check on the ulcer statistic and PBO (CSCV, weekly P&L of the 37 + REF); in-sample on the 43 months (no fitted choice; recent windows L6M/L3M and older HOLD/GAP/PRE/X' are the walk-forward-style split); FIRST PASS, shown only for what landed.

## Status (what has landed)
- IDENTITY gate (inert / re-implemented cell = TL3_EV_JL3 trade for trade on 202610 and 202504): pending
- JL3 months landed (of 43): REF 43; LATCH 0; BE 0; BT 0; C 0; D2 0; D4 0; F 0; OFF 0; grid cells: 0 of 30 with all 43 months, 0 with any month. Inert-month copies written by the prefilter: 0 (a month in which the rule condition never holds on the OFF trade list cannot change anything; verification runs: see section 9).
- Controls: not built yet: the controls are calibrated on the OFF path once all 43 OFF months have landed (analytic halted-share match; sets pre-listed in the queue). A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.
- Rule as implemented (code/th_dd/dd_hooks.py): the live C22 gate = stack closes today >= n AND stack day P&L (net of fees, engine BASE lots) <= thr, day = 17:00 ET roll, checked at every entry attempt (not latched). Live $4,200 = 2,400 base (x1.75). Variants replace the gate (OFF + hook). The engine's gate is NOT latched; the live rule may latch at the trip (variant a2).

## Table 1 - JL3: ulcer change / mean change vs OFF per window (engine base lots; ulcer + = lower than OFF); the reference row REF is the live setting itself
Ulcer = RMS of daily drawdown on cumulative P&L. P(lower) = week-clustered bootstrap (2,000) that the variant ulcer < OFF ulcer. Percentiles: Table 2. Days halted = label days with a trip on the cell's own closed-trade list (open-P&L cells approximate).

| setting | months | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | halted days L6M / pooled | halted share of sessions | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 0 | not landed | | | | | | | | | |
| a2. live rule latched at the 22nd close, until reset | 0 | not landed | | | | | | | | | |
| b1. open P&L counted, checked at entry, until reset | 0 | not landed | | | | | | | | | |
| b2. open P&L counted, checked at each close, latched to reset | 0 | not landed | | | | | | | | | |
| c. halt to next session boundary (22 / -4,200) | 0 | not landed | | | | | | | | | |
| d. halt 2 h | 0 | not landed | | | | | | | | | |
| d. halt 4 h | 0 | not landed | | | | | | | | | |
| f. per-book (books net negative on the day stop) | 0 | not landed | | | | | | | | | |

Same, vs REF (the live setting; ulcer + = lower than live):

| setting | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|

## Table 2 - percentile among the controls of the matching family (JL3; real vs OFF + random halts of the same halted share), three price/size columns
pct = share of valid controls the setting beats (ulcer: lower is better; mean). Columns: base lots $1.18 RT | $4.84 RT | x1.75 live lots (live lots = max(1, floor(1.75 x base + 0.5))). Halted share check: cell share vs the family target.

| setting | family | halted share cell / ctrl target | valid ctrl L6M | pct ulcer L6M base / 4.84 / live | pct mean L6M base / 4.84 / live | pct ulcer L3M | pct ulcer HOLD | pct ulcer GAP / PRE / X' | pct ulcer pooled | tier | tier W44 |
|--|--|--|--|--|--|--|--|--|--|--|--|

## Table 3 - what the halt skipped (JL3 cell vs OFF; trades present in OFF and absent in the cell = skipped, trades only in the cell = gained after the freed room; base-lot dollars, OFF lots)
Positive $ on the skipped trades = the skipped sessions were winners on average (the halt cost money); negative = losers (the halt saved money). Common-trade change = path effect on trades both runs share.

Window L6M
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

Window HOLD
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

Window HOLD
| setting | ulcer | mean $/wk | max DD | worst week | x1.75 live: ulcer / mean / max DD |
|--|--|--|--|--|--|

Window pooled
| setting | ulcer | mean $/wk | max DD | worst week | x1.75 live: ulcer / mean / max DD |
|--|--|--|--|--|--|

## Table 5 - threshold grid (JL3): ulcer change vs OFF % / mean change $/wk base; rows = closes, columns = live day loss

live form (eval at entry, until reset) - window L6M
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | n/l | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

live form (eval at entry, until reset) - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | n/l | n/l | n/l |
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
| 22 | n/l | n/l | n/l | n/l |
| 26 | n/l | n/l | n/l | n/l |
| 30 | n/l | n/l | n/l | n/l |

halt only to the next session boundary - window HOLD
| closes \ live loss | 3,000 | 4,200 | 6,000 | 8,000 |
|--|--|--|--|--|
| 18 | n/l | n/l | n/l | n/l |
| 22 | n/l | n/l | n/l | n/l |
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

## Notes and limits
- Everything is FIRST PASS and in-sample on 43 months; a window is shown only when every month of it landed for the cell and OFF. n/l = not landed; missing controls = NOT FINISHED, never passing.
- Live-vs-engine: the live night of 11-16 (22 closes, -9,660 live, halt 01:26 ET to the 18:00 reset, day -5,450) is one event; the engine day-figure counts realised closes only. Variants b1/b2 test whether open profits would have kept the halt from tripping.
- The engine's gate is evaluated at entry attempts and is not latched; a2 latches it at the trip close. c/d are trip-form: the halt starts at the closing trade that satisfies the condition, ends at the boundary / after N hours, and any later close that still satisfies the condition re-trips it.
- Inert-month copies: for settings with n >= 26 the condition rarely holds on a month's OFF trades, so those months are copies of OFF (hook cannot act). The tier percentiles use only landed, validated months.
