# NYAM_STAGE1_FIT - per-book fit of the Asia own-checks pool (W-LAYERS, refreshed 2026-11-21 17:34Z)

GATES (order 1810Z, Josh approved): fitted settings are judged by (2) WALK-FORWARD persistence >= 0.58 (fixed pick over 93 two-week periods now; TRUE rolling pick among top-3 per group arrives from wf_run), (3) prior-year band (RULE, lead 1900Z: decided on the EQUAL-RISK $/wk change only = fitted scaled to the unfitted version's ulcer in that year, then $/wk compared; the 1-lot ulcer change is shown, not decisive; GREEN <= 15%, AMBER 15-30%, RED > 30% fails), (4) search-aware null >= 4 of 5 draws; the 27/30 date-shift count is SHOWN only. Shared function code/th_layers/wf_gate.py. Reference = the book's own BASE (today's settings). Method: S1 screen of 56 settings x last 6 months ranks; one pick per group (BRK, LOSS, LOCK, TAKE); verdict from the joint fit.

| book | picks | L6M d ulcer (neg=better) | walk-fwd persistence (fixed pick) | rolling WF | prior-year band 23/24/25 (equal-risk $/wk only; 1-lot ulcer shown, not decisive) | null | 27/30 (shown) | verdict |
|---|---|---|---|---|---|---|---|---|
| B6f77f23d | BRK: BRK4; LOSS: FR_LOSS8; LOCK: LK9; TAKE: TK8 | -762 | - | 0.493 (67 periods) | -/-/- | 2/5 | 20/30 | - |
| B7bfd33b7 | LOSS: CX3; TAKE: TK8 | -258 | - | 0.43 (79 periods) | -/-/- | 1/5 | 19/30 | - |
| L05350e98 | LOSS: CU1; LOCK: LK3; TAKE: FR_TAKE4 | -374 | - | 0.608 (79 periods) | -/-/- | 1/5 | 15/30 | - |
| L488784d8 | BRK: BRK2; LOSS: CX3; TAKE: TK5 | -1381 | - | 0.62 (79 periods) | -/-/- | 5/5 | 19/30 | - |
| L6547965c | BRK: BRK4; TAKE: TK10 | -271 | - | 0.408 (76 periods) | -/-/- | 0/5 | 17/30 | - |
| L7cc56d99 | LOCK: LK9; TAKE: FR_TAKE5 | -978 | - | 0.623 (77 periods) | -/-/- | 1/5 | 20/30 | - |

In progress: B57507767 (S1), Le0da99e2 (S3)

Fit list (own-checks pool, unaffected bars): see /mnt/l2/l2vast/_layers/ny_pool_fit_list.json
