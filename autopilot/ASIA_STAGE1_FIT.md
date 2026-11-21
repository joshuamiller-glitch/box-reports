# ASIA_STAGE1_FIT - per-book fit of the Asia own-checks pool (W-LAYERS, refreshed 2026-11-21 04:39Z)

GATES (order 1810Z, Josh approved): fitted settings are judged by (2) WALK-FORWARD persistence >= 0.58 (fixed pick over 93 two-week periods now; TRUE rolling pick among top-3 per group arrives from wf_run), (3) prior-year band (RULE, lead 1900Z: decided on the EQUAL-RISK $/wk change only = fitted scaled to the unfitted version's ulcer in that year, then $/wk compared; the 1-lot ulcer change is shown, not decisive; GREEN <= 15%, AMBER 15-30%, RED > 30% fails), (4) search-aware null >= 4 of 5 draws; the 27/30 date-shift count is SHOWN only. Shared function code/th_layers/wf_gate.py. Reference = the book's own BASE (today's settings). Method: S1 screen of 56 settings x last 6 months ranks; one pick per group (BRK, LOSS, LOCK, TAKE); verdict from the joint fit.

| book | picks | L6M d ulcer (neg=better) | walk-fwd persistence (fixed pick) | rolling WF | prior-year band 23/24/25 (equal-risk $/wk only; 1-lot ulcer shown, not decisive) | null | 27/30 (shown) | verdict |
|---|---|---|---|---|---|---|---|---|
| L15f14deb | BRK: BRK1; LOCK: LK8; TAKE: FR_TAKE4 | +847 | 0.538 | 0.562 (80 periods) | RED/GREEN/RED | 2/5 | 12/30 | FAIL: walk-forward persistence 0.54 < 0.58; RED prior year(s) [2023, 2025]; null: beats only 2 of 5 draws |
| L578701ed | BRK: BRK2; LOSS: FR_LOSS9; LOCK: LK2; TAKE: FR_TAKE4 | -2255 | 0.581 | 0.588 (80 periods) | GREEN/GREEN/GREEN | 4/5 | 12/30 | PASS: all gates met (27/30 shown only) |
| Lff52ec0c | LOSS: CX3; LOCK: LK7; TAKE: FR_TAKE4 | -1272 | 0.624 | 0.529 (70 periods) | GREEN/GREEN/RED | 4/5 | 15/30 | FAIL: RED prior year(s) [2025] |
| L9aa7805c | LOSS: CX2; TAKE: NRT2 | -1034 | 0.538 | 0.613 (80 periods) | RED/GREEN/AMBER | 4/5 | 20/30 | FAIL: walk-forward persistence 0.54 < 0.58; RED prior year(s) [2023] |
| M7423c0d9 | LOSS: FR_LOSS9; TAKE: TK12 | -801 | 0.57 | 0.588 (80 periods) | AMBER/RED/RED | 4/5 | 19/30 | FAIL: walk-forward persistence 0.57 < 0.58; RED prior year(s) [2024, 2025] |
| L1edb9fab | BRK: BRK1; LOCK: LK1; TAKE: NRT3 | +1485 | 0.505 | 0.575 (80 periods) | RED/GREEN/GREEN | 2/5 | 16/30 | FAIL: walk-forward persistence 0.51 < 0.58; RED prior year(s) [2023]; null: beats only 2 of 5 draws |
| L7f41b347 | LOSS: STC2; LOCK: LK7; TAKE: FR_TAKE4 | +118 | - | 0.562 (80 periods) | -/-/- | 2/5 | 14/30 | - |
| Lcbc8a7ec | BRK: BRK2; LOSS: CU2; TAKE: NRT1 | -1976 | - | 0.52 (75 periods) | -/-/- | 4/5 | 18/30 | - |
| L3faac8df | BRK: BRK1; LOSS: CX3; TAKE: NRT4 | -2159 | - | 0.693 (75 periods) | -/-/- | 5/5 | 17/30 | - |
| L973b5c8a | LOSS: CX1 | -808 | - | 0.6 (80 periods) | -/-/- | 4/5 | 19/30 | - |
| Lb68a132d | BRK: BRK3; LOSS: CX2; LOCK: LK2; TAKE: TK5 | -1269 | - | 0.471 (68 periods) | -/-/- | 4/5 | 17/30 | - |
| Lec335094 | - | - | - | 0.608 (79 periods) | -/-/- | pending | - | no setting passes the drawdown-first rule: the book keeps today's (stand-in) settings |
| L5dee2059 | BRK: BRK4; LOCK: LK1 | -1313 | - | 0.722 (79 periods) | -/-/- | 4/5 | 18/30 | - |
| L7c368a4f | BRK: BRK2; LOCK: LK1 | -1660 | - | 0.537 (80 periods) | -/-/- | 4/5 | 15/30 | - |
| L1756b913 | BRK: BRK1; LOCK: LK7; TAKE: NRT3 | -648 | - | 0.528 (72 periods) | -/-/- | 3/5 | 17/30 | - |
| L29b1bc3f | BRK: BRK1; LOSS: STC1; TAKE: TK1 | -570 | - | 0.633 (79 periods) | -/-/- | 3/5 | 13/30 | - |
| L40bde9ea | BRK: BRK1; LOSS: STC3; LOCK: LK2; TAKE: TK8 | +427 | - | 0.557 (79 periods) | -/-/- | 2/5 | 13/30 | - |
| L7ea48296 | BRK: BRK1; LOSS: CU4; LOCK: LK4; TAKE: TK5 | +608 | - | 0.628 (78 periods) | -/-/- | 2/5 | 14/30 | - |
| L65a26c02 | LOSS: CX3 | -1107 | - | 0.595 (79 periods) | -/-/- | 4/5 | 19/30 | - |
| La010c3eb | BRK: BRK3; LOSS: CX1; LOCK: LK6; TAKE: SHV2 | -958 | - | 0.675 (80 periods) | -/-/- | 4/5 | 0/0 | - |
| Lc754cf58 | BRK: BRK2; LOSS: STC2; TAKE: TK5 | +1190 | - | 0.588 (80 periods) | -/-/- | 2/5 | 8/30 | - |
| Ma010c3eb | BRK: BRK1; LOSS: FR_LOSS9; LOCK: LK1; TAKE: TK2 | +166 | - | 0.685 (73 periods) | -/-/- | 2/5 | 0/0 | - |
| Mcae177ba | TAKE: TK12 | -329 | - | 0.671 (76 periods) | -/-/- | 3/5 | 0/0 | - |
| L385f4f2e | BRK: BRK4; LOSS: STC2; LOCK: LK4; TAKE: TK1 | -895 | - | 0.709 (79 periods) | -/-/- | 4/5 | 0/0 | - |
| M7ea48296 | BRK: BRK2; LOSS: CX2; LOCK: LK4; TAKE: TK5 | -1027 | - | 0.649 (77 periods) | -/-/- | 4/5 | 0/0 | - |

In progress: L11152f7a (S3), Lcae177ba (S1), L9e4754b9 (S1), M86781ac0 (S1)

Fit list (own-checks pool, unaffected bars): see /mnt/l2/l2vast/_layers/pool_fit_list.json
