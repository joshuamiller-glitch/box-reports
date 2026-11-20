# ASIA_STAGE1_FIT - per-book fit of the Asia own-checks pool (W-LAYERS, refreshed 2026-11-20 20:44Z)

GATES (order 1810Z, Josh approved): fitted settings are judged by (2) WALK-FORWARD persistence >= 0.58 (fixed pick over 93 two-week periods now; TRUE rolling pick among top-3 per group arrives from wf_run), (3) prior-year band (RULE, lead 1900Z: decided on the EQUAL-RISK $/wk change only = fitted scaled to the unfitted version's ulcer in that year, then $/wk compared; the 1-lot ulcer change is shown, not decisive; GREEN <= 15%, AMBER 15-30%, RED > 30% fails), (4) search-aware null >= 4 of 5 draws; the 27/30 date-shift count is SHOWN only. Shared function code/th_layers/wf_gate.py. Reference = the book's own BASE (today's settings). Method: S1 screen of 56 settings x last 6 months ranks; one pick per group (BRK, LOSS, LOCK, TAKE); verdict from the joint fit.

| book | picks | L6M d ulcer (neg=better) | walk-fwd persistence (fixed pick) | rolling WF | prior-year band 23/24/25 (equal-risk $/wk only; 1-lot ulcer shown, not decisive) | null | 27/30 (shown) | verdict |
|---|---|---|---|---|---|---|---|---|
| L15f14deb | BRK: BRK1; LOCK: LK8; TAKE: FR_TAKE4 | +847 | 0.538 | 0.562 (80 periods) | RED/GREEN/RED | 2/5 | 12/30 | FAIL: walk-forward persistence 0.54 < 0.58; RED prior year(s) [2023, 2025]; null: beats only 2 of 5 draws |
| L578701ed | BRK: BRK2; LOSS: FR_LOSS9; LOCK: LK2; TAKE: FR_TAKE4 | -2255 | 0.581 | 0.588 (80 periods) | GREEN/GREEN/GREEN | 4/5 | 12/30 | PASS: all gates met (27/30 shown only) |
| Lff52ec0c | LOSS: CX3; LOCK: LK7; TAKE: FR_TAKE4 | -1272 | 0.624 | 0.529 (70 periods) | GREEN/GREEN/RED | 4/5 | 15/30 | FAIL: RED prior year(s) [2025] |
| L9aa7805c | LOSS: CX2; TAKE: NRT2 | -1034 | 0.538 | 0.613 (80 periods) | RED/GREEN/AMBER | 4/5 | 20/30 | FAIL: walk-forward persistence 0.54 < 0.58; RED prior year(s) [2023] |
| M7423c0d9 | LOSS: FR_LOSS9; TAKE: TK12 | -801 | 0.57 | pending | AMBER/RED/RED | 4/5 | 19/30 | FAIL: walk-forward persistence 0.57 < 0.58; RED prior year(s) [2024, 2025] |
| L1edb9fab | BRK: BRK1; LOCK: LK1; TAKE: NRT3 | +1485 | 0.505 | 0.575 (80 periods) | RED/GREEN/GREEN | 2/5 | 16/30 | FAIL: walk-forward persistence 0.51 < 0.58; RED prior year(s) [2023]; null: beats only 2 of 5 draws |
| L7f41b347 | LOSS: STC2; LOCK: LK7; TAKE: FR_TAKE4 | +118 | - | pending | -/-/- | 2/5 | 14/30 | - |
| Lcbc8a7ec | BRK: BRK2; LOSS: CU2; TAKE: NRT1 | -1976 | - | pending | -/-/- | 4/5 | 18/30 | - |
| L3faac8df | BRK: BRK1; LOSS: CX3; TAKE: NRT4 | -2159 | - | 0.693 (75 periods) | -/-/- | 5/5 | 17/30 | - |
| L973b5c8a | LOSS: CX1 | -808 | - | pending | -/-/- | 4/5 | 19/30 | - |

In progress: L11152f7a (S3), L1756b913 (S1), L29b1bc3f (S1), L7c368a4f (S3), Lb68a132d (S3), Lec335094 (S1), L5dee2059 (S1)

Fit list (own-checks pool, unaffected bars): see /mnt/l2/l2vast/_layers/pool_fit_list.json
