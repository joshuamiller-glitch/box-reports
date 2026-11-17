# DS3_REBUILD_S3 - T-REBUILD stage 3: exits jointly on the raw chassis, chosen walk-forward (W-S3). FIRST PASS. Updated 2026-11-17 08:34Z
> VALIDATION (W-S3, FIRST PASS, 2026-11-17): trials counted = 497 grid sets (7 books x 71) = N_low, 1,065 book-session-candidates = N_used (TRIALS_LEDGER.csv RB3); correction = walk-forward (select on 2023-04..2025-10 only, freeze, then HOLD 2025-11..2026-04 and L6M 2026-05..10 untouched) + ulcer reality check over the grid + CSCV PBO + >= 30 persistent random-exit engine controls on the chosen cells; numbers shown: none yet (no selection frozen; grid still landing); missing controls = NOT FINISHED, never passing. Prereg: DECISIONS.md line 2026-11-17 W-S3 PREREG.

VERDICT (data ends 2026-10-30; FIRST PASS; NO RESULT YET: the grid is landing and the selection is not frozen): grid of 497 raw-chassis exit sets is queued (21271 set-months pending of 21,385); identity gate not yet passed (a grid cell is not read until it passes); landed set-months so far 124 (SEL + HOLD + L6M). Order: server 2 takes from the front (identity, then HOLD+L6M months for every cell), box 1 takes from the back (oldest SEL months), so both ends close in on the middle.

## 1. Design
Chassis = TL3_RB_S0_<book> (JL2 engine, one book alone, every layer off: no LOT/SIGQ/REG, no cuts/locks/caps/blackout/NTZ, native lots), months 202304..202610 (43, nothing from 202611). Exit cell = d10_hooks static bracket (stop S, target T in points; lots x 60/S, min 1 = live ApplyPolicyBracket, so every stop is compared at the same dollar risk; the book trades the SAME setting in all its sessions) + bd_hooks time stop (exit at N minutes after the fill if open profit < +M points, M99 = unconditional) or half-off at +X with breakeven on the rest. 71 settings per book:
- 41 brackets: stop {30,40,50,60,75,90} x target {20,30,40,50,60,75,90} less the native point (K7 M7 U7 P7 H7 A7 60/60, O7 40/90). Code S<stop>T<target>.
- 24 time stops: N {30,60,120,240} min x M {0 (exit if not in profit), 99 (hard)} on three anchor brackets A0 native, A1 40/40, A2 50/30. Code A<anchor>N<min>M<pts>.
- 6 half-off: take half at +20/+30/+40 pts, breakeven on the rest off/on, native bracket. Code HX<pts>B<0|1>.
Per-session choice: the grid runs one setting for all sessions of the book; the per-session pick reads that session's trades from the uniform-setting set (approximation: sessions interact only through the one-position rule); the frozen picks are then run as an ASSEMBLED set per book (exact) and that run is the reported one.
Selection rule (frozen before any result, s3_select.py): per book x session cell with >= 150 native SEL trades (15 cells), candidates = grid sets with all 31 SEL months landed; floor SEL mean $/wk >= native -25%; lowest SEL ulcer (RMS of daily drawdown, dollars); keep native unless ulcer falls >= 10%.

## 2. Progress (set-months landed)
| book | cells | SEL months landed (of 31 x 71) | HOLD months landed (of 6 x 71) | L6M months landed (of 6 x 71) |
|--|--|--|--|--|
| K7 | 71 | 4 / 2201 (0 cells complete) | 0 / 426 | 12 / 426 |
| M7 | 71 | 2 / 2201 (0 cells complete) | 0 / 426 | 13 / 426 |
| P7 | 71 | 3 / 2201 (0 cells complete) | 0 / 426 | 13 / 426 |
| U7 | 71 | 3 / 2201 (0 cells complete) | 0 / 426 | 15 / 426 |
| H7 | 71 | 3 / 2201 (0 cells complete) | 0 / 426 | 18 / 426 |
| A7 | 71 | 4 / 2201 (0 cells complete) | 0 / 426 | 15 / 426 |
| O7 | 71 | 4 / 2201 (0 cells complete) | 0 / 426 | 15 / 426 |

Identity gate (TL3_RB_S3_ID_<book> vs TL3_RB_S0_<book>, 202610 and 202504, trade for trade):
```
TL3_RB_S3_ID_K7 202610: not run
TL3_RB_S3_ID_K7 202504: not run
TL3_RB_S3_ID_M7 202610: not run
TL3_RB_S3_ID_M7 202504: not run
TL3_RB_S3_ID_P7 202610: not run
TL3_RB_S3_ID_P7 202504: not run
TL3_RB_S3_ID_U7 202610: not run
TL3_RB_S3_ID_U7 202504: not run
TL3_RB_S3_ID_H7 202610: not run
TL3_RB_S3_ID_H7 202504: 32 vs 32 trades, net 22628.44 vs 22628.44 -> IDENTICAL
TL3_RB_S3_ID_A7 202610: not run
TL3_RB_S3_ID_A7 202504: not run
TL3_RB_S3_ID_O7 202610: 9 vs 9 trades, net -6425.62 vs -6425.62 -> IDENTICAL
TL3_RB_S3_ID_O7 202504: not run
```

## Results
NOT YET: selection is frozen only when every grid set has its 31 SEL months; HOLD and L6M of grid cells stay unread until then.
