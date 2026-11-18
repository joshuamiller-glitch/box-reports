# DS3_P7_NYAM_LOT - P7 NY AM lots on JL3, all layers on (W-P7L, order 11-17 23:30Z)
VERDICT (data ends 2026-11-13; FIRST PASS; updated 2026-11-18 04:38Z): no real cells landed yet

Five-line summary: (1) pick window end 2026-11-13 (trailing 6M 2026-05-14..2026-11-13, 3M beside, 1M also). (2) refit date 2026-11-18, then every 2 weeks (walk-forward refit dates every 14 days from 2023-10-02). (3) data end 2026-11-13 (202611 base-lot store months via W-DATA). (4) rule: P7 NY AM lots 7 live = base 4 vs base 3 / 2 / 1 / 0 (live 5 / 4 / 2 / 0; live 3 is not reachable with x1.75) and the two halves at 7 live (HA 09:30-11:00 only, HP 11:00-12:00 only); walk-forward rule R6 = cut when trailing-6M P7 NY AM P&L is negative. (5) prior-year % vs live: see the per-year table (AMBER 15-30%, RED >30% worse on ulcer / max DD / mean).

> VALIDATION (desk standard, FIRST PASS): trials counted = 6 real engine cells + 2 walk-forward rules (levels L0/L2 and L1/L3 reported), no best-of selection beyond the per-cell table; correction = percentile among 30 persistent-draw engine controls (staged: controls run for the leading cells only) + week-clustered bootstrap (2,000) + calibrated ulcer-primary tiers (cutoffs_ulc TUNED); PBO not applicable (no fitted parameters; the cut level is a fixed table); in-sample on all 44 months, walk-forward section is the out-of-sample judge; prereg PREREG_P7L.md sha in DECISIONS.md.

Months landed: ; JL3 base months 44.

## P7 NY AM in JL3 (anatomy; $4.84 RT, base lots)
| window | trades | net $ | $/wk | 09:30-11:00 n / net | 11:00-12:00 n / net |
|--|--|--|--|--|--|
| L6M | 43 | 7,195 | 274 | 23 / 3,098 | 20 / 4,097 |
| L3M | 22 | 4,282 | 326 | 10 / 948 | 12 / 3,334 |
| HOLD | 27 | 14,516 | 561 | 12 / 10,843 | 15 / 3,673 |
| PRE | 71 | -18,794 | -482 | 40 / -14,091 | 31 / -4,703 |
| X' | 89 | 10,555 | 135 | 44 / 3,754 | 45 / 6,801 |
| POOLED | 252 | 17,479 | 92 | 132 / 5,038 | 120 / 12,441 |

## Table A - every cell vs JL3 live (lots 7), all windows (ulcer first; $4.84 RT base lots; x1.75 live lots at $4.84 beside)

## Table B - freed-book effects (net $ change vs JL3, base lots $1.18, by book; P7 NY AM = own cell, others = what the freed stack room did)
| cell | window | P7 NY AM | P7 other sessions | K7 | M7 | U7 | H7 | A7 | O7 | stack |
|--|--|--|--|--|--|--|--|--|--|--|

## Table C - rolling 2-week refit walk-forward of the lot choice (rule R6: cut P7 NY AM to the cell level when trailing-6M P7 NY AM P&L (JL3, base lots) < 0, else live 7; arithmetic splice of the cell and JL3 daily P&L, no boundary path effects; $4.84 base lots)
walk-forward not run yet (needs the cell for all months).

## Table D - persistent random controls and calibrated tier
controls not queued/landed yet.

## Bar swap vs lot cut (W-SWB, 36 TL3_SWB sets for P7 NY AM)
Swap page line: - Engine: hook identity (live 1-min bar through the hook = JL3 trade for trade): P7 NY AM and O7 exact on 202504 and 202610 (hook v1); P7 London and H7 NY AM exact on 202504 with hook v2 (swb_inject2; 202610 and the other cells in section 4 as they land); sets TL3_SWB_* queued per cell: top 5 naked (6M), top 5 naked (3M), best row per bar family, 30 random-clock controls on the primary pick; verdi | the lot-cut result is in Table A; compare on ulcer first.

Live DS7 need: panel setting only (P7 lots by session 12,7,0,7,0,0 -> 12,7,0,N,0,0 with N = live lots in the table); the half-session variants need a time-of-day lot window (new code: lots 0 for P7 in 09:30-11:00 or 11:00-12:00).
